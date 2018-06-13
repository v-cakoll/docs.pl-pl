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
ms.openlocfilehash: 48c2a394126aca3a10b38ab2ba2df945f53e45d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438275"
---
# <a name="icorconfigurationsetgchostcontrol-method"></a><span data-ttu-id="08d42-102">ICorConfiguration::SetGCHostControl — Metoda</span><span class="sxs-lookup"><span data-stu-id="08d42-102">ICorConfiguration::SetGCHostControl Method</span></span>
<span data-ttu-id="08d42-103">Ustawia wywołanie zwrotne interfejsu używanego przez moduł garbage collector na żądanie hosta, aby zmienić limit pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="08d42-103">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08d42-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="08d42-104">Syntax</span></span>  
  
```  
HRESULT SetGCHostControl (  
    [in] IGCHostControl* pGCHostControl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="08d42-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="08d42-105">Parameters</span></span>  
 `pGCHostControl`  
 <span data-ttu-id="08d42-106">[in] Wskaźnik do [IGCHostControl](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md) obiekt, który umożliwia modułu zbierającego elementy bezużyteczne na żądanie hosta, aby zmienić limit pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="08d42-106">[in] A pointer to an [IGCHostControl](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md) object that allows the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08d42-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="08d42-107">Requirements</span></span>  
 <span data-ttu-id="08d42-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08d42-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08d42-109">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="08d42-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="08d42-110">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="08d42-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="08d42-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08d42-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08d42-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="08d42-112">See Also</span></span>  
 [<span data-ttu-id="08d42-113">ICorConfiguration, interfejs</span><span class="sxs-lookup"><span data-stu-id="08d42-113">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
