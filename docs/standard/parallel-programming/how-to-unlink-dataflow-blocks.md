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
ms.openlocfilehash: 65d42597c572a85a95f9e2b4407df42c6fb7bb3d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43407894"
---
# <a name="how-to-unlink-dataflow-blocks"></a><span data-ttu-id="43bf5-102">Porady: Rozłączanie bloków przepływu danych</span><span class="sxs-lookup"><span data-stu-id="43bf5-102">How to: Unlink Dataflow Blocks</span></span>
<span data-ttu-id="43bf5-103">Ten dokument zawiera opis sposobu odłączania docelowej bloku przepływu danych ze źródła.</span><span class="sxs-lookup"><span data-stu-id="43bf5-103">This document describes how to unlink a target dataflow block from its source.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a><span data-ttu-id="43bf5-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="43bf5-104">Example</span></span>  
 <span data-ttu-id="43bf5-105">Poniższy przykład tworzy trzy <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> obiektów, każdy która wywołuje metodę `TrySolution` metodę w celu obliczenia wartości.</span><span class="sxs-lookup"><span data-stu-id="43bf5-105">The following example creates three <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objects, each of which calls the `TrySolution` method to compute a value.</span></span> <span data-ttu-id="43bf5-106">W tym przykładzie wymaga tylko wyniki z pierwszym wywołaniu `TrySolution` na zakończenie.</span><span class="sxs-lookup"><span data-stu-id="43bf5-106">This example requires only the result from the first call to `TrySolution` to finish.</span></span>  
  
 [!code-csharp[TPLDataflow_ReceiveAny#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_receiveany/cs/dataflowreceiveany.cs#1)]
 [!code-vb[TPLDataflow_ReceiveAny#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_receiveany/vb/dataflowreceiveany.vb#1)]  
  
 <span data-ttu-id="43bf5-107">Aby otrzymać wartość od pierwszego <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> obiektu, który zakończy się, w tym przykładzie definiuje `ReceiveFromAny(T)` metody.</span><span class="sxs-lookup"><span data-stu-id="43bf5-107">To receive the value from the first <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> object that finishes, this example defines the `ReceiveFromAny(T)` method.</span></span> <span data-ttu-id="43bf5-108">`ReceiveFromAny(T)` Metoda przyjmuje tablicę <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> obiektów i każdy z tych obiektów do łączy <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> obiektu.</span><span class="sxs-lookup"><span data-stu-id="43bf5-108">The `ReceiveFromAny(T)` method accepts an array of <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> objects and links each of these objects to a <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object.</span></span> <span data-ttu-id="43bf5-109">Kiedy używasz <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> metodę, aby połączyć bloku przepływu danych źródłowych do bloku docelowego, źródłowego propaguje komunikatów do obiektu docelowego danych staje się dostępna.</span><span class="sxs-lookup"><span data-stu-id="43bf5-109">When you use the <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> method to link a source dataflow block to a target block, the source propagates messages to the target as data becomes available.</span></span> <span data-ttu-id="43bf5-110">Ponieważ <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> klasy akceptuje tylko pierwszy komunikat, który jest dostępna, `ReceiveFromAny(T)` generuje jej wynik, wywołując <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="43bf5-110">Because the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> class accepts only the first message that it is offered, the `ReceiveFromAny(T)` method produces its result by calling the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> method.</span></span> <span data-ttu-id="43bf5-111">Daje to pierwszy komunikat, który jest oferowany <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> obiektu.</span><span class="sxs-lookup"><span data-stu-id="43bf5-111">This produces the first message that is offered to the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object.</span></span> <span data-ttu-id="43bf5-112"><xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> Metoda ma przeciążona wersja, która przyjmuje <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions> obiekt z <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions.MaxMessages> właściwości, gdy jest równa `1`, powoduje, że blok źródłowy można odłączyć od obiektu docelowego, gdy docelowym otrzyma jeden komunikat ze źródła .</span><span class="sxs-lookup"><span data-stu-id="43bf5-112">The <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> method has an overloaded version that takes an <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions> object with a <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions.MaxMessages> property that, when it is set to `1`, instructs the source block to unlink from the target after the target receives one message from the source.</span></span> <span data-ttu-id="43bf5-113">Ważne jest, aby <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> obiektu można odłączyć od źródła, ponieważ relacja między tablicą źródeł i <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> obiekt nie jest już wymagane po <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> obiekt otrzymuje komunikat.</span><span class="sxs-lookup"><span data-stu-id="43bf5-113">It is important for the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object to unlink from its sources because the relationship between the array of sources and the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object is no longer required after the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object receives a message.</span></span>  
  
 <span data-ttu-id="43bf5-114">Aby włączyć pozostałe wywołania do `TrySolution` kończy się po jednej z nich oblicza wartość `TrySolution` metoda przyjmuje <xref:System.Threading.CancellationToken> obiektów, które zostało anulowane po wywołaniu `ReceiveFromAny(T)` zwraca.</span><span class="sxs-lookup"><span data-stu-id="43bf5-114">To enable the remaining calls to `TrySolution` to end after one of them computes a value, the `TrySolution` method takes a <xref:System.Threading.CancellationToken> object that is canceled after the call to `ReceiveFromAny(T)` returns.</span></span> <span data-ttu-id="43bf5-115"><xref:System.Threading.SpinWait.SpinUntil%2A> Metoda zwraca, kiedy to <xref:System.Threading.CancellationToken> obiektu zostanie anulowane.</span><span class="sxs-lookup"><span data-stu-id="43bf5-115">The <xref:System.Threading.SpinWait.SpinUntil%2A> method returns when this <xref:System.Threading.CancellationToken> object is canceled.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="43bf5-116">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="43bf5-116">Compiling the Code</span></span>  
 <span data-ttu-id="43bf5-117">Kopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `DataflowReceiveAny.cs` (`DataflowReceiveAny.vb` dla języka Visual Basic), a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="43bf5-117">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DataflowReceiveAny.cs` (`DataflowReceiveAny.vb` for Visual Basic), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 <span data-ttu-id="43bf5-118">Visual C#</span><span class="sxs-lookup"><span data-stu-id="43bf5-118">Visual C#</span></span>  
  
 <span data-ttu-id="43bf5-119">**CSC.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.cs**</span><span class="sxs-lookup"><span data-stu-id="43bf5-119">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.cs**</span></span>  
  
 <span data-ttu-id="43bf5-120">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="43bf5-120">Visual Basic</span></span>  
  
 <span data-ttu-id="43bf5-121">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.vb**</span><span class="sxs-lookup"><span data-stu-id="43bf5-121">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.vb**</span></span>  

## <a name="see-also"></a><span data-ttu-id="43bf5-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="43bf5-122">See Also</span></span>  
 [<span data-ttu-id="43bf5-123">Przepływ danych</span><span class="sxs-lookup"><span data-stu-id="43bf5-123">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
