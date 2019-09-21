{::nomarkdown}

<html>

	<head>
<script src="https://cdnjs.cloudflare.com/ajax/libs/underscore.js/1.4.4/underscore-min.js" integrity="sha256-J4KbHSnj+1MtdhmH1AVyddHp7N0+r0tMQKKTglkLgg4=" crossorigin="anonymous"></script>
<script type="text/html" id='filterTemplate'>
      <% _.each(filters, function(filter, filterHeading) { %> 
      <div id="filterDiv-<%= filterHeading %>">
				  <b><%= filterHeading %><b> 
          <button type="button" onclick="checkUncheck('filterDiv-<%= filterHeading %>')">Select All</button>
					<button type="button" onclick="checkUncheck('filterDiv-<%= filterHeading %>')">Clear All!</button>

          <hr>
          <% _.each(filter, function(piKeys, checkBox) { %> 
          	<div id="filterDiv-child-<%= checkBox %>" onclick="checkUncheck('filterDiv-child-<%= checkBox %>')">
          	<i><input type="checkbox" disabled="disabled" value="<%= checkBox %>"> <%= checkBox %></i>
              <% _.each(piKeys, function(piKey, hiddenCheckBox) { %> 
              		<i><input type="checkbox" disabled="disabled" value="<%= piKey %>"> <%= piKey %></i> 
              <% });%>
            <hr>
            </div>
   		 		<% });%>
      </div>
 			<% });%>
</script>
<script>

	var filters = {
  "Locations": {
    "Angola": [1, 2, 3, 4],
    "Qatar": [2, 3, 4]
  },
  "Relationships": {
    "Customer": [2, 3],
    "Friends": [3, 4]
  }
}

function checkUncheck(divid) {
 var checks = document.querySelectorAll('#' + divid + ' input[type="checkbox"]');
 		console.log(checks.length);
    for(var i =0; i< checks.length;i++){
        var check = checks[i];
        check.checked = !check.checked;
    }
}
</script>

	</head>
	<body>
<div id="fiiltersDiv"></div>


</body>
	<footer>

		<script>

var template = filterTemplate.innerHTML;
fiiltersDiv.innerHTML = _.template(template, {
  filters: filters
});
		</script>
	</footer>
</html>



{:/}
