---
title: Kiedy należy wybrać oprogramowanie .NET Framework dla kontenerów Docker
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Kiedy należy wybrać oprogramowanie .NET Framework dla kontenerów Docker
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/11/2018
ms.openlocfilehash: 1a91f645aa6f9ce8652fb18243c2e2775abe87d1
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53128755"
---
# <a name="when-to-choose-net-framework-for-docker-containers"></a>Kiedy należy wybrać oprogramowanie .NET Framework dla kontenerów Docker

Natomiast platformy .NET Core oferuje znaczące korzyści w przypadku nowych aplikacji i wzorców do zastosowań, .NET Framework będą nadal być dobrym wyborem dla wielu istniejących scenariuszy.

## <a name="migrating-existing-applications-directly-to-a-windows-server-container"></a>Migrowanie istniejących aplikacji bezpośrednio do kontenera systemu Windows Server

Możesz chcieć użyć kontenerów platformy Docker po prostu można Uproszczenie wdrażania, nawet wtedy, gdy są nietworzenie mikrousług. Na przykład, być może chcesz poprawę pracy DevOps z platformą Docker, kontenery umożliwiają lepsze izolowane testowym i również eliminuje problemy z wdrażaniem spowodowany brakującymi zależnościami, po przejściu do środowiska produkcyjnego. W takich przypadkach nawet wtedy, gdy wdrażasz aplikacji monolitycznej, warto używać platformy Docker i kontenerów Windows dla istniejących aplikacji .NET Framework.

W większości przypadków w tym scenariuszu nie należy do migrowania istniejących aplikacji .NET Core; Możesz użyć kontenerów platformy Docker, które obejmują tradycyjnych .NET Framework. Jednak zalecanym podejściem jest używać platformy .NET Core, jak rozszerzyć istniejącą aplikację, takie jak zapisywanie nowej usługi w programie ASP.NET Core.

## <a name="using-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>Za pomocą biblioteki .NET innych firm lub pakiety NuGet nie są dostępne dla platformy .NET Core

Szybko używają bibliotek innych firm [.NET Standard](../../net-standard.md), która umożliwia udostępnianie we wszystkich wersjach platformy .NET, w tym .NET Core kodu. Za pomocą platformy .NET Standard 2.0 biblioteki i nie tylko powierzchni interfejsu API zgodność dla różnych platform stało się znacznie większe i platformie .NET Core 2.x aplikacji można także bezpośrednio odwoływać się do istniejących bibliotek .NET Framework (zobacz [zgodności podkładki](https://github.com/dotnet/standard/blob/master/docs/netstandard-20/README.md#net-framework-461-supporting-net-standard-20)).

Ponadto [systemie Windows Compatibility Pack](../../../core/porting/windows-compat-pack.md) został wydany Listopada 2017 r. Aby rozszerzyć powierzchni interfejsu API dostępne dla platformy .NET Standard 2.0 na Windows. Ten pakiet umożliwia ponownej kompilacji większość istniejącego kodu .NET Standard 2.x z niewielkie modyfikacje, systemem Windows.

Jednak nawet w przypadku tego wyjątkowych postęp od .NET Standard 2.0 i .NET Core 2.1, może istnieć przypadkach, gdy niektóre pakiety NuGet muszą Windows do uruchomienia i nie może obsługiwać platformę .NET Core. Jeśli te pakiety są krytyczne dla swojej aplikacji, należy używać .NET Framework w kontenerach Windows.

## <a name="using-net-technologies-not-available-for-net-core"></a>Przy użyciu technologii .NET, które nie są dostępne dla platformy .NET Core 

Niektóre technologie .NET Framework nie są dostępne w bieżącej wersji programu .NET Core (wersja 2.1 w trakcie tworzenia tej dokumentacji). Niektóre z nich będzie dostępny w nowszych wersjach platformy .NET Core (.NET Core 2.x), ale nie dotyczą innych nową aplikację wzorce docelowej platformy .NET Core i nigdy nie mogą być dostępne.

Na poniższej liście przedstawiono najbardziej technologii, które nie są dostępne w programie .NET Core 2.x:

-   Formularze sieci Web ASP.NET. Ta technologia jest dostępna tylko w programie .NET Framework. Obecnie nie ma żadnych planów, aby wyświetlić formularzy sieci Web ASP.NET i .NET Core.

-   Usługi WCF. Nawet wtedy, gdy [biblioteki klienta platformy WCF](https://github.com/dotnet/wcf) jest dostępna do korzystania z usług WCF z platformy .NET Core, ponieważ połowie 2017 implementacji serwera WCF jest dostępna tylko w programie .NET Framework. Ten scenariusz może zostać uznane za w przyszłych wersjach programu .NET Core, istnieją nawet z niektórych interfejsów API uwzględnione w w [systemie Windows Compatibility Pack](../../../core/porting/windows-compat-pack.md).

-   Usługi związane z przepływu pracy. Windows Workflow Foundation (WF), usługi przepływu pracy (WCF + WF w jednej usłudze) i usługi danych WCF (wcześniej znane jako architektury ADO.NET Data Services) są dostępne tylko w programie .NET Framework. Obecnie nie ma żadnych planów, aby dostosować je do programu .NET Core.

Technologie wymienione w oficjalnym [harmonogram działania dla platformy .NET Core](https://github.com/aspnet/Home/wiki/Roadmap), inne funkcje mogą być przenoszone do platformy .NET Core. Aby uzyskać pełną listę, Przyjrzyj się elementy oznaczone jako [portu core](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core) w witrynie CoreFX GitHub. Uwaga Ta lista nie reprezentuje zobowiązania firmy Microsoft na wprowadzanie tych składników na platformy .NET Core — elementy po prostu przechwytywać żądania od społeczności. Jeśli interesujące Cię któregokolwiek ze składników wymienionych powyżej, należy wziąć pod uwagę uczestniczących w dyskusji w witrynie GitHub, dzięki czemu Twój głos może Twój głos zostanie wysłuchany. A jeśli Twoim zdaniem czegoś brakuje, [pliku nowego problemu w repozytorium CoreFX](https://github.com/dotnet/corefx/issues/new).

Mimo że program .NET Core 3 (w momencie pisania tego dokumentu, to w działa) będzie zawierać obsługę wiele istniejących interfejsów API programu .NET Framework, są to zorientowane na tak, obecnie pulpitu, są one użycia na całym świecie kontenera.

## <a name="using-a-platform-or-api-that-does-not-support-net-core"></a>Przy użyciu platformy i interfejsu API, który nie obsługuje platformy .NET Core

Niektóre firmy Microsoft lub innych platform nie obsługują platformy .NET Core. Na przykład niektórych usług platformy Azure zapewniają zestawu SDK, które nie są jeszcze dostępne do użycia na platformie .NET Core. Może to być tymczasowy, dlatego wszystkich usług platformy Azure zostanie ostatecznie wykorzystania platformy .NET Core. Na przykład [zestawu SDK usługi DocumentDB na platformie Azure dla platformy .NET Core](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core/1.2.1) został wydany w wersji zapoznawczej 16 listopada 2016 r., lecz teraz jest ogólnie dostępna (GA) jako stabilną wersję.

W międzyczasie dowolnej platformy i usługi na platformie Azure nadal nie obsługuje platformy .NET Core za pomocą jego interfejsu API klienta, można użyć równoważne interfejsu API REST usługi platformy Azure lub zestawu SDK klienta w programie .NET Framework.

### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Przewodnik platformy .NET Core**  
    [https://docs.microsoft.com/dotnet/core/index](../../../core/index.md)

-   **Przenoszenie z .NET Framework i .NET Core**  
    [https://docs.microsoft.com/dotnet/core/porting/index](../../../core/porting/index.md)

-   **.NET Framework na platformie Docker — przewodnik**  
    [https://docs.microsoft.com/dotnet/framework/docker/](../../../framework/docker/index.md)

-   **Omówienie składników platformy .NET**  
    [https://docs.microsoft.com/dotnet/standard/components](../../components.md)

>[!div class="step-by-step"]
>[Poprzednie](net-core-container-scenarios.md)
>[dalej](container-framework-choice-factors.md)