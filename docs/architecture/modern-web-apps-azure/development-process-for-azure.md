---
title: Proces programistyczny dla platformy Azure
description: Architekt nowoczesne aplikacje internetowe z ASP.NET Core i Azure | Proces tworzenia platformy Azure
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 7a641c1b6665af6e9e78ef182174b360041d74aa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77450049"
---
# <a name="development-process-for-azure"></a>Proces programistyczny dla platformy Azure

> _"Dzięki chmurze osoby fizyczne i małe firmy mogą przyciągać palce i natychmiast konfigurować usługi klasy korporacyjnej"._  
> _- Roy Stephan_

## <a name="vision"></a>Obraz

> *Opracuj dobrze zaprojektowane aplikacje ASP .NET Core tak, jak chcesz, używając programu Visual Studio lub kodu dotnet CLI i programu Visual Studio lub wybranego edytora.*

## <a name="development-environment-for-aspnet-core-apps"></a>Środowisko programistyczne dla aplikacji ASP.NET Core

### <a name="development-tools-choices-ide-or-editor"></a>Opcje narzędzi programistycznych: IDE lub edytor

Niezależnie od tego, czy wolisz pełny i wydajny edytor IDE, czy lekki i zwinny edytor, firma Microsoft zapewnia ochronę podczas opracowywania aplikacji ASP.NET Core.

**Visual Studio 2019.** Visual Studio 2019 jest najlepszym w swojej klasie IDE do tworzenia aplikacji dla ASP.NET Core. Oferuje wiele funkcji, które zwiększają produktywność programistów. Można go użyć do opracowania aplikacji, a następnie analizować jego wydajność i inne cechy. Zintegrowany debuger umożliwia wstrzymanie wykonywania kodu i krok w przód iw tył za pomocą kodu w locie, jak jest uruchomiony. Wbudowany testrunner umożliwia organizowanie testów i ich wyników, a nawet może wykonywać testy jednostkowe na żywo podczas kodowania. Korzystając z udostępniania na żywo, możesz współpracować w czasie rzeczywistym z innymi programistami, bezproblemowo udostępniając sesję kodu za pomocą sieci. A gdy wszystko będzie gotowe, program Visual Studio zawiera wszystko, czego potrzebujesz do opublikowania aplikacji na platformie Azure lub gdziekolwiek możesz ją hostować.

[Pobierz program Visual Studio 2019](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

**Visual Studio Code i dotnet CLI** (Cross-Platform Tools for Mac, Linux i Windows). Jeśli wolisz edytor lekki i wieloplatformowy obsługujący dowolny język deweloperski, możesz użyć kodu programu Microsoft Visual Studio i identyfikatora cli dotnet. Produkty te zapewniają proste, ale niezawodne środowisko, które usprawnia przepływ pracy dewelopera. Ponadto Visual Studio Code obsługuje rozszerzenia\# dla C i rozwoju sieci Web, zapewniając intellisense i skrótów zadań w edytorze.

[Pobierz zestaw SDK .NET Core](https://dotnet.microsoft.com/download)

[Pobierz kod programu Visual Studio](https://code.visualstudio.com/download)

## <a name="development-workflow-for-azure-hosted-aspnet-core-apps"></a>Przepływ pracy deweloperów dla aplikacji ASP.NET Core hostowanych na platformie Azure

Cykl tworzenia aplikacji rozpoczyna się od komputera każdego dewelopera, kodując aplikację przy użyciu preferowanego języka i testując ją lokalnie. Deweloperzy mogą wybrać preferowany system kontroli źródła i skonfigurować ciągłą integrację (CI) i/lub ciągłe dostarczanie/wdrażanie (CD) przy użyciu serwera kompilacji lub na podstawie wbudowanych funkcji platformy Azure.

Aby rozpocząć opracowywanie aplikacji ASP.NET Core przy użyciu ciągłej integracji/ciągłej integracji, można użyć usługi Azure DevOps Services lub serwera TFS (Team Foundation Server) organizacji.

### <a name="initial-setup"></a>Konfiguracja początkowa

Aby utworzyć potok wydania dla aplikacji, musisz mieć kod aplikacji w kontroli źródła. Skonfiguruj lokalne repozytorium i podłącz je do repozytorium zdalnego w projekcie zespołowym. Postępuj zgodnie z poniższymi instrukcjami:

- [Udostępnij swój kod w git i visual studio](https://docs.microsoft.com/azure/devops/git/share-your-code-in-git-vs) lub

- [Udostępnianie kodu w programach TFVC i Visual Studio](https://docs.microsoft.com/azure/devops/tfvc/share-your-code-in-tfvc-vs)

Utwórz usługę Azure App Service, w której wdrożysz aplikację. Utwórz aplikację sieci Web, przechodząc do bloku Usługi aplikacji w witrynie Azure portal. Kliknij przycisk +Dodaj, wybierz szablon aplikacji sieci Web, kliknij pozycję Utwórz i podaj nazwę i inne szczegóły. Aplikacja internetowa będzie dostępna z {name}.azurewebsites.net.

![Aplikacja AzureWebApp](./media/image10-2.png)

**Rysunek 10-1.** Tworzenie nowej aplikacji sieci Web usługi Azure App w witrynie Azure Portal.

Proces kompilacji ci wykona kompilację automatyczną, gdy nowy kod jest zatwierdzony do repozytorium kontroli źródła projektu. Daje to natychmiastową informację zwrotną, że kod tworzy (i, najlepiej, przechodzi testy automatyczne) i potencjalnie mogą być wdrażane. Ta kompilacja ciągłej integracji z utylizacją spowoduje utworzenie artefaktu pakietu wdrażania sieci Web i opublikuje go do użycia przez proces dysku CD.

[Zdefiniuj proces kompilacji ci](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core#ci)

Pamiętaj, aby włączyć ciągłą integrację, aby system umieszczał kompilację w kolejce za każdym razem, gdy ktoś z twojego zespołu zatwierdza nowy kod. Przetestuj kompilację i sprawdź, czy produkuje pakiet wdrażania sieci web jako jeden z jego artefaktów.

Gdy kompilacja zakończy się pomyślnie, proces dysku CD wdroży wyniki kompilacji ciągłej integracji w aplikacji sieci Web platformy Azure. Aby to skonfigurować, należy utworzyć i skonfigurować *wydanie*, które zostaną wdrożone w usłudze Azure App Service.

[Definiowanie procesu zwalniania dysku CD](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core#cd)

Po skonfigurowaniu potoku ciągłej integracji/ciągłego wdrażania można po prostu wprowadzać aktualizacje aplikacji sieci web i zatwierdzać je do kontroli źródła, aby je wdrożyć.

### <a name="workflow-for-developing-azure-hosted-aspnet-core-applications"></a>Przepływ pracy do tworzenia ASP.NET podstawowych aplikacji hostowanych na platformie Azure

Po skonfigurowaniu konta platformy Azure i procesu ciągłej integracji/ciągłego rozwoju tworzenie aplikacji ASP.NET podstawowych hostowanych na platformie Azure jest proste. Poniżej przedstawiono podstawowe kroki, które zwykle należy wykonać podczas tworzenia aplikacji ASP.NET Core, hostowanych w usłudze Azure App Service jako aplikacja sieci Web, jak pokazano na rysunku 10-2.

![EndtoenddevDeployWorkflow (Przepływ pracy endtoenddevdeployworkflow)](./media/image10-3.png)

**Rysunek 10-2.** Przepływ pracy krok po kroku do tworzenia ASP.NET aplikacji Core i hostowania ich na platformie Azure

#### <a name="step-1-local-dev-environment-inner-loop"></a>Krok 1. Lokalna pętla wewnętrzna środowiska deweloperów

Tworzenie aplikacji ASP.NET Core do wdrożenia na platformie Azure nie różni się od tworzenia aplikacji w przeciwnym razie. Użyj lokalnego środowiska programistycznego, z którym chcesz korzystać, niezależnie od tego, czy jest to program Visual Studio 2017, kod dotnet CLI i Visual Studio lub preferowany edytor. Można napisać kod, uruchomić i debugować zmiany, uruchamiać testy automatyczne i wprowadzać lokalne zatwierdzenia do kontroli źródła, dopóki nie będzie gotowy do wypychania zmian do repozytorium kontroli źródła udostępnionego.

#### <a name="step-2-application-code-repository"></a>Krok 2. Repozytorium kodu aplikacji

Zawsze, gdy wszystko jest gotowe do udostępnienia kodu zespołowi, należy wypchnąć zmiany z lokalnego repozytorium źródłowego do repozytorium udostępnionego źródła zespołu. Jeśli pracujesz w gałęzi niestandardowej, ten krok zwykle polega na scalaniu kodu do gałęzi udostępnionej (być może za pomocą [żądania ściągnięcia).](https://docs.microsoft.com/azure/devops/git/pull-requests)

#### <a name="step-3-build-server-continuous-integration-build-test-package"></a>Krok 3. Serwer kompilacji: ciągła integracja. budować, testować, pakować

Nowa kompilacja jest wyzwalana na serwerze kompilacji za każdym razem, gdy nowe zatwierdzenie jest dokonywane w repozytorium kodu udostępnionej aplikacji. W ramach procesu ci, ta kompilacja powinna w pełni skompilować aplikację i uruchomić zautomatyzowane testy, aby potwierdzić, że wszystko działa zgodnie z oczekiwaniami. Wynik końcowy procesu pw powinna być spakowana wersja aplikacji sieci web, gotowy do wdrożenia.

#### <a name="step-4-build-server-continuous-delivery"></a>Krok 4. Serwer kompilacji: ciągłe dostarczanie

Po kompilacji powiodło się, proces cd będzie odebrać artefakty kompilacji produkowane. Będzie to obejmować pakiet wdrażania sieci web. Serwer kompilacji wdroży ten pakiet w usłudze Azure App Service, zastępując dowolną istniejącą usługę nowo utworzoną usługą. Zazwyczaj ten krok dotyczy środowiska przejściowego, ale niektóre aplikacje wdrażają bezpośrednio do środowiska produkcyjnego za pośrednictwem procesu dysku CD.

#### <a name="step-5-azure-app-service-web-app"></a>Krok 5. Aplikacja internetowa usługi Azure App Service

Po wdrożeniu ASP.NET aplikacja Core jest uruchamiana w kontekście aplikacji sieci Web usługi Azure App Service. Ta aplikacja sieci Web można monitorować i dalej konfigurować przy użyciu usługi Azure Portal.

#### <a name="step-6-production-monitoring-and-diagnostics"></a>Krok 6. Monitorowanie i diagnostyka produkcji

Gdy aplikacja sieci Web jest uruchomiona, można monitorować kondycję aplikacji i zbierać dane diagnostyczne i zachowanie użytkownika. Usługa Application Insights jest dołączona do programu Visual Studio i oferuje automatyczne instrumentację dla ASP.NET aplikacji. Może dostarczyć informacji na temat użycia, wyjątków, żądań, wydajności i dzienników.

## <a name="references"></a>Dokumentacja

**Tworzenie i wdrażanie ASP.NET podstawowej aplikacji na platformie Azure**  
<https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core>

>[!div class="step-by-step"]
>[Poprzedni](test-asp-net-core-mvc-apps.md)
>[następny](azure-hosting-recommendations-for-asp-net-web-apps.md)
