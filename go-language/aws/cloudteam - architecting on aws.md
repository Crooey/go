Tomasz Breś: tomasz.bres@cloudteam.pl
aws builder ID: https://profile.aws.amazon.com

jakubmajda95@gmail.com
T5dW5x9d6&0r8Uv%

jmajda@trans.eu
!m3C@RAJ$k941Pqf

- [https://classrooms.aws.training](https://classrooms.aws.training "https://classrooms.aws.training/") 
- [https://us-east-1.student.classrooms.aws.training/class/kpKsiMWZ7TiFoBnDDxfHPz](https://us-east-1.student.classrooms.aws.training/class/kpKsiMWZ7TiFoBnDDxfHPz "https://us-east-1.student.classrooms.aws.training/class/kpksimwz7tifobnddxfhpz")
- https://skillbuilder.aws/search?searchText=architecting-on-aws-online-course-supplement&showRedirectNotFoundBanner=true - materiały dodatkowe i dokumentacja AWS.

https://classrooms.aws.training/class/kpKsiMWZ7TiFoBnDDxfHPz

Guildy i certyfika:
https://aws.amazon.com/certification/certified-solutions-architect-associate/
https://skillbuilder.aws/category/exam-prep/solutions-architect-associate-SAA-C03


1. To szkolenie jest dla nas.
2. Zachęcamy do zadawania pytań do uczestnictwa i zadawania pytań.
3. Będziemy robić między czasie laby

- Lunch przewidywany o koło godziny 12:00.
- Między modułami będą przerwy.

Co powinniśmy wiedzieć:
- Powinniśmy wiedzieć coś o chmurze:
	- jak działają rozproszone systemy
	- jakie są rozproszone chmury
	- jak działają adresy IP, która częśc odpowiada za sieć, która za hosta. Będziemy budować VPC.

Laby:
- Od dzisiaj przez miesiąć mamy dostęp do labów i każdy lab możemy odpalić 5 razy!

VitalSource - książki / materiały szkoleniowe - warto tutaj zarejestrować się kontem prywatnym bo dodaje to wtedy ksiazki / materiały szkoleniowe - one będą dostępne przez 2 lata.

Cel kursy:
- poznanie serwisów AWS.
- sposoby łączania usług AWS, odpornych na awarie i bezpieczne.


Moduł 1: Architektura
- CTO - chief technology officer, osoba która pomoże dostosować rozwiązania architektoniczne.
- Płacimy za tyle ile wykorzystamy. Są nieliczne przypadki gdzie płacimy opłaty abonamentowe. 
- Optymalizacja  kosztów.

**Data Centers**
- Budynek w środku są serwery. To wszystko jest po stronie AWS, przechodzi on audyty, AWS artifact. Są one rozrzucone po cały świecie w obrębie lokalizacji tzw region.
- Brak zimnych DC - czyli wszystkie są działające, nie są one wyłączone.
- DC - nie mamy możliwośc wybrania w którym DC nasz EC2 / ECS gdzie będzie uruchomiony, mamy natomiast możliwość wybrania sobie AZ - availability zones. Kilka AZ będzie skupionych w tzw region. AZ będziemy mogli wybrać w przypadku EC2 i RDS. W większości przypadków będziemy mogli wybrać tylko region.
- Nie wszystke usługi będą dostępnew każdym regionie!

**Availability Zones**
- low latency
- ha

**Regions**
- Aby wybrać region to musimy sprawdzić usługi czy są dostępne w danym regionie.
- Te same serwisyw różnych regionach mogą różnić się cenami.
- Opóźnienie - to ważne w przypadku uruchomienie aplikacji w danym regionie / kraju.
- Spór prawny / rządowy.

**AWS Local Zones**
- Część infry zlokalizowana w innych miejscach np: Warszawa. Tam znajduje się tylko część usług AWS w danym local zonie. Nie wszystko można uruchomić w serwerowni w Warszawie.
- Warto sprawdzić czy SLA Local Zones jest zgodne z naszymi oczekiwaniami.

**Edge locations**
- Miejsca gdzie backbone sieciowy jest używany. Autorka maszyna Amazona, wykorzystują swoje własne światłowody, w której łączą się między serwerami. Edge Location pozwala na uruchomienie kilku usług sieciowych np: cloudflare.
- Skraca drogę przez publiczną sięc komputerową do backbone AWS.

Well-architected Framework:
- Planowanie
	- Planowanie na podstawie komunikacji z biznesem - przekłada rozwiązanei biznesowe na technologiczne.
- Reaserch
	- Sprawdza co ma zrobić aby dostosować najlepsze rozwiązanie.
	- Tworzy założenia naszego rozwiązania.
	- Po zaplanowaniu czegoś powinien być pewien, że to będzie działać, powinien iwedzieć jak posklejać odpowiendie serwisy itp.
- Budowanie:
	- Albo buduje architekt, ale jego zespół.

Decyzje arhcitektoniczne:
- Architekt bierze na klatę wszystko co jest zaplanowane i zbudowane, musi udowadniać każdemy, że jego rozwiązanie jego infy jest nieruszalne i najlepsze.
- Well-architected Frameworkj pillars, jest to dokument architektoniczny, który jest filarem środowiska.
- Well-architected tool - rozwiązanie, które pozwala zdefiniować workflow jakie chcemy zrobić (co chcemy itp), ma ono pomóc zebrać wszystkie wymagania z różnych obszarów, które potrzebujemy - definiuje kogo mamy o co zapytać zanim zaczniemy realizować aplikację. (bardziej biznesowe pytania). 

 #Lab1: Exploring and Interacting with the AWS Management Console and AWS CLI

**Komendy cli:**

Sprawdzanie bucketa s3
```
aws s3 ls
2026-04-29 16:33:55 awslabs-resources-krxqqla59sui8d-us-east-1-723263934196
2026-04-28 17:09:52 awslabs-resources-r5b3y6ojjszcap-us-east-1-723263934196
2026-09-14 09:15:48 labbucket-987981
```

Tworzenie bucketa s3:
```
sh-5.2$ aws s3 mb s3://labbucket-987981-2
make_bucket: labbucket-987981-2
```

```
aws s3 ls
2026-04-29 16:33:55 awslabs-resources-krxqqla59sui8d-us-east-1-723263934196
2026-04-28 17:09:52 awslabs-resources-r5b3y6ojjszcap-us-east-1-723263934196
2026-09-14 09:15:48 labbucket-987981
2026-09-14 09:23:07 labbucket-987981-2
sh-5.2$
```

Kopiowanie rzczy do bucketa s3:
```
aws s3 cp /home/ssm-user/HappyFace.jpg s3://labbucket-987981-2
upload: ../../home/ssm-user/HappyFace.jpg to s3://labbucket-987981-2/HappyFace.jpg
sh-5.2$
```

```
sh-5.2$ aws s3 ls s3://labbucket-987981-2
2026-09-14 09:26:20     131281 HappyFace.jpg
sh-5.2$
```

Moduł 2: Zarządzanie dostępami do kont AWS.
- AWS account root user - user który tworzony jest w momencie utworzenia konta AWS w nim podajemy dane, numer karty płatniczej ITP. Login to adres email a hasło to jest ustawione w ramach formatki. To jest jedyny user, który ma podany email, wszystkie informacje od AWSa przychodzą do niego, to jest jedyny user do zarządzania AWS - tego usera nie wolno używać do codziennej pracy! Jego używanie powinno być bardzo ograniczone.
	- Ważne aby ustawić MFA.
	- Hasło powinno składać z się 50 znaków +.
- User IAM - ten user służy do zarządzania kontem AWS.
	- AWS Identity and Access Management (IAM) - konto, które służy do zarządzania innymi kontami AWS, za jego pomocą możemy tworzyć userów, grupy userów, role IAM i możemy analizować kto z czego korzysta itp.
- Principals and identities:
	- Principals - osoba lub coś co będzie wykonywało operację na naszych zasobach AWS. Osoba fizyczna, konto IAM aplikacji, inne konto AWS. Taka osoba moża być częścią polityki, która zarządza dostępm.
- IAM users:
	- Best practices:
		- Każdy user powinien mieć swojewgo usera IAM do zarządzania swoim sektorem.
	- Do logowania się programistycznego należy utworzyć poświadczenia: Access Key ID oraz Secret Access Key.
	- Do logowania od konsoli wymagany jest: login i hasło.

**IAM Polices** - polityki IAM w nich określamy, kto i co może wykonywać na naszym AWSie. Nastepnie taką politykę możemy przypiąć do naszego usera IAM.
- Przyponamy do: IAM user, IAM group

**IAM user groups** - Sposób grupowania userów i polityk do odpowiednich grup. Do grupy możemy przypiąć userów oraz polityki. Jeden user może być w kilku grupach.

**IAM roles** - to rozwiązanie, które pozwala na zgrupowanie politykch dostępu, a potem w ramach takiej roli, że przypisany do tej roli polityuki dostępu przypiąć do zasobów w AWS. Taką rolę można przypiać do instancji EC2. To rozwiązanie pozwala na automatyczną wymianę poświadczeń. Taka instanacja EC2  wykonując połączenie s3 podpisuje własne poświadczenie w celu połączenia się do zasobów. Te role też mogą być używane przez zewnętrznych providerów np AD.

**Ważne!**
- IAM user mają poświadczenia stałe / rotacyjne!
- IAM roles automatycznie rotują poświadczenia!

Typy polityk:
- Polityki nadające uprawniania.
	- Polityka IAM, identity-based polices, są przypisywane do naszego principal. ?
	- Resource-based - to są polityki jakie mogą wykonywać nasi principale. ?
- Polityki ograniczające uprawnienia.
Doczytać o tym!

Skąd brać takie polityki?
AWS managed:
- Service access
	- AmazonEC2FullAccess - polityka pozwalająca na wykonywanie wszystkiego na EC2
	- AmazonEC2ReadOnlyAccess
- Job function
	- Billing - można sprawdzać i zarządzać bilingami
- Custom policy
	- Level9Admins
	- EasterTeam
	- Można tutaj też stworzyć własne polityki, które ograniczają poprzenie polityki.

Explicit allow and explicit deny
- Allows ("Allow") polityka która nadaje dostep i coś jest jawnie możliwe.
- Denies ("Deny") odwrotnie od ww.

![[Pasted image 20260914120611.png]]

- Czy aws loguje gdzieś te akcje?

Resource-based policy w jej politycy musimy okreslić principal np konto AWS, konkretna rola lub * wtedy każdy będzie miał dostep do zasobu.

Typy polityki:
- IAM permissions boundaries - ogranicza naszego usera, user będzie mógł wykonać operacje  na które pozwoli mu ta polityka. Ona ograniczago maksymalnie. Pilnuje tego co mogą dani userzy mogą sobie nadawać.

**Managing multiple accounts - konta AWS**
- Służy do oddzielenia teamów od siebie.
- Zapewniamy im izolację między sobą aby userzy / developerzy nie psuli coś między sobą.
- Wszystkie usługi cloudowe mają swoje ograniczenia.

Podział bez organizacji:
- root account posiada
	- IAM account
		- IAM account posiada konta AWS'owe

AWS Organizations:
- Root account / Master account - Management account - jest to konto które zarządza innymi kontami do niego można podpiąć kartę płatniczą i w ramach tego billingu inne konta OU (organizational unit) mogą korzystać z tego billingu.
- Management account -> OU -> AWS account 
![[Pasted image 20260914131241.png]]

- IAM polices można podpiąć do SCP(service control policy) (dodatkowa warstwa) za pomocą ktorej można kontrolować konta AWS i OU
![[Pasted image 20260914131403.png]]



#Moduł3 Sieci komputerowe
AWS adresuje z default  IPv4, jego IP będzie skłądał się z 2 elementów.
- 1 - to jest adres sieci
- 2 - to jest adres host

AWS wszędzie będzie wymagał podanie adresów CIDR
![[Pasted image 20260914133537.png]]

czyli **adres/maska**
jeżeli chodzi o maskę to jest możliwa w przedziale: /28 do /16

VPC - Virtual Private Cloud - prywatna kontrolowana przestrzeń sieciowa, tworząć VPC musimy podać CIDR np: VPC 172.31.0.0/16. W ramach takiego VPC jest możliwy tylko nasz ruch w naszej infrastrukturze, jest to wyizolowana na przestrzeń sieciowa rzeczy w tym VPC komunikują się tylko same ze sobą. Amazon z defaultu tworzy gotowe VPC aby można było po zalogowaniu się odrazu działać.

VPC działa w obrębie jednego regionu i może działać na wszystkie zony w ramach regionu.
![[Pasted image 20260914134119.png]]

- W podstawowej konfiguracji można zrobić 4 sieci (lub więcej) ale odnośńie ww obrazka to sieć bez routingu to nie widzą siebie między AZ.
- Sieci i podsieci muszą znajdować się w przestrzeni naszego CIDR, warto usiąść z kalkulatorem sieciowym.
- 5 adresów jest w każdej sieci rezerwowana.

Sieć jest słabo dynamiczna jeżeli chodzi o rozszerzenie. Sieć w AWS jest mało modyfikowalna i robi się problem jak mamy za mało sieci / adresów.

Public subnets - aby wyjść na zewnątrz to musimy utworzyć internet gateway nastepnie public subnet musi mić tabele routingową przekierowaną na internet gateway. Wtedy maszyna EC2 otrzyma public IP.

Internet gateway - jenda per VPC, ten internet gateway skaluje się automatycznie bez naszej ingerencji i nie będzie nigdy bottle neckiem.

Route tables - tablice routingu ustawiamy na 0.0.0.0/0 i nasz internet gateway, wtedy wszystko będzie mogło mieć wejście i wyjście na świat.
![[Pasted image 20260914135120.png]]

prywatną tablicę routing - best practice warto zostawić tak jak amazon zaproponował.

Private subnects - różnica między nimi jest taka, że ich sieć nie będzie miała wyjścia do świata zewnętrznego. W ramach tego samego VPC urządzenia będą mogły ze sobą się kominikować bez problemu.

W takich sieciach najczęściej wstawiamy:
- backend
- bazy danych
- loadbalancery

Aby wyjść na świat z takiej śieci prywatnej musimy postawić NAT gateway, będzie on miał przypisany publiczny adres IP. Można dzięki temu zagwarantować dostęp np do aktualizacji EC2 albo innej instancji.
![[Pasted image 20260914135521.png]]

NAT gateway jest płatny warto o tym pamiętać aby nie generować sobie dodatkowych kosztów.

Elastic network interface:
![[Pasted image 20260914135729.png]]

Do elastic network interface podpinamy firewall, który nazywa się security groups. Ten ENI posiada tylko jeden macadres kartysieciowej.

Elastic IP addresses - płatny
![[Pasted image 20260914135904.png]]

Wdrażanie VPC między AZ:
![[Pasted image 20260914140017.png]]

Network security:
- Network access control lists (network ACLs) - kontrolujemy jaki ruch jest wpuszczany a jaki wypuszczany. Ale nie pozwala nazarządzanie ruchem między urządzeniami.
![[Pasted image 20260914140334.png]]

- Security groups - działają na poziomie interfejsów sieciowych np przypietych do instancji EC2.
	- jest to rodzaj firwalla instancji trzymających STAN, czyli jak wpuszczamy 80/443 na EC2 to ona będzie zapamiętana. By default SG nie przepuszcza nic z zewnątrz, ale natomiast pozwala na wyjście z sieci.
![[Pasted image 20260914140729.png]]

Cała ścieżka naszego network routingu:
![[Pasted image 20260914141109.png]] 
Różnice SG i ACL:
![[Pasted image 20260914141206.png]]

### Podsumowanie modułu:
- Sieć VPC może działać tylko w obrębie jednego regionu.
- Aby sieć była publiczna trzeba ją wyroutować cały ruch przez internet gateway.
-  NAT gateway służy od wystawienia iseci z prywatnej do publicznej.
- Filtrowanie ruchu może być wykonane za pomocą: Network access control list (network ACL).
- Które porty są defaultowo otwarte?
	- Nic nie może wejść do sieci.
	- Wszystko może wyjść z sieci.

Warto powtórzyć różnicę między ACL i SG

#Moduł4 Compute

EC2 - wirtualna maszyna
- Warto wiedzieć zanim uruchomimy: 
	- Co chcemy uruchomić na tych innstancjach, jakie to mają być systemy, czy mają być licencjonowane.
	- Aby uruchomić taką instancję musimy wybrać miejsce sieciowe w którym mają być one uruchomione.
	- Jakie powinny mieć dysku czy jeden czy dwa i w zależności jakie to powinny być dyski.
- Tags
	- Pomagają w zarządzaniu w AWS.
	- Pozwala na szybką identyfikację zasobów / instancji.
	- Jest dodatkową bazą metadanych aby ułatwić sobie zarządzanie.
	- Za pomocą tagów możemy też sterować security.
- AMI
	- W momencie wybrania OS używamy Amazon Machine Image (AMI), za jego pomocą mamy zdefiniowane jakie dyski mamy przypięte do instancji. Są one defaultowo preconfigurowane, jeżeli nie chcemy używać gotowców to konfigurujemy sobie własnego.

Rozpiska instancji:
![[Pasted image 20260914145647.png]]

![[Pasted image 20260914145831.png]]

AWS Compute Optimizer - tool defaultowo wyłączony przez amazona, można za jego pomocą zoptymalizować swoje EC2, pozwala na redukcję kosztów, analizuje workload, instancję ECS/EC2/Lambda - jest dodatkowo darmowy.
![[Pasted image 20260914150337.png]]

Amazon EC2 key pairs.
- Para kluczy jest generowana na maszynie, zostawiamy sobie klucz prywatny a na EC2 zostawiamy publiczny i możemy go wrzucić do repo, albo EC2 itp.

Tenancy:
- Shared tenancy - nasze instancje EC2 działają sobie obok instancji innych klientów na tym samym hoście (to jest nasze default).
- Dedicated Instance - pozwala na wygonienie innych instancji klientów ze swojej przestrzeni serwerowej w racku AWS. Opcja płatna oddatkowo.
- Dedicated Host - dedykowany host w serwerowni AWS - tutaj mamy do dyspozycji cały serwer fizyczny. Różni się tym, że w tym dostajemy HostID i jest to potrzebne w sytuacji, że warunbki regulacyjne muszą mieć informację na jakim hardware jest coś uruchomione.

Placement groups and use cases:
- Sposób rozmieszczenia instancji EC2 w serwerowniach AWS w zależności od tego jaki mamy typ instancji.
	- Cluster - w obrębie jednego racka w przestrzeni AWS.
	- Spread - rozrzucone instancę po jak najdalszych kontach serwerowni AWS.
	- Partition - grupowanie instancji w klastry, ale rozrzucamy te klastry w róznych częściach serwerowni, ma to zapobieć awariom bloków.

User data:
- Co ma się dziać z naszą instancją kiedy pierwszy raz uruchomimy nasz EC2. Np skrypt autostart.
	- cloudinit - linux
	- etctoolaunch? - windows ?

Instanc metadata:
- Każda instancja wystawia swoje metadane i jest to dostępne wewnątrz instancji.
- Pomaga to np z wyciągnięciu rzeczy z instancji np w jakim AV jest uruchomione jakie ma publicze IP itp. Potrzebne to jest np dla autokonfiguracji AMI.

Amazon Elastic Block Store (EBS)
- Są to dyski, które można podłączyć od EC2, mogą one być przepinane między VM. Dodatkowo kilka dysków może być podpiętych do tej samej instancji.
- Typy wolumentów:
	- EBS SSD-backed volumes
		- dysku generacji gp3 są tańsze niż generacji gp2
		- maksymalna ilość IOPS w gp2/3 to jest 16 000 wejść i wyjść.
		- jak chcemy więcje to musimy dokupić IOPS SSD (io1, io2 Block Express)
	- EBS HDD-backed volumes
		- dyski tależowe dają mniejsze i niższe parametry IOPS - low cost
		- st1 i sc1

Instance store volumes:
- Są to dyski, które są bezpośrednio podpiętę do serwera na którym działa nasze EC2.
- W momencie kiedy zatrzymamy instancję EC2 to nasze te dyski są kasowane i czyszczone.

Amazon EC2 purchase options:
- On-Demand - cennik do niczego nas nie zobowiązuję, płacimy tylko za to ile zasobów (czasu) zużyliśmy.
- Spot Instances - moce przerobowe w serwerach aws, które nie są używane przez AWS, możemy dzięki temu dostać instancję EC2 działającę przez AWS o 90% taniej. Nasza instancja może zostać zatrzymana w momencie jak jakiś klient wykupi On-Demand EC2.
- Savings Plans - możemy zaoszczędzić na EC2, ale dopiero w momencie jak chcemy współpracować z AWS.
	- Compute savings plans - EC2, AWS Fargate, AWS Lambda - możemy zaoszczędzić do 66% ceny. TZW zniżka, którą możemy kupić w wybranym przez znas regionie.
	- EC2 Instance Sacing Plans - tylko zniżka do EC2 do 72%, mniej elastyczny.

 EC2 Spot Instances - fajne narzędzie do EC2, które działają chwilę np:
 - pipeline
 - image and media rendering
 - web services
 - big data an analytics

Przykład jak można połączyć te wszystkie sposoby rozliczania EC2 w celu optymalizacji kosztów:
![[Pasted image 20260914153416.png]]

Serverless computing - przydatne do uruchomienia tylko kawałka kodu.
Do tego jest wymagany serwis Lambda. Za jego pomocą możemy tworzyć fukncję lambda. Jej funkcja nie może działać więcej niż 15 minut. Jeżeli działa więcej niż 15 minut to lambda nie jest odpowiednią funkcja dla nas. Dodatkowo może ważyć tylko maksymalnie 10 GB.

Kod ładujemy do -> Lambda -> Lmbda wykonuje funkcję -> Wykonaj np: uderzenie do endpointów aby pobrać dane. Wykonuje się i koniec.

Event source examples:
- Cloudwatch
- EventBridge
- Step Functions
- S3
- Application Load Balancer
- API Gateway
- DynamoDB
- Data Firehose
- Simple Notification Service (Amazon SNS)
- Config
- CloudFormation
- Simple Queue Service
- Amazon Kineses

Gdzie z tego można korzystać:
- Backends
- Amazon Alexa
- IT automation
### Podsumowanie modułu
- za pomocą AMI możesz:
	- Uzyskać informację odnośnie maszyny EC2
	- Możesz uruchomić kilka instancji EC2
- która część określa generację instancji EC2:
	- 8 - numer
	- g - gravitony
- Lambda może maksymalnie operować na 10GB i trwać do 15 minut.
# 15.09.2026

#Moduł5 Storage

- Block storage (Amazon EBS) - blokowe składowanie danych, HD, storage area, SAN, storage arrays - dyski bezpośrednio podłączone do naszych serwerów.
- File storage (Amazon EFS) - dyski, które sa podłączone sieciowe za pomocą NFS, SAMBA, iSCASI, które można podmonotwać w naszych serwerach lub komputerach. Wymagane podpięcie compute / serwisu
- Object storage (Amazon S3 / Amazon S3 Glacier) - standalone umożliwia przechowywanie danych wysyłania ich i trzymania w storage. Do Glaciera wrzucamy dane, które chcemy trzymać bardzo długi czas.

### S3
Jest to serwer webowy, który przechowuje nasze dane / pliki, można w nim bez problemów zrobić w nim backupy, migracje danych itp. Tam gdzie chcemy trzymać duże ilości danych a nie chcemy podpinać dodatkowego dysku. S3 ma nieograniczoną przestrzeń do przechowywania danych, aczkolwiek limitem jest to, że pojedyńczy obiekt nie może mieć więcej niż 5TB.
- Nazwa wiaderka (S3 bucket) musi mieć unikatową nazwę
- Każde S3 dostaje własne unikatowe URL
- Wiaderko można podzielić na kilka katalogów czyli na tzw prefix.

Przykładowe użycie S3:
- Back and restore
- Data lakes for analytics
- Media storage and streaming
- Static website
- Archiving and compliance

Zabezpieczenie:
- By default wszystkie wiaderka w S3 są prywatne, tylko userzy w roli IAM będa mogli wykonywać akcję na tych wiaderkach.
- Można sprawić aby wiaderko S3 było publiczne.
- Można kontrolować dostęp do S3, do ich kontroli wykorzystuje się politykę: **Resource-based policy** lub Bucket policy, taka polityka pozwala na anonimowy dostęp do takiego wiaderka.

S3 Access Points
- Polityka wiaderka S3 ma ograniczenia, taka polityka jest często za mała, a z błędem na poziomie tej polityki można było łatwo zabrać komuś dostepy do prefixów danego S3.
- Za pomocą access pointa możemy nadać dostęp do odpowiednich uprawnień dla pojedyńczej osoby lub całego zespołu ten access point ma przypisany access policy.
- Do każdego access pointa dostajemy odpowiedni URL do korzystania z S3.

Szyfrowanie:
- Każdy S3 ma właczone szyfrowanie za pomocą kluczy SSE-S3, ale najczęściej tworzy się parę kluczy AWS KMS Keys (SSE-KMS), taki klucz można udostępnić innym kontom AWS aby pozwolić na udostępnienie kontom dostępu do S3
- DSSE-KMS - Dual-layer server-side encryption - dwa oddzielne klucze z dwoma oddzielnymi politykami.
- Customer-provided keys (SSE-C) - udostępnienie własnego klucza szyfrującego, na S3 można przechowywać swoje dane ale zaszyfrowane przez nas już.

Przechowywanie obiektów
- Storage classes
![[Pasted image 20260915094459.png]]

![[Pasted image 20260915094419.png]]

- Długo terminowe przechowywanie plików to najlepiej jest używać S3 Glacier Deep Archive.

Wersjonowanie w S3:
- działa w taki sposób, że jeżeli nadpiszemy obiekt pod takim samym kluczem to tworzony jest obiekt takiego pliku i pozwala to na trzymanie historii zmian takiego pliku + chroni nas przed przypadkowym usunięciem takiego pliku. Co generuj jednocześnie większe koszta za te pliku. Im wiecej plików tym więcej płacimy za przechowywanie.

Lifecycle polices:
- Dzięki temu możemy przerzucać dane między storage, możemy tutaj kontrolować np żywotność tych plików, np 5 wersji danego pliku może być przechowywane i np po 30 dniach z S3 plik może trafić do Glaciera.

Replikacja obiektów:
- Możemy robić backup wiaderka lub backup plików w S3.
- Można też na tym samym konce zrobić replikację do innego regionu.
- Możemy zrobić backup innego wiaderka do innego regionu dla innego konta w AWS!

S3 multipart upload
- W momencie ładowania dużych plików do S3 plik dzieli się na kilka części obiektu, co przekłąda się na szybsze ładowanie plików i zemniejsza awaryjność wysyłania plików.

S3 Transfer Acceleration
- Przyśpiesza transfer za dodatkową cenę

S3 Event Notifications
- Pozwala na uruchomienie jakiś procesów kiedy pojawia się pliki w naszych wiaderkach.
- Może to np uruchomić funkcję lambda, która może zmienić pliki albo ich rozmiar, nazwę, rozdzielczość itp.

S3 cost factor
- Płacimy za:
	- Ilość danych przechowywanych w wiaderkach. Im niższa storage class tym niższa kwota.
	- Za operację: wkładania danych i wyciągania ich.
	- Wersjonowanie obiektów.
	- Replikację.
	- S3 insight - Management and analytics - jest wersja darmowa albo można ją płatnie rozszerzyć.

S3 Express One Zone
- Nowa storage klasa, która przechowywane jest na jednym Availability Zone, oferuje ona tylko szybkość dostępu.

Amazon EFS - Shared file systems - współdzielona przestrzeń plików
- EFS - tworzymy sobie wolument w EFS, on automatycznie replikuje dane we wszystkich Avability Zones w naszym regionie. Tworzymy mount targety w naszych podsieciach w danym VPC.
- Za pomocą takich mount target możemy za pomocą CLI w EC2 podpiąć je sobie.
- Możemy go współdzielić między wieloma instancjami.
- Płacimy za ilość przechowywanych danych w EFS.
- Brak limitu pojemności.
- Można modyfikować koszt takiego EFS przez zmiany storage klasy.

FSx - głównie pod windowsy
![[Pasted image 20260915100827.png]]

Data migration tools
- AWS Storage Gateway
	- Lokalny appliance, towrzymy lokalną przestrzeń do storage gateway w serwerowni i przycamy go do naszego gateway aws w naszym serwerze a on przerzuca to do AWS.
- AWS DataSync
- AWS Transfer Family
	- S3, stary format, który stosuje SFTP, FTPS, FTP i AS2
- AWS Snowball Edge (offline)
	- Skrzynka danych zamawiane przez AWS do którego ładujemy dane i kurier potem zabiera to i wgrywają do AWSa.

#Moduł6 - Databases Services
![[Pasted image 20260915103956.png]]

![[Pasted image 20260915104230.png]]

![[Pasted image 20260915104440.png]]

RDS - relational database service
- Takie bazydanych są przygotowane w sposób prekonfigurowane jeżeli chodzi o security i patche.
- Możemy wymusić szyfrowane połączenia do bazydanych.
- Automatyczna odpłatna replikacja.
- Wybieramy resourcy dla tej bazydanych i jaka ma być przestrzeń dyskowa dla takiej bazydanych.

Wsparcie:
 - PostgreSQL
 - MySQL
 - MariaDB
 - Orcale
 - SQL Server
 - Db2
 - Aurora - rozwiązanie AWS przygotwane do współpracy jako PostgreSQL i MySQL

RDS Multi-AZ deployments
- Tam gdzie jest wymagany wymóg dostępności to można uruchomić przez AWS 2 instancji bazdanych w wybranych przez nas AZ.
- Jedna baza jest masterem, druga jest replikacją w trybie standby - postronie AWS zapowniona jest replikacja 1:1 między dwoma bazami danych.
- Zwiększa koszt działania bazydanych dwukrotnie.
![[Pasted image 20260915105324.png]]

Read replicas
- Do baz uruchomionych w RDS możemy utworzyć read replica - pozwala na odczytanie danych jako replikacja. Pozwala na odciążenie mastera od zapytań.

Data encryption at rest
- Szyfrowanie za pomocą kluczy KMS, tworzymy sobie klucz kms i szyfrujemy nim dane przechowywane na dyskach z naszymi bazami danych.

Aurora
- Bazadanych, która jest zgodna z PostgreSQL i MySQL, rozdziela warstwę silnika i storage, wpełni zarządzane przez AWS dostpne w trybie serverless.
- Jego klaster możemy rozciągnąć na większą ilość AV zones dla zapewnienia wysokiej dostępności bazdanych.
- Możliwość uruchomienia jej w trybie on demand.
- Płacimy za to co używamy.
- Automatyczne skalowanie do przychodzących zapytań bazy danych.

DynamoDB
- Nierelatywna bazdanych w której nie twrzymy tabelek tylko klucze - wartość.
![[Pasted image 20260915110128.png]]

- Przechowujemy JSON obiekty w takich bazach danych: key:value.
- Możliwość zakładania indeksów.
![[Pasted image 20260915110330.png]]

- Rozliczanie:
![[Pasted image 20260915110647.png]]


- Best practics:
	- Warto ustawić na początku na On-demand, przeanalzować zurzycie i potem przełączyć się na tryb: Provisioned
- DynamoDB consistency options:
![[Pasted image 20260915110820.png]]

- DynamoDB global tables
	- Pozawala to na replikowanie danych i bazdanych w różnych regionach świata.
![[Pasted image 20260915111020.png]]

Cache
- Cachowanie pozwoli nam na mniejszenie zużycia bazdanych i pomoże nam to w oszczędnościach dla bazydanych.
- Trzeba się zastanowić nad cachowaniem odpowiednich danych.

Cache architecture
- Możemy wrzucić klaster cache, który będzie replikował się między aplikacjami / obok bazdanych w różnych AV.
- Lazy loading - jeżeli coś jest w cache to dostajemy odpowiedz od cache, jeżeli czegoś nie ma to uderzenie leci do bazydanych. Tutaj mamy dane o które przedchwila userzy pytali.
- Write-throught - zapisujemy jednocześnie do bazydanych i do cache. Pozwala to nam na przechowywanie najświeższych danych.

Managing cache
- Warto wiedzieć jakie treści należy cachować oraz jak długo mają być cachowane

Amazon ElastiCachce
- Mamy do dyspozycji:
	- redis
	- memcache ??? - doczytać

DAX - DynamoDB Accelerator
- Wbudowany cache dla DynamoDB.
![[Pasted image 20260915111535.png]]

- Warto wiedzieć co cachować i jak długo powinniśmy trzymać tego cache. 

Migracja Danych - AWS Database Migration Service
- Możemy migrować do AWS i z AWSa do On-premises
- Dzięki niemu możemy migrować bazydanych i replikować je między serwerami On-premises i AWS.
- Sprawdza on czy możemy też wykonać taką migrację, weryfikuje problemy i wykonuje migrację bazydanych.

Schema Conversion Tool:
- Tool do migracji bazdanych, pozwala na takie migracje.
- Płacimy głównie za zućyte capacity i unity.

Lab 3:
writer-endpoint: aurora.cluster-cd2zfl6xviz3.us-west-2.rds.amazonaws.com
reader-endpoint: aurora.cluster-ro-cd2zfl6xviz3.us-west-2.rds.amazonaws.com

#moduł7 Monitorowanie i autoskalowanie

CloudWatch - tool AWS'a do metrykowania rzeczy z możliwością tworzenia eventów w zależności od eventów.

Typy logów:
- CloudWatch Logs
![[Pasted image 20260915131658.png]]
- CloudTrail - można sprawdzić jakie operacje wykonują ludzie na poziomie konta AWS. By default przechowuje on logi przez 90 dni. Dodatkowo CloudTrail jest defaultowo włączony w naszej infrastrukturze. logowne głównie jest: kto co zmienił, co zmienił i gdzie zmienił.
![[Pasted image 20260915132007.png]]
- VPC FLow Logs - logi sieciowe.
![[Pasted image 20260915132819.png]]
- Flow logs będą tyllko logować pakiety jakie przeszły przez naszą sieć, niestety nie będzie mirrorowanego ruchu! Fajnie się sprawdza w momencie weryfikacji naszego ruchu czy nie jest gdzieś coś poblokowane z poziomu security group lub acl.
![[Pasted image 20260915132843.png]]
- Access Logs - logi na poziomie S3, loadbalancerów itp.
- Custom Logs - Logi, które można wrzucać do CloudWatcha, ale trzymanie ich w S3.

EventBridge - eventy publikowane przez AWS, pojawiają się w nich informacje, że jakiś alarm został wyzwolony albo zgaszony, lub coś stało się z polityką naszego wiaderka S3. Dzięki niemu można również odpalać procesy wyzwalane przez alerty.
![[Pasted image 20260915133904.png]]

![[Pasted image 20260915133921.png]]

### Loadbalancing

Elastic Load Balancing (ELB) - loadbalacner co daje na to:
- Pojedyńczy punkt wejściowy klienta do naszej aplikacji.
- W ramach serwisu ELB możemy uruchomić 3 typy load balancingu.
	- Application Load Balancer - warstwa 7 - HTTP / HTTPS.
	- Network Load Balancer - warstwa 4 - TCP / UDP. Jako jedyny posiada stały adres IP.
	- Gateway Load Balancer - warstwa 3, służy głównie do tego aby uruchmić dla firma trzecich inspekcję na poziomie sieci i protokołu: IP
		- Fortinet itp
- ELB load balancer components składa się z:
	- Listener - porty na jakim loadbalancerze będą działały i w nim konfigurujemy target do którego ma trafić.
	- Target group - grupy targetów - worki do której trafiają pakiety.
![[Pasted image 20260915134639.png]]

### Autoscaling
AWS Auto Scaling
![[Pasted image 20260915134928.png]]

![[Pasted image 20260915135006.png]]

Auto Scaling group - będzie bazowała na health checkach, są 2 rodzaje i defaultowo przychodzą one od hypervisoriów. Można dodatkowo wykorzystać spięcie z load balancerem może sprawić aby przy błędzie podniesieniu EC2 / ECS kiedy jest unhealthy to może wysłać takie informację dla scaling groupy.

![[Pasted image 20260915135512.png]]

Launch template
![[Pasted image 20260915135556.png]]

Group capacity
![[Pasted image 20260915135652.png]]

Scaling methods
![[Pasted image 20260915135829.png]]

- Fixed - ustawiamy desigre ktora okresla ile mamy maszyn 1, 2 lub 6.
- Manually - ręcznie ustawiamy.
- Scheduled - harmonogram, ustawiamy, że o 7:30 odpalone zostają maszyny i kończą się o 16:00
- Dynamically - na podstawie eventów, że potrzeba dostawić coś np. Tutaj trochę więcej zabawy jest bo trzeba to połączyć z monitoringiem i na jego podstawie dostosowywać Load Balancing do skalowania.
- Proactive - automatyczna na podstawie danych historycznych próbujemy przewidzieć ile potrzebujemy compute na dany moment.
![[Pasted image 20260915140108.png]]

Optymalizacja kosztu EC2 auto scaling
![[Pasted image 20260915140236.png]]

- Jeżeli instancja spot zostanie nam zabrana to AWS dostawi nam nowy spot, ale aplikacja zostanie zatrzymana, w tym przypadku warto mieć miejsce przechowywania stanu poza tą instancją - np. w Dynamodb.

#Lab4
```
#!/bin/bash #yum -y update dnf update -y dnf install -y httpd wget php-fpm php-mysqli php-json php php-devel # Install and enable AWS Systems Manager Agent cd /tmp systemctl enable amazon-ssm-agent systemctl start amazon-ssm-agent # Download Inventory App Lab files wget https://us-west-2-tcprod.s3.us-west-2.amazonaws.com/courses/ILT-TF-200-ARCHIT/v7.12.4.prod-4a58a96a/lab-4-HA/scripts/inventory-app.zip unzip inventory-app.zip -d /var/www/html/ # Download and install the AWS SDK for PHP wget https://us-west-2-tcprod.s3.us-west-2.amazonaws.com/courses/ILT-TF-200-ARCHIT/v7.12.4.prod-4a58a96a/lab-4-HA/scripts/aws.zip unzip aws -d /var/www/html unzip /var/www/html/aws.zip -d /var/www/html/ # Load Amazon Aurora DB connection details from AWS CloudFormation un="dbadmin" pw="lab-password" ep="inventory-cluster.cluster-covimzn9lqv4.us-west-2.rds.amazonaws.com" db="inventory" # Populate PHP app settings with DB info sed -i "s/DBENDPOINT/$ep/g" /var/www/html/get-parameters.php sed -i "s/DBNAME/$db/g" /var/www/html/get-parameters.php sed -i "s/DBUSERNAME/$un/g" /var/www/html/get-parameters.php sed -i "s/DBPASSWORD/$pw/g" /var/www/html/get-parameters.php # Turn on web server systemctl enable --now httpd
```


#Moduł8 Automatyzacja
![[Pasted image 20260915151502.png]]

![[Pasted image 20260915151553.png]]

Zasady:
- Robimy zmiany w template.
- Liczymy się z tym, że te zmiany mogą nabrudzić conieco.

CloudFormation
- Rozwiązanie AWS.
- Piszę się template w YAML lub JSON, grupuje to do stacka z różnych resourcesów.
- Jest ona przechowywana w stacku CloudFormation - co jest jednocześnie dobrą i złą wiadomością.
- Nie ma w nim pliku stanu! W przeciwieństwie do terraforma.
![[Pasted image 20260915152008.png]]

- Jeżeli coś pójdzie nie tak to CloudFormation może przywrócić poprzedni stan środowiska.
- CloudFormation może używać wielu templates
![[Pasted image 20260915152154.png]]

- Jak chcemy poprawić coś w backendzie to fajne jest to, że tylko warstwa backendowa się zmienia bez modyfikacji niższych warstw, in niżej tym bardziej affectować można na powyższe rzeczy.

Zarządzanie infrą (Infrastructure tools):
- AWS Elastic Beanstalk
	- To jest rozwiązanie, które bardzo szybko pozwoli nam na szybkie uruchomienie infrastryktury np: serwer webowy.
![[Pasted image 20260915152520.png]]

- AWS Solutions Library https://aws.amazon.com/solutions/
	- Gotowce od AWS'a.
	- Są opisane i odukomentowane.
![[Pasted image 20260915152844.png]]

- AWS CDK
	- Głównie zamienia naszą infrastrukturę w kawałek aplikacji w ramach napisanego przez nas kodu.
![[Pasted image 20260915152920.png]]

- AWS Systems Manager
	- Pozwala na wykonywanie operacji na infrastrukturze AWS.
	- Zbieramy zap omocą CloudWatch agenta inforamcję odnońśie dysków z instancji EC2, taki agent buduje metryki o raporcie dysków podpiętej do instancji, w momencie przekroczenia wartości uruchamia system manager autoamtion i w jego zadaniach wykonuje operacje: zwiększenie dysków w EBS np. Kiedy serwis EBS zaraportuje, że jak powiedziony jest powiększony dysk to uruchamia system managera na hoście i rozszerza FS o dodaną pamięć dysku EBS.

- Amazon Q
	- Amazon Q przestaje żyć - ten serwis zostanie zamknięty przez Amazona.
	- Pozwalał on na pracę z kodem naszym i wspierał w pisaniu kodów dla developerów.
	- Pracował też jako helpdesk.
	- Zostanie zastąpiony przez Amazon Kiro.
![[Pasted image 20260915153514.png]]

#Moduł9 Kontenery
![[Pasted image 20260915154417.png]]

![[Pasted image 20260915154614.png]]

- Każdy taki mikroserwis można łatwo skalować.
- Można pisać w dowolnym języku.

Konteneryzacja
- W domyśle kontenery są w silniku dockera.
- Dobrze jest przewidzieć, albo zaplanować skalowalność tych kontenerów.
![[Pasted image 20260915155147.png]]

![[Pasted image 20260915155438.png]]

![[Pasted image 20260915155722.png]]

- Aby uruchomić kontenery na AWS mżemy uruchomić EC2 z dockerem albo inny orchetratr
- Albo możemy wykorzystać gotowca w ramach dostępnych w AWS usług.

ECR - Amazon Container Registry
- Amazonowy odpowiednik Registery np: Harbor
- Do niego możemy ładować obrazy dockerowe
	- Amazon inspector - może przeskanować obrazy z ECR i sprawdzić je pod kątem bezpieczeństwa i wykonać raport bezpieczeństwa obrazu.
- Rejestr kontenerów, tagujemy obrazy i możemy wyciągać konkretne obrazy.
- Tworzymy tyle repozytorium ile tylko potrzebujemy, będzie ono przechowywało różne wersje kontenera.

EKS - Elastic Kubernetes Service
ECS - Elastic Container Service

Są 2 opcje uruchomienia takich kontenerów:
- EC2, na niej stawiamy silniki kontenerów i za pomocą klastra możemy rozrzucać kontenery na te hosty.
- AWS Fargate - pozwala na pozbycie się części odpowiedzialnej za zarządzanie VM. Podpinamy go do VPC, ile chcemy mieć zasobów: RAM, CPU jaka sieć i gotowe. Wszystko dzieje się samo podspodem.

![[Pasted image 20260915160731.png]]

![[Pasted image 20260915160933.png]]

![[Pasted image 20260915161030.png]]

EKS - Kubernetes
![[Pasted image 20260915161117.png]] 
![[Pasted image 20260915161136.png]]

- Minusem tych rozwiązań K8s to, że bardzo rzadko są one dostepn w najnowszych wersjach. Dostarcza je AWS a nie aktualizuje go on na bierząco. Niezgodność wersji tworzy więcej problemów niż to jest warte.

AWS Fargate
- Uruchamiamy sobie nasze kontenery w naszej przestrzeni AWS.
- Przypisujemy mu kontenery, które będą zarządzane przez AWS.

Wybór:
![[Pasted image 20260915161519.png]]

# 16.09.2026

#Moduł10 Networking 2

**VPC endpoints** - pozwalają na towrzenie interfejsów sieciowych w naszych subnetach, dzięki którymi możemy dostawać się przez sieć prywatną
![[Pasted image 20260916091107.png]]

Dzięki endpointom w VPC możemy zawinąć ruch do innego endpointu VPC dzięki temu mamy dostępny ruch do innego VPC do innej maszyny / usługi dzięki temu nie wychodzimy na świat.

**Gateway VPC endpoints**
![[Pasted image 20260916091305.png]]

Taki endpoint jest dostępny tylko dla serwisów s3 i dynamodb.

Za taki endpoint aws nie będzie chargował dodatkowych kosztów do tych dwóch serwisów po wewnętrznej sieci.

**Interface VPC endpoints** - płatne ale umożliwiają na ruch dla każdego serwisu awsowego.

Te rozwiązania nazywają się AWS private link

**VPC peering** - łączenie VPC między sobą.
- Takie rozwiązanie można stosować w obrębie jednego konta AWSowego, ale także można połączyć z innym VPC w innym regionie.
- Istotną rzeczą jest to, że adresy sieciowe VPC nie mogą się pokrywać!
- Peering VPC działa tylko między dwoma sieciami VPC! Czy VPCA połączymy z VPCB i VPCB z VPCC ale VPCA i VPCC już nie połączymy.
- Przez takie peerowanie zyskujemy połączenie między regionami.
- Takie połączenie jest zawsze dostepne i nie generuje bottle-necków.
- Możemy używać prywatnych adresów sieciowych aby komunikować się między serwisami.
![[Pasted image 20260916092111.png]]

![[Pasted image 20260916092237.png]]

**Transit Gateway** - nowy tool AWS, który pomaga na połączenie wielu VPC i on-premises środowiska w bardzo łatwy sposób.

![[Pasted image 20260916092400.png]]

![[Pasted image 20260916092448.png]]

Przygotowanie:
- Budujemy Transit Gateway a potem przypinamy do niego  attachmenty:
	- VPC
	- VPN connection
	- Direct Connect gateway
	- Transit gateway peering

![[Pasted image 20260916092725.png]]

Pełne połączenie:
![[Pasted image 20260916092757.png]]

Częściowe połaczenie:
![[Pasted image 20260916093002.png]]

Izolowane:
![[Pasted image 20260916093024.png]]


**Site-toSite VPN** - za pomocą Virtual private gateway, możemy skonfugurować VPNa.
- On-premises VPN server łączy się do Customer gateway device (po naszej stronie serwerowej to może być fizyczne / vm urządzenie) po stronie AWS to jest adres IP który łączy się do VPC.
- Wymiana kluczy dzieje się po stronie Virtual private gateway.
- Sposób szyfrowania ustawia się między Customer gateway device a Virtual private gaateway.
- Takie połączenie ma ograniczoną przepustowość. 1,25GBps, ostatnio doszła zmiana, o możliwości 5GBps. Jak się zepnie kilka tuneli VPN.
- Dodatkowo połączenie jest organizowane publicznie.

**AWS Direct Connect** - pośrednik, Direct Connect Partner jest to dostawca, który ma bezpośrednie połączenie do chmury AWS. Możemy dzięki temu stworzyć w pełni prywatne połaczenie naszej infry do AWS'a.

![[Pasted image 20260916094222.png]]

- W momencie kiedy używamy VPN'a to mamy standardowe opłaty za wyciąganie danych z usług AWS, 10 centów / 1GB.
- W momencie kiedy używamy direct connect to opłaty są 3 razy tańsze.

![[Pasted image 20260916094528.png]]

![[Pasted image 20260916094629.png]]

#Moduł11 **Serverless** - z punktu naszego widoku to są rozwiązanie za których infrastrukturę nie odpowiadamy, zarządzaniem skalowaniem, ha itp zajmuje się dostawca takiej usługi, najczęściej opłaty mamy za zużycie używania takiej infry. By default mamy wbudowane całe security itp.

**AWS serverless portfolio**
- AWS Lambda
- AWS Fargate
- Amazon API Gateway
- S3
- DynamoDB
- Aurora
- Amazon Cognito
- Amazon Simple Notification Service
- Amazon Simple Queueu Service
- Amazon Kinesis
- Amazon Athena
- itp
## doczytać jeszcze raz od tego aktu
Ponieważ ptaszek uderzył w okno i nie byłem w ogóle skupiony na tej części prezentacji.>

Przykład architektury serverless:
![[Pasted image 20260916100241.png]]

Przetwarzanie rzeczy za pomocą kolejki jest asynchroniczne.

**API Gateway** - dostarcza nam endpoitn do którego mozemy uderzać z naszej aplikacji.
![[Pasted image 20260916100353.png]]

![[Pasted image 20260916100705.png]]

**Amazon SQS** - kolejki AWS w ramach takiego serwisu mamy nieograniczoną możliwość kolejkowania.
- Wiadomości żyją tak długo ile ustawimy wielkość tej kolejki.
- Przechowuje wiadomość tak długo do póki nie skasujemy takiej wiadomości, manualnie lub ręcznie.
- Używamy kolejki tam gdzie ilość eventów jest generowana w dużej ilości w naszej aplikacji.

![[Pasted image 20260916101028.png]]

![[Pasted image 20260916101312.png]]

![[Pasted image 20260916101436.png]]

![[Pasted image 20260916101731.png]]

Optymalizacja kolejki:
- Nasz konsument będzie konsumował sobie naszą kolejkę, strzela on do API może z niej wyciągnąc wiadomości. Do 10 wiadomości SQS w tamach jednego batcha. Kiedy wyciągamy lub nie wyciągamy wiadomości z kolejki to płacimy AWSowi.

![[Pasted image 20260916102007.png]]

**Amazpm SNS** - serwis, który może wysyłać jedną wiadomość do wielu osob. Jest to serwis typu push, który wysyła wiadomości do zasubskrybowanych osób.
- Zaastosowanie:
	- Powiadomienia CLoudWatch alarm notification
	- Push notifications for app updates.
	- Email and SMS messages.
- To co wrzucimy do topic SNS to nie można go odwołać. W przeciwieństwie do kolejek, które można w każdej chwili jeszcze odwołać.
- Jedyne co można zrobić to wysłać kolejną wiadomość do subskrybnentów z przeprosinami.

![[Pasted image 20260916102423.png]]

Połączenie jedno z drugim:
![[Pasted image 20260916102645.png]]

![[Pasted image 20260916102751.png]]

**Amazon Kinesis** - zbieranie i analizowani danych strumieniowych.
- Kinesis Data Streams - zbiera i przechowuje dane z źródeł w celach analizy.
- Logi aplikacji.
- Ruchy myszki na stronie itp.![[Pasted image 20260916102913.png]]

**Kinesis Firehose**
![[Pasted image 20260916103210.png]]

- Stosuje się w przypadku bardzo dużej ilości danych i przetwarzania ich.

**Step Functions** - serwis, które orkiestruje przepływ naszych procesów, który będzie zarządzał róznymi serwisami.
![[Pasted image 20260916103643.png]]

![[Pasted image 20260916103656.png]]

![[Pasted image 20260916103725.png]]

Przykład zabijania instancji EC2
![[Pasted image 20260916103947.png]]
tutaj trzeba mieć ustawiony ttl w tej instancji EC2.

- Takie inforamcje w EC2 pojawią się w zakładce Executions.

Doczytać odnośnie Stanów i Step Functions.

W przypadku OOM Killer - na takiej maszynie można zainstalować cloudwatch agenta i pokazać temu cloudwatchowi agena, że któryś plik z tegocloudwatcha można analizować ile wiadomości wysyła info do tego pliku, 5 albo 10 na minut i to jest spodziewana ilość tych logów, jeżeli w pewnym momencie spada ilość logów to wtedy możemy ruszyć funkcję, żeby ją zrestartować albo wymienić na nową.

#Lab5 
![[Pasted image 20260916105755.png]]

arn:aws:sns:us-west-2:445420258223:resize-image-topic-1234
resize-image-topic-1234
445420258223

S3 location

[arn:aws:s3:::awslambda-us-west-2-tasks/snapshots/445420258223/CreateThumbnail-be00b0d6-1863-444c-bd17-f4da01af306b](https://awslambda-us-west-2-tasks.s3.us-west-2.amazonaws.com/snapshots/445420258223/CreateThumbnail-be00b0d6-1863-444c-bd17-f4da01af306b?versionId=tcqjHJlWwSFxcW6H5Wri_R_QFuKwI_Ti&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEEkaCXVzLXdlc3QtMiJHMEUCICddBTZUznWZg91ucp67Je%2FOKy9bQ2w1%2FYEJOMBcvJaGAiEAtWvscnhUmd61yXTjtWrBlAYD88ZAcr7qbfeW70Cpo%2FEqiwIIERAFGgw1MDIyOTcwNzYxNjMiDJDTIGWKoIBt7IaahSroAXm26gXblzSVzK1rUrhr5QQUKDtY%2FLCF4Bh0LNnyK5HzROuMghLc0sAoVHI7rZ4HijhkDpFNKgrWzjCmCMQO1VmWx%2F%2BZ8e2voWw1iSkVGxNtmHbs%2F2mnvedK3HHR4qgkrrAnX%2F5Jy1K3sm5VPyLTQR9%2FofW8me%2Fk5H7Pd%2BbStrGpK%2F1gm6AnxJ%2FcQ%2FEXX21IYTCglhoN%2FbkzTKZO4LiRqBtzURl6VELk2hPGk9%2BTTimXl33HNu1nSehSY8U7lWxGo5f61HDaUt6gXjJVzvrpwv8Dr2eMKm2X4YrGY%2BLwkVuEVj0NzRQRDIQwg6ap1QY6jQGsTeNrNZwWH3SpRDzbsxylTXjqVgz5BpDmDJgPM1hpCUnKMhEvVbqhVFoH8JKpTyi7jwj9uBygsSrLzlQBgMxhe4xhDyMsqyKFahw9a7IysQAgQzJ75%2BwHwA5CfYPMcuaLlxOZq5EtrSbYJcSj7rbyiUh4PPAIKQPQFs4zgH7r4DuEGo%2FcQh9J8jiQDOE%3D&X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Date=20260916T091332Z&X-Amz-SignedHeaders=host&X-Amz-Expires=599&X-Amz-Credential=ASIAXJ4Z5EHB7OI7LBGZ%2F20260916%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Signature=5d167f05113e4097d27d1e86ef1c0939a721ad54178ba0c72d7cf8ffd4b04d0d)

#Moduł12 **Edge Services** - serwowanie usług w bliższych lokalizacja. Pomaga to na zmniejszenie latency naszej aplikacji.

![[Pasted image 20260916130604.png]]

**Route 53** - DNS AWS, rejestrujemy nazwę domenową do IP. Wramach tego serwisu można rejestrować i utrzymywać domeny. Dodatkowo możemy używać w nim policy do health checków, latency i ochronę DDOS.
- Tworzymy hosted zony (publiczne) - te domeny będą rozwiązywalne z publicznej sieci. Trzeba to skonfigurować z dostawcą domeny do naszej hosted zone.
- Prywatne hosted zone, przypięte są do VPC i pomagają na rozwiązanie nazw prywatnych.
![[Pasted image 20260916130939.png]]

**Routing polices**
- Simple - jeden rekord, który będzie zwracany do danej domeny.
![[Pasted image 20260916131053.png]]

- Failover routing
![[Pasted image 20260916131109.png]]

- Geolocation routing
	- Kierowanie userów do odpowiednich endpointów.
![[Pasted image 20260916131224.png]]

- Geoproximity routing
	- Obszarowe kierowanie userów do danego endpointa.
![[Pasted image 20260916131322.png]]

- Latency-based routing
	- Kierowanie userów do endpointa, który dla niego ma najmniejsze latency.
![[Pasted image 20260916131356.png]]

- Multivalue answer routing
![[Pasted image 20260916131425.png]]

- Weighted routing
	- Częściowe przekirowywanie ruchu między AZ.
![[Pasted image 20260916131451.png]]

**CloudFront** - content delivery networks, ponad 600 punktów gdzie sieć aws łączy się z sieciami publicznymi, każdy taki punkt jest rozpatrywany jako edge locations, część takich edgy ma funkcję regional edge caches.
- Za jego pomocą można udostępniać statyczny albo dynamiczny kontent.
- Można dostosować politykę cache.
- Można do niego podpiąć reguły WAF.
- By default AWS shield ma włączony odrazu anty DDoS service.
- Ruch w CloudFront jest zawsze szyfrowany.
- Można za jego pomocą włączyć geolokalizację i np wycinać ruch przychodzący z danego regionu świata.
![[Pasted image 20260916131728.png]]

**Edge caching** - warstwa cachce, która stoi między serwerami kontentu.
![[Pasted image 20260916131956.png]]

**CloudFronta caching steps**
![[Pasted image 20260916132109.png]]

**Konfiguracja CloudFronta**
- Sprawdzamy co jest naszym originem - wybieramy sobie:
	- s3 bucket
	- ELB load balancer
	- Custom origin
		- EC2 instances
		- On-premises server
- Tworzymy dystrybucję
	- Path pattern
	- Protocol policy
	- HTTP methods
	- Signed URL
	- Cache policy
		- TTL - time to live
		- Cache key settings
![[Pasted image 20260916132317.png]]

**Improving perfomance**
![[Pasted image 20260916132512.png]]

**DDoS attacks** - atakujący wykorzystuje boty aby zaatakować naszą aplikację
![[Pasted image 20260916132609.png]]

**AWS Shield** - protecka od AWS'a przed DDoS i innymi rodzajami ataku.
![[Pasted image 20260916132812.png]]

**AWS WAF**
![[Pasted image 20260916132933.png]]

![[Pasted image 20260916133036.png]]

- Reguły WAF można samemu sobie pisać.
- Kupić.
- Korzystać z gotowych rozwiązań AWS.

**Kontrola ruchu za pomocą reguł ALC**
![[Pasted image 20260916133223.png]]

**Firewall Manager** - rozwiązanie, które ma sens w momencie jak mamy więcej kont AWSowych
![[Pasted image 20260916133505.png]]

- Można do niego wprorwadzać reguły WAF.
![[Pasted image 20260916133741.png]]

![[Pasted image 20260916134006.png]]

**AWS Outpost family** - rozwiązanie, które pozwala mieć w naszej serwerowni mieć kawałek przeznaczony dla AWS'a. Pokazujemy Amazonowi miejsce gdzie co jest w serwerowni, przyjeżdża ekipa i montuje bardzo ograniczonego outposta w naszej serwerowni.
- Outpost rack - rack do 96U większy compute oraz więcej opcji serwisów.
- Outpost servers - server 1U lub 2U wrzucony do naszej szafy rack
![[Pasted image 20260916134211.png]]

- Dzięki temu można rozciągnąć nasze VPC o dodatkowego outposta na naszym koncie AWS.
![[Pasted image 20260916134303.png]]

#Lab6
arn:aws:cloudfront::445420258223:distribution/E11EKO6G69M9IP
d3e39r8a9rnt72.cloudfront.net

LabELB-1294369779.us-west-2.elb.amazonaws.com

bucket:
arn:aws:s3:::lab-bucket-992881725
"Resource": "arn:aws:s3:::lab-bucket-992881725/*

#Moduł12 Backup and Recovery
- Planowania backupów.
	- Testy backupów.
	- Resourcesy - complex recovery path.
	- Lack of sufficient resources.
	- Plan backupów.
	- Zmiany, które nie zostały wprowadzone.

W przypadku AWS możemy zaplwanować co może przestać działać.
- Staramy się zrobić tak aby nasza aplikacja była HA.
- Fault tolerance - możliwość odtworzenia stanu naszej aplikacji / serwera, która przywróci / uruchomi nam serwer i podepnie go spowrotem do klastra.
- Backup - miejsce do którego wrzucamy backup.
- Disaster recovery - zaplanowanie co by się stało, aby nasza aplikacja mogła nadal działać. Planowanie i ćwiczenie scenariuszy kiedy wypadnie nam AZ lub nawet cały Region.

**RPO** - Recovery Point Objective
 - Ile danych możemy stracić - biznesowo to około 12h.

**RTO** - Recovery Time Objective
- Ile czasu po tym zdarzeniu potrzebujemy na to aby uruchomić i przywrócić nasze usługi.

![[Pasted image 20260916145658.png]]

Składowanie danych:
![[Pasted image 20260916145723.png]]

Do backupowania instancji EC2 możemy użyć AMI:
![[Pasted image 20260916145931.png]]

Failover network design:
![[Pasted image 20260916150009.png]]
- Route 53 jest w 100% odporne na disastery

Bazydanych:
![[Pasted image 20260916150126.png]]

Templates and scripts:
![[Pasted image 20260916150313.png]]

Podsumowanie:
![[Pasted image 20260916150712.png]]

Benefity:
![[Pasted image 20260916150742.png]]

![[Pasted image 20260916150946.png]]

- Brakuje tutaj punktu, że od czasu do czasu warto testować takie backupy.

**Strategia przywracania usług**
- Backup and restore - najbardziej prymitywna i najprostrza forma backupu, przywracamy od zera do w pełni działającego środowiska.
- Pilot light
	- Po stronie naszego disaster recovery regionu mamy przygotowaną infrę, zsynchronizowaną bazę i w momencie jak nasza aplikacja przestanie działać to odpala się drugi backup infry.
![[Pasted image 20260916151224.png]]

![[Pasted image 20260916151315.png]]

- Warm standby 
	-  Po stronie recovery coś już działa i w momencie jak infra main Prod umrze to wszystko jest już przerzucane na Recovery region, częściowo w ramach tego route  53 może częściowo nawet przerzucać workload na drugi region.
![[Pasted image 20260916151631.png]]

![[Pasted image 20260916151735.png]]

- Multi-site active/active
	- Dobrze zschynchronizowane dane.
	- Replikowane bazydanych.
	- Droższa opcja - bo urzymujemy 2 środowiska.
![[Pasted image 20260916151800.png]]

Porównanie:
![[Pasted image 20260916151943.png]]

-----
# Podsumowanie kursu:

Exam:
[AWS Certified Solutions Architect – Associate](https://aws.amazon.com/certification/certified-solutions-architect-associate/ "https://aws.amazon.com/certification/certified-solutions-architect-associate/")

- Tutaj mamy infrmacje jak egzamin będzie wyglądał, możemy przedłużyć czas do 160 minut z racji tego, że egzamin nie jest w naszym ojczystym języku.
- 65 Pytań, 50 jest tylko punktowane.
- Na egzaminie nie ma punktów karnych za błędne odpowiedzi.

Exam guide:
[https://docs.aws.amazon.com/pdfs/aws-certification/latest/solutions-architect-associate-03/solutions-architect-associate-03.pdf#solutions-architect-associate-03](https://docs.aws.amazon.com/pdfs/aws-certification/latest/solutions-architect-associate-03/solutions-architect-associate-03.pdf#solutions-architect-associate-03 "https://docs.aws.amazon.com/pdfs/aws-certification/latest/solutions-architect-associate-03/solutions-architect-associate-03.pdf#solutions-architect-associate-03")

- in-scope AWS services - pytania z którymi na pewno możemy się spotkać na egzaminie.
- Warto podkreslić, że to jest trudny egzamin.
- **Warto zrobić egzamin z cloud-operations a dopiero potem do cloud-architecting.**

Szkolenia i pytania testowe:
[https://skillbuilder.aws/category/exam-prep/solutions-architect-associate-SAA-C03](https://skillbuilder.aws/category/exam-prep/solutions-architect-associate-SAA-C03 "https://skillbuilder.aws/category/exam-prep/solutions-architect-associate-saa-c03")

- W zakładce explore możemy wyklikać co chcemy się nauczyć itd.