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
ms.openlocfilehash: db23b424d4357ad94b8b0de66ca71726b765321e
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44182976"
---
# <a name="how-to-use-anonymous-pipes-for-local-interprocess-communication"></a><span data-ttu-id="1c2fa-102">Porady: stosowanie anonimowych potoków do lokalnej komunikacji międzyprocesowej</span><span class="sxs-lookup"><span data-stu-id="1c2fa-102">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>
<span data-ttu-id="1c2fa-103">Anonimowe potoki zapewniają komunikację międzyprocesorową na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="1c2fa-103">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="1c2fa-104">One oferuje mniej funkcji niż nazwane potoki, ale wymagają również mniejsze obciążenie.</span><span class="sxs-lookup"><span data-stu-id="1c2fa-104">They offer less functionality than named pipes, but also require less overhead.</span></span> <span data-ttu-id="1c2fa-105">Za pomocą potoków anonimowych ułatwiają komunikację międzyprocesorową na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="1c2fa-105">You can use anonymous pipes to make interprocess communication on a local computer easier.</span></span> <span data-ttu-id="1c2fa-106">Anonimowe potoki nie można używać do komunikacji za pośrednictwem sieci.</span><span class="sxs-lookup"><span data-stu-id="1c2fa-106">You cannot use anonymous pipes for communication over a network.</span></span>  
  
 <span data-ttu-id="1c2fa-107">Aby zaimplementować potoki anonimowe, użyj <xref:System.IO.Pipes.AnonymousPipeServerStream> i <xref:System.IO.Pipes.AnonymousPipeClientStream> klasy.</span><span class="sxs-lookup"><span data-stu-id="1c2fa-107">To implement anonymous pipes, use the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c2fa-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="1c2fa-108">Example</span></span>  
 <span data-ttu-id="1c2fa-109">W poniższym przykładzie pokazano sposób wysyłania ciąg z procesu nadrzędnego do procesu podrzędnego, za pomocą potoków anonimowych.</span><span class="sxs-lookup"><span data-stu-id="1c2fa-109">The following example demonstrates a way to send a string from a parent process to a child process using anonymous pipes.</span></span> <span data-ttu-id="1c2fa-110">Ten przykład tworzy <xref:System.IO.Pipes.AnonymousPipeServerStream> obiektu w proces nadrzędny <xref:System.IO.Pipes.PipeDirection> wartość <xref:System.IO.Pipes.PipeDirection.Out>.</span><span class="sxs-lookup"><span data-stu-id="1c2fa-110">This example creates an <xref:System.IO.Pipes.AnonymousPipeServerStream> object in a parent process with a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.Out>.</span></span> <span data-ttu-id="1c2fa-111">Proces nadrzędny następnie tworzy proces podrzędny przy użyciu dojścia klienta w celu utworzenia <xref:System.IO.Pipes.AnonymousPipeClientStream> obiektu.</span><span class="sxs-lookup"><span data-stu-id="1c2fa-111">The parent process then creates a child process by using a client handle to create an <xref:System.IO.Pipes.AnonymousPipeClientStream> object.</span></span> <span data-ttu-id="1c2fa-112">Proces podrzędny ma <xref:System.IO.Pipes.PipeDirection> wartość <xref:System.IO.Pipes.PipeDirection.In>.</span><span class="sxs-lookup"><span data-stu-id="1c2fa-112">The child process has a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.In>.</span></span>  
  
 <span data-ttu-id="1c2fa-113">Proces nadrzędny wysyła następnie ciąg dostarczone przez użytkownika do procesu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="1c2fa-113">The parent process then sends a user-supplied string to the child process.</span></span> <span data-ttu-id="1c2fa-114">Ten ciąg jest wyświetlana w konsoli w procesu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="1c2fa-114">The string is displayed to the console in the child process.</span></span>  
  
 <span data-ttu-id="1c2fa-115">Poniższy przykład przedstawia proces serwera.</span><span class="sxs-lookup"><span data-stu-id="1c2fa-115">The following example shows the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/vb/program.vb#01)]  
  
## <a name="example"></a><span data-ttu-id="1c2fa-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="1c2fa-116">Example</span></span>  
 <span data-ttu-id="1c2fa-117">Poniższy przykład pokazuje procesu klienta.</span><span class="sxs-lookup"><span data-stu-id="1c2fa-117">The following example shows the client process.</span></span> <span data-ttu-id="1c2fa-118">Proces serwera rozpoczyna się proces klienta i zapewnia procesu dojście do klienta.</span><span class="sxs-lookup"><span data-stu-id="1c2fa-118">The server process starts the client process and gives that process a client handle.</span></span> <span data-ttu-id="1c2fa-119">Wynikowy plik wykonywalny z poziomu kodu klienta powinno się nazywać `pipeClient.exe` i skopiowany do tego samego katalogu co serwer pliku wykonywalnego przed uruchomieniem procesu serwera.</span><span class="sxs-lookup"><span data-stu-id="1c2fa-119">The resulting executable from the client code should be named `pipeClient.exe` and be copied to the same directory as the server executable before running the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/vb/program.vb#01)]  
  
## <a name="see-also"></a><span data-ttu-id="1c2fa-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1c2fa-120">See also</span></span>

- [<span data-ttu-id="1c2fa-121">Potoki</span><span class="sxs-lookup"><span data-stu-id="1c2fa-121">Pipes</span></span>](../../../docs/standard/io/pipe-operations.md)  
- [<span data-ttu-id="1c2fa-122">Instrukcje: stosowanie potoków nazwanych do sieciowej komunikacji międzyprocesowej</span><span class="sxs-lookup"><span data-stu-id="1c2fa-122">How to: Use Named Pipes for Network Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
