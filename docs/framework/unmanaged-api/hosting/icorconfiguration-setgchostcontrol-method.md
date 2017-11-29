---
title: "ICorConfiguration::SetGCHostControl — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorConfiguration.SetGCHostControl
api_location: mscoree.dll
api_type: COM
f1_keywords: SetGCHostControl
helpviewer_keywords:
- ICorConfiguration::SetGCHostControl method [.NET Framework hosting]
- SetGCHostControl method [.NET Framework hosting]
ms.assetid: bca6bd79-e288-475a-aa46-6bf81541d966
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 33d01ff208e9814e73c7a658e41819348da6831a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorconfigurationsetgchostcontrol-method"></a><span data-ttu-id="7e039-102">ICorConfiguration::SetGCHostControl — Metoda</span><span class="sxs-lookup"><span data-stu-id="7e039-102">ICorConfiguration::SetGCHostControl Method</span></span>
<span data-ttu-id="7e039-103">Ustawia wywołanie zwrotne interfejsu używanego przez moduł garbage collector na żądanie hosta, aby zmienić limit pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="7e039-103">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e039-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7e039-104">Syntax</span></span>  
  
```  
HRESULT SetGCHostControl (  
    [in] IGCHostControl* pGCHostControl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7e039-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7e039-105">Parameters</span></span>  
 `pGCHostControl`  
 <span data-ttu-id="7e039-106">[in] Wskaźnik do [IGCHostControl](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md) obiekt, który umożliwia modułu zbierającego elementy bezużyteczne na żądanie hosta, aby zmienić limit pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="7e039-106">[in] A pointer to an [IGCHostControl](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md) object that allows the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e039-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7e039-107">Requirements</span></span>  
 <span data-ttu-id="7e039-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e039-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e039-109">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7e039-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7e039-110">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7e039-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7e039-111">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e039-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e039-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7e039-112">See Also</span></span>  
 [<span data-ttu-id="7e039-113">ICorConfiguration — interfejs</span><span class="sxs-lookup"><span data-stu-id="7e039-113">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
