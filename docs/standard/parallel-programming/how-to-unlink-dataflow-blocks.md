---
title: 'Porady: Rozłączanie bloków przepływu danych'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dataflow blocks, unlinking in TPL
- Task Parallel Library, dataflows
- TPL dataflow library, unlinking dataflow blocks
ms.assetid: 40f0208d-4618-47f7-85cf-4913d07d2d7d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ead52a55bfc45cbffc98552f3a7f4b01e1a6aa1e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-unlink-dataflow-blocks"></a><span data-ttu-id="6cac4-102">Porady: Rozłączanie bloków przepływu danych</span><span class="sxs-lookup"><span data-stu-id="6cac4-102">How to: Unlink Dataflow Blocks</span></span>
<span data-ttu-id="6cac4-103">Ten dokument zawiera opis sposobu odłączania docelowy bloku przepływu danych ze źródła.</span><span class="sxs-lookup"><span data-stu-id="6cac4-103">This document describes how to unlink a target dataflow block from its source.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a><span data-ttu-id="6cac4-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="6cac4-104">Example</span></span>  
 <span data-ttu-id="6cac4-105">Poniższy przykład tworzy trzy <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> obiekty, każdy z których wywołania `TrySolution` metodę w celu obliczenia wartości.</span><span class="sxs-lookup"><span data-stu-id="6cac4-105">The following example creates three <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objects, each of which calls the `TrySolution` method to compute a value.</span></span> <span data-ttu-id="6cac4-106">W tym przykładzie wymaga tylko wyników z pierwszego wywołania `TrySolution` aby zakończyć.</span><span class="sxs-lookup"><span data-stu-id="6cac4-106">This example requires only the result from the first call to `TrySolution` to finish.</span></span>  
  
 [!code-csharp[TPLDataflow_ReceiveAny#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_receiveany/cs/dataflowreceiveany.cs#1)]
 [!code-vb[TPLDataflow_ReceiveAny#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_receiveany/vb/dataflowreceiveany.vb#1)]  
  
 <span data-ttu-id="6cac4-107">Aby otrzymać wartość od pierwszego <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> obiektu, który zakończy, w tym przykładzie definiuje `ReceiveFromAny(T)` metody.</span><span class="sxs-lookup"><span data-stu-id="6cac4-107">To receive the value from the first <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> object that finishes, this example defines the `ReceiveFromAny(T)` method.</span></span> <span data-ttu-id="6cac4-108">`ReceiveFromAny(T)` Metoda przyjmuje tablicę <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> obiektów, a każdy z tych obiektów do łącza <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> obiektu.</span><span class="sxs-lookup"><span data-stu-id="6cac4-108">The `ReceiveFromAny(T)` method accepts an array of <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> objects and links each of these objects to a <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object.</span></span> <span data-ttu-id="6cac4-109">Jeśli używasz <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> metodę, aby połączyć źródła bloku przepływu danych bloku docelowego, źródłowego propaguje komunikatów do obiektu docelowego, wraz ze wzrostem dostępności danych.</span><span class="sxs-lookup"><span data-stu-id="6cac4-109">When you use the <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> method to link a source dataflow block to a target block, the source propagates messages to the target as data becomes available.</span></span> <span data-ttu-id="6cac4-110">Ponieważ <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> klasy akceptuje tylko pierwszy komunikat, który ma jej na liście, `ReceiveFromAny(T)` generuje wyniku przez wywołanie metody <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6cac4-110">Because the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> class accepts only the first message that it is offered, the `ReceiveFromAny(T)` method produces its result by calling the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> method.</span></span> <span data-ttu-id="6cac4-111">Daje to pierwszy komunikat, który jest oferowana <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> obiektu.</span><span class="sxs-lookup"><span data-stu-id="6cac4-111">This produces the first message that is offered to the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object.</span></span> <span data-ttu-id="6cac4-112"><xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> Metoda ma zastąpionej wersji, która przyjmuje <xref:System.Boolean> parametru `unlinkAfterOne` , jeśli jest równa `True`, powoduje, że blok źródła, aby odłączyć element docelowy, gdy element docelowy otrzyma jeden komunikat ze źródła.</span><span class="sxs-lookup"><span data-stu-id="6cac4-112">The <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> method has an overloaded version that takes a <xref:System.Boolean> parameter, `unlinkAfterOne` that, when it is set to `True`, instructs the source block to unlink from the target after the target receives one message from the source.</span></span> <span data-ttu-id="6cac4-113">Ważne jest, aby <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> obiekt, aby odłączyć od źródła, ponieważ relacja między tablicy źródeł i <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> obiekt nie jest już wymagane po <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> obiekt odbiera wiadomości.</span><span class="sxs-lookup"><span data-stu-id="6cac4-113">It is important for the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object to unlink from its sources because the relationship between the array of sources and the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object is no longer required after the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object receives a message.</span></span>  
  
 <span data-ttu-id="6cac4-114">Aby włączyć pozostałe wywołania do `TrySolution` kończy się po jednej z nich oblicza wartość, `TrySolution` ma metodę <xref:System.Threading.CancellationToken> obiekt, który jest anulowane po wywołaniu `ReceiveFromAny(T)` zwraca.</span><span class="sxs-lookup"><span data-stu-id="6cac4-114">To enable the remaining calls to `TrySolution` to end after one of them computes a value, the `TrySolution` method takes a <xref:System.Threading.CancellationToken> object that is canceled after the call to `ReceiveFromAny(T)` returns.</span></span> <span data-ttu-id="6cac4-115"><xref:System.Threading.SpinWait.SpinUntil%2A> Metoda zwraca, kiedy to <xref:System.Threading.CancellationToken> obiektu została anulowana.</span><span class="sxs-lookup"><span data-stu-id="6cac4-115">The <xref:System.Threading.SpinWait.SpinUntil%2A> method returns when this <xref:System.Threading.CancellationToken> object is canceled.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6cac4-116">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="6cac4-116">Compiling the Code</span></span>  
 <span data-ttu-id="6cac4-117">Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `DataflowReceiveAny.cs` (`DataflowReceiveAny.vb` w języku Visual Basic), a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6cac4-117">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DataflowReceiveAny.cs` (`DataflowReceiveAny.vb` for Visual Basic), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 <span data-ttu-id="6cac4-118">Visual C#</span><span class="sxs-lookup"><span data-stu-id="6cac4-118">Visual C#</span></span>  
  
 <span data-ttu-id="6cac4-119">**CSC.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.cs**</span><span class="sxs-lookup"><span data-stu-id="6cac4-119">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.cs**</span></span>  
  
 <span data-ttu-id="6cac4-120">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6cac4-120">Visual Basic</span></span>  
  
 <span data-ttu-id="6cac4-121">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.vb**</span><span class="sxs-lookup"><span data-stu-id="6cac4-121">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.vb**</span></span>  

## <a name="see-also"></a><span data-ttu-id="6cac4-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6cac4-122">See Also</span></span>  
 [<span data-ttu-id="6cac4-123">Przepływ danych</span><span class="sxs-lookup"><span data-stu-id="6cac4-123">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
