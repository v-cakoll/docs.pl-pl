---
title: "Używanie wątków i wątkowości"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 9b5ec2cd-121b-4d49-b075-222cf26f2344
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 80eb4c3bb98acdd1f83dbf5bcf57b2f7b295742b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="using-threads-and-threading"></a><span data-ttu-id="53d49-102">Używanie wątków i wątkowości</span><span class="sxs-lookup"><span data-stu-id="53d49-102">Using Threads and Threading</span></span>
<span data-ttu-id="53d49-103">Tematy w tej sekcji omówiono tworzenie i zarządzanie wątków zarządzanych, jak przekazywać dane do zarządzanych wątków i uzyskiwać wyniki z powrotem i jak zniszczyć wątków i obsługiwać <xref:System.Threading.ThreadAbortException>.</span><span class="sxs-lookup"><span data-stu-id="53d49-103">The topics in this section discuss the creation and management of managed threads, how to pass data to managed threads and get results back, and how to destroy threads and handle a <xref:System.Threading.ThreadAbortException>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="53d49-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="53d49-104">In This Section</span></span>  
 [<span data-ttu-id="53d49-105">Tworzenie wątków i przekazywanie danych w chwili rozpoczęcia</span><span class="sxs-lookup"><span data-stu-id="53d49-105">Creating Threads and Passing Data at Start Time</span></span>](../../../docs/standard/threading/creating-threads-and-passing-data-at-start-time.md)  
 <span data-ttu-id="53d49-106">Opisano i przedstawiono tworzenie wątków zarządzanych, w tym sposób przekazywania danych do nowego wątków i jak odzyskać dane.</span><span class="sxs-lookup"><span data-stu-id="53d49-106">Discusses and demonstrates the creation of managed threads, including how to pass data to new threads and how to get data back.</span></span>  
  
 [<span data-ttu-id="53d49-107">Wstrzymywanie i wznawianie wątków</span><span class="sxs-lookup"><span data-stu-id="53d49-107">Pausing and Resuming Threads</span></span>](../../../docs/standard/threading/pausing-and-resuming-threads.md)  
 <span data-ttu-id="53d49-108">W tym artykule omówiono zagadnienia wstrzymywanie i wznawianie wątków zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="53d49-108">Discusses the ramifications of pausing and resuming managed threads.</span></span>  
  
 [<span data-ttu-id="53d49-109">Niszczenie wątków</span><span class="sxs-lookup"><span data-stu-id="53d49-109">Destroying Threads</span></span>](../../../docs/standard/threading/destroying-threads.md)  
 <span data-ttu-id="53d49-110">W tym artykule omówiono konsekwencje niszczenia zarządzanych wątków i sposób obsługi <xref:System.Threading.ThreadAbortException>.</span><span class="sxs-lookup"><span data-stu-id="53d49-110">Discusses the ramifications of destroying managed threads, and how to handle a <xref:System.Threading.ThreadAbortException>.</span></span>  
  
 [<span data-ttu-id="53d49-111">Harmonogram wątków</span><span class="sxs-lookup"><span data-stu-id="53d49-111">Scheduling Threads</span></span>](../../../docs/standard/threading/scheduling-threads.md)  
 <span data-ttu-id="53d49-112">W tym artykule omówiono priorytetów wątku i ich wpływu na planowanie wątku.</span><span class="sxs-lookup"><span data-stu-id="53d49-112">Discusses thread priorities and how they affect thread scheduling.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="53d49-113">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="53d49-113">Reference</span></span>  
 <xref:System.Threading.Thread>  
 <span data-ttu-id="53d49-114">Zawiera dokumentacja referencyjna dla <xref:System.Threading.Thread> klasy, która reprezentuje zarządzanego wątku, czy pochodzi kodu niezarządzanego, lub został utworzony w zarządzanej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="53d49-114">Provides reference documentation for the <xref:System.Threading.Thread> class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.Threading.ThreadStart>  
 <span data-ttu-id="53d49-115">Zawiera dokumentacja referencyjna dla <xref:System.Threading.ThreadStart> delegata, który reprezentuje procedury wątku bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="53d49-115">Provides reference documentation for the <xref:System.Threading.ThreadStart> delegate that represents parameterless thread procedures.</span></span>  
  
 <xref:System.Threading.ParameterizedThreadStart>  
 <span data-ttu-id="53d49-116">Zapewnia prosty sposób na przekazywanie danych do procedury wątku, mimo że bez wprowadzania silne.</span><span class="sxs-lookup"><span data-stu-id="53d49-116">Provides an easy way to pass data to a thread procedure, although without strong typing.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="53d49-117">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="53d49-117">Related Sections</span></span>  
 [<span data-ttu-id="53d49-118">Wątki i wątkowość</span><span class="sxs-lookup"><span data-stu-id="53d49-118">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)  
 <span data-ttu-id="53d49-119">Wprowadzenie do zarządzanych wątków.</span><span class="sxs-lookup"><span data-stu-id="53d49-119">Provides an introduction to managed threading.</span></span>
