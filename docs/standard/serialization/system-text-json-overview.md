---
title: Serializacja kodu JSON w programie .NET
author: tdykstra
ms.author: tdykstra
ms.date: 09/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
ms.openlocfilehash: 6cb45fded220b6123dbf4461f5f1cf1c3556ff69
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083092"
---
# <a name="json-serialization-in-net"></a><span data-ttu-id="25530-102">Serializacja kodu JSON w programie .NET</span><span class="sxs-lookup"><span data-stu-id="25530-102">JSON serialization in .NET</span></span>

<span data-ttu-id="25530-103">`System.Text.Json` Przestrzeń nazw zawiera funkcje serializowania do i z JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="25530-103">The `System.Text.Json` namespace provides functionality for serializing to and from JavaScript Object Notation (JSON).</span></span>

<span data-ttu-id="25530-104">Projekt biblioteki wyróżnia wysoką wydajność i małą alokację pamięci w ramach rozbudowanego zestawu funkcji.</span><span class="sxs-lookup"><span data-stu-id="25530-104">The library design emphasizes high performance and low memory allocation over an extensive feature set.</span></span> <span data-ttu-id="25530-105">Wbudowana obsługa UTF-8 optymalizuje proces odczytywania i pisania tekstu JSON zakodowanego w formacie UTF-8, który jest najbardziej rozpowszechnionym kodowaniem danych w sieci Web i plikach na dysku.</span><span class="sxs-lookup"><span data-stu-id="25530-105">Built-in UTF-8 support optimizes the process of reading and writing JSON text encoded as UTF-8, which is the most prevalent encoding for data on the web and files on disk.</span></span>

<span data-ttu-id="25530-106">Biblioteka zawiera również klasy umożliwiające pracę z modelem DOM (Document objecting) w pamięci.</span><span class="sxs-lookup"><span data-stu-id="25530-106">The library also provides classes for working with an in-memory document object model (DOM).</span></span> <span data-ttu-id="25530-107">Ta funkcja włącza losowy dostęp tylko do odczytu do elementów w pliku JSON lub ciągu.</span><span class="sxs-lookup"><span data-stu-id="25530-107">This feature enables random read-only access of the elements in a JSON file or string.</span></span> 

## <a name="how-to-get-the-library"></a><span data-ttu-id="25530-108">Jak uzyskać bibliotekę</span><span class="sxs-lookup"><span data-stu-id="25530-108">How to get the library</span></span>

* <span data-ttu-id="25530-109">Biblioteka jest wbudowana w ramach platformy udostępnionej [.NET Core 3,0](https://aka.ms/netcore3download) .</span><span class="sxs-lookup"><span data-stu-id="25530-109">The library is built-in as part of the [.NET Core 3.0](https://aka.ms/netcore3download) shared framework.</span></span>
* <span data-ttu-id="25530-110">W przypadku innych platform docelowych Zainstaluj pakiet NuGet [System. Text. JSON](https://www.nuget.org/packages/System.Text.Json) .</span><span class="sxs-lookup"><span data-stu-id="25530-110">For other target frameworks, install the [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet package.</span></span> <span data-ttu-id="25530-111">Pakiet obsługuje:</span><span class="sxs-lookup"><span data-stu-id="25530-111">The package supports:</span></span>
  * <span data-ttu-id="25530-112">.NET Standard 2,0 i nowsze wersje</span><span class="sxs-lookup"><span data-stu-id="25530-112">.NET Standard 2.0 and later versions</span></span>
  * <span data-ttu-id="25530-113">.NET Framework 4,61 i nowsze wersje</span><span class="sxs-lookup"><span data-stu-id="25530-113">.NET Framework 4.61 and later versions</span></span>
  * <span data-ttu-id="25530-114">.NET Core 2,0 i nowsze wersje</span><span class="sxs-lookup"><span data-stu-id="25530-114">.NET Core 2.0 and later versions</span></span>

## <a name="additional-resources"></a><span data-ttu-id="25530-115">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="25530-115">Additional resources</span></span>

* [<span data-ttu-id="25530-116">Jak używać biblioteki</span><span class="sxs-lookup"><span data-stu-id="25530-116">How to use the library</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="25530-117">Kod źródłowy</span><span class="sxs-lookup"><span data-stu-id="25530-117">Source code</span></span>](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json)
* [<span data-ttu-id="25530-118">Dokumentacja interfejsu API</span><span class="sxs-lookup"><span data-stu-id="25530-118">API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="25530-119">Plan rozwoju</span><span class="sxs-lookup"><span data-stu-id="25530-119">Roadmap</span></span>](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/roadmap/README.md)
* <span data-ttu-id="25530-120">Problemy z usługą GitHub w repozytorium dotnet/corefx</span><span class="sxs-lookup"><span data-stu-id="25530-120">GitHub issues in the dotnet/corefx repository</span></span>
  * [<span data-ttu-id="25530-121">Omówienie tworzenia pliku System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="25530-121">Discussion about the development of System.Text.Json</span></span>](https://github.com/dotnet/corefx/issues/33115)
  * [<span data-ttu-id="25530-122">Wszystkie problemy z System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="25530-122">All System.Text.Json issues</span></span>](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json)
  * [<span data-ttu-id="25530-123">Problemy z System. Text. JSON oznaczone etykietą JSON-funkcja-doc</span><span class="sxs-lookup"><span data-stu-id="25530-123">System.Text.Json issues labeled json-functionality-doc</span></span>](https://github.com/dotnet/corefx/labels/json-functionality-doc)
