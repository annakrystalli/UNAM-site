## **Collaborative `github`**
<br>
<br>

### **Anna Krystalli**
##### ***Instituto de Ecología, UNAM 1 Sep. 2016***

<br>

###### <https://annakrystalli.github.io/UNAM/collab_gh_intro.nb.html>

###### [\@annakrystalli](https://twitter.com/annakrystalli) | annakrystalli@googlemail.com

<br>
<br>

## 

### **github for collaboration (in RStudio)**

<img src="http://www.palermo.edu/Archivos_content/ingenieria/top/130712_git_github_topdenota1.jpg" height="300px" />


<br>
<br>


## **github & science**

> \"*The need for a logical way to organize and control revisions has existed for almost as long as writing has existed, but revision control became much more important, and complicated, when the era of computing began.*\"

<br>

## **version control**

- **long been used to maintain code repositories in the software industry**

     > especially in open source software
    
- **science increasingly computational**

    > demands for increased openness

<br>




## {data-background-iframe="http://billmills.github.io/scienceXpython/"}

.
<br>
<br>
<br>

<http://billmills.github.io/scienceXpython/>

<br>

## modern science workflows

***can be overwhelming***

<img src="images/workflows.png" width="500px" />

<br>

## succesful modern science workflows

***can be extremely powerful***

<img src="images/collab.png" width="500px" />

<br>
<br>

## github for science

[![](images/git4sci.png)](http://scfbm.biomedcentral.com/articles/10.1186/1751-0473-8-7)


> ideal for managing the full suite of research outputs such as datasets, statistical code, figures, lab notes, and manuscripts.

#### e.g [***My research workflow, based on Github***](https://status.github.com/images/invertocat.png) by [*Carl Boettiger*](https://twitter.com/cboettig)


<br>

## Rstudio for r users 

![](https://status.github.com/images/invertocat.png)

<img src="https://pbs.twimg.com/profile_images/487277095681150976/aEp2vlJy.png" width="200px" />



## **invest in next generation science skills**

<br>

- ...and super-charge your teams!

- ...or get left behind

<br>
<br>

***

# **empowering collaboration**

## repos

centralising information e.g. [**ROpenSci / rfishbase**](https://github.com/ropensci/rfishbase)

<img src="images/repo-1.png" width="500px"/>




<br>

## issues

project management

[<img src="images/issues-1.png" width="500px"/>](https://github.com/ropensci/rfishbase/issues)

<br>

## commits 

project tracking

[<img src="images/track-1.png" width="500px"/>](https://github.com/ropensci/rfishbase/network)

<br>
<br>

***

# **fostering reproducibility**

## commits

traceability

[<img src="images/commits-1.png" width="500px"/>](https://github.com/ropensci/rfishbase/commits/master)

<br>
<br>

## **entire process of project evolution reproducible**

<br>
<br>

***

# **PRACTICALS**

<br>

## **Practical 1: Github & Rstusio for version control**

Code Cafe Style tutorial by [Mike Croucher](http://www.walkingrandomly.com/)

### [**Enter Practical**](https://github.com/mikecroucher/ISBE_Symposium)


<br>
<br>
<br>


## **Practical 2: Github & Rstusio for collaborative coding**

In this exercise, each participant will be forking a repo in order to create and contribute a **trendline for the evolution of a trait** in an imaginary species.

We'll use github to collate the trendlines for all our species and plot them up all together!

<br>
<br>


## **github: start with a repo**

<https://github.com/RSE-Sheffield/collaborative_github_exercise>

<img src="images/repo.png" width="500px" />

<br>

## **fork repo**

**github: make your **own copy of the repository** on github

- fork are linked and traceable

<img src="images/fork-1.png" width="500px" /> 

<br>

##

**github:** Github makes a **copy into your account**

<img src="images/fork-2.png" width="500px" />
 
<br>

## 
        
**github: clone it: copy repo link** to initiate Rstudio project
    
<img src="images/fork-3.png" width="500px" />

<br>
<br>


## **create new project in Rstudio**


##
**rstudio: Create **new project**

<img src="images/newproj-1.png" width="500px" />

<br>

##
**rstudio:** Checkout from **version control repository**

<img src="images/newproj-2.png" width="500px" />

<br>

##
**rstudio:** Clone project from a **git** repository

<img src="images/newproj-3.png" width="500px" />

<br>


##
**rstudio:** Paste **repo link copied from Github** into **Repository URL** field. Click **`Create Project`**. 

<img src="images/newproj-4.png" width="500px" />

<br>

##
**rstudio:** Rstudio project now **contains all files from the github repo.**

<img src="images/newproj-5.png" width="500px" />

<br>
<br>




## **make a change to the repo**



**rstudio:** open **`params/params_tmpl.R`**

<img src="images/edit-1.png" width="500px" />

<br>

##


**rstudio:** save as new `.R` script in **`params/`** folder. Use species name of your choice to name new file

<img src="images/edit-2.png" width="500px" />

<br>

##


**rstudio:** edit file with parameters of your choice and save.

<img src="images/edit-3.png" width="500px" />

<br>

<br>


## commit changes locally to git

**rstudio:** in the *git* tab, select the **new file** you created and click **`Commit`**

<img src="images/commit-1.png" width="500px" />

<br>

##

**rstudio:** write an informative commit message and click **`Commit`**  

<img src="images/commit-2.png" width="500px" />

<br>

##

**rstudio:** your new file has now been commited  

<img src="images/commit-3.png" width="500px" />

<br>
<br>

## push changes to Github

**rstudio:** on the *git* tab click ⇧  to **push changes to Github**

<img src="images/push-1.png" width="500px" />

<br>

##

**rstudio:** changes have now been updated on **Github repo**

<img src="images/push-2.png" width="500px" />

<br>
<br>

## create pull request

**github:** in your repository, create **`new pull request`** to merge fork to master repo (ie the original repo you forked)

<img src="images/merge-1.png" width="500px" />

<br>

##

**github:** github checkes whether your requested merge creates any coflicts. If all is good, click on **`Create pull request`**

<img src="images/merge-2.png" width="500px" />

<br>

##

**github:** write an informative message, explaining your changes to the master repo administrators. Click on **`Create pull request`**

<img src="images/merge-3.png" width="500px" />

<br>

##

**github:** check original repo to see **your merged changes**

<img src="images/merged.png" width="500px" />

<br>
<br>
<br>

# exercise

## your mission

- fork the repo: <https://github.com/RSE-Sheffield/collaborative_github_exercise>
- link it up to a new Rstudio project
- create a new params `.R` script. Name it using your selected species name.
- enter parameters for your species.
- commit & push your changes
- create a pull request to the master repo

We'll merge all contributions and [plot them together at the end!](http://rpubs.com/annakrystalli/200121) 


## resources

[link to presentation handout](https://github.com/annakrystalli/ISBE_symposium/blob/master/Collaborative_github_test/collab_gh_into.md)

[Karthik Ram's article:](http://scfbm.biomedcentral.com/articles/10.1186/1751-0473-8-7) *'Git can facilitate greater reproducibility and increased transparency in science'*

[Getting started with GitHub](http://jennybc.github.io/2014-05-12-ubc/ubc-r/session2.4_github.html) from materials for a [software carpentry course at UBC](http://jennybc.github.io/2014-05-12-ubc/)

[Slides for lecture](http://kbroman.org/Tools4RR/assets/lectures/04_git_withnotes.pdf)  Karl Broman gave on git/github, with notes

[joeyklee's friendly github intro](https://github.com/joeyklee/friendly-github-intro). *Mozilla Science Lab* workshop



