## JQuery
```
Select element type: 	$(“H1”)
Select className: 	$(“.titles”)
Select element ID: 	$(“#addButton”)

Document.querySelector();

$("#toggleH2s").on("click", function () {
    $("h2").toggle("slow");
})
$("div").hover(
    // in callback
    function () {
        $(this).css("background-color", "CornflowerBlue");
    },
    // out callback
    function () {
        $(this).css("background-color", "");
    }
);
//hover actions:
    //table rows not equal to row zero exclude hover actions
    $('#akronInfoDiv table tr:not(:eq(0))').hover(function(){
        $(this).css('background-color', 'WhiteSmoke');
    }, 
    function(){
        $(this).css('background-color', '');
    });
<asp:Button ID=’mybutton’ onmouseover=”this.src=’/image/bluebutton.png’” onmouseout=…>
```
