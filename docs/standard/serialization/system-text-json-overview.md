---
title: Serializowanie i deserializacja JSON przy użyciu języka C# — .NET
description: To omówienie zawiera opis System.Text.Json funkcji przestrzeni nazw do serializacji do i deserializacji z JSON w programie .NET.
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 909d979d46b30939e304af071de65d230febd92d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "83380125"
---
# <a name="json-serialization-and-deserialization-marshalling-and-unmarshalling-in-net---overview"></a><span data-ttu-id="c205f-103">Serializacja i deserializacja kodu JSON (kierowanie i cofanie) w programie .NET — Omówienie</span><span class="sxs-lookup"><span data-stu-id="c205f-103">JSON serialization and deserialization (marshalling and unmarshalling) in .NET - overview</span></span>

<span data-ttu-id="c205f-104">`System.Text.Json`Przestrzeń nazw zawiera funkcje serializacji do i deserializacji z JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="c205f-104">The `System.Text.Json` namespace provides functionality for serializing to and deserializing from JavaScript Object Notation (JSON).</span></span>

<span data-ttu-id="c205f-105">Projekt biblioteki wyróżnia wysoką wydajność i małą alokację pamięci w ramach rozbudowanego zestawu funkcji.</span><span class="sxs-lookup"><span data-stu-id="c205f-105">The library design emphasizes high performance and low memory allocation over an extensive feature set.</span></span> <span data-ttu-id="c205f-106">Wbudowana obsługa UTF-8 optymalizuje proces odczytywania i pisania tekstu JSON zakodowanego w formacie UTF-8, który jest najbardziej rozpowszechnionym kodowaniem danych w sieci Web i plikach na dysku.</span><span class="sxs-lookup"><span data-stu-id="c205f-106">Built-in UTF-8 support optimizes the process of reading and writing JSON text encoded as UTF-8, which is the most prevalent encoding for data on the web and files on disk.</span></span>

<span data-ttu-id="c205f-107">Biblioteka zawiera również klasy umożliwiające pracę z modelem DOM (Document objecting) w pamięci.</span><span class="sxs-lookup"><span data-stu-id="c205f-107">The library also provides classes for working with an in-memory document object model (DOM).</span></span> <span data-ttu-id="c205f-108">Ta funkcja włącza losowy dostęp tylko do odczytu do elementów w pliku JSON lub ciągu.</span><span class="sxs-lookup"><span data-stu-id="c205f-108">This feature enables random read-only access of the elements in a JSON file or string.</span></span>

## <a name="how-to-get-the-library"></a><span data-ttu-id="c205f-109">Jak uzyskać bibliotekę</span><span class="sxs-lookup"><span data-stu-id="c205f-109">How to get the library</span></span>

* <span data-ttu-id="c205f-110">Biblioteka jest wbudowana w ramach platformy udostępnionej [.NET Core 3,0](https://aka.ms/netcore3download) .</span><span class="sxs-lookup"><span data-stu-id="c205f-110">The library is built-in as part of the [.NET Core 3.0](https://aka.ms/netcore3download) shared framework.</span></span>
* <span data-ttu-id="c205f-111">W przypadku innych platform docelowych zainstaluj [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="c205f-111">For other target frameworks, install the [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet package.</span></span> <span data-ttu-id="c205f-112">Pakiet obsługuje:</span><span class="sxs-lookup"><span data-stu-id="c205f-112">The package supports:</span></span>
  * <span data-ttu-id="c205f-113">.NET Standard 2,0 i nowsze wersje</span><span class="sxs-lookup"><span data-stu-id="c205f-113">.NET Standard 2.0 and later versions</span></span>
  * <span data-ttu-id="c205f-114">.NET Framework 4.7.2 i nowsze wersje</span><span class="sxs-lookup"><span data-stu-id="c205f-114">.NET Framework 4.7.2 and later versions</span></span>
  * <span data-ttu-id="c205f-115">.NET Core 2,0, 2,1 i 2,2</span><span class="sxs-lookup"><span data-stu-id="c205f-115">.NET Core 2.0, 2.1, and 2.2</span></span>

## <a name="additional-resources"></a><span data-ttu-id="c205f-116">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="c205f-116">Additional resources</span></span>

* [<span data-ttu-id="c205f-117">Jak używać biblioteki</span><span class="sxs-lookup"><span data-stu-id="c205f-117">How to use the library</span></span>](system-text-json-how-to.md)
* <span data-ttu-id="c205f-118">[Jak przeprowadzić migrację zNewtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span><span class="sxs-lookup"><span data-stu-id="c205f-118">[How to migrate from Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span></span>
* [<span data-ttu-id="c205f-119">Jak pisać konwertery</span><span class="sxs-lookup"><span data-stu-id="c205f-119">How to write converters</span></span>](system-text-json-converters-how-to.md)
* <span data-ttu-id="c205f-120">[System.Text.Jsonkod źródłowy](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="c205f-120">[System.Text.Json source code](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json)</span></span>
* <span data-ttu-id="c205f-121">[System.Text.JsonDokumentacja interfejsu API](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="c205f-121">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="c205f-122">[System.Text.Json. Dokumentacja interfejsu API serializacji](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="c205f-122">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
<!-- * [Roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
