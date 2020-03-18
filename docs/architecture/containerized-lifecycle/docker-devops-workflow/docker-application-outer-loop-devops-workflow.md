---
title: Kroki przepływu pracy DevOps w zewnętrznej pętli dla aplikacji platformy Docker
description: Poznaj kroki dla "zewnętrznej pętli" przepływu pracy DevOps
ms.date: 02/15/2019
ms.openlocfilehash: 735f92c00cd6279649ec3b0c35cfb00543f21a8c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75936781"
---
# <a name="steps-in-the-outer-loop-devops-workflow-for-a-docker-application"></a>Kroki przepływu pracy DevOps w zewnętrznej pętli dla aplikacji platformy Docker

Rysunek 5-1 przedstawia end-to-end przedstawienie kroków składających się na devops przepływu pracy pętli zewnętrznej. Pokazuje "zewnętrzną pętlę" DevOps. Gdy kod jest wypychany do reppo, potoku ciągłej integracji jest uruchamiany, a następnie rozpoczyna potoku dysku CD, gdzie aplikacja zostanie wdrożony. Metryki zebrane z wdrożonych aplikacji są przekazywane z powrotem do obciążenia programistycznego, gdzie występuje "pętla wewnętrzna", więc zespoły programistyczne mają rzeczywiste dane, aby odpowiedzieć na potrzeby użytkowników i firm.

![Diagram przedstawiający 6 kroków przepływu pracy w pętli zewnętrznej DevOps.](./media/docker-application-outer-loop-devops-workflow/overview-dev-ops-outter-loop-workflow.png)

**Rysunek 5-1**. Przepływ pracy w pętli zewnętrznej DevOps dla aplikacji platformy Docker za pomocą narzędzi firmy Microsoft

Teraz przeanalizujmy każdy z tych kroków bardziej szczegółowo.

## <a name="step-1-inner-loop-development-workflow"></a>Krok 1: Przepływ pracy tworzenia pętli wewnętrznej

Ten krok jest szczegółowo wyjaśniony w rozdziale 4, ale, podsumowując, tutaj zaczyna się zewnętrzna pętla, moment, w którym deweloper wypycha kod do systemu zarządzania kontrolą źródła (jak Git) imicjającego akcje potoku CI.

## <a name="step-2-source-code-control-integration-and-management-with-azure-devops-services-and-git"></a>Krok 2: Integracja i zarządzanie kontrolą kodu źródłowego za pomocą usług Azure DevOps services i Git

Na tym etapie musisz mieć system kontroli wersji, aby zebrać skonsolidowaną wersję całego kodu pochodzącego od różnych deweloperów w zespole.

Mimo że kontrola kodu źródłowego (SCC) i zarządzanie kodem źródłowym mogą wydawać się drugą naturą dla większości deweloperów, podczas tworzenia aplikacji platformy Docker w cyklu życia DevOps, ważne jest, aby podkreślić, że nie wolno przesyłać obrazów platformy Docker z aplikacją bezpośrednio do globalnego rejestru platformy Docker (np. rejestru kontenerów azure lub centrum docker hub) z komputera dewelopera. Wręcz przeciwnie obrazy platformy Docker, które mają zostać wydane i wdrożone w środowiskach produkcyjnych, muszą być tworzone wyłącznie na kodzie źródłowym zintegrowanym z potokiem kompilacji globalnej lub kompilacji wiersza kompilacji na podstawie repozytorium kodu źródłowego (takiego jak Git).

Obrazy lokalne, generowane przez deweloperów, powinny być używane przez nich podczas testowania w ich własnych komputerach. Dlatego ważne jest, aby potok DevOps został aktywowany z kodu SCC.

Usługi Azure DevOps i team foundation server obsługują kontrolę wersji Git i Team Foundation. Możesz wybrać między nimi i użyć go do obsługi firmy Microsoft. Jednak można również zarządzać kodem w zewnętrznych repozytoriach (takich jak GitHub, lokalne repozytoria Git lub Subversion) i nadal można połączyć się z nim i uzyskać kod jako punkt wyjścia dla potoku deweloperskiego ci.

## <a name="step-3-build-ci-integrate-and-test-with-azure-devops-services-and-docker"></a>Krok 3: Tworzenie, pw., integrowanie i testowanie za pomocą usług Azure DevOps i platformy Docker

CI stał się standardem dla nowoczesnego testowania i dostarczania oprogramowania. Rozwiązanie platformy Docker utrzymuje wyraźne oddzielenie problemów między zespołami deweloperów i operacji. Niezmienność obrazów platformy Docker zapewnia powtarzalne wdrożenie między tym, co jest opracowywane, testowane za pośrednictwem pw i uruchamiane w środowisku produkcyjnym. Aparat platformy Docker wdrożony w komputerach przenośnych deweloperów i infrastrukturze testowej sprawia, że kontenery są przenośne w różnych środowiskach.

W tym momencie po masz system kontroli wersji z poprawnym kodem przesłane, trzeba *usługi kompilacji,* aby odebrać kod i uruchomić kompilacji globalnej i testów.

Wewnętrzny przepływ pracy dla tego kroku (CI, kompilacji, test) jest o budowie potoku usługi CI składający się z repozytorium kodu (Git, itp.), serwera kompilacji (Usługi Azure DevOps Services), Docker Engine i docker rejestru.

Usługi Azure DevOps można używać jako podstawy do tworzenia aplikacji i ustawiania potoku infrastruktury i publikowania wbudowanych "artefaktów" w "repozytorium artefaktów", co wyjaśniono w następnym kroku.

Korzystając z platformy Docker do wdrożenia, "artefakty końcowe", które mają zostać wdrożone są obrazy platformy Docker z aplikacji lub usług osadzonych w nich. Te obrazy są wypychane lub publikowane w *rejestrze platformy Docker* (prywatne repozytorium, takie jak te, które można mieć w rejestrze kontenerów platformy Azure, lub publiczne, takie jak rejestr docker hub, który jest powszechnie używany dla oficjalnych obrazów podstawowych).

Oto podstawowa koncepcja: Rurociąg CI zostanie wyrzucony przez zobowiązanie do repozytorium SCC, takiego jak Git. Zatwierdzenie spowoduje, że usługi Azure DevOps Services do uruchomienia zadania kompilacji w kontenerze platformy Docker i, po pomyślnym zakończeniu tego zadania, wypychanie obrazu platformy Docker do rejestru platformy Docker, jak pokazano na rysunku 5-2. Pierwsza część pętli zewnętrznej obejmuje kroki od 1 do 3, z kodu, uruchom, debugowania i sprawdzania poprawności, a następnie repo kodu do kroku kompilacji i testowania ci.

![Diagram przedstawiający trzy kroki związane z przepływem pracy pw.](./media/docker-application-outer-loop-devops-workflow/continuous-integration-steps.png)

**Rysunek 5-2**. Kroki związane z PW

Oto podstawowe kroki przepływu pracy pw.

1. Deweloper wypycha zatwierdzenie do repozytorium SCC (Usługi Git/Azure DevOps, GitHub itp.).

2. Jeśli używasz usługi Azure DevOps Services lub Git, ci jest wbudowany, co oznacza, że jest tak proste, jak zaznaczanie pola wyboru w usłudze Azure DevOps Services. Jeśli używasz zewnętrznego SCC (jak GitHub), a `webhook` powiadomi usługi Azure DevOps usługi aktualizacji lub wypychania do Git/GitHub.

3. Usługi Azure DevOps services ściąga repozytorium SCC, w tym plik Dockerfile opisujący obraz, a także aplikację i kod testu.

4. Usługi Azure DevOps tworzy obraz platformy Docker i etykiety go z numerem kompilacji.

5. Usługi Azure DevOps tworzy kontener platformy Docker w ramach aprowizowanego hosta platformy Docker i uruchamia odpowiednie testy.

6. Jeśli testy się powiodą, obraz jest najpierw przemianowany na znaczącą nazwę, dzięki czemu wiadomo, że jest to "błogosławiona kompilacja" (na przykład "/1.0.0" lub dowolna inna etykieta), a następnie wypchany do rejestru platformy Docker (Docker Hub, Azure Container Registry, DTR itp.)

### <a name="implementing-the-ci-pipeline-with-azure-devops-services-and-the-docker-extension-for-azure-devops-services"></a>Implementowanie potoku pw.

Usługi DevOps programu Visual Studio Azure zawierają szablony wersji kompilacji &, których można używać w potoku ciągłej integracji/ciągłego dysku CD, za pomocą którego można tworzyć obrazy platformy Docker, wypychać obrazy platformy Docker do uwierzytelnionego rejestru platformy Docker, uruchamiać obrazy platformy Docker lub uruchamiać inne operacje oferowane przez interfejsu interfejsu akcesora Docker. Dodaje również docker Compose zadanie, które służy do tworzenia, wypychania i uruchamiania aplikacji platformy Docker wielu kontenerów lub uruchamiania innych operacji oferowanych przez platformę Docker Compose CLI, jak pokazano na rysunku 5-3.

![Zrzut ekranu przedstawiający potok platformy Azure — pw.](./media/docker-application-outer-loop-devops-workflow/docker-ci-pipeline-azure-devops.png)

**Rysunek 5-3**. Potok platformy Azure CI w usługach Azure DevOps, w tym szablony wersji kompilacji & i skojarzone zadania.

Te szablony i zadania służy do konstruowania artefaktów ciągłej integracji/ciągłego wdrażania do tworzenia / testowania i wdrażania w sieci szkieletowej usług Azure, usługi Azure Kubernetes service i podobnych ofert.

Dzięki tym zadaniom programu Visual Studio Team Services kompilacja hosta/maszyny Wirtualnej platformy Linux-Docker aprowizowanej na platformie Azure i preferowany rejestr platformy Docker (Azure Container Registry, Docker Hub, prywatny dtr platformy Docker lub inny rejestr platformy Docker) można złożyć potok ci platformy Docker w bardzo spójny sposób.

***Wymagania:***

- Usługi Azure DevOps lub dla instalacji lokalnych, Team Foundation Server 2015 Update 3 lub nowsze.

- Agent usług Azure DevOps Services, który ma pliki binarne platformy Docker.

  Łatwym sposobem utworzenia jednego z tych agentów jest użycie platformy Docker do uruchomienia kontenera na podstawie obrazu platformy Docker agenta usługi Azure DevOps.

> [! INFORMACJE] Aby dowiedzieć się więcej o składaniu potoku azure devops services platformy dokowej platformy Azure i wyświetlić instruktaże, odwiedź następujące witryny:
>
> - Uruchamianie agenta usług zespołu programu Visual Studio (Teraz usługi DevOps Platformy Azure) jako kontener platformy Docker: \
>   <https://hub.docker.com/_/microsoft-azure-pipelines-vsts-agent>
>
> - Tworzenie obrazów platformy Docker .NET Core Linux za pomocą usług Azure DevOps Services: \
>   <https://docs.microsoft.com/archive/blogs/stevelasker/building-net-core-linux-docker-images-with-visual-studio-team-services>
>
> - Tworzenie maszyny kompilacji visual studio z systemem Linux z obsługą platformy Docker: \
>   <http://donovanbrown.com/post/2016/06/03/Building-a-Linux-Based-Visual-Studio-Team-Service-Build-Machine-with-Docker-Support>

### <a name="integrate-test-and-validate-multi-container-docker-applications"></a>Integrowanie, testowanie i sprawdzanie poprawności aplikacji platformy Docker dla wielu kontenerów

Zazwyczaj większość aplikacji platformy Docker składa się z wielu kontenerów, a nie jednego kontenera. Dobrym przykładem jest aplikacja zorientowana na mikrousługi, dla której będzie jeden kontener na mikrousługi. Ale nawet bez ściśle następujące wzorce podejścia mikrousług jest prawdopodobne, że aplikacja platformy Docker będzie składać się z wielu kontenerów lub usług.

W związku z tym po utworzeniu kontenerów aplikacji w potoku ciągłej integracji, należy również wdrożyć, zintegrować i przetestować aplikację jako całość ze wszystkimi jego kontenerów w hosta platformy Docker integracji lub nawet do klastra testowego, do którego kontenery są Rozproszonych.

Jeśli używasz jednego hosta, można użyć poleceń platformy Docker, takich jak docker-compose do tworzenia i wdrażania powiązanych kontenerów do testowania i sprawdzania poprawności środowiska platformy Docker w jednej maszynie wirtualnej. Jeśli jednak pracujesz z klastrem koordynatora, takim jak DC/OS, Kubernetes lub Docker Swarm, musisz wdrożyć kontenery za pomocą innego mechanizmu lub koordynatora, w zależności od wybranego klastra/harmonogramu.

Poniżej przedstawiono kilka typów testów, które można uruchomić względem kontenerów platformy Docker:

- Testy jednostkowe kontenerów platformy Docker

- Testowanie grup powiązanych aplikacji lub mikrousług

- Test w produkcji i wydania "kanarek"

Ważną kwestią jest to, że podczas uruchamiania testów integracji i funkcjonalności, należy uruchomić te testy spoza kontenerów. Testy nie są zawarte lub uruchamiane w kontenerach, które wdrażasz, ponieważ kontenery są oparte na statycznych obrazów, które powinny być dokładnie takie jak te, które będą wdrażane w środowisku produkcyjnym.

Praktyczną opcją podczas testowania bardziej zaawansowanych scenariuszy, takich jak w tym kilka klastrów (klastrtest, klaster przejściowy i klaster produkcyjny) jest opublikowanie obrazów w rejestrze, dzięki czemu można go przetestować w różnych klastrach.

### <a name="push-the-custom-application-docker-image-into-your-global-docker-registry"></a>Wypchnij obraz platformy Docker aplikacji niestandardowej do globalnego rejestru platformy Docker

Po przetestowaniu i zweryfikowaniu obrazów platformy Docker należy je oznaczyć i opublikować w rejestrze platformy Docker. Rejestr platformy Docker jest kluczowym elementem w cyklu życia aplikacji platformy Docker, ponieważ jest centralnym miejscem, w którym przechowujesz test niestandardowy (znany również jako "błogosławione obrazy" do wdrożenia w środowiskach qa i produkcyjnych.

Podobnie jak kod aplikacji przechowywane w repozytorium SCC (Git, itp.) jest "źródłem prawdy", docker rejestru jest "źródłem prawdy" dla aplikacji binarnych lub bitów, które mają być wdrożone w środowisku qa lub środowiska produkcyjnego.

Zazwyczaj można mieć prywatne repozytoria obrazów niestandardowych w prywatnym repozytorium w rejestrze kontenerów azure lub w rejestrze lokalnym, takim jak Zaufany rejestr platformy Docker, lub w rejestrze chmury publicznej z ograniczonym dostępem (np. Docker Hub), chociaż w tym ostatnim przypadku, jeśli kod nie jest open source, należy ufać zabezpieczeń dostawcy. Tak czy inaczej, metoda, której używasz `docker push` jest podobny i jest oparty na poleceniu, jak pokazano na rysunku 5-4.

![Diagram przedstawiający wypychanie obrazów niestandardowych do rejestru kontenerów.](./media/docker-application-outer-loop-devops-workflow/docker-push-custom-images.png)

**Rysunek 5-4**. Publikowanie obrazów niestandardowych w rejestrze platformy Docker

W kroku 3 do tworzenia integracji i testowania (CI) można opublikować wynikowe obrazy docker do rejestru prywatnego lub publicznego. Istnieje wiele ofert rejestrów platformy Docker od dostawców chmury, takich jak Azure Container Registry, Rejestr kontenerów Amazon Web Services, Rejestr kontenerów Google, Rejestr Quay i tak dalej.

Za pomocą zadań platformy Docker można wypchnąć zestaw obrazów usługi zdefiniowanych przez `docker-compose.yml` plik z wieloma tagami do uwierzytelnionego rejestru platformy Docker (np. rejestru kontenerów azure), jak pokazano na rysunku 5-5.

![Zrzut ekranu przedstawiający krok publikowania obrazów w rejestrze.](./media/docker-application-outer-loop-devops-workflow/publish-custom-image-to-docker-registry.png)

**Rysunek 5-5**. Publikowanie obrazów niestandardowych w rejestrze platformy Docker przy użyciu usług Azure DevOps Services

> [! INFORMACJE] Aby uzyskać więcej informacji <https://aka.ms/azurecontainerregistry>na temat rejestru kontenerów platformy Azure, zobacz .

## <a name="step-4-cd-deploy"></a>Krok 4: CD, Wdrażanie

Niezmienność obrazów platformy Docker zapewnia powtarzalne wdrożenie z tym, co jest opracowywane, testowane za pośrednictwem pw i uruchamiane w środowisku produkcyjnym. Po opublikowaniu obrazów platformy Docker aplikacji w rejestrze platformy Docker (prywatnych lub publicznych) można wdrożyć je w kilku środowiskach, które mogą być dostępne (produkcyjne, qa, przemieszczania itp.) z potoku dysku CD przy użyciu usług Azure DevOps Services potoku lub zarządzania wersjami usług Azure DevOps.

Jednak w tym momencie zależy od rodzaju aplikacji platformy Docker, którą wdrażasz. Wdrażanie prostej aplikacji (z punktu widzenia kompozycji i wdrażania), takiej jak monolityczne zastosowanie składające się z kilku kontenerów lub usług i wdrożone na kilku serwerach lub maszynach wirtualnych różni się od wdrażania bardziej złożonej aplikacji, takiej jak aplikacja zorientowana na mikrousługi z możliwościami hiperskali. Te dwa scenariusze zostały wyjaśnione w poniższych sekcjach.

### <a name="deploying-composed-docker-applications-to-multiple-docker-environments"></a>Wdrażanie złożonych aplikacji platformy Docker w wielu środowiskach platformy Docker

Przyjrzyjmy się najpierw mniej złożony scenariusz: wdrażanie do prostych hostów platformy Docker (maszyny wirtualne lub serwery) w jednym środowisku lub wielu środowiskach (QA, przemieszczania i produkcji). W tym scenariuszu wewnętrznie potoku dysku CD można użyć docker-compose (z zadań wdrażania usług Azure DevOps Services) do wdrażania aplikacji platformy Docker z powiązanym zestawkontenerów lub usług, jak pokazano na rysunku 5-6.

![Diagram przedstawiający krok wdrażania dysku CD wdrażający w trzech środowiskach.](./media/docker-application-outer-loop-devops-workflow/deploy-app-containers-to-docker-host-environments.png)

**Rysunek 5-6**. Wdrażanie kontenerów aplikacji w rejestrze środowisk hosta prostego platformy Docker

Rysunek 5-7 przedstawia sposób łączenia kompilacji ze środowiskami qa/testzaza pomocą usług Azure DevOps Services, klikając przycisk Docker Compose w oknie dialogowym Dodawanie zadania. Jednak podczas wdrażania w środowiskach przejściowych lub produkcyjnych, zwykle należy użyć funkcji zarządzania wersjami obsługi wielu środowisk (takich jak QA, przemieszczania i produkcji). Jeśli wdrażasz na pojedynczych hostach platformy Docker, jest przy użyciu usługi Azure DevOps `docker-compose up` Services "Docker Compose" zadanie (który jest wywoływanie polecenia pod maską). Jeśli wdrażasz usługę Azure Kubernetes Service (AKS), używa zadania wdrażania platformy Docker, jak wyjaśniono w dalszej sekcji.

![Zrzut ekranu przedstawiający okno dialogowe Dodawanie zadań zadania Docker Compose.](./media/docker-application-outer-loop-devops-workflow/add-tasks-docker-compose.png)

**Rysunek 5-7**. Dodawanie zadania do tworzenia platformy Docker Compose w potoku usług Azure DevOps Services

Podczas tworzenia wersji w usłudze Azure DevOps Services, pobiera zestaw artefaktów wejściowych. Te artefakty są przeznaczone do niezmienne dla okresu istnienia wydania, we wszystkich środowiskach. Po wprowadzeniu kontenerów artefakty wejściowe identyfikują obrazy w rejestrze do wdrożenia. W zależności od tego, jak te obrazy są identyfikowane, nie są one gwarantowane, aby pozostać `myimage:latest` takie `docker-compose` same przez cały czas trwania wydania, najbardziej oczywistym przypadkiem jest odniesienie z pliku.

Szablony usług Azure DevOps Services umożliwia generowanie artefaktów kompilacji, które zawierają określone skróty obrazów rejestru, które są gwarantowane do unikatowej identyfikacji tego samego pliku binarnego obrazu. Są to, co naprawdę chcesz użyć jako dane wejściowe do wydania.

### <a name="managing-releases-to-docker-environments-by-using-azure-devops-services-release-management"></a>Zarządzanie wersjami w środowiskach platformy Docker przy użyciu zarządzania wersjami usług Azure DevOps Services

Za pomocą szablonów usług Azure DevOps Services można utworzyć nowy obraz, opublikować go w rejestrze platformy `docker-compose` Docker, uruchomić go na hostach systemu Linux lub Windows i użyć poleceń, takich jak wdrażanie wielu kontenerów jako całej aplikacji, a wszystko to za pośrednictwem funkcji zarządzania wersjami usług Azure DevOps, które są przeznaczone dla wielu środowisk, jak pokazano na rysunku 5–8.

![Zrzut ekranu przedstawiający konfigurację wersji doplatformowania.](./media/docker-application-outer-loop-devops-workflow/configure-docker-compose-release.png)

**Rysunek 5-8**. Konfigurowanie azure devops usługi docker Tworzenie zadań z zarządzania wersjami usług Azure DevOps

Należy jednak pamiętać, że scenariusz pokazany na rysunku 5-6 i zaimplementowany na rysunku 5-8 jest prosty (wdraża na pojedynczych hostach platformy Docker i maszynach wirtualnych, a na obraz ie będzie jeden kontener lub wystąpienie) i prawdopodobnie powinien być używany tylko do tworzenia lub testowania Scenariuszy. W większości scenariuszy produkcyjnych przedsiębiorstwa chcesz mieć wysoką dostępność (HA) i łatwą w zarządzaniu skalowalność przez równoważenie obciążenia w wielu węzłach, serwerach i maszynach wirtualnych, a także "inteligentne praca awaryjna", więc jeśli serwer lub węzeł ulegnie awarii, jego usługi i kontenery zostanie przeniesiona na inny serwer hosta lub maszynę wirtualną. W takim przypadku potrzebne są bardziej zaawansowane technologie, takie jak klastry kontenerów, koordynatorów i planistów. W związku z tym sposób wdrożenia do tych klastrów jest obsługa zaawansowanych scenariuszy wyjaśnione w następnej sekcji.

### <a name="deploying-docker-applications-to-docker-clusters"></a>Wdrażanie aplikacji platformy Docker w klastrach platformy Docker

Charakter aplikacji rozproszonych wymaga zasobów obliczeniowych, które są również dystrybuowane. Aby mieć możliwości skali produkcyjnej, musisz mieć możliwości klastrowania, które zapewniają wysoką skalowalność i wysoką dostępność na podstawie połączonych zasobów.

Kontenery można wdrażać ręcznie w tych klastrach za pomocą narzędzia interfejsu interfejsu opartego na interfejsie firmy Web lub interfejsu internetowego, ale należy zarezerwować tego rodzaju pracę ręczną w celu wykrycia testowania wdrażania lub celów zarządzania, takich jak skalowanie w poziomie lub monitorowanie.

Z punktu widzenia dysku CD i usług Azure DevOps services można uruchamiać specjalnie wykonane zadania wdrażania ze środowisk zarządzania wersjami usług Azure DevOps, które będą wdrażać konteneryzowane aplikacje w klastrach rozproszonych w kontenerze usługi, jak pokazano na rysunku 5-9.

![Diagram przedstawiający krok wdrażania dysku CD wdrażania do koordynatorów.](./media/docker-application-outer-loop-devops-workflow/cd-deploy-to-orchestrators.png)

**Rysunek 5-9**. Wdrażanie aplikacji rozproszonych w usłudze container service

Początkowo podczas wdrażania do niektórych klastrów lub koordynatorów, tradycyjnie używać określonych skryptów wdrażania i mechanizmów na każdego koordynatora (czyli Kubernetes i sieci szkieletowej `docker-compose` usług mają `docker-compose.yml` różne mechanizmy wdrażania) zamiast prostsze i łatwe w użyciu narzędzie oparte na pliku definicji. Jednak dzięki zadania Azure DevOps Services Docker Deploy, pokazanemu na rysunku 5-10, można teraz również `docker-compose.yml` wdrożyć do obsługiwanych koordynatorów, po prostu `docker-compose.yml` przy użyciu znajomego pliku, ponieważ narzędzie wykonuje to "tłumaczenie" dla Ciebie (z pliku do formatu wymaganego przez koordynatora).

![Zrzut ekranu przedstawiający zadanie Wdrażanie w kubernetes.](./media/docker-application-outer-loop-devops-workflow/add-deploy-to-kubernetes-task.png)

**Rysunek 5-10**. Dodawanie zadania Wdrażanie do kubernetes do środowiska

Rysunek 5-11 pokazuje, jak można edytować zadanie Wdrażanie w programie Kubernetes z sekcjami dostępnymi do konfiguracji. Jest to zadanie, które będzie pobierać gotowe do użycia niestandardowe obrazy platformy Docker do wdrożenia jako kontenery w klastrze.

![Zrzut ekranu przedstawiający konfigurację zadań Wdrażanie w programie Kubernetes.](./media/docker-application-outer-loop-devops-workflow/edit-deploy-to-kubernetes-task.png)

**Rysunek 5-11**. Docker Wdrażanie definicji zadania wdrażania w usłek ACS DC/OS

> [! INFORMACJE] Aby dowiedzieć się więcej o potoku dysku CD z usługami Azure DevOps i platformą Docker, odwiedź stronę<https://azure.microsoft.com/services/devops/pipelines>

## <a name="step-5-run-and-manage"></a>Krok 5: Uruchamianie i zarządzanie

Ponieważ prowadzenie i zarządzanie aplikacjami na poziomie produkcji przedsiębiorstwa jest głównym tematem samym w sobie, a ze względu na rodzaj operacji i osób pracujących na tym poziomie (operacje IT), a także duży zakres tego obszaru, cały następny rozdział poświęcony jest wyjaśniając to.

## <a name="step-6-monitor-and-diagnose"></a>Krok 6: Monitorowanie i diagnozowanie

Ten temat jest również omówiony w następnym rozdziale jako część zadań, które IT wykonuje w systemach produkcyjnych; jednak ważne jest, aby podkreślić, że szczegółowe informacje uzyskane w tym kroku musi karmić z powrotem do zespołu programistycznego, tak aby aplikacja jest stale ulepszana. Z tego punktu widzenia jest również częścią DevOps, chociaż zadania i operacje są często wykonywane przez IT.

Tylko wtedy, gdy monitorowanie i diagnostyka są w 100% w sferze DevOps są procesy monitorowania i analizy wykonywane przez zespół programistów przed testowania lub środowisk beta. Odbywa się to poprzez wykonanie testów obciążenia lub monitorowanie środowisk beta lub qa, w których testerzy wersji beta próbują nowych wersji.

>[!div class="step-by-step"]
>[Poprzedni](index.md)
>[następny](create-ci-cd-pipelines-azure-devops-services-aspnetcore-kubernetes.md)
