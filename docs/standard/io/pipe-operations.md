---
title: Operacje potokowe w oprogramowaniu .NET Framework
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- pipes [.NET Framework]
- pipe operations [.NET Framework]
- interprocess communication [.NET Framework], pipes
- I/O [.NET Framework], pipes
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fdc12091a377a118dc533e5f299fa4833af64baf
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44081872"
---
# <a name="pipe-operations-in-the-net-framework"></a><span data-ttu-id="82861-102">Operacje potokowe w oprogramowaniu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="82861-102">Pipe Operations in the .NET Framework</span></span>
<span data-ttu-id="82861-103">Potoki zapewniają środki do komunikacji międzyprocesowej.</span><span class="sxs-lookup"><span data-stu-id="82861-103">Pipes provide a means for interprocess communication.</span></span> <span data-ttu-id="82861-104">Istnieją dwa rodzaje potoków:</span><span class="sxs-lookup"><span data-stu-id="82861-104">There are two types of pipes:</span></span>  
  
-   <span data-ttu-id="82861-105">Anonimowe potoki.</span><span class="sxs-lookup"><span data-stu-id="82861-105">Anonymous pipes.</span></span>  
  
     <span data-ttu-id="82861-106">Anonimowe potoki zapewniają komunikację międzyprocesorową na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="82861-106">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="82861-107">Anonimowe potoki wymagają mniejsze obciążenie niż nazwane potoki, ale oferują ograniczonej liczbie usług.</span><span class="sxs-lookup"><span data-stu-id="82861-107">Anonymous pipes require less overhead than named pipes but offer limited services.</span></span> <span data-ttu-id="82861-108">Anonimowe potoki są jednokierunkowe i nie można używać za pośrednictwem sieci.</span><span class="sxs-lookup"><span data-stu-id="82861-108">Anonymous pipes are one-way and cannot be used over a network.</span></span> <span data-ttu-id="82861-109">Obsługują tylko jeden serwer wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="82861-109">They support only a single server instance.</span></span> <span data-ttu-id="82861-110">Anonimowe potoki są przydatne do komunikacji między wątkami lub między procesami nadrzędnymi i podrzędnymi, gdzie uchwyty potoku mogą być łatwo przekazywane do procesu podrzędnego podczas jego tworzenia.</span><span class="sxs-lookup"><span data-stu-id="82861-110">Anonymous pipes are useful for communication between threads, or between parent and child processes where the pipe handles can be easily passed to the child process when it is created.</span></span>  
  
     <span data-ttu-id="82861-111">W .NET Framework, zaimplementować anonimowych potoków przy użyciu <xref:System.IO.Pipes.AnonymousPipeServerStream> i <xref:System.IO.Pipes.AnonymousPipeClientStream> klasy.</span><span class="sxs-lookup"><span data-stu-id="82861-111">In the .NET Framework, you implement anonymous pipes by using the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="82861-112">Zobacz [porady: stosowanie potoków anonimowych do lokalnej komunikacji międzyprocesowej](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span><span class="sxs-lookup"><span data-stu-id="82861-112">See [How to: Use Anonymous Pipes for Local Interprocess Communication](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span></span>  
  
-   <span data-ttu-id="82861-113">Nazwane potoki.</span><span class="sxs-lookup"><span data-stu-id="82861-113">Named pipes.</span></span>  
  
     <span data-ttu-id="82861-114">Nazwane potoki zapewniają komunikację międzyprocesorową pomiędzy serwerem potoku i jednym lub kilkoma klientami potoku.</span><span class="sxs-lookup"><span data-stu-id="82861-114">Named pipes provide interprocess communication between a pipe server and one or more pipe clients.</span></span> <span data-ttu-id="82861-115">Nazwane potoki mogą być jednokierunkowe lub dwukierunkowego.</span><span class="sxs-lookup"><span data-stu-id="82861-115">Named pipes can be one-way or duplex.</span></span> <span data-ttu-id="82861-116">One obsługi komunikacji typu oparta na komunikatach i umożliwić wielu klientów jednocześnie nawiązać proces serwera, korzystając z tej samej nazwy potoku.</span><span class="sxs-lookup"><span data-stu-id="82861-116">They support message-based communication and allow multiple clients to connect simultaneously to the server process using the same pipe name.</span></span> <span data-ttu-id="82861-117">Nazwane potoki obsługują także personifikacji, która pozwala łączyć procesy z ich własnych uprawnień na serwerach zdalnych.</span><span class="sxs-lookup"><span data-stu-id="82861-117">Named pipes also support impersonation, which enables connecting processes to use their own permissions on remote servers.</span></span>  
  
     <span data-ttu-id="82861-118">W .NET Framework, zaimplementować nazwane potoki przy użyciu <xref:System.IO.Pipes.NamedPipeServerStream> i <xref:System.IO.Pipes.NamedPipeClientStream> klasy.</span><span class="sxs-lookup"><span data-stu-id="82861-118">In the .NET Framework, you implement named pipes by using the <xref:System.IO.Pipes.NamedPipeServerStream> and <xref:System.IO.Pipes.NamedPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="82861-119">Zobacz [porady: stosowanie potoków nazwanych do sieciowej komunikacji międzyprocesowej](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).</span><span class="sxs-lookup"><span data-stu-id="82861-119">See [How to: Use Named Pipes for Network Interprocess Communication](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82861-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="82861-120">See also</span></span>

- [<span data-ttu-id="82861-121">We/Wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="82861-121">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)  
- [<span data-ttu-id="82861-122">Instrukcje: stosowanie potoków anonimowych do lokalnej komunikacji międzyprocesowej</span><span class="sxs-lookup"><span data-stu-id="82861-122">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)  
- [<span data-ttu-id="82861-123">Instrukcje: stosowanie potoków nazwanych do sieciowej komunikacji międzyprocesowej</span><span class="sxs-lookup"><span data-stu-id="82861-123">How to: Use Named Pipes for Network Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
