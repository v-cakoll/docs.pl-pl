---
title: Kroki przepływu pracy DevOps w zewnętrznej pętli dla aplikacji platformy Docker
description: Informacje na temat instrukcji "pętla zewnętrzna" przepływu pracy DevOps
ms.date: 02/15/2019
ms.openlocfilehash: 735f92c00cd6279649ec3b0c35cfb00543f21a8c
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75936781"
---
# <a name="steps-in-the-outer-loop-devops-workflow-for-a-docker-application"></a>Kroki przepływu pracy DevOps w zewnętrznej pętli dla aplikacji platformy Docker

Ilustracja 5-1 przedstawia kompleksowe przedstawienie kroków obejmujących przepływ pracy pętli zewnętrznej DevOps. Pokazuje "pętlę zewnętrzną" DevOps. Gdy kod jest wypychany do repozytorium, uruchamiany jest potok elementu konfiguracji, a następnie rozpoczyna potok CD, gdzie aplikacja zostanie wdrożona. Metryki zebrane z wdrożonych aplikacji są przekazywane z powrotem do obciążenia programistycznego, w którym występuje "pętla wewnętrzna", więc zespoły programistyczne mają rzeczywiste dane, aby reagować na potrzeby użytkowników i firm.

![Diagram przedstawiający 6 kroków przepływu pracy pętli zewnętrznej DevOps.](./media/docker-application-outer-loop-devops-workflow/overview-dev-ops-outter-loop-workflow.png)

**Rysunek 5-1**. DevOps przepływ pracy pętli zewnętrznej dla aplikacji platformy Docker za pomocą narzędzi firmy Microsoft

Teraz sprawdźmy, czy wszystkie te kroki są bardziej szczegółowe.

## <a name="step-1-inner-loop-development-workflow"></a>Krok 1. przepływ pracy tworzenia pętli wewnętrznej

Ten krok został szczegółowo wyjaśniony w rozdziale 4, ale w tym miejscu jest miejsce, w którym rozpoczyna się pętla zewnętrzna, moment, w którym deweloper wypycha kod do systemu zarządzania kontrolą źródła (na przykład Git) inicjujących akcje potoku elementu konfiguracji.

## <a name="step-2-source-code-control-integration-and-management-with-azure-devops-services-and-git"></a>Krok 2. Integracja kontroli kodu źródłowego i zarządzanie za pomocą Azure DevOps Services i git

W tym kroku należy mieć system kontroli wersji, aby zebrać skonsolidowaną wersję całego kodu pochodzącego od różnych deweloperów w zespole.

Mimo że funkcja kontroli kodu źródłowego (SCC) i zarządzania kodem źródłowym może wydawać się na drugim poziomie dla większości deweloperów, podczas tworzenia aplikacji platformy Docker w cyklu życia DevOps jest to konieczne, aby podkreślić, że nie można przesłać obrazów platformy Docker do aplikacji bezpośrednio z globalnym rejestrem platformy Docker (na przykład Azure Container Registry lub Hub) z komputera dewelopera. W przeciwieństwie do oprogramowania platformy Docker, które mają zostać wydane i wdrożone w środowisku produkcyjnym, należy utworzyć wyłącznie w kodzie źródłowym, który jest zintegrowany w globalnym potoku kompilacji lub ciągłej integracji, na podstawie repozytorium kodu źródłowego (na przykład Git).

Obrazy lokalne, generowane przez deweloperów, powinny być używane tylko podczas testowania w ramach własnych maszyn. Dlatego niezwykle ważne jest, aby potok DevOps został aktywowany z kodu SCC.

Azure DevOps Services i Team Foundation Server obsługują narzędzia Git i Kontrola wersji serwera Team Foundation. Możesz wybrać między nimi i wykorzystać je do kompleksowego korzystania z firmy Microsoft. Jednak można również zarządzać kodem w zewnętrznych repozytoriach (takich jak GitHub, lokalne repozytoria Git lub Subversion) i nadal mieć możliwość nawiązywania połączenia z nim i uzyskać kod jako punkt wyjścia dla potoku DevOps CI.

## <a name="step-3-build-ci-integrate-and-test-with-azure-devops-services-and-docker"></a>Krok 3. kompilowanie, CI, Integrowanie i testowanie przy użyciu Azure DevOps Services i platformy Docker

Ciągłej kontroli nad oprogramowaniem i dostarczaniu jest standardowa. Rozwiązanie Docker utrzymuje wyraźne rozdzielenie problemów między zespołami programistycznymi i operacyjnymi. Niezmienności obrazów platformy Docker zapewnia powtarzające się wdrożenie między opracowaną, przetestowaną przez CI i uruchamianą w środowisku produkcyjnym. Aparat platformy Docker wdrożony na laptopach i infrastrukturze testowej sprawia, że kontenery są przenośne między środowiskami.

W tym momencie, gdy masz system kontroli wersji o poprawnym kodzie, potrzebujesz *usługi kompilacji* , aby pobrać kod i uruchomić globalną kompilację i testy.

Wewnętrzny przepływ pracy dla tego kroku (CI, Build, test) dotyczy budowy potoku CI, składającego się z repozytorium kodu (git itp.), serwera kompilacji (Azure DevOps Services), aparatu platformy Docker i rejestru platformy Docker.

Azure DevOps Services jako podstawy do kompilowania aplikacji oraz ustawiania potoku CI i publikowania skompilowanych "artefaktów" można użyć do "repozytorium artefaktów", co zostało wyjaśnione w następnym kroku.

W przypadku korzystania z platformy Docker do wdrożenia "końcowe artefakty" zostaną wdrożone jako obrazy platformy Docker z aplikacją lub usługami osadzonymi w nich. Te obrazy są wypychane lub publikowane w *rejestrze platformy Docker* (prywatne repozytorium, takie jak te, które mogą znajdować się w Azure Container Registry, lub publiczne, takie jak rejestr usługi Docker Hub, który jest często używany do oficjalnych obrazów bazowych).

Oto podstawowe koncepcje: potok CI zostanie rozpoczęty przez zatwierdzenie repozytorium SCC, takiego jak Git. Zatwierdzenie spowoduje Azure DevOps Services uruchomienie zadania kompilacji w kontenerze platformy Docker i po pomyślnym zakończeniu tego zadania wypchnięcie obrazu platformy Docker do rejestru platformy Docker, jak pokazano na rysunku 5-2. Pierwsza część pętli zewnętrznej obejmuje kroki od 1 do 3, od kodu, uruchomienia, debugowania i walidacji, a następnie repozytorium kodu do kroku kompilowania i testowania elementu konfiguracji.

![Diagram przedstawiający trzy kroki, które są związane z przepływem pracy CI.](./media/docker-application-outer-loop-devops-workflow/continuous-integration-steps.png)

**Rysunek 5-2**. Kroki związane z

Oto podstawowe kroki przepływu pracy elementu konfiguracji z rozwiązaniami Docker i Azure DevOps Services:

1. Deweloper wypycha zatwierdzenie do repozytorium SCC (git/Azure DevOps Services, GitHub itp.).

2. Jeśli używasz usługi Azure DevOps Services lub git, CI jest wbudowana w, co oznacza, że jest to proste, co pozwala zaznaczyć pole wyboru w Azure DevOps Services. Jeśli używasz zewnętrznego SCC (takiego jak GitHub), `webhook` powiadomi Azure DevOps Services aktualizacji lub wypychania do usługi git/GitHub.

3. Azure DevOps Services ściąga repozytorium SCC, w tym pliku dockerfile opisujące obraz, a także kod aplikacji i testu.

4. Azure DevOps Services kompiluje obraz platformy Docker i etykietuje go przy użyciu numeru kompilacji.

5. Azure DevOps Services tworzy wystąpienie kontenera Docker na hoście aprowizacji platformy Docker i uruchamia odpowiednie testy.

6. Jeśli testy zakończą się pomyślnie, obraz jest najpierw ponownie oznaczony etykietą do zrozumiałej nazwy, dzięki czemu wiadomo, że jest to "Kompilacja zalecany" (na przykład "/1.0.0" lub jakakolwiek inna etykieta), a następnie zostanie wypchnięcia do rejestru platformy Docker (z systemem Docker Hub, Azure Container Registry, DTR itp.)

### <a name="implementing-the-ci-pipeline-with-azure-devops-services-and-the-docker-extension-for-azure-devops-services"></a>Implementowanie potoku CI przy użyciu Azure DevOps Services i rozszerzenia Docker dla Azure DevOps Services

Program Visual Studio Azure DevOps Services zawiera szablony wydań & kompilacji, których można użyć w potoku ciągłej integracji/ciągłego wdrażania, za pomocą którego można tworzyć obrazy platformy Docker, wypchnięcia obrazów platformy Docker do uwierzytelnionego rejestru platformy Docker, uruchamiania obrazów platformy Docker lub uruchamiania innych operacji oferowanych przez interfejs wiersza polecenia platformy Docker. Dodaje także zadanie Docker Compose, którego można użyć do kompilowania, wypychania i uruchamiania aplikacji platformy Docker obejmujących wiele kontenerów lub uruchamiania innych operacji oferowanych przez interfejs wiersza polecenia Docker Compose, jak pokazano na rysunku 5-3.

![Zrzut ekranu przedstawiający potok elementu konfiguracji platformy Docker w usłudze Azure DevOps.](./media/docker-application-outer-loop-devops-workflow/docker-ci-pipeline-azure-devops.png)

**Rysunek 5-3**. Potok elementu konfiguracji platformy Docker w Azure DevOps Services, w tym tworzenie szablonów wydań & i skojarzonych zadań.

Za pomocą tych szablonów i zadań można tworzyć artefakty ciągłej integracji/ciągłego tworzenia i testowania i wdrażania w usłudze Azure Service Fabric, usłudze Azure Kubernetes Service i podobnych ofertach.

Za pomocą tych Visual Studio Team Servicesych zadań kompilacja systemu Linux — Host platformy Docker/maszyna wirtualna, która została zainicjowana na platformie Azure i preferowany rejestr platformy Docker (Azure Container Registry, usługa Docker Hub, prywatny moduł Docker DTR lub inny rejestr platformy Docker), można utworzyć potok usługi Docker w bardzo spójny sposób.

***Wymagania:***

- Azure DevOps Services lub dla instalacji lokalnych Team Foundation Server 2015 Update 3 lub nowszej.

- Agent Azure DevOps Services, który ma pliki binarne platformy Docker.

  Prostym sposobem utworzenia jednego z tych agentów jest użycie platformy Docker w celu uruchomienia kontenera na podstawie obrazu Azure DevOps Services agenta Docker.

> [! INFORMACJE] aby dowiedzieć się więcej na temat asemblera potoku elementu konfiguracji Azure DevOps Services Docker i wyświetlania przewodników, odwiedź następujące witryny:
>
> - Uruchamianie agenta Visual Studio Team Services (teraz Azure DevOps Services) jako kontenera Docker: \
>   <https://hub.docker.com/_/microsoft-azure-pipelines-vsts-agent>
>
> - Kompilowanie obrazów platformy Docker .NET Core Linux przy użyciu Azure DevOps Services: \
>   <https://docs.microsoft.com/archive/blogs/stevelasker/building-net-core-linux-docker-images-with-visual-studio-team-services>
>
> - Kompilowanie maszyny kompilacji usługi Visual Studio Team Service opartej na systemie Linux z obsługą platformy Docker: \
>   <http://donovanbrown.com/post/2016/06/03/Building-a-Linux-Based-Visual-Studio-Team-Service-Build-Machine-with-Docker-Support>

### <a name="integrate-test-and-validate-multi-container-docker-applications"></a>Integrowanie, testowanie i Weryfikowanie aplikacji platformy Docker z obsługą kontenera

Zazwyczaj większość aplikacji platformy Docker składa się z wielu kontenerów, a nie jednego kontenera. Dobrym przykładem jest aplikacja zorientowana na mikrousług, dla której masz jeden kontener dla mikrousług. Jednak nawet bez ścisłego zastosowania wzorców podejścia mikrousług, istnieje prawdopodobieństwo, że aplikacja platformy Docker będzie składać się z wielu kontenerów lub usług.

W związku z tym po skompilowaniu kontenerów aplikacji w potoku CI należy również wdrożyć, zintegrować i przetestować aplikację jako całość ze wszystkimi kontenerami w ramach hosta Integration Docker lub nawet do klastra testowego, do którego kontenery są podlega.

Jeśli używasz jednego hosta, możesz użyć poleceń platformy Docker, takich jak Docker-Build, aby skompilować i wdrożyć powiązane kontenery do testowania i weryfikowania środowiska Docker na jednej maszynie wirtualnej. Ale w przypadku pracy z klastrem programu Orchestrator, takim jak DC/OS, Kubernetes lub Docker Swarm, należy wdrożyć kontenery za pomocą innego mechanizmu lub koordynatora, w zależności od wybranego klastra/harmonogramu.

Poniżej przedstawiono kilka typów testów, które można uruchomić w kontenerach platformy Docker:

- Testy jednostkowe dla kontenerów platformy Docker

- Testowanie grup powiązanych aplikacji lub mikrousług

- Testowanie w środowisku produkcyjnym i w wersjach "Kanaryjskich"

Ważnym punktem jest to, że podczas uruchamiania integracji i testów funkcjonalnych należy uruchomić te testy spoza kontenerów. Testy nie są zawarte ani uruchamiane w wdrażanych kontenerach, ponieważ kontenery są oparte na obrazach statycznych, które powinny być dokładnie takie jak te, które będą wdrażane w środowisku produkcyjnym.

Praktyczną opcją testowania bardziej zaawansowanych scenariuszy, takich jak dołączanie kilku klastrów (klaster testowy, klaster przejściowy i klaster produkcyjny) polega na opublikowaniu obrazów w rejestrze, aby można było je przetestować w różnych klastrach.

### <a name="push-the-custom-application-docker-image-into-your-global-docker-registry"></a>Wypychanie niestandardowego obrazu platformy Docker do rejestru globalnego platformy Docker

Po przetestowaniu i zweryfikowaniu obrazów platformy Docker warto je oznaczyć i opublikować w rejestrze platformy Docker. Rejestr platformy Docker to element krytyczny cyklu życia aplikacji platformy Docker, ponieważ jest to centralne miejsce, w którym przechowujesz niestandardowy test (znany również jako "obrazy zalecany"), który ma zostać wdrożony w środowiskach pytań i odpowiedzi.

Podobnie jak kod aplikacji przechowywany w repozytorium SCC (git itp.) jest "źródłem prawdy", rejestrem platformy Docker jest "Źródło prawdy" dla aplikacji binarnej lub BITS do wdrożenia w środowiskach pytań i odpowiedzi.

Zazwyczaj można chcieć mieć prywatne repozytoria dla obrazów niestandardowych w repozytorium prywatnym w Azure Container Registry lub w rejestrze lokalnym, takim jak zaufany rejestr platformy Docker, lub w rejestrze w chmurze publicznej z ograniczonym dostępem (np. W przypadku oprogramowania Docker Hub, chociaż w tym ostatnim przypadku kod nie jest otwarty, należy zaufać zabezpieczenia dostawcy. W obu przypadkach stosowana Metoda jest podobna i opiera się na `docker push` polecenie, jak pokazano na rysunku 5-4.

![Diagram przedstawiający wypychanie obrazów niestandardowych do rejestru kontenerów.](./media/docker-application-outer-loop-devops-workflow/docker-push-custom-images.png)

**Rysunek 5-4**. Publikowanie obrazów niestandardowych w rejestrze platformy Docker

W kroku 3, w przypadku tworzenia integracji i testowania (CI) można opublikować utworzone obrazy platformy Docker w rejestrze prywatnym lub publicznym. Istnieje wiele ofert rejestrów platformy Docker od dostawców chmury, takich jak Azure Container Registry, Amazon Web Services Container Registry, Google Container Registry, Nabrzeż i tak dalej.

Korzystając z zadań platformy Docker, można wypchnąć zestaw obrazów usługi zdefiniowany przez plik `docker-compose.yml` z wieloma tagami do uwierzytelnionego rejestru platformy Docker (na przykład Azure Container Registry), jak pokazano na rysunku 5-5.

![Zrzut ekranu przedstawiający krok publikowania obrazów w rejestrze.](./media/docker-application-outer-loop-devops-workflow/publish-custom-image-to-docker-registry.png)

**Rysunek 5-5**. Używanie Azure DevOps Services do publikowania niestandardowych obrazów w rejestrze platformy Docker

> [! INFORMACJE] Aby uzyskać więcej informacji na temat Azure Container Registry, zobacz <https://aka.ms/azurecontainerregistry>.

## <a name="step-4-cd-deploy"></a>Krok 4: CD, wdrażanie

Niezmienności obrazów platformy Docker zapewnia powtarzające się wdrożenie z możliwościami, które zostały opracowane, przetestowane przez CI i działają w środowisku produkcyjnym. Po opublikowaniu obrazów platformy Docker w rejestrze platformy Docker (prywatnym lub publicznym) można wdrożyć je w kilku środowiskach (produkcja, pytania i odpowiedzi, przemieszczanie itp.) z potoku CD przy użyciu Azure DevOps Services zadania potoku lub Release Management Azure DevOps Services.

Jednak w tym momencie zależy od rodzaju wdrażanej aplikacji platformy Docker. Wdrażanie prostej aplikacji (z punktu widzenia składu i wdrożenia), takiego jak aplikacja monolityczna składająca się z kilku kontenerów lub usług i wdrożona na kilku serwerach lub maszynach wirtualnych, różni się od wdrażania bardziej złożonej aplikacji, takiej jak aplikacje zorientowane na mikrousługi z możliwościami skalowania. Te dwa scenariusze zostały omówione w poniższych sekcjach.

### <a name="deploying-composed-docker-applications-to-multiple-docker-environments"></a>Wdrażanie złożonych aplikacji platformy Docker w wielu środowiskach platformy Docker

Najpierw przyjrzyjmy się w mniej skomplikowanym scenariuszu: wdrażanie na prostych hostach platformy Docker (maszyn wirtualnych lub serwerach) w jednym środowisku lub wielu środowiskach (pytań i odpowiedzi, przemieszczanie i produkcja). W tym scenariuszu wewnętrznie potok CD może używać narzędzia Docker-Zredaguj (z Azure DevOps Services zadań wdrażania), aby wdrożyć aplikacje platformy Docker za pomocą powiązanego zestawu kontenerów lub usług, jak pokazano na rysunku 5-6.

![Diagram przedstawiający etap wdrażania z dysku CD do trzech środowisk.](./media/docker-application-outer-loop-devops-workflow/deploy-app-containers-to-docker-host-environments.png)

**Rysunek 5-6**. Wdrażanie kontenerów aplikacji do prostych rejestrów środowisk hosta platformy Docker

Rysunek 5-7. pokazuje, jak można połączyć swoją kompilację do środowisk pytań i odpowiedzi za pośrednictwem Azure DevOps Services, klikając Docker Compose w oknie dialogowym Dodawanie zadania. Jednak podczas wdrażania w środowisku przejściowym lub produkcyjnym zwykle używane są funkcje Release Management obsługujące wiele środowisk (na przykład pytań i odpowiedzi, przemieszczanie i produkcja). W przypadku wdrażania w ramach jednego hosta platformy Docker jest używane zadanie Azure DevOps Services "Docker Compose" (które wywołuje polecenie `docker-compose up` pod okapem). W przypadku wdrażania w usłudze Azure Kubernetes Service (AKS) usługa korzysta z zadania wdrażania platformy Docker, jak wyjaśniono w poniższej sekcji.

![Zrzut ekranu przedstawiający okno dialogowe Dodawanie zadań zadania Docker Compose.](./media/docker-application-outer-loop-devops-workflow/add-tasks-docker-compose.png)

**Rysunek 5-7**. Dodawanie Docker Compose zadania w potoku Azure DevOps Services

Podczas tworzenia wydania w Azure DevOps Services pobiera on zestaw artefaktów wejściowych. Te artefakty są przeznaczone do niezmiennego okresu istnienia wersji we wszystkich środowiskach. Gdy wprowadzisz kontenery, artefakty wejściowe identyfikują obrazy w rejestrze do wdrożenia. W zależności od tego, jak te obrazy są identyfikowane, nie ma gwarancji, że przez cały czas trwania wydania nie są one tak samo, jak w przypadku odniesienia `myimage:latest` z pliku `docker-compose`.

Szablony Azure DevOps Services umożliwiają generowanie artefaktów kompilacji, które zawierają określone skróty obrazu rejestru, które są gwarantowane do jednoznacznego identyfikowania tego samego obrazu binarnego. Są one naprawdę potrzebne do wydania jako dane wejściowe.

### <a name="managing-releases-to-docker-environments-by-using-azure-devops-services-release-management"></a>Zarządzanie wersjami w środowiskach platformy Docker przy użyciu Azure DevOps Services Release Management

Za pomocą szablonów Azure DevOps Services można utworzyć nowy obraz, opublikować go w rejestrze platformy Docker, uruchomić go na hostach z systemem Linux lub Windows, a także użyć poleceń, takich jak `docker-compose`, aby wdrożyć wiele kontenerów jako całą aplikację, a wszystko to za pomocą funkcji Azure DevOps Services Release Management przeznaczonych dla wielu środowisk, jak pokazano na rysunku 5-8.

![Zrzut ekranu przedstawiający konfigurację wersji programu Docker.](./media/docker-application-outer-loop-devops-workflow/configure-docker-compose-release.png)

**Rysunek 5-8**. Konfigurowanie zadań Docker Compose Azure DevOps Services Azure DevOps Services Release Management

Należy jednak pamiętać, że scenariusz przedstawiony na rysunku 5-6 i zaimplementowany na rysunku 5-8 jest prostym (jest wdrażany na jednym hoście platformy Docker i na maszynach wirtualnych) i prawdopodobnie powinien być używany tylko na potrzeby tworzenia i testowania SCE narios. W większości scenariuszy produkcyjnych przedsiębiorstwa warto mieć wysoką dostępność (HA) i łatwą w zarządzaniu skalowalność dzięki obciążeniu w wielu węzłach, serwerach i maszynach wirtualnych, a także "inteligentnej pracy awaryjnej", więc jeśli serwer lub węzeł zakończy się niepowodzeniem, jego usługi i kontenery zostanie przeniesiony na inny serwer hosta lub maszynę wirtualną. W takim przypadku potrzebne są bardziej zaawansowane technologie, takie jak klastry kontenerów, Koordynatory i harmonogramy. W ten sposób można wdrożyć w tych klastrach, obsługując zaawansowane scenariusze opisane w następnej sekcji.

### <a name="deploying-docker-applications-to-docker-clusters"></a>Wdrażanie aplikacji platformy Docker w klastrach platformy Docker

Charakter aplikacji rozproszonych wymaga również zasobów obliczeniowych, które są dystrybuowane. W celu zapewnienia możliwości skalowania produkcji należy mieć możliwość klastrowania, które zapewniają wysoką skalowalność i wysoką dostępność na podstawie zasobów w puli.

Kontenery można wdrożyć ręcznie w tych klastrach za pomocą narzędzia CLI lub interfejsu użytkownika sieci Web, ale należy zastrzec ten rodzaj pracy ręcznej do testowania wdrożenia lub zarządzania, takich jak skalowanie i monitorowanie.

Z punktu widzenia dysku CD, a Azure DevOps Services w szczególnie, można uruchomić specjalnie wykonane zadania wdrażania ze środowisk Azure DevOps Services Release Management, które będą wdrażać aplikacje z kontenerów w klastrach rozproszonych w kontenerze Usługa, jak pokazano na rysunku 5-9.

![Diagram przedstawiający etap wdrażania dysku CD do programu Orchestrator.](./media/docker-application-outer-loop-devops-workflow/cd-deploy-to-orchestrators.png)

**Rysunek 5-9**. Wdrażanie aplikacji rozproszonych w usłudze Container Service

Początkowo podczas wdrażania do określonych klastrów lub programów Orchestrator można tradycyjnie używać konkretnych skryptów i mechanizmów wdrażania dla każdego koordynatora (to jest, Kubernetes i Service Fabric mają różne mechanizmy wdrażania) zamiast prostszego i łatwego w użyciu `docker-compose` narzędzia opartego na pliku definicji `docker-compose.yml`. Jednak dzięki obsłudze Azure DevOps Services narzędzia Docker Deploy pokazano na rysunku 5-10, teraz można również wdrożyć je do obsługiwanych koordynatorów przez samo użycie znanego pliku `docker-compose.yml`, ponieważ narzędzie wykonuje to "tłumaczenie" (z pliku `docker-compose.yml` do formatu wymaganego przez program Orchestrator).

![Zrzut ekranu przedstawiający zadanie Deploy to Kubernetes.](./media/docker-application-outer-loop-devops-workflow/add-deploy-to-kubernetes-task.png)

**Rysunek 5-10**. Dodawanie zadania Deploy to Kubernetes do środowiska

Rysunek 5-11 pokazuje, w jaki sposób można edytować zadanie Deploy to Kubernetes z sekcjami dostępnymi dla konfiguracji. Jest to zadanie, które spowoduje pobranie gotowych do użycia niestandardowych obrazów platformy Docker, które zostaną wdrożone jako kontenery w klastrze.

![Zrzut ekranu przedstawiający konfigurację zadania Deploy to Kubernetes.](./media/docker-application-outer-loop-devops-workflow/edit-deploy-to-kubernetes-task.png)

**Rysunek 5-11**. Wdrażanie definicji zadania platformy Docker na platformie DC/OS usługi ACS

> [! INFORMACJE] aby dowiedzieć się więcej na temat potoku dysku CD przy użyciu Azure DevOps Services i platformy Docker, odwiedź stronę <https://azure.microsoft.com/services/devops/pipelines>

## <a name="step-5-run-and-manage"></a>Krok 5. Uruchamianie i zarządzanie

Ponieważ aplikacje i zarządzanie nimi na poziomie produkcyjnym przedsiębiorstwa są głównym podmiotem w ramach i dla siebie i ze względu na typ operacji i osób pracujących na tym poziomie (operacje IT), jak również duży zakres tego obszaru, cały następny rozdział jest zastosowany do wyjaśnienie.

## <a name="step-6-monitor-and-diagnose"></a>Krok 6. monitorowanie i diagnozowanie

Ten temat został również omówiony w następnym rozdziale w ramach zadań wykonywanych w systemach produkcyjnych; Jednak ważne jest, aby podkreślić, że szczegółowe informacje uzyskane w tym kroku muszą powracać do zespołu programistycznego, aby aplikacja była stale ulepszana. Z tego punktu widzenia jest również częścią DevOps, chociaż zadania i operacje są zwykle wykonywane przez nią.

Tylko wtedy, gdy monitorowanie i Diagnostyka są 100% w obszarze DevOps są procesy monitorowania i analizy wykonywane przez zespół programistyczny przed testowaniem i środowiskiem beta. W tym celu należy przeprowadzić testowanie obciążenia lub monitorować środowiska beta lub pytania i odpowiedzi, gdzie testerzy wersji beta próbują uzyskać nowe wersje.

>[!div class="step-by-step"]
>[Poprzedni](index.md)
>[Następny](create-ci-cd-pipelines-azure-devops-services-aspnetcore-kubernetes.md)
