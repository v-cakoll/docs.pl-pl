---
title: Napisz prosty program równoległy przy użyciu Parallel.ForEach
ms.date: 02/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
ms.openlocfilehash: 02b94b673dc4468e68a1dadd83aab0e3bfcfaa16
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160303"
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a><span data-ttu-id="c6885-102">Jak: Napisz prostą pętlę Parallel.ForEach</span><span class="sxs-lookup"><span data-stu-id="c6885-102">How to: Write a simple Parallel.ForEach loop</span></span>

<span data-ttu-id="c6885-103">W tym przykładzie pokazano, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> jak używać pętli, <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> aby włączyć równoległość danych nad dowolnym lub źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="c6885-103">This example shows how to use a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop to enable data parallelism over any <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> data source.</span></span>

> [!NOTE]
> <span data-ttu-id="c6885-104">Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w PLINQ.</span><span class="sxs-lookup"><span data-stu-id="c6885-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="c6885-105">Jeśli nie znasz wyrażeń lambda w języku C# lub Visual Basic, zobacz [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="c6885-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>

## <a name="example"></a><span data-ttu-id="c6885-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="c6885-106">Example</span></span>

<span data-ttu-id="c6885-107">W tym przykładzie przyjęto założenie, że w folderze *C:\Users\Public\Public\Pictures\Sample Pictures* znajduje się kilka plików jpg i tworzy nowy podfolder o nazwie *Zmodyfikowano*.</span><span class="sxs-lookup"><span data-stu-id="c6885-107">This example assumes you have several .jpg files in a *C:\Users\Public\Pictures\Sample Pictures* folder and creates a new sub-folder named *Modified*.</span></span> <span data-ttu-id="c6885-108">Po uruchomieniu przykładu obraca każdy obraz jpg w *przykładowych obrazach* i zapisuje go w *zmodyfikowanej*.</span><span class="sxs-lookup"><span data-stu-id="c6885-108">When you run the example, it rotates each .jpg image in *Sample Pictures* and saves it to *Modified*.</span></span> <span data-ttu-id="c6885-109">W razie potrzeby można zmodyfikować dwie ścieżki.</span><span class="sxs-lookup"><span data-stu-id="c6885-109">You can modify the two paths as necessary.</span></span>

[!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
[!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]

<span data-ttu-id="c6885-110">Pętla <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> działa <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> jak pętla.</span><span class="sxs-lookup"><span data-stu-id="c6885-110">A <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop works like a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> loop.</span></span> <span data-ttu-id="c6885-111">Pętla dzieli kolekcję źródłową i planuje pracę nad wieloma wątkami na podstawie środowiska systemowego.</span><span class="sxs-lookup"><span data-stu-id="c6885-111">The loop partitions the source collection and schedules the work on multiple threads based on the system environment.</span></span> <span data-ttu-id="c6885-112">Im więcej procesorów w systemie, tym szybciej działa metoda równoległa.</span><span class="sxs-lookup"><span data-stu-id="c6885-112">The more processors on the system, the faster the parallel method runs.</span></span> <span data-ttu-id="c6885-113">W przypadku niektórych kolekcji źródłowych pętla sekwencyjna może być szybsza, w zależności od rozmiaru źródła i rodzaju pracy wykonywanej przez pętlę.</span><span class="sxs-lookup"><span data-stu-id="c6885-113">For some source collections, a sequential loop may be faster, depending on the size of the source and the kind of work the loop performs.</span></span> <span data-ttu-id="c6885-114">Aby uzyskać więcej informacji na temat wydajności, zobacz [Potencjalne pułapki w równoległości danych i zadań](potential-pitfalls-in-data-and-task-parallelism.md).</span><span class="sxs-lookup"><span data-stu-id="c6885-114">For more information about performance, see [Potential pitfalls in data and task parallelism](potential-pitfalls-in-data-and-task-parallelism.md).</span></span>

<span data-ttu-id="c6885-115">Aby uzyskać więcej informacji na temat pętli równoległych, zobacz [Jak: Napisać prostą parallel.For pętli](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).</span><span class="sxs-lookup"><span data-stu-id="c6885-115">For more information about parallel loops, see [How to: Write a simple Parallel.For loop](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).</span></span>

<span data-ttu-id="c6885-116">Aby <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> użyć z kolekcji nierodzajowych, <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> można użyć metody rozszerzenia do konwersji kolekcji do kolekcji ogólnej, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="c6885-116">To use <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> with a non-generic collection, you can use the <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> extension method to convert the collection to a generic collection, as shown in the following example:</span></span>

[!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
[!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]

<span data-ttu-id="c6885-117">Można również użyć Równoległego LINQ (PLINQ) do równoległego przetwarzania <xref:System.Collections.Generic.IEnumerable%601> źródeł danych.</span><span class="sxs-lookup"><span data-stu-id="c6885-117">You can also use Parallel LINQ (PLINQ) to parallelize processing of <xref:System.Collections.Generic.IEnumerable%601> data sources.</span></span> <span data-ttu-id="c6885-118">PLINQ umożliwia użycie deklaratywnej składni kwerendy do wyrażenia zachowania pętli.</span><span class="sxs-lookup"><span data-stu-id="c6885-118">PLINQ enables you to use declarative query syntax to express the loop behavior.</span></span> <span data-ttu-id="c6885-119">Aby uzyskać więcej informacji, zobacz [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="c6885-119">For more information, see [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).</span></span>

## <a name="compile-and-run-the-code"></a><span data-ttu-id="c6885-120">Kompilowanie i uruchamianie kodu</span><span class="sxs-lookup"><span data-stu-id="c6885-120">Compile and run the code</span></span>

<span data-ttu-id="c6885-121">Kod można skompilować jako aplikację konsoli dla platformy .NET Framework lub jako aplikację konsoli dla .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c6885-121">You can compile the code as a console application for .NET Framework or as a console application for .NET Core.</span></span>

<span data-ttu-id="c6885-122">W programie Visual Studio istnieją szablony aplikacji konsoli Visual Basic i C# dla komputerów stacjonarnych systemu Windows i programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c6885-122">In Visual Studio, there are Visual Basic and C# console application templates for Windows Desktop and .NET Core.</span></span>

<span data-ttu-id="c6885-123">Z wiersza polecenia można użyć poleceń .NET Core CLI `dotnet new console` `dotnet new console -lang vb`(na przykład lub), lub można utworzyć plik i użyć kompilatora wiersza polecenia dla aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c6885-123">From the command line, you can use either the .NET Core CLI commands (for example, `dotnet new console` or `dotnet new console -lang vb`), or you can create the file and use the command-line compiler for a .NET Framework application.</span></span>

<span data-ttu-id="c6885-124">W przypadku projektu .NET Core należy odwołać się do pakietu **System.Drawing.Common** NuGet.</span><span class="sxs-lookup"><span data-stu-id="c6885-124">For a .NET Core project, you must reference the **System.Drawing.Common** NuGet package.</span></span> <span data-ttu-id="c6885-125">W programie Visual Studio użyj Menedżera pakietów NuGet, aby zainstalować pakiet.</span><span class="sxs-lookup"><span data-stu-id="c6885-125">In Visual Studio, use the NuGet Package Manager to install the package.</span></span> <span data-ttu-id="c6885-126">Alternatywnie możesz dodać odwołanie do pakietu \*w pliku .csproj lub \*.vbproj:</span><span class="sxs-lookup"><span data-stu-id="c6885-126">Alternatively, you can add a reference to the package in your \*.csproj or \*.vbproj file:</span></span>

```xml
<ItemGroup>
     <PackageReference Include="System.Drawing.Common" Version="4.5.1" />
</ItemGroup>
```

<span data-ttu-id="c6885-127">Aby uruchomić aplikację konsoli .NET Core z `dotnet run` wiersza polecenia, należy użyć z folderu, który zawiera aplikację.</span><span class="sxs-lookup"><span data-stu-id="c6885-127">To run a .NET Core console application from the command line, use `dotnet run` from the folder that contains your application.</span></span>

<span data-ttu-id="c6885-128">Aby uruchomić aplikację konsoli z programu Visual Studio, naciśnij klawisz **F5**.</span><span class="sxs-lookup"><span data-stu-id="c6885-128">To run your console application from Visual Studio, press **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="c6885-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c6885-129">See also</span></span>

- [<span data-ttu-id="c6885-130">Równoległość danych</span><span class="sxs-lookup"><span data-stu-id="c6885-130">Data parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="c6885-131">Programowanie równoległe</span><span class="sxs-lookup"><span data-stu-id="c6885-131">Parallel programming</span></span>](../../../docs/standard/parallel-programming/index.md)
- [<span data-ttu-id="c6885-132">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="c6885-132">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
