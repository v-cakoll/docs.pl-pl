---
title: ICorConfiguration::SetGCThreadControl — Metoda
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetGCThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCThreadControl
helpviewer_keywords:
- ICorConfiguration::SetGCThreadControl method [.NET Framework hosting]
- SetGCThreadControl method [.NET Framework hosting]
ms.assetid: 72e38e61-3d56-4ae3-b8f6-0ab7922aaf11
topic_type:
- apiref
ms.openlocfilehash: 7874424150e0f4e1818ad9c72e31fd584e016829
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762399"
---
# <a name="icorconfigurationsetgcthreadcontrol-method"></a><span data-ttu-id="2bebb-102">ICorConfiguration::SetGCThreadControl — Metoda</span><span class="sxs-lookup"><span data-stu-id="2bebb-102">ICorConfiguration::SetGCThreadControl Method</span></span>
<span data-ttu-id="2bebb-103">Ustawia interfejs wywołania zwrotnego dla wątków planowania dla zadań innych niż środowisko uruchomieniowe, które w przeciwnym razie byłyby blokowane dla wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="2bebb-103">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bebb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2bebb-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCThreadControl (  
    [in] IGCThreadControl* pGCThreadControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2bebb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2bebb-105">Parameters</span></span>  
 `pGCThreadControl`  
 <span data-ttu-id="2bebb-106">podczas Wskaźnik do obiektu [IGCThreadControl](igcthreadcontrol-interface.md) , który powiadamia hosta o zawieszeniu wątków dla zadań innych niż środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="2bebb-106">[in] A pointer to an [IGCThreadControl](igcthreadcontrol-interface.md) object that notifies the host about the suspension of threads for non-runtime tasks.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2bebb-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2bebb-107">Remarks</span></span>  
 <span data-ttu-id="2bebb-108">Host może wybrać w ramach wywołania zwrotnego [IGCThreadControl:: ThreadIsBlockingForSuspension —](igcthreadcontrol-threadisblockingforsuspension-method.md) , czy ponownie zaplanować wątek.</span><span class="sxs-lookup"><span data-stu-id="2bebb-108">The host may choose within the [IGCThreadControl::ThreadIsBlockingForSuspension](igcthreadcontrol-threadisblockingforsuspension-method.md) callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bebb-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2bebb-109">Requirements</span></span>  
 <span data-ttu-id="2bebb-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2bebb-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bebb-111">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2bebb-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2bebb-112">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2bebb-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2bebb-113">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bebb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bebb-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2bebb-114">See also</span></span>

- [<span data-ttu-id="2bebb-115">ICorConfiguration, interfejs</span><span class="sxs-lookup"><span data-stu-id="2bebb-115">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)
