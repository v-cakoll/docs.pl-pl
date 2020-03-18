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
ms.openlocfilehash: ea4aee60d090a56eb0cf3f2a81c1b05c04806d4b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "77627997"
---
# <a name="how-to-use-anonymous-pipes-for-local-interprocess-communication"></a><span data-ttu-id="745f9-102">Porady: stosowanie anonimowych potoków do lokalnej komunikacji międzyprocesowej</span><span class="sxs-lookup"><span data-stu-id="745f9-102">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>
<span data-ttu-id="745f9-103">Anonimowe potoki zapewniają komunikację międzyprocesową na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="745f9-103">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="745f9-104">Oferują one mniej funkcji niż nazwane potoki, ale również wymagają mniej narzutów.</span><span class="sxs-lookup"><span data-stu-id="745f9-104">They offer less functionality than named pipes, but also require less overhead.</span></span> <span data-ttu-id="745f9-105">Za pomocą anonimowych potoków można ułatwić komunikację międzyprocesową na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="745f9-105">You can use anonymous pipes to make interprocess communication on a local computer easier.</span></span> <span data-ttu-id="745f9-106">Nie można używać anonimowych potoków do komunikacji za pomocą sieci.</span><span class="sxs-lookup"><span data-stu-id="745f9-106">You cannot use anonymous pipes for communication over a network.</span></span>  
  
 <span data-ttu-id="745f9-107">Aby zaimplementować anonimowe <xref:System.IO.Pipes.AnonymousPipeServerStream> <xref:System.IO.Pipes.AnonymousPipeClientStream> potoki, należy użyć i klas.</span><span class="sxs-lookup"><span data-stu-id="745f9-107">To implement anonymous pipes, use the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="745f9-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="745f9-108">Example</span></span>  
 <span data-ttu-id="745f9-109">W poniższym przykładzie przedstawiono sposób wysyłania ciągu z procesu nadrzędnego do procesu podrzędnego przy użyciu anonimowych potoków.</span><span class="sxs-lookup"><span data-stu-id="745f9-109">The following example demonstrates a way to send a string from a parent process to a child process using anonymous pipes.</span></span> <span data-ttu-id="745f9-110">W tym <xref:System.IO.Pipes.AnonymousPipeServerStream> przykładzie tworzy obiekt w <xref:System.IO.Pipes.PipeDirection> procesie <xref:System.IO.Pipes.PipeDirection.Out>nadrzędnym o wartości .</span><span class="sxs-lookup"><span data-stu-id="745f9-110">This example creates an <xref:System.IO.Pipes.AnonymousPipeServerStream> object in a parent process with a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.Out>.</span></span> <span data-ttu-id="745f9-111">Proces nadrzędny następnie tworzy proces podrzędny przy <xref:System.IO.Pipes.AnonymousPipeClientStream> użyciu dojścia klienta do utworzenia obiektu.</span><span class="sxs-lookup"><span data-stu-id="745f9-111">The parent process then creates a child process by using a client handle to create an <xref:System.IO.Pipes.AnonymousPipeClientStream> object.</span></span> <span data-ttu-id="745f9-112">Proces podrzędny <xref:System.IO.Pipes.PipeDirection> ma <xref:System.IO.Pipes.PipeDirection.In>wartość .</span><span class="sxs-lookup"><span data-stu-id="745f9-112">The child process has a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.In>.</span></span>  
  
 <span data-ttu-id="745f9-113">Następnie proces nadrzędny wysyła ciąg dostarczony przez użytkownika do procesu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="745f9-113">The parent process then sends a user-supplied string to the child process.</span></span> <span data-ttu-id="745f9-114">Ciąg jest wyświetlany do konsoli w procesie podrzędnym.</span><span class="sxs-lookup"><span data-stu-id="745f9-114">The string is displayed to the console in the child process.</span></span>  
  
 <span data-ttu-id="745f9-115">W poniższym przykładzie przedstawiono proces serwera.</span><span class="sxs-lookup"><span data-stu-id="745f9-115">The following example shows the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/vb/program.vb#01)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]
  
## <a name="example"></a><span data-ttu-id="745f9-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="745f9-116">Example</span></span>  
 <span data-ttu-id="745f9-117">W poniższym przykładzie przedstawiono proces klienta.</span><span class="sxs-lookup"><span data-stu-id="745f9-117">The following example shows the client process.</span></span> <span data-ttu-id="745f9-118">Proces serwera uruchamia proces klienta i daje temu procesowi dojście klienta.</span><span class="sxs-lookup"><span data-stu-id="745f9-118">The server process starts the client process and gives that process a client handle.</span></span> <span data-ttu-id="745f9-119">Wynikowy plik wykonywalny z `pipeClient.exe` kodu klienta powinien zostać nazwany i skopiowany do tego samego katalogu co plik wykonywalny serwera przed uruchomieniem procesu serwera.</span><span class="sxs-lookup"><span data-stu-id="745f9-119">The resulting executable from the client code should be named `pipeClient.exe` and be copied to the same directory as the server executable before running the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/vb/program.vb#01)]  
  
## <a name="see-also"></a><span data-ttu-id="745f9-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="745f9-120">See also</span></span>

- [<span data-ttu-id="745f9-121">Potoki</span><span class="sxs-lookup"><span data-stu-id="745f9-121">Pipes</span></span>](../../../docs/standard/io/pipe-operations.md)
- [<span data-ttu-id="745f9-122">Instrukcje: stosowanie potoków nazwanych do sieciowej komunikacji międzyprocesowej</span><span class="sxs-lookup"><span data-stu-id="745f9-122">How to: Use Named Pipes for Network Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
