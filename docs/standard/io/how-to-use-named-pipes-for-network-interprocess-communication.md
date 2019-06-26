---
title: 'Instrukcje: Stosowanie nazwanych potoków do sieciowej komunikacji międzyprocesowej'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- message-based communication [.NET Framework], named pipes
- named pipes [.NET Framework]
- pipes [.NET Framework]
- multiple connections via named pipes
- network communications [.NET Framework], named pipes
- impersonation [.NET Framework], named pipes
- full duplex communication [.NET Framework], named pipes
ms.assetid: 4e4d7e64-9f1b-4026-98f7-20488ac7b42b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ddd862480a5977a4bada17945e10a25753b44de4
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2019
ms.locfileid: "67402492"
---
# <a name="how-to-use-named-pipes-for-network-interprocess-communication"></a><span data-ttu-id="31236-102">Instrukcje: Stosowanie nazwanych potoków do sieciowej komunikacji międzyprocesowej</span><span class="sxs-lookup"><span data-stu-id="31236-102">How to: Use Named Pipes for Network Interprocess Communication</span></span>
<span data-ttu-id="31236-103">Nazwane potoki zapewniają komunikację międzyprocesorową pomiędzy serwerem potoku i jednym lub kilkoma klientami potoku.</span><span class="sxs-lookup"><span data-stu-id="31236-103">Named pipes provide interprocess communication between a pipe server and one or more pipe clients.</span></span> <span data-ttu-id="31236-104">Oferują one więcej funkcji niż potoki anonimowe, które zapewniają komunikację międzyprocesorową na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="31236-104">They offer more functionality than anonymous pipes, which provide interprocess communication on a local computer.</span></span> <span data-ttu-id="31236-105">Nazwane potoki obsługują komunikację pełnodupleksową przez sieć i wiele instancji serwera, komunikację opartą na komunikatach i personifikację klienta, co pozwala łączyć procesy z ich własnymi zestawami uprawnień na serwerach zdalnych.</span><span class="sxs-lookup"><span data-stu-id="31236-105">Named pipes support full duplex communication over a network and multiple server instances, message-based communication, and client impersonation, which enables connecting processes to use their own set of permissions on remote servers.</span></span>  
  
 <span data-ttu-id="31236-106">Aby zaimplementować nazwane potoki, należy użyć klas <xref:System.IO.Pipes.NamedPipeServerStream> i <xref:System.IO.Pipes.NamedPipeClientStream>.</span><span class="sxs-lookup"><span data-stu-id="31236-106">To implement name pipes, use the <xref:System.IO.Pipes.NamedPipeServerStream> and <xref:System.IO.Pipes.NamedPipeClientStream> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31236-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="31236-107">Example</span></span>  
 <span data-ttu-id="31236-108">W poniższym przykładzie pokazano jak utworzyć nazwany potok używając klasy <xref:System.IO.Pipes.NamedPipeServerStream>.</span><span class="sxs-lookup"><span data-stu-id="31236-108">The following example demonstrates how to create a named pipe by using the <xref:System.IO.Pipes.NamedPipeServerStream> class.</span></span> <span data-ttu-id="31236-109">W tym przykładzie proces serwera tworzy cztery wątki.</span><span class="sxs-lookup"><span data-stu-id="31236-109">In this example, the server process creates four threads.</span></span> <span data-ttu-id="31236-110">Każdy wątek może zaakceptować połączenie klienta.</span><span class="sxs-lookup"><span data-stu-id="31236-110">Each thread can accept a client connection.</span></span> <span data-ttu-id="31236-111">Następnie połączony proces klienta dostarcza do serwera nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="31236-111">The connected client process then supplies the server with a file name.</span></span> <span data-ttu-id="31236-112">Jeśli klient ma wystarczające uprawnienia, proces serwera otwiera plik i wysyła jego zawartość z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="31236-112">If the client has sufficient permissions, the server process opens the file and sends its contents back to the client.</span></span>  
  
 [!code-cpp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/vb/program.vb#01)]  
  
## <a name="example"></a><span data-ttu-id="31236-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="31236-113">Example</span></span>  
 <span data-ttu-id="31236-114">W poniższym przykładzie pokazano proces klienta, który korzysta z klasy <xref:System.IO.Pipes.NamedPipeClientStream>.</span><span class="sxs-lookup"><span data-stu-id="31236-114">The following example shows the client process, which uses the <xref:System.IO.Pipes.NamedPipeClientStream> class.</span></span> <span data-ttu-id="31236-115">Klient łączy się z procesem serwera i wysyła nazwę pliku do serwera.</span><span class="sxs-lookup"><span data-stu-id="31236-115">The client connects to the server process and sends a file name to the server.</span></span> <span data-ttu-id="31236-116">W przykładzie użyto personifikacji, więc tożsamość, która uruchamia aplikację klienta, musi mieć uprawnienia dostępu do tego pliku.</span><span class="sxs-lookup"><span data-stu-id="31236-116">The example uses impersonation, so the identity that is running the client application must have permission to access the file.</span></span> <span data-ttu-id="31236-117">Serwer wysyła następnie zawartość pliku z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="31236-117">The server then sends the contents of the file back to the client.</span></span> <span data-ttu-id="31236-118">Zawartość pliku jest następnie wyświetlana w konsoli.</span><span class="sxs-lookup"><span data-stu-id="31236-118">The file contents are then displayed to the console.</span></span>  
  
 [!code-csharp[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/vb/program.vb#01)]  
  
## <a name="robust-programming"></a><span data-ttu-id="31236-119">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="31236-119">Robust Programming</span></span>  
 <span data-ttu-id="31236-120">Procesy klienta i serwera w tym przykładzie są przeznaczone do uruchomienia na tym samym komputerze, więc nazwa serwera dostarczona do obiektu <xref:System.IO.Pipes.NamedPipeClientStream> to `"."`.</span><span class="sxs-lookup"><span data-stu-id="31236-120">The client and server processes in this example are intended to run on the same computer, so the server name provided to the <xref:System.IO.Pipes.NamedPipeClientStream> object is `"."`.</span></span> <span data-ttu-id="31236-121">Jeśli procesy klienta i serwera znajdują się na oddzielnych komputerach, `"."` zostanie zamienione na nazwę sieciową komputera, który uruchamia proces serwera.</span><span class="sxs-lookup"><span data-stu-id="31236-121">If the client and server processes were on separate computers, `"."` would be replaced with the network name of the computer that runs the server process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31236-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="31236-122">See also</span></span>

- <xref:System.Security.Principal.TokenImpersonationLevel>
- <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName%2A>
- [<span data-ttu-id="31236-123">Potoki</span><span class="sxs-lookup"><span data-stu-id="31236-123">Pipes</span></span>](../../../docs/standard/io/pipe-operations.md)
- [<span data-ttu-id="31236-124">Instrukcje: Stosowanie anonimowych potoków do lokalnej komunikacji międzyprocesowej</span><span class="sxs-lookup"><span data-stu-id="31236-124">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
