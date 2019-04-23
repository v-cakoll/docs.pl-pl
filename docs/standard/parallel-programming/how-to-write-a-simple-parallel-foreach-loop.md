---
title: Napisać prosty program równoległego za pomocą Parallel.ForEach
ms.date: 02/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 599432af178031a85dea4155a8fd2923f879a600
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59427360"
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a><span data-ttu-id="aff77-102">Instrukcje: Zapisywanie prostej pętli Parallel.ForEach</span><span class="sxs-lookup"><span data-stu-id="aff77-102">How to: Write a simple Parallel.ForEach loop</span></span>

<span data-ttu-id="aff77-103">W tym przykładzie pokazano, jak używać <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> pętli, aby włączyć równoległość danych przez dowolny <xref:System.Collections.IEnumerable?displayProperty=nameWithType> lub <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> źródła danych.</span><span class="sxs-lookup"><span data-stu-id="aff77-103">This example shows how to use a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop to enable data parallelism over any <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> data source.</span></span>

> [!NOTE]
> <span data-ttu-id="aff77-104">Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w PLINQ.</span><span class="sxs-lookup"><span data-stu-id="aff77-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="aff77-105">Jeśli nie znasz wyrażeń lambda w C# lub Visual Basic, zobacz [wyrażeń Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="aff77-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>

## <a name="example"></a><span data-ttu-id="aff77-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="aff77-106">Example</span></span>

<span data-ttu-id="aff77-107">W tym przykładzie przyjęto założenie, masz kilka plików .jpg w *obrazy C:\Users\Public\Pictures\Sample* folder i tworzy nowy folder podrzędny o nazwie *zmodyfikowane*.</span><span class="sxs-lookup"><span data-stu-id="aff77-107">This example assumes you have several .jpg files in a *C:\Users\Public\Pictures\Sample Pictures* folder and creates a new sub-folder named *Modified*.</span></span> <span data-ttu-id="aff77-108">Po uruchomieniu tego przykładu, obraca się każdy obraz jpg w *przykładowe obrazy* i zapisuje go do *zmodyfikowane*.</span><span class="sxs-lookup"><span data-stu-id="aff77-108">When you run the example, it rotates each .jpg image in *Sample Pictures* and saves it to *Modified*.</span></span> <span data-ttu-id="aff77-109">Można modyfikować tych dwóch ścieżek, zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="aff77-109">You can modify the two paths as necessary.</span></span>

[!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
[!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]

<span data-ttu-id="aff77-110">A <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> pętli działa jak <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> pętli.</span><span class="sxs-lookup"><span data-stu-id="aff77-110">A <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop works like a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> loop.</span></span> <span data-ttu-id="aff77-111">Pętla partycje kolekcji źródłowej oraz planowanie zadań w wielu wątkach, w zależności od środowiska systemu.</span><span class="sxs-lookup"><span data-stu-id="aff77-111">The loop partitions the source collection and schedules the work on multiple threads based on the system environment.</span></span> <span data-ttu-id="aff77-112">Więcej procesorów w systemie, tym szybciej parallel — metoda jest uruchamiany.</span><span class="sxs-lookup"><span data-stu-id="aff77-112">The more processors on the system, the faster the parallel method runs.</span></span> <span data-ttu-id="aff77-113">W niektórych kolekcjach źródła pętli sekwencyjnej może być szybsze, w zależności od rozmiaru źródła i rodzaj pracy, który wykonuje pętlę.</span><span class="sxs-lookup"><span data-stu-id="aff77-113">For some source collections, a sequential loop may be faster, depending on the size of the source and the kind of work the loop performs.</span></span> <span data-ttu-id="aff77-114">Aby uzyskać więcej informacji o wydajności, zobacz [potencjalne pułapki związane z równoległości danych i zadań](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)</span><span class="sxs-lookup"><span data-stu-id="aff77-114">For more information about performance, see [Potential pitfalls in data and task parallelism](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)</span></span>

<span data-ttu-id="aff77-115">Aby uzyskać więcej informacji na temat pętli równoległych zobacz [jak: Zapisywanie prostej pętli Parallel.For](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).</span><span class="sxs-lookup"><span data-stu-id="aff77-115">For more information about parallel loops, see [How to: Write a simple Parallel.For loop](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).</span></span>

<span data-ttu-id="aff77-116">Aby użyć <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> z nieogólna kolekcja, możesz użyć <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> metodę rozszerzenia, aby przekonwertować kolekcji do kolekcji ogólnej, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="aff77-116">To use <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> with a non-generic collection, you can use the <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> extension method to convert the collection to a generic collection, as shown in the following example:</span></span>

[!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
[!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]

<span data-ttu-id="aff77-117">Umożliwia także Parallel LINQ (PLINQ) do zrównoleglenia przetwarzania <xref:System.Collections.Generic.IEnumerable%601> źródeł danych.</span><span class="sxs-lookup"><span data-stu-id="aff77-117">You can also use Parallel LINQ (PLINQ) to parallelize processing of <xref:System.Collections.Generic.IEnumerable%601> data sources.</span></span> <span data-ttu-id="aff77-118">PLINQ umożliwia użycie składni zapytań deklaratywne określenie zachowania pętli.</span><span class="sxs-lookup"><span data-stu-id="aff77-118">PLINQ enables you to use declarative query syntax to express the loop behavior.</span></span> <span data-ttu-id="aff77-119">Aby uzyskać więcej informacji, zobacz [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="aff77-119">For more information, see [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).</span></span>

## <a name="compile-and-run-the-code"></a><span data-ttu-id="aff77-120">Kompilowanie i uruchamianie kodu</span><span class="sxs-lookup"><span data-stu-id="aff77-120">Compile and run the code</span></span>

<span data-ttu-id="aff77-121">Można skompilować kod jako aplikację konsolową w języku .NET Framework lub aplikacji konsoli dla platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="aff77-121">You can compile the code as a console application for .NET Framework or as a console application for .NET Core.</span></span>

<span data-ttu-id="aff77-122">W programie Visual Studio są Visual Basic i C# konsoli szablonów aplikacji dla Windows Desktop i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="aff77-122">In Visual Studio, there are Visual Basic and C# console application templates for Windows Desktop and .NET Core.</span></span>

<span data-ttu-id="aff77-123">W wierszu polecenia można użyć platformy .NET Core i jego narzędzi interfejsu wiersza polecenia (na przykład `dotnet new console` lub `dotnet new console -lang vb`), lub można utworzyć pliku i używania kompilatora wiersza polecenia dla aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aff77-123">From the command line, you can use either .NET Core and its CLI tools (for example, `dotnet new console` or `dotnet new console -lang vb`), or you can create the file and use the command-line compiler for a .NET Framework application.</span></span>

<span data-ttu-id="aff77-124">Dla projektu .NET Core, należy odwołać **System.Drawing.Common** pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="aff77-124">For a .NET Core project, you must reference the **System.Drawing.Common** NuGet package.</span></span> <span data-ttu-id="aff77-125">W programie Visual Studio Użyj Menedżera pakietów NuGet, aby zainstalować pakiet.</span><span class="sxs-lookup"><span data-stu-id="aff77-125">In Visual Studio, use the NuGet Package Manager to install the package.</span></span> <span data-ttu-id="aff77-126">Alternatywnie, można dodać odwołania do pakietu w swojej \*.csproj lub \*pliku vbproj:</span><span class="sxs-lookup"><span data-stu-id="aff77-126">Alternatively, you can add a reference to the package in your \*.csproj or \*.vbproj file:</span></span>
 
```xml
<ItemGroup>
     <PackageReference Include="System.Drawing.Common" Version="4.5.1" />
</ItemGroup>
```

<span data-ttu-id="aff77-127">Aby uruchomić aplikację konsoli .NET Core z poziomu wiersza polecenia, użyj `dotnet run` z folderu, który zawiera aplikację.</span><span class="sxs-lookup"><span data-stu-id="aff77-127">To run a .NET Core console application from the command line, use `dotnet run` from the folder that contains your application.</span></span>

<span data-ttu-id="aff77-128">Aby uruchomić aplikację konsoli w programie Visual Studio, naciśnij klawisz **F5**.</span><span class="sxs-lookup"><span data-stu-id="aff77-128">To run your console application from Visual Studio, press **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="aff77-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aff77-129">See also</span></span>

- [<span data-ttu-id="aff77-130">Równoległość danych</span><span class="sxs-lookup"><span data-stu-id="aff77-130">Data parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="aff77-131">Programowanie równoległe</span><span class="sxs-lookup"><span data-stu-id="aff77-131">Parallel programming</span></span>](../../../docs/standard/parallel-programming/index.md)
- [<span data-ttu-id="aff77-132">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="aff77-132">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
