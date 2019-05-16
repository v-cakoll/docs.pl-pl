---
title: Kroki przepływu pracy DevOps w zewnętrznej pętli dla aplikacji platformy Docker
description: Poznaj procedurę "zewnętrzna pętla" przepływ pracy DevOps
ms.date: 02/15/2019
ms.openlocfilehash: 194786a90fc02801211c7614eb632392d67f0109
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641052"
---
# <a name="steps-in-the-outer-loop-devops-workflow-for-a-docker-application"></a>Kroki przepływu pracy DevOps w zewnętrznej pętli dla aplikacji platformy Docker

Rysunek 5-1 przedstawiono kroki przepływu pracy DevOps zewnętrzna pętla wchodzących w skład sceny end-to-end.

![Ten diagram przedstawia "zewnętrzna pętla" metodyki DevOps. Wypchnięcie kodu do repozytorium potoku ciągłej integracji jest uruchomiona, a następnie rozpoczyna się potok ciągłego wdrażania, w którym aplikacja zostanie wdrożona. Metryki zebrane z wdrożonych aplikacji są podawane na obciążenie programowanie, w którym występuje "wewnętrzną pętlę", więc zespoły programistyczne rzeczywistych danych, aby odpowiedzieć na użytkownika oraz o potrzebach biznesowych.](./media/image1.png)

**Rysunek 5-1**. Przepływ pracy zewnętrzna pętla DevOps dla aplikacji platformy Docker przy użyciu narzędzi firmy Microsoft

Teraz Przeanalizujmy każdy z tych kroków, które bardziej szczegółowo.

## <a name="step-1-inner-loop-development-workflow"></a>Krok 1. Przepływ pracy wewnętrznej pętli tworzenia kodu

Ten krok jest omówiona szczegółowo w rozdziale 4, ale aby podsumowanie, Oto gdzie zewnętrzna pętla rozpoczyna się, moment, w którym Deweloper wypycha kodu do systemu zarządzania kontrolą źródła (takich jak Git), inicjowanie działania potoku ciągłej integracji.

## <a name="step-2-source-code-control-integration-and-management-with-azure-devops-services-and-git"></a>Krok 2. Integracja kontroli kodu źródłowego i zarządzanie za pomocą usługi Azure DevOps Services i Git

W tym kroku musisz mieć systemu kontroli wersji, aby zebrać jednolity całego kodu pochodzących z różnych deweloperów w zespole.

Mimo, że kontrola kodu źródłowego (SCC) i kod źródłowy zarządzania mogą wydawać się charakter sekundy, przechodzić do większości deweloperów, podczas tworzenia aplikacji platformy Docker w życiu metodyki DevOps, warto podkreślić, że nie musisz przesłać obrazów platformy Docker z aplikacją bezpośrednio do globalnego rejestru platformy Docker (np. usługi Azure Container Registry lub Docker Hub) z komputera dewelopera. Przeciwnie obrazy platformy Docker, które są zwalniane i wdrażane do środowisk produkcyjnych należy utworzyć wyłącznie na kod źródłowy, który jest integrowany w ramach globalnego kompilacji lub potoku ciągłej integracji, oparte na repozytorium kodu źródłowego (takich jak Git).

Obrazów lokalnych, generowane przez deweloperów, powinny być używane tylko przez ich, podczas testowania w ramach ich własnych maszyn. Dlatego koniecznie mieć z potokiem metodyki DevOps, aktywowana z poziomu kodu SCC.

Usługa Azure DevOps usług i Team Foundation Server obsługuje Git i kontroli wersji serwera Team Foundation. Można wybrać między nimi i użyć jej do środowiska Microsoft end-to-end. Można jednak również mogą zarządzać kodu w repozytoriach zewnętrznych (takich jak GitHub, lokalne repozytoria Git i Subversion) i nadal mieć możliwość nawiązania połączenia i pobrania kodu jako punktu wyjścia dla potoku ciągłej integracji metodyki DevOps.

## <a name="step-3-build-ci-integrate-and-test-with-azure-devops-services-and-docker"></a>Krok 3. Tworzenie elementu konfiguracji, integracja i testowanie na platformie Azure DevOps usług i platformą Docker

Ciągła Integracja została uznana zawiera standardowe rozwiązanie dla nowoczesnych oprogramowania testowania i dostarczania. Rozwiązanie Docker przechowuje separacji między zespołami deweloperów i operacyjne. Niezmienność obrazów platformy Docker zapewnia powtarzalne wdrożenia między co został opracowany, przetestowane za pośrednictwem ciągłej integracji i uruchomić w środowisku produkcyjnym. Aparat platformy docker wdrożony na komputery przenośne dla deweloperów i infrastrukturę testowania sprawia, że kontenery przenośny między środowiskami.

W tym momencie po system kontroli wersji przy użyciu prawidłowego kodu przesłane, potrzebujesz *Tworzenie usługi* przejmą kod i uruchom testy i globalne kompilacji.

Wewnętrzny przepływu pracy dla tego kroku (ciągłej integracji, kompilacja, testowanie) jest informacje do budowy potoku ciągłej integracji, składający się z repozytorium kodu (Git itp.), serwer kompilacji (usługom DevOps platformy Azure), aparat platformy Docker i rejestr platformy Docker.

Umożliwia usługom DevOps platformy Azure jako podstawa do tworzenia aplikacji, a potok ciągłej integracji i publikowania "artefaktów kompilacji" "repozytorium artefaktów,", która została wyjaśniona w następnym kroku.

W przypadku używania platformy Docker dla wdrożenia "końcowe artefakty" do wdrożenia są obrazy platformy Docker do aplikacji lub usługi z osadzone wewnątrz nich. Te obrazy są wypychane lub opublikowane na *rejestru platformy Docker* (prywatne repozytorium, takich jak te mogą mieć w usłudze Azure Container Registry, lub publiczny podobny rejestru koncentratora platformy Docker, która jest powszechnie używana oficjalne obrazy podstawowej).

Poniżej przedstawiono podstawowe pojęcia: Potok ciągłej integracji będą się wyłączone przez zatwierdzenia do repozytorium SCC, takich jak Git. Zatwierdzenie spowoduje, że usługom DevOps platformy Azure Uruchom zadanie kompilacji w kontenerze platformy Docker, i po pomyślnym zakończeniu tego zadania, Wypchnij obraz platformy Docker do rejestru platformy Docker, jak pokazano w rysunek 5-2.

![Pierwsza część zewnętrzna pętla obejmuje kroki 1 – 3 z kodu, uruchamianie, debugować i następnie zweryfikować repozytorium kodu do kroku ciągłej integracji, kompilacji i testowania](./media/image2.png)

**Rysunek 5-2**. Kroki wykonywane w elemencie konfiguracji

Poniżej przedstawiono podstawowe kroki przepływu pracy ciągłej integracji z platformami Docker i usługom DevOps platformy Azure:

1. Deweloper wypycha zatwierdzenie do repozytorium SCC (Git/usług platformy Azure DevOps, GitHub itp.).

2. Jeśli używasz usługi Azure DevOps Services lub program Git, ciągła Integracja jest wbudowany, co oznacza, że jest tak proste, jak zaznaczenie pola wyboru w usługom DevOps platformy Azure. Jeśli używasz zewnętrznego SCC (na przykład GitHub) `webhook` będzie Powiadom usługom DevOps platformy Azure, aktualizacji lub Wypychanie do usługi Git/GitHub.

3. Usługi Azure DevOps ściąga SCC repozytorium, w tym pliku Dockerfile, zawierająca opis obrazu, a także kod aplikacji i testów.

4. Usługi Azure DevOps tworzy obraz platformy Docker i etykiet go numerem kompilacji.

5. Usługi Azure DevOps tworzy kontener platformy Docker w ramach elastycznie hosta platformy Docker i uruchamia odpowiednie testy.

6. Jeśli testy zakończą się powodzeniem, obraz jest najpierw relabeled na nazwę opisową, dzięki czemu będzie wiadomo, że jest "kompilacja specjalne" (np. "/ 1.0.0" lub inne etykiety), a następnie wypchnięto do rejestru platformy Docker (Docker Hub, Azure Container Registry, DTR itp.)

### <a name="implementing-the-ci-pipeline-with-azure-devops-services-and-the-docker-extension-for-azure-devops-services"></a>Wdrażania potoku ciągłej integracji, dzięki usługom DevOps platformy Azure oraz rozszerzenie Docker dla usługi DevOps platformy Azure

Usługom DevOps platformy Azure w usłudze Visual Studio zawiera kompilacji i szablony wydań, używanego w potoku ciągłej integracji/ciągłego wdrażania za pomocą którego można utworzyć obrazy platformy Docker, Wypchnij obrazy aparatu Docker do uwierzytelnionego rejestru platformy Docker, uruchamianie obrazów platformy Docker lub uruchamiania innych operacji oferowane przez Interfejs wiersza polecenia platformy Docker. Dodaje zadanie narzędzia Docker Compose, używanej do kompilacji, wypychania i uruchamianie aplikacji platformy Docker z wieloma kontenerami lub uruchomić inne operacje oferowane przez Docker Compose interfejsu wiersza polecenia, jak pokazano w rysunek 5-3.

![Widok przeglądarki potoku ciągłej integracji platformy Docker w infrastrukturze DevOps platformy Azure](./media/image3.png)

**Rysunek 5-3**. Potok ciągłej integracji platformy Docker w usługach Azure DevOps, kompilacji i szablonów wydań i skojarzonych zadań.

Można używać tych szablonów i zadania, które znajdują się do tworzenia artefaktów ciągłej integracji/ciągłego Dostarczania do tworzenia / testowania i wdrażania w usłudze Azure Service Fabric, Azure Kubernetes Service i podobne oferty.

Te zadania programu Visual Studio Team Services kompilacji hostów/maszyn wirtualnych systemu Linux Docker elastycznie na platformie Azure i preferowaną rejestru platformy Docker (usługi Azure Container Registry, Docker Hub, prywatne DTR platformy Docker lub dowolnego rejestru platformy Docker) można grupować w potoku ciągłej integracji platformy Docker bardzo spójny sposób.

***Wymagania:***

- Usługi DevOps platformy Azure lub w przypadku instalacji lokalnej, Team Foundation Server 2015 Update 3 lub nowszej.

- Agenta usługi DevOps platformy Azure, który ma pliki binarne platformy Docker.

  Prosty sposób utworzyć jedną z tych agentów jest korzystać z aparatu Docker w celu uruchomienia kontenera na podstawie obrazu platformy Docker agenta usługom DevOps platformy Azure.

> [! Informacje o] Aby przeczytać więcej na temat złożenia ciągłej integracji usługi Azure DevOps usług Docker potoku i wyświetlić przewodniki, odwiedź te witryny:
>
> - Uruchamianie agenta programu Visual Studio Team Services (teraz usługom DevOps platformy Azure) jako kontener platformy Docker: \
>   <https://hub.docker.com/_/microsoft-azure-pipelines-vsts-agent>
>
> - Tworzenie obrazów Docker systemu Linux w programie .NET Core dzięki usługom DevOps platformy Azure: \
>   <https://blogs.msdn.microsoft.com/stevelasker/2016/06/13/building-net-core-linux-docker-images-with-visual-studio-team-services/>
>
> - Tworzenie opartych na systemie Linux usługi Visual Studio Team kompilacji maszyny z obsługą platformy Docker: \
>   <http://donovanbrown.com/post/2016/06/03/Building-a-Linux-Based-Visual-Studio-Team-Service-Build-Machine-with-Docker-Support>

### <a name="integrate-test-and-validate-multi-container-docker-applications"></a>Integracja, testowanie i weryfikowanie aplikacji platformy Docker z wieloma kontenerami

Zazwyczaj większość aplikacji platformy Docker składają się z wielu kontenerów, a nie jeden kontener. Dobrym przykładem jest zorientowanych na mikrousługi aplikacji, dla którego trzeba jednego kontenera na mikrousługach. Ale nawet bez wyłącznie następujące wzorce podejście mikrousług, jest prawdopodobne, że aplikację platformy Docker może składać się z wielu kontenerów i usług.

W związku z tym po utworzeniu kontenerów aplikacji w potoku ciągłej integracji, trzeba będzie również wdrażać, integrowanie i testowanie aplikacji jako całości ze wszystkimi jego kontenerów w ramach integracji hosta platformy Docker lub nawet do klastra testowego, w jakim są usługi kontenerów rozproszone.

Jeśli używasz jednego hosta, możesz użyć poleceń Docker, takich jak platforma docker-compose, aby skompilować i wdrożyć powiązane kontenerów na potrzeby testowania i sprawdzania, czy środowisko platformy Docker w pojedynczej maszyny Wirtualnej. Jednak jeśli pracujesz z klastrem usługi orchestrator, np. DC/OS, Kubernetes lub Docker Swarm, zajdzie potrzeba wdrożenia kontenerów przy użyciu innego mechanizmu lub programu orchestrator, w zależności od wybranego klastra/harmonogramu.

Poniżej przedstawiono kilka rodzajów testów, które mogą być uruchamiane względem kontenerów platformy Docker:

- Testy jednostkowe dla kontenerów Docker

- Testowanie grup aplikacji połączonych ze sobą lub mikrousług

- Testowanie w produkcji i "kanarkiem" wersji

Istotną kwestią jest to, że podczas uruchamiania, integracji i testów funkcjonalnych, należy uruchomić te testy z poza kontenerów. Testy są nie zawarte lub w kontenerach, który jest wdrażany, ponieważ kontenery są oparte na obrazy statyczne, które powinny być dokładnie tak, jak te, które będziesz wdrażać do środowiska produkcyjnego.

Jest to praktyczne opcja podczas testowania bardziej zaawansowane scenariusze, takie jak z klastrami kilka (testowanie, klastra, klaster przemieszczania i w warunkach produkcyjnych klastra) opublikować obrazów do rejestru, dzięki czemu mogą być testowane w różnych klastrach.

### <a name="push-the-custom-application-docker-image-into-your-global-docker-registry"></a>Wypychanie obrazu platformy Docker niestandardowych aplikacji do globalnego rejestr platformy Docker

Po obrazów platformy Docker zostały przetestowane i zweryfikowane, należy je oznaczać i opublikuj je do rejestru platformy Docker. Rejestr platformy Docker jest krytycznego w cyklu życia aplikacji platformy Docker, ponieważ to centralne miejsce, w którym są przechowywane niestandardowe testu (znany także jako "specjalne obrazy") do wdrożenia w odpowiedzi na pytania i wdrożeń produkcyjnych.

Podobnie jak kod aplikacji, przechowywane w repozytorium SCC (Git itp.) jest "źródło prawdziwych informacji", rejestr platformy Docker jest "źródłem prawdziwych" binarnych aplikacji lub usługi bits do wdrożenia środowiska QA lub produkcja.

Zazwyczaj warto mieć prywatnych repozytoriów dla obrazów niestandardowych w prywatnym repozytorium w usłudze Azure Container Registry lub rejestru lokalnych, takich jak Docker Trusted Registry lub rejestru chmury publicznej z ograniczonym dostępem (np. Usługi docker Hub), chociaż w tym ostatnim przypadku, jeśli kod nie jest typu open source, muszą ufać zabezpieczeń dostawcy. W obu przypadkach używane jest podobny i opiera się na `docker push` polecenia, jak pokazano na rysunku 5-4.

![W kroku 3, tworzenia integracji i testowania (CI) możesz opublikować wynikowy obrazów platformy docker do rejestru prywatnej lub publicznej.](./media/image4.png)

**Rysunek 5-4**. Publikowanie niestandardowych obrazów do rejestru platformy Docker

Istnieje wiele ofert z rejestrów platformy Docker z dostawców chmury, takich jak usługa Azure Container Registry, Amazon Web Services Container Registry, Google Container Registry, rejestr nabrzeża i tak dalej.

Przy użyciu zadań platformy Docker, możesz wypchnąć zestaw obrazów usługi zdefiniowane przez `docker-compose.yml` plików za pomocą wielu tagów do uwierzytelnionego rejestru platformy Docker (np. usługi Azure Container Registry), jak pokazano na rysunku 5-5.

![Widok przeglądarkę krok w celu publikowania obrazów do rejestru z DevOps platformy Azure.](./media/image5.png)

**Rysunek 5-5**. Publikowanie niestandardowych obrazów do rejestru platformy Docker przy użyciu usługi DevOps platformy Azure

> [! Informacje o] Aby uzyskać więcej informacji na temat usługi Azure Container Registry, zobacz <https://aka.ms/azurecontainerregistry>.

## <a name="step-4-cd-deploy"></a>Krok 4. Ciągłe wdrażanie, wdrażanie

Niezmienność obrazów platformy Docker zapewnia powtarzalne wdrożenia za pomocą co został opracowany, przetestowane za pośrednictwem ciągłej integracji i uruchomić w środowisku produkcyjnym. Po utworzeniu aplikacji obrazów platformy Docker, opublikowane w rejestrze Docker (prywatnej lub publicznej), można wdrożyć je do kilku środowiskach, które mogą wystąpić (produkcyjne, QA, przemieszczania, itp.) z potok ciągłego wdrażania za pomocą usługi DevOps platformy Azure zadania potoku lub usługi Azure DevOps usługi Release Management.

Jednak w tym momencie to zależy od rodzaju aplikację platformy Docker jest wdrażany. Wdrażając prostą aplikację (z tworzenia i wdrażania punktu widzenia) takich jak monolitycznych aplikacji wchodzących w skład kilku kontenerów lub usług i wdrożone na kilku serwerach lub maszynach wirtualnych jest inna niż wdrażanie bardziej złożonych aplikacji, takich jak zorientowanych na mikrousługi aplikacji z możliwościami w hiperskali. W poniższych sekcjach opisano te dwa scenariusze.

### <a name="deploying-composed-docker-applications-to-multiple-docker-environments"></a>Wdrażanie składa się z aplikacji platformy Docker w wielu środowiskach platformy Docker

Przyjrzyjmy się pierwsze u scenariusz mniej złożone: Wdrażanie prostego hostów platformy Docker (maszyn wirtualnych lub serwerach) w ramach jednego środowiska lub do wielu środowisk (kontroli jakości, środowisk przejściowych i produkcyjnych). W tym scenariuszu wewnętrznie potok ciągłego Dostarczania można używać platformy docker-compose (z zadań wdrożenia usługom DevOps platformy Azure) do wdrożenia przy użyciu jego powiązany zestaw aplikacji platformy Docker, kontenery lub usługi, tak jak przedstawiono to w rysunek 5 – 6.

![Wdrażanie dysku CD kroku (4) można publikować w różnych środowiskach, takich jak q &, środowisk przejściowych i produkcyjnych.](./media/image6.png)

**Rysunek 5 i 6-**. Wdrażanie aplikacji kontenerów do prostych rejestru środowiska hosta platformy Docker

Rysunek 5 – 7 pokazuje, jak połączyć kompilacji ciągłej integracji do odpowiedzi na pytania/testowym za pośrednictwem usługi DevOps platformy Azure, klikając pozycję Narzędzia Docker Compose w oknie dialogowym Dodaj zadanie. Jednak w przypadku wdrażania w środowiskach przejściowych lub produkcyjnych, zazwyczaj używasz funkcji Release Management, obsługa wielu środowisk (takich jak pytań i odpowiedzi, środowisk przejściowych i produkcyjnych). Jeśli wdrażasz do pojedynczego hostów platformy Docker, jest za pomocą usługi Azure DevOps zadanie "Narzędzia Docker Compose" (który wywołuje `docker-compose up` polecenia kulisy). Jeśli wdrażasz do usługi Azure Container Service używa zadania wdrażania platformy Docker, jak wyjaśniono w poniższej sekcji.

![Wyświetlany w przeglądarce widok dodawania zadania narzędzia Docker Compose.](./media/image7.png)

**Rysunek 5 – 7**. Dodanie zadania narzędzia Docker Compose w potoku usługi Azure DevOps usług

Po utworzeniu wydania w usługom DevOps platformy Azure ma zbiór wejściowy artefaktów. Te artefakty są przeznaczone do być niezmienialne okres istnienia wersji, we wszystkich środowiskach. Po wprowadzeniu kontenerów, danych wejściowych artefaktów zidentyfikować obrazów w rejestrze, aby wdrożyć. W zależności od tego, jak te obrazy są identyfikowane, mają nie gwarancję, że pozostają takie same, w okresie obowiązywania wersji najbardziej oczywiste przypadków są Gdy odwołujesz się `myimage:latest` z `docker-compose` pliku.

Szablony usług DevOps platformy Azure generuje skróty służące możliwość generowania artefaktów kompilacji, które zawiera obrazu określonego rejestru, które gwarantują do unikatowej identyfikacji tego samego obrazu binarnego. Są to, co naprawdę chcesz użyć jako dane wejściowe do wydania.

### <a name="managing-releases-to-docker-environments-by-using-azure-devops-services-release-management"></a>Zarządzanie wersjami w środowiskach platformy Docker przy użyciu usługi Azure DevOps usługi Release Management

Za pomocą szablonów usługi DevOps platformy Azure, można utworzyć nowy obraz, opublikuj go do rejestru platformy Docker, uruchom go na hostach z systemem Linux lub Windows i używać poleceń, takich jak `docker-compose` do wdrożenia wielu kontenerów jako całej aplikacji, wspomaga DevOps platformy Azure Możliwości zarządzania wydaniami przeznaczonych dla wielu środowisk usług, jak pokazano w rysunek 5 – 8.

![Widok przeglądarki DevOps platformy Azure, konfigurowanie platformy Docker compose wydań.](./media/image8.png)

**Rysunek 5 – 8**. Konfigurowanie usługi Azure DevOps usług narzędzia Docker Compose zadań przy użyciu usługi Azure DevOps usługi Release Management

Jednak należy pamiętać o tym, czy scenariusz pokazano w rysunek 5 i 6- i wdrażane w rysunek 5 – 8 jest proste (jest wdrożenie jednego hostów platformy Docker i maszynom wirtualnym i będzie jeden kontener i wystąpienie na obrazie) i prawdopodobnie powinna być używana tylko w przypadku projektowania lub testowania sce narios. W większości scenariuszy produkcyjnych przedsiębiorstwa, chcesz mieć wysokiej dostępności (HA) i łatwe w zarządzaniu skalowalności, równoważeniem obciążenia na wiele węzłów, serwerów i maszyn wirtualnych, a także "inteligentne przejścia w tryb failover" więc jeśli serwerze lub w węźle nie powiedzie się, jej usług i kontenerów zostanie przeniesiony do innego serwera hosta lub maszyny Wirtualnej. W takim przypadku potrzebujesz bardziej zaawansowanych technologii, takich jak klastry kontenerów, koordynatorów i transfery danych. W związku z tym sposób wdrażania tych klastrach dzięki obsłudze zaawansowanych scenariuszy opisanej w następnej sekcji.

### <a name="deploying-docker-applications-to-docker-clusters"></a>Wdrażanie aplikacji platformy Docker z klastrami platformy Docker

Rodzaj aplikacji rozproszonych wymaga zasobów obliczeniowych, które są rozpowszechniane. Zapewnienie możliwości skalowania w środowisku produkcyjnym, musisz mieć, klastrowanie możliwości, które zapewniają wysoką skalowalność i wysoką dostępność na podstawie puli zasobów.

Można wdrożyć kontenery ręcznie do tych klastrów z narzędzia interfejsu wiersza polecenia lub internetowy interfejs użytkownika, ale powinno się zarezerwować tego rodzaju ręcznych do testowania wdrożenia dodatkowych lub zarządzania nim, takie jak skalowanie w poziomie lub monitorowania.

Z punktu widzenia ciągłego Dostarczania i usługom DevOps platformy Azure w szczególności można uruchamiać zadania specjalnie wykonane wdrożenia ze środowiska usługi Azure DevOps usługi Release Management, które zostaną wdrożone w klastrach rozproszonych w kontenerze aplikacji konteneryzowanych Usługi, jak pokazano w rysunek 5-9.

![Wdrażanie dysku CD kroku (4) można również publikować z klastrami przy użyciu koordynatorów.](./media/image9.png)

**Rysunek 5-9**. Wdrażanie aplikacji rozproszonych w usłudze Container Service

Początkowo podczas wdrażania aplikacji na niektórych klastrów lub koordynatorów, tradycyjnie używasz skryptów wdrażania i mechanizmy na poszczególnych koordynatorów, (oznacza to, Kubernetes i usługi Service Fabric mają mechanizmy innego wdrożenia) zamiast prostszej i łatwy w użyciu `docker-compose` narzędzie oparte na `docker-compose.yml` pliku definicji. Jednak dzięki gotowej do zadania usługi Azure DevOps usług wdrażana w rozwiązaniu Docker pokazano na rysunku 5-10, teraz również można wdrożyć obsługiwanych koordynatorów korzystając tylko z powszechnie znane `docker-compose.yml` plik odgrywa narzędzie "Translacja" (z Twojej `docker-compose.yml`plik do formatu wymagane przez program orchestrator).

![Zadanie wdrażania widok wykazu zadań w infrastrukturze DevOps platformy Azure, przedstawiający platformy Docker w przeglądarce.](./media/image10.png)

**Rysunek 5 – 10**. Dodawanie zadania wdrażania platformy Docker do swojego menedżera zasobów w środowisku

Rysunek 5 – 11 pokazano, jak można edytować zadania wdrażania platformy Docker i określić typ docelowy (Azure Container Service DC/OS, w tym przypadku), plik Docker Compose i połączenie rejestru platformy Docker (np. usługi Azure Container Registry lub Docker Hub). To zadanie, które pobierze gotowych do użycia niestandardowe obrazy usługi Docker zostać wdrożony jako kontenery w klastrze.

![Widok przeglądarki DevOps platformy Azure, Wdróż definicji zadania programu orchestrator.](./media/image11.png)

**Rysunek 5 – 11**. Docker Wdróż zadań definicji wdrażania do Azure Container Service DC/OS

> [! Informacje o] Aby dowiedzieć się więcej o potok ciągłego wdrażania za pomocą usługi DevOps platformy Azure i Docker, odwiedź <https://azure.microsoft.com/services/devops/pipelines>

## <a name="step-5-run-and-manage"></a>Krok 5. Uruchamianie i zarządzanie

Ponieważ uruchamianie aplikacji i zarządzanie nimi w środowisku produkcyjnym przedsiębiorstwa poziom jest główne tematu w i samego siebie oraz ze względu na rodzaj operacji, i ludzie przy pracy na tym samym poziomie (operacje IT) oraz duży zakres tego obszaru, cały następny rozdział jest poświęcona to wyjaśniać.

## <a name="step-6-monitor-and-diagnose"></a>Krok 6. Monitorowanie i diagnozowanie

W tym temacie jest również przedstawione w następnym rozdziale jako część zadania jej wykonuje w systemach produkcyjnych. jednak ważne jest wyróżnić szczegółowe dane uzyskane w tym kroku źródła musi danych do zespołu programistycznego, tak, aby stale zwiększona aplikacji. Z tego punktu widzenia, jest również częścią metodyki DevOps, chociaż zadania oraz operacje najczęściej są wykonywane przez IT.

Tylko wtedy, gdy monitorowania i diagnostyki są w 100% w obrębie obszaru DevOps są procesy monitorowania i analizy, wykonywane przez zespół programistyczny dla środowisk testowych lub wersji beta. Jest to realizowane przez wykonywanie testów obciążenia lub przez monitorowanie w wersji beta lub odpowiedzi na pytania środowisk, w którym próbujesz się nowe wersje testerów wersji beta.

>[!div class="step-by-step"]
>[Poprzednie](index.md)
>[dalej](create-ci-cd-pipelines-azure-devops-services-aspnetcore-kubernetes.md)
