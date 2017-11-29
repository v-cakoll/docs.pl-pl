---
title: "Porady: stosowanie anonimowych potoków do lokalnej komunikacji międzyprocesowej"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- anonymous pipes [.NET Framework]
- parent-child communication [.NET Framework]
- pipes [.NET Framework]
- one-way communication [.NET Framework]
- local computer communication [.NET Framework], pipes
ms.assetid: e7773c77-c646-4a01-8a96-a003d59fc4c9
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f457cc91e6fbfc118e5363d1b0a8e8c2ad800748
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-anonymous-pipes-for-local-interprocess-communication"></a><span data-ttu-id="72683-102">Porady: stosowanie anonimowych potoków do lokalnej komunikacji międzyprocesowej</span><span class="sxs-lookup"><span data-stu-id="72683-102">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>
<span data-ttu-id="72683-103">Potoki anonimowe zapewnienia komunikacji międzyprocesowej na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="72683-103">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="72683-104">One oferują mniej funkcji niż nazwane potoki, ale również wymagać mniejsze koszty.</span><span class="sxs-lookup"><span data-stu-id="72683-104">They offer less functionality than named pipes, but also require less overhead.</span></span> <span data-ttu-id="72683-105">Potoki anonimowe umożliwia łatwiejsze komunikacji międzyprocesowej na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="72683-105">You can use anonymous pipes to make interprocess communication on a local computer easier.</span></span> <span data-ttu-id="72683-106">Potoki anonimowe nie można używać do komunikacji za pośrednictwem sieci.</span><span class="sxs-lookup"><span data-stu-id="72683-106">You cannot use anonymous pipes for communication over a network.</span></span>  
  
 <span data-ttu-id="72683-107">Aby zaimplementować potoki anonimowe, użyj <xref:System.IO.Pipes.AnonymousPipeServerStream> i <xref:System.IO.Pipes.AnonymousPipeClientStream> klasy.</span><span class="sxs-lookup"><span data-stu-id="72683-107">To implement anonymous pipes, use the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72683-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="72683-108">Example</span></span>  
 <span data-ttu-id="72683-109">W poniższym przykładzie pokazano sposób wysyłania ciąg z procesu nadrzędnego procesów podrzędnych za pomocą potoków anonimowych.</span><span class="sxs-lookup"><span data-stu-id="72683-109">The following example demonstrates a way to send a string from a parent process to a child process using anonymous pipes.</span></span> <span data-ttu-id="72683-110">Ten przykład tworzy <xref:System.IO.Pipes.AnonymousPipeServerStream> obiekt w ramach procesu nadrzędnego z <xref:System.IO.Pipes.PipeDirection> wartość <xref:System.IO.Pipes.PipeDirection.Out>.</span><span class="sxs-lookup"><span data-stu-id="72683-110">This example creates an <xref:System.IO.Pipes.AnonymousPipeServerStream> object in a parent process with a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.Out>.</span></span> <span data-ttu-id="72683-111">Proces nadrzędny tworzy następnie procesu podrzędnego przy użyciu dojścia klienta w celu utworzenia <xref:System.IO.Pipes.AnonymousPipeClientStream> obiektu.</span><span class="sxs-lookup"><span data-stu-id="72683-111">The parent process then creates a child process by using a client handle to create an <xref:System.IO.Pipes.AnonymousPipeClientStream> object.</span></span> <span data-ttu-id="72683-112">Proces podrzędny ma <xref:System.IO.Pipes.PipeDirection> wartość <xref:System.IO.Pipes.PipeDirection.In>.</span><span class="sxs-lookup"><span data-stu-id="72683-112">The child process has a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.In>.</span></span>  
  
 <span data-ttu-id="72683-113">Proces nadrzędny wysyła następnie ciągu podanego przez użytkownika do procesu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="72683-113">The parent process then sends a user-supplied string to the child process.</span></span> <span data-ttu-id="72683-114">Ciąg jest wyświetlana w konsoli w procesu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="72683-114">The string is displayed to the console in the child process.</span></span>  
  
 <span data-ttu-id="72683-115">W poniższym przykładzie przedstawiono proces serwera.</span><span class="sxs-lookup"><span data-stu-id="72683-115">The following example shows the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/vb/program.vb#01)]  
  
## <a name="example"></a><span data-ttu-id="72683-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="72683-116">Example</span></span>  
 <span data-ttu-id="72683-117">W poniższym przykładzie przedstawiono procesu klienta.</span><span class="sxs-lookup"><span data-stu-id="72683-117">The following example shows the client process.</span></span> <span data-ttu-id="72683-118">Proces serwera rozpoczyna proces klienta i zapewnia procesu obsługi klienta.</span><span class="sxs-lookup"><span data-stu-id="72683-118">The server process starts the client process and gives that process a client handle.</span></span> <span data-ttu-id="72683-119">Wynikowy plik wykonywalny z kodu klienta powinno być nazwanym `pipeClient.exe` i skopiowane do katalogu, co serwer pliku wykonywalnego przed uruchomieniem procesu serwera.</span><span class="sxs-lookup"><span data-stu-id="72683-119">The resulting executable from the client code should be named `pipeClient.exe` and be copied to the same directory as the server executable before running the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/vb/program.vb#01)]  
  
## <a name="see-also"></a><span data-ttu-id="72683-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="72683-120">See Also</span></span>  
 [<span data-ttu-id="72683-121">Potoki</span><span class="sxs-lookup"><span data-stu-id="72683-121">Pipes</span></span>](../../../docs/standard/io/pipe-operations.md)  
 [<span data-ttu-id="72683-122">Porady: stosowanie nazwanych potoków do sieciowej komunikacji międzyprocesowej</span><span class="sxs-lookup"><span data-stu-id="72683-122">How to: Use Named Pipes for Network Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
