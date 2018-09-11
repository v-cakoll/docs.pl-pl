---
title: 'Porady: Określanie stopnia równoległości w bloku przepływu danych'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dataflow block, specifying parallelism in TPL
- Task Parallel Library, dataflows
- TPL dataflow library, specifying parallelism
ms.assetid: e4088541-ee05-40db-95f5-147cfe62fde7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0b597cf93cdf249936a34b2c07b38d000c96333f
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2018
ms.locfileid: "44353005"
---
# <a name="how-to-specify-the-degree-of-parallelism-in-a-dataflow-block"></a><span data-ttu-id="9b426-102">Porady: Określanie stopnia równoległości w bloku przepływu danych</span><span class="sxs-lookup"><span data-stu-id="9b426-102">How to: Specify the Degree of Parallelism in a Dataflow Block</span></span>
<span data-ttu-id="9b426-103">W tym dokumencie opisano sposób ustawiania <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> właściwości, aby umożliwić wykonanie bloku przepływu danych do przetwarzania więcej niż jeden komunikat w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="9b426-103">This document describes how to set the <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> property to enable an execution dataflow block to process more than one message at a time.</span></span> <span data-ttu-id="9b426-104">Jest to przydatne w po bloku przepływu danych, która wykonuje obliczenia długotrwałych i może być korzystne przetwarzanie komunikatów w sposób równoległy.</span><span class="sxs-lookup"><span data-stu-id="9b426-104">Doing this is useful when you have a dataflow block that performs a long-running computation and can benefit from processing messages in parallel.</span></span> <span data-ttu-id="9b426-105">W tym przykładzie użyto <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> klasy do wykonywania wielu operacji przepływu danych, jednocześnie; Jednakże, można określić maksymalny stopień równoległości w żadnym z typów bloków wykonywanie wstępnie zdefiniowanych, udostępniane Biblioteka przepływu danych TPL <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>, i <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9b426-105">This example uses the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> class to perform multiple dataflow operations concurrently; however, you can specify the maximum degree of parallelism in any of the predefined execution block types that the TPL Dataflow Library provides, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>, and <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a><span data-ttu-id="9b426-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="9b426-106">Example</span></span>  
 <span data-ttu-id="9b426-107">Poniższy przykład wykonuje dwa obliczeń przepływu danych i wyświetla czas, która jest wymagana dla każdego obliczenia.</span><span class="sxs-lookup"><span data-stu-id="9b426-107">The following example performs two dataflow computations and prints the elapsed time that is required for each computation.</span></span> <span data-ttu-id="9b426-108">Pierwszy obliczeń określa maksymalny stopień równoległości, 1, co jest ustawieniem domyślnym.</span><span class="sxs-lookup"><span data-stu-id="9b426-108">The first computation specifies a maximum degree of parallelism of 1, which is the default.</span></span> <span data-ttu-id="9b426-109">Maksymalny stopień równoległości 1 powoduje, że blok przepływu danych do przetwarzania komunikatów szeregowo.</span><span class="sxs-lookup"><span data-stu-id="9b426-109">A maximum degree of parallelism of 1 causes the dataflow block to process messages serially.</span></span> <span data-ttu-id="9b426-110">Drugi obliczeń przypomina pierwsze, z tą różnicą, że określa maksymalny stopień równoległości, która jest równa liczbie procesorów dostępnych.</span><span class="sxs-lookup"><span data-stu-id="9b426-110">The second computation resembles the first, except that it specifies a maximum degree of parallelism that is equal to the number of available processors.</span></span> <span data-ttu-id="9b426-111">Dzięki temu bloku przepływu danych do wykonywania wielu operacji równoległych.</span><span class="sxs-lookup"><span data-stu-id="9b426-111">This enables the dataflow block to perform multiple operations in parallel.</span></span>  
  
 [!code-csharp[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_degreeofparallelism/cs/dataflowdegreeofparallelism.cs#1)]
 [!code-vb[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_degreeofparallelism/vb/dataflowdegreeofparallelism.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9b426-112">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="9b426-112">Compiling the Code</span></span>  
 <span data-ttu-id="9b426-113">Kopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `DataflowDegreeOfParallelism.cs` (`DataflowDegreeOfParallelism.vb` dla języka Visual Basic), a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9b426-113">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DataflowDegreeOfParallelism.cs` (`DataflowDegreeOfParallelism.vb` for Visual Basic), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 <span data-ttu-id="9b426-114">Visual C#</span><span class="sxs-lookup"><span data-stu-id="9b426-114">Visual C#</span></span>  
  
 <span data-ttu-id="9b426-115">**CSC.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.cs**</span><span class="sxs-lookup"><span data-stu-id="9b426-115">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.cs**</span></span>  
  
 <span data-ttu-id="9b426-116">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9b426-116">Visual Basic</span></span>  
  
 <span data-ttu-id="9b426-117">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.vb**</span><span class="sxs-lookup"><span data-stu-id="9b426-117">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="9b426-118">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="9b426-118">Robust Programming</span></span>  
 <span data-ttu-id="9b426-119">Domyślnie każdy blok przepływu danych wstępnie zdefiniowanych propaguje wiadomości w kolejności, w jakiej komunikaty są odbierane.</span><span class="sxs-lookup"><span data-stu-id="9b426-119">By default, each predefined dataflow block propagates out messages in the order in which the messages are received.</span></span>  <span data-ttu-id="9b426-120">Chociaż wiele wiadomości są przetwarzane jednocześnie w przypadku określenia maksymalny stopień równoległości, która jest większa niż 1, są nadal propagowane się w kolejności, w której zostały odebrane.</span><span class="sxs-lookup"><span data-stu-id="9b426-120">Although multiple messages are processed simultaneously when you specify a maximum degree of parallelism that is greater than 1, they are still propagated out in the order in which they are received.</span></span>  
  
 <span data-ttu-id="9b426-121">Ponieważ <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> właściwość reprezentuje maksymalny stopień równoległości, bloku przepływu danych może być wykonywany z niższy stopień równoległości, niż można określić.</span><span class="sxs-lookup"><span data-stu-id="9b426-121">Because the <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> property represents the maximum degree of parallelism, the dataflow block might execute with a lesser degree of parallelism than you specify.</span></span> <span data-ttu-id="9b426-122">W bloku przepływu danych można użyć niższy stopień równoległości, do swoich wymagań funkcjonalności lub konto z powodu braku dostępnych zasobów systemowych.</span><span class="sxs-lookup"><span data-stu-id="9b426-122">The dataflow block can use a lesser degree of parallelism to meet its functional requirements or to account for a lack of available system resources.</span></span> <span data-ttu-id="9b426-123">W bloku przepływu danych nigdy nie wybiera większego stopnia równoległości nie określisz.</span><span class="sxs-lookup"><span data-stu-id="9b426-123">A dataflow block never chooses a greater degree of parallelism than you specify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b426-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9b426-124">See also</span></span>

- [<span data-ttu-id="9b426-125">Przepływ danych</span><span class="sxs-lookup"><span data-stu-id="9b426-125">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
