---
title: CoordinatorRecoveryLogEntryCorrupt
ms.date: 03/30/2017
ms.assetid: 3cd0c3e3-84c8-4d43-a561-a8851c78e565
ms.openlocfilehash: de9d27e74088b1bac9c8a401c5af2b119fc8e90e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797986"
---
# <a name="coordinatorrecoverylogentrycorrupt"></a><span data-ttu-id="99f1d-102">CoordinatorRecoveryLogEntryCorrupt</span><span class="sxs-lookup"><span data-stu-id="99f1d-102">CoordinatorRecoveryLogEntryCorrupt</span></span>
<span data-ttu-id="99f1d-103">#C1 139</span><span class="sxs-lookup"><span data-stu-id="99f1d-103">Id: 139</span></span>  
  
 <span data-ttu-id="99f1d-104">Obrażeń Błąd</span><span class="sxs-lookup"><span data-stu-id="99f1d-104">Severity: Error</span></span>  
  
 <span data-ttu-id="99f1d-105">Kategorii TransactionBridge</span><span class="sxs-lookup"><span data-stu-id="99f1d-105">Category: TransactionBridge</span></span>  
  
## <a name="description"></a><span data-ttu-id="99f1d-106">Opis</span><span class="sxs-lookup"><span data-stu-id="99f1d-106">Description</span></span>  
 <span data-ttu-id="99f1d-107">To zdarzenie wskazuje, że wpis dziennika odzyskiwania koordynatora został uszkodzony i nie można go zdeserializować.</span><span class="sxs-lookup"><span data-stu-id="99f1d-107">This event indicates that a  coordinator recovery log entry was corrupt and could not be deserialized.</span></span> <span data-ttu-id="99f1d-108">Przyczyną tego błędu może być utrata danych.</span><span class="sxs-lookup"><span data-stu-id="99f1d-108">Data loss may result from this error.</span></span> <span data-ttu-id="99f1d-109">Zdarzenie Wyświetla identyfikator transakcji, dane odzyskiwania (kodowane algorytmem Base64), wyjątek, nazwę procesu i identyfikator procesu.</span><span class="sxs-lookup"><span data-stu-id="99f1d-109">The event lists the Transaction ID, Recovery data (Base64 encoded), exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99f1d-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="99f1d-110">See also</span></span>

- [<span data-ttu-id="99f1d-111">Rejestrowanie zdarzeń</span><span class="sxs-lookup"><span data-stu-id="99f1d-111">Event Logging</span></span>](index.md)
- [<span data-ttu-id="99f1d-112">Informacje ogólne o zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="99f1d-112">Events General Reference</span></span>](events-general-reference.md)
