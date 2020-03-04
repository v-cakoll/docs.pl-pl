---
title: Wybierz między platformą .NET Core i .NET Framework dla aplikacji serwerowych
description: Przewodnik dotyczący implementacji platformy .NET, którą należy wziąć pod uwagę podczas kompilowania aplikacji serwera w programie .NET.
author: cartermp
ms.date: 06/19/2018
ms.openlocfilehash: 0b6bf4c2eb66aa4de497923a0a16b65a955ba6fc
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159978"
---
# <a name="choosing-between-net-core-and-net-framework-for-server-apps"></a>Wybieranie między programami .NET Core i .NET Framework na potrzeby aplikacji serwerowych

Istnieją dwie obsługiwane implementacje do kompilowania aplikacji po stronie serwera za pomocą platformy .NET: .NET Framework i .NET Core. Obie te same składniki są współużytkowane i można udostępnić kod w obu tych samych składnikach. Istnieją jednak podstawowe różnice między tymi, a wybór zależy od tego, co chcesz osiągnąć.  Ten artykuł zawiera wskazówki dotyczące tego, kiedy należy używać każdego z nich.

Użyj platformy .NET Core dla aplikacji serwera, gdy:

- Wymagania dotyczące wielu platform.
- Są one ukierunkowane na mikrousługi.
- Używasz kontenerów platformy Docker.
- Potrzebujesz wysokiej wydajności i skalowalności systemów.
- Musisz mieć obok siebie wersje platformy .NET dla każdej aplikacji.

Użyj .NET Framework dla aplikacji serwera, gdy:

- Twoja aplikacja używa obecnie .NET Framework (zalecane jest, aby zwiększyć zamiast migracji).
- Twoja aplikacja używa bibliotek .NET innych firm lub pakietów NuGet niedostępnych dla platformy .NET Core.
- Twoja aplikacja korzysta z technologii .NET, które nie są dostępne dla platformy .NET Core.
- Aplikacja korzysta z platformy, która nie obsługuje programu .NET Core. Systemy Windows, macOS i Linux obsługują platformę .NET Core.

## <a name="when-to-choose-net-core"></a>Kiedy należy wybrać platformę .NET Core

Poniższe sekcje zawierają bardziej szczegółowy opis powodów wyboru platformy .NET Core.

### <a name="cross-platform-needs"></a>Potrzeby dla wielu platform

Jeśli aplikacja (sieć Web/usługa) musi działać na wielu platformach (Windows, Linux i macOS), użyj platformy .NET Core.

Platforma .NET Core obsługuje wcześniej wymienione systemy operacyjne jako stacje robocze do tworzenia. Program Visual Studio udostępnia zintegrowane środowisko programistyczne (IDE) dla systemu Windows i macOS. Można również użyć Visual Studio Code, które działa w systemach macOS, Linux i Windows. Visual Studio Code obsługuje platformę .NET Core, w tym IntelliSense i debugowanie. Większość edytorów innych firm, takich jak subwapno, Emacs: i VI, pracują z platformą .NET Core. Te edytory innych firm uzyskują funkcję IntelliSense w edytorze przy użyciu [omnisharp](https://www.omnisharp.net/). Można również uniknąć dowolnego edytora kodu i bezpośrednio używać [interfejs wiersza polecenia platformy .NET Core](../core/tools/index.md), dostępnego dla wszystkich obsługiwanych platform.

### <a name="microservices-architecture"></a>Architektura mikrousług

Architektura mikrousług umożliwia łączenie różnych technologii między granicami usług. Ten miks technologii umożliwia stopniowe wdrażanie platformy .NET Core dla nowych mikrousług, które współpracują z innymi mikrousługami lub usługami. Można na przykład mieszać mikrousługi lub usługi opracowane za pomocą .NET Framework, Java, Ruby lub innych, monolitycznych technologii.

Dostępnych jest wiele platform infrastruktury. [Usługa Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/) jest przeznaczona dla dużych i złożonych systemów mikrousług. [Azure App Service](https://azure.microsoft.com/services/app-service/) to dobry wybór w przypadku mikrousług bezstanowych. Alternatywy mikrousług oparte na platformie Docker pasują do dowolnego rodzaju podejścia mikrousług, jak wyjaśniono w sekcji [Containers](#containers) . Wszystkie te platformy obsługują platformę .NET Core i sprawiają, że są one idealne do obsługi mikrousług.

Aby uzyskać więcej informacji o architekturze mikrousług, zobacz [.NET mikrousługi. Architektura dla kontenerów aplikacji .NET](../architecture/microservices/index.md).

### <a name="containers"></a>Containers

Kontenery są często używane w połączeniu z architekturą mikrousług. Kontenery mogą być również używane do konteneryzowanie aplikacji lub usług sieci Web, które są zgodne ze wzorcem architektury. .NET Framework można używać w kontenerach systemu Windows, ale modularność i lekki charakter platformy .NET Core ułatwia wybór dla kontenerów. Podczas tworzenia i wdrażania kontenera rozmiar jego obrazu jest znacznie mniejszy przy użyciu platformy .NET Core niż z .NET Framework. Ponieważ jest to platforma międzyplatformowa, można wdrożyć aplikacje serwera w kontenerach platformy Docker systemu Linux, na przykład.

Kontenery platformy Docker mogą być hostowane we własnej infrastrukturze systemu Linux lub Windows lub w usłudze w chmurze, takiej jak [usługa Azure Kubernetes](https://azure.microsoft.com/services/kubernetes-service/). Usługa Azure Kubernetes umożliwia zarządzanie, organizowanie i skalowanie aplikacji opartych na kontenerach w chmurze.

### <a name="a-need-for-high-performance-and-scalable-systems"></a>Potrzeba dla systemów o wysokiej wydajności i skalowalności

Gdy system potrzebuje najlepszej możliwej wydajności i skalowalności, program .NET Core i ASP.NET Core są najlepszymi opcjami. Środowisko uruchomieniowe serwera o wysokiej wydajności dla systemów Windows Server i Linux sprawia, że platforma sieci Web jest wydajnym środowiskiem [TechEmpower na testach porównawczych](https://www.techempower.com/benchmarks/#hw=ph&test=plaintext).

Wydajność i skalowalność są szczególnie istotne w przypadku architektury mikrousług, w których mogą być uruchomione setki mikrousług. W przypadku ASP.NET Core systemy działają z znacznie mniejszą liczbą serwerów/Virtual Machines (VM). Zredukowane serwery/maszyny wirtualne oszczędzają koszty infrastruktury i hostingu.

### <a name="a-need-for-side-by-side-of-net-versions-per-application-level"></a>Potrzeba obok siebie wersji .NET na poziom aplikacji

Aby zainstalować aplikacje z zależnościami w różnych wersjach programu .NET, zalecamy platformę .NET Core. Program .NET Core oferuje równoległą instalację różnych wersji środowiska uruchomieniowego platformy .NET Core na tym samym komputerze. Taka instalacja równoległa umożliwia korzystanie z wielu usług na tym samym serwerze, z których każda została zainstalowana w osobnym systemie .NET Core. Zmniejsza również ryzyko i oszczędza pieniądze w przypadku uaktualnień aplikacji i operacji IT.

## <a name="when-to-choose-net-framework"></a>Kiedy należy wybrać .NET Framework

Platforma .NET Core oferuje znaczące korzyści dla nowych aplikacji i wzorców aplikacji. Jednak .NET Framework nadal jest naturalnym wyborem dla wielu istniejących scenariuszy i w taki sposób .NET Framework nie jest zastępowana przez .NET Core dla wszystkich aplikacji serwera.

### <a name="current-net-framework-applications"></a>Bieżące .NET Framework aplikacje

W większości przypadków nie trzeba migrować istniejących aplikacji do programu .NET Core. Zamiast tego zalecane podejście polega na użyciu platformy .NET Core podczas rozszerzając istniejącej aplikacji, na przykład pisząc nową usługę sieci Web w ASP.NET Core.

### <a name="a-need-to-use-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>Konieczność użycia bibliotek .NET innych firm lub pakietów NuGet niedostępnych dla platformy .NET Core

Biblioteki umożliwiają szybkie wdrażanie .NET Standard. .NET Standard umożliwia udostępnianie kodu we wszystkich implementacjach platformy .NET, w tym .NET Core. W .NET Standard 2,0 jest to jeszcze prostsze:

- Powierzchnia interfejsu API stała się znacznie większa.
- Wprowadza .NET Framework tryb zgodności. Ten tryb zgodności zezwala na odwoływanie się do bibliotek .NET Framework przez projekty .NET Standard/. NET Core. Aby dowiedzieć się więcej o trybie zgodności, zobacz temat [ogłaszanie .NET Standard 2,0](https://devblogs.microsoft.com/dotnet/announcing-net-standard-2-0/).

Tak więc w przypadku, gdy biblioteki lub pakiety NuGet używają technologii, które nie są dostępne w .NET Standard/. NET Core, należy użyć .NET Framework.

### <a name="a-need-to-use-net-technologies-not-available-for-net-core"></a>Konieczne jest korzystanie z technologii .NET, które nie są dostępne dla platformy .NET Core

Niektóre technologie .NET Framework nie są dostępne w programie .NET Core. Niektóre z nich mogą być dostępne w nowszych wersjach platformy .NET Core. Inne nie mają zastosowania do nowych wzorców aplikacji przeznaczonych dla platformy .NET Core i mogą być nigdy niedostępne. Na poniższej liście przedstawiono najpopularniejsze technologie, które nie są dostępne w programie .NET Core:

- Aplikacje ASP.NET Web Forms: formularze sieci Web ASP.NET są dostępne tylko w .NET Framework. Nie można używać ASP.NET Core dla formularzy sieci Web ASP.NET. Nie istnieją plany dotyczące przenoszenia formularzy sieci Web ASP.NET do platformy .NET Core.

- Aplikacje ASP.NET Web Pages: ASP.NET Web Pages nie są uwzględnione w ASP.NET Core.

- Implementacja usług WCF. Nawet jeśli istnieje [Biblioteka klienta WCF](https://github.com/dotnet/wcf) , która umożliwia korzystanie z usług WCF z platformy .NET Core, implementacja serwera WCF jest obecnie dostępna tylko w .NET Framework. Ten scenariusz nie jest częścią bieżącego planu dla platformy .NET Core, ale jest brany pod uwagę w przyszłości.

- Usługi związane z przepływem pracy: Windows Workflow Foundation (WF), usługi Workflow Services (WCF + WF w jednej usłudze) i Usługi danych programu WCF (wcześniej znane jako "ADO.NET Data Services") są dostępne tylko w .NET Framework.  Nie ma żadnych planów, aby przenieść WF/WCF + WF/Usługi danych programu WCF do programu .NET Core.

- Obsługa języków: Visual Basic i F# są obecnie obsługiwane w programie .NET Core, ale nie dla wszystkich typów projektów. Aby zapoznać się z listą obsługiwanych szablonów projektu, zobacz [Opcje szablonu dla programu dotnet New](../core/tools/dotnet-new.md#arguments).

Oprócz oficjalnych planów istnieją inne struktury, które można przenieść do programu .NET Core. Aby uzyskać pełną listę, zobacz CoreFX problemy oznaczone jako [Port-to-Core](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core). Ta lista nie reprezentuje zobowiązania firmy Microsoft do przenoszenia tych składników do programu .NET Core. Są one po prostu przechwytywać pragnienie z społeczności, aby to zrobić. Jeśli zamierzasz dowiedzieć się więcej o składnikach oznaczonych jako `port-to-core`, weź udział w dyskusjach w witrynie GitHub. Jeśli uważasz, że coś nie ma, zastanów się w nim nowy problem w [repozytorium .NET](https://github.com/dotnet/runtime/issues/new).

### <a name="a-need-to-use-a-platform-that-doesnt-support-net-core"></a>Konieczność korzystania z platformy, która nie obsługuje programu .NET Core

Niektóre platformy firmy Microsoft lub innych firm nie obsługują platformy .NET Core. Niektóre usługi platformy Azure udostępniają zestaw SDK, który nie jest jeszcze dostępny do użycia w programie .NET Core. Jest to okoliczności przejściowe, ponieważ wszystkie usługi platformy Azure korzystają z platformy .NET Core. W międzyczasie zawsze możesz użyć równoważnego interfejsu API REST zamiast zestawu SDK klienta.

## <a name="see-also"></a>Zobacz też

- [Wybierz między ASP.NET a ASP.NET Core](/aspnet/core/choose-aspnet-framework)
- [ASP.NET Core określania celu .NET Framework](/aspnet/core#aspnet-core-targeting-net-framework)
- [Platformy docelowe](frameworks.md)
- [Przewodnik platformy .NET Core](../core/index.md)
- [Przenoszenie z .NET Framework do platformy .NET Core](../core/porting/index.md)
- [Wprowadzenie do platform .NET i Docker](../core/docker/introduction.md)
- [Przegląd składników platformy .NET](components.md)
- [Mikrousługi platformy .NET. Architektura dla kontenerów aplikacji .NET](../architecture/microservices/index.md)
