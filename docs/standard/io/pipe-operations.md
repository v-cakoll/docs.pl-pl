---
title: Operacje potokowe w programie .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- pipes [.NET Framework]
- pipe operations [.NET Framework]
- interprocess communication [.NET Framework], pipes
- I/O [.NET Framework], pipes
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
ms.openlocfilehash: 693dd1eb0b0b9bb87973eead26a344ed67641e34
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706559"
---
# <a name="pipe-operations-in-net"></a><span data-ttu-id="9fd18-102">Operacje potokowe w programie .NET</span><span class="sxs-lookup"><span data-stu-id="9fd18-102">Pipe Operations in .NET</span></span>
<span data-ttu-id="9fd18-103">Potoki zapewniają metodę komunikacji międzyprocesowej.</span><span class="sxs-lookup"><span data-stu-id="9fd18-103">Pipes provide a means for interprocess communication.</span></span> <span data-ttu-id="9fd18-104">Istnieją dwa typy potoków:</span><span class="sxs-lookup"><span data-stu-id="9fd18-104">There are two types of pipes:</span></span>  
  
- <span data-ttu-id="9fd18-105">Potoki anonimowe.</span><span class="sxs-lookup"><span data-stu-id="9fd18-105">Anonymous pipes.</span></span>  
  
     <span data-ttu-id="9fd18-106">Potoki anonimowe zapewniają komunikację międzyprocesową na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="9fd18-106">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="9fd18-107">Potoki anonimowe wymagają mniej obciążenia niż potoki nazwane, ale oferują ograniczone usługi.</span><span class="sxs-lookup"><span data-stu-id="9fd18-107">Anonymous pipes require less overhead than named pipes but offer limited services.</span></span> <span data-ttu-id="9fd18-108">Potoki anonimowe są jednokierunkowe i nie mogą być używane w sieci.</span><span class="sxs-lookup"><span data-stu-id="9fd18-108">Anonymous pipes are one-way and cannot be used over a network.</span></span> <span data-ttu-id="9fd18-109">Obsługują one tylko jedno wystąpienie serwera.</span><span class="sxs-lookup"><span data-stu-id="9fd18-109">They support only a single server instance.</span></span> <span data-ttu-id="9fd18-110">Potoki anonimowe są przydatne do komunikacji między wątkami lub między procesami nadrzędnymi i podrzędnymi, w których uchwyty potoku mogą być łatwo przesłane do procesu podrzędnego po jego utworzeniu.</span><span class="sxs-lookup"><span data-stu-id="9fd18-110">Anonymous pipes are useful for communication between threads, or between parent and child processes where the pipe handles can be easily passed to the child process when it is created.</span></span>  
  
     <span data-ttu-id="9fd18-111">W programie .NET można zaimplementować anonimowe potoki przy użyciu klas <xref:System.IO.Pipes.AnonymousPipeServerStream> i <xref:System.IO.Pipes.AnonymousPipeClientStream>.</span><span class="sxs-lookup"><span data-stu-id="9fd18-111">In .NET, you implement anonymous pipes by using the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="9fd18-112">Zobacz [jak: korzystanie z anonimowych potoków do lokalnej komunikacji międzyprocesowej](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span><span class="sxs-lookup"><span data-stu-id="9fd18-112">See [How to: Use Anonymous Pipes for Local Interprocess Communication](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span></span>  
  
- <span data-ttu-id="9fd18-113">Nazwane potoki.</span><span class="sxs-lookup"><span data-stu-id="9fd18-113">Named pipes.</span></span>  
  
     <span data-ttu-id="9fd18-114">Nazwane potoki zapewniają komunikację międzyprocesorową pomiędzy serwerem potoku i jednym lub kilkoma klientami potoku.</span><span class="sxs-lookup"><span data-stu-id="9fd18-114">Named pipes provide interprocess communication between a pipe server and one or more pipe clients.</span></span> <span data-ttu-id="9fd18-115">Nazwane potoki mogą być jednokierunkowe lub dwustronne.</span><span class="sxs-lookup"><span data-stu-id="9fd18-115">Named pipes can be one-way or duplex.</span></span> <span data-ttu-id="9fd18-116">Obsługują komunikację opartą na komunikatach i umożliwiają wielu klientom jednoczesne łączenie się z procesem serwera przy użyciu tej samej nazwy potoku.</span><span class="sxs-lookup"><span data-stu-id="9fd18-116">They support message-based communication and allow multiple clients to connect simultaneously to the server process using the same pipe name.</span></span> <span data-ttu-id="9fd18-117">Nazwane potoki obsługują również personifikację, która umożliwia łączenie procesów w celu używania ich własnych uprawnień na serwerach zdalnych.</span><span class="sxs-lookup"><span data-stu-id="9fd18-117">Named pipes also support impersonation, which enables connecting processes to use their own permissions on remote servers.</span></span>  
  
     <span data-ttu-id="9fd18-118">W programie .NET należy zaimplementować nazwane potoki przy użyciu klas <xref:System.IO.Pipes.NamedPipeServerStream> i <xref:System.IO.Pipes.NamedPipeClientStream>.</span><span class="sxs-lookup"><span data-stu-id="9fd18-118">In .NET, you implement named pipes by using the <xref:System.IO.Pipes.NamedPipeServerStream> and <xref:System.IO.Pipes.NamedPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="9fd18-119">Zobacz [jak: używanie nazwanych potoków do komunikacji międzyprocesowej sieci](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).</span><span class="sxs-lookup"><span data-stu-id="9fd18-119">See [How to: Use Named Pipes for Network Interprocess Communication](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fd18-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9fd18-120">See also</span></span>

- [<span data-ttu-id="9fd18-121">We/Wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="9fd18-121">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
- [<span data-ttu-id="9fd18-122">Instrukcje: stosowanie potoków anonimowych do lokalnej komunikacji międzyprocesowej</span><span class="sxs-lookup"><span data-stu-id="9fd18-122">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
- [<span data-ttu-id="9fd18-123">Instrukcje: stosowanie potoków nazwanych do sieciowej komunikacji międzyprocesowej</span><span class="sxs-lookup"><span data-stu-id="9fd18-123">How to: Use Named Pipes for Network Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
