---
title: Kiedy należy wybrać oprogramowanie .NET Framework dla kontenerów Docker
description: Architektura mikrousług .NET dla konteneryzowanych aplikacji .NET | Kiedy wybrać .NET Framework dla kontenerów platformy Docker
ms.date: 01/30/2020
ms.openlocfilehash: dfb1e8883fc9c3d9235672bc2885858bfb64afa5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77501958"
---
# <a name="when-to-choose-net-framework-for-docker-containers"></a>Kiedy należy wybrać oprogramowanie .NET Framework dla kontenerów Docker

Program .NET Core oferuje znaczące korzyści dla nowych aplikacji i wzorców aplikacji, ale program .NET Framework będzie nadal dobrym wyborem dla wielu istniejących scenariuszy.

## <a name="migrating-existing-applications-directly-to-a-windows-server-container"></a>Migrowanie istniejących aplikacji bezpośrednio do kontenera systemu Windows Server

Można użyć kontenerów platformy Docker tylko w celu uproszczenia wdrażania, nawet jeśli nie tworzysz mikrousług. Na przykład być może chcesz poprawić przepływ pracy DevOps za pomocą platformy Docker — kontenery mogą zapewniać lepsze izolowane środowiska testowe, a także eliminować problemy z wdrażaniem spowodowane brakującymi zależnościami podczas przenoszenia do środowiska produkcyjnego. W takich przypadkach, nawet jeśli wdrażasz aplikację monolityczną, warto użyć platformy Docker i kontenerów systemu Windows dla bieżących aplikacji .NET Framework.

W większości przypadków w tym scenariuszu nie trzeba będzie migrować istniejących aplikacji do .NET Core; można użyć kontenerów platformy Docker, które zawierają tradycyjne .NET Framework. Jednak zaleca się podejście do korzystania z .NET Core, jak rozszerzyć istniejącą aplikację, takich jak pisanie nowej usługi w ASP.NET Core.

## <a name="using-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>Korzystanie z bibliotek .NET innych firm lub pakietów NuGet niedostępnych dla programu .NET Core

Biblioteki innych firm szybko ogarniają [standard .NET ,](../../../standard/net-standard.md)który umożliwia udostępnianie kodu we wszystkich smakach .NET, w tym w .NET Core. Z .NET Standard 2.0 i nowszych, zgodności powierzchni interfejsu API w różnych ramach stała się znacznie większa. Co więcej, .NET Core 2.x i nowsze aplikacje mogą również bezpośrednio odwoływać się do istniejących bibliotek .NET Framework (zobacz [.NET Framework 4.6.1 obsługujące .NET Standard 2.0](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#net-framework-461-supporting-net-standard-20)).

Ponadto pakiet [zgodności systemu Windows](../../../core/porting/windows-compat-pack.md) rozszerza powierzchnię interfejsu API dostępną dla .NET Standard 2.0 w systemie Windows. Ten pakiet umożliwia ponowne kompilowanie większości istniejącego kodu do .NET Standard 2.x z niewielkimi lub żadnymi modyfikacjami, aby uruchomić w systemie Windows.

Jednak nawet przy tym wyjątkowym progresji od .NET Standard 2.0 i .NET Core 2.1, mogą wystąpić przypadki, w których niektóre pakiety NuGet wymagają uruchomienia systemu Windows i mogą nie obsługiwać .NET Core. Jeśli te pakiety są krytyczne dla aplikacji, następnie należy użyć .NET Framework w kontenerach systemu Windows.

## <a name="using-net-technologies-not-available-for-net-core"></a>Korzystanie z technologii .NET niejest dostępna dla programu .NET Core

Niektóre technologie programu .NET Framework nie są dostępne w bieżącej wersji programu .NET Core (wersja 3.1 w chwili pisania). Niektóre z nich mogą stać się dostępne w nowszych wersjach, ale inne nie pasują do nowych wzorców aplikacji, na które jest przeznaczony dla programu .NET Core i mogą nigdy nie być dostępne.

Na poniższej liście przedstawiono większość technologii, które nie są dostępne w .NET Core 3.1:

- ASP.NET formularzy sieci Web. Ta technologia jest dostępna tylko w platformie .NET Framework. Obecnie nie ma żadnych planów, aby wprowadzić ASP.NET formularze sieci Web do .NET Core.

- Usługi WCF. Nawet wtedy, gdy [biblioteka Klienta WCF](https://github.com/dotnet/wcf) jest dostępna do używania usług WCF z .NET Core, od lutego do 2020 r. implementacja serwera WCF jest dostępna tylko w platformie .NET Framework. Ten scenariusz może być brany pod uwagę w przypadku przyszłych wersji programu .NET Core, istnieją nawet niektóre interfejsy API brane pod uwagę do włączenia do [pakietu zgodności systemu Windows](../../../core/porting/windows-compat-pack.md).

- Usługi związane z przepływem pracy. Windows Workflow Foundation (WF), Workflow Services (WCF + WF w jednej usłudze) i WCF Data Services (wcześniej znany jako ADO.NET Data Services) są dostępne tylko w programie .NET Framework. Obecnie nie ma żadnych planów, aby doprowadzić je do .NET Core.

Oprócz technologii wymienionych w oficjalnym [planie .NET Core](https://github.com/dotnet/core/blob/master/roadmap.md)inne funkcje mogą zostać przeniesione do .NET Core lub nowej [ujednoliconej platformy .NET](https://devblogs.microsoft.com/dotnet/introducing-net-5/). Możesz rozważyć udział w dyskusjach na GitHubie, aby twój głos był słyszalny. A jeśli uważasz, że czegoś brakuje, złóż nowy problem w repozytorium GitHub [dotnet/runtime.](https://github.com/dotnet/runtime/issues/new)

## <a name="using-a-platform-or-api-that-doesnt-support-net-core"></a>Korzystanie z platformy lub interfejsu API, który nie obsługuje programu .NET Core

Niektóre platformy firmy Microsoft i innych firm nie obsługują programu .NET Core. Na przykład niektóre usługi platformy Azure zapewniają zestaw SDK, który nie jest jeszcze dostępny do użycia w platformie .NET Core. Większość zestawu Azure SDK powinny ostatecznie zostać przeniesione do .NET Core/Standard, ale niektóre mogą nie z różnych powodów. Dostępne zestawy SDK platformy Azure można wyświetlić na stronie [Najnowsze wersje zestawu Azure SDK.](https://azure.github.io/azure-sdk/releases/latest/index.html)

W międzyczasie, jeśli jakakolwiek platforma lub usługa na platformie Azure nadal nie obsługuje .NET Core z interfejsem API klienta, można użyć równoważnego interfejsu API REST z usługi Azure lub zestawu SDK klienta w platformie .NET Framework.

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Przewodnik po rdzeniu .NET** \
  [https://docs.microsoft.com/dotnet/core/index](../../../core/index.md)

- **Przenoszenie z platformy .NET Framework do platformy .NET Core** \
  [https://docs.microsoft.com/dotnet/core/porting/index](../../../core/porting/index.md)

- **Przewodnik po platformie .NET Core w platformie Docker** \
  [https://docs.microsoft.com/dotnet/core/docker/introduction](../../../core/docker/introduction.md)

- **Omówienie składników .NET** \
  [https://docs.microsoft.com/dotnet/standard/components](../../../standard/components.md)

>[!div class="step-by-step"]
>[Poprzedni](net-core-container-scenarios.md)
>[następny](container-framework-choice-factors.md)
