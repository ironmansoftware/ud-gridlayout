# UDGridLayout

Drag and drop layout control for [PowerShell Universal Dashboard](https://ironmansoftware.com/powershell-universal).

![](/images/demo.gif)

## Install

```powershell
Install-Module UniversalDashboard.GridLayout
```

## Designing Layouts

To design layouts, you should use the `-Design` parameter. It will allow you to drag and drop components that you place within the content of the grid layout. As you drag and resize components, the layout will be copied to your clipboard. You need to ensure that your components have a static ID.

```powershell
    New-UDGridLayout -Content {
        1..10 | ForEach-Object {
            New-UDPaper -Id "Paper$_" -Content { New-UDTypography -Text $_ } -Elevation 5
        }
    } -Design
```

## Using a Layout

Once you've designed your layout, you can paste the JSON into the script and assign the `-Layout` parameter. 

```powershell
$Layout = '{"lg":[{"w":7,"h":7,"x":5,"y":0,"i":"grid-element-Paper1","moved":false,"static":false},{"w":7,"h":5,"x":5,"y":7,"i":"grid-element-Paper2","moved":false,"static":false},{"w":1,"h":1,"x":0,"y":0,"i":"grid-element-Paper3","moved":false,"static":false},{"w":1,"h":1,"x":0,"y":1,"i":"grid-element-Paper4","moved":false,"static":false},{"w":1,"h":1,"x":0,"y":2,"i":"grid-element-Paper5","moved":false,"static":false},{"w":1,"h":1,"x":0,"y":3,"i":"grid-element-Paper6","moved":false,"static":false},{"w":1,"h":1,"x":0,"y":4,"i":"grid-element-Paper7","moved":false,"static":false},{"w":1,"h":1,"x":0,"y":5,"i":"grid-element-Paper8","moved":false,"static":false},{"w":1,"h":1,"x":0,"y":6,"i":"grid-element-Paper9","moved":false,"static":false},{"w":1,"h":1,"x":0,"y":7,"i":"grid-element-Paper10","moved":false,"static":false}]}'
New-UDGridLayout -Content {
    1..10 | ForEach-Object {
        New-UDPaper -Id "Paper$_" -Content { New-UDTypography -Text $_ } -Elevation 5
    }
} -Layout $Layout
```

## Allowing Users to Customize Layouts

You can use the `-Draggable`, `-Resizable`, and `-Persist` parameters to allow users to resize the dashboard. The layouts will be stored in local storage so that the next time the user visits the page, it will load it from storage. 

```powershell
New-UDGridLayout -Content {
    1..10 | ForEach-Object {
        New-UDPaper -Id "Paper$_" -Content { New-UDTypography -Text $_ } -Elevation 5
    }
} -Draggable -Resizable -Persist
```

