---
title: Kiedy należy wybrać oprogramowanie .NET Framework dla kontenerów Docker
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Kiedy należy wybrać .NET Framework kontenerów platformy Docker
ms.date: 01/07/2019
ms.openlocfilehash: 0b948017c3bbbcc8c43d5d2d9698d9a1a6f9deed
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784081"
---
# <a name="when-to-choose-net-framework-for-docker-containers"></a>Kiedy należy wybrać oprogramowanie .NET Framework dla kontenerów Docker

Chociaż platforma .NET Core oferuje znaczne korzyści dla nowych aplikacji i wzorców aplikacji, .NET Framework nadal będzie dobrym wyborem dla wielu istniejących scenariuszy.

## <a name="migrating-existing-applications-directly-to-a-windows-server-container"></a>Migrowanie istniejących aplikacji bezpośrednio do kontenera systemu Windows Server

Możesz chcieć użyć kontenerów platformy Docker tylko do uproszczenia wdrażania, nawet jeśli nie tworzysz mikrousług. Na przykład być może chcesz ulepszyć przepływ pracy usługi DevOps przy użyciu platformy Docker — kontenery mogą zapewniać lepsze izolowane środowiska testowe i mogą również wyeliminować problemy związane z wdrażaniem wynikające z brakujących zależności podczas przechodzenia do środowiska produkcyjnego. W takich przypadkach, nawet jeśli wdrażana jest aplikacja monolityczna, warto używać kontenerów Docker i Windows dla bieżących aplikacji .NET Framework.

W większości przypadków w tym scenariuszu nie ma potrzeby migrowania istniejących aplikacji do programu .NET Core; można użyć kontenerów platformy Docker, które zawierają tradycyjne .NET Framework. Jednak zalecanym podejściem jest użycie platformy .NET Core podczas rozszerzając istniejącej aplikacji, takiej jak zapisanie nowej usługi w ASP.NET Core.

## <a name="using-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>Korzystanie z bibliotek .NET innych firm lub pakietów NuGet niedostępnych dla platformy .NET Core

Biblioteki innych firm umożliwiają szybkie wdrażanie [.NET Standard](../../../standard/net-standard.md), co umożliwia udostępnianie kodu we wszystkich wersjach .NET, w tym .NET Core. W przypadku biblioteki .NET Standard 2,0 i wykraczając poza zgodność urządzeń z interfejsem API w różnych strukturach znacznie większe i w aplikacjach .NET Core 2. x mogą również bezpośrednio odwoływać się do istniejących bibliotek .NET Framework (zobacz [.NET Framework 4.6.1 obsługa .NET Standard 2,0](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#net-framework-461-supporting-net-standard-20)).

Ponadto [pakiet zgodności systemu Windows](../../../core/porting/windows-compat-pack.md) został opublikowany na lis-2017, aby zwiększyć powierzchnię interfejsu API dostępną dla .NET Standard 2,0 w systemie Windows. Ten pakiet umożliwia ponowne kompilowanie najbardziej istniejącego kodu do .NET Standard 2. x z małą lub bez modyfikacji, aby uruchomić program w systemie Windows.

Jednak nawet w przypadku nadzwyczajnych postępów od .NET Standard 2,0 i .NET Core 2,1 mogą wystąpić sytuacje, w których niektóre pakiety NuGet wymagają uruchomienia systemu Windows i mogą nie obsługiwać platformy .NET Core. Jeśli te pakiety mają krytyczne znaczenie dla aplikacji, należy użyć .NET Framework w kontenerach systemu Windows.

## <a name="using-net-technologies-not-available-for-net-core"></a>Korzystanie z technologii .NET niedostępne dla platformy .NET Core 

Niektóre technologie .NET Framework nie są dostępne w bieżącej wersji programu .NET Core (wersja 2,2). Niektóre z nich będą dostępne w nowszych wersjach platformy .NET Core (.NET Core 2. x), ale inne nie mają zastosowania do nowych wzorców aplikacji przeznaczonych dla platformy .NET Core i mogą być nigdy niedostępne.

Na poniższej liście przedstawiono większość technologii, które nie są dostępne w programie .NET Core 2. x:

- ASP.NET Web Forms. Ta technologia jest dostępna tylko na .NET Framework. Obecnie nie ma żadnych planów do przenoszenia formularzy sieci Web ASP.NET do platformy .NET Core.

- Usługi WCF. Nawet wtedy, gdy [Biblioteka klienta WCF](https://github.com/dotnet/wcf) jest dostępna do korzystania z usług WCF z platformy .NET Core, w połowie 2017 implementacja serwera WCF jest dostępna tylko na .NET Framework. Ten scenariusz może być brany pod uwagę w przyszłych wydaniach platformy .NET Core. Istnieje nawet kilka interfejsów API do uwzględnienia w [pakiecie zgodności systemu Windows](../../../core/porting/windows-compat-pack.md).

- Usługi związane z przepływem pracy. Windows Workflow Foundation (WF), usługi Workflow Services (WCF + WF w ramach jednej usługi) i Usługi danych programu WCF (dawniej znany jako ADO.NET Data Services) są dostępne tylko na .NET Framework. Obecnie nie ma żadnych planów, aby przenieść je do programu .NET Core.

Oprócz technologii wymienionych w oficjalnym [planie .NET Core](https://github.com/aspnet/Home/wiki/Roadmap), inne funkcje mogą być przemieszczone w programie .NET Core. Aby zapoznać się z pełną listą, należy zapoznać się z elementami oznaczonymi jako [Port-to-Core](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core) w witrynie CoreFX GitHub. Należy zauważyć, że ta lista nie reprezentuje zobowiązania firmy Microsoft do przenoszenia tych składników do programu .NET Core — elementy po prostu przechwytują żądania ze społeczności. Jeśli postanowisz o każdym z wymienionych powyżej składników, rozważ uczestnictwo w dyskusjach w witrynie GitHub, aby umożliwić wysłuchanie głosu. Jeśli uważasz, że coś nie ma, Utwórz [nowy problem w repozytorium CoreFX](https://github.com/dotnet/corefx/issues/new).

Mimo że program .NET Core 3 (w czasie tego pisania jest w programie Works) będzie obejmował obsługę wielu istniejących .NET Framework interfejsów API, są one zorientowane na komputery stacjonarne, a obecnie nie są one używane w świecie kontenerów.

## <a name="using-a-platform-or-api-that-does-not-support-net-core"></a>Korzystanie z platformy lub interfejsu API, który nie obsługuje programu .NET Core

Niektóre platformy firmy Microsoft lub innych firm nie obsługują platformy .NET Core. Na przykład niektóre usługi platformy Azure udostępniają zestaw SDK, który nie jest jeszcze dostępny do użycia w programie .NET Core. Jest to tymczasowe, ponieważ wszystkie usługi platformy Azure ostatecznie będą korzystać z platformy .NET Core. Na przykład [usługa Azure DOCUMENTDB SDK dla platformy .NET Core](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core/1.2.1) została wydana jako wersja zapoznawcza 16 listopada 2016, ale teraz jest ogólnie dostępna (ga) jako stabilna.

W międzyczasie, jeśli jakakolwiek platforma lub usługa na platformie Azure nadal nie obsługuje platformy .NET Core z interfejsem API klienta, można użyć równoważnego interfejsu API REST z usługi platformy Azure lub zestawu SDK klienta na .NET Framework.

### <a name="additional-resources"></a>Dodatkowe zasoby

- **Przewodnik platformy .NET Core**  
    [https://docs.microsoft.com/dotnet/core/index](../../../core/index.md)

- **Przenoszenie z .NET Framework do platformy .NET Core**  
    [https://docs.microsoft.com/dotnet/core/porting/index](../../../core/porting/index.md)

- **.NET Core w przewodniku Docker**[https://docs.microsoft.com/dotnet/core/docker/introduction](../../../core/docker/introduction.md)

- **Przegląd składników platformy .NET**  
    [https://docs.microsoft.com/dotnet/standard/components](../../../standard/components.md)

>[!div class="step-by-step"]
>[Poprzedni](net-core-container-scenarios.md)Następny
>[](container-framework-choice-factors.md)
