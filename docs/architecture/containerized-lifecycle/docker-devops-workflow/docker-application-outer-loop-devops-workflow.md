---
title: Kroki przepływu pracy DevOps w zewnętrznej pętli dla aplikacji platformy Docker
description: Zapoznaj się z instrukcjami "zewnętrznej pętli" przepływu pracy DevOps
ms.date: 02/15/2019
ms.openlocfilehash: 44bd73bf88a743e5350e422d3ea000ca075f7383
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "82021299"
---
# <a name="steps-in-the-outer-loop-devops-workflow-for-a-docker-application"></a>Kroki przepływu pracy DevOps w zewnętrznej pętli dla aplikacji platformy Docker

Rysunek 5-1 przedstawia end-to-end obraz kroków składających devops przepływu pracy pętli zewnętrznej. Pokazuje "zewnętrzną pętlę" DevOps. Gdy kod jest wypychany do repozytorium, potok ciągłej integracji jest uruchamiany, a następnie rozpoczyna potok dysku CD, w którym zostanie wdrożona aplikacja. Metryki zebrane z wdrożonych aplikacji są przekazywane z powrotem do obciążenia programistycznego, gdzie występuje "wewnętrzna pętla", więc zespoły programistyczne mają rzeczywiste dane, aby odpowiedzieć na potrzeby użytkowników i firm.

![Diagram przedstawiający 6 kroków przepływu pracy pętli zewnętrznej DevOps.](./media/docker-application-outer-loop-devops-workflow/overview-dev-ops-outter-loop-workflow.png)

**Rysunek 5-1**. Przepływ pracy pętli zewnętrznej DevOps dla aplikacji platformy Docker za pomocą narzędzi firmy Microsoft

Teraz przyjrzyjmy się każdej z tych kroków bardziej szczegółowo.

## <a name="step-1-inner-loop-development-workflow"></a>Krok 1: Przepływ pracy tworzenia pętli wewnętrznej

Ten krok jest szczegółowo wyjaśnione w rozdziale 4, ale, podsumowując, tutaj jest, gdzie rozpoczyna się zewnętrzna pętla, w momencie, w którym deweloper wypycha kod do systemu zarządzania kontrolą źródła (jak Git) inicjowania akcji potoku ciągłej.

## <a name="step-2-source-code-control-integration-and-management-with-azure-devops-services-and-git"></a>Krok 2: Integracja i zarządzanie kontrolą kodu źródłowego za pomocą usług DevOps Azure i git

W tym kroku musisz mieć system kontroli wersji, aby zebrać skonsolidowaną wersję całego kodu pochodzącego od różnych deweloperów w zespole.

Mimo że kontrola kodu źródłowego (SCC) i zarządzanie kodem źródłowym może wydawać się drugorzędne dla większości deweloperów, podczas tworzenia aplikacji platformy Docker w cyklu życia DevOps, ważne jest, aby podkreślić, że nie należy przesyłać obrazów platformy Docker z aplikacją bezpośrednio do globalnego rejestru platformy Docker (takich jak Azure Container Registry lub Docker Hub) z komputera dewelopera. Wręcz przeciwnie obrazy platformy Docker, które mają zostać wydane i wdrożone w środowiskach produkcyjnych, muszą być tworzone wyłącznie na kodzie źródłowym, który jest zintegrowany z globalną kompilacją lub potokiem ciągłej integracji na podstawie repozytorium kodu źródłowego (takiego jak Git).

Obrazy lokalne, generowane przez deweloperów, powinny być używane przez nich podczas testowania w ramach własnych maszyn. Dlatego bardzo ważne jest, aby potok DevOps był aktywowany z kodu SCC.

Usługi Azure DevOps i serwer Team Foundation obsługują kontrolę wersji git i team foundation. Można wybrać między nimi i używać go do kompleksowego środowiska firmy Microsoft. Można jednak również zarządzać kodem w zewnętrznych repozytoriach (takich jak GitHub, lokalne repozytoria Git lub Subversion) i nadal można się z nim połączyć i uzyskać kod jako punkt wyjścia dla potoku ciągłej ewidencji DevOps.

## <a name="step-3-build-ci-integrate-and-test-with-azure-devops-services-and-docker"></a>Krok 3: Tworzenie, ci, integracja i testowanie za pomocą usług Azure DevOps i platformy Docker

Ci stał się standardem dla nowoczesnych testów oprogramowania i dostarczania. Rozwiązanie platformy Docker utrzymuje wyraźny rozdzielenie problemów między zespołami deweloperów i operacji. Niezmienność obrazów platformy Docker zapewnia powtarzalne wdrożenie między tym, co jest opracowane, przetestowane za pośrednictwem ciągłej integracji i uruchamiane w produkcji. Aparat platformy Docker wdrożony w komputerach przenośnych deweloperów i infrastruktury testowej sprawia, że kontenery są przenośne w różnych środowiskach.

W tym momencie po systemie kontroli wersji z poprawnym kodem przesłane, trzeba *usługi kompilacji,* aby odebrać kod i uruchomić globalnej kompilacji i testów.

Wewnętrzny przepływ pracy dla tego kroku (CI, kompilacja, test) dotyczy budowy potoku ciągłej integracji składającego się z repozytorium kodu (Git itp.), serwera kompilacji (usługi Azure DevOps), aparatu platformy Docker engine i rejestru platformy Docker.

Usługi Azure DevOps można używać jako podstawy do tworzenia aplikacji i ustawiania potoku ciągłej integracji oraz publikowania wbudowanych "artefaktów" w "repozytorium artefaktów", co wyjaśniono w następnym kroku.

Podczas korzystania z platformy Docker do wdrożenia, "ostateczne artefakty", które mają zostać wdrożone są obrazy platformy Docker z aplikacji lub usług osadzonych w nich. Te obrazy są wypychane lub publikowane w rejestrze platformy *Docker* (prywatne repozytorium, takie jak te, które można mieć w usłudze Azure Container Registry lub publiczne, takie jak docker hub registry, który jest powszechnie używany dla oficjalnych obrazów podstawowych).

Oto podstawowa koncepcja: Potok ciągłej integracji zostanie rozpoczęty przez zatwierdzenie do repozytorium SCC, takiego jak Git. Zatwierdzenie spowoduje, że usługi Azure DevOps Services do uruchomienia zadania kompilacji w kontenerze platformy Docker i po pomyślnym zakończeniu tego zadania wypchnąć obraz platformy Docker do rejestru platformy Docker, jak pokazano na rysunku 5-2. Pierwsza część pętli zewnętrznej obejmuje kroki 1 do 3, od kodu, uruchom, debugowania i sprawdzania poprawności, a następnie repozytorium kodu do kroku kompilacji i testowania ci.

![Diagram przedstawiający trzy kroki związane z przepływem pracy ciągłej integracji.](./media/docker-application-outer-loop-devops-workflow/continuous-integration-steps.png)

**Rysunek 5-2**. Kroki związane z ci

Oto podstawowe kroki przepływu pracy w zakresie ciągłej integracji za pomocą usług Docker i Azure DevOps:

1. Deweloper wypycha zatwierdzenie do repozytorium SCC (Usługi Git/Azure DevOps, GitHub itp.).

2. Jeśli używasz usługi Azure DevOps services lub Git, ci jest wbudowany, co oznacza, że jest tak proste, jak zaznaczenie pola wyboru w usługach Azure DevOps. Jeśli używasz zewnętrznego SCC (takiego jak GitHub), a `webhook` powiadomi usługi Azure DevOps o aktualizacji lub wypchniesz do git/GitHub.

3. Usługi Azure DevOps pobiera repozytorium SCC, w tym Dockerfile opisujące obraz, a także kod aplikacji i testów.

4. Usługi Azure DevOps tworzy obraz platformy Docker i etykiety go z numerem kompilacji.

5. Usługi Azure DevOps services wystąpienia kontenera platformy Docker w ramach aprowizacji hosta platformy Docker i uruchamia odpowiednie testy.

6. Jeśli testy się powiodą, obraz zostanie najpierw przeliczony do znaczącej nazwy, aby wiedzieć, że jest to "błogosławiona kompilacja" (np. "/1.0.0" lub inna etykieta), a następnie wypchnięty do rejestru platformy Docker (Docker Hub, Azure Container Registry, DTR itp.)

### <a name="implementing-the-ci-pipeline-with-azure-devops-services-and-the-docker-extension-for-azure-devops-services"></a>Implementowanie potoku ciągłej integracji za pomocą usług DevOps azure i rozszerzenia platformy Docker dla usług Azure DevOps

Visual Studio Azure DevOps Services zawiera szablony kompilacji & wersji, które można użyć w potoku ciągłej integracji/ciągłego wdrażania, za pomocą którego można tworzyć obrazy platformy Docker, wypychać obrazy platformy Docker do uwierzytelnionego rejestru platformy Docker, uruchamiać obrazy platformy Docker lub uruchamiać inne operacje oferowane przez wiersz polecenia platformy Docker. Dodaje również zadanie docker compose, którego można użyć do tworzenia, wypychania i uruchamiania aplikacji platformy Docker z wieloma kontenerami lub uruchamiania innych operacji oferowanych przez interfejsu wiersza polecenia docker compose, jak pokazano na rysunku 5-3.

![Zrzut ekranu przedstawiający potok docker CI w usłudze Azure DevOps.](./media/docker-application-outer-loop-devops-workflow/docker-ci-pipeline-azure-devops.png)

**Rysunek 5-3**. Potok docker CI w usługach Azure DevOps, w tym tworzenie szablonów & wersji i skojarzonych zadań.

Za pomocą tych szablonów i zadań można tworzyć artefakty ciągłej integracji/ciągłego wdrażania do kompilacji/testowania i wdrażania w usłudze Azure Service Fabric, usłudze Azure Kubernetes i podobnych ofertach.

Dzięki tym zadaniom programu Visual Studio Team Services kompilacja hosta/maszyny wirtualnej linux-docker aprowizowana na platformie Azure i preferowany rejestr platformy Docker (Azure Container Registry, Docker Hub, private Docker DTR lub inny rejestr platformy Docker) można zebrać potoku docker CI w bardzo spójny sposób.

***Wymagania:***

- Usługi Azure DevOps lub dla instalacji lokalnych, Team Foundation Server 2015 Update 3 lub nowsze.

- Agent usługi Azure DevOps services, który ma pliki binarne platformy Docker.

  Łatwym sposobem utworzenia jednego z tych agentów jest użycie platformy Docker do uruchamiania kontenera na podstawie obrazu platformy Docker agenta usługi Azure DevOps.

> [! INFORMACJE] Aby dowiedzieć się więcej na temat składania potoku docker ci usług Deweloperów platformy Azure i wyświetlić wskazówki, odwiedź następujące witryny:
>
> - Uruchamianie agenta usługi zespołu programu Visual Studio (teraz usługi Azure DevOps) jako kontenera platformy Docker: \
>   <https://hub.docker.com/_/microsoft-azure-pipelines-vsts-agent>
>
> - Tworzenie obrazów platformy Docker .NET Core Linux za pomocą usług Azure DevOps: \
>   <https://docs.microsoft.com/archive/blogs/stevelasker/building-net-core-linux-docker-images-with-visual-studio-team-services>
>
> - Tworzenie komputera kompilacji usługi Visual Studio z systemem Linux z obsługą platformy Docker: \
>   <http://donovanbrown.com/post/2016/06/03/Building-a-Linux-Based-Visual-Studio-Team-Service-Build-Machine-with-Docker-Support>

### <a name="integrate-test-and-validate-multi-container-docker-applications"></a>Integracja, testowanie i sprawdzanie poprawności aplikacji platformy Docker z wieloma kontenerami

Zazwyczaj większość aplikacji platformy Docker składa się z wielu kontenerów, a nie z jednego kontenera. Dobrym przykładem jest aplikacja zorientowana na mikrousługi, dla której można mieć jeden kontener na mikrousługi. Ale nawet bez ścisłego po mikrousług wzorców podejścia, jest prawdopodobne, że aplikacja platformy Docker będzie składać się z wielu kontenerów lub usług.

W związku z tym po tworzeniu kontenerów aplikacji w potoku ciągłej integracji należy również wdrożyć, zintegrować i przetestować aplikację jako całość ze wszystkimi jej kontenerami w ramach platformy Docker integracji lub nawet do klastra testowego, do którego kontenery są dystrybuowane.

Jeśli używasz jednego hosta, można użyć poleceń platformy Docker, takich jak docker-compose do tworzenia i wdrażania powiązanych kontenerów do testowania i sprawdzania poprawności środowiska platformy Docker w jednej maszynie wirtualnej. Ale jeśli pracujesz z klastra orkiestratora, takich jak DC/OS, Kubernetes lub Docker Swarm, należy wdrożyć kontenery za pomocą innego mechanizmu lub orchestrator, w zależności od wybranego klastra/harmonogramu.

Poniżej przedstawiono kilka typów testów, które można uruchomić w kontenerach platformy Docker:

- Testy jednostkowe kontenerów platformy Docker

- Grupy testowe powiązanych ze sobą aplikacji lub mikrousług

- Test w produkcji i "kanarek" zwalnia

Ważne jest to, że podczas uruchamiania integracji i testów funkcjonalnych, należy uruchomić te testy spoza kontenerów. Testy nie są zawarte lub uruchamiane w kontenerach, które wdrażasz, ponieważ kontenery są oparte na statycznych obrazach, które powinny być dokładnie takie, jak te, które będą wdrażane w procesach produkcyjnych.

Praktyczną opcją podczas testowania bardziej zaawansowanych scenariuszy, takich jak włączenie kilku klastrów (klastra testowego, klastra przemieszczania i klastra produkcyjnego) jest opublikowanie obrazów w rejestrze, dzięki czemu można je przetestować w różnych klastrach.

### <a name="push-the-custom-application-docker-image-into-your-global-docker-registry"></a>Wypychanie niestandardowego obrazu platformy Docker aplikacji do globalnego rejestru platformy Docker

Po przetestowaniu i sprawdzeniu obrazów platformy Docker należy oznaczyć je i opublikować w rejestrze platformy Docker. Rejestr platformy Docker jest krytycznym elementem w cyklu życia aplikacji platformy Docker, ponieważ jest to centralne miejsce przechowywania testu niestandardowego (znanego również jako "błogosławione obrazy"), który ma zostać wdrożony w środowiskach kontroli jakości i środowiskach produkcyjnych.

Podobnie jak kod aplikacji przechowywany w repozytorium SCC (Git, itp.) jest "źródłem prawdy", rejestr platformy Docker jest "źródłem prawdy" dla aplikacji binarnej lub bitów, które mają być wdrożone w qa lub środowiskach produkcyjnych.

Zazwyczaj można mieć prywatne repozytoria obrazów niestandardowych albo w prywatnym repozytorium w usłudze Azure Container Registry lub w rejestrze lokalnym, takim jak Zaufany rejestr platformy Docker, lub w rejestrze chmury publicznej z ograniczonym dostępem (takim jak Docker Hub), chociaż w tym ostatnim przypadku, jeśli kod nie jest open source, należy ufać bezpieczeństwu dostawcy. Tak czy inaczej, metoda, której używasz `docker push` jest podobna i opiera się na poleceniu, jak pokazano na rysunku 5-4.

![Diagram przedstawiający wypychanie obrazów niestandardowych do rejestru kontenerów.](./media/docker-application-outer-loop-devops-workflow/docker-push-custom-images.png)

**Rysunek 5-4**. Publikowanie obrazów niestandardowych w rejestrze platformy Docker

W kroku 3 do tworzenia integracji i testowania (CI) można opublikować wynikowe obrazy platformy docker do rejestru prywatnego lub publicznego. Istnieje wiele ofert rejestrów platformy Docker od dostawców chmury, takich jak Azure Container Registry, Amazon Web Services Container Registry, Google Container Registry, Quay Registry i tak dalej.

Za pomocą zadań platformy Docker można wypchnąć `docker-compose.yml` zestaw obrazów usług zdefiniowanych przez plik, z wieloma tagami, do uwierzytelnionego rejestru platformy Docker (takiego jak usługa Azure Container Registry), jak pokazano na rysunku 5-5.

![Zrzut ekranu przedstawiający krok do publikowania obrazów w rejestrze.](./media/docker-application-outer-loop-devops-workflow/publish-custom-image-to-docker-registry.png)

**Rysunek 5-5**. Używanie usług DevOps platformy Azure do publikowania obrazów niestandardowych w rejestrze platformy Docker

> [! INFORMACJE] Aby uzyskać więcej informacji <https://aka.ms/azurecontainerregistry>na temat rejestru kontenerów platformy Azure, zobacz .

## <a name="step-4-cd-deploy"></a>Krok 4: CD, Wdrażanie

Niezmienność obrazów platformy Docker zapewnia powtarzalne wdrożenie z tym, co jest opracowywane, testowane za pośrednictwem ciągłej integracji i uruchamiane w produkcji. Po opublikowaniu obrazów platformy Docker aplikacji w rejestrze platformy Docker (prywatnych lub publicznych) można wdrożyć je w kilku środowiskach, które mogą mieć (produkcja, kontrola jakości, przemieszczania itp.) z potoku dysku CD przy użyciu zadań potoku usług Azure DevOps lub usługi Azure DevOps Release Management.

Jednak w tym momencie zależy od tego, jaki rodzaj aplikacji platformy Docker wdrażasz. Wdrażanie prostej aplikacji (z punktu widzenia kompozycji i wdrażania) jak monolityczne aplikacji składającej się z kilku kontenerów lub usług i wdrożony na kilku serwerach lub maszyn wirtualnych różni się od wdrażania bardziej złożonych aplikacji, takich jak aplikacja zorientowana na mikrousługi z możliwością hiperskali. Te dwa scenariusze są wyjaśnione w poniższych sekcjach.

### <a name="deploying-composed-docker-applications-to-multiple-docker-environments"></a>Wdrażanie złożonych aplikacji platformy Docker w wielu środowiskach platformy Docker

Przyjrzyjmy się najpierw mniej złożonemu scenariuszowi: wdrażanie na prostych hostach platformy Docker (maszyny wirtualne lub serwery) w jednym środowisku lub wielu środowiskach (qa, przemieszczania i produkcji). W tym scenariuszu wewnętrznie potoku dysku CD można użyć docker-compose (z zadań wdrażania usługi Azure DevOps Services) do wdrażania aplikacji platformy Docker z powiązanym zestawem kontenerów lub usług, jak pokazano na rysunku 5-6.

![Diagram przedstawiający krok wdrażania dysku CD w trzech środowiskach.](./media/docker-application-outer-loop-devops-workflow/deploy-app-containers-to-docker-host-environments.png)

**Rysunek 5-6**. Wdrażanie kontenerów aplikacji w prostym rejestrze środowisk hosta platformy Docker

Rysunek 5-7 podkreśla, jak można połączyć kompilacji CI do środowiska QA/test za pośrednictwem usługi Azure DevOps Services, klikając docker compose w oknie dialogowym Dodawanie zadania. Jednak podczas wdrażania w środowiskach przejściowych lub produkcyjnych zwykle należy używać funkcji zarządzania wersjami obsługujących wiele środowisk (takich jak kontrola jakości, przemieszczania i produkcji). Jeśli wdrażasz do pojedynczych hostów platformy Docker, używa zadania "Docker Compose" usług Azure `docker-compose up` DevOps (które wywołuje polecenie pod maską). Jeśli wdrażasz w usłudze Azure Kubernetes Service (AKS), używa zadania wdrażania platformy Docker, jak wyjaśniono w sekcji, która jest następująca.

![Zrzut ekranu przedstawiający okno dialogowe Dodawanie zadań zadania dok.](./media/docker-application-outer-loop-devops-workflow/add-tasks-docker-compose.png)

**Rysunek 5-7**. Dodawanie zadania dokowania compose w potoku usług Azure DevOps

Podczas tworzenia wersji w usłudze Azure DevOps Services, trwa zestaw artefaktów wejściowych. Te artefakty są przeznaczone do niezmienne przez cały okres istnienia wydania, we wszystkich środowiskach. Po wprowadzeniu kontenerów artefakty wejściowe identyfikują obrazy w rejestrze do wdrożenia. W zależności od sposobu identyfikacji tych obrazów nie są one gwarantowane, aby pozostać takie same przez `myimage:latest` cały `docker-compose` czas trwania wydania, najbardziej oczywistym przypadkiem jest odwołanie z pliku.

Szablony usług DevOps platformy Azure umożliwiają generowanie artefaktów kompilacji, które zawierają określone skróty obrazów rejestru, które są gwarantowane, aby jednoznacznie zidentyfikować ten sam plik binarny obrazu. Są to, co naprawdę chcesz użyć jako dane wejściowe do wydania.

### <a name="managing-releases-to-docker-environments-by-using-azure-devops-services-release-management"></a>Zarządzanie wersjami do środowisk platformy Docker przy użyciu zarządzania wersjami usług Azure DevOps

Za pomocą szablonów usług Azure DevOps można utworzyć nowy obraz, opublikować go w rejestrze platformy Docker, `docker-compose` uruchomić go na platformie Linux lub Windows hosts i używać poleceń, takich jak wdrożenie wielu kontenerów jako całej aplikacji, wszystko za pośrednictwem funkcji zarządzania wersjami usługi Azure DevOps przeznaczone dla wielu środowisk, jak pokazano na rysunku 5-8.

![Zrzut ekranu przedstawiający konfigurację wersji kompozycji docker.](./media/docker-application-outer-loop-devops-workflow/configure-docker-compose-release.png)

**Rysunek 5-8**. Konfigurowanie zadań dokowania usługi Azure DevOps compose z zarządzania wydaniami usług Azure DevOps

Należy jednak pamiętać, że scenariusz pokazany na rysunku 5-6 i zaimplementowany na rysunku 5-8 jest prosty (wdrażany na pojedynczych hostach platformy Docker i maszynach wirtualnych i będzie jeden kontener lub wystąpienie na obraz) i prawdopodobnie powinien być używany tylko do scenariuszy programistycznych lub testowych. W większości scenariuszy produkcyjnych przedsiębiorstwa chcesz mieć wysoką dostępność (HA) i łatwe w zarządzaniu skalowalność przez równoważenie obciążenia w wielu węzłach, serwerach i maszynach wirtualnych oraz "inteligentne tryb failovers", więc jeśli serwer lub węzeł ulegnie awarii, jego usługi i kontenery zostaną przeniesione do innego serwera hosta lub maszyny wirtualnej. W takim przypadku potrzebne są bardziej zaawansowane technologie, takie jak klastry kontenerów, koordynatorzy i harmonogramy. W związku z tym sposób wdrożenia do tych klastrów jest obsługa zaawansowanych scenariuszy wyjaśnione w następnej sekcji.

### <a name="deploying-docker-applications-to-docker-clusters"></a>Wdrażanie aplikacji platformy Docker w klastrach platformy Docker

Charakter aplikacji rozproszonych wymaga zasobów obliczeniowych, które są również dystrybuowane. Aby mieć możliwości skali produkcyjnej, należy mieć możliwości klastrowania, które zapewniają wysoką skalowalność i wysoką dostępność na podstawie zasobów puli.

Kontenery można wdrożyć ręcznie do tych klastrów z narzędzia interfejsu wiersza polecenia lub interfejsu użytkownika sieci web, ale należy zarezerwować tego rodzaju pracy ręcznej do wykrywania testowania wdrażania lub celów zarządzania, takich jak skalowanie lub monitorowanie.

Z punktu widzenia dysku CD, a usługi Azure DevOps w szczególności można uruchomić specjalnie wykonane zadania wdrażania ze środowisk zarządzania wersjami usługi Azure DevOps, które będą wdrażać konteneryzowane aplikacje do klastrów rozproszonych w usłudze kontenera, jak pokazano na rysunku 5-9.

![Diagram przedstawiający krok wdrażania dysku CD dla koordynatorów.](./media/docker-application-outer-loop-devops-workflow/cd-deploy-to-orchestrators.png)

**Rysunek 5-9**. Wdrażanie aplikacji rozproszonych w usłudze kontenerowej

Początkowo podczas wdrażania do niektórych klastrów lub koordynatorów, tradycyjnie należy użyć określonych skryptów wdrażania i mechanizmów na każdego koordynatora (czyli Kubernetes i sieci `docker-compose` szkieletowej usług `docker-compose.yml` mają różne mechanizmy wdrażania) zamiast prostszego i łatwego w użyciu narzędzia opartego na pliku definicji. Jednak dzięki zadaniu wdrażania platformy Azure DevOps Services, pokazane na rysunku 5-10, teraz można również wdrożyć do obsługiwanych koordynatorów, po prostu przy użyciu znanego `docker-compose.yml` pliku, ponieważ narzędzie wykonuje to "tłumaczenie" dla Ciebie (z `docker-compose.yml` pliku do formatu wymaganego przez koordynatora).

![Zrzut ekranu przedstawiający zadanie Wdrażanie w uduśne.](./media/docker-application-outer-loop-devops-workflow/add-deploy-to-kubernetes-task.png)

**Rysunek 5-10**. Dodawanie zadania Wdrażanie do usługi Kubernetes do środowiska

Rysunek 5-11 pokazuje, jak można edytować wdrożenie do kubernetes zadanie z sekcji dostępnych do konfiguracji. Jest to zadanie, które będzie pobierać gotowe do użycia niestandardowe obrazy platformy Docker do wdrożenia jako kontenery w klastrze.

![Zrzut ekranu przedstawiający konfigurację zadania Wdrażanie w uduchowienia.](./media/docker-application-outer-loop-devops-workflow/edit-deploy-to-kubernetes-task.png)

**Rysunek 5-11**. Wdrażanie definicji zadania wdrażania w deployą definicji systemu ACS DC/OS

> [! INFORMACJE] Aby dowiedzieć się więcej o potoku dysku CD w usłudze Azure DevOps Services i platformie Docker, odwiedź stronę<https://azure.microsoft.com/services/devops/pipelines>

## <a name="step-5-run-and-manage"></a>Krok 5: Uruchamianie i zarządzanie

Ponieważ uruchamianie aplikacji i zarządzanie aplikacjami na poziomie produkcji przedsiębiorstwa jest głównym tematem samym w sobie, a także ze względu na rodzaj operacji i osób pracujących na tym poziomie (operacje IT), a także duży zakres tego obszaru, cały następny rozdział poświęcony jest wyjaśnieniu tego.

## <a name="step-6-monitor-and-diagnose"></a>Krok 6: Monitorowanie i diagnozowanie

Ten temat jest również omówiony w następnym rozdziale jako część zadań, które IT wykonuje w systemach produkcyjnych; jednak ważne jest, aby podkreślić, że szczegółowe informacje uzyskane w tym kroku musi przesyłać z powrotem do zespołu deweloperów, tak aby aplikacja jest stale ulepszana. Z tego punktu widzenia jest również częścią DevOps, chociaż zadania i operacje są często wykonywane przez IT.

Tylko wtedy, gdy monitorowanie i diagnostyka są w 100% w obrębie obszaru DevOps są procesy monitorowania i analizy wykonywane przez zespół programistów przed testowaniem lub środowiskach beta. Odbywa się to poprzez przeprowadzenie testów obciążenia lub monitorowanie środowisk beta lub qa, gdzie beta testerzy próbują nowych wersji.

>[!div class="step-by-step"]
>[Poprzedni](index.md)
>[następny](create-ci-cd-pipelines-azure-devops-services-aspnetcore-kubernetes.md)
