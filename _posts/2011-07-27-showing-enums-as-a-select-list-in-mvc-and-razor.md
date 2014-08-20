---
layout: post
title: Showing Enums as a Select List in MVC and Razor
date: 2011-07-27 16:03:55
categories: development
tags:
  - .net
  - mvc
  - razor
---

Recently I needed to show a drop down list of all of the enumeration values. So I did what we all do and hit up Google. While there was plenty of information out there detailing how to convert the enum to a `Dictionary<int, string>` and render it, I couldn't find something that fit my needs.

Essentially I have an enumeration of field types. I wanted to display the names of those fields in a drop down list, but be able to make some of them prettier. Here is the enumeration:

{% gist 6335482 FieldType.cs %}

Now I need a way to show the items in a drop down list, and set the selected one (from the Model) to selected. I decided the easiest way would be to use an editor template. So I created the FieldType editor template (under `/Views/Shared/EditorTemplates`) using the code below:

{% gist 6335482 FieldType.cshtml %}

Now when I want to render a `FieldType` property of an object, I can just use the `Html.EditorFor` extension as I would for any other object:

{% gist 6335482 View.cshtml %}

And Voila!

If for some reason you cannot name your editor template the same as the type, you can supply the name of the template to the EditorFor method using one of the overloads provided.

Happy coding!
