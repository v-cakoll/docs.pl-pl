---
title: Kiedy należy wybrać oprogramowanie .NET Framework dla kontenerów Docker
description: Architektura mikrousług platformy .NET dla konteneryzowanych aplikacji .NET | Kiedy wybrać platformę .NET Framework dla kontenerów platformy Docker
ms.date: 01/30/2020
ms.openlocfilehash: 2697ae56eda104a0ee8e7bfcd79d3972943d1f79
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344994"
---
# <a name="when-to-choose-net-framework-for-docker-containers"></a>Kiedy należy wybrać oprogramowanie .NET Framework dla kontenerów Docker

Program .NET Core oferuje znaczące korzyści dla nowych aplikacji i wzorców aplikacji, program .NET Framework nadal będzie dobrym wyborem dla wielu istniejących scenariuszy.

## <a name="migrating-existing-applications-directly-to-a-windows-server-container"></a>Migrowanie istniejących aplikacji bezpośrednio do kontenera systemu Windows Server

Można użyć kontenerów platformy Docker tylko w celu uproszczenia wdrażania, nawet jeśli nie są tworzenie mikrousług. Na przykład być może chcesz poprawić przepływ pracy DevOps za pomocą platformy Docker — kontenery mogą zapewnić lepsze izolowane środowiska testowe, a także wyeliminować problemy z wdrażaniem spowodowane brakującymi zależnościami podczas przenoszenia do środowiska produkcyjnego. W takich przypadkach, nawet jeśli wdrażasz aplikację monolityczną, warto używać docker i kontenerów systemu Windows dla bieżących aplikacji .NET Framework.

W większości przypadków w tym scenariuszu nie trzeba będzie migrować istniejących aplikacji do platformy .NET Core; można użyć kontenerów platformy Docker, które zawierają tradycyjne .NET Framework. Jednak zalecane podejście jest użycie .NET Core podczas rozszerzania istniejącej aplikacji, takich jak pisanie nowej usługi w ASP.NET Core.

## <a name="using-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>Korzystanie z bibliotek .NET innych firm lub pakietów NuGet nie jest dostępne dla programu .NET Core

Biblioteki innych firm szybko obejmują [.NET Standard](../../../standard/net-standard.md), który umożliwia udostępnianie kodu we wszystkich smakach platformy .NET, w tym .NET Core. Z .NET Standard 2.0 i nowsze, zgodność powierzchni interfejsu API w różnych ramach stała się znacznie większa. Co więcej, .NET Core 2.x i nowsze aplikacje mogą również bezpośrednio odwoływać się do istniejących bibliotek programu .NET Framework (zobacz [.NET Framework 4.6.1 obsługujący program .NET Standard 2.0](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#net-framework-461-supporting-net-standard-20)).

Ponadto pakiet [zgodności systemu Windows](../../../core/porting/windows-compat-pack.md) rozszerza powierzchnię interfejsu API dostępną dla platformy .NET Standard 2.0 w systemie Windows. Ten pakiet umożliwia ponowne skompilowanie większości istniejącego kodu do platformy .NET Standard 2.x z niewielką lub żadną modyfikacją, aby uruchomić go w systemie Windows.

Jednak nawet przy tym wyjątkowy postęp od .NET Standard 2.0 i .NET Core 2.1, mogą wystąpić przypadki, w których niektóre pakiety NuGet wymagają systemu Windows do uruchomienia i może nie obsługiwać .NET Core. Jeśli te pakiety są krytyczne dla aplikacji, należy użyć programu .NET Framework w kontenerach systemu Windows.

## <a name="using-net-technologies-not-available-for-net-core"></a>Korzystanie z technologii .NET jest niedostępne dla platformy .NET Core

Niektóre technologie platformy .NET Framework nie są dostępne w bieżącej wersji programu .NET Core (wersja 3.1 w chwili pisania tego tekstu). Niektóre z nich mogą być dostępne w późniejszych wersjach, ale inne nie pasują do nowych wzorców aplikacji, do których kierowany jest program .NET Core i mogą nigdy nie być dostępne.

Na poniższej liście przedstawiono większość technologii, które nie są dostępne w .NET Core 3.1:

- ASP.NET formularzy sieci Web. Ta technologia jest dostępna tylko w programie .NET Framework. Obecnie nie ma planów wprowadzenia ASP.NET formularzy sieci Web do platformy .NET Core.

- usługi WCF. Nawet wtedy, gdy [biblioteka WCF-Client](https://github.com/dotnet/wcf) jest dostępna do korzystania z usług WCF z .NET Core, od lutego-2020 r. implementacja serwera WCF jest dostępna tylko w programie .NET Framework. Ten scenariusz może być rozważony w przyszłych wersjach programu .NET Core, istnieją nawet niektóre interfejsy API rozważane do włączenia do [pakietu zgodności systemu Windows](../../../core/porting/windows-compat-pack.md).

- Usługi związane z przepływem pracy. Windows Workflow Foundation (WF), Workflow Services (WCF + WF w jednej usłudze) i WCF Data Services (dawniej znany jako ADO.NET Usługi danych) są dostępne tylko w programie .NET Framework. Obecnie nie ma planów, aby doprowadzić je do .NET Core.

Oprócz technologii wymienionych w oficjalnym [planie działania platformy .NET Core](https://github.com/dotnet/core/blob/master/roadmap.md)inne funkcje mogą zostać przeniesione na platformę .NET Core lub nową [zunifikowaną platformę .NET.](https://devblogs.microsoft.com/dotnet/introducing-net-5/) Możesz rozważyć udział w dyskusjach na GitHub, aby twój głos mógł zostać usłyszany. A jeśli uważasz, że czegoś brakuje, zgłać nowy problem w repozytorium [dotnet/runtime](https://github.com/dotnet/runtime/issues/new) GitHub.

## <a name="using-a-platform-or-api-that-doesnt-support-net-core"></a>Korzystanie z platformy lub interfejsu API, który nie obsługuje programu .NET Core

Niektóre platformy firmy Microsoft i innych firm nie obsługują platformy .NET Core. Na przykład niektóre usługi platformy Azure zapewniają zestaw SDK, który nie jest jeszcze dostępny do użycia w programie .NET Core. Większość zestawów SDK platformy Azure należy ostatecznie przenieść do platformy .NET Core/Standard, ale niektóre mogą nie z różnych powodów. Dostępne zestawy SDK platformy Azure można zobaczyć na stronie [Najnowsze wersje zestawów SDK platformy Azure.](https://azure.github.io/azure-sdk/releases/latest/index.html)

W międzyczasie, jeśli dowolna platforma lub usługa na platformie Azure nadal nie obsługuje programu .NET Core z interfejsem API klienta, można użyć równoważnego interfejsu API REST z usługi Azure lub sdk klienta w programie .NET Framework.

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Przewodnik po rdzeniu .NET** \
  [https://docs.microsoft.com/dotnet/core/index](../../../core/index.yml)

- **Przenoszenie z programu .NET Framework do programu .NET Core** \
  [https://docs.microsoft.com/dotnet/core/porting/index](../../../core/porting/index.md)

- **Przewodnik po programie .NET Core on Docker** \
  [https://docs.microsoft.com/dotnet/core/docker/introduction](../../../core/docker/introduction.md)

- **Omówienie składników platformy .NET** \
  [https://docs.microsoft.com/dotnet/standard/components](../../../standard/components.md)

>[!div class="step-by-step"]
>[Poprzedni](net-core-container-scenarios.md)
>[następny](container-framework-choice-factors.md)
