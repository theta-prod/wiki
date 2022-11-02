# [SOP] How to build a wiki page

- **Metadata** : `type: SOP` `scope: wiki` 
- **Techs Need** : `markdown` 
- **Status** : `on-going`

## ✨ You should already know

> Nothing

👩‍💻 👨‍💻

## ✨ About the wiki

- `Situation:`  We need to create many wiki pages or docs for org. 
- `Target:`  Make a template for all wiki

- `Index:`

| Sub title | decription | memo |
| ------ | ------ | ------ |
| Make a Section | template for creating a Section | - |
| Metadata for wiki | types can use for Metadata | - |
| Techs need for wiki | Add tags for wiki | - |
| Status for wiki | Add tags for wiki | - |
| You should already know | something should be learned first. | - |
| About the wiki | Create decription for wiki | - |
| Page Template | you can copy it | - |

## ✨  Sections


### **Make a Section**
`type: doc` `status: done`
> It's a template for creating a Section.
> We should add some text to introduce this section, and appends sample code or template could be rebuilt. 

#### 📝 A template for making section.
> cope it to new sections.
```
### **...**
`type: ...` `status: ...`
> ...

####  📝 title of section (1)
> cope it to new sections.
...


####  📝 title of section (2)
> cope it to new sections.
...


```


####  📝 What did kind of "type" for section we have
> Following types you can use for sections-type.
> Submit a PR to create new type if you need.


| Type | decription | 
| ------ | ------ | 
| doc | document, tutorial,or other content focus on introduction |
| code | Sample code, Anything relate about programming | 
| command | config, shell script, or other like .ymal or .env file |
| template | Example for copy and paste |



####  📝What did kind of "status" for section we have
> Following status-types you can use for sections-status.
> Submit a PR to create new status-types if you need.

| Status | decription | 
| ------ | ------ | 
| need-a-owner | something need to-do but without someone. |
| todo | something need to-do and had know who need to do. | 
| on-going | already to begin but not yet completed |
| need-review | already completed but need someone review |
| done | completed and reviewed |




### **Metadata for Wiki**
`type: doc` `status: done`
> Create Metadatas for wiki.
> Metadatas would contain type and scope
> Submit a PR to update if you need.

####  📝What did kind of "type" for Metadata we have
> following type you could use to be Metadata tag and prefix of title.

| Type | decription | 
| ------ | ------ | 
| SOP | Anyone has to know |
| REF | something you want to sharing | 
| Tutorial | teach other how to rebuilt something |

####  📝What did kind of "scope" for Metadata we have
> new any tag you want.
> following type just as reference.
- wiki
- sre
- backend
- frontend


### **Techs need for wiki**
`type: doc` `status: done`
> Add some tags to intro this wiki.

####  📝What did kind of "Techs" for Metadata we have
> new any tag you want.
> following type just as reference.
- markdown
- python
- backend
- fastapi


### **Status for wiki**
`type: doc` `status: done`
> make everyone to know what's status of this wiki.


####  📝 What did kind of "status" for section we have
> Submit a PR to create new status-types if you need.

| Status | decription | 
| ------ | ------ | 
| need-a-owner | something need to-do but without someone. |
| todo | something need to-do and had know who need to do. | 
| on-going | already to begin but not yet completed |
| need-review | already completed but need someone review |
| done | completed and reviewed |


### **You should already know**
`type: doc` `status: done`
> Alarm people to study some topic before read this wiki.

####  📝 What's the part will be contain
> following as reference.

| reference | decription | 
| ------ | ------ | 
| knowlage/paper | something need to-do but without someone. |
| skill | like docker, k8s, restful api| 
| framework | like flask, pytorch | 
| platform | like huggingface, github, dockerhub | 

### **About the wiki**
`type: doc` `status: done`
> Create decription for wiki.
> decription would contain `Situation`, `Target` and `Index`

####  📝 Situation
> why we need to read this wiki or When we should ref this wiki.


####  📝 Target
> what can we do after we read this wiki

####  📝 Index
> Table of contents.
> Cope it can help you

| Subtitle | decription | memo |
| ------ | ------ | ------ |
| title | - | - |




### **Page Template**
`type: template` `status: done`

```
# [...] <WIKI PAGE NAME>

- **Metadata** : `type: ...` `scope: ...` 
- **Techs Need** : `...` `...`
- **Status** : `..`

## ✨ You should already know

> ...

👩‍💻 👨‍💻

## ✨ About the wiki

- `Situation:`  ... 
- `Target:` ...

- `Index:`

| Sub title | decription | memo |
| ------ | ------ | ------ |
| - | - | - |
| - | - | - |


## ✨  Sections


### **<SECTION NAME>**
`type: ...` `status: ...`
> ....

#### 📝 <SUBSECTION NAME>
> ...
```
