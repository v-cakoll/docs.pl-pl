---
title: Operacje potokowe w oprogramowaniu .NET Framework
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipes [.NET Framework]
- pipe operations [.NET Framework]
- interprocess communication [.NET Framework], pipes
- I/O [.NET Framework], pipes
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 68c1ad34952ee4d20dbf56aa8ca437a3f99db751
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="pipe-operations-in-the-net-framework"></a><span data-ttu-id="43414-102">Operacje potokowe w oprogramowaniu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="43414-102">Pipe Operations in the .NET Framework</span></span>
<span data-ttu-id="43414-103">Potoki umożliwiają do komunikacji międzyprocesowej.</span><span class="sxs-lookup"><span data-stu-id="43414-103">Pipes provide a means for interprocess communication.</span></span> <span data-ttu-id="43414-104">Istnieją dwa typy potoków:</span><span class="sxs-lookup"><span data-stu-id="43414-104">There are two types of pipes:</span></span>  
  
-   <span data-ttu-id="43414-105">Potoki anonimowe.</span><span class="sxs-lookup"><span data-stu-id="43414-105">Anonymous pipes.</span></span>  
  
     <span data-ttu-id="43414-106">Potoki anonimowe zapewnienia komunikacji międzyprocesowej na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="43414-106">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="43414-107">Potoki anonimowe wymagają mniejsze koszty niż nazwane potoki, ale oferuje ograniczonych usług.</span><span class="sxs-lookup"><span data-stu-id="43414-107">Anonymous pipes require less overhead than named pipes but offer limited services.</span></span> <span data-ttu-id="43414-108">Potoki anonimowe są jednokierunkowe i nie można używać w sieci.</span><span class="sxs-lookup"><span data-stu-id="43414-108">Anonymous pipes are one-way and cannot be used over a network.</span></span> <span data-ttu-id="43414-109">Obsługuje tylko jeden serwer wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="43414-109">They support only a single server instance.</span></span> <span data-ttu-id="43414-110">Potoki anonimowe są przydatne w przypadku komunikacji między wątkami lub między procesami nadrzędnych i podrzędnych, których dojścia potoku mogą być łatwo przekazywane do procesu podrzędnego podczas jego tworzenia.</span><span class="sxs-lookup"><span data-stu-id="43414-110">Anonymous pipes are useful for communication between threads, or between parent and child processes where the pipe handles can be easily passed to the child process when it is created.</span></span>  
  
     <span data-ttu-id="43414-111">W programie .NET Framework potoków anonimowych wdrożyć przy użyciu <xref:System.IO.Pipes.AnonymousPipeServerStream> i <xref:System.IO.Pipes.AnonymousPipeClientStream> klasy.</span><span class="sxs-lookup"><span data-stu-id="43414-111">In the .NET Framework, you implement anonymous pipes by using the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="43414-112">Zobacz [porady: stosowanie anonimowych potoków do lokalnej komunikacji międzyprocesowej](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span><span class="sxs-lookup"><span data-stu-id="43414-112">See [How to: Use Anonymous Pipes for Local Interprocess Communication](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span></span>  
  
-   <span data-ttu-id="43414-113">Nazwane potoki.</span><span class="sxs-lookup"><span data-stu-id="43414-113">Named pipes.</span></span>  
  
     <span data-ttu-id="43414-114">Nazwane potoki zapewniają komunikację międzyprocesorową pomiędzy serwerem potoku i jednym lub kilkoma klientami potoku.</span><span class="sxs-lookup"><span data-stu-id="43414-114">Named pipes provide interprocess communication between a pipe server and one or more pipe clients.</span></span> <span data-ttu-id="43414-115">Nazwane potoki mogą być jednokierunkowe lub dwukierunkowego.</span><span class="sxs-lookup"><span data-stu-id="43414-115">Named pipes can be one-way or duplex.</span></span> <span data-ttu-id="43414-116">Obsługuje komunikacja oparta na komunikat, a Zezwalaj wielu klientom na łączenie się jednocześnie do procesu serwera przy użyciu tej samej nazwy potoku.</span><span class="sxs-lookup"><span data-stu-id="43414-116">They support message-based communication and allow multiple clients to connect simultaneously to the server process using the same pipe name.</span></span> <span data-ttu-id="43414-117">Nazwane potoki obsługują także personifikacji, dzięki czemu łączącego procesów własnych uprawnień na serwerach zdalnych.</span><span class="sxs-lookup"><span data-stu-id="43414-117">Named pipes also support impersonation, which enables connecting processes to use their own permissions on remote servers.</span></span>  
  
     <span data-ttu-id="43414-118">W programie .NET Framework nazwanych potoków można wdrożyć przy użyciu <xref:System.IO.Pipes.NamedPipeServerStream> i <xref:System.IO.Pipes.NamedPipeClientStream> klasy.</span><span class="sxs-lookup"><span data-stu-id="43414-118">In the .NET Framework, you implement named pipes by using the <xref:System.IO.Pipes.NamedPipeServerStream> and <xref:System.IO.Pipes.NamedPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="43414-119">Zobacz [porady: stosowanie nazwanych potoków do sieciowej komunikacji międzyprocesowej](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).</span><span class="sxs-lookup"><span data-stu-id="43414-119">See [How to: Use Named Pipes for Network Interprocess Communication](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43414-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="43414-120">See Also</span></span>  
 [<span data-ttu-id="43414-121">Plik i strumienia I-O</span><span class="sxs-lookup"><span data-stu-id="43414-121">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)  
 [<span data-ttu-id="43414-122">Instrukcje: stosowanie potoków anonimowych do lokalnej komunikacji międzyprocesowej</span><span class="sxs-lookup"><span data-stu-id="43414-122">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)  
 [<span data-ttu-id="43414-123">Instrukcje: stosowanie potoków nazwanych do sieciowej komunikacji międzyprocesowej</span><span class="sxs-lookup"><span data-stu-id="43414-123">How to: Use Named Pipes for Network Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
