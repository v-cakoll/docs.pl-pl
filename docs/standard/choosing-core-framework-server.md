---
title: Wybierz między programem.NET Core i .NET Framework dla aplikacji serwerowych
description: Przewodnik, na które implementacji .NET należy rozważyć podczas kompilowania aplikacji serwera na platformie .NET.
author: cartermp
ms.author: mairaw
ms.date: 06/19/2018
ms.openlocfilehash: 541bcdf69d658fd37271169c028fb64611a35655
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42934536"
---
# <a name="choosing-between-net-core-and-net-framework-for-server-apps"></a>Wybieranie między programami .NET Core i .NET Framework dla aplikacji serwerowych

Istnieją dwie obsługiwane implementacje do tworzenia aplikacji po stronie serwera za pomocą platformy .NET: .NET Framework i .NET Core. Mają wiele te same składniki i mogą współużytkować kod między nimi. Jednak istnieją fundamentalne różnice między nimi, a wybór zależy od tego, co chcesz osiągnąć.  Ten artykuł zawiera wskazówki dotyczące kiedy należy używać każdego.

Użyj platformy .NET Core dla aplikacji serwera po:

* Masz wymagania dla wielu platform.
* Przeznaczonych do mikrousług.
* Używasz kontenerów platformy Docker.
* Należy systemów o wysokiej wydajności i skalowalne.
* Należy side-by-side wersje programu .NET dla aplikacji.

Używać .NET Framework dla aplikacji serwera w przypadku:

* Aplikacja używa obecnie .NET Framework (zaleca się rozszerzyć zamiast migracji).
* Aplikacja używa biblioteki .NET innych firm lub pakiety NuGet nie są dostępne dla platformy .NET Core.
* Twoja aplikacja korzysta z technologii .NET, które nie są dostępne dla platformy .NET Core.
* Twoja aplikacja korzysta z platformy, która nie obsługuje platformy .NET Core.

## <a name="when-to-choose-net-core"></a>Kiedy należy wybrać oprogramowanie .NET Core

W poniższych sekcjach znajdują się bardziej szczegółowy opis wcześniej podane przyczyny pobrania platformy .NET Core.

### <a name="cross-platform-needs"></a>Wymagania dla wielu platform

Jeśli wymagania w zakresie aplikacji (usługa sieci web) / do uruchamiania na wielu platformach (Windows, Linux i macOS) wykorzystania platformy .NET Core.

.NET core obsługuje systemów operacyjnych wymienionych jako deweloperskiej stacji roboczej. Program Visual Studio udostępnia zintegrowane środowisko programowania (IDE) dla Windows i macOS. Można również użyć programu Visual Studio Code, który jest uruchamiany w systemach macOS, Linux i Windows. Visual Studio Code obsługuje platformę .NET Core, w tym funkcji IntelliSense i debugowania. Większość edytorów innych firm, takich jak Sublime Emacs i VI, pracy z platformą .NET Core. Tych innych edytorów uzyskać funkcji IntelliSense w edytorze za pomocą [technologię Omnisharp](https://www.omnisharp.net/). Można także uniknąć dowolnego edytora kodu i bezpośrednio przy użyciu [narzędzi interfejsu wiersza polecenia platformy .NET Core](../core/tools/index.md), która jest dostępna dla wszystkich obsługiwanych platform.

### <a name="microservices-architecture"></a>Architektura Mikrousług

Architektura mikrousług umożliwia mieszanina technologii granicę usługi. Proporcje tej mieszanki technologii umożliwia stopniowe poszukująca programu .NET Core dla nowych mikrousług, współpracy z innymi mikrousług lub usługami. Na przykład można łączyć mikrousług lub usług, przygotowane w programie .NET Framework, Java, Ruby lub inne technologie monolitycznego.

Brak dostępnych wielu różnych platformach infrastruktury. [Usługa Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/) mikrousług dużych i złożonych systemów. [Usługa Azure App Service](https://azure.microsoft.com/services/app-service/) jest dobrym wyborem dla mikrousługi bezstanowe. Alternatywy Mikrousług platformy Docker w oparciu Dopasuj dowolny rodzaj podejście mikrousług, zgodnie z objaśnieniem w [kontenery](#containers) sekcji. Te platformy .NET Core obsługuje i były idealne do hostowania mikrousługi.

Aby uzyskać więcej informacji na temat architektury mikrousług, zobacz [Mikrousługi .NET. Architektura konteneryzowanych aplikacji .NET](microservices-architecture/index.md).

### <a name="containers"></a>Kontenery

Kontenery są często używane w połączeniu z architektury mikrousług. Kontenery mogą również konteneryzowanie aplikacji sieci web lub usługi, które należy wykonać wszelkie wzorzec architektury. .NET framework może być używany na kontenery Windows, ale modułowości i uproszczone charakter platformy .NET Core sprawia, że lepszym rozwiązaniem dla kontenerów. Podczas tworzenia i wdrażania kontenera, rozmiar jego obrazu jest znacznie mniejszy z platformą .NET Core niż za pomocą .NET Framework. Ponieważ jest dla wielu platform, można wdrożyć aplikacji serwerowych kontenerów platformy Docker w systemie Linux, na przykład.

Kontenery platformy docker może być hostowana w własnej infrastruktury systemu Linux lub Windows lub w usłudze w chmurze takich jak [usługi Azure Container Service](https://azure.microsoft.com/services/container-service/). Usługa Azure Container Service można zarządzać, organizowania i skalowania opartych na kontenerach aplikacji w chmurze.

### <a name="a-need-for-high-performance-and-scalable-systems"></a>Na potrzeby systemów o wysokiej wydajności i skalowalna

Gdy system potrzebuje maksymalną wydajność i skalowalność, .NET Core i ASP.NET Core są najlepsze opcje. Środowisko uruchomieniowe serwera o wysokiej wydajności dla systemu Windows Server i Linux programu .NET sprawia, że najważniejsze wykonywania platforma internetowa na [testy porównawcze TechEmpower](https://www.techempower.com/benchmarks/#hw=ph&test=plaintext).

Wydajność i skalowalność są szczególnie istotne dla architektury mikrousług, gdzie mogą być uruchomione setki mikrousług. Uruchamianie systemów platformy ASP.NET Core za pomocą znacznie mniejszej liczby serwerów/maszyny wirtualne (VM). Zmniejszenie serwerów/maszyn wirtualnych obniżenia kosztów infrastruktury i hostingu.

### <a name="a-need-for-side-by-side-of-net-versions-per-application-level"></a>Na potrzeby obok siebie wersji platformy .NET na poziomie aplikacji

Aby zainstalować aplikacje z zależnościami w różnych wersjach programu .NET, firma Microsoft zaleca platformy .NET Core. .NET core oferuje side-by-side instalacji różnych wersji środowiska uruchomieniowego .NET Core na tym samym komputerze. Ta instalacja side-by-side umożliwia wiele usług na tym samym serwerze, każde z nich na własną wersję platformy .NET Core. Ponadto zmniejsza ryzyko i pozwala oszczędzać pieniądze w uaktualnień aplikacji i działu operacji IT.

## <a name="when-to-choose-net-framework"></a>Kiedy należy wybrać oprogramowanie .NET Framework

.NET core oferuje znaczące korzyści w przypadku nowych aplikacji i wzorców do zastosowań. Jednak .NET Framework w dalszym ciągu jest naturalnym wyborem dla wielu istniejących scenariuszy i jako takie programu .NET Framework nie jest zastępowany przez platformy .NET Core dla wszystkich aplikacji serwera.

### <a name="current-net-framework-applications"></a>Bieżące aplikacje .NET Framework

W większości przypadków nie trzeba migrować istniejące aplikacje .NET Core. Zalecanym podejściem jest używać platformy .NET Core, jak rozszerzyć istniejącą aplikację, takie jak zapisywanie nowej usługi sieci web w programie ASP.NET Core.

### <a name="a-need-to-use-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>Trzeba użyć bibliotek .NET innych firm lub pakiety NuGet nie są dostępne dla platformy .NET Core

Biblioteki szybko używają .NET Standard. .NET standard umożliwia udostępnianie kodu między wszystkie implementacje platformy .NET, w tym .NET Core. .NET Standard 2.0 to ustawienie jest jeszcze łatwiejsze:

- Powierzchni interfejsu API stał się znacznie większe. 
- Wprowadza tryb zgodności .NET Framework. Ten tryb zgodności umożliwia projektów .NET Standard/.NET Core do odwołania do bibliotek .NET Framework. Aby dowiedzieć się więcej na temat trybu zgodności, zobacz [ogłoszenie .NET Standard 2.0](https://blogs.msdn.microsoft.com/dotnet/2017/08/14/announcing-net-standard-2-0/).

Tylko w przypadkach, gdy biblioteki lub pakiety NuGet użyć technologii, które nie są dostępne w programie .NET Standard/.NET Core musisz używać programu .NET Framework.

### <a name="a-need-to-use-net-technologies-not-available-for-net-core"></a>Konieczność stosowania technologii .NET, które nie są dostępne dla platformy .NET Core

Niektóre technologie .NET Framework nie są dostępne w programie .NET Core. Niektóre z nich mogą być dostępne w nowszych wersjach platformy .NET Core. Inne osoby nie mają zastosowania do nowych wzorców aplikacji docelowej platformy .NET Core i nigdy nie mogą być dostępne. Na poniższej liście przedstawiono najbardziej typowe technologie, nie można odnaleźć w programie .NET Core:

* Aplikacje formularzy sieci Web ASP.NET: ASP.NET Web Forms są dostępne tylko w programie .NET Framework. Nie można używać platformy ASP.NET Core dla formularzy sieci Web ASP.NET. Nie ma żadnych planów, aby wyświetlić formularzy sieci Web ASP.NET i .NET Core.

* Aplikacje programu ASP.NET Web Pages: strony sieci Web ASP.NET nie zostaną uwzględnione w programie ASP.NET Core. Platforma ASP.NET Core [stron Razor](/aspnet/core/mvc/razor-pages/) mają wiele wspólnego ze stronami sieci Web.

* Implementacja usługi WCF. Nawet w przypadku [biblioteki klienta platformy WCF](https://github.com/dotnet/wcf) korzystanie z usługi WCF z platformy .NET Core, implementacja serwera WCF jest obecnie dostępny tylko w programie .NET Framework. W tym scenariuszu nie jest częścią bieżącego planu dla platformy .NET Core, ale jest rozważane w przyszłości.

* Usługi związane z przepływu pracy: Windows Workflow Foundation (WF), usługi przepływu pracy (WCF + WF w jednej usłudze) i usługi danych WCF (wcześniej znane jako "Architektury ADO.NET Data Services") są dostępne tylko w programie .NET Framework.  Nie ma żadnych planów, aby wyświetlić usług danych WCF + WF/WF/WCF i .NET Core.

* Obsługa języków: Visual Basic i F # są obecnie obsługiwane w .NET Core, ale nie dla wszystkich typów projektów. Aby uzyskać listę szablonów obsługiwanych projektów, zobacz [opcje szablonu dla platformy dotnet nowe](../core/tools/dotnet-new.md#arguments).

Oprócz oficjalne plan istnieją inne struktury mogą być przenoszone do platformy .NET Core. Aby uzyskać pełną listę, zobacz problemy CoreFX oznaczone jako [portu core](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core). Ta lista nie stanowią zobowiązania firmy Microsoft na wprowadzanie tych składników na platformy .NET Core. Są one po prostu przechwytywania wymaganą przez społeczność, aby to zrobić. Jeśli interesujące Cię któregokolwiek ze składników, oznaczone jako `port-to-core`, udział w dyskusjach w witrynie GitHub. A jeśli Twoim zdaniem czegoś brakuje, zgłoś nowy problem w [repozytorium CoreFX](https://github.com/dotnet/corefx/issues/new).

### <a name="a-need-to-use-a-platform-that-doesnt-support-net-core"></a>Konieczność użycia platformy, która nie obsługuje platformy .NET Core

Niektóre firmy Microsoft lub innych platform nie obsługują platformy .NET Core. Na przykład usługi niektóre platformy Azure, takich jak Usługa Service Fabric stanowych usług Reliable Services i elementów Reliable Actors usługi Service Fabric wymaga środowiska .NET Framework. Niektóre inne usługi zapewniają zestaw SDK nie jest jeszcze dostępna do użytku na platformie .NET Core. Jest to przejściowy okoliczności, wszystkich usług platformy Azure wykorzystania platformy .NET Core. W międzyczasie zawsze można użyć równoważnego API REST zamiast zestawu SDK klienta.

## <a name="see-also"></a>Zobacz także

 [Wybieranie między ASP.NET i ASP.NET Core](/aspnet/core/choose-aspnet-framework) [ustalać platformy docelowe](frameworks.md) [przewodnik platformy .NET Core](../core/index.md)  
 [Przenoszenie z .NET Framework i .NET Core](../core/porting/index.md)  
 [.NET Framework na platformie Docker — przewodnik](../framework/docker/index.md)  
 [Omówienie składników platformy .NET](components.md)  
 [Mikrousługi .NET. Architektura konteneryzowanych aplikacji .NET](microservices-architecture/index.md)
