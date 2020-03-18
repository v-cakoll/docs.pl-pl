---
title: Wybieranie między programami .NET Core i .NET Framework dla aplikacji serwerowych
description: Przewodnik, który implementacji .NET należy wziąć pod uwagę podczas tworzenia aplikacji serwera w .NET.
author: cartermp
ms.date: 06/19/2018
ms.openlocfilehash: 0b6bf4c2eb66aa4de497923a0a16b65a955ba6fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159978"
---
# <a name="choosing-between-net-core-and-net-framework-for-server-apps"></a>Wybieranie między programami .NET Core i .NET Framework na potrzeby aplikacji serwerowych

Istnieją dwie obsługiwane implementacje do tworzenia aplikacji po stronie serwera z .NET: .NET Framework i .NET Core. Oba współużytkują wiele tych samych składników i można udostępniać kod między tymi dwoma. Istnieją jednak zasadnicze różnice między tymi dwoma i wybór zależy od tego, co chcesz osiągnąć.  Ten artykuł zawiera wskazówki dotyczące używania każdego z nich.

Użyj programu .NET Core dla aplikacji serwera, gdy:

- Masz potrzeby wieloplatformowe.
- Są przeznaczone mikrousług.
- Używasz kontenerów platformy Docker.
- Potrzebujesz wydajnych i skalowalnych systemów.
- Na aplikację potrzebne są wersje .NET obok siebie.

Użyj platformy .NET Framework dla aplikacji serwera, gdy:

- Aplikacja korzysta obecnie z platformy .NET Framework (zaleca się rozszerzenie zamiast migracji).
- Aplikacja korzysta z bibliotek .NET innych firm lub pakietów NuGet niedostępnych dla .NET Core.
- Aplikacja korzysta z technologii .NET, które nie są dostępne dla .NET Core.
- Aplikacja korzysta z platformy, która nie obsługuje .NET Core. Obsługa systemów Windows, macOS i Linux .NET Core.

## <a name="when-to-choose-net-core"></a>Kiedy wybrać .NET Core

W poniższych sekcjach przedstawiono bardziej szczegółowe wyjaśnienie wcześniej poddanych powodów pobrania .NET Core.

### <a name="cross-platform-needs"></a>Potrzeby międzyplatformowe

Jeśli aplikacja (sieć Web/usługa) musi działać na wielu platformach (Windows, Linux i macOS), użyj .NET Core.

Program .NET Core obsługuje wcześniej wymienione systemy operacyjne jako rozwijanie stacji roboczej. Visual Studio udostępnia zintegrowane środowisko programistyczne (IDE) dla systemów Windows i macOS. Można również użyć kodu programu Visual Studio, który jest uruchamiany w systemach macOS, Linux i Windows. Visual Studio Code obsługuje .NET Core, w tym IntelliSense i debugowania. Większość edytorów innych firm, takich jak Sublime, Emacs i VI, współpracuje z .NET Core. Te edytory innych firm uzyskać edytor IntelliSense za pomocą [Omnisharp](https://www.omnisharp.net/). Można również uniknąć edytora kodu i bezpośrednio użyć [.NET Core CLI](../core/tools/index.md), dostępne dla wszystkich obsługiwanych platform.

### <a name="microservices-architecture"></a>Architektura mikrousług

Architektura mikrousług umożliwia połączenie technologii na granicy usługi. Ta kombinacja technologii umożliwia stopniowe objęcie .NET Core dla nowych mikrousług, które współpracują z innymi mikrousług lub usług. Na przykład można mieszać mikrousług lub usług opracowanych z .NET Framework, Java, Ruby lub innych technologii monolitycznych.

Dostępnych jest wiele platform infrastruktury. [Sieć szkieletowa usług azure](https://azure.microsoft.com/services/service-fabric/) jest przeznaczony dla dużych i złożonych systemów mikrousług. [Usługa Azure App Service](https://azure.microsoft.com/services/app-service/) jest dobrym wyborem dla mikrousług bezstanowych. Alternatywy mikrousług oparte na platformie Docker pasują do każdego rodzaju podejścia mikrousług, jak wyjaśniono w [kontenerach](#containers) sekcji. Wszystkie te platformy obsługują program .NET Core i sprawiają, że są idealne do obsługi mikrousług.

Aby uzyskać więcej informacji na temat architektury mikrousług, zobacz [.NET Mikrousług. Architektura konteneryzowanych aplikacji .NET](../architecture/microservices/index.md).

### <a name="containers"></a>Kontenery

Kontenery są często używane w połączeniu z architekturą mikrousług. Kontenery mogą również służyć do konteneryzacji aplikacji sieci web lub usług, które następują do dowolnego wzorca architektury. Program .NET Framework może być używany w kontenerach systemu Windows, ale modułowość i lekki charakter .NET Core sprawia, że jest to lepszy wybór dla kontenerów. Podczas tworzenia i wdrażania kontenera rozmiar jego obrazu jest znacznie mniejszy w przypadku programu .NET Core niż w przypadku programu .NET Framework. Ponieważ jest to wiele platform, można wdrożyć aplikacje serwera do kontenerów platformy Docker systemu Linux, na przykład.

Kontenery platformy Docker mogą być hostowane we własnej infrastrukturze systemu Linux lub Windows lub w usłudze w chmurze, takiej jak [usługa Azure Kubernetes .](https://azure.microsoft.com/services/kubernetes-service/) Usługa Azure Kubernetes service może zarządzać aplikacjami opartymi na kontenerach w chmurze, aranżować je i skalować.

### <a name="a-need-for-high-performance-and-scalable-systems"></a>Zapotrzebowanie na wydajne i skalowalne systemy

Gdy system potrzebuje najlepszej możliwej wydajności i skalowalności, najlepszymi opcjami są .NET Core i ASP.NET Core. Środowisko uruchomieniowe serwera o wysokiej wydajności dla systemów Windows Server i Linux sprawia, że program .NET jest najlepszym systemem sieci Web na [testach porównawczych TechEmpower.](https://www.techempower.com/benchmarks/#hw=ph&test=plaintext)

Wydajność i skalowalność są szczególnie istotne dla architekturmikrousług, gdzie setki mikrousług mogą być uruchomione. W przypadku ASP.NET Core systemy działają ze znacznie mniejszą liczbą serwerów/maszyn wirtualnych (VM). Zmniejszone serwery/maszyny wirtualne oszczędzają koszty w infrastrukturze i hostingu.

### <a name="a-need-for-side-by-side-of-net-versions-per-application-level"></a>Potrzeba obok wersji .NET na poziomie aplikacji

Aby zainstalować aplikacje z zależnościami od różnych wersji programu .NET, zaleca się program .NET Core. .NET Core oferuje instalację obok siebie różnych wersji programu runtime .NET Core na tym samym komputerze. Ta instalacja side-by-side umożliwia wiele usług na tym samym serwerze, z których każda jest w własnej wersji programu .NET Core. Zmniejsza również ryzyko i oszczędza pieniądze na modernizacjach aplikacji i operacjach IT.

## <a name="when-to-choose-net-framework"></a>Kiedy wybrać .NET Framework

.NET Core oferuje znaczące korzyści dla nowych aplikacji i wzorców aplikacji. Jednak .NET Framework nadal jest naturalnym wyborem dla wielu istniejących scenariuszy i jako takie .NET Framework nie jest zastępowany przez .NET Core dla wszystkich aplikacji serwera.

### <a name="current-net-framework-applications"></a>Bieżące aplikacje programu .NET Framework

W większości przypadków nie trzeba migrować istniejących aplikacji do .NET Core. Zamiast tego zaleca się użycie .NET Core podczas rozszerzania istniejącej aplikacji, takiej jak pisanie nowej usługi sieci web w ASP.NET Core.

### <a name="a-need-to-use-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>Konieczność używania bibliotek .NET innych firm lub pakietów NuGet niedostępnych dla programu .NET Core

Biblioteki szybko ogarniają standard .NET. .NET Standard umożliwia udostępnianie kodu we wszystkich implementacjach .NET, w tym .NET Core. W przypadku .NET Standard 2.0 jest to jeszcze łatwiejsze:

- Powierzchnia Interfejsu API stała się znacznie większa.
- Wprowadzono tryb zgodności .NET Framework. Ten tryb zgodności umożliwia projektom .NET Standard/.NET Core odwoływanie się do bibliotek programu .NET Framework. Aby dowiedzieć się więcej o trybie zgodności, zobacz [Ogłaszanie .NET Standard 2.0](https://devblogs.microsoft.com/dotnet/announcing-net-standard-2-0/).

Tak więc tylko w przypadkach, gdy biblioteki lub pakiety NuGet używają technologii, które nie są dostępne w .NET Standard/.NET Core, należy użyć .NET Framework.

### <a name="a-need-to-use-net-technologies-not-available-for-net-core"></a>Konieczność używania technologii .NET niejest dostępna dla programu .NET Core

Niektóre technologie programu .NET Framework nie są dostępne w platformie .NET Core. Niektóre z nich mogą być dostępne w nowszych wersjach programu .NET Core. Inne nie mają zastosowania do nowych wzorców aplikacji przeznaczonych dla .NET Core i mogą nigdy nie być dostępne. Na poniższej liście przedstawiono najpopularniejsze technologie, które nie występują w .NET Core:

- ASP.NET aplikacji formularzy sieci Web: ASP.NET formularze sieci Web są dostępne tylko w platformie .NET Framework. ASP.NET Core nie może być używany w ASP.NET formularzach sieci Web. Nie ma żadnych planów wprowadzenia ASP.NET formularzy sieci Web do programu .NET Core.

- ASP.NET aplikacje stron sieci Web: ASP.NET strony sieci Web nie są uwzględniane w ASP.NET Core.

- Implementacja usług WCF. Nawet wtedy, gdy istnieje [biblioteka Klienta WCF](https://github.com/dotnet/wcf) do używania usług WCF z .NET Core, implementacja serwera WCF jest obecnie dostępna tylko w .NET Framework. Ten scenariusz nie jest częścią bieżącego planu dla .NET Core, ale jest rozważany w przyszłości.

- Usługi związane z przepływem pracy: Windows Workflow Foundation (WF), Workflow Services (WCF + WF w jednej usłudze) i WCF Data Services (wcześniej znane jako "ADO.NET Data Services") są dostępne tylko w programie .NET Framework.  Nie ma żadnych planów, aby przynieść WF/WCF + WF/WCF Data Services do .NET Core.

- Obsługa języka: Visual Basic i F# są obecnie obsługiwane w programie .NET Core, ale nie dla wszystkich typów projektów. Aby uzyskać listę obsługiwanych szablonów projektów, zobacz [Opcje szablonów dla dotnet new](../core/tools/dotnet-new.md#arguments).

Oprócz oficjalnego planu działania istnieją inne struktury, które mają być przeniesione do .NET Core. Aby uzyskać pełną listę, zobacz [port-to-core](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core)problemy Zus. Ta lista nie reprezentuje zobowiązania firmy Microsoft do wprowadzenia tych składników do .NET Core. Po prostu uchwycą pragnienie społeczności, aby to zrobić. Jeśli zależy Ci na którymkolwiek `port-to-core`ze składników oznaczonych jako , weź udział w dyskusjach na GitHubie. A jeśli uważasz, że czegoś brakuje, zgłoś nowy problem w [repozytorium .NET](https://github.com/dotnet/runtime/issues/new).

### <a name="a-need-to-use-a-platform-that-doesnt-support-net-core"></a>Konieczność korzystania z platformy, która nie obsługuje .NET Core

Niektóre platformy firmy Microsoft lub innych firm nie obsługują programu .NET Core. Niektóre usługi platformy Azure zapewniają zestaw SDK, który nie jest jeszcze dostępny do użycia w platformie .NET Core. Jest to okoliczność przejściowa, ponieważ wszystkie usługi platformy Azure używają .NET Core. W międzyczasie zawsze można użyć równoważnego interfejsu API REST zamiast sdk klienta.

## <a name="see-also"></a>Zobacz też

- [Wybierz między ASP.NET a ASP.NET Core](/aspnet/core/choose-aspnet-framework)
- [Platforma ASP.NET Core ukierunkowana na platformę .NET Framework](/aspnet/core#aspnet-core-targeting-net-framework)
- [Platformy docelowe](frameworks.md)
- [Przewodnik po rdzeniu .NET](../core/index.md)
- [Przenoszenie z platformy .NET Framework do platformy .NET Core](../core/porting/index.md)
- [Wprowadzenie do platform .NET i Docker](../core/docker/introduction.md)
- [Omówienie składników .NET](components.md)
- [Mikrousług .NET. Architektura konteneryzowanych aplikacji .NET](../architecture/microservices/index.md)
