---
title: Kroki w przepływie pracy DevOps zewnętrznej pętli dla aplikacji platformy Docker
description: Poznaj procedurę "zewnętrzna pętla" przepływ pracy DevOps
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: b75e9df1c31e8bcebcaa6d56336a6aa499d13e1d
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56220942"
---
# <a name="steps-in-the-outer-loop-devops-workflow-for-a-docker-application"></a>Kroki w przepływie pracy DevOps zewnętrznej pętli dla aplikacji platformy Docker

Rysunek 5-1 przedstawiono kroki przepływu pracy DevOps zewnętrzna pętla wchodzących w skład sceny end-to-end.

![](./media/image1.png)

Rysunek 5-1. Przepływ pracy zewnętrzna pętla DevOps dla aplikacji platformy Docker przy użyciu narzędzi firmy Microsoft

Teraz Przeanalizujmy każdy z tych kroków, które bardziej szczegółowo.

## <a name="step-1-inner-loop-development-workflow"></a>Krok 1. Przepływ pracy wewnętrznej pętli tworzenia kodu

Ten krok jest omówiona szczegółowo w rozdziale 4, ale aby podsumowanie, Oto gdzie zewnętrzna pętla rozpoczyna się, moment, w którym Deweloper wypycha kodu do systemu zarządzania kontrolą źródła (takich jak Git), inicjowanie działania potoku ciągłej integracji.

## <a name="step-2-source-code-control-integration-and-management-with-azure-devops-services-and-git"></a>Krok 2. Integracja kontroli kodu źródłowego i zarządzanie za pomocą usługi Azure DevOps Services i Git

W tym kroku musisz mieć systemu kontroli wersji, aby zebrać jednolity całego kodu pochodzących z różnych deweloperów w zespole.

Mimo, że kontrola kodu źródłowego (SCC) i kod źródłowy zarządzania mogą wydawać się charakter sekundy, przechodzić do większości deweloperów, podczas tworzenia aplikacji platformy Docker w życiu metodyki DevOps, warto podkreślić, że nie musisz przesłać obrazów platformy Docker z aplikacją bezpośrednio do globalnego rejestru platformy Docker (np. usługi Azure Container Registry lub Docker Hub) z komputera dewelopera. Przeciwnie obrazy platformy Docker, które są zwalniane i wdrażane do środowisk produkcyjnych należy utworzyć wyłącznie na kod źródłowy, który jest integrowany w ramach globalnego kompilacji lub potoku ciągłej integracji, oparte na repozytorium kodu źródłowego (takich jak Git).

Obrazów lokalnych generowane przez deweloperów, samodzielnie powinny być używane tylko przez deweloperów, podczas testowania w ramach ich własnych maszyn. Jest to, dlaczego warto mieć z potokiem metodyki DevOps, aktywowana z poziomu kodu SCC.

Usługa Azure DevOps usług i Team Foundation Server obsługuje Git i kontroli wersji serwera Team Foundation. Można wybrać między nimi i użyć jej do środowiska Microsoft end-to-end. Można jednak również mogą zarządzać kodu w repozytoriach zewnętrznych (takich jak GitHub, lokalne repozytoria Git i Subversion) i nadal mieć możliwość nawiązania połączenia i pobrania kodu jako punktu wyjścia dla potoku ciągłej integracji metodyki DevOps.

## <a name="step-3-build-ci-integrate-and-test-with-azure-devops-services-and-docker"></a>Krok 3. Tworzenie elementu konfiguracji, integracja i testowanie na platformie Azure DevOps usług i platformą Docker

Ciągła Integracja została uznana zawiera standardowe rozwiązanie dla nowoczesnych oprogramowania testowania i dostarczania. Rozwiązanie Docker przechowuje separacji między zespołami deweloperów i operacyjne. Niezmienność obrazów platformy Docker zapewnia powtarzalne wdrożenia między co został opracowany, przetestowane za pośrednictwem ciągłej integracji i uruchomić w środowisku produkcyjnym. Aparat platformy docker wdrożony na komputery przenośne dla deweloperów i infrastrukturę testowania sprawia, że kontenery przenośny między środowiskami.

W tym momencie po system kontroli wersji przy użyciu prawidłowego kodu przesłane, potrzebujesz *Tworzenie usługi* przejmą kod i uruchom testy i globalne kompilacji.

Wewnętrzny przepływu pracy dla tego kroku (ciągłej integracji, kompilacja, testowanie) jest informacje do budowy potoku ciągłej integracji, składający się z repozytorium kodu (Git itp.), serwer kompilacji (usługom DevOps platformy Azure), aparat platformy Docker i rejestr platformy Docker.

Umożliwia usługom DevOps platformy Azure jako podstawa do tworzenia aplikacji, a potok ciągłej integracji i publikowania "artefaktów kompilacji" "repozytorium artefaktów,", która została wyjaśniona w następnym kroku.

W przypadku używania platformy Docker dla wdrożenia "końcowe artefakty" do wdrożenia są obrazy platformy Docker do aplikacji lub usługi z osadzone wewnątrz nich. Te obrazy są wypychane lub opublikowane na *rejestru platformy Docker* (prywatne repozytorium, takich jak te mogą mieć w usłudze Azure Container Registry, lub publiczny podobny rejestru koncentratora platformy Docker, która jest powszechnie używana oficjalne obrazy podstawowej).

Poniżej przedstawiono podstawowe pojęcia: Potok ciągłej integracji będą się wyłączone przez zatwierdzenia do repozytorium SCC, takich jak Git. Zatwierdzenie spowoduje, że usługom DevOps platformy Azure Uruchom zadanie kompilacji w kontenerze platformy Docker, i po pomyślnym zakończeniu tego zadania, Wypchnij obraz platformy Docker do rejestru platformy Docker, jak pokazano w rysunek 5-2.

![](./media/image2.png)

Rysunek 5-2: Kroki wykonywane w elemencie konfiguracji

Poniżej przedstawiono podstawowe kroki przepływu pracy ciągłej integracji z platformami Docker i usługom DevOps platformy Azure:

1.  Deweloper wypycha zatwierdzenie do repozytorium SCC (Git/usług platformy Azure DevOps, GitHub itp.).

2.  Jeśli używasz usługi Azure DevOps Services lub program Git, ciągła Integracja jest wbudowany, co oznacza, że jest tak proste, jak zaznaczenie pola wyboru w usługom DevOps platformy Azure. Jeśli używasz zewnętrznego SCC (na przykład GitHub) *elementu webhook* będzie Powiadom usługom DevOps platformy Azure, aktualizacji lub Wypychanie do usługi Git/GitHub.

3.  Usługi Azure DevOps ściąga SCC repozytorium, w tym pliku DockerFile, zawierająca opis obrazu, a także kod aplikacji i testów.

4.  Usługi Azure DevOps tworzy obraz platformy Docker i etykiet go numerem kompilacji.

5.  Usługi Azure DevOps tworzy kontener platformy Docker w ramach elastycznie hosta platformy Docker i uruchamia odpowiednie testy.

6.  Jeśli testy zakończą się powodzeniem, obraz jest najpierw relabeled na nazwę opisową, dzięki czemu będzie wiadomo, że jest "kompilacja specjalne" (np. "/ 1.0.0" lub inne etykiety), a następnie wypchnięto do rejestru platformy Docker (Docker Hub, Azure Container Registry, DTR itp.)

### <a name="implementing-the-ci-pipeline-with-azure-devops-services-and-the-docker-extension-for-azure-devops-services"></a>Wdrażania potoku ciągłej integracji, dzięki usługom DevOps platformy Azure oraz rozszerzenie Docker dla usługi DevOps platformy Azure

[Rozszerzenie Azure DevOps usług Docker](https://aka.ms/vstsdockerextension) dodaje zadania do potoku ciągłej integracji za pomocą którego można utworzyć obrazy platformy Docker, Wypchnij obrazy aparatu Docker do uwierzytelnionego rejestru platformy Docker, uruchamianie obrazów platformy Docker lub uruchamiania innych operacji oferowane przez platformy Docker INTERFEJS WIERSZA POLECENIA. Dodaje zadanie narzędzia Docker Compose, używanej do kompilacji, wypychania i uruchom z wieloma kontenerami w celu aplikacji platformy Docker lub uruchomić inne operacje oferowane przez Docker Compose interfejsu wiersza polecenia, jak pokazano w rysunek 5-3.

![](./media/image3.png)

Rysunek 5-3: Potok ciągłej integracji platformy Docker w usługom DevOps platformy Azure

Rozszerzenia platformy Docker można użyć punktów końcowych usługi dla hostów platformy Docker i kontenerów lub rejestry obrazów. Domyślnie zadania i używa lokalnego hosta platformy Docker, jeśli jest dostępny, (obecnie wymaga niestandardowych agenta usługom DevOps platformy Azure); w przeciwnym razie wymagają one, że podajesz połączenia hosta platformy Docker. Akcje, które są zależne od uwierzytelniane za pomocą rejestru platformy Docker, takich jak wypychanie obrazu wymaga zapewnienia Docker registry połączenia.

Rozszerzenie Azure DevOps usług Docker instaluje następujące składniki na Twoim koncie usługi DevOps platformy Azure:

-   Punkt końcowy usługi do łączenia się z rejestrem platformy Docker

-   Punkt końcowy usługi do łączenia się z hosta kontenera platformy Docker

-   Zadanie platformy Docker, aby wykonać następujące czynności:

-   Zbuduj obraz

-   Wypchnij obraz lub repozytorium do rejestru

-   Uruchamianie obrazu w kontenerze

-   Uruchom polecenie Docker

-   Zadaniem narzędzia Docker Compose, aby uruchamiać polecenia narzędzia Docker Compose

Te zadania usługom DevOps platformy Azure kompilacji hosta platformy Docker systemu Linux i maszyn wirtualnych aprowizowane na platformie Azure i preferowanych rejestru platformy Docker (usługi Azure Container Registry, Docker Hub, prywatne DTR platformy Docker lub dowolnego rejestru platformy Docker) można utworzyć potok ciągłej integracji platformy Docker w bardzo spójny sposób.

***Wymagania:***

-   Usługi DevOps platformy Azure lub w przypadku instalacji lokalnej, Team Foundation Server 2015 Update 3 lub nowszej.

-   Agenta usługi DevOps platformy Azure, który ma pliki binarne platformy Docker.

Jest łatwy sposób utworzyć jeden z nich korzystać z aparatu Docker w celu uruchomienia kontenera na podstawie obrazu platformy Docker agenta usługom DevOps platformy Azure.

**Więcej informacji o** aby przeczytać więcej informacji na temat złożenia CI Docker usługi Azure DevOps potoku i aby wyświetlić przewodniki, odwiedź następującą witrynę:

Uruchamianie agenta usługom DevOps platformy Azure jako kontener platformy Docker: [  https://hub.docker.com/r/\ /vsts-agent usług microsoft /](https://hub.docker.com/r/microsoft/vsts-agent/)

Rozszerzenie metodyki DevOps platformy Docker z usług platformy Azure: <https://aka.ms/vstsdockerextension>

Tworzenie obrazów Docker systemu Linux w programie .NET Core dzięki usługom DevOps platformy Azure: <https://blogs.msdn.microsoft.com/stevelasker/2016/06/13/building-net-core-linux-docker-images-with-visual-studio-team-services/>

Kompilowanie maszyny kompilacji opartej na systemie Linux Visual Studio Team Service z obsługą platformy Docker: <http://donovanbrown.com/post/2016/06/03/Building-a-Linux-Based-Visual-Studio-Team-Service-Build-Machine-with-Docker-Support>

### <a name="integrate-test-and-validate-multicontainer-docker-applications"></a>Integracja, testowanie i Walidacja wieloma kontenerami w celu aplikacji platformy Docker

Zazwyczaj większość aplikacji platformy Docker składają się z wielu kontenerów, a nie jeden kontener. Dobrym przykładem jest zorientowanych na mikrousługi aplikacji, dla którego trzeba jednego kontenera na mikrousługach. Ale nawet bez wyłącznie następujące wzorce podejście mikrousług, jest bardzo prawdopodobne, że aplikacja platformy Docker będzie składać się z wielu kontenerów i usług.

W związku z tym po utworzeniu kontenerów aplikacji w potoku ciągłej integracji, trzeba będzie również wdrażać, integrowanie i testowanie aplikacji jako całości ze wszystkimi jego kontenerów w ramach integracji hosta platformy Docker lub nawet do klastra testowego, w jakim są usługi kontenerów rozproszone.

Jeśli używasz jednego hosta, możesz użyć poleceń Docker, takich jak platforma docker-compose, aby skompilować i wdrożyć powiązane kontenerów na potrzeby testowania i sprawdzania, czy środowisko platformy Docker w pojedynczej maszyny Wirtualnej. Jednak jeśli pracujesz z klastrem usługi orchestrator, np. DC/OS, Kubernetes lub Docker Swarm, zajdzie potrzeba wdrożenia kontenerów przy użyciu innego mechanizmu lub programu orchestrator, w zależności od wybranego klastra/harmonogramu.

Poniżej przedstawiono kilka rodzajów testów, które mogą być uruchamiane względem kontenerów platformy Docker:

-   Testy jednostkowe dla kontenerów Docker

-   Testowanie grup aplikacji połączonych ze sobą lub mikrousług

-   Testowanie w produkcji i "kanarkiem" wersji

Istotną kwestią jest to, że podczas uruchamiania, integracji i testów funkcjonalnych, należy uruchomić te testy z poza kontenerów. Testy, nie należy zdefiniowane i uruchamiane w ramach kontenerów, które są wdrażane, ponieważ kontenery są oparte na obrazy statyczne, które powinny być dokładnie tak, jak te, które będą wdrażane w środowisku produkcyjnym.

Jest to bardzo możliwe opcja podczas testowania bardziej zaawansowanych scenariuszy, takich jak testowanie wielu klastrów (testowanie, klastra, klaster przemieszczania i w warunkach produkcyjnych klastra) opublikować obrazów do rejestru, aby przetestować w różnych klastrach.

### <a name="push-the-custom-application-docker-image-into-your-global-docker-registry"></a>Wypychanie obrazu platformy Docker niestandardowych aplikacji do globalnego rejestr platformy Docker

Po obrazów platformy Docker zostały przetestowane i zweryfikowane, należy je oznaczać i opublikuj je do rejestru platformy Docker. Rejestr platformy Docker jest krytycznego w cyklu życia aplikacji platformy Docker, ponieważ to centralne miejsce, w którym są przechowywane niestandardowe testu (zwane również "specjalne obrazy") do wdrożenia w odpowiedzi na pytania i wdrożeń produkcyjnych.

Podobnie jak kod aplikacji, przechowywane w repozytorium SCC (Git itp.) jest "źródło prawdziwych informacji", rejestr platformy Docker jest "źródłem prawdziwych" binarnych aplikacji lub usługi bits do wdrożenia środowiska QA lub produkcja.

Zazwyczaj warto mieć prywatnych repozytoriów dla obrazów niestandardowych w prywatnym repozytorium w usłudze Azure Container Registry lub rejestru lokalnych, takich jak Docker Trusted Registry lub rejestru chmury publicznej z ograniczonym dostępem (np. Usługi docker Hub), chociaż w tym ostatnim przypadku, jeśli kod nie jest typu open source, muszą ufać zabezpieczeń dostawcy. W obu przypadkach metoda, za pomocą którego można to zrobić jest bardzo podobne i ostatecznie zależnie od polecenia wypychania platformy docker, jak pokazano na rysunku 5-4.

![](./media/image4.png)

Rysunek 5-4: Publikowanie niestandardowych obrazów do rejestru platformy Docker

Istnieje wiele ofert z rejestrów platformy Docker z dostawców chmury, takich jak usługa Azure Container Registry, Amazon Web Services Container Registry, Google Container Registry, rejestr nabrzeża i tak dalej.

Korzystanie z rozszerzenia Azure DevOps usługi Docker, możesz wypchnąć zestaw obrazów usługi zdefiniowane w pliku docker-compose.yml przy użyciu wielu tagów do uwierzytelnionego rejestru platformy Docker (np. usługi Azure Container Registry), jak pokazano na rysunku 5-5.

![](./media/image5.png)

Rysunek 5-5: Publikowanie niestandardowych obrazów do rejestru platformy Docker przy użyciu usługi DevOps platformy Azure

**Więcej informacji o** Aby dowiedzieć się więcej o rozszerzeniu Docker dla usługi DevOps platformy Azure, przejdź do <https://aka.ms/vstsdockerextension>. Aby dowiedzieć się więcej na temat usługi Azure Container Registry, przejdź do <https://aka.ms/azurecontainerregistry>.

## <a name="step-4-cd-deploy"></a>Krok 4. Ciągłe wdrażanie, wdrażanie

Niezmienność obrazów platformy Docker zapewnia powtarzalne wdrożenia za pomocą co został opracowany, przetestowane za pośrednictwem ciągłej integracji i uruchomić w środowisku produkcyjnym. Po utworzeniu aplikacji obrazów platformy Docker, opublikowane w rejestrze Docker (prywatnej lub publicznej), można wdrożyć je do kilku środowiskach, które mogą wystąpić (produkcyjne, QA, przemieszczania, itp.) z potok ciągłego wdrażania za pomocą usługi DevOps platformy Azure zadania potoku lub usługi Azure DevOps usługi Release Management.

Jednak na tym etapie zależy ona wdrażanie jakiego rodzaju aplikację platformy Docker. Wdrażanie prostej aplikacji (z tworzenia i wdrażania punktu widzenia) takich jak monolitycznych aplikacji wchodzących w skład kilku kontenerów lub usług i wdrożone na kilku serwerach lub maszynach wirtualnych jest bardzo różnią się od wdrażanie bardziej złożonych aplikacji, takich jak zorientowanych na mikrousługi aplikacji z możliwościami w hiperskali. W poniższych sekcjach opisano te dwa scenariusze.

### <a name="deploying-composed-docker-applications-to-multiple-docker-environments"></a>Wdrażanie składa się z aplikacji platformy Docker w wielu środowiskach platformy Docker

Przyjrzyjmy się pierwsze u scenariusz mniej złożone: Wdrażanie prostego hostów platformy Docker (maszyn wirtualnych lub serwerach) w ramach jednego środowiska lub do wielu środowisk (kontroli jakości, środowisk przejściowych i produkcyjnych). W tym scenariuszu wewnętrznie potok ciągłego Dostarczania można używać platformy docker-compose (z zadań wdrożenia usługom DevOps platformy Azure) do wdrożenia przy użyciu jego powiązany zestaw aplikacji platformy Docker, kontenery lub usługi, tak jak przedstawiono to w rysunek 5 – 6.

![](./media/image6.png)

Rysunek 5 – 6: Wdrażanie aplikacji kontenerów do prostych rejestru środowiska hosta platformy Docker

Rysunek 5 – 7 pokazuje, jak połączyć kompilacji ciągłej integracji do odpowiedzi na pytania/testowym za pośrednictwem usługi DevOps platformy Azure, klikając pozycję Narzędzia Docker Compose w oknie dialogowym Dodaj zadanie. Jednak w przypadku wdrażania w środowiskach przejściowych lub produkcyjnych, zazwyczaj używasz funkcji Release Management, obsługa wielu środowisk (takich jak pytań i odpowiedzi, środowisk przejściowych i produkcyjnych). Jeśli wdrażasz do pojedynczego hostów platformy Docker, jest za pomocą usługi Azure DevOps "Narzędzia Docker Compose" zadanie (który wywołuje platformy docker-compose się polecenia kulisy). Jeśli wdrażasz do usługi Azure Container Service używa zadania wdrażania platformy Docker, jak wyjaśniono w poniższej sekcji.

![](./media/image7.png)

Rysunek 5 – 7: Dodawanie zadania narzędzia Docker Compose w potoku usługom DevOps platformy Azure

Po utworzeniu wydania w usługom DevOps platformy Azure ma zbiór wejściowy artefaktów. Te powinny być niezmienialny w okresie istnienia wersji w wielu środowiskach. Po wprowadzeniu kontenerów, danych wejściowych artefaktów zidentyfikować obrazów w rejestrze, aby wdrożyć. W zależności od tego, jak są one zidentyfikowane mają nie gwarancję, że pozostają takie same, w okresie obowiązywania wersji najbardziej oczywisty przypadek, że gdy odwołujesz się z plikiem docker-compose "myimage:latest".

Rozszerzenia platformy Docker dla usługi Azure DevOps Services wyświetla skróty służące możliwość generowania artefaktów kompilacji, które zawiera obrazu określonego rejestru, które gwarantują do unikatowej identyfikacji tego samego obrazu binarnego. Są to, co naprawdę chcesz użyć jako dane wejściowe do wydania.

### <a name="managing-releases-to-docker-environments-by-using-azure-devops-services-release-management"></a>Zarządzanie wersjami w środowiskach platformy Docker przy użyciu usługi Azure DevOps usługi Release Management

Za pośrednictwem rozszerzeń usługom DevOps platformy Azure, można utworzyć nowy obraz, opublikuj go do rejestru platformy Docker, uruchom go na hostach z systemem Linux lub Windows i użyj poleceń, takich jak platforma docker-compose w celu wdrożenia wielu kontenerów jako całej aplikacji, wspomaga DevOps platformy Azure Możliwości zarządzania wydaniami przeznaczonych dla wielu środowisk usług, jak pokazano w rysunek 5 – 8.

![](./media/image8.png)

Rysunek 5 – 8: Konfigurowanie usługi Azure DevOps usług narzędzia Docker Compose zadań przy użyciu usługi Azure DevOps usługi Release Management

Jednak pamiętać, że scenariusz pokazano w rysunek 5 i 6- i wdrażane w rysunek 5 – 8 jest zbyt skomplikowany (jest wdrożenie prostego hostów platformy Docker i maszynom wirtualnym i będzie jeden kontener i wystąpienie na obrazie) i prawdopodobnie należy używać tylko w przypadku projektowania lub testowania sc enarios. W większości scenariuszy produkcyjnych przedsiębiorstwa, chcesz mieć wysokiej dostępności (HA) i łatwy w zarządzaniu skalowalność, przez równoważenie obciążenia między wiele węzłów, serwerów i maszyn wirtualnych, a także "inteligentne przejścia w tryb failover" tak, jeśli serwer lub węzła nie powiedzie się, usługach i kontenery zostanie przeniesiony do innego serwera hosta lub maszyny Wirtualnej. W takim przypadku potrzebujesz bardziej zaawansowanych technologii, takich jak klastry kontenerów, koordynatorów i transfery danych. W związku z tym sposób wdrażania tych klastrach jest dokładnie za pomocą zaawansowanych scenariuszy, które wyjaśniono w następnej sekcji.

### <a name="deploying-complex-docker-applications-to-docker-clusters-dcos-kubernetes-and-docker-swarm"></a>Wdrażanie złożonych aplikacji platformy Docker z klastrami platformy Docker (DC/OS, Kubernetes i Docker Swarm)

Rodzaj aplikacji rozproszonych wymaga zasobów obliczeniowych, które są rozpowszechniane. Zapewnienie możliwości skalowania w środowisku produkcyjnym, musisz mieć, klastrowanie możliwości, które zapewniają wysoką skalowalność i wysokiej dostępności na podstawie puli zasobów.

Można wdrożyć kontenery ręcznie do tych klastrów za pomocą narzędzia interfejsu wiersza polecenia, takie jak Docker Swarm (takimi jak wymaganie użycia [tworzenia usługi docker](https://docs.docker.com/engine/swarm/swarm-tutorial/deploy-service/)) lub internetowego interfejsu użytkownika takich jak [Mesosphere Marathon](https://mesosphere.github.io/marathon/docs/marathon-ui.html) dla platformy DC/OS klastrów, ale należy Zarezerwuj, tylko do celów testowych terminową wdrożenia lub do celów zarządzania, takie jak skalowanie w poziomie lub celów monitorowania.

Z punktu widzenia ciągłego Dostarczania i usługom DevOps platformy Azure w w szczególności można uruchomić zadania związane z wdrażaniem specjalnie wykonane z środowiska usługi Azure DevOps usługi Release Management, które zostaną wdrożone w klastrach rozproszonych w kontenerze aplikacji konteneryzowanych Usługi, jak pokazano w rysunek 5-9.

![](./media/image9.png)

Rysunek 5-9: Wdrażanie aplikacji rozproszonych w usłudze Container Service

Początkowo podczas wdrażania aplikacji na niektórych klastrów lub koordynatorów, tradycyjnie używasz skryptów wdrażania i mechanizmy na poszczególnych koordynatorów (czyli Mesosphere DC/OS lub Kubernetes, które mają mechanizmy innego wdrożenia niż platformy Docker i platformy Docker Swarm) zamiast prostszy i łatwy w użyciu narzędzia docker-compose narzędzia na podstawie pliku definicji docker-compose.yml. Jednak dzięki zadanie wdrażania platformy Docker usług do programu Microsoft Azure DevOps pokazano na rysunku 5-10 teraz również można wdrożyć rozwiązania DC/OS za pomocą pliku docker-compose.yml znanych po prostu, ponieważ Microsoft przeprowadza "Translacja" (z usługi Plik docker-compose.yml w innych formatach, wymagane przez platformy DC/OS).

![](./media/image10.png)

Rysunek 5 – 10: Dodawanie zadania wdrażania platformy Docker do swojego menedżera zasobów w środowisku

Rysunek 5 – 11 pokazano, jak można edytować zadania wdrażania platformy Docker i określić typ docelowy (Azure Container Service DC/OS, w tym przypadku), plik Docker Compose i połączenie rejestru platformy Docker (np. usługi Azure Container Registry lub Docker Hub). Jest to, gdy zadanie pobiera gotowych do użycia niestandardowe obrazy usługi Docker do wdrożenia jako kontenery w klastrze DC/OS.

![](./media/image11.png)

Rysunek 5 – 11: Docker Wdróż zadań definicji wdrażania do Azure Container Service DC/OS

**Więcej informacji o** Aby dowiedzieć się więcej o potok ciągłego wdrażania za pomocą usługi DevOps platformy Azure i Docker, odwiedź następującą witrynę:

Rozszerzenie usługom DevOps platformy Azure dla platformy Docker i Azure Container Service: [ https://aka.ms/\ vstsdockerextension](https://aka.ms/vstsdockerextension)

Usługa Azure Container Service: <https://aka.ms/azurecontainerservice>

Mesosphere DC/OS: <https://mesosphere.com/product/>

## <a name="step-5-run-and-manage"></a>Krok 5. Uruchamianie i zarządzanie

Ponieważ uruchamianie aplikacji i zarządzanie nimi w środowisku produkcyjnym przedsiębiorstwa poziom jest główne tematu w i samego siebie oraz ze względu na rodzaj operacji, i ludzie przy pracy na tym samym poziomie (operacje IT) oraz duży zakres tego obszaru, firma Microsoft ma poświęcona całą obok rozdziału w celu objaśniające go.

## <a name="step-6-monitor-and-diagnose"></a>Krok 6. Monitorowanie i diagnozowanie

W tym temacie również jest objęte w następnym rozdziale zadań wykonywanych przez dział operacji IT w systemach produkcyjnych. jednak ważne jest wyróżnić szczegółowe dane uzyskane w tym kroku źródła musi danych do zespołu programistycznego, tak, aby stale zwiększona aplikacji. Z tego punktu widzenia, jest również częścią metodyki DevOps, chociaż zadania oraz operacje są zazwyczaj wykonywane przez IT.

Tylko w przypadku monitorowania i diagnostyki 100 procent, w obszarze metodyki DevOps są procesy monitorowania i analizy, wykonywane przez zespół programistyczny dla środowisk testowych lub wersji beta. Jest to realizowane przez wykonywanie testów obciążenia lub po prostu monitorowania w wersji beta lub odpowiedzi na pytania środowisk, w którym próbujesz się nowe wersje testerów wersji beta.

>[!div class="step-by-step"]
>[Poprzednie](index.md)
>[dalej](create-ci-cd-pipelines-azure-devops-services-aspnetcore-kubernetes.md)
