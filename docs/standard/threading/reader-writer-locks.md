---
title: Klasa reader_writer_lock
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ReaderWriterLock class, about ReaderWriterLock class
- threading [.NET Framework], ReaderWriterLock class
ms.assetid: 8c71acf2-2c18-4f4d-8cdb-0728639265fd
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d005442ee74b46a0ecb1eaafe214e7190330cfe7
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="reader-writer-locks"></a><span data-ttu-id="ab8dc-102">Klasa reader_writer_lock</span><span class="sxs-lookup"><span data-stu-id="ab8dc-102">Reader-Writer Locks</span></span>
<span data-ttu-id="ab8dc-103"><xref:System.Threading.ReaderWriterLockSlim> Klasa umożliwia wiele wątków jednocześnie odczytać zasobu, ale wymaga wątku oczekiwania na wyłączność w celu zapisu do tego zasobu.</span><span class="sxs-lookup"><span data-stu-id="ab8dc-103">The <xref:System.Threading.ReaderWriterLockSlim> class enables multiple threads to read a resource concurrently, but requires a thread to wait for an exclusive lock in order to write to the resource.</span></span>  
  
 <span data-ttu-id="ab8dc-104">Można na przykład <xref:System.Threading.ReaderWriterLockSlim> w Twojej aplikacji w celu umożliwienia współpracy synchronizacji między wątków, które uzyskują dostęp do zasobu udostępnionego.</span><span class="sxs-lookup"><span data-stu-id="ab8dc-104">You might use a <xref:System.Threading.ReaderWriterLockSlim> in your application to provide cooperative synchronization among threads that access a shared resource.</span></span> <span data-ttu-id="ab8dc-105">Blokady są pobierane <xref:System.Threading.ReaderWriterLockSlim> samej siebie.</span><span class="sxs-lookup"><span data-stu-id="ab8dc-105">Locks are taken on the <xref:System.Threading.ReaderWriterLockSlim> itself.</span></span>  
  
 <span data-ttu-id="ab8dc-106">Zgodnie z wątku mechanizm synchronizacji, należy się upewnić, że nie ma wątków obejścia blokowania zapewnianej przez <xref:System.Threading.ReaderWriterLockSlim>.</span><span class="sxs-lookup"><span data-stu-id="ab8dc-106">As with any thread synchronization mechanism, you must ensure that no threads bypass the locking that is provided by <xref:System.Threading.ReaderWriterLockSlim>.</span></span> <span data-ttu-id="ab8dc-107">Jest jednym ze sposobów zapewnienia zaprojektować klasy, która hermetyzuje zasób udostępniony.</span><span class="sxs-lookup"><span data-stu-id="ab8dc-107">One way to ensure this is to design a class that encapsulates the shared resource.</span></span> <span data-ttu-id="ab8dc-108">Ta klasa zapewni elementów członkowskich, który dostępu prywatnego udostępnionych zasobów, które korzystają z prywatnej <xref:System.Threading.ReaderWriterLockSlim> do synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="ab8dc-108">This class would provide members that access the private shared resource and that use a private <xref:System.Threading.ReaderWriterLockSlim> for synchronization.</span></span> <span data-ttu-id="ab8dc-109">Na przykład, zobacz przykład kodu <xref:System.Threading.ReaderWriterLockSlim> klasy.</span><span class="sxs-lookup"><span data-stu-id="ab8dc-109">For an example, see the code example for the <xref:System.Threading.ReaderWriterLockSlim> class.</span></span> <span data-ttu-id="ab8dc-110"><xref:System.Threading.ReaderWriterLockSlim>jest za mało wydajne, ma być używany do synchronizowania poszczególnych obiektów.</span><span class="sxs-lookup"><span data-stu-id="ab8dc-110"><xref:System.Threading.ReaderWriterLockSlim> is efficient enough to be used to synchronize individual objects.</span></span>  
  
 <span data-ttu-id="ab8dc-111">Struktury aplikacji w taki sposób, aby zminimalizować czas trwania odczytu i zapisu.</span><span class="sxs-lookup"><span data-stu-id="ab8dc-111">Structure your application to minimize the duration of read and write operations.</span></span> <span data-ttu-id="ab8dc-112">Operacje zapisu długi wpływa na przepływność bezpośrednio ponieważ blokady zapisu jest na wyłączność.</span><span class="sxs-lookup"><span data-stu-id="ab8dc-112">Long write operations affect throughput directly because the write lock is exclusive.</span></span> <span data-ttu-id="ab8dc-113">Czas odczytu autorów oczekiwania bloku operacji, i jeśli co najmniej jeden wątek oczekuje na dostęp do zapisu, wątków, które żądają dostępu do odczytu będzie również zablokowany.</span><span class="sxs-lookup"><span data-stu-id="ab8dc-113">Long read operations block waiting writers, and if at least one thread is waiting for write access, threads that request read access will be blocked as well.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ab8dc-114">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Ma dwa reader_writer_lock, <xref:System.Threading.ReaderWriterLockSlim> i <xref:System.Threading.ReaderWriterLock>.</span><span class="sxs-lookup"><span data-stu-id="ab8dc-114">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] has two reader-writer locks, <xref:System.Threading.ReaderWriterLockSlim> and <xref:System.Threading.ReaderWriterLock>.</span></span> <span data-ttu-id="ab8dc-115"><xref:System.Threading.ReaderWriterLockSlim>jest zalecana dla wszystkich nowych wdrożeń.</span><span class="sxs-lookup"><span data-stu-id="ab8dc-115"><xref:System.Threading.ReaderWriterLockSlim> is recommended for all new development.</span></span> <span data-ttu-id="ab8dc-116"><xref:System.Threading.ReaderWriterLockSlim>przypomina <xref:System.Threading.ReaderWriterLock>, ale jest prostszy zasady rekursji oraz uaktualniania i zmiany na starszą wersję stan blokady.</span><span class="sxs-lookup"><span data-stu-id="ab8dc-116"><xref:System.Threading.ReaderWriterLockSlim> is similar to <xref:System.Threading.ReaderWriterLock>, but it has simplified rules for recursion and for upgrading and downgrading lock state.</span></span> <span data-ttu-id="ab8dc-117"><xref:System.Threading.ReaderWriterLockSlim>pozwala uniknąć wielu przypadkach potencjalnych zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="ab8dc-117"><xref:System.Threading.ReaderWriterLockSlim> avoids many cases of potential deadlock.</span></span> <span data-ttu-id="ab8dc-118">Ponadto wydajność <xref:System.Threading.ReaderWriterLockSlim> jest znacznie lepszą niż <xref:System.Threading.ReaderWriterLock>.</span><span class="sxs-lookup"><span data-stu-id="ab8dc-118">In addition, the performance of <xref:System.Threading.ReaderWriterLockSlim> is significantly better than <xref:System.Threading.ReaderWriterLock>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab8dc-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ab8dc-119">See Also</span></span>  
 <xref:System.Threading.ReaderWriterLockSlim>  
 <xref:System.Threading.ReaderWriterLock>  
 [<span data-ttu-id="ab8dc-120">Wątkowość</span><span class="sxs-lookup"><span data-stu-id="ab8dc-120">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="ab8dc-121">Wątkowość obiektów i funkcji</span><span class="sxs-lookup"><span data-stu-id="ab8dc-121">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
