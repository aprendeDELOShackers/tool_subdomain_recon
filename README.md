# _veamos algunos ejemplo_

    # _tooooooools a nombrar abajo
    Type   		Tool	          Repo	   						Language
    Passive		Amass	          https://github.com/OWASP/Amass			Go	ya
    Passive		Sublist3r	  https://github.com/aboul3la/Sublist3r			Python  ya
    Passive		crobat	          https://github.com/Cgboal/SonarSearch			Go	ya
    Passive		chaos	          https://github.com/projectdiscovery/chaos-client	Go	
    Passive		subfinder	  https://github.com/projectdiscovery/subfinder		Go	ya
    Passive		assetfinder	  https://github.com/tomnomnom/assetfinder		Go	ya
    Passive		waybackurls	  https://github.com/tomnomnom/waybackurls		Go	ya
    Passive	        gau		  https://github.com/lc/gau				Go	ya
    Passive	        github-subdomains https://github.com/gwen001/github-subdomains		Go	ya
    Passive	        findomain	  https://github.com/Findomain/Findomain		Rust	ya
    Passive	        OneForAll	  https://github.com/shmilylty/OneForAll		Python  
    Resolution/BF   shuffledns	  https://github.com/projectdiscovery/shuffledns	Go	ya
    Resolution/BF	puredns	          https://github.com/d3mondev/puredns			Go	
    Resolution/BF	dnsx	          https://github.com/projectdiscovery/dnsx		Go	
    Resolution/BF	dnscan		  https://github.com/rbsec/dnscan			Python  
    Resolution/BF	gobuster      	  https://github.com/OJ/gobuster			Go	ya
    Resolution/BF	aiodnsbrute	  https://github.com/blark/aiodnsbrute			Python  
    Resolution/BF	massdns		  https://github.com/blechschmidt/massdns		C	
    Resolution/BF	Amass	          https://github.com/OWASP/Amass			Go	ya
    Resolution/BF	rusolver	  https://github.com/Edu4rdSHL/rusolver			Rust	
    Wordlists	altdns	          https://github.com/infosec-au/altdns			Python	
    Wordlists	dnscewl		  https://github.com/codingo/DNSCewl			C++	
    Wordlists	gotator		  https://github.com/Josue87/gotator			Go	
    Wordlists	dmut		  https://github.com/bp0lr/dmut				Go
    Wordlists	dnsgen		  https://github.com/ProjectAnte/dnsgen			Python


    #Passive results
      #Tools with apis
    Tools with apis			Command
    Amass				amass enum -passive -d domain.com
    Sublist3r			python3 sublist3r.py -d domain.com | tail -n +25
    crobat				crobat -s domain.com
    chaos				chaos -d domain.com -silent
    subfinder			subfinder -d domain.com -all -silent
    assetfinder			assetfinder –subs-only domain.com
    waybackurls			waybackurls domain.com | unfurl -u domains
    gau				gau –subs domain.com | unfurl -u domains
    github-subdomains		github-subdomains -d domain.com -k -q -t .github_tokens -o result.txt
    findomain			findomain –quiet -t domain.com
    OneForAll			python3 oneforall.py –target domain.com –alive False –brute False –dns False –fmt json –path results/ run && cat results/domain.com.json | jq ‘.[] | .subdomain’

      #No apis

    No APIS			Command
    Amass			amass enum -passive -d domain.com
    Sublist3r		python3 sublist3r.py -d domain.com | tail -n +25
    crobat			crobat -s domain.com
    chaos			chaos -d domain.com -silent
    subfinder		subfinder -d domain.com -all -silent
    assetfinder		assetfinder –subs-only domain.com
    waybackurls		waybackurls domain.com | unfurl -u domains
    gau			gau –subs domain.com | unfurl -u domains
    github-subdomains	github-subdomains -d domain.com -k -q -t .github_tokens -o result.txt
    findomain		findomain –quiet -t domain.com
    OneForAll		python3 oneforall.py –target domain.com –alive False –brute False –dns False –fmt json –path results/ run && cat results/domain.com.json | jq ‘.[] | .subdomain’

      #DNS results
    #BF short === novios corto

    BF short
    Tool		Command
    shuffledns	shuffledns -d domain.com -w ~/Tools/subdomains_big.txt -r ~/Tools/resolvers.txt
    puredns		puredns bruteforce ~/Tools/subdomains_big.txt domain.com -w puredns_domain.com_bf.txt -r ~/Tools/resolvers.txt
    dnsx		-	-	-	-	-	-	-	-	
    dnscan		python3 Tools/dnscan/dnscan.py -d domain.com -w ~/Tools/subdomains_big.txt -L ~/Tools/resolvers.txt
    gobuster	gobuster dns -d domain.com -w ~/Tools/subdomains_big.txt -q -t 100
    aiodnsbrute	aiodnsbrute -w ~/Tools/subdomains_big.txt -r ~/Tools/resolvers.txt
    massdns		—	—	—	—	—	—			
    amass		amass enum -brute -d domain.com -rf ~/Tools/resolvers.txt -w ~/Tools/subdomains_big.txt
    rusolver	cat ~/Tools/subdomains_big.txt | rusolver -d domain.com -r ~/Tools/resolvers.txt


      #Baseline results === Resultado de referencia			
    BF long									
    Tool			Command
    shuffledns	shuffledns -d domain.com -w ~/Tools/subdomains.txt -r ~/Tools/resolvers.txt
    puredns		puredns bruteforce ~/Tools/subdomains.txt domain.com -w puredns_domain.com_bf.txt -r ~/Tools/resolvers.txt
    dnsx	—	—	—	—	—	—			
    dnscan		python3 Tools/dnscan/dnscan.py -d domain.com -w ~/Tools/subdomains.txt -L ~/Tools/resolvers.txt
    gobuster	gobuster dns -d domain.com -w ~/Tools/subdomains.txt -q -t 100
    aiodnsbrute	aiodnsbrute -w ~/Tools/subdomains.txt -r ~/Tools/resolvers.txt
    massdns	—	—	—	—	—	—			
    amass			amass enum -brute -d domain.com -rf ~/Tools/resolvers.txt -w ~/Tools/subdomains.txt
    rusolver	cat ~/Tools/subdomains.txt | rusolver -d domain.com -r ~/Tools/resolvers.txt
      #Baseline results


    ##########################################

    #AltPerm results

    Tools		Command
    altdns		altdns -i subdomains.txt -w permutations.txt
    dnscewl		DNScewl –tL subdomains.txt -p permutations.txt –level=0 –subs –no-color | tail -n +14
    gotator		gotator -sub subdomains.txt -perm permutations.txt -depth 1 -numbers 10 -mindup -adv -md -silent
    dmut		cat subdomains.txt | dmut -d permutations.txt –save-gen
    dnsgen		dnsgen subdomains.txt –wordlist permutations_list.txt

    #100 subs lazada.com						
    Tools		Command
    altdns		altdns -i subdomains.txt -w permutations.txt
    dnscewl		DNScewl –tL subdomains.txt -p permutations.txt –level=0 –subs –no-color | tail -n +14
    gotator		gotator -sub subdomains.txt -perm permutations.txt -depth 1 -numbers 10 -mindup -adv -md -silent
    dmut		cat subdomains.txt | dmut -d permutations.txt –save-gen
    dnsgen		dnsgen subdomains.txt –wordlist permutations_list.txt

    #500 subs lazada.com						
    Tools		Command
    altdns		altdns -i subdomains.txt -w permutations.txt
    dnscewl		DNScewl –tL subdomains.txt -p permutations.txt –level=0 –subs –no-color | tail -n +14
    gotator		gotator -sub subdomains.txt -perm permutations.txt -depth 1 -numbers 10 -mindup -adv -md -silent
    dmut		cat subdomains.txt | dmut -d permutations.txt –save-gen
    dnsgen		dnsgen subdomains.txt –wordlist permutations_list.txt


      #CONCLUTIONS
    #GANADOR
    Passive
    🥇 Amass
    🥈 Subfinder
    🥉 Findomain	

    Amass sigue teniendo una gran ventaja en cuanto a la cantidad de terceros integrados 
    y ese es un punto clave en estas herramientas, por lo que desde mi punto de vista 
    es imbatible. El resto de ganadores obtienen el puesto por el número de fuentes integradas 
    que está directamente relacionado con el número de resultados.

    #DNS resolution / DNS Bruteforcing
    🥇 Puredns
    🥈 Dnscan
    🥉 Shuffledns

    La cantidad de opciones que tiene Puredns para afinar la resolución de DNS, la rapidez con 
    la que lo hace (a costa de consumir ancho de banda) y lo centrado que está en resolver 
    subdominios de manera efectiva la convierten sin duda en la mejor herramienta de resolución 
    de DNS para pentesters y bug hunters. sin duda. Dnscan ha sido una grata sorpresa 
    para mí ya que ha logrado una estabilidad y calidad de resultados que no esperaba, mientras 
    que shuffledns creo que necesita ser revisado y mejorado en el filtrado de 
    comodines y la precisión de los resultados devueltos.

    #Alterations / Permutations
    🥇 Gotator
    🥈 Altdns
    🥉 Dmut

    En este caso, todas las herramientas del top 3 han obtenido el mismo número de 
    estrellas, por lo que tuve que revisar los resultados con más detalle. He puesto a Gotator 
    en primer lugar porque la calidad y cantidad de resultados es muy superior al 
    resto y aunque es más lento, no es un valor que me parezca tan importante como la 
    calidad del resultado. En cuanto a altdns, lo he puesto en segundo lugar por la misma 
    razón, dejando a dmut en tercer lugar.
