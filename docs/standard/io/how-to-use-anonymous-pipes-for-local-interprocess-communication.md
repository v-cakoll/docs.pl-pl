---
title: 'Porady: stosowanie anonimowych potoków do lokalnej komunikacji międzyprocesowej'
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 846d97871492b89026d50dd89b78a28263863cce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-anonymous-pipes-for-local-interprocess-communication"></a><span data-ttu-id="272cf-102">Porady: stosowanie anonimowych potoków do lokalnej komunikacji międzyprocesowej</span><span class="sxs-lookup"><span data-stu-id="272cf-102">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>
<span data-ttu-id="272cf-103">Potoki anonimowe zapewnienia komunikacji międzyprocesowej na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="272cf-103">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="272cf-104">One oferują mniej funkcji niż nazwane potoki, ale również wymagać mniejsze koszty.</span><span class="sxs-lookup"><span data-stu-id="272cf-104">They offer less functionality than named pipes, but also require less overhead.</span></span> <span data-ttu-id="272cf-105">Potoki anonimowe umożliwia łatwiejsze komunikacji międzyprocesowej na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="272cf-105">You can use anonymous pipes to make interprocess communication on a local computer easier.</span></span> <span data-ttu-id="272cf-106">Potoki anonimowe nie można używać do komunikacji za pośrednictwem sieci.</span><span class="sxs-lookup"><span data-stu-id="272cf-106">You cannot use anonymous pipes for communication over a network.</span></span>  
  
 <span data-ttu-id="272cf-107">Aby zaimplementować potoki anonimowe, użyj <xref:System.IO.Pipes.AnonymousPipeServerStream> i <xref:System.IO.Pipes.AnonymousPipeClientStream> klasy.</span><span class="sxs-lookup"><span data-stu-id="272cf-107">To implement anonymous pipes, use the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="272cf-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="272cf-108">Example</span></span>  
 <span data-ttu-id="272cf-109">W poniższym przykładzie pokazano sposób wysyłania ciąg z procesu nadrzędnego procesów podrzędnych za pomocą potoków anonimowych.</span><span class="sxs-lookup"><span data-stu-id="272cf-109">The following example demonstrates a way to send a string from a parent process to a child process using anonymous pipes.</span></span> <span data-ttu-id="272cf-110">Ten przykład tworzy <xref:System.IO.Pipes.AnonymousPipeServerStream> obiekt w ramach procesu nadrzędnego z <xref:System.IO.Pipes.PipeDirection> wartość <xref:System.IO.Pipes.PipeDirection.Out>.</span><span class="sxs-lookup"><span data-stu-id="272cf-110">This example creates an <xref:System.IO.Pipes.AnonymousPipeServerStream> object in a parent process with a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.Out>.</span></span> <span data-ttu-id="272cf-111">Proces nadrzędny tworzy następnie procesu podrzędnego przy użyciu dojścia klienta w celu utworzenia <xref:System.IO.Pipes.AnonymousPipeClientStream> obiektu.</span><span class="sxs-lookup"><span data-stu-id="272cf-111">The parent process then creates a child process by using a client handle to create an <xref:System.IO.Pipes.AnonymousPipeClientStream> object.</span></span> <span data-ttu-id="272cf-112">Proces podrzędny ma <xref:System.IO.Pipes.PipeDirection> wartość <xref:System.IO.Pipes.PipeDirection.In>.</span><span class="sxs-lookup"><span data-stu-id="272cf-112">The child process has a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.In>.</span></span>  
  
 <span data-ttu-id="272cf-113">Proces nadrzędny wysyła następnie ciągu podanego przez użytkownika do procesu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="272cf-113">The parent process then sends a user-supplied string to the child process.</span></span> <span data-ttu-id="272cf-114">Ciąg jest wyświetlana w konsoli w procesu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="272cf-114">The string is displayed to the console in the child process.</span></span>  
  
 <span data-ttu-id="272cf-115">W poniższym przykładzie przedstawiono proces serwera.</span><span class="sxs-lookup"><span data-stu-id="272cf-115">The following example shows the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/vb/program.vb#01)]  
  
## <a name="example"></a><span data-ttu-id="272cf-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="272cf-116">Example</span></span>  
 <span data-ttu-id="272cf-117">W poniższym przykładzie przedstawiono procesu klienta.</span><span class="sxs-lookup"><span data-stu-id="272cf-117">The following example shows the client process.</span></span> <span data-ttu-id="272cf-118">Proces serwera rozpoczyna proces klienta i zapewnia procesu obsługi klienta.</span><span class="sxs-lookup"><span data-stu-id="272cf-118">The server process starts the client process and gives that process a client handle.</span></span> <span data-ttu-id="272cf-119">Wynikowy plik wykonywalny z kodu klienta powinno być nazwanym `pipeClient.exe` i skopiowane do katalogu, co serwer pliku wykonywalnego przed uruchomieniem procesu serwera.</span><span class="sxs-lookup"><span data-stu-id="272cf-119">The resulting executable from the client code should be named `pipeClient.exe` and be copied to the same directory as the server executable before running the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/vb/program.vb#01)]  
  
## <a name="see-also"></a><span data-ttu-id="272cf-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="272cf-120">See Also</span></span>  
 [<span data-ttu-id="272cf-121">Potoki</span><span class="sxs-lookup"><span data-stu-id="272cf-121">Pipes</span></span>](../../../docs/standard/io/pipe-operations.md)  
 [<span data-ttu-id="272cf-122">Instrukcje: stosowanie potoków nazwanych do sieciowej komunikacji międzyprocesowej</span><span class="sxs-lookup"><span data-stu-id="272cf-122">How to: Use Named Pipes for Network Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
