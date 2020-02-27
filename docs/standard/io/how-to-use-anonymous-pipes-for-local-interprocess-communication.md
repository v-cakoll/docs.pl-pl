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
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627997"
---
# <a name="how-to-use-anonymous-pipes-for-local-interprocess-communication"></a><span data-ttu-id="176d7-102">Porady: stosowanie anonimowych potoków do lokalnej komunikacji międzyprocesowej</span><span class="sxs-lookup"><span data-stu-id="176d7-102">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>
<span data-ttu-id="176d7-103">Potoki anonimowe zapewniają komunikację międzyprocesową na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="176d7-103">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="176d7-104">Oferują one mniej funkcji niż nazwane potoki, ale również wymagają mniejszego obciążenia.</span><span class="sxs-lookup"><span data-stu-id="176d7-104">They offer less functionality than named pipes, but also require less overhead.</span></span> <span data-ttu-id="176d7-105">Można używać potoków anonimowych, aby ułatwić komunikację międzyprocesową na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="176d7-105">You can use anonymous pipes to make interprocess communication on a local computer easier.</span></span> <span data-ttu-id="176d7-106">Nie można używać potoków anonimowych do komunikacji za pośrednictwem sieci.</span><span class="sxs-lookup"><span data-stu-id="176d7-106">You cannot use anonymous pipes for communication over a network.</span></span>  
  
 <span data-ttu-id="176d7-107">Aby zaimplementować anonimowe potoki, użyj klas <xref:System.IO.Pipes.AnonymousPipeServerStream> i <xref:System.IO.Pipes.AnonymousPipeClientStream>.</span><span class="sxs-lookup"><span data-stu-id="176d7-107">To implement anonymous pipes, use the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="176d7-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="176d7-108">Example</span></span>  
 <span data-ttu-id="176d7-109">Poniższy przykład ilustruje sposób wysyłania ciągu z procesu nadrzędnego do procesu podrzędnego przy użyciu potoków anonimowych.</span><span class="sxs-lookup"><span data-stu-id="176d7-109">The following example demonstrates a way to send a string from a parent process to a child process using anonymous pipes.</span></span> <span data-ttu-id="176d7-110">Ten przykład tworzy obiekt <xref:System.IO.Pipes.AnonymousPipeServerStream> w procesie nadrzędnym z <xref:System.IO.Pipes.PipeDirection> wartością <xref:System.IO.Pipes.PipeDirection.Out>.</span><span class="sxs-lookup"><span data-stu-id="176d7-110">This example creates an <xref:System.IO.Pipes.AnonymousPipeServerStream> object in a parent process with a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.Out>.</span></span> <span data-ttu-id="176d7-111">Następnie proces nadrzędny tworzy proces podrzędny przy użyciu dojścia klienta do tworzenia obiektu <xref:System.IO.Pipes.AnonymousPipeClientStream>.</span><span class="sxs-lookup"><span data-stu-id="176d7-111">The parent process then creates a child process by using a client handle to create an <xref:System.IO.Pipes.AnonymousPipeClientStream> object.</span></span> <span data-ttu-id="176d7-112">Proces podrzędny ma <xref:System.IO.Pipes.PipeDirection> wartość <xref:System.IO.Pipes.PipeDirection.In>.</span><span class="sxs-lookup"><span data-stu-id="176d7-112">The child process has a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.In>.</span></span>  
  
 <span data-ttu-id="176d7-113">Następnie proces nadrzędny wysyła ciąg dostarczony przez użytkownika do procesu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="176d7-113">The parent process then sends a user-supplied string to the child process.</span></span> <span data-ttu-id="176d7-114">Ten ciąg jest wyświetlany w konsoli w procesie podrzędnym.</span><span class="sxs-lookup"><span data-stu-id="176d7-114">The string is displayed to the console in the child process.</span></span>  
  
 <span data-ttu-id="176d7-115">Poniższy przykład przedstawia proces serwera.</span><span class="sxs-lookup"><span data-stu-id="176d7-115">The following example shows the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/vb/program.vb#01)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]
  
## <a name="example"></a><span data-ttu-id="176d7-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="176d7-116">Example</span></span>  
 <span data-ttu-id="176d7-117">Poniższy przykład przedstawia proces klienta.</span><span class="sxs-lookup"><span data-stu-id="176d7-117">The following example shows the client process.</span></span> <span data-ttu-id="176d7-118">Proces serwera uruchamia proces klienta i zapewnia, że proces obsługi klienta.</span><span class="sxs-lookup"><span data-stu-id="176d7-118">The server process starts the client process and gives that process a client handle.</span></span> <span data-ttu-id="176d7-119">Utworzony plik wykonywalny z kodu klienta powinien mieć nazwę `pipeClient.exe` i być kopiowany do tego samego katalogu co plik wykonywalny serwera przed uruchomieniem procesu serwera.</span><span class="sxs-lookup"><span data-stu-id="176d7-119">The resulting executable from the client code should be named `pipeClient.exe` and be copied to the same directory as the server executable before running the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/vb/program.vb#01)]  
  
## <a name="see-also"></a><span data-ttu-id="176d7-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="176d7-120">See also</span></span>

- [<span data-ttu-id="176d7-121">Potoki</span><span class="sxs-lookup"><span data-stu-id="176d7-121">Pipes</span></span>](../../../docs/standard/io/pipe-operations.md)
- [<span data-ttu-id="176d7-122">Instrukcje: stosowanie potoków nazwanych do sieciowej komunikacji międzyprocesowej</span><span class="sxs-lookup"><span data-stu-id="176d7-122">How to: Use Named Pipes for Network Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
