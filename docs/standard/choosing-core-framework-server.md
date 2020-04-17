---
title: Wybieranie między programami .NET Core i .NET Framework na potrzeby aplikacji serwerowych
description: Przewodnik, na którym implementacji platformy .NET należy wziąć pod uwagę podczas tworzenia aplikacji serwera w programie .NET.
author: cartermp
ms.date: 06/19/2018
ms.openlocfilehash: 885a7fb3419eafa5d88ef621cf6ad04a8d48bb59
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607496"
---
# <a name="choose-between-net-core-and-net-framework-for-server-apps"></a>Wybieranie między programami .NET Core i .NET Framework na potrzeby aplikacji serwerowych

Istnieją dwie obsługiwane implementacje do tworzenia aplikacji po stronie serwera z .NET: .NET Framework i .NET Core. Oba współużytkować wiele tych samych składników i można udostępnić kod w dwóch. Istnieją jednak zasadnicze różnice między nimi i twój wybór zależy od tego, co chcesz osiągnąć.  Ten artykuł zawiera wskazówki dotyczące tego, kiedy należy używać każdego z nich.

Użyj programu .NET Core dla aplikacji serwera, gdy:

- Masz potrzeby międzyplatformowe.
- Są przeznaczone dla mikrousług.
- Używasz kontenerów platformy Docker.
- Potrzebujesz wysokowydajnych i skalowalnych systemów.
- Potrzebne są wersje platformy .NET obok siebie dla aplikacji.

Użyj programu .NET Framework dla aplikacji serwera, gdy:

- Aplikacja obecnie używa programu .NET Framework (zaleca się rozszerzenie zamiast migracji).
- Aplikacja korzysta z bibliotek platformy .NET innych firm lub pakietów NuGet, które nie są dostępne dla platformy .NET Core.
- Aplikacja korzysta z technologii platformy .NET, które nie są dostępne dla platformy .NET Core.
- Aplikacja korzysta z platformy, która nie obsługuje platformy .NET Core. Obsługa systemu Windows, macOS i Linux .NET Core.

## <a name="when-to-choose-net-core"></a>Kiedy wybrać program .NET Core

W poniższych sekcjach przedstawiono bardziej szczegółowe wyjaśnienie wcześniej podanych powodów pobrania .NET Core.

### <a name="cross-platform-needs"></a>Potrzeby między platformami

Jeśli aplikacja (sieć web/usługa) musi działać na wielu platformach (Windows, Linux i macOS), należy użyć polecenia .NET Core.

Program .NET Core obsługuje wcześniej wymienione systemy operacyjne jako rozwojową stację roboczą. Program Visual Studio udostępnia zintegrowane środowisko programistyczne (IDE) dla systemów Windows i macOS. Można również użyć programu Visual Studio Code, który działa w systemach macOS, Linux i Windows. Visual Studio Code obsługuje .NET Core, w tym IntelliSense i debugowania. Większość edytorów innych firm, takich jak Sublime, Emacs i VI, współpracuje z programem .NET Core. Te edytory innych firm uzyskać edytor IntelliSense za pomocą [Omnisharp](https://www.omnisharp.net/). Można również uniknąć dowolnego edytora kodu i bezpośrednio użyć [.NET Core CLI](../core/tools/index.md), dostępne dla wszystkich obsługiwanych platform.

### <a name="microservices-architecture"></a>Architektura mikrousług

Architektura mikrousług umożliwia mieszanie technologii w granicach usługi. Ta kombinacja technologii umożliwia stopniowe objęcie .NET Core dla nowych mikrousług, które współpracują z innymi mikrousługami lub usługami. Na przykład można mieszać mikrousług lub usług opracowanych za pomocą platformy .NET Framework, Java, Ruby lub innych technologii monolitycznych.

Dostępnych jest wiele platform infrastrukturalnych. [Usługa Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/) jest przeznaczona dla dużych i złożonych systemów mikrousług. [Usługa Azure App Service](https://azure.microsoft.com/services/app-service/) jest dobrym wyborem dla mikrousług bezstanowych. Mikrousługi alternatywy oparte na docker pasuje wszelkiego rodzaju mikrousług podejście, jak wyjaśniono w [kontenery](#containers) sekcji. Wszystkie te platformy obsługują .NET Core i sprawiają, że są idealne do obsługi mikrousług.

Aby uzyskać więcej informacji na temat architektury mikrousług, zobacz [.NET Microservices. Architektura konteneryzowanych aplikacji .NET](../architecture/microservices/index.md).

### <a name="containers"></a>Containers

Kontenery są powszechnie używane w połączeniu z architekturą mikrousług. Kontenery mogą również służyć do konteneryzacji aplikacji sieci web lub usług, które są zgodne z dowolnego wzorca architektury. Program .NET Framework może być używany w kontenerach systemu Windows, ale modułowość i lekki charakter programu .NET Core sprawiają, że jest to lepszy wybór dla kontenerów. Podczas tworzenia i wdrażania kontenera rozmiar jego obrazu jest znacznie mniejszy w przypadku programu .NET Core niż w przypadku programu .NET Framework. Ponieważ jest to międzyplatformowe, można wdrożyć aplikacje serwera do kontenerów platformy Docker systemu Linux, na przykład.

Kontenery platformy Docker mogą być hostowane we własnej infrastrukturze systemu Linux lub Windows lub w usłudze w chmurze, takiej jak [usługa Azure Kubernetes.](https://azure.microsoft.com/services/kubernetes-service/) Usługa Azure Kubernetes może zarządzać aplikacjami opartymi na kontenerach, aranżować je i skalować w chmurze.

### <a name="a-need-for-high-performance-and-scalable-systems"></a>Potrzeba systemów o wysokiej wydajności i skalowalnych

Gdy system potrzebuje najlepszej możliwej wydajności i skalowalności, .NET Core i ASP.NET Core są najlepszymi opcjami. Wysokowydajne środowisko wykonawcze serwerów dla systemów Windows Server i Linux sprawia, że program .NET jest najlepiej działającą platformą internetową w [benchmarkach TechEmpower.](https://www.techempower.com/benchmarks/#hw=ph&test=plaintext)

Wydajność i skalowalność są szczególnie istotne dla architektury mikrousług, gdzie setki mikrousług może być uruchomiony. Dzięki ASP.NET Core systemy działają ze znacznie mniejszą liczbą serwerów/maszyn wirtualnych (VM). Zredukowane serwery/maszyny wirtualne pozwalają zaoszczędzić koszty infrastruktury i hostingu.

### <a name="a-need-for-side-by-side-of-net-versions-per-application-level"></a>Potrzeba stosowania wersji .NET obok siebie na poziomie aplikacji

Aby zainstalować aplikacje z zależnościami w różnych wersjach platformy .NET, zalecamy .NET Core. Program .NET Core oferuje instalację obok siebie różnych wersji środowiska wykonawczego .NET Core na tym samym komputerze. Ta instalacja side-by-side umożliwia wiele usług na tym samym serwerze, z których każda jest dostępna we własnej wersji programu .NET Core. Zmniejsza również ryzyko i oszczędza pieniądze w uaktualnieniach aplikacji i operacjach IT.

## <a name="when-to-choose-net-framework"></a>Kiedy wybrać platformę .NET Framework

Program .NET Core oferuje znaczące korzyści dla nowych aplikacji i wzorców aplikacji. Jednak .NET Framework nadal jest naturalnym wyborem dla wielu istniejących scenariuszy i jako takie .NET Framework nie jest zastępowany przez .NET Core dla wszystkich aplikacji serwera.

### <a name="current-net-framework-applications"></a>Bieżące aplikacje .NET Framework

W większości przypadków nie trzeba migrować istniejących aplikacji do platformy .NET Core. Zamiast tego zalecane podejście jest użycie .NET Core podczas rozszerzania istniejącej aplikacji, takich jak pisanie nowej usługi sieci web w ASP.NET Core.

### <a name="a-need-to-use-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>Potrzeba użycia bibliotek .NET innych firm lub pakietów NuGet nie jest dostępna dla platformy .NET Core

Biblioteki szybko ogarniają standard .NET. Program .NET Standard umożliwia udostępnianie kodu we wszystkich implementacjach platformy .NET, w tym w programach .NET Core. W przypadku platformy .NET Standard 2.0 jest to jeszcze łatwiejsze:

- Powierzchnia interfejsu API stała się znacznie większa.
- Wprowadzono tryb zgodności programu .NET Framework. Ten tryb zgodności umożliwia projektom .NET Standard/.NET Core odwoływanie się do bibliotek programu .NET Framework. Aby dowiedzieć się więcej o trybie zgodności, zobacz [Ogłaszanie standardu .NET Standard 2.0](https://devblogs.microsoft.com/dotnet/announcing-net-standard-2-0/).

Tak więc tylko w przypadkach, gdy biblioteki lub pakiety NuGet używać technologii, które nie są dostępne w .NET Standard/.NET Core, należy użyć .NET Framework.

### <a name="a-need-to-use-net-technologies-not-available-for-net-core"></a>Potrzeba użycia technologii .NET niedostępna dla platformy .NET Core

Niektóre technologie platformy .NET Framework nie są dostępne w ramach platformy .NET Core. Niektóre z nich mogą być dostępne w późniejszych wersjach .NET Core. Inne nie mają zastosowania do nowych wzorców aplikacji, których dotyczy program .NET Core i mogą nigdy nie być dostępne. Na poniższej liście przedstawiono najczęściej spotykane technologie, które nie zostały znalezione w pliku .NET Core:

- ASP.NET aplikacji formularzy sieci Web: ASP.NET formularzy sieci Web są dostępne tylko w ramach .NET Framework. ASP.NET Core nie może być używany w ASP.NET formularzach sieci Web. Nie ma żadnych planów wprowadzenia ASP.NET formularzy sieci Web do platformy .NET Core.

- ASP.NET aplikacji stron sieci Web: ASP.NET strony sieci Web nie są uwzględniane w ASP.NET Core.

- implementacji usług WCF. Nawet wtedy, gdy istnieje [biblioteka WCF-Client](https://github.com/dotnet/wcf) do korzystania z usług WCF z .NET Core, implementacja serwera WCF jest obecnie dostępna tylko w ramach .NET Framework. Ten scenariusz nie jest częścią bieżącego planu dla platformy .NET Core, ale jest rozważany na przyszłość.

- Usługi związane z przepływem pracy: Windows Workflow Foundation (WF), Workflow Services (WCF + WF w jednej usłudze) i WCF Data Services (dawniej znane jako "ADO.NET Data Services") są dostępne tylko w programie .NET Framework.  Nie ma żadnych planów, aby przenieść WF/WCF +WF/WCF Usługi danych do .NET Core.

- Obsługa języka: Visual Basic i F# są obecnie obsługiwane w programie .NET Core, ale nie dla wszystkich typów projektów. Aby uzyskać listę obsługiwanych szablonów projektów, zobacz [Opcje szablonów dla dotnet new](../core/tools/dotnet-new.md#arguments).

Oprócz oficjalnego planu działania istnieją inne struktury, które mają zostać przeniesione do platformy .NET Core. Aby uzyskać pełną listę, zobacz problemy CoreFX oznaczone jako [port-core](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core). Ta lista nie reprezentuje zobowiązania firmy Microsoft do wprowadzenia tych składników do platformy .NET Core. Po prostu chwytają pragnienie społeczności, aby to zrobić. Jeśli zależy Ci na którykolwiek `port-to-core`ze składników oznaczonych jako , weź udział w dyskusjach na GitHub. A jeśli uważasz, że czegoś brakuje, złóż nowy problem w [repozytorium .NET](https://github.com/dotnet/runtime/issues/new).

### <a name="a-need-to-use-a-platform-that-doesnt-support-net-core"></a>Konieczność korzystania z platformy, która nie obsługuje programu .NET Core

Niektóre platformy firmy Microsoft lub innych firm nie obsługują platformy .NET Core. Niektóre usługi platformy Azure zapewniają zestaw SDK, który nie jest jeszcze dostępny do użycia w programie .NET Core. Jest to okoliczność przejściowa, ponieważ wszystkie usługi platformy Azure używają platformy .NET Core. W międzyczasie zawsze można użyć równoważnego interfejsu API REST zamiast sdk klienta.

## <a name="see-also"></a>Zobacz też

- [Wybierz między ASP.NET a ASP.NET Core](/aspnet/core/choose-aspnet-framework)
- [Platforma ASP.NET Core ukierunkowana na platformę .NET Framework](/aspnet/core/introduction-to-aspnet-core#aspnet-core-targeting-net-framework)
- [Platformy docelowe](frameworks.md)
- [Przewodnik po rdzeniu .NET](../core/index.yml)
- [Przenoszenie z programu .NET Framework do programu .NET Core](../core/porting/index.md)
- [Wprowadzenie do platform .NET i Docker](../core/docker/introduction.md)
- [Omówienie składników platformy .NET](components.md)
- [Mikrousług .NET. Architektura konteneryzowanych aplikacji .NET](../architecture/microservices/index.md)
