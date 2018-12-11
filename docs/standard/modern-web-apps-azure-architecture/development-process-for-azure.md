---
title: Proces programistyczny dla platformy Azure
description: Projektowania nowoczesnych aplikacji sieci Web za pomocą platformy ASP.NET Core i platformy Azure | Proces programistyczny dla platformy Azure
author: ardalis
ms.author: wiwagn
ms.date: 06/28/2018
ms.openlocfilehash: 932d3869483b6c96f2394ec308d3aa014b8650d4
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152617"
---
# <a name="development-process-for-azure"></a>Proces programistyczny dla platformy Azure

> _"W chmurze użytkowników indywidualnych i małych firmach mogą przyciąganie ich palców i natychmiast skonfigurować usługi klasy korporacyjnej."_  
> _-Roy Stephan_

 ## <a name="vision"></a>Obraz

> *Twórz dobrze zaprojektowanego aplikacje ASP .NET Core lubisz, za pomocą programu Visual Studio lub wiersz polecenia dotnet i programu Visual Studio Code lub Edytor wybór.*

## <a name="development-environment-for-aspnet-core-apps"></a>Środowisko programistyczne dla aplikacji platformy ASP.NET Core

### <a name="development-tools-choices-ide-or-editor"></a>Opcje narzędzia do opracowywania: Środowiskiem IDE lub edytorem

Czy wolisz, pełne i zaawansowanego środowiska IDE lub edytora lekkie i elastyczne, Microsoft zapewnia pełne wsparcie podczas tworzenia aplikacji platformy ASP.NET Core.

**Visual Studio 2017.** Jeśli używasz *programu Visual Studio 2017* aplikacje można tworzyć platformy ASP.NET Core tak długo, jak masz *programowanie dla wielu platform .NET Core* zainstalowanym obciążeniem. Rysunek 10-1 pokazuje wymaganego obciążenia w oknie dialogowym Ustawienia programu Visual Studio 2017.

![](./media/image10-1.png)

**Rysunek 10-1.** Instalowanie obciążenia .NET Core w programie Visual Studio 2017.

[Pobierz program Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

**Visual Studio Code i interfejsu wiersza polecenia platformy dotnet** (narzędzi dla wielu Platform dla systemów Mac, Linux i Windows). Jeśli wolisz edytora uproszczona i dla wielu platform, obsługa dowolnego języka programowania, można użyć programu Microsoft Visual Studio Code i wiersz polecenia dotnet. Te produkty oferują proste, ale niezawodna usprawniające przepływ pracy dla deweloperów. Ponadto, Visual Studio Code obsługuje rozszerzenia dla języka C\# i aplikacji sieci web w technologii intellisense i skrótów zadań w edytorze.

[Pobierz program .NET Core SDK](https://www.microsoft.com/net/download/core)

[Pobierz program Visual Studio Code](https://code.visualstudio.com/download)

## <a name="development-workflow-for-azure-hosted-aspnet-core-apps"></a>Przepływ pracy tworzenia oprogramowania dla aplikacji hostowanych na platformie Azure platformy ASP.NET Core

Cykl życia projektowania aplikacji rozpoczyna się od maszyny każdy Deweloper aplikacji przy użyciu preferowanego języka i testowanie jej lokalnie. Deweloperzy i zrezygnować z ich preferowanego systemu kontroli źródła można skonfigurować ciągłej integracji (CI) i/lub ciągłe dostarczanie/wdrażanie (CD) przy użyciu serwera kompilacji lub oparte na wbudowanych funkcjach platformy Azure.

Aby rozpocząć tworzenie aplikacji platformy ASP.NET Core przy użyciu ciągłej integracji/ciągłego wdrażania, można użyć usługom DevOps platformy Azure lub w organizacji właścicielem Team Foundation Server (TFS).

### <a name="initial-setup"></a>Konfiguracja początkowa

Aby utworzyć potok tworzenia wersji aplikacji, musisz mieć kod aplikacji w kontroli źródła. Konfigurowanie lokalnego repozytorium i podłącz go do zdalnego repozytorium w projekcie zespołowym. Wykonaj te instrukcje:

- [Udostępnianie kodu z Git i Visual Studio](https://docs.microsoft.com/azure/devops/git/share-your-code-in-git-vs) lub

- [Udostępnianie kodu z TFVC i Visual Studio](https://docs.microsoft.com/azure/devops/tfvc/share-your-code-in-tfvc-vs)

Tworzenie usługi Azure App Service, w przypadku wdrażania aplikacji. Tworzenie aplikacji sieci Web, przechodząc do bloku usługi App Services w witrynie Azure portal. Kliknij pozycję + Dodaj, wybierz szablon aplikacji sieci Web, kliknij przycisk Utwórz, a następnie podaj nazwę i inne szczegóły. Aplikacja sieci web będzie niedostępny z {name}. azurewebsites.net.

![AzureWebApp](./media/image10-2.png)

**Rysunek 10-2.** Tworzenie nowej usługi Azure App Service Web Apps w witrynie Azure Portal.

Proces kompilacji ciągłej integracji przeprowadzi automatyczne kompilowanie, zawsze wtedy, gdy nowy kod jest zaangażowana w repozytorium kontroli źródła projektu. Dzięki temu można natychmiast uzyskuje opinie na to, że kod zostanie skompilowany (a najlepiej przekazuje zautomatyzowane testy) i potencjalnie mogą zostać wdrożone. Kompilację o ciągłej integracji powoduje wygenerowanie sieci web wdrażanie pakietów artefaktów i opublikować ją do użycia przez proces ciągłego Dostarczania.

[Zdefiniuj proces kompilacji ciągłej integracji](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core#ci)

Pamiętaj umożliwić ciągłą integrację, więc system kolejkować kompilację, zawsze wtedy, gdy ktoś z zespołu zatwierdzeń nowego kodu. Testowanie kompilacji i sprawdź, czy jest to tworzenie internetowego wdrożyć pakiet jako jeden z jego artefaktów.

Po pomyślnym zakończeniu kompilacji, proces ciągłego Dostarczania wdroży wyniki kompilacji ciągłej integracji do aplikacji internetowej platformy Azure. Aby to skonfigurować, należy utworzyć i skonfigurować *wersji*, które zostaną wdrożone do usługi Azure App Service.

[Definiowanie procesu tworzenia wersji ciągłego Dostarczania](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core#cd)

Po skonfigurowaniu potok ciągłej integracji/ciągłego wdrażania, możesz po prostu aktualizowanie aplikacji sieci web i zatwierdzić je do kontroli źródła, aby były wdrożone.

### <a name="workflow-for-developing-azure-hosted-aspnet-core-applications"></a>Przepływ pracy umożliwiający projektowanie aplikacji hostowanych na platformie Azure platformy ASP.NET Core

Po skonfigurowaniu konta platformy Azure i procesu ciągłej integracji/ciągłego wdrażania, tworzenie aplikacji hostowanych na platformie Azure ASP.NET Core jest proste. Poniżej przedstawiono podstawowe kroki, które zazwyczaj zajmują się podczas tworzenia aplikacji ASP.NET Core, hostowana w usłudze Azure App Service jako aplikację internetową, jak pokazano w rysunek 10-3.

![EndToEndDevDeployWorkflow](./media/image10-3.png)

**Rysunek 10-3.** Instrukcje krok po kroku przepływu pracy tworzenia aplikacji platformy ASP.NET Core i hostować je na platformie Azure

#### <a name="step-1-local-dev-environment-inner-loop"></a>Krok 1. Dev w lokalnym środowisku wewnętrzną pętlę

Tworzenie aplikacji platformy ASP.NET Core do wdrożenia na platformie Azure nie różni się od tworzenia aplikacji, w przeciwnym razie. Za pomocą środowiska programowania lokalnego, który potrafisz się, czy to program Visual Studio 2017 lub wiersz polecenia dotnet i programu Visual Studio Code lub preferowanego edytora. Można napisać kod, uruchamiania i debugowania zmiany, uruchamiania testów automatycznych i wprowadzić lokalnych zatwierdzeń do kontroli źródła, dopóki wszystko będzie gotowe do Wypchnij zmiany do repozytorium kontroli źródła udostępnionego.

#### <a name="step-2-application-code-repository"></a>Krok 2. Repozytorium kodu aplikacji

Zawsze, gdy wszystko będzie gotowe udostępniać kod swojemu zespołowi, będzie wypchnąć zmiany z repozytorium lokalnego źródła do repozytorium źródłowy udostępniony Twojego zespołu. Jeśli masz doświadczenie w pracy w gałęzi niestandardowych, ten krok obejmuje zazwyczaj scalanie kodu w gałęzi udostępnionej (prawdopodobnie przez klasy [żądania ściągnięcia](https://docs.microsoft.com/azure/devops/git/pull-requests)).

#### <a name="step-3-build-server-continuous-integration-build-test-package"></a>Krok 3. Serwer kompilacji: Ciągła integracja. kompilowanie, testowanie, pakietu

Nowa kompilacja jest wyzwalana na serwerze kompilacji zawsze wtedy, gdy przeprowadzane jest zatwierdzenie nowe repozytorium kodu udostępnionej aplikacji. Jako część procesu ciągłej integracji Ta kompilacja powinna pełni skompilować aplikację i uruchomić testy automatyczne, aby upewnić się, że wszystko działa zgodnie z oczekiwaniami. Wynik końcowy w procesie ciągłej integracji powinny być spakowana utworzona wersja aplikacji sieci web, gotowe do wdrożenia.

#### <a name="step-4-build-server-continuous-delivery"></a>Krok 4. Serwer kompilacji: Ciągłe dostarczanie

Gdy kompilacja zakończyła się pomyślnie, proces ciągłego Dostarczania przejmą artefaktów kompilacji utworzone. Dotyczy to sieci web wdrożenia pakietu. Serwer kompilacji zostanie wdrożona ten pakiet w usłudze Azure App Service, zastępując wszystkie istniejące usługi na nowo utworzony zestaw. Zazwyczaj ten krok jest przeznaczony dla środowisko przejściowe, ale niektóre aplikacje wdrażać bezpośrednio w środowisku produkcyjnym przez proces ciągłego Dostarczania.

#### <a name="step-5-azure-app-service-web-app"></a>Krok 5. Usługa Azure App Service Web App

Po wdrożeniu aplikacji platformy ASP.NET Core jest uruchamiany w kontekście usługi Azure App Service Web Apps. Ta aplikacja sieci Web można monitorować, a dodatkowo skonfigurować w witrynie Azure Portal.

#### <a name="step-6-production-monitoring-and-diagnostics"></a>Krok 6. Produkcji, monitorowania i diagnostyki

Po uruchomieniu aplikacji sieci Web można monitorować kondycję aplikacji i zbierać dane diagnostyczne i dane zachowania użytkowników. Application Insights znajduje się w programie Visual Studio i oferuje automatyczną Instrumentacją dla aplikacji ASP.NET. Go może dostarczyć informacji na temat użycia, wyjątków, żądań, wydajności i dzienników.

## <a name="references"></a>Odwołania

**Tworzenie i wdrażanie aplikacji platformy ASP.NET Core na platformie Azure**  
<https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core>

>[!div class="step-by-step"]
>[Poprzednie](test-asp-net-core-mvc-apps.md)
>[dalej](azure-hosting-recommendations-for-asp-net-web-apps.md)