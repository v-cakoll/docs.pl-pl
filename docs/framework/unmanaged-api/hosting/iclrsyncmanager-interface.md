---
title: ICLRSyncManager — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager
helpviewer_keywords:
- ICLRSyncManager interface [.NET Framework hosting]
ms.assetid: a49f9d80-1c76-4ddd-8c49-34f913a5c596
topic_type:
- apiref
ms.openlocfilehash: 3593e4d68058a1820f575c92ff9571d43560316a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133930"
---
# <a name="iclrsyncmanager-interface"></a><span data-ttu-id="08341-102">ICLRSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="08341-102">ICLRSyncManager Interface</span></span>
<span data-ttu-id="08341-103">Definiuje metody, które pozwalają hostowi uzyskać informacje o żądanych zadaniach i wykryć zakleszczenie w swojej implementacji synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="08341-103">Defines methods that allow the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="08341-104">Metody</span><span class="sxs-lookup"><span data-stu-id="08341-104">Methods</span></span>  
  
|<span data-ttu-id="08341-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="08341-105">Method</span></span>|<span data-ttu-id="08341-106">Opis</span><span class="sxs-lookup"><span data-stu-id="08341-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="08341-107">CreateRWLockOwnerIterator, metoda</span><span class="sxs-lookup"><span data-stu-id="08341-107">CreateRWLockOwnerIterator Method</span></span>](iclrsyncmanager-createrwlockowneriterator-method.md)|<span data-ttu-id="08341-108">Żądania, które środowisko uruchomieniowe języka wspólnego (CLR) tworzy iterator dla hosta do użycia w celu określenia zestawu zadań oczekujących na blokadę modułu odczytującego.</span><span class="sxs-lookup"><span data-stu-id="08341-108">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>|  
|[<span data-ttu-id="08341-109">DeleteRWLockOwnerIterator, metoda</span><span class="sxs-lookup"><span data-stu-id="08341-109">DeleteRWLockOwnerIterator Method</span></span>](iclrsyncmanager-deleterwlockowneriterator-method.md)|<span data-ttu-id="08341-110">Żądania, aby środowisko CLR zniszczyć iterator, który został utworzony przez wywołanie do `CreateRWLockOwnerIterator`.</span><span class="sxs-lookup"><span data-stu-id="08341-110">Requests that the CLR destroy an iterator that was created by a call to `CreateRWLockOwnerIterator`.</span></span>|  
|[<span data-ttu-id="08341-111">GetMonitorOwner, metoda</span><span class="sxs-lookup"><span data-stu-id="08341-111">GetMonitorOwner Method</span></span>](iclrsyncmanager-getmonitorowner-method.md)|<span data-ttu-id="08341-112">Pobiera zadanie, które jest właścicielem określonego monitora.</span><span class="sxs-lookup"><span data-stu-id="08341-112">Gets the task that owns the specified monitor.</span></span>|  
|[<span data-ttu-id="08341-113">GetRWLockOwnerNext, metoda</span><span class="sxs-lookup"><span data-stu-id="08341-113">GetRWLockOwnerNext Method</span></span>](iclrsyncmanager-getrwlockownernext-method.md)|<span data-ttu-id="08341-114">Pobiera następne zadanie czekające na bieżącą blokadę modułu odczytującego.</span><span class="sxs-lookup"><span data-stu-id="08341-114">Gets the next task that is waiting on the current reader-writer lock.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="08341-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="08341-115">Requirements</span></span>  
 <span data-ttu-id="08341-116">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08341-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08341-117">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="08341-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="08341-118">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="08341-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="08341-119">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08341-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08341-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="08341-120">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="08341-121">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="08341-121">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- <span data-ttu-id="08341-122">[Wątki zarządzane i niezarządzane](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="08341-122">[Managed and Unmanaged Threading](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))</span></span>
- [<span data-ttu-id="08341-123">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="08341-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
