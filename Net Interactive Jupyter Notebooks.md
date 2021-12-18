
202112181552
Status: #bookmarks
Tags: #windows #system_adminitration
Content-Type:
Source: 

# Net Interactive Jupyter Notebooks

The biggest problem with scripts + sessions is a lack of data persistance. Microsoft has a new .Net Interactive, and render them on github. 

## Setting up Jupyter for Powershell
Requires
- dot net sdk
- jupyer (can be installed using anaconda)
- visual studio code (not required but recommended)

Check your Jupyter Kernels
````
jupyter kernelspec list
````
Install dot net kernel 
```
dotnet tool install --global Microsoft.dotnet-interactive
```

start your jupyter server opening a browser or remote connect through vs code. Additionaly it ties in nicely with Azure data studio.

A similar alternative it nteract.io but i prefer vscode or the web ui.

### VS code setup
```
ext install ms-dotnettools.dotnet-interactive-vscode
```

---
# Refrences
[NET Interactive is here](https://devblogs.microsoft.com/dotnet/net-interactive-is-here-net-notebooks-preview-2/)
[dot net interactive on github ](https://github.com/dotnet/interactive)

<iframe width="1266" height="719" src="https://www.youtube.com/embed/W-F0gO7dVOE" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>