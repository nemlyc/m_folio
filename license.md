# 権利表記

<p id="license"></p>

<script>
    const json = URL.create

    var rawFile = new XMLHttpRequest();
    rawFile.open("GET", "./src/licenses.json", true);
    rawFile.onreadystatechange = function ()
    {
        if(rawFile.readyState === 4)
        {
            if(rawFile.status === 200 || rawFile.status == 0)
            {
                const json = rawFile.responseText;
                const obj = JSON.parse(json);

                var str = "";

                for(i in obj){
                    if(obj[i]instanceof Object){
                        str += i + "<br>";
                        if (obj[i].copyright != null){
                            str += obj[i].copyright + "<br><br>";
                        }else{
                            str += obj[i].repository + "<br><br>";
                        }
                        str += obj[i].licenseText + "<br><br>";
                        console.log(obj[i]);
                    }
                }

                var paragraph = document.getElementById("license");
                paragraph.innerHTML = str;

            }
        }
    }
    rawFile.send(null);

</script>
