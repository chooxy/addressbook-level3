# Developer Guide

* [Setting Up](#setting-up)
* [Design](#design)
* [Testing](#testing)
* [Appendix A: User Stories](#appendix-a--user-stories)
* [Appendix B: Use Cases](#appendix-b--use-cases)
* [Appendix C: Non Functional Requirements](#appendix-c--non-functional-requirements)
* [Appendix D: Gloassary](#appendix-d--glossary)

## Setting up

#### Prerequisites

1. **JDK 8** or later
2. **Eclipse** IDE
3. **e(fx)clipse** plugin for Eclipse (Do the steps 2 onwards given in
   [this page](http://www.eclipse.org/efxclipse/install.html#for-the-ambitious))


#### Importing the project into Eclipse

0. Fork this repo, and clone the fork to your computer
1. Open Eclipse (Note: Ensure you have installed the **e(fx)clipse plugin** as given in the prerequisites above)
2. Click `File` > `Import`
3. Click `General` > `Existing Projects into Workspace` > `Next`
4. Click `Browse`, then locate the project's directory
5. Click `Finish`

## Design
<img src="images/mainClassDiagram.png"/>

## Testing

* In Eclipse, right-click on the `test/java` folder and choose `Run as` > `JUnit Test`

## Appendix A : User Stories

Priorities: High (must have) - `* * *`, Medium (nice to have)  - `* *`,  Low (unlikely to have) - `*`


Priority | As a ... | I want to ... | So that I can...
-------- | :-------- | :--------- | :-----------
`* * *` | new user | see usage instructions | refer to instructions when I forget how to use the App
`* * *` | user | add a new person |
`* * *` | user | delete a person | remove entries that I no longer need
`* * *` | user | find a person by name | locate details of persons without having to go through the entire list
`* * *` | user | find a person by contact details | find out who contacted me without leaving their name
`* * *` | user | edit a person's contact details | update contact details without having to delete and add from scratch
`* *` | user | hide [private contact details](#private-contact-detail) by default | minimize chance of someone else seeing them by accident
`* *` | user | see a list of recently added people | find a new acquaintance whose name I may have forgotten
`* *` | lazy user | alternative, shorter command words | type less 
`* *` | user| tag people | search for a group of people
`*` | user with many persons in the address book | sort persons by name | locate a person easily
`*` | user with bad memory | see a list of most most searched names | easily find the same people again
`*` | user | export a list of people in | refer to a specific list of people's details without having to start up the App

## Appendix B : Use Cases

(For all use cases below, the **System** is the `AddressBook` and the **Actor** is the `user`, unless specified otherwise)

#### Use case: Delete person

**MSS**

1. User requests to list persons
2. AddressBook shows a list of persons
3. User requests to delete a specific person in the list
4. AddressBook deletes the person <br>
Use case ends.

**Extensions**

2a. The list is empty

> Use case ends

3a. The given index is invalid

> 3a1. AddressBook shows an error message <br>
  Use case resumes at step 2

#### Use case: Rename tag

**MSS**

1. User requests to list tags
2. AddressBook shows a list of tags
3. User requests to rename a specific tag in the list
4. AddressBook asks for new name
5. User provides new name
6. AddressBook prompts user to confirm changing specific tag from old name to new name
7. User confirms
8. AddressBook renames specific tag from old name to new name
Use case ends.

**Extensions**

2a. The list is empty

> Use case ends

3a. The given index is invalid

> 3a1. AddressBook shows an error message
  Use case resumes at step 2
  
5a. User decides not to change the selected tag

> 5a1. User enters command to cancel instead of new name
  Use case resumes at step 2
  
6a. User typed new name wrongly

> 6a1. User rejects the change
  Use case resumes at step 4
  
8a. User decides to undo the change

> 8a1. User enters command to undo the change
  Use case ends
  
## Appendix C : Non Functional Requirements

1. Should work on any [mainstream OS](#mainstream-os) as long as it has Java 8 or higher installed.
2. Should be able to hold up to 1000 persons.
3. Should come with automated unit tests and open source code.
4. Should favor DOS style commands over Unix-style commands.
5. Should start up within one second.
6. Should accept email address up to 254 characters. (Maximum length of email addresses as of [SMTP](#SMTP) RFC5321 standards)

## Appendix D : Glossary

##### Mainstream OS

> Windows, Linux, Unix, OS-X

##### Private contact detail

> A contact detail that is not meant to be shared with others

#### SMTP

> Short for Simple Mail Transfer Protocol