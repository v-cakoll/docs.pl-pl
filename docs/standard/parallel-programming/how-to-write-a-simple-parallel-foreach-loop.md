---
title: Napisz prosty program równoległy używający metody Parallel. ForEach
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
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160303"
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a><span data-ttu-id="9728d-102">Instrukcje: zapisywanie prostej pętli Parallel. ForEach</span><span class="sxs-lookup"><span data-stu-id="9728d-102">How to: Write a simple Parallel.ForEach loop</span></span>

<span data-ttu-id="9728d-103">Ten przykład pokazuje, jak używać pętli <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>, aby włączyć równoległość danych dla dowolnego <xref:System.Collections.IEnumerable?displayProperty=nameWithType> lub <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> źródła danych.</span><span class="sxs-lookup"><span data-stu-id="9728d-103">This example shows how to use a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop to enable data parallelism over any <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> data source.</span></span>

> [!NOTE]
> <span data-ttu-id="9728d-104">Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w PLINQ.</span><span class="sxs-lookup"><span data-stu-id="9728d-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="9728d-105">Jeśli nie znasz wyrażeń lambda w C# lub Visual Basic, zobacz [wyrażenia lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="9728d-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>

## <a name="example"></a><span data-ttu-id="9728d-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="9728d-106">Example</span></span>

<span data-ttu-id="9728d-107">W tym przykładzie założono, że masz kilka plików jpg w folderze *C:\Users\Public\Pictures\Sample obrazy* i utworzysz nowy podfolder o nazwie *zmodyfikowano*.</span><span class="sxs-lookup"><span data-stu-id="9728d-107">This example assumes you have several .jpg files in a *C:\Users\Public\Pictures\Sample Pictures* folder and creates a new sub-folder named *Modified*.</span></span> <span data-ttu-id="9728d-108">Gdy uruchamiasz ten przykład, obraca każdy obraz jpg w *przykładowych* obrazach i zapisuje je do *zmodyfikowania*.</span><span class="sxs-lookup"><span data-stu-id="9728d-108">When you run the example, it rotates each .jpg image in *Sample Pictures* and saves it to *Modified*.</span></span> <span data-ttu-id="9728d-109">W razie potrzeby można zmodyfikować dwie ścieżki.</span><span class="sxs-lookup"><span data-stu-id="9728d-109">You can modify the two paths as necessary.</span></span>

[!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
[!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]

<span data-ttu-id="9728d-110">Pętla <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> działa jak pętla <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9728d-110">A <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop works like a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> loop.</span></span> <span data-ttu-id="9728d-111">Pętla jest partycją źródłową kolekcji i planuje prace na wielu wątkach na podstawie środowiska systemowego.</span><span class="sxs-lookup"><span data-stu-id="9728d-111">The loop partitions the source collection and schedules the work on multiple threads based on the system environment.</span></span> <span data-ttu-id="9728d-112">Im więcej procesorów w systemie, tym szybsze jest uruchamianie metody równoległej.</span><span class="sxs-lookup"><span data-stu-id="9728d-112">The more processors on the system, the faster the parallel method runs.</span></span> <span data-ttu-id="9728d-113">W przypadku niektórych kolekcji źródłowych pętla sekwencyjna może być szybsza, w zależności od rozmiaru źródła i rodzaju pracy wykonywanej przez pętlę.</span><span class="sxs-lookup"><span data-stu-id="9728d-113">For some source collections, a sequential loop may be faster, depending on the size of the source and the kind of work the loop performs.</span></span> <span data-ttu-id="9728d-114">Aby uzyskać więcej informacji o wydajności, zobacz [potencjalne pułapek w zakresie danych i równoległości zadań](potential-pitfalls-in-data-and-task-parallelism.md).</span><span class="sxs-lookup"><span data-stu-id="9728d-114">For more information about performance, see [Potential pitfalls in data and task parallelism](potential-pitfalls-in-data-and-task-parallelism.md).</span></span>

<span data-ttu-id="9728d-115">Aby uzyskać więcej informacji na temat pętli równoległych, zobacz [How to: Write a Simple Parallel. for](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).</span><span class="sxs-lookup"><span data-stu-id="9728d-115">For more information about parallel loops, see [How to: Write a simple Parallel.For loop](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).</span></span>

<span data-ttu-id="9728d-116">Aby użyć <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> z kolekcją nieogólną, można użyć metody rozszerzenia <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> do przekonwertowania kolekcji na kolekcję ogólną, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9728d-116">To use <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> with a non-generic collection, you can use the <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> extension method to convert the collection to a generic collection, as shown in the following example:</span></span>

[!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
[!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]

<span data-ttu-id="9728d-117">Można również użyć równoległego LINQ (PLINQ) do przetwarzania zrównoleglanie <xref:System.Collections.Generic.IEnumerable%601> źródeł danych.</span><span class="sxs-lookup"><span data-stu-id="9728d-117">You can also use Parallel LINQ (PLINQ) to parallelize processing of <xref:System.Collections.Generic.IEnumerable%601> data sources.</span></span> <span data-ttu-id="9728d-118">PLINQ umożliwia użycie deklaracyjnej składni zapytań, aby wyrazić zachowanie pętli.</span><span class="sxs-lookup"><span data-stu-id="9728d-118">PLINQ enables you to use declarative query syntax to express the loop behavior.</span></span> <span data-ttu-id="9728d-119">Aby uzyskać więcej informacji, zobacz [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="9728d-119">For more information, see [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).</span></span>

## <a name="compile-and-run-the-code"></a><span data-ttu-id="9728d-120">Kompiluj i uruchamiaj kod</span><span class="sxs-lookup"><span data-stu-id="9728d-120">Compile and run the code</span></span>

<span data-ttu-id="9728d-121">Można skompilować kod jako aplikację konsolową dla .NET Framework lub jako aplikację konsolową dla platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9728d-121">You can compile the code as a console application for .NET Framework or as a console application for .NET Core.</span></span>

<span data-ttu-id="9728d-122">W programie Visual Studio istnieją Visual Basic i C# szablony aplikacji konsolowych dla systemów Windows Desktop i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9728d-122">In Visual Studio, there are Visual Basic and C# console application templates for Windows Desktop and .NET Core.</span></span>

<span data-ttu-id="9728d-123">W wierszu polecenia można użyć poleceń interfejs wiersza polecenia platformy .NET Core (na przykład `dotnet new console` lub `dotnet new console -lang vb`) lub można utworzyć plik i użyć kompilatora wiersza polecenia dla aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9728d-123">From the command line, you can use either the .NET Core CLI commands (for example, `dotnet new console` or `dotnet new console -lang vb`), or you can create the file and use the command-line compiler for a .NET Framework application.</span></span>

<span data-ttu-id="9728d-124">W przypadku projektu .NET Core należy odwołać się do pakietu NuGet **System. Drawing. Common** .</span><span class="sxs-lookup"><span data-stu-id="9728d-124">For a .NET Core project, you must reference the **System.Drawing.Common** NuGet package.</span></span> <span data-ttu-id="9728d-125">W programie Visual Studio Użyj Menedżera pakietów NuGet, aby zainstalować pakiet.</span><span class="sxs-lookup"><span data-stu-id="9728d-125">In Visual Studio, use the NuGet Package Manager to install the package.</span></span> <span data-ttu-id="9728d-126">Alternatywnie można dodać odwołanie do pakietu w pliku \*. csproj lub \*. vbproj:</span><span class="sxs-lookup"><span data-stu-id="9728d-126">Alternatively, you can add a reference to the package in your \*.csproj or \*.vbproj file:</span></span>

```xml
<ItemGroup>
     <PackageReference Include="System.Drawing.Common" Version="4.5.1" />
</ItemGroup>
```

<span data-ttu-id="9728d-127">Aby uruchomić aplikację konsolową .NET Core z poziomu wiersza polecenia, należy użyć `dotnet run` z folderu, który zawiera aplikację.</span><span class="sxs-lookup"><span data-stu-id="9728d-127">To run a .NET Core console application from the command line, use `dotnet run` from the folder that contains your application.</span></span>

<span data-ttu-id="9728d-128">Aby uruchomić aplikację konsolową z poziomu programu Visual Studio, naciśnij klawisz **F5**.</span><span class="sxs-lookup"><span data-stu-id="9728d-128">To run your console application from Visual Studio, press **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="9728d-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9728d-129">See also</span></span>

- [<span data-ttu-id="9728d-130">Równoległość danych</span><span class="sxs-lookup"><span data-stu-id="9728d-130">Data parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="9728d-131">Programowanie równoległe</span><span class="sxs-lookup"><span data-stu-id="9728d-131">Parallel programming</span></span>](../../../docs/standard/parallel-programming/index.md)
- [<span data-ttu-id="9728d-132">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="9728d-132">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
