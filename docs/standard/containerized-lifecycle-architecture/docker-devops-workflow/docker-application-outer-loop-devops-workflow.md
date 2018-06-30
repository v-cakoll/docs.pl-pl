---
title: Kroki w przepływie pracy DevOps zewnętrzne pętli dla aplikacji Docker
description: Cykl życia aplikacji konteneryzowanych Docker z platformy firmy Microsoft i narzędzia
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: b88eb5637bf266ab2e0a6d255f2e83f6aadc8af2
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106165"
---
# <a name="steps-in-the-outer-loop-devops-workflow-for-a-docker-application"></a>Kroki w przepływie pracy DevOps zewnętrzne pętli dla aplikacji Docker

Rysunek 5-1 przedstawia kroki składającej się z przepływu pracy zewnętrznego pętli DevOps sceny end-to-end.

![](./media/image1.png)

Rysunek 5-1: DevOps zewnętrzne pętli przepływ pracy Docker aplikacji z narzędzi firmy Microsoft

Teraz Przeanalizujmy każdy z tych kroków większej liczby szczegółów.

## <a name="step-1-inner-loop-development-workflow"></a>Krok 1: Wewnętrzny pętli Programowanie w przepływie pracy

Ten krok jest szczegółowo omówiono w rozdziale 4, ale recap, w tym miejscu jest gdzie rozpoczyna zewnętrzne pętli, moment, jaką dewelopera wypychanie kodu do systemu zarządzania kontroli źródła (np. Git), inicjowanie CI potoku akcje.

## <a name="step-2-source-code-control-integration-and-management-with-visual-studio-team-services-and-git"></a>Krok 2: Integracji kontroli kodu źródłowego i zarządzanie za pomocą programu Visual Studio Team Services i Git

W tym kroku musisz mieć systemu kontroli wersji, aby zebrać jednolity całego kodu pochodzącego z różnych deweloperów w zespole.

Mimo że kontroli kodu źródłowego (SCC) i kod źródłowy zarządzania mogą wydawać się drugie — charakter cykl do większość deweloperów, podczas tworzenia aplikacji Docker życia DevOps, jest bardzo istotne, aby podkreślić, czy należy przesłać nie obrazy usługi Docker z aplikacją bezpośrednio do globalnego Docker rejestru (na przykład rejestru kontenera platformy Azure lub Centrum Docker) z komputera dewelopera. Przeciwnie obrazy usługi Docker są zwalniane i wdrożone w środowisku produkcyjnym należy utworzyć wyłącznie na kod źródłowy, który jest integrowana w tym globalnych kompilacji lub potoku CI oparte na repozytorium kodu źródłowego (np. Git).

Lokalne obrazy generowane przez deweloperów, same powinna być używana tylko przez deweloperów, podczas testowania w ich własnych maszyn. Jest to, dlaczego jest bardzo istotne, aby aktywować z kodu SCC potoku DevOps.

Visual Studio Team Services i Team Foundation Server obsługuje Git i kontroli wersji Team Foundation. Można wybrać między nimi i użyć jej do środowiska Microsoft end-to-end. Jednak możesz również zarządzać kodu w repozytoria zewnętrznych (na przykład GitHub, repozytoria Git lokalnymi lub Podwersją) i nadal mieć możliwość nawiązania połączenia i uzyskać jako punktu wyjścia planowaną DevOps CI kod.

## <a name="step-3-build-ci-integrate-and-test-with-visual-studio-team-services-and-docker"></a>Krok 3: Kompilacji, CI, integracji i przetestowania z programu Visual Studio Team Services i platformy Docker

CI pojawiło się jako standardowe rozwiązanie dla nowoczesnych oprogramowania testowania i dostarczania. Rozwiązanie Docker przechowuje wyraźnej separacji między zespołami i. Immutability obrazów Docker zapewnia powtarzalne wdrożenia między co został opracowany, przetestowane za pośrednictwem elementu konfiguracji i uruchomić w środowisku produkcyjnym. Aparatem platformy docker wdrożonego na komputery przenośne developer i infrastruktury testowego sprawia, że kontenery przenośny w środowiskach.

W tym momencie po korzystasz z systemu kontroli wersji z prawidłowego kodu przesłane należy *usługi kompilacji* Pobieranie kodu i uruchom testy i globalnych kompilacji.

Wewnętrzny przepływu pracy dla tego kroku (elementu konfiguracji, kompilacji, test) jest informacje do budowy potoku CI składające się z repozytorium kodu (Git, itp.), serwer kompilacji (Visual Studio Team Services), aparatem platformy Docker i rejestru Docker.

Służy Visual Studio Team Services jako podstawy do tworzenia aplikacji i ustawienie potoku elementu konfiguracji sieci i publikowania wbudowanych "artefakty" do "repozytorium artefaktów,", który znajduje się w następnym kroku.

W przypadku używania Docker dla wdrożenia "końcowego artefaktów" do wdrożenia są obrazy usługi Docker z aplikacji lub usług osadzone w nich. Te obrazy są naciśnięty, czy opublikowane *rejestru Docker* (prywatne repozytorium takich jak te mogą mieć w rejestrze kontenera platformy Azure, lub publiczny podobny rejestrze Centrum Docker, który jest powszechnie używany do oficjalnego obrazy podstawowe).

Poniżej przedstawiono podstawowe pojęcia: potoku elementu konfiguracji będzie kopać poza przez zatwierdzeń do repozytorium SCC, takich jak Git. Zatwierdzanie spowoduje Visual Studio Team Services, aby uruchomić zadanie kompilacji w kontenerze Docker i, po pomyślnym ukończeniu zadania, wypychanie obrazu Docker rejestru Docker, jak pokazano na rysunku 5-2.

![](./media/image2.png)

Rysunek 5-2: kroki związane z elementu konfiguracji

Poniżej przedstawiono podstawowe czynności przepływu pracy CI Docker i Visual Studio Team Services:

1.  Deweloper wypychanie zatwierdzenia do repozytorium SCC (Git/Visual Studio Team Services, GitHub itp.).

2.  Jeśli używasz programu Visual Studio Team Services lub Git, CI jest wbudowany, która oznacza, że jest tak proste, jak zaznaczenie pola wyboru w programie Visual Studio Team Services. Jeśli używasz zewnętrznego SCC (na przykład GitHub), *webhook* będzie powiadamiać Visual Studio Team Services aktualizacji lub Wypychanie do Git/GitHub.

3.  Visual Studio Team Services pobiera SCC repozytorium, w tym plik DockerFile opisujące obrazu, a także kod aplikacji i testowania.

4.  Visual Studio Team Services tworzy obraz Docker i etykiet go przy użyciu numeru kompilacji.

5.  Visual Studio Team Services tworzy kontener Docker w udostępnione hostów Docker i uruchamia odpowiednie testy.

6.  Jeśli testy zakończą się powodzeniem, obraz jest najpierw relabeled łatwy do rozpoznania nazwy, aby wiedzieli, "specjalne kompilacja" (takich jak "/ 1.0.0" lub inne etykiety), a następnie przesunięta w do rejestru Docker (Centrum Docker rejestru kontenera platformy Azure, DTR, itp.)

### <a name="implementing-the-ci-pipeline-with-visual-studio-team-services-and-the-docker-extension-for-visual-studio-team-services"></a>Wdrażanie potoku elementu konfiguracji z programu Visual Studio Team Services i rozszerzenia Docker dla Visual Studio Team Services

[Rozszerzenia programu Visual Studio Team Services Docker](https://aka.ms/vstsdockerextension) dodaje do potoku sieci CI, z którym mogą kompilacji obrazy usługi Docker, wypychana obrazy usługi Docker na uwierzytelniony rejestru Docker, uruchom obrazy usługi Docker lub uruchomić inne operacje oferowane przez zadanie Interfejs wiersza polecenia docker. Dodano również rozwiązania Docker Compose zadanie, które służy do kompilacji, powiadomień wypychanych i uruchamianie aplikacji platformy Docker multicontainer lub uruchomić inne operacje oferowane przez rozwiązania Docker Compose interfejsu wiersza polecenia, jak pokazano na rysunku 5-3.

![](./media/image3.png)

Rysunek 5-3 potoku Docker CI w Visual Studio Team Services

Dla hostów Docker i kontener lub rejestrów obrazu rozszerzenia Docker można używać punktów końcowych usługi. Domyślnie zadania za pomocą lokalnego hosta Docker, jeśli jest dostępna, (obecnie wymaga niestandardowych agenta programu Visual Studio Team Services); w przeciwnym razie wymagają one, musisz zapewnić połączenie hostów Docker. Akcje, które są zależne od uwierzytelnianego z rejestru Docker, takich jak wypychanie obrazu, wymagają podania Docker rejestru połączenia.

Rozszerzenia programu Visual Studio Team Services Docker na koncie usługi Visual Studio Team Services instalowane są następujące składniki:

-   Punkt końcowy usługi w celu nawiązania połączenia z rejestrem Docker

-   Punkt końcowy usługi do nawiązywania połączenia z hostem kontenera Docker

-   Zadanie Docker wykonać następujące czynności:

-   Tworzenie obrazu

-   Wypychanie obrazu lub repozytorium do rejestru

-   Uruchom obrazu w kontenerze

-   Uruchom polecenie Docker

-   Aby uruchomić polecenie rozwiązania Docker Compose zadania rozwiązania Docker Compose

Z tych zadań programu Visual Studio Team Services kompilacji Linux Docker Host/wirtualna zainicjowane na platformie Azure i preferowanych rejestru Docker (rejestru kontenera platformy Azure, Centrum Docker, prywatne DTR Docker lub innych rejestru Docker) można utworzyć potoku sieci Docker CI w bardzo spójny sposób.

***Wymagania:***

-   Visual Studio Team Services, lub w przypadku instalacji lokalnej, Team Foundation Server 2015 Update 3 lub nowszym.

-   Agent programu Visual Studio Team Services zawiera dane binarne Docker.

W prosty sposób utworzyć jeden z nich jest do używania Docker do uruchamiania kontener na podstawie obrazu Docker agenta programu Visual Studio Team Services.

**Więcej informacji o** aby przeczytać więcej informacji na temat łączenia Visual Studio Team Services Docker CI potoku i aby wyświetlić wskazówki, odwiedź następującą witrynę:

Uruchomiony agent programu Visual Studio Team Services jako kontener Docker: [ https://hub.docker.com/r/\ vsts-microsoft-agent /](https://hub.docker.com/r/microsoft/vsts-agent/)

Rozszerzenie programu VSTS Docker: <https://aka.ms/vstsdockerextension>

Tworzenie obrazów .NET Core Linux Docker za pomocą programu Visual Studio Team Services: <https://blogs.msdn.microsoft.com/stevelasker/2016/06/13/building-net-core-linux-docker-images-with-visual-studio-team-services/>

Tworzenie opartych na systemie Linux Visual Studio Team Service maszyna kompilacji z Docker pomocy technicznej: <http://donovanbrown.com/post/2016/06/03/Building-a-Linux-Based-Visual-Studio-Team-Service-Build-Machine-with-Docker-Support>

### <a name="integrate-test-and-validate-multicontainer-docker-applications"></a>Integrowanie, testowanie i weryfikowanie multicontainer aplikacji Docker

Zazwyczaj większość aplikacji Docker składają się z wielu kontenerów niż jeden kontener. Dobrym przykładem jest ukierunkowane mikrousług aplikacji, dla którego trzeba jednego kontenera na mikrousługi. Jednak nawet bez ściśle mikrousług wzorce podejście, jest bardzo prawdopodobne, że aplikacja Docker może składać się z wielu kontenerów lub usług.

Dlatego po utworzeniu kontenery aplikacji w potoku elementu konfiguracji, należy również wdrażania, integracji i przetestować aplikację jako całość, biorąc pod uwagę jego kontenery w ramach integracji hosta Docker lub nawet w klastrze testu, do której są kontenerów rozproszone.

Jeśli używasz jednego hosta, można użyć polecenia Docker, takie jak docker-Napisz do tworzenia i wdrażania powiązane kontenerów do testowania i sprawdzania, czy środowisko Docker na jednej maszynie wirtualnej. Jednak jeśli pracujesz z klastra programu orchestrator, takich jak DC/OS, Kubernetes lub Docker Swarm, należy wdrożyć kontenerów za pośrednictwem programu orchestrator, w zależności od sieci klastra/harmonogramu lub inny mechanizm.

Poniżej przedstawiono kilka typów testów, które można uruchomić dla kontenerów Docker:

-   Testy jednostkowe dla kontenerów Docker

-   Testowanie grup aplikacji połączonych ze sobą i mikrousług

-   Testowanie w produkcji i "element canary" wersjach

Istotne jest, czy podczas uruchamiania, integracja i testy funkcjonalne, należy uruchomić te testy z poza kontenerów. Testy nie musi zdefiniowany i uruchamiane w ramach kontenerów, które są wdrażane, ponieważ kontenery są oparte na obrazach statycznych, które powinny być dokładnie takie same jak te, które wdrażania w środowisku produkcyjnym.

Jest bardzo możliwe podczas testowania bardziej zaawansowanych scenariuszy, takich jak testowanie kilku klastrów (test, klastrem, przemieszczania klastra i klastra produkcyjnego) opublikować obrazów w rejestrze, aby przetestować w różnych klastrach.

### <a name="push-the-custom-application-docker-image-into-your-global-docker-registry"></a>Wypchnąć obrazu Docker niestandardową aplikację do globalnego rejestru Docker

Po Docker obrazy zostały sprawdzone i zatwierdzone, należy je oznaczać i publikowanie ich do rejestru Docker. Rejestr Docker jest krytycznego Docker cyklu życia aplikacji, ponieważ jest centralne miejsce przechowywania niestandardowych testu (alias "specjalne obrazy") do wdrożenia w odpowiedzi na pytania i środowiska produkcyjne.

Podobnie jak kod aplikacji przechowywanych w repozytorium SCC (Git itp.) jest "źródłem prawdy", "źródłem prawdy" binary aplikacji lub usługi bits do wdrożenia do środowiska odpowiedzi na pytania lub produkcji jest rejestru Docker.

Zazwyczaj warto mieć repozytoriami prywatne dla obrazów niestandardowych w prywatnym repozytorium w rejestrze kontenera platformy Azure lub w rejestrze lokalnym jak Docker zaufane rejestru albo w rejestrze chmura publiczna z ograniczonym dostępem (np. Centrum docker), mimo że w tym ostatnim przypadku, jeśli kod nie jest typu open source, muszą ufać dostawcy zabezpieczeń. W obu przypadkach metoda, za pomocą którego można to zrobić jest bardzo podobne i ostatecznie oparte na polecenia docker wypychania, jak pokazano na rysunku 5-4.

![](./media/image4.png)

Rysunek 5-4: publikowanie niestandardowych obrazów w rejestrze Docker

Istnieje wiele ofert z rejestrów Docker od dostawców chmury, takich jak rejestru kontenera platformy Azure, Amazon Web Services kontenera rejestru, rejestru kontenera Google, nabrzeża rejestru i tak dalej.

Przy użyciu rozszerzenia programu Visual Studio Team Services Docker, możesz wypchnąć utworzenie zestawu obrazów usługi zdefiniowanych przez plik docker-compose.yml, z użyciem wielu tagów, uwierzytelnionym rejestrze Docker (na przykład rejestr kontenera Azure), jak pokazano na rysunku 5-5.

![](./media/image5.png)

Rysunek 5-5: przy użyciu programu Visual Studio Team Services do publikowania niestandardowych obrazów w rejestrze Docker

**Więcej informacji o** Aby dowiedzieć się więcej o rozszerzeniu Docker dla programu Visual Studio Team Services, przejdź do <https://aka.ms/vstsdockerextension>. Aby dowiedzieć się więcej na temat rejestru kontenera platformy Azure, przejdź do <https://aka.ms/azurecontainerregistry>.

## <a name="step-4-cd-deploy"></a>Krok 4: CD, wdrażanie

Immutability obrazów Docker zapewnia powtarzalne wdrożenia o co został opracowany, przetestowane za pośrednictwem elementu konfiguracji i uruchomić w środowisku produkcyjnym. Po utworzeniu obrazów Docker aplikacji, które są publikowane w rejestrze Docker (prywatny czy publiczny), można je wdrożyć w kilku środowiskach, w których mogą występować (środowiska produkcyjnego, pytań i odpowiedzi, przemieszczania, itp.) z dysku CD planowaną przy użyciu programu Visual Studio Team Services zadania potoku lub Visual Studio Team Services Release Management.

Jednak w tym momencie to zależy od rodzaju Docker aplikacji jest wdrażany. Wdrażanie prostej aplikacji (z kompozycji i wdrożenia punktu widzenia) jak wbudowanymi aplikacji składającej się z kilku kontenery lub usług i wdrożone na kilku serwerach lub maszyn wirtualnych jest bardzo różnią się od bardziej złożonych aplikacji, takich jak wdrażanie mikrousług aplikację z możliwościami informatycznych. W poniższych sekcjach opisano te dwa scenariusze.

### <a name="deploying-composed-docker-applications-to-multiple-docker-environments"></a>Wdrażanie składane Docker aplikacjom wiele środowisk Docker

Oto pierwszy w scenariuszu mniej złożone: Wdrażanie prostego hostów Docker (maszyn wirtualnych i serwery) w środowisku jednego lub wiele środowisk (pytań i odpowiedzi, tymczasowych i produkcyjnych). W tym scenariuszu wewnętrznie planowaną CD można użyć docker-tworzą (z zadań wdrożenia programu Visual Studio Team Services) do wdrażania aplikacji Docker z zestawem powiązanych kontenery lub usług, zgodnie z opisami w rysunek 5 – 6.

![](./media/image6.png)

Rysunek 5-6: Wdrażanie kontenerów aplikacji proste rejestru środowisk hostów Docker

Rysunek 5-7 przedstawia, jak łączyć z elementu konfiguracji kompilacji w środowiskach, w odpowiedzi na pytania i testowanie za pomocą programu Visual Studio Team Services, klikając rozwiązania Docker Compose w oknie dialogowym Dodaj zadanie. Jednak podczas wdrażania środowisk przemieszczania i produkcji, należy zwykle użyje funkcji zarządzania zleceniami obsługi wielu środowiskach (takich jak pytań i odpowiedzi, tymczasowych i produkcyjnych). Jeśli wdrażasz do pojedynczego hostów Docker jest przy użyciu programu Visual Studio Team Services "Rozwiązania Docker Compose" zadania (który wywołuje docker-tworzą się polecenie kulisy). Jeśli wdrażasz do usługi kontenera platformy Azure, używa zadania wdrażania Docker, jak wyjaśniono w poniższej sekcji.

![](./media/image7.png)

Rysunek 5-7: Dodawanie rozwiązania Docker Compose zadania w potoku Visual Studio Team Services

Po utworzeniu zlecenia w programie Visual Studio Team Services ma zestaw wejściowy artefaktów. Są one przeznaczone za niezmienialny w okresie istnienia wersji w wielu środowiskach. Podczas wprowadzania kontenery wejściowych artefaktów zidentyfikować obrazów w rejestrze do wdrożenia. W zależności od tego, jak te są identyfikowane ich nie ma gwarancji pozostają takie same, w okresie obowiązywania wersji najbardziej oczywisty przypadek jest odwołanie "myimage:latest" z pliku docker-compose.

Rozszerzenie Docker dla Visual Studio Team Services zapewnia który możliwość generowania artefaktów kompilacji, zawierające obrazu rejestru skróty służące który dotrą do unikatowego identyfikowania ten sam obraz binarny. Są to, co naprawdę chcesz użyć jako dane wejściowe dla wersji.

### <a name="managing-releases-to-docker-environments-by-using-visual-studio-team-services-release-management"></a>Zarządzanie wersjach środowiska Docker za pomocą programu Visual Studio Team Services Release Management

Za pośrednictwem rozszerzenia programu Visual Studio Team Services, można utworzyć nowy obraz, opublikowania go w rejestrze Docker, uruchom go na hostach z systemem Linux lub Windows i polecenia takie jak docker-Napisz do wdrożenia wielu kontenerów jako całej aplikacji przez element wizualny Możliwości zespołu usługi Release Management Studio przeznaczony dla wielu środowiskach, jak pokazano na rysunku 5-8.

![](./media/image8.png)

Rysunek 5 – 8: Konfigurowanie programu Visual Studio Team Services rozwiązania Docker Compose zadań z programu Visual Studio Team Services Release Management

Jednak należy pamiętać, że scenariusza wyświetlana w rysunek 5 – 6 i wdrożone w rysunek 5 – 8 jest bardzo proste (jest wdrażana do prostych Docker hosty i maszyny wirtualne i będą istnieć jeden kontener lub wystąpienia na obraz) i prawdopodobnie powinna być używana tylko w przypadku sc deweloperskich lub testowania enarios. W większości przypadków produkcji przedsiębiorstwa, należy mieć wysokiej dostępności (HA) i łatwe w zarządzaniu skalowalność Równoważenie obciążenia w wielu węzłów, serwerów i maszyn wirtualnych, a także "inteligentnego praca awaryjna" tak że jeśli serwer lub węzeł ulegnie awarii, jego usług i kontenery zostaną przeniesione do innego serwera hosta lub maszyny Wirtualnej. W takim przypadku należy bardziej zaawansowanych technologii, takich jak klastry kontenera, orchestrators i transfery danych. W związku z tym sposób, aby wdrożyć te klastry jest dokładnie za pomocą zaawansowanych scenariuszy szczegółowo w następnej sekcji.

### <a name="deploying-complex-docker-applications-to-docker-clusters-dcos-kubernetes-and-docker-swarm"></a>Wdrażanie złożonych aplikacji Docker do klastrów Docker (DC/OS, Kubernetes i Docker Swarm)

Rodzaj aplikacji rozproszonych wymaga zasoby obliczeniowe, które również są rozkładane. Aby mieć możliwości skalowania produkcji, musisz mieć klaster możliwości, które zapewniają wysoką skalowalność i wysokiej dostępności na podstawie puli zasobów.

Można wdrożyć kontenery ręcznie do tych klastrów za pomocą narzędzia interfejsu wiersza polecenia, takich jak Docker Swarm (podobnie jak przy użyciu [tworzenia usługi docker](https://docs.docker.com/engine/swarm/swarm-tutorial/deploy-service/)) lub interfejsu użytkownika sieci web takich jak [Mesosphere Marathon](https://mesosphere.github.io/marathon/docs/marathon-ui.html) dla DC/OS klastrów, ale powinien który zarezerwować tylko do celów testowych terminową wdrożenia lub do celów zarządzania, takich jak skalowania w poziomie lub celów monitorowania.

Z punktu widzenia CD i Visual Studio Team Services w szczególności można uruchomić zadania wdrażania specjalnie wykonane z środowiska Visual Studio Team Services Release Management, które zostaną wdrożone konteneryzowanych aplikacji rozproszonej klastrów w Usługa kontenera, jak pokazano w rysunek 5 – 9.

![](./media/image9.png)

Rysunek 5 – 9: Wdrażanie aplikacji rozproszonej do usługi kontenera

Początkowo wdrażając do niektórych klastrów lub orchestrators tradycyjnie używasz skrypty wdrażania i mechanizmów na każdym orchestrator (to znaczy Mesosphere DC/OS lub Kubernetes ma mechanizmów wdrażania innego niż Docker i Docker Swarm) zamiast prostszy i łatwy w użyciu rozwiązania docker-compose narzędzia na podstawie pliku definicji docker-compose.yml. Jednak dzięki użyciu Microsoft Visual Studio Team Services Docker wdrażanie zadań wyświetlane w rysunek 5 – 10 teraz również można wdrożyć DC/OS przez tylko przy użyciu znanych docker-compose.yml pliku, ponieważ Microsoft przeprowadza "Translacja" (z sieci Plik docker-compose.yml w innych formatach wymagane przez DC/OS).

![](./media/image10.png)

Rysunek 5-10: Dodawanie zadanie wdrażania Docker do Twojego środowiska RM

Rysunek 5-11 pokazano, jak można edytować zadanie wdrażania Docker i określić typ docelowy (Azure kontenera DC/OS usługi, w tym przypadku), plik rozwiązania Docker Compose i połączenia Docker rejestru (na przykład rejestru kontenera platformy Azure lub Centrum Docker). Jest to, gdy zadanie pobierze gotowe do użycia niestandardowego obrazy usługi Docker wdrażanych jako kontenery w klastrze DC/OS.

![](./media/image11.png)

Rysunek 5-11: Wdróż Docker zadań definicji wdrażania do usługi kontenera platformy Azure DC/OS

**Więcej informacji o** Aby dowiedzieć się więcej o potok dysku CD wraz z Visual Studio Team Services i Docker, odwiedź następującą witrynę:

Visual Studio Team Services rozszerzenia Docker i usługi kontenera platformy Azure: [ https://aka.ms/\ vstsdockerextension](https://aka.ms/vstsdockerextension)

Usługa kontenera platformy Azure: <https://aka.ms/azurecontainerservice>

Mesosphere DC/OS: <https://mesosphere.com/product/>

## <a name="step-5-run-and-manage"></a>Krok 5: Uruchom i zarządzanie nimi

Dlatego uruchamiania aplikacji i zarządzanie nimi w środowisku produkcyjnym enterprise poziom głównych podmiotu w i samego siebie oraz ze względu na typ operacji i działa na tym poziomie (operacji IT) oraz duże zakres ten obszar osób, firma Microsoft ma poświęcony całą obok rozdział wyjaśniający go.

## <a name="step-6-monitor-and-diagnose"></a>Krok 6: Monitorowanie i diagnozowanie

W tym temacie jest uwzględniane w rozdziale dalej jako część zadania, które wykonuje operacje IT w systemach produkcyjnych. jednak ważne jest wyróżnić szczegółowych danych uzyskanych w tym kroku źródła musi danych do zespół deweloperów, dzięki czemu aplikacja stale zwiększona. Z tego punktu widzenia jest również częścią DevOps, mimo że operacji i zadań są zazwyczaj wykonywane przez IT.

Tylko w przypadku monitorowania i diagnostyki 100 procent w obszarze DevOps są procesy monitorowania i analizy wykonywane przez zespół deweloperów dla środowisk testowych lub w wersji beta. Jest to realizowane przez wykonywania testów obciążenia lub po prostu beta lub środowiskach pytań i odpowiedzi, na którym próbujesz nowe wersje beta testerów monitorowania.

>[!div class="step-by-step"]
[Poprzednie](index.md)
[dalej](../run-manage-monitor-docker-environments/index.md)
