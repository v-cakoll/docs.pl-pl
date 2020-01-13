---
title: Serializacja i deserializacja JSON C# przy użyciu-.NET
ms.date: 01/10/2020
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: c05783963ba521109fb542f247ec9e62fdb5c2d9
ms.sourcegitcommit: dfad244ba549702b649bfef3bb057e33f24a8fb2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2020
ms.locfileid: "75904643"
---
# <a name="json-serialization-and-deserialization-marshalling-and-unmarshalling-in-net---overview"></a><span data-ttu-id="f7ddd-102">Serializacja i deserializacja kodu JSON (kierowanie i cofanie) w programie .NET — Omówienie</span><span class="sxs-lookup"><span data-stu-id="f7ddd-102">JSON serialization and deserialization (marshalling and unmarshalling) in .NET - overview</span></span>

<span data-ttu-id="f7ddd-103">Przestrzeń nazw `System.Text.Json` zawiera funkcje serializowania do i deserializacji z JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="f7ddd-103">The `System.Text.Json` namespace provides functionality for serializing to and deserializing from JavaScript Object Notation (JSON).</span></span>

<span data-ttu-id="f7ddd-104">Projekt biblioteki wyróżnia wysoką wydajność i małą alokację pamięci w ramach rozbudowanego zestawu funkcji.</span><span class="sxs-lookup"><span data-stu-id="f7ddd-104">The library design emphasizes high performance and low memory allocation over an extensive feature set.</span></span> <span data-ttu-id="f7ddd-105">Wbudowana obsługa UTF-8 optymalizuje proces odczytywania i pisania tekstu JSON zakodowanego w formacie UTF-8, który jest najbardziej rozpowszechnionym kodowaniem danych w sieci Web i plikach na dysku.</span><span class="sxs-lookup"><span data-stu-id="f7ddd-105">Built-in UTF-8 support optimizes the process of reading and writing JSON text encoded as UTF-8, which is the most prevalent encoding for data on the web and files on disk.</span></span>

<span data-ttu-id="f7ddd-106">Biblioteka zawiera również klasy umożliwiające pracę z modelem DOM (Document objecting) w pamięci.</span><span class="sxs-lookup"><span data-stu-id="f7ddd-106">The library also provides classes for working with an in-memory document object model (DOM).</span></span> <span data-ttu-id="f7ddd-107">Ta funkcja włącza losowy dostęp tylko do odczytu do elementów w pliku JSON lub ciągu.</span><span class="sxs-lookup"><span data-stu-id="f7ddd-107">This feature enables random read-only access of the elements in a JSON file or string.</span></span> 

## <a name="how-to-get-the-library"></a><span data-ttu-id="f7ddd-108">Jak uzyskać bibliotekę</span><span class="sxs-lookup"><span data-stu-id="f7ddd-108">How to get the library</span></span>

* <span data-ttu-id="f7ddd-109">Biblioteka jest wbudowana w ramach platformy udostępnionej [.NET Core 3,0](https://aka.ms/netcore3download) .</span><span class="sxs-lookup"><span data-stu-id="f7ddd-109">The library is built-in as part of the [.NET Core 3.0](https://aka.ms/netcore3download) shared framework.</span></span>
* <span data-ttu-id="f7ddd-110">W przypadku innych platform docelowych Zainstaluj pakiet NuGet [System. Text. JSON](https://www.nuget.org/packages/System.Text.Json) .</span><span class="sxs-lookup"><span data-stu-id="f7ddd-110">For other target frameworks, install the [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet package.</span></span> <span data-ttu-id="f7ddd-111">Pakiet obsługuje:</span><span class="sxs-lookup"><span data-stu-id="f7ddd-111">The package supports:</span></span>
  * <span data-ttu-id="f7ddd-112">.NET Standard 2,0 i nowsze wersje</span><span class="sxs-lookup"><span data-stu-id="f7ddd-112">.NET Standard 2.0 and later versions</span></span>
  * <span data-ttu-id="f7ddd-113">.NET Framework 4.7.2 i nowsze wersje</span><span class="sxs-lookup"><span data-stu-id="f7ddd-113">.NET Framework 4.7.2 and later versions</span></span>
  * <span data-ttu-id="f7ddd-114">.NET Core 2,0, 2,1 i 2,2</span><span class="sxs-lookup"><span data-stu-id="f7ddd-114">.NET Core 2.0, 2.1, and 2.2</span></span>

## <a name="additional-resources"></a><span data-ttu-id="f7ddd-115">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="f7ddd-115">Additional resources</span></span>

* [<span data-ttu-id="f7ddd-116">Jak używać biblioteki</span><span class="sxs-lookup"><span data-stu-id="f7ddd-116">How to use the library</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="f7ddd-117">Jak przeprowadzić migrację z pliku Newtonsoft. JSON</span><span class="sxs-lookup"><span data-stu-id="f7ddd-117">How to migrate from Newtonsoft.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="f7ddd-118">Jak pisać konwertery</span><span class="sxs-lookup"><span data-stu-id="f7ddd-118">How to write converters</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="f7ddd-119">Kod źródłowy system. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="f7ddd-119">System.Text.Json source code</span></span>](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json)
* [<span data-ttu-id="f7ddd-120">Dokumentacja interfejsu API System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="f7ddd-120">System.Text.Json API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="f7ddd-121">Dokumentacja interfejsu API System. Text. JSON. Serialization</span><span class="sxs-lookup"><span data-stu-id="f7ddd-121">System.Text.Json.Serialization API reference</span></span>](xref:System.Text.Json.Serialization)
<!-- * [Roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
