---
title: 'Instrukcje: Stosowanie anonimowych potoków do lokalnej komunikacji międzyprocesowej'
description: Dowiedz się, jak używać anonimowych potoków do lokalnej komunikacji międzyprocesowej na komputerze lokalnym w programie .NET. Potoki anonimowe wymagają mniej obciążenia niż potoki nazwane.
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
ms.openlocfilehash: 090a25aea4f280fc2ad00cf7777a501c475dfc66
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594806"
---
# <a name="how-to-use-anonymous-pipes-for-local-interprocess-communication"></a><span data-ttu-id="189fd-104">Instrukcje: Stosowanie anonimowych potoków do lokalnej komunikacji międzyprocesowej</span><span class="sxs-lookup"><span data-stu-id="189fd-104">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>
<span data-ttu-id="189fd-105">Potoki anonimowe zapewniają komunikację międzyprocesową na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="189fd-105">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="189fd-106">Oferują one mniej funkcji niż nazwane potoki, ale również wymagają mniejszego obciążenia.</span><span class="sxs-lookup"><span data-stu-id="189fd-106">They offer less functionality than named pipes, but also require less overhead.</span></span> <span data-ttu-id="189fd-107">Można używać potoków anonimowych, aby ułatwić komunikację międzyprocesową na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="189fd-107">You can use anonymous pipes to make interprocess communication on a local computer easier.</span></span> <span data-ttu-id="189fd-108">Nie można używać potoków anonimowych do komunikacji za pośrednictwem sieci.</span><span class="sxs-lookup"><span data-stu-id="189fd-108">You cannot use anonymous pipes for communication over a network.</span></span>  
  
 <span data-ttu-id="189fd-109">Aby zaimplementować anonimowe potoki, <xref:System.IO.Pipes.AnonymousPipeServerStream> Użyj <xref:System.IO.Pipes.AnonymousPipeClientStream> klas i.</span><span class="sxs-lookup"><span data-stu-id="189fd-109">To implement anonymous pipes, use the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="189fd-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="189fd-110">Example</span></span>  
 <span data-ttu-id="189fd-111">Poniższy przykład ilustruje sposób wysyłania ciągu z procesu nadrzędnego do procesu podrzędnego przy użyciu potoków anonimowych.</span><span class="sxs-lookup"><span data-stu-id="189fd-111">The following example demonstrates a way to send a string from a parent process to a child process using anonymous pipes.</span></span> <span data-ttu-id="189fd-112">Ten przykład tworzy <xref:System.IO.Pipes.AnonymousPipeServerStream> obiekt w procesie nadrzędnym z <xref:System.IO.Pipes.PipeDirection> wartością <xref:System.IO.Pipes.PipeDirection.Out> .</span><span class="sxs-lookup"><span data-stu-id="189fd-112">This example creates an <xref:System.IO.Pipes.AnonymousPipeServerStream> object in a parent process with a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.Out>.</span></span> <span data-ttu-id="189fd-113">Następnie proces nadrzędny tworzy proces podrzędny przy użyciu dojścia klienta do utworzenia <xref:System.IO.Pipes.AnonymousPipeClientStream> obiektu.</span><span class="sxs-lookup"><span data-stu-id="189fd-113">The parent process then creates a child process by using a client handle to create an <xref:System.IO.Pipes.AnonymousPipeClientStream> object.</span></span> <span data-ttu-id="189fd-114">Proces podrzędny ma <xref:System.IO.Pipes.PipeDirection> wartość <xref:System.IO.Pipes.PipeDirection.In> .</span><span class="sxs-lookup"><span data-stu-id="189fd-114">The child process has a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.In>.</span></span>  
  
 <span data-ttu-id="189fd-115">Następnie proces nadrzędny wysyła ciąg dostarczony przez użytkownika do procesu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="189fd-115">The parent process then sends a user-supplied string to the child process.</span></span> <span data-ttu-id="189fd-116">Ten ciąg jest wyświetlany w konsoli w procesie podrzędnym.</span><span class="sxs-lookup"><span data-stu-id="189fd-116">The string is displayed to the console in the child process.</span></span>  
  
 <span data-ttu-id="189fd-117">Poniższy przykład przedstawia proces serwera.</span><span class="sxs-lookup"><span data-stu-id="189fd-117">The following example shows the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/vb/program.vb#01)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]
  
## <a name="example"></a><span data-ttu-id="189fd-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="189fd-118">Example</span></span>  
 <span data-ttu-id="189fd-119">Poniższy przykład przedstawia proces klienta.</span><span class="sxs-lookup"><span data-stu-id="189fd-119">The following example shows the client process.</span></span> <span data-ttu-id="189fd-120">Proces serwera uruchamia proces klienta i zapewnia, że proces obsługi klienta.</span><span class="sxs-lookup"><span data-stu-id="189fd-120">The server process starts the client process and gives that process a client handle.</span></span> <span data-ttu-id="189fd-121">Utworzony plik wykonywalny z kodu klienta powinien mieć nazwę `pipeClient.exe` i być kopiowany do tego samego katalogu co plik wykonywalny serwera przed uruchomieniem procesu serwera.</span><span class="sxs-lookup"><span data-stu-id="189fd-121">The resulting executable from the client code should be named `pipeClient.exe` and be copied to the same directory as the server executable before running the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/vb/program.vb#01)]  
  
## <a name="see-also"></a><span data-ttu-id="189fd-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="189fd-122">See also</span></span>

- [<span data-ttu-id="189fd-123">Potoki</span><span class="sxs-lookup"><span data-stu-id="189fd-123">Pipes</span></span>](pipe-operations.md)
- [<span data-ttu-id="189fd-124">Instrukcje: Stosowanie nazwanych potoków do sieciowej komunikacji międzyprocesowej</span><span class="sxs-lookup"><span data-stu-id="189fd-124">How to: Use Named Pipes for Network Interprocess Communication</span></span>](how-to-use-named-pipes-for-network-interprocess-communication.md)
