---
title: 'Porady: Określanie stopnia równoległości w bloku przepływu danych'
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
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
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0631603e3426a08cc1f3abb07bc0f9ecc73adb21
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-specify-the-degree-of-parallelism-in-a-dataflow-block"></a><span data-ttu-id="1a157-102">Porady: Określanie stopnia równoległości w bloku przepływu danych</span><span class="sxs-lookup"><span data-stu-id="1a157-102">How to: Specify the Degree of Parallelism in a Dataflow Block</span></span>
<span data-ttu-id="1a157-103">Ten dokument zawiera opis sposobu ustawiania <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> właściwości, aby umożliwić wykonanie bloku przepływu danych do jednoczesnego przetwarzania więcej niż jeden komunikat.</span><span class="sxs-lookup"><span data-stu-id="1a157-103">This document describes how to set the <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> property to enable an execution dataflow block to process more than one message at a time.</span></span> <span data-ttu-id="1a157-104">Jest to przydatne w przypadku ma bloku przepływu danych, która wykonuje obliczenia długotrwałe oraz mogą korzystać z przetwarzanie komunikatów równolegle.</span><span class="sxs-lookup"><span data-stu-id="1a157-104">Doing this is useful when you have a dataflow block that performs a long-running computation and can benefit from processing messages in parallel.</span></span> <span data-ttu-id="1a157-105">W tym przykładzie użyto <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> klasy w celu wykonania wielu operacji przepływu danych, jednocześnie; jednak, można określić maksymalny stopień równoległości w żadnym z typów bloku wykonania wstępnie zdefiniowanych, które udostępnia przepływu danych tpl, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>, i <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1a157-105">This example uses the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> class to perform multiple dataflow operations concurrently; however, you can specify the maximum degree of parallelism in any of the predefined execution block types that the TPL Dataflow Library provides, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>, and <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a><span data-ttu-id="1a157-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="1a157-106">Example</span></span>  
 <span data-ttu-id="1a157-107">W poniższym przykładzie wykonuje dwie obliczenia przepływu danych i wyświetla czas, który upłynął wymaganego do każdego obliczeń.</span><span class="sxs-lookup"><span data-stu-id="1a157-107">The following example performs two dataflow computations and prints the elapsed time that is required for each computation.</span></span> <span data-ttu-id="1a157-108">Pierwszy obliczenia określa maksymalny stopień równoległości 1, co jest ustawieniem domyślnym.</span><span class="sxs-lookup"><span data-stu-id="1a157-108">The first computation specifies a maximum degree of parallelism of 1, which is the default.</span></span> <span data-ttu-id="1a157-109">Maksymalny stopień równoległości 1 powoduje, że blok przepływu danych do przetwarzania komunikatów pojedynczo.</span><span class="sxs-lookup"><span data-stu-id="1a157-109">A maximum degree of parallelism of 1 causes the dataflow block to process messages serially.</span></span> <span data-ttu-id="1a157-110">Drugi obliczenia podobny pierwsza strona, z tą różnicą, że określa maksymalny stopień równoległości, który jest taki sam, jak liczba dostępnych procesorów.</span><span class="sxs-lookup"><span data-stu-id="1a157-110">The second computation resembles the first, except that it specifies a maximum degree of parallelism that is equal to the number of available processors.</span></span> <span data-ttu-id="1a157-111">Dzięki temu bloku przepływu danych do wykonywania wielu operacji równolegle.</span><span class="sxs-lookup"><span data-stu-id="1a157-111">This enables the dataflow block to perform multiple operations in parallel.</span></span>  
  
 [!code-csharp[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_degreeofparallelism/cs/dataflowdegreeofparallelism.cs#1)]
 [!code-vb[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_degreeofparallelism/vb/dataflowdegreeofparallelism.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1a157-112">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="1a157-112">Compiling the Code</span></span>  
 <span data-ttu-id="1a157-113">Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `DataflowDegreeOfParallelism.cs` (`DataflowDegreeOfParallelism.vb` w języku Visual Basic), a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1a157-113">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DataflowDegreeOfParallelism.cs` (`DataflowDegreeOfParallelism.vb` for Visual Basic), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 <span data-ttu-id="1a157-114">Visual C#</span><span class="sxs-lookup"><span data-stu-id="1a157-114">Visual C#</span></span>  
  
 <span data-ttu-id="1a157-115">**CSC.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.cs**</span><span class="sxs-lookup"><span data-stu-id="1a157-115">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.cs**</span></span>  
  
 <span data-ttu-id="1a157-116">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1a157-116">Visual Basic</span></span>  
  
 <span data-ttu-id="1a157-117">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.vb**</span><span class="sxs-lookup"><span data-stu-id="1a157-117">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="1a157-118">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="1a157-118">Robust Programming</span></span>  
 <span data-ttu-id="1a157-119">Domyślnie każdy blok przepływu danych wstępnie zdefiniowanych propaguje wiadomości w kolejności, w którym są odbierane wiadomości.</span><span class="sxs-lookup"><span data-stu-id="1a157-119">By default, each predefined dataflow block propagates out messages in the order in which the messages are received.</span></span>  <span data-ttu-id="1a157-120">Mimo że wiele komunikatów przetwarzanych jednocześnie po określeniu maksymalny stopień równoległości, która jest większa niż 1, są nadal propagowane w kolejności, w którym są odbierane.</span><span class="sxs-lookup"><span data-stu-id="1a157-120">Although multiple messages are processed simultaneously when you specify a maximum degree of parallelism that is greater than 1, they are still propagated out in the order in which they are received.</span></span>  
  
 <span data-ttu-id="1a157-121">Ponieważ <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> właściwość reprezentuje maksymalny stopień równoległości, bloku przepływu danych może być wykonywane za pomocą niższy stopień równoległości nie określisz.</span><span class="sxs-lookup"><span data-stu-id="1a157-121">Because the <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> property represents the maximum degree of parallelism, the dataflow block might execute with a lesser degree of parallelism than you specify.</span></span> <span data-ttu-id="1a157-122">W bloku przepływu danych można użyć niższy stopień równoległości do swoich wymagań funkcjonalnych lub konto z powodu braku dostępnych zasobów systemowych.</span><span class="sxs-lookup"><span data-stu-id="1a157-122">The dataflow block can use a lesser degree of parallelism to meet its functional requirements or to account for a lack of available system resources.</span></span> <span data-ttu-id="1a157-123">Bloku przepływu danych nigdy nie wybierze większy stopień równoległości nie określisz.</span><span class="sxs-lookup"><span data-stu-id="1a157-123">A dataflow block never chooses a greater degree of parallelism than you specify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a157-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1a157-124">See Also</span></span>  
 [<span data-ttu-id="1a157-125">Przepływ danych</span><span class="sxs-lookup"><span data-stu-id="1a157-125">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
