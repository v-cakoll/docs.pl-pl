---
title: Omówienie platformy .NET Core
description: Zapoznaj się z charakterystyką i kompozycją platformy .NET Core i porównaj ją z innymi implementacjami platformy .NET.
ms.date: 03/26/2020
ms.openlocfilehash: e57451968ed8c4d5457acea084d3c6c9f998b8da
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144529"
---
# <a name="net-core-overview"></a>Omówienie platformy .NET Core

Platforma .NET Core ma następujące cechy:

- **Wiele platform:** Działa w [systemach operacyjnych](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md)Windows, MacOS i Linux.
- **Open Source:** .NET Core Framework to [Open Source](https://github.com/dotnet/core), przy użyciu licencji MIT i Apache 2. .NET Core to projekt [platformy .NET Foundation](https://dotnetfoundation.org/) .
- **Nowoczesny:** Implementuje nowoczesne odmiany, takie jak programowanie asynchroniczne, wzorce bez kopiowania przy użyciu struktur i zarządzania zasobami dla kontenerów.
- **Wydajność:**  Zapewnia [wysoką wydajność](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-core-3-0/) dzięki funkcjom, takim jak [wewnętrzne sprzętowe](https://devblogs.microsoft.com/dotnet/hardware-intrinsics-in-net-core/), [kompilacja warstwowa](https://github.com/dotnet/coreclr/blob/master/Documentation/design-docs/tiered-compilation.md)i [zakres \<T> ](../standard/memory-and-spans/index.md).
- **Spójne w różnych środowiskach:** Uruchamia kod z zachowaniem tego samego zachowania w wielu systemach operacyjnych i architekturach, w tym x64, x86 i ARM.
- **Narzędzia wiersza polecenia:**  Obejmuje łatwe w użyciu narzędzia wiersza polecenia, które mogą być używane do lokalnego tworzenia i ciągłej integracji.
- **Elastyczne wdrożenie:** Możesz dołączyć platformę .NET Core do swojej aplikacji lub zainstalować ją obok siebie (instalacje dla całego użytkownika lub systemu). Może być używany z [kontenerami platformy Docker](docker/introduction.md).

## <a name="languages"></a>Języki

Języka [C#](../csharp/index.yml), [Visual Basic](../visual-basic/index.yml)i [języka F #](../fsharp/index.yml) można używać do pisania aplikacji i bibliotek dla platformy .NET Core. Te języki mogą być używane w ulubionym edytorze tekstu lub zintegrowanego środowiska programistycznego (IDE), w tym:

- [Program Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)
- [Visual Studio Code](https://code.visualstudio.com/download)

Integracja z edytorem jest zapewniana w części przez współautorów projektów [OmniSharp](https://www.omnisharp.net/) i [Ionide](https://ionide.io) .

## <a name="apis"></a>Interfejsy API

Platforma .NET Core udostępnia platformy do tworzenia aplikacji dowolnego rodzaju:

* Aplikacje w chmurze z [ASP.NET Core](/aspnet/core/)
* Aplikacje mobilne przy użyciu platformy [Xamarin](/xamarin)
* Aplikacje IoT z [System. Device. GPIO](https://docs.microsoft.com/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0)
* Aplikacje klienckie systemu Windows z [WPF](../desktop-wpf/overview/index.md) i Windows Forms
* [Ml.NET](../machine-learning/index.yml) uczenia maszynowego

Dołączono wiele interfejsów API, które spełniają typowe potrzeby:

- Typy pierwotne, takie jak <xref:System.Boolean?displayProperty=nameWithType> i <xref:System.Int32?displayProperty=nameWithType> .
- Kolekcje, takie jak <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> i <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> .
- Typy narzędzi, takie jak <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> , i <xref:System.IO.FileStream?displayProperty=nameWithType> .
- Typy danych, takie jak <xref:System.Data.DataSet?displayProperty=nameWithType> , i <xref:System.Data.Entity.DbSet?displayProperty=nameWithType> .
- Typy wysokiej wydajności, takie jak <xref:System.Span%601?displayProperty=nameWithType> , <xref:System.Numerics.Vector?displayProperty=nameWithType> i [potoki](../standard/io/pipelines.md).

Platforma .NET Core zapewnia zgodność z interfejsami API .NET Framework i mono, implementując specyfikację [.NET Standard](../standard/net-standard.md) .

## <a name="composition"></a>Kompozycja

Platforma .NET Core składa się z następujących części:

- [Środowisko uruchomieniowe platformy .NET Core](https://github.com/dotnet/runtime/tree/master/src/coreclr), które udostępnia system typów, ładowanie zestawu, Moduł wyrzucania elementów bezużytecznych, natywną międzyoperacyjność i inne podstawowe usługi. [Biblioteki .NET Core Framework](https://github.com/dotnet/runtime/tree/master/src/libraries) zapewniają typy danych pierwotnych, typy kompozycji aplikacji i podstawowe narzędzia.
- [Środowisko uruchomieniowe ASP.NET Core](https://github.com/dotnet/aspnetcore), które zapewnia platformę do tworzenia nowoczesnych, opartych na chmurze aplikacji internetowych, takich jak aplikacje internetowe, aplikacje IoT i frontony mobilne.
- [Zestaw .NET Core SDK](https://github.com/dotnet/sdk) i kompilatory języka ([Roslyn](https://github.com/dotnet/roslyn) i [F #](https://github.com/microsoft/visualfsharp)), które umożliwiają środowisko deweloperskie platformy .NET Core.
- [Polecenie dotnet](./tools/dotnet.md), które służy do uruchamiania aplikacji .NET Core i poleceń interfejsu wiersza polecenia. Wybiera i obsługuje środowisko uruchomieniowe, udostępnia zasady ładowania zestawu oraz uruchamia aplikacje i narzędzia.

### <a name="open-source"></a>Kod open source

[.NET Core](about.md) to platforma programistyczna [Open Source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT). Można tworzyć aplikacje .NET Core dla systemów Windows, macOS i Linux dla procesorów x64, x86, ARM32 i ARM64. Platformy i interfejsy API są udostępniane dla [chmur](/aspnet/core/), [IoT](https://docs.microsoft.com/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0), [interfejsu użytkownika klienta](../desktop-wpf/overview/index.md)i [uczenia maszynowego](../machine-learning/index.yml).

## <a name="support"></a>Pomoc techniczna

Platforma .NET Core jest [obsługiwana przez firmę Microsoft](https://dotnet.microsoft.com/platform/support/policy) w systemach Windows, MacOS i Linux. Jest ona regularnie aktualizowana pod kątem bezpieczeństwa i jakości (drugi wtorek każdego miesiąca).

Dystrybucje binarnych programu .NET Core od firmy Microsoft są kompilowane i testowane na serwerach obsługiwanych przez firmę Microsoft na platformie Azure i są zgodne z praktyką inżynieryjną firmy Microsoft.

[Red Hat obsługuje platformę .NET Core](https://developers.redhat.com/topics/dotnet/) na Red Hat Enterprise Linux (RHEL). Red Hat kompiluje platformę .NET Core ze źródła i udostępnia je w [kolekcjach oprogramowania Red Hat](https://developers.redhat.com/products/softwarecollections/overview/). Red Hat i Microsoft Współpracuj, aby upewnić się, że .NET Core działa dobrze na RHEL.

[Tizen obsługuje platformę .NET Core](https://developer.tizen.org/development/training/.net-application) na platformach Tizen.
