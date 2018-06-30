---
title: Proces programowania dla platformy Azure
description: Projektowania nowoczesnych aplikacji sieci Web platformy ASP.NET Core i Azure | Proces programowania dla platformy Azure
author: ardalis
ms.author: wiwagn
ms.date: 10/08/2017
ms.openlocfilehash: ea7b173369cea3b785297a136546d65965c3d789
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106856"
---
# <a name="development-process-for-azure"></a>Proces programowania dla platformy Azure

> _"Z chmury, osoby i małych firm można przyciąganie ich palców i teraz skonfigurować usługi klasy korporacyjnej."_  
> _-Royowi Stephan_

 ## <a name="vision"></a>Wizja

> *Tworzenie dobrze zaprojektowanego aplikacji ASP .NET Core lubisz, za pomocą programu Visual Studio lub platformy dotnet interfejsu wiersza polecenia i Visual Studio Code lub edytora wybór.*

## <a name="development-environment-for-aspnet-core-apps"></a>Środowisko projektowe dla aplikacji platformy ASP.NET Core

### <a name="development-tools-choices-ide-or-editor"></a>Opcje narzędzi programistycznych: IDE lub edytora

Czy można jednak pełne i wydajne środowiska IDE lub edytora nieskomplikowane i elastyczne Microsoft ma będzie podczas tworzenia aplikacji platformy ASP.NET Core.

**Visual Studio 2017.** Jeśli używasz *programu Visual Studio 2017* można tworzyć platformy ASP.NET Core aplikacje tak długo, jak masz *aplikacji dla wielu platform .NET Core* obciążenia zainstalowane. Wymagane obciążenia przedstawiono na rysunku 10-1 w oknie dialogowym Ustawienia programu Visual Studio 2017 r.

![](./media/image10-1.png)

**Rysunek 10-1.** Instalowanie obciążenia .NET Core w Visual Studio 2017 r.

[Pobierz program Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

**Visual Studio Code i platformy CLI dotnet** (narzędzia wieloplatformowe dla komputerów Mac, Linux i Windows). Jeśli wolisz edytorze nieskomplikowane i Międzyplatformowe obsługi żadnego języka programowania, można użyć programu Microsoft Visual Studio Code i dotnet interfejsu wiersza polecenia. Te produkty zapewniają proste, ale niezawodne środowisko, które upraszcza przepływu pracy deweloperów. Ponadto Visual Studio Code obsługuje rozszerzenia do C\# i aplikacji sieci web, zapewniając intellisense i skrótów zadań w edytorze.

[Pobierz oprogramowanie .NET Core SDK](https://www.microsoft.com/net/download/core)

[Pobierz kod programu Visual Studio](https://code.visualstudio.com/download)



## <a name="development-workflow-for-azure-hosted-aspnet-core-apps"></a>Przepływu pracy programowania dla aplikacji hostowanej Azure platformy ASP.NET Core

Cykl życia programowania aplikacji rozpoczyna się od wszystkich deweloperów maszyny, kodowania aplikacji przy użyciu preferowanego języka i testowanie go lokalnie. Deweloperzy mogą wybrać ich systemu kontroli źródła preferowanych i można skonfigurować ciągłej integracji (CI) i/lub ciągłego dostarczania/wdrożenia (CD) przy użyciu serwera kompilacji lub oparte na wbudowanych funkcji platformy Azure.

Aby rozpocząć tworzenie aplikacji platformy ASP.NET Core za pomocą elementu konfiguracji/CD, można użyć programu Visual Studio Team Services lub organizacji właścicielem Team Foundation Server (TFS).

### <a name="initial-setup"></a>Początkowej konfiguracji

Aby utworzyć potok wersji aplikacji, należy mieć kod aplikacji w kontroli źródła. Konfigurowanie lokalnego repozytorium i podłącz go do zdalnego repozytorium w projekcie zespołowym. Wykonaj te instrukcje:

-   [Udostępnianie kodu Git i Visual Studio](https://docs.microsoft.com/vsts/git/share-your-code-in-git-vs) lub

-   [Udostępnianie kodu TFVC i Visual Studio](https://docs.microsoft.com/vsts/tfvc/share-your-code-in-tfvc-vs)

Tworzenie usługi Azure App Service w przypadku wdrażania aplikacji. Tworzenie aplikacji sieci Web, przechodząc do bloku usługi aplikacji w portalu Azure. Kliknij pozycję + Dodaj, wybierz szablon aplikacji sieci Web, kliknij przycisk Utwórz i podaj nazwę i inne szczegóły. Aplikacja sieci web będzie dostępna z {nazwa}. azurewebsites.net.

![AzureWebApp](./media/image10-2.png)

**Rysunek 10-2.** Tworzenie nowej aplikacji sieci Web usługi aplikacji Azure w portalu Azure.

Procesie budowy CI wykona automatyczne kompilacji zawsze, gdy nowy kod został przekazany do repozytorium kontroli źródła projektu. Dzięki temu można natychmiast uzyskuje opinie, która tworzy kod (a najlepiej, jeśli pomyślnie przejdzie testy automatyczne) i może potencjalnie być wdrożony. Ta kompilacja CI utworzy sieci web wdrażanie pakietu artefaktów i opublikować ją w celu użycia przez proces z dysku CD.

[Definiowanie procesu kompilacji elementu konfiguracji](https://docs.microsoft.com/vsts/build-release/apps/aspnet/build-aspnet-core#ci)

Należy włączyć ciągłej integracji, więc system może umieścić w kolejce kompilacji zawsze, gdy ktoś w zespole zatwierdza nowy kod. Testowanie kompilacji i sprawdź, czy jest tworzenie sieci web podczas wdrażania pakietu jako jeden z jego artefakty.

Gdy kompilacja zakończy się powodzeniem, proces CD wdroży wyniki kompilacji elementu konfiguracji do aplikacji sieci web platformy Azure. Aby to skonfigurować, należy utworzyć i skonfigurować *wersji*, które zostaną wdrożone do usługi Azure App Service.

[Zdefiniuj proces wersji z dysku CD](https://docs.microsoft.com/vsts/build-release/apps/aspnet/build-aspnet-core#cd)

Po skonfigurowaniu planowaną CI/CD można po prostu aktualizowanie aplikacji sieci web i zatwierdzić je do kontroli źródła do nich wdrożone.

### <a name="workflow-for-developing-azure-hosted-aspnet-core-applications"></a>Przepływ pracy umożliwiający projektowanie aplikacji hostowanymi na platformie Azure platformy ASP.NET Core

Po skonfigurowaniu konta platformy Azure i CI/CD procesu projektowania aplikacji hostowanymi na platformie Azure platformy ASP.NET Core jest proste. Poniżej przedstawiono podstawowe kroki, które zwykle wykonać podczas tworzenia aplikacji platformy ASP.NET Core, obsługiwane w usłudze Azure App Service jako aplikacji sieci Web, jak pokazano na rysunku nr 10-3.

![EndToEndDevDeployWorkflow](./media/image10-3.png)

**Rysunek 10-3.** Krok przepływu pracy do tworzenia aplikacji platformy ASP.NET Core i obsługiwania je na platformie Azure

#### <a name="step-1-local-dev-environment-inner-loop"></a>Krok 1. Pętla wewnętrzny środowiska lokalnego deweloperów

Tworzenie aplikacji platformy ASP.NET Core do wdrożenia na platformie Azure nie różni się od tworzenia aplikacji, w przeciwnym razie wartość. Użyj środowisko projektowe lokalne, które znasz, czy jest Visual Studio 2017 lub dotnet interfejsu wiersza polecenia i Visual Studio Code lub edytora preferowany. Można napisać kod, uruchomić i debugowania zmiany, Uruchamianie testów automatycznych i wprowadzić zatwierdzeń lokalnego do kontroli źródła, dopóki wszystko jest gotowe do Wypchnij zmiany do repozytorium kontroli źródła udostępnionego.

#### <a name="step-2-application-code-repository"></a>Krok 2. Repozytorium kodu aplikacji

Zawsze, gdy wszystko jest gotowe do udostępnienia kodu zespołowi, ma wypychać zmiany z repozytorium lokalnego źródła do zespołu udostępnionego źródła repozytorium. Jeśli używane w niestandardowych gałęzi, ten krok obejmuje zwykle Wstawianie kodu do udostępnionego gałęzi (być może za pomocą klasy [żądania ściągnięcia](https://docs.microsoft.com/vsts/git/pull-requests)).

#### <a name="step-3-build-server-continuous-integration-build-test-package"></a>Krok 3. Serwer kompilacji: Ciągłej integracji. Pakiet kompilacji, testu

Po każdej nowe zatwierdzenia w repozytorium kodu aplikacji udostępnionych, nowej kompilacji zostanie wywołany na serwerze kompilacji. W trakcie procesu konfiguracji kompilacji w pełni należy skompilować aplikację i Uruchamianie testów automatycznych, aby upewnić się, że wszystko działa zgodnie z oczekiwaniami. W wyniku zakończenia procesu CI powinno być wersją spakowanych aplikacji sieci web, gotowy do wdrożenia.

#### <a name="step-4-build-server-continuous-delivery"></a>Krok 4. Serwera kompilacji: Ciągłego dostarczania

Po kompilacji, ponieważ zakończyło się pomyślnie, proces dysku CD przejmą wyprodukowanych artefaktów kompilacji. Będzie to obejmowało sieci web wdrażania pakietu. Serwer kompilacji zostanie wdrażania tego pakietu w usłudze Azure App Service, zastępując istniejące usługi z elementem nowo utworzony. Zazwyczaj ten krok dotyczy środowisko przejściowe, ale niektóre aplikacje wdrożyć bezpośrednio do środowiska produkcyjnego w procesie dysku CD.

#### <a name="step-5-azure-app-service-web-app"></a>Krok 5. Usługa aplikacji Azure. Aplikacja sieci Web.

Po wdrożeniu aplikacji platformy ASP.NET Core działa w kontekście aplikacji sieci Web platformy Azure App Service. Ta aplikacja sieci Web mogą być monitorowane i jeszcze skonfigurowane przy użyciu portalu Azure.

#### <a name="step-6-production-monitoring-and-diagnostics"></a>Krok 6. Produkcji, monitorowania i diagnostyki

Po uruchomieniu aplikacji sieci Web można monitorowania kondycji aplikacji i zbierać dane diagnostyczne i dane działanie użytkownika. Usługi Application Insights znajduje się w programie Visual Studio i oferuje automatyczne Instrumentacja dla aplikacji ASP.NET. Użytkownik może udostępnić informacje dotyczące użycia, wyjątki żądania, wydajności i dzienniki.

## <a name="references"></a>Odwołania

**Tworzenie i wdrażanie aplikacji platformy ASP.NET Core w systemie Azure**  
<https://docs.microsoft.com/vsts/build-release/apps/aspnet/build-aspnet-core>


>[!div class="step-by-step"]
[Poprzednie](test-asp-net-core-mvc-apps.md)
[dalej](azure-hosting-recommendations-for-asp-net-web-apps.md)
