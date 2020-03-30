---
title: Omówienie platformy .NET Core
description: Dowiedz się więcej o charakterystyce i składzie programu .NET Core i porównaj ją z innymi implementacjami platformy .NET.
ms.date: 03/26/2020
ms.openlocfilehash: c9a63ddba14cf176be529e9520027c0610cfc087
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391172"
---
# <a name="net-core-overview"></a>Omówienie platformy .NET Core

Program .NET Core ma następujące właściwości:

- **Platforma krzyżowa:** Działa w [systemach operacyjnych](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md)Windows, macOS i Linux .
- **Open source:** .NET Core framework jest [open source,](https://github.com/dotnet/core)przy użyciu licencji MIT i Apache 2. .NET Core to projekt [.NET Foundation.](https://dotnetfoundation.org/)
- **Nowoczesne:** Implementuje nowoczesne paradygmaty, takie jak programowanie asynchroniczne, wzorce bez kopiowania przy użyciu struktur i zarządzanie zasobami dla kontenerów.
- **Wydajność:**  Zapewnia [wysoką wydajność](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-core-3-0/) dzięki funkcjom, takim jak [wyrozumiałość sprzętu,](https://devblogs.microsoft.com/dotnet/hardware-intrinsics-in-net-core/) [kompilacja warstwowa](https://github.com/dotnet/coreclr/blob/master/Documentation/design-docs/tiered-compilation.md)i [Span\<T>. ](../standard/memory-and-spans/index.md)
- **Spójne w różnych środowiskach:** Uruchamia kod z takim samym zachowaniem na wielu systemach operacyjnych i architekturach, w tym x64, x86 i ARM.
- **Narzędzia wiersza polecenia:**  Zawiera łatwe w użyciu narzędzia wiersza polecenia, które mogą być używane do lokalnego rozwoju i ciągłej integracji.
- **Elastyczne wdrażanie:** Program .NET Core można dołączyć do aplikacji lub zainstalować obok siebie (instalacje dla całego użytkownika lub całego systemu). Może być używany z [kontenerami platformy Docker](docker/introduction.md).

## <a name="languages"></a>Języki

Języki [C#](../csharp/index.yml), [Visual Basic](../visual-basic/index.yml)i [F#](../fsharp/index.yml) mogą być używane do pisania aplikacji i bibliotek dla platformy .NET Core. Te języki mogą być używane w ulubionym edytorze tekstu lub zintegrowanym środowisku programistycznym (IDE), w tym:

- [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)
- [Kod programu Visual Studio](https://code.visualstudio.com/download)

Integracja edytora jest częściowo świadczona przez współautorów projektów [OmniSharp](https://www.omnisharp.net/) i [Ionide.](http://ionide.io)

## <a name="apis"></a>Interfejsy API

.NET Core udostępnia struktury do tworzenia dowolnego rodzaju aplikacji:

* Aplikacje w chmurze z [ASP.NET Core](/aspnet/core/)
* Aplikacje mobilne z [systemem Xamarin](/xamarin)
* Aplikacje IoT z [System.Device.GPIO](https://docs.microsoft.com/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0)
* Aplikacje klienckie systemu Windows z [wyw.](../desktop-wpf/overview/index.md)
* ML.NET uczenia [maszynowego](../machine-learning/index.yml)

Wiele interfejsów API są zawarte, które spełniają wspólne potrzeby:

- Typy pierwotne, <xref:System.Boolean?displayProperty=nameWithType> takie <xref:System.Int32?displayProperty=nameWithType>jak i .
- Kolekcje, takie <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>jak i .
- Typy narzędzi, <xref:System.Net.Http.HttpClient?displayProperty=nameWithType>takie <xref:System.IO.FileStream?displayProperty=nameWithType>jak , i .
- Typy danych, <xref:System.Data.DataSet?displayProperty=nameWithType>takie <xref:System.Data.Entity.DbSet?displayProperty=nameWithType>jak , i .
- Typy o wysokiej <xref:System.Span%601?displayProperty=nameWithType>wydajności, takie jak , <xref:System.Numerics.Vector?displayProperty=nameWithType>i [Potoki](../standard/io/pipelines.md).

Program .NET Core zapewnia zgodność z interfejsami API platformy .NET Framework i mono, implementując specyfikację [standardu .NET.](../standard/net-standard.md)

## <a name="composition"></a>Kompozycja

Program .NET Core składa się z następujących części:

- [Środowisko uruchomieniowe .NET Core](https://github.com/dotnet/runtime/tree/master/src/coreclr), który zapewnia system typów, ładowanie zestawu, moduł zbierający elementy bezużyteczne, natywne interop i inne podstawowe usługi. [Biblioteki .NET Core framework](https://github.com/dotnet/runtime/tree/master/src/libraries) zapewniają podstawowe typy danych, typy kompozycji aplikacji i podstawowe narzędzia.
- [Środowisko wykonawcze ASP.NET Core](https://github.com/dotnet/aspnetcore), które zapewnia platformę do tworzenia nowoczesnych, opartych na chmurze aplikacji połączonych z Internetem, takich jak aplikacje internetowe, aplikacje IoT i zaplecze mobilne.
- [Kompilatora zestawu .NET Core SDK](https://github.com/dotnet/sdk) i języka[(Roslyn](https://github.com/dotnet/roslyn) i [F#),](https://github.com/microsoft/visualfsharp)które umożliwiają środowisko deweloperskie .NET Core.
- [Polecenie dotnet](./tools/dotnet.md), które służy do uruchamiania aplikacji .NET Core i poleceń interfejsu wiersza polecenia. Wybiera i obsługuje środowisko uruchomieniowe, udostępnia zasady ładowania zestawu i uruchamia aplikacje i narzędzia.

### <a name="open-source"></a>Kod open source

[.NET Core](about.md) jest platformą programową [typu open source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)i ogólnego przeznaczenia. Aplikacje .NET Core można tworzyć dla systemów Windows, macOS i Linux dla procesorów x64, x86, ARM32 i ARM64. Struktury i interfejsy API są dostarczane dla [chmury,](/aspnet/core/) [IoT](https://docs.microsoft.com/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0), [interfejsu użytkownika klienta](../desktop-wpf/overview/index.md)i uczenia [maszynowego.](../machine-learning/index.yml)

## <a name="support"></a>Pomoc techniczna

Program .NET Core jest [obsługiwany przez firmę Microsoft](https://dotnet.microsoft.com/platform/support/policy) w systemach Windows, macOS i Linux. Jest regularnie aktualizowany pod kątem bezpieczeństwa i jakości (drugi wtorek każdego miesiąca).

Dystrybucje binarne .NET Core firmy Microsoft są tworzone i testowane na serwerach obsługiwanych przez firmę Microsoft na platformie Azure i stosują się do praktyk inżynieryjnych i zabezpieczeń firmy Microsoft.

[Red Hat obsługuje .NET Core](http://redhatloves.net/) na Red Hat Enterprise Linux (RHEL). Red Hat buduje .NET Core ze źródła i udostępnia go w [red hat software collections](https://developers.redhat.com/products/softwarecollections/overview/). Red Hat i Microsoft współpracują, aby zapewnić, że program .NET Core działa dobrze na RHEL.

[Tizen obsługuje platformy .NET Core](https://developer.tizen.org/development/training/.net-application) na platformach Tizen.
