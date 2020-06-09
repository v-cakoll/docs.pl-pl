---
title: Powiązanie usługi MSMQ sieci
ms.date: 03/30/2017
ms.assetid: fe4bb696-f57c-4cb3-9b7e-9d95fe6b8323
ms.openlocfilehash: 622341ef00f5d8950fa0c013e427f20e02187893
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602430"
---
# <a name="net-msmq-binding"></a><span data-ttu-id="c96f9-102">Powiązanie usługi MSMQ sieci</span><span class="sxs-lookup"><span data-stu-id="c96f9-102">Net MSMQ Binding</span></span>
<span data-ttu-id="c96f9-103">Ta sekcja zawiera przykłady, które demonstrują korzystanie z atrybutów powiązania usługi MSMQ elementu punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="c96f9-103">This section contains samples that demonstrate using MSMQ binding attributes of an endpoint element.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c96f9-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="c96f9-104">In This Section</span></span>  
 [<span data-ttu-id="c96f9-105">Transakcyjne powiązanie MSMQ</span><span class="sxs-lookup"><span data-stu-id="c96f9-105">Transacted MSMQ Binding</span></span>](transacted-msmq-binding.md)  
 <span data-ttu-id="c96f9-106">Pokazuje, jak przeprowadzić komunikację z kolejką w kolejce przy użyciu usługi kolejkowania komunikatów (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="c96f9-106">Demonstrates how to perform transacted queued communication by using Message Queuing (MSMQ).</span></span>  
  
 [<span data-ttu-id="c96f9-107">Komunikacja za pomocą nietrwałych kolejek</span><span class="sxs-lookup"><span data-stu-id="c96f9-107">Volatile Queued Communication</span></span>](volatile-queued-communication.md)  
 <span data-ttu-id="c96f9-108">Pokazuje, jak przeprowadzić komunikację nietrwałą w kolejce za pośrednictwem transportu kolejkowania komunikatów (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="c96f9-108">Demonstrates how to perform volatile queued communication over the Message Queuing (MSMQ) transport.</span></span>  
  
 [<span data-ttu-id="c96f9-109">Kolejki utraconych komunikatów</span><span class="sxs-lookup"><span data-stu-id="c96f9-109">Dead Letter Queues</span></span>](dead-letter-queues.md)  
 <span data-ttu-id="c96f9-110">Pokazuje, jak obsługiwać i przetwarzać komunikaty, których dostarczenie nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="c96f9-110">Demonstrates how to handle and process messages that have failed delivery.</span></span>  
  
 [<span data-ttu-id="c96f9-111">Obsługa zanieczyszczonych komunikatów w usłudze MSMQ 4.0</span><span class="sxs-lookup"><span data-stu-id="c96f9-111">Poison Message Handling in MSMQ 4.0</span></span>](poison-message-handling-in-msmq-4-0.md)  
 <span data-ttu-id="c96f9-112">Pokazuje, jak przeprowadzić obsługę skażonych komunikatów w usłudze przy użyciu usługi MSMQ 4,0.</span><span class="sxs-lookup"><span data-stu-id="c96f9-112">Demonstrates how to perform poison message handling in a service using MSMQ 4.0.</span></span>  
  
 [<span data-ttu-id="c96f9-113">Sesje i kolejki</span><span class="sxs-lookup"><span data-stu-id="c96f9-113">Sessions and Queues</span></span>](sessions-and-queues.md)  
 <span data-ttu-id="c96f9-114">Pokazuje, jak wysyłać i odbierać zestaw powiązanych komunikatów w kolejce komunikacji za pośrednictwem transportu usługi kolejkowania komunikatów (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="c96f9-114">Demonstrates how to send and receive a set of related messages in queued communication over the Message Queuing (MSMQ) transport.</span></span>  
  
 [<span data-ttu-id="c96f9-115">Komunikacja dwukierunkowa</span><span class="sxs-lookup"><span data-stu-id="c96f9-115">Two-Way Communication</span></span>](two-way-communication.md)  
 <span data-ttu-id="c96f9-116">Pokazuje, jak przeprowadzić transakcję dwukierunkowej komunikacji w kolejce za pośrednictwem usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="c96f9-116">Demonstrates how to perform transacted two-way queued communication over MSMQ.</span></span>
  
 [<span data-ttu-id="c96f9-117">SRMP</span><span class="sxs-lookup"><span data-stu-id="c96f9-117">SRMP</span></span>](srmp.md)  
 <span data-ttu-id="c96f9-118">Pokazuje, w jaki sposób przeprowadzić komunikację z kolejką w kolejce przy użyciu usługi kolejkowania komunikatów (MSMQ) za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="c96f9-118">Demonstrates how to perform transacted queued communication by using Message Queuing (MSMQ) over HTTP.</span></span>  
  
 [<span data-ttu-id="c96f9-119">Zabezpieczenia komunikatów w ramach kolejkowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="c96f9-119">Message Security over Message Queuing</span></span>](message-security-over-message-queuing.md)  
 <span data-ttu-id="c96f9-120">Demonstruje sposób implementacji aplikacji, która korzysta z protokołu WS-Security z uwierzytelnianiem przy użyciu certyfikatu X. 509v3 na potrzeby klienta i wymaga uwierzytelniania serwera za pomocą certyfikatu X. 509v3 serwera za pośrednictwem usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="c96f9-120">Demonstrates how to implement an application that uses WS-Security with X.509v3 certificate authentication for the client and requires server authentication using the server's X.509v3 certificate over MSMQ.</span></span>
