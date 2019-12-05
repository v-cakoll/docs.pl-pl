---
title: Serializacja i deserializacja JSON C# przy użyciu-.NET
author: tdykstra
ms.author: tdykstra
ms.date: 09/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
ms.openlocfilehash: b43c3f6fd8ca56aaa99fffd40317920ee7600a2c
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802716"
---
# <a name="json-serialization-in-net---overview"></a><span data-ttu-id="000a7-102">Serializacja kodu JSON w programie .NET — Omówienie</span><span class="sxs-lookup"><span data-stu-id="000a7-102">JSON serialization in .NET - overview</span></span>

<span data-ttu-id="000a7-103">Przestrzeń nazw `System.Text.Json` zawiera funkcje serializowania do i deserializacji z JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="000a7-103">The `System.Text.Json` namespace provides functionality for serializing to and deserializing from JavaScript Object Notation (JSON).</span></span>

<span data-ttu-id="000a7-104">Projekt biblioteki wyróżnia wysoką wydajność i małą alokację pamięci w ramach rozbudowanego zestawu funkcji.</span><span class="sxs-lookup"><span data-stu-id="000a7-104">The library design emphasizes high performance and low memory allocation over an extensive feature set.</span></span> <span data-ttu-id="000a7-105">Wbudowana obsługa UTF-8 optymalizuje proces odczytywania i pisania tekstu JSON zakodowanego w formacie UTF-8, który jest najbardziej rozpowszechnionym kodowaniem danych w sieci Web i plikach na dysku.</span><span class="sxs-lookup"><span data-stu-id="000a7-105">Built-in UTF-8 support optimizes the process of reading and writing JSON text encoded as UTF-8, which is the most prevalent encoding for data on the web and files on disk.</span></span>

<span data-ttu-id="000a7-106">Biblioteka zawiera również klasy umożliwiające pracę z modelem DOM (Document objecting) w pamięci.</span><span class="sxs-lookup"><span data-stu-id="000a7-106">The library also provides classes for working with an in-memory document object model (DOM).</span></span> <span data-ttu-id="000a7-107">Ta funkcja włącza losowy dostęp tylko do odczytu do elementów w pliku JSON lub ciągu.</span><span class="sxs-lookup"><span data-stu-id="000a7-107">This feature enables random read-only access of the elements in a JSON file or string.</span></span> 

## <a name="how-to-get-the-library"></a><span data-ttu-id="000a7-108">Jak uzyskać bibliotekę</span><span class="sxs-lookup"><span data-stu-id="000a7-108">How to get the library</span></span>

* <span data-ttu-id="000a7-109">Biblioteka jest wbudowana w ramach platformy udostępnionej [.NET Core 3,0](https://aka.ms/netcore3download) .</span><span class="sxs-lookup"><span data-stu-id="000a7-109">The library is built-in as part of the [.NET Core 3.0](https://aka.ms/netcore3download) shared framework.</span></span>
* <span data-ttu-id="000a7-110">W przypadku innych platform docelowych Zainstaluj pakiet NuGet [System. Text. JSON](https://www.nuget.org/packages/System.Text.Json) .</span><span class="sxs-lookup"><span data-stu-id="000a7-110">For other target frameworks, install the [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet package.</span></span> <span data-ttu-id="000a7-111">Pakiet obsługuje:</span><span class="sxs-lookup"><span data-stu-id="000a7-111">The package supports:</span></span>
  * <span data-ttu-id="000a7-112">.NET Standard 2,0 i nowsze wersje</span><span class="sxs-lookup"><span data-stu-id="000a7-112">.NET Standard 2.0 and later versions</span></span>
  * <span data-ttu-id="000a7-113">.NET Framework 4.6.1 i nowsze wersje</span><span class="sxs-lookup"><span data-stu-id="000a7-113">.NET Framework 4.6.1 and later versions</span></span>
  * <span data-ttu-id="000a7-114">.NET Core 2,0, 2,1 i 2,2</span><span class="sxs-lookup"><span data-stu-id="000a7-114">.NET Core 2.0, 2.1, and 2.2</span></span>

## <a name="additional-resources"></a><span data-ttu-id="000a7-115">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="000a7-115">Additional resources</span></span>

* [<span data-ttu-id="000a7-116">Jak używać biblioteki</span><span class="sxs-lookup"><span data-stu-id="000a7-116">How to use the library</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="000a7-117">Kod źródłowy</span><span class="sxs-lookup"><span data-stu-id="000a7-117">Source code</span></span>](https://github.com/dotnet/runtime/tree/master/src/libraries/System.Text.Json)
* [<span data-ttu-id="000a7-118">Dokumentacja interfejsu API</span><span class="sxs-lookup"><span data-stu-id="000a7-118">API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="000a7-119">Plan rozwoju</span><span class="sxs-lookup"><span data-stu-id="000a7-119">Roadmap</span></span>](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Text.Json/roadmap/README.md)
* <span data-ttu-id="000a7-120">Problemy z usługą GitHub w repozytorium dotnet/corefx</span><span class="sxs-lookup"><span data-stu-id="000a7-120">GitHub issues in the dotnet/corefx repository</span></span>
  * [<span data-ttu-id="000a7-121">Omówienie tworzenia pliku System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="000a7-121">Discussion about the development of System.Text.Json</span></span>](https://github.com/dotnet/corefx/issues/33115) <!-- TODO: Issues are still not moved to the new repo-->
  * [<span data-ttu-id="000a7-122">Wszystkie problemy z System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="000a7-122">All System.Text.Json issues</span></span>](https://github.com/dotnet/runtime/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json)
  * [<span data-ttu-id="000a7-123">Problemy z System. Text. JSON oznaczone etykietą JSON-funkcja-doc</span><span class="sxs-lookup"><span data-stu-id="000a7-123">System.Text.Json issues labeled json-functionality-doc</span></span>](https://github.com/dotnet/runtime/labels/json-functionality-doc)
