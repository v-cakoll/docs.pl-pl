---
title: ICorConfiguration::SetGCHostControl — Metoda
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetGCHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCHostControl
helpviewer_keywords:
- ICorConfiguration::SetGCHostControl method [.NET Framework hosting]
- SetGCHostControl method [.NET Framework hosting]
ms.assetid: bca6bd79-e288-475a-aa46-6bf81541d966
topic_type:
- apiref
ms.openlocfilehash: 5a32fb0480e76f47495590a29c329f54722e2dee
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127783"
---
# <a name="icorconfigurationsetgchostcontrol-method"></a><span data-ttu-id="9282f-102">ICorConfiguration::SetGCHostControl — Metoda</span><span class="sxs-lookup"><span data-stu-id="9282f-102">ICorConfiguration::SetGCHostControl Method</span></span>
<span data-ttu-id="9282f-103">Ustawia interfejs wywołania zwrotnego, który ma być używany przez moduł wyrzucania elementów bezużytecznych, aby zażądać od hosta zmiany limitów pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="9282f-103">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9282f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9282f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCHostControl (  
    [in] IGCHostControl* pGCHostControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9282f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9282f-105">Parameters</span></span>  
 `pGCHostControl`  
 <span data-ttu-id="9282f-106">podczas Wskaźnik do obiektu [IGCHostControl](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md) , który umożliwia modułowi wyrzucania elementów bezużytecznych żądanie zmiany limitów pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="9282f-106">[in] A pointer to an [IGCHostControl](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md) object that allows the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9282f-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9282f-107">Requirements</span></span>  
 <span data-ttu-id="9282f-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9282f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9282f-109">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9282f-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9282f-110">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9282f-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9282f-111">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9282f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9282f-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9282f-112">See also</span></span>

- [<span data-ttu-id="9282f-113">ICorConfiguration, interfejs</span><span class="sxs-lookup"><span data-stu-id="9282f-113">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
