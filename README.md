# Frontend First Todo App

This repository contains an implementation of the [TodoMVC app](https://todomvc.com/). 
This is meant as the starting point showcase for the Frontend First development style.

## Frontend First

Agile software development is now common, but there are still problems. Developers don't
get the quality feedback they require, or they get this feedback too late in the development process.

The idea behind Frontend First development is to get real feedback, from real users, as soon as possible.

Instead of delivering incomplete systems to internal product managers, frontend first focuses on getting
a real working prototype application in the hands of real users as quick as possible. To that end the
initial focus is on getting the frontend working and complete enough that users will want to try it out. 
The backend is only implemented to the minimal functionality needed to allow the frontend to work.

Frontend First focuses on the part that users work with, including usability and user experience (UX).
Things like security, reliability, stability, scalability, etc. are all secondary concerns. The main 
problem it tries to solve is to get feedback from users from actual use. In our experience users will
only really use a product (or prototype), if it looks like a real product and if it reaches a minimum
level of usability.

The backend starts out as dumb as possible. Only when the frontend requires it, the backend is expanded.
For this to work well a few things need to be done:

1 - You must be able to iterate the frontend fast, while making sure the quality is good enough. This
can be accomplished using design systems and component libraries. In addition keep the javascript code
to a minimum. This example uses [SimplyEdit](https://simplyedit.io) and 
[SimplyView](https://github.com/simplyedit/simplyview/) to that end. Vue.js is also a good fit.

2 - The backend must be able to grow from small and simple to as big and complex as is needed later,
without a complete rewrite. Micro-services are a good fit for this, but we can actually start even smaller.
This example uses a set of [PHP components by Muze, called ARC](https://github.com/Ariadne-CMS/arc-arc). 
Firebase and Appwrite, or other backend-as-a-service systems may also be a good fit. 
Ideally you don't have to define routes and models early on.

## Simply Todo

This is about as simple an application that you can make and still be an application. It is meant to
showcase the first steps in a frontend-first approach. Other repositories will appear later that will 
expand on this example to show how you grow from a first prototype.

## Quickstart

This example uses Docker Compose to start the frontend, backend and database. It also starts a front proxy, called
Traefik, that will allow you to add security and API management features later.

The todo app and backend use the `todo.local` and `backend.local` names. To open these in your browser, add these
names to your hosts file as `127.0.0.1`, or add `*.local`.

Make sure you aren't running a webserver on port 80 locally, then start the services from the root of the repository:
```
docker-compose up
```

## Backend

The backend is a simple REST api that doesn't require any configuration. You can add any content to it
without needing a model or configuration. It also has no security, so only use it for prototypes.

### Usage

Get contents
`curl http://backend.local/`

Create content
`curl -X POST -d '{"foo":"bar"}' http://backend.local/`

Update or create content
`curl -X PUT -d '{"foo":"bar","bar":"baz"}' http://backend.local/95c689ea-9f42-4b89-b0ee-f4a8ea5f081d/`

Update content
`curl -X PATCH -d '{"bar":"bazzz"}' http://backend.local/95c689ea-9f42-4b89-b0ee-f4a8ea5f081d/`

Delete content
`curl -X DELETE http://backend.local/95c689ea-9f42-4b89-b0ee-f4a8ea5f081d/`


