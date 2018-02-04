---
title: "Kiedy należy wybrać .NET Framework dla kontenerów Docker"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Kiedy należy wybrać .NET Framework dla kontenerów Docker"
keywords: Docker, Microservices, ASP.NET, Container
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: fcfb78bf521107b14d7796235f52c836f48f41fe
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="when-to-choose-net-framework-for-docker-containers"></a>Kiedy należy wybrać .NET Framework dla kontenerów Docker

Gdy oprogramowanie .NET Core oferuje istotne korzyści dla nowych aplikacji i wzorce aplikacji, .NET Framework będzie nadal dobrym rozwiązaniem w przypadku wielu istniejących scenariuszy.

## <a name="migrating-existing-applications-directly-to-a-windows-server-container"></a>Migrowanie istniejących aplikacji bezpośrednio do kontenera systemu Windows Server

Można użyć kontenery Docker tylko w celu uproszczenia wdrażania, nawet jeśli nie utworzysz mikrousług. Na przykład, prawdopodobnie chcesz zwiększyć DevOps przepływu pracy z rozwiązaniem Docker z — kontenery pozwoli lepiej izolowanego testu środowisk i pozwala również wyeliminować problemy z wdrażaniem spowodowane przez Brak zależności po przejściu do środowiska produkcyjnego. W takich przypadkach nawet wtedy, gdy wdrażasz aplikację wbudowanymi dobrym rozwiązaniem jest użycie dla bieżącej aplikacji .NET Framework Docker i kontenery systemu Windows.

W większości przypadków w tym scenariuszu nie należy przeprowadzić migrację istniejących aplikacji .NET Core; Możesz użyć Docker kontenerów, które obejmują tradycyjnych .NET Framework. Jednak zalecanym podejściem jest użycie .NET Core, jak rozszerzyć istniejącą aplikację, takie jak zapisywanie nową usługę w ASP.NET Core.

## <a name="using-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>Przy użyciu bibliotek .NET innych firm lub pakietów NuGet nie jest dostępna dla platformy .NET Core

Biblioteki innych firm są szybko obejmującego [.NET Standard](https://docs.microsoft.com/dotnet/standard/net-standard), która umożliwia udostępnianie wszystkich odmian .NET, w tym oprogramowanie .NET Core kodu. Standardowa biblioteka .NET 2.0 i nowszych powierzchni interfejsu API zgodności na różnych platformach stało się znacznie większe i w programie .NET Core 2.0 aplikacji można również bezpośrednio odwoływać istniejących bibliotek .NET Framework (zobacz [compat podkładki](https://github.com/dotnet/standard/blob/master/docs/faq.md#how-does-net-standard-versioning-work)).

Jednak nawet w przypadku tego wyjątkowych postępu od platformy .NET Standard w wersji 2.0 i .NET Core 2.0, mogą wystąpić przypadkach potrzebne do pracy systemu Windows i mogą nie obsługiwać .NET Core niektórych pakietów NuGet. Jeśli te pakiety są krytyczne dla aplikacji, będzie konieczne używanie środowiska .NET Framework do kontenerów systemu Windows.

## <a name="using-net-technologies-not-available-for-net-core"></a>Przy użyciu technologii .NET nie jest dostępna dla platformy .NET Core 

Niektóre technologie .NET Framework nie są dostępne w bieżącej wersji programu .NET Core (wersja 2.0 opracowywania tego tekstu). Niektóre z nich będzie dostępny w nowszych wersjach platformy .NET Core (.NET Core 2.x), ale nie dotyczą innych nowej aplikacji wzorce objęci .NET Core i nigdy nie mogą być dostępne.

Poniższa lista zawiera większość technologie, które nie są dostępne w programie .NET Core 2.0:

-   Formularze sieci Web ASP.NET. Ta technologia jest dostępna tylko w środowisku .NET Framework. Obecnie nie ma żadnych planów, aby wyświetlić formularzy sieci Web ASP.NET w celu .NET Core.

-   Usługi WCF. Nawet wtedy, gdy [biblioteki klienta WCF](https://github.com/dotnet/wcf) jest dostępny do korzystania z usług WCF z platformy .NET Core. począwszy od połowy 2017 implementacją serwera WCF jest dostępna tylko w środowisku .NET Framework. Ten scenariusz może zostać uznane za w przyszłych wersjach programu .NET Core.

-   Usługi związane z przepływu pracy. Windows Workflow Foundation (WF), usługi przepływu pracy (WCF i WF w jednej usługi) i usługi danych WCF (wcześniej znane jako ADO.NET Data Services) są dostępne tylko w środowisku .NET Framework. Obecnie nie ma żadnych planów, aby dostosować je do platformy .NET Core.

Technologie wymienionych w oficjalnym [plan .NET Core](https://github.com/aspnet/Home/wiki/Roadmap), inne funkcje mogą być przenoszone do platformy .NET Core. Aby uzyskać pełną listę przyjrzeć się elementy oznaczone jako [portu core](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core) w witrynie CoreFX GitHub. Należy pamiętać, że ta lista nie reprezentuje zobowiązania firmy Microsoft, aby przenieść te składniki .NET Core — elementy po prostu przechwytywać żądania przez społeczność. Jeśli interesują o wyżej wymienione składniki, rozważ należący do dyskusji w witrynie GitHub, aby Twój głos można Twój głos zostanie wysłuchany. A jeśli uważasz, że element nie istnieje, skontaktuj się z [pliku nowego problemu w repozytorium CoreFX](https://github.com/dotnet/corefx/issues/new).

## <a name="using-a-platform-or-api-that-does-not-support-net-core"></a>Przy użyciu platformy lub interfejsu API, który nie obsługuje platformy .NET Core

Niektóre firmy Microsoft lub innych platform nie obsługują .NET Core. Na przykład niektóre usługi Azure zapewniają zestawu SDK, który nie jest jeszcze dostępne do użycia przez .NET Core. Jest to tymczasowe, ponieważ wszystkich usług platformy Azure po pewnym czasie będzie używać .NET Core. Na przykład [Azure DocumentDB SDK dla platformy .NET Core](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core/1.2.1) został wydany jako podgląd 16 listopada 2016, lecz teraz jest ogólnie dostępna (GA) w wersji stabilnej.

Tymczasem dowolną platformę i dowolne usługi w usłudze Azure nadal nie obsługuje platformy .NET Core z klienta interfejsu API, można użyć równoważnych interfejsu API REST usługi Azure lub zestawu SDK klienta w programie .NET Framework.

### <a name="additional-resources"></a>Dodatkowe zasoby

-   **.NET core przewodnik**
    [*https://docs.microsoft.com/dotnet/core/index*](https://docs.microsoft.com/dotnet/core/index)

-   **Eksportowanie z .NET Framework do platformy .NET Core**
    [*https://docs.microsoft.com/dotnet/core/porting/index*](https://docs.microsoft.com/dotnet/core/porting/index)

-   **.NET framework w przewodniku Docker**
    [*https://docs.microsoft.com/dotnet/framework/docker/*](https://docs.microsoft.com/dotnet/framework/docker/)

-   **Omówienie składników platformy .NET**
    [*https://docs.microsoft.com/dotnet/standard/components*](https://docs.microsoft.com/dotnet/standard/components)




>[!div class="step-by-step"]
[Previous] (net-core-container-scenarios.md) [Next] (container-framework-choice-factors.md)
