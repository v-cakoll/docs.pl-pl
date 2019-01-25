---
title: 'Instrukcje: Korzystanie z potoków nazwanych do sieciowej komunikacji międzyprocesowej'
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
- full duplex communcation [.NET Framework], named pipes
ms.assetid: 4e4d7e64-9f1b-4026-98f7-20488ac7b42b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 608991878b49bf0bafe9ebf90dbfc8eaec69e0e7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54698872"
---
# <a name="how-to-use-named-pipes-for-network-interprocess-communication"></a><span data-ttu-id="235fd-102">Instrukcje: Korzystanie z potoków nazwanych do sieciowej komunikacji międzyprocesowej</span><span class="sxs-lookup"><span data-stu-id="235fd-102">How to: Use Named Pipes for Network Interprocess Communication</span></span>
<span data-ttu-id="235fd-103">Nazwane potoki zapewniają komunikację międzyprocesorową pomiędzy serwerem potoku i jednym lub kilkoma klientami potoku.</span><span class="sxs-lookup"><span data-stu-id="235fd-103">Named pipes provide interprocess communication between a pipe server and one or more pipe clients.</span></span> <span data-ttu-id="235fd-104">Oferują one więcej funkcji niż potoki anonimowe, które zapewniają komunikację międzyprocesorową na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="235fd-104">They offer more functionality than anonymous pipes, which provide interprocess communication on a local computer.</span></span> <span data-ttu-id="235fd-105">Nazwane potoki obsługują komunikację pełnodupleksową przez sieć i wiele instancji serwera, komunikację opartą na komunikatach i personifikację klienta, co pozwala łączyć procesy z ich własnymi zestawami uprawnień na serwerach zdalnych.</span><span class="sxs-lookup"><span data-stu-id="235fd-105">Named pipes support full duplex communication over a network and multiple server instances, message-based communication, and client impersonation, which enables connecting processes to use their own set of permissions on remote servers.</span></span>  
  
 <span data-ttu-id="235fd-106">Aby zaimplementować nazwane potoki, należy użyć klas <xref:System.IO.Pipes.NamedPipeServerStream> i <xref:System.IO.Pipes.NamedPipeClientStream>.</span><span class="sxs-lookup"><span data-stu-id="235fd-106">To implement name pipes, use the <xref:System.IO.Pipes.NamedPipeServerStream> and <xref:System.IO.Pipes.NamedPipeClientStream> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="235fd-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="235fd-107">Example</span></span>  
 <span data-ttu-id="235fd-108">W poniższym przykładzie pokazano jak utworzyć nazwany potok używając klasy <xref:System.IO.Pipes.NamedPipeServerStream>.</span><span class="sxs-lookup"><span data-stu-id="235fd-108">The following example demonstrates how to create a named pipe by using the <xref:System.IO.Pipes.NamedPipeServerStream> class.</span></span> <span data-ttu-id="235fd-109">W tym przykładzie proces serwera tworzy cztery wątki.</span><span class="sxs-lookup"><span data-stu-id="235fd-109">In this example, the server process creates four threads.</span></span> <span data-ttu-id="235fd-110">Każdy wątek może zaakceptować połączenie klienta.</span><span class="sxs-lookup"><span data-stu-id="235fd-110">Each thread can accept a client connection.</span></span> <span data-ttu-id="235fd-111">Następnie połączony proces klienta dostarcza do serwera nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="235fd-111">The connected client process then supplies the server with a file name.</span></span> <span data-ttu-id="235fd-112">Jeśli klient ma wystarczające uprawnienia, proces serwera otwiera plik i wysyła jego zawartość z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="235fd-112">If the client has sufficient permissions, the server process opens the file and sends its contents back to the client.</span></span>  
  
 [!code-cpp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/vb/program.vb#01)]  
  
## <a name="example"></a><span data-ttu-id="235fd-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="235fd-113">Example</span></span>  
 <span data-ttu-id="235fd-114">W poniższym przykładzie pokazano proces klienta, który korzysta z klasy <xref:System.IO.Pipes.NamedPipeClientStream>.</span><span class="sxs-lookup"><span data-stu-id="235fd-114">The following example shows the client process, which uses the <xref:System.IO.Pipes.NamedPipeClientStream> class.</span></span> <span data-ttu-id="235fd-115">Klient łączy się z procesem serwera i wysyła nazwę pliku do serwera.</span><span class="sxs-lookup"><span data-stu-id="235fd-115">The client connects to the server process and sends a file name to the server.</span></span> <span data-ttu-id="235fd-116">W przykładzie użyto personifikacji, więc tożsamość, która uruchamia aplikację klienta, musi mieć uprawnienia dostępu do tego pliku.</span><span class="sxs-lookup"><span data-stu-id="235fd-116">The example uses impersonation, so the identity that is running the client application must have permission to access the file.</span></span> <span data-ttu-id="235fd-117">Serwer wysyła następnie zawartość pliku z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="235fd-117">The server then sends the contents of the file back to the client.</span></span> <span data-ttu-id="235fd-118">Zawartość pliku jest następnie wyświetlana w konsoli.</span><span class="sxs-lookup"><span data-stu-id="235fd-118">The file contents are then displayed to the console.</span></span>  
  
 [!code-csharp[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/vb/program.vb#01)]  
  
## <a name="robust-programming"></a><span data-ttu-id="235fd-119">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="235fd-119">Robust Programming</span></span>  
 <span data-ttu-id="235fd-120">Procesy klienta i serwera w tym przykładzie są przeznaczone do uruchomienia na tym samym komputerze, więc nazwa serwera dostarczona do obiektu <xref:System.IO.Pipes.NamedPipeClientStream> to `"."`.</span><span class="sxs-lookup"><span data-stu-id="235fd-120">The client and server processes in this example are intended to run on the same computer, so the server name provided to the <xref:System.IO.Pipes.NamedPipeClientStream> object is `"."`.</span></span> <span data-ttu-id="235fd-121">Jeśli procesy klienta i serwera znajdują się na oddzielnych komputerach, `"."` zostanie zamienione na nazwę sieciową komputera, który uruchamia proces serwera.</span><span class="sxs-lookup"><span data-stu-id="235fd-121">If the client and server processes were on separate computers, `"."` would be replaced with the network name of the computer that runs the server process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="235fd-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="235fd-122">See also</span></span>

- <xref:System.Security.Principal.TokenImpersonationLevel>
- <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName%2A>
- [<span data-ttu-id="235fd-123">Potoki</span><span class="sxs-lookup"><span data-stu-id="235fd-123">Pipes</span></span>](../../../docs/standard/io/pipe-operations.md)
- [<span data-ttu-id="235fd-124">Instrukcje: Stosowanie anonimowych potoków do lokalnej komunikacji międzyprocesowej</span><span class="sxs-lookup"><span data-stu-id="235fd-124">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
