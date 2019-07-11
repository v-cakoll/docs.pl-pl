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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a23c2793dce5be459b3aa0f183179c584592c115
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779876"
---
# <a name="icorconfigurationsetgchostcontrol-method"></a><span data-ttu-id="c3555-102">ICorConfiguration::SetGCHostControl — Metoda</span><span class="sxs-lookup"><span data-stu-id="c3555-102">ICorConfiguration::SetGCHostControl Method</span></span>
<span data-ttu-id="c3555-103">Określa interfejs wywołania zwrotnego do użycia przez moduł zbierający elementy bezużyteczne na żądanie hosta, aby zmienić limity pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="c3555-103">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3555-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c3555-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCHostControl (  
    [in] IGCHostControl* pGCHostControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3555-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c3555-105">Parameters</span></span>  
 `pGCHostControl`  
 <span data-ttu-id="c3555-106">[in] Wskaźnik do [igchostcontrol —](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md) obiekt, który pozwala modułowi odśmiecania żądanie hosta, aby zmienić limity pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="c3555-106">[in] A pointer to an [IGCHostControl](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md) object that allows the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3555-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c3555-107">Requirements</span></span>  
 <span data-ttu-id="c3555-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3555-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3555-109">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c3555-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c3555-110">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c3555-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c3555-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3555-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3555-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c3555-112">See also</span></span>

- [<span data-ttu-id="c3555-113">ICorConfiguration, interfejs</span><span class="sxs-lookup"><span data-stu-id="c3555-113">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
