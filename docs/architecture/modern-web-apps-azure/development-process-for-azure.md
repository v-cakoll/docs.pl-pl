---
title: Proces programistyczny dla platformy Azure
description: Architekt nowoczesnych aplikacji sieci Web z ASP.NET Core i Azure | Proces tworzenia platformy Azure
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 640cfebea3c70314be4a597bc07b0dc6854f5848
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607896"
---
# <a name="development-process-for-azure"></a>Proces programistyczny dla platformy Azure

> _"Dzięki chmurze osoby prywatne i małe firmy mogą zatrzasnąć palcami i natychmiast skonfigurować usługi klasy korporacyjnej"._  
> _- Roy Stephan_

## <a name="vision"></a>Obraz

> *Twórz dobrze zaprojektowane aplikacje ASP .NET Core w taki sposób, jak chcesz, korzystając z programu Visual Studio lub interfejsu wiersza polecenia dotnet i kodu programu Visual Studio lub wybranego edytora.*

## <a name="development-environment-for-aspnet-core-apps"></a>Środowisko programistyczne dla aplikacji ASP.NET Core

### <a name="development-tools-choices-ide-or-editor"></a>Opcje narzędzi programistycznych: IDE lub edytor

Niezależnie od tego, czy wolisz pełny i zaawansowany IDE, czy lekki i zwinny edytor, firma Microsoft zapewnia ci omówione podczas opracowywania aplikacji ASP.NET Core.

**Visual Studio 2019.** Visual Studio 2019 jest najlepszym w swojej klasie IDE do tworzenia aplikacji dla ASP.NET Core. Oferuje wiele funkcji, które zwiększają produktywność programistów. Można go użyć do opracowania aplikacji, a następnie analizować jej wydajność i inne cechy. Wbudowany debuger umożliwia wstrzymanie wykonywania kodu i krok w tę iz powrotem za pośrednictwem kodu w locie, gdy jest uruchomiony. Wbudowana próbka testowa umożliwia organizowanie testów i ich wyników, a nawet wykonywanie testów jednostkowych na żywo podczas kodowania. Korzystając z funkcji Udostępniania na żywo, możesz współpracować w czasie rzeczywistym z innymi deweloperami, bezproblemowo udostępniając sesję kodu w sieci. A gdy wszystko będzie gotowe, program Visual Studio zawiera wszystko, czego potrzebujesz, aby opublikować aplikację na platformie Azure lub gdziekolwiek może być hostowane.

[Pobierz program Visual Studio 2019](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

**Visual Studio Code i dotnet CLI** (Narzędzia międzyplatformowe dla komputerów Mac, Linux i Windows). Jeśli wolisz lekki i wieloplatformowy edytor obsługujący dowolny język programowania, możesz użyć programu Microsoft Visual Studio Code i interfejsu wiersza polecenia dotnet. Te produkty zapewniają proste, ale niezawodne środowisko, które usprawnia przepływ pracy programisty. Ponadto Visual Studio Code obsługuje rozszerzenia\# dla języka C i tworzenia sieci Web, zapewniając intellisense i skróty zadań w edytorze.

[Pobieranie zestawu .NET Core SDK](https://dotnet.microsoft.com/download)

[Pobierz kod programu Visual Studio](https://code.visualstudio.com/download)

## <a name="development-workflow-for-azure-hosted-aspnet-core-apps"></a>Przepływ pracy programistyczne dla aplikacji ASP.NET Core hostowanych na platformie Azure

Cykl życia tworzenia aplikacji rozpoczyna się od komputera każdego dewelopera, kodowanie aplikacji przy użyciu preferowanego języka i testowania go lokalnie. Deweloperzy mogą wybrać preferowany system kontroli źródła i można skonfigurować ciągłej integracji (CI) i/lub ciągłego dostarczania/wdrażania (CD) przy użyciu serwera kompilacji lub na podstawie wbudowanych funkcji platformy Azure.

Aby rozpocząć tworzenie aplikacji ASP.NET Core przy użyciu ciągłej integracji/ciągłego wdrażania, można użyć usług Azure DevOps services lub własnego programu Team Foundation Server (TFS) organizacji.

### <a name="initial-setup"></a>Konfiguracja początkowa

Aby utworzyć potok wersji dla aplikacji, musisz mieć kod aplikacji w kontroli źródła. Skonfiguruj lokalne repozytorium i połącz go z repozytorium zdalnym w projekcie zespołowym. Postępuj zgodnie z poniższymi instrukcjami:

- [Udostępnianie kodu w usłudze Git i Visual Studio](https://docs.microsoft.com/azure/devops/git/share-your-code-in-git-vs) lub

- [Udostępnianie kodu za pomocą tfvc i programu Visual Studio](https://docs.microsoft.com/azure/devops/tfvc/share-your-code-in-tfvc-vs)

Utwórz usługę Azure App Service, w której wdrożysz aplikację. Utwórz aplikację sieci Web, przechodząc do bloku usługi app services w witrynie Azure portal. Kliknij pozycję Dodaj, wybierz szablon aplikacji sieci Web, kliknij pozycję Utwórz i podaj nazwę i inne szczegóły. Aplikacja internetowa będzie dostępna z pliku {name}.azurewebsites.net.

![Usługa AzureWebApp](./media/image10-2.png)

**Rysunek 10-1.** Tworzenie nowej aplikacji sieci Web usługi Azure App Service w witrynie Azure Portal.

Proces kompilacji ciągłej integracji będzie wykonywać automatyczną kompilację, gdy nowy kod zostanie zatwierdzony do repozytorium kontroli źródła projektu. Daje to natychmiastową informację zwrotną, że kod kompilacji (i, najlepiej, przechodzi zautomatyzowane testy) i potencjalnie można wdrożyć. Ta kompilacja ciągłej integracji spowoduje powstanie artefaktu pakietu wdrażania sieci web i opublikuje go do użycia przez proces dysku CD.

[Definiowanie procesu kompilacji ciągłej integracji](https://docs.microsoft.com/azure/devops/pipelines/ecosystems/dotnet-core)

Pamiętaj, aby włączyć ciągłą integrację, dzięki czemu system będzie w kolejce kompilacji, gdy ktoś w zespole zatwierdza nowy kod. Przetestuj kompilację i sprawdź, czy tworzy pakiet wdrażania sieci web jako jeden z jego artefaktów.

Gdy kompilacja zakończy się pomyślnie, proces dysku CD wdroży wyniki kompilacji ciągłej integracji w aplikacji sieci web platformy Azure. Aby to skonfigurować, należy utworzyć i skonfigurować *wersję*, która zostanie wdrożona w usłudze Azure App Service.

[Wdrażanie aplikacji sieci Web platformy Azure](https://docs.microsoft.com/azure/devops/pipelines/targets/webapp)

Po skonfigurowaniu potoku ciągłej integracji/ciągłego wdrażania można po prostu wprowadzać aktualizacje aplikacji sieci web i zatwierdzać je do kontroli źródła w celu ich wdrożenia.

### <a name="workflow-for-developing-azure-hosted-aspnet-core-applications"></a>Przepływ pracy do tworzenia aplikacji ASP.NET Core hostowanych na platformie Azure

Po skonfigurowaniu konta platformy Azure i procesu ciągłej integracji/ciągłego wdrażania tworzenie aplikacji hostowanych na platformie Azure ASP.NET core jest proste. Poniżej przedstawiono podstawowe kroki, które zwykle należy wykonać podczas tworzenia aplikacji ASP.NET Core, hostowane w usłudze Azure App Service jako aplikacji sieci Web, jak pokazano na rysunku 10-2.

![EndToEndDevDeployPraca](./media/image10-3.png)

**Rysunek 10-2.** Przepływ pracy krok po kroku do tworzenia aplikacji ASP.NET Core i hostowania ich na platformie Azure

#### <a name="step-1-local-dev-environment-inner-loop"></a>Krok 1. Wewnętrzna pętla lokalnego środowiska deweloperskiego

Tworzenie aplikacji ASP.NET Core do wdrożenia na platformie Azure nie różni się od tworzenia aplikacji w przeciwnym razie. Użyj lokalnego środowiska programistycznego, z którego użytkownik jest wygodny, niezależnie od tego, czy jest to visual studio 2017, czy dotnet CLI i Visual Studio Code lub preferowany edytor. Możesz napisać kod, uruchomić i debugować zmiany, uruchomić testy automatyczne i dokonać lokalnych zatwierdzeń do kontroli źródła, dopóki nie będziesz gotowy do wypchnięcia zmian do repozytorium kontroli źródła udostępnionego.

#### <a name="step-2-application-code-repository"></a>Krok 2. Repozytorium kodu aplikacji

Zawsze, gdy jesteś gotowy do udostępnienia kodu zespołowi, należy wypchnąć zmiany z lokalnego repozytorium źródłowego do repozytorium źródeł udostępnionych zespołu. Jeśli pracujesz w gałęzi niestandardowej, ten krok zwykle polega na scaleniu kodu do udostępnionej gałęzi (być może za pomocą [żądania ściągnięcia).](https://docs.microsoft.com/azure/devops/git/pull-requests)

#### <a name="step-3-build-server-continuous-integration-build-test-package"></a>Krok 3. Serwer kompilacji: ciągła integracja. budować, testować, pakować

Nowa kompilacja jest wyzwalana na serwerze kompilacji za każdym razem, gdy nowe zatwierdzenie jest dokonywane w repozytorium kodu udostępnionej aplikacji. W ramach procesu ciągłej integracji ta kompilacja powinna w pełni skompilować aplikację i uruchomić zautomatyzowane testy, aby potwierdzić, że wszystko działa zgodnie z oczekiwaniami. Efektem końcowym procesu ciągłej integracji powinna być spakowana wersja aplikacji sieci web, gotowa do wdrożenia.

#### <a name="step-4-build-server-continuous-delivery"></a>Krok 4. Serwer kompilacji: ciągłe dostarczanie

Gdy kompilacja zakończy się pomyślnie, proces CD będzie odebrać artefakty kompilacji produkowane. Będzie to obejmować pakiet wdrażania sieci web. Serwer kompilacji wdroży ten pakiet w usłudze Azure App Service, zastępując dowolną istniejącą usługę nowo utworzoną. Zazwyczaj ten krok jest przeznaczony dla środowiska przejściowego, ale niektóre aplikacje wdrażać bezpośrednio do produkcji za pośrednictwem procesu dysku CD.

#### <a name="step-5-azure-app-service-web-app"></a>Krok 5. Aplikacja internetowa usługi Azure App Service

Po wdrożeniu aplikacja ASP.NET Core działa w kontekście aplikacji sieci Web usługi Azure App Service. Ta aplikacja sieci Web można monitorować i dalej konfigurować za pomocą witryny Azure Portal.

#### <a name="step-6-production-monitoring-and-diagnostics"></a>Krok 6. Monitorowanie i diagnostyka produkcji

Gdy aplikacja sieci Web jest uruchomiona, można monitorować kondycję aplikacji i zbierać dane diagnostyczne i zachowanie użytkownika. Usługa Application Insights jest zawarta w programie Visual Studio i oferuje automatyczne instrumentamenty dla ASP.NET aplikacji. Może dostarczyć informacji na temat użycia, wyjątków, żądań, wydajności i dzienników.

## <a name="references"></a>Dokumentacja

**Tworzenie i wdrażanie aplikacji ASP.NET Core na platformie Azure**  
<https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core>

>[!div class="step-by-step"]
>[Poprzedni](test-asp-net-core-mvc-apps.md)
>[następny](azure-hosting-recommendations-for-asp-net-web-apps.md)
