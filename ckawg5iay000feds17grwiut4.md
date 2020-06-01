## How To Build A To-Do List With React


![Final app.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1591008906908/Tc_9Ji6hu.png)


Things you must know:

- 
All functional components or functions apart from those provided by *create-react-app*, are going to be written as arrow functions.


- 
You need to know the basics of React to understand this article.
(you could check out  [React Documentation](https://reactjs.org/) .)


- 
This article does not involve deploying the to-do list app.

For those who would like to check out the real code, here’s the  [link](https://github.com/caspero-62/to-do-list-demo-for-article)  to that.
You could also access the live app  [here](https://caspero-62.github.io/to-do-list/) .

Since this is just a React tutorial, I am just going to drop the links to the CSS files for each component:

1.  [Index.css](https://github.com/caspero-62/to-do-list-demo-for-article/blob/master/src/index.css)  
2.  [App.css](https://github.com/caspero-62/to-do-list-demo-for-article/blob/master/src/App.css)    
3.  [ToDoList.style.css](https://github.com/caspero-62/to-do-list-demo-for-article/blob/master/src/components/ToDoList/ToDoList.style.css)   
4.  [ToDo.style.css](https://github.com/caspero-62/to-do-list-demo-for-article/blob/master/src/components/ToDo/ToDo.style.css)  
5.  [TaskIndicator.style.css](https://github.com/caspero-62/to-do-list-demo-for-article/blob/master/src/components/TaskIndicator/TaskIndicator.style.css)   
6.  [InputForm.style.css](https://github.com/caspero-62/to-do-list-demo-for-article/blob/master/src/components/InputForm/InputForm.style.css)    



**Setting Up the React App** 

For the sake of this example, we would be using the *create-react-app* method to set up our app. This is to make everything easy for us. 

If you do not have *create-react-app* set up on your computer, you can get started by checking out  [Create React Documentation](https://facebook.github.io/create-react-app/docs/getting-started) .

The following steps would get you started to setting up your app:

1. Go to your terminal (if you are a MAC OS/LINUX user) or command prompt (if you are a Windows user).


> 
Note: In this article, I would be using only the term ‘terminal’. 

2. Change path to the directory you want to app to be created on, using the *cd* command:

![create-react-app3.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1591015383987/puvGwtpn8.png)

3. Type ```create-react-app <name of the app>``` in your terminal and hit Enter. This installs and the app and Voila!! We can start coding our app.

![create-react-app5.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1591015410701/GjJcnaJaY.png)

> 
Note: If you get an error message, try using the *sudo* command to switch to root.

4. Go into the app folder and open in VsCode or any IDE of your choice :

![create-react-app4.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1591015487543/kgUG08Ze9.png)


**Sketch And Structure**

Before we dive into coding our app, we need to have a visual representation or structure of what we want to achieve. I have a quick sketch of how we want the app to look like :

![to-do-list sketch.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1591009596056/TUEqfW8UU.png)

Most especially in React, we want to know the following:

- 
What our components would look like.

- 
What part of the components should change or be updated. 

- 
When they would change.

Looking at the image, there are three basic components we would need to come up with:
1. **Input Form:** This part takes care of receiving user input (task) which would eventually be rendered to the “to-do list” component. 
2. **To-do List:** This component serves as a container for each to-do (task) component and accommodates any new task accepted.
3. **Task Indicator:** This component would display the number of tasks you have at that moment.

Just as these components have been set out, this is how they would look like in our app. We would have to include a to-do component for each task and finally, our *App.js* file would contain all of these components (this is already provided to us by *create-react-app*.)

After the whole setup, we have our app’s *src* structure looking like this:

![codestructure.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1591015599121/3Mq0vkAWP.png)

As you can see here, we created a *component* folder under the *src* folder, to house all individual and reusable components. This is one of the major advantages of React; it helps to break down our entire app into chunks (reusable components). We tend to see that advantage more, when building larger applications.



**Coding The App** 

Finally, it is time to code our app. With all our files in place, let us start with the *App* component since it would house all of our remaining components. 
This particular *App* component would be a class component so that we can have access to React's *state*.

I would recommend we clear the whole content inside our *App.js* file and start coding it from scratch. However, you could just modify it to the code below:

![App1.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1591015632699/HGpmA3tmO.png)
![App2.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1591015651395/WMg2O4Evo.png)

Okay let’s explain what we’ve done so far - The first image just describes what we have to import. As you know, before writing any functional or class component in React, we have to import React. Since this is a class component, we also have to import React’s component class as well.

We then import the *TaskIndicator* function from its respective file and also the css file for the App component.

After this, we start writing our *App* class components which would extend the Component class of React and has access to its methods (by calling *super()*). This gives us access to a *state* property which we can declare what we want to change.

In the case of our app, what we want to change is our tasks (*lists*) property, with object values containing each *task* and its respective *id*.

The *render* method is then called, which would *return* the components we want to in HTML like format (*JSX*). The first thing we render for now is the *TaskIndicator* component, which we pass the number props into, indicating the number of tasks left in our to-do list.

Let’s see how our *TaskIndicator* component will look like:

![Taskindicator code.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1591015711682/x4bAh_lzu.png)

We make it a functional component(since it doesn't contain any state) that just returns a text with the number of tasks we have (using the *number* props we passed to it).
After applying the components CSS file, we should see this in our browser:

![Task Indicator.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1591015743455/bLXIuOtM7.png)

As you can see, it indicates that we have 3 tasks which is the amount of objects present in our lists array.

That was pretty easy, wasn’t it?! Now let’s move on to adding our *ToDoList* component which would take the *lists* array as its *props*, and also have a *handleDelete* method that would help delete any task we are done with. The *handleDelete* method is as follows:

![handleDelete.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1591015776249/yILtyKluk.png)

This method takes in an *index* argument that would help to filter out a task from the list with id not equal to the index. It then modifies the lists state to the filtered form using the *this.setState()* method.

We then add the *ToDoList* component to the *render* method of our *App.js* file:

![newApp.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1591016358632/TxxYQS1Ls.png)

Do not forget to *import* the *ToDoList* function from its file and then go on to write the *ToDoList* function:

![ToDoList.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1591015893612/1jo1up-g0.png)

This functional component iterates through the *lists* array given as *props*, and returns a *ToDo* component for each list. We then give each *ToDo* component the following props:

- 
**key** (equivalent to the id value in the list object)

- 
**index** (same as key, but this is passed into the handleDelete method for removing each task.)

- 
**task** (which represents each task of the lists array)

- 
**onDelete** (this is the *handleDelete* method written in our App component.)

Of course, we import our *ToDo* component and write the function in our *ToDo.component.jsx* file:

![ToDo.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1591016193577/3OG2sFeP7.png)

This part of our app finally returns a *div* with each task and a font awesome minus (-) icon  that has the *onDelete* props passed to it. When this icon is clicked, the corresponding task is removed. The component is then exported.

To access the font awesome icon, we add the *script* tag below to the end of our body tag, in our *index.html* file which is located in the *public* folder of our app.
```
<script src="https://kit.fontawesome.com/8ca81c817e.js" crossorigin="anonymous"></script>
```


After all this, our app comes out looking like this:

![2nd stage.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1591015926194/vwxTjmDf8.png)

Now the final stage of our app which is creating the input form that would take in new tasks and add them to the list. From our sketch, this form would contain an *input* element (of type=’text’) and another font-awesome icon with the plus (+) sign. 

To help us achieve this, we need the following methods:

- 
a handleChange method that takes care of any value being passed as  input

- 
a handleSubmit method that adds the input (task) to the list as far as it is not empty.

First of, we add an *input* state in our *App* component:

![inputstate.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1591015956960/AhtGUf4h3.png)

After which we proceed to write our *handleChange* and *handleSubmit* methods after the *constructor*.

![hanldes.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1591016250273/x-pmMGFr0.png)

The *handleChange* method as mentioned earlier, just takes note of what the user types and sets our input to that value. 

Our *handleSubmit* method on the other hand, does nothing if the user's input is empty. If the user eventually does write something, it creates an object with the *task* and *id* property and adds this object to our to-do list. When the task is added, the form is cleared or reset.

As we have done for the previous components, we import the *InputForm* component from its corresponding file and render it in our *App* component :
```
import InputForm from './components/InputForm/InputForm.component.jsx';
```
![render.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1591016302542/oqn6Of8cG.png)

Remember that we have to pass in the two methods we just wrote, as props into the *InputForm* component.

Our *InputForm* component is shown below:

![InputForm.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1591016051359/rvd-la75g.png)

We make use of all necessary props and *export* our component. 

**Conclusion**

And that’s it!! We have our to-do list app ready. Just add the necessary styles and we have our app looking exactly like the finished product at the beginning.

Understanding a little project like this can help you grab some basic concepts in React and prepare you to learn more challenging concepts as you proceed.


                                   .  .  .

If you liked this article, you could share and give a thumbs up. Cheers!! 


