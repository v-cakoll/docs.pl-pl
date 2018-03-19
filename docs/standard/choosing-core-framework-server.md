---
title: "Wybór między .NET Core i .NET Framework dla serwera aplikacji"
description: "Przewodnik w życie .NET należy rozważyć podczas kompilowania aplikacji serwera, programu .NET."
author: cartermp
ms.author: mairaw
ms.date: 03/15/2018
ms.topic: article
ms.prod: .net
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c07b0b760e2a46faea574eef3575409bac773942
ms.sourcegitcommit: 15316053918995cc1380163a7d7e7edd5c44e6d7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="choosing-between-net-core-and-net-framework-for-server-apps"></a>Wybór między .NET Core i .NET Framework dla serwera aplikacji

Istnieją dwa implementacje obsługiwanych do tworzenia aplikacji serwerowych z platformą .NET: .NET Framework i .NET Core. Zarówno mają te same składniki i kodu mogą udostępniać między nimi. Jednak podstawowych różnic między nimi i wybór zależy od tego, co chcesz zrobić.  Ten artykuł zawiera wskazówki dotyczące każdego użycie.

Użyj .NET Core dla aplikacji serwera po:

* Możesz korzystać z wielu platform.
* Przeznaczonych mikrousług.
* Używasz kontenery Docker.
* Należy systemów wysokiej wydajności i skalowalności.
* Należy side-by-side wersje programu .NET dla aplikacji.

Używanie środowiska .NET Framework dla aplikacji serwera po:

* Aplikacja używa obecnie .NET Framework (zalecenie jest rozszerzenie zamiast migracji).
* Twoja aplikacja korzysta z bibliotek .NET innych firm lub pakietów NuGet nie jest dostępna dla platformy .NET Core.
* Twoja aplikacja korzysta z technologii .NET, które nie są dostępne dla platformy .NET Core.
* Twoja aplikacja korzysta z platformy, która nie obsługuje platformy .NET Core.

## <a name="when-to-choose-net-core"></a>Kiedy należy wybrać oprogramowanie .NET Core

W poniższych sekcjach znajdują się bardziej szczegółowy opis wcześniej podane powody pobrania .NET Core.

### <a name="cross-platform-needs"></a>Należy między platformami

Jeśli wymagań aplikacji (usługa sieci web) / do uruchamiania na wielu platform (Windows, Linux lub macOS), za pomocą platformy .NET Core.

Oprogramowanie .NET core obsługuje systemów operacyjnych wymienionych jako deweloperskiej stacji roboczej. Program Visual Studio udostępnia zintegrowane środowisko rozwoju (IDE) dla systemu Windows i macOS. Można również użyć Visual Studio Code, która działa na macOS, Linux i Windows. Visual Studio Code obsługuje .NET Core, w tym IntelliSense i debugowania. Większość edytorów innych firm, takich jak Sublime, Emacs i VI, pracy z platformą .NET Core. IntelliSense Edytor uzyskać te edytory innych firm przy użyciu [Omnisharp](http://www.omnisharp.net/). Można także uniknąć dowolnego edytora kodu i używać bezpośrednio [narzędzi interfejsu wiersza polecenia platformy .NET Core](../core/tools/index.md), dostępne dla wszystkich obsługiwanych platformach.

### <a name="microservices-architecture"></a>Architektura Mikrousług

Architektura mikrousług umożliwia różnych technologii granicy usługi. Tej technologii umożliwia stopniowe objęło programu .NET Core dla nowych mikrousług, który współpracować z innymi mikrousług lub usługi. Na przykład można mieszać mikrousług lub przygotowane w programie .NET Framework, Java, Ruby i inne technologie wbudowanymi usług.

Brak dostępnych wiele platform infrastruktury. [Sieć szkieletowa usług Azure](https://azure.microsoft.com/services/service-fabric/) mikrousługi dużych i złożonych systemów. [Usługa aplikacji Azure](https://azure.microsoft.com/services/app-service/) jest dobrym rozwiązaniem w przypadku bezstanowych mikrousług. Alternatywy Mikrousług oparte na Docker dopasowania dowolnego rodzaju mikrousług podejście, zgodnie z objaśnieniem w [kontenery](#containers) sekcji. Tych platform obsługują .NET Core i były nadaje się doskonale dla hostingu sieci mikrousług.

Aby uzyskać więcej informacji o architekturze mikrousług, zobacz [Mikrousług .NET. Architektura aplikacji .NET konteneryzowanych](microservices-architecture/index.md).

### <a name="containers"></a>Kontenery

Kontenery są często używane w połączeniu z architekturą mikrousług. Kontenery można również containerize aplikacji sieci web lub usługi, które należy wykonać wszelkie wzorzec architektury. .NET framework może służyć do kontenerów systemu Windows, ale modułowości i lekkie rodzaj .NET Core umożliwia lepszym rozwiązaniem dla kontenerów. Podczas tworzenia i wdrażania kontener, rozmiar obrazu jego jest znacznie mniejszy z platformą .NET Core niż platformy .NET Framework. Ponieważ między platformami, można wdrożyć aplikacji serwera do kontenerów Linux Docker, na przykład.

Kontenery docker mogą być hostowane w ramach własnej infrastruktury systemu Linux lub Windows lub w usłudze w chmurze takich jak [usługi kontenera platformy Azure](https://azure.microsoft.com/services/container-service/). Usługa kontenera platformy Azure można zarządzać, organizować i skalowanie aplikacji kontenera w chmurze.

### <a name="a-need-for-high-performance-and-scalable-systems"></a>Potrzebę systemów wysokiej wydajności i skalowalności

Gdy system potrzebuje najlepszą wydajność i skalowalność, oprogramowanie .NET Core i ASP.NET Core są najlepsze opcje. Środowisko uruchomieniowe serwera wysokiej wydajności dla systemu Windows Server i Linux .NET sprawia, że wykonywanie top web framework na [testów porównawczych TechEmpower](https://www.techempower.com/benchmarks/#hw=ph&test=plaintext).

Wydajność i skalowalność są szczególnie istotne dla architektur mikrousług, gdzie mogą być uruchomione setki mikrousług. Za pomocą platformy ASP.NET Core systemów uruchomić ze znacznie mniejszą liczbę maszyny wirtualne/serwery (VM). Zmniejszenie serwerów/VMs zapisywania koszty infrastruktury i hosting.

### <a name="a-need-for-side-by-side-of-net-versions-per-application-level"></a>Potrzeba równolegle z wersji platformy .NET na poziomie aplikacji

Aby zainstalować aplikacje z zależnościami w różnych wersjach programu .NET, firma Microsoft zaleca .NET Core. Oprogramowanie .NET core oferuje side-by-side instalacji różnych wersji środowiska uruchomieniowego .NET Core na tym samym komputerze. Ta instalacja side-by-side umożliwia wielu usług na tym samym serwerze, każde z nich na własną wersję platformy .NET Core. Ponadto zmniejsza ryzyko i zapisuje oszczędność pieniędzy w operacje IT i uaktualnień aplikacji.

## <a name="when-to-choose-net-framework"></a>Kiedy należy wybrać .NET Framework

Oprogramowanie .NET core oferuje istotne korzyści dla nowych aplikacji i wzorce aplikacji. Jednak programu .NET Framework jest nadal wybór fizycznych w różnych scenariuszach istniejących i jako taki. .NET Framework nie jest zastępowany przez oprogramowanie .NET Core dla wszystkich aplikacji serwera.

### <a name="current-net-framework-applications"></a>Bieżące aplikacje .NET Framework

W większości przypadków nie trzeba przeprowadzać migracji istniejącej aplikacji .NET Core. Zalecanym podejściem jest użyć .NET Core, jak rozszerzyć istniejącą aplikację, takie jak zapisywanie nową usługę sieci web w ASP.NET Core.

### <a name="a-need-to-use-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>Trzeba użyć bibliotek .NET innych firm lub pakietów NuGet nie jest dostępna dla platformy .NET Core

Biblioteki są szybko obejmującego .NET Standard. .NET standard umożliwia udostępnianie kodu we wszystkich implementacjach .NET, w tym oprogramowanie .NET Core. .NET 2.0 standardowa to ustawienie jest łatwiejsze:

- Powierzchnię interfejsu API stał się znacznie większe. 
- Wprowadzono trybu zgodności .NET Framework. Ten tryb zgodności umożliwia .NET Standard/.NET Core projekty do odwołania do bibliotek .NET Framework. Aby dowiedzieć się więcej na temat trybu zgodności, zobacz [Announcing .NET 2.0 standardowe](https://blogs.msdn.microsoft.com/dotnet/2017/08/14/announcing-net-standard-2-0/).

Tylko w przypadkach, gdy bibliotek i pakietów NuGet używać technologii, które nie są dostępne w .NET Standard/.NET Core musisz użyć programu .NET Framework.

### <a name="a-need-to-use-net-technologies-not-available-for-net-core"></a>Trzeba używać technologii .NET nie jest dostępna dla platformy .NET Core

Niektóre technologie .NET Framework nie są dostępne w .NET Core. Niektóre z nich mogą być dostępne w nowszej wersji platformy .NET Core. Inne osoby nie można stosować do nowych wzorców aplikacji objęci .NET Core i nigdy nie mogą być dostępne. Poniższa lista przedstawia najbardziej typowe technologie, nie można odnaleźć w .NET Core:

* Aplikacji formularzy sieci Web programu ASP.NET: formularzy sieci Web ASP.NET są dostępne tylko w programie .NET Framework. Nie można używać platformy ASP.NET Core dla formularzy sieci Web ASP.NET. Nie ma żadnych planów, aby wyświetlić formularzy sieci Web ASP.NET w celu .NET Core.

* Aplikacji stron sieci Web programu ASP.NET: stron sieci Web programu ASP.NET nie zostaną uwzględnione w ASP.NET Core. Platformy ASP.NET Core [stron Razor](/aspnet/core/mvc/razor-pages/) ma wiele podobieństw ze stronami sieci Web.

* Implementacja serwera i klienta ASP.NET SignalR. Obecnie [ASP.NET SignalR](https://github.com/aspnet/SignalR) jest dostępna w wersji zapoznawczej przy użyciu platformy ASP.NET Core 2.1.

* Implementacja usługi WCF. Nawet wtedy, gdy istnieje [biblioteki klienta WCF](https://github.com/dotnet/wcf) do korzystania z usług WCF z platformy .NET Core, implementacją serwera WCF jest obecnie dostępna tylko w programie .NET Framework. W tym scenariuszu nie jest częścią bieżącego planu dla platformy .NET Core, ale jest rozważane w przyszłości.

* Usług związanych z przepływu pracy: Windows Workflow Foundation (WF), usługi przepływu pracy (WCF i WF w jednej usługi) i usługi danych WCF (wcześniej znane jako "Usług danych ADO.NET") są dostępne tylko w programie .NET Framework.  Nie ma żadnych planów, aby wyświetlić usługi danych WCF/WF z + WCF/WF w celu .NET Core.

* Windows Presentation Foundation (WPF) i formularze systemu Windows: aplikacje WPF i formularze systemu Windows są dostępne tylko w programie .NET Framework. Nie ma żadnych planów do portu je do platformy .NET Core.

* Obsługa języków: Visual Basic i F # są obecnie obsługiwane w .NET Core, ale nie dla wszystkich typów projektów. Lista szablonów obsługiwanych projektu, zobacz [opcje szablon dla nowych dotnet](../core/tools/dotnet-new.md#arguments).

Oprócz oficjalnego plan ma innych platform, które mogą być przenoszone do platformy .NET Core. Aby uzyskać pełną listę, zobacz problemy CoreFX oznaczona jako [portu core](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core). Ta lista nie zawiera zobowiązania firmy Microsoft, aby przenieść te składniki .NET Core. Są one po prostu przechwytywania zamiar to zrobić przez społeczność. Jeśli Cię interesuje któregokolwiek ze składników oznaczona jako `port-to-core`, brać udziału w dyskusjach w witrynie GitHub. I jeśli coś nie istnieje, nowy problem w pliku [repozytorium CoreFX](https://github.com/dotnet/corefx/issues/new).

### <a name="a-need-to-use-a-platform-that-doesnt-support-net-core"></a>Konieczność użycia platformy, która nie obsługuje platformy .NET Core

Niektóre firmy Microsoft lub innych firm platformy nie obsługuje platformy .NET Core. Na przykład niektóre Azure usług, takich jak usługi sieć szkieletowa stanowych usług Reliable Services i Reliable Actors sieć szkieletowa usług wymagają .NET Framework. Niektóre inne usługi zawierają zestaw SDK nie jest jeszcze dostępny do użycia przez oprogramowanie .NET Core. Jest to przejściowy okoliczności, użyj wszystkich usług Azure .NET Core. W międzyczasie zawsze można użyć równoważnych interfejsu API REST zamiast zestawu SDK klienta.

## <a name="see-also"></a>Zobacz także
 [Wybór między ASP.NET i ASP.NET Core](/aspnet/core/choose-aspnet-framework)  
 [Przewodnik platformy .NET Core](../core/index.md)  
 [Eksportowanie z .NET Framework do platformy .NET Core](../core/porting/index.md)  
 [.NET Framework na platformie Docker — przewodnik](../framework/docker/index.md)  
 [Omówienie składników platformy .NET](components.md)  
 [Mikrousług .NET. Architektura aplikacji .NET konteneryzowanych](microservices-architecture/index.md)
