---
title: IAssemblyName::Clone — Metoda
ms.date: 03/30/2017
api_name:
- IAssemblyName.Clone
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::Clone
helpviewer_keywords:
- Clone method, IAssemblyName interface [.NET Framework fusion]
- IAssemblyName::Clone method [.NET Framework fusion]
ms.assetid: 7b345e08-5e16-4e3d-a044-4e19d0892943
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2bf67506fca161a64dd5d4ee915031c155c49241
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754030"
---
# <a name="iassemblynameclone-method"></a><span data-ttu-id="d10af-102">IAssemblyName::Clone — Metoda</span><span class="sxs-lookup"><span data-stu-id="d10af-102">IAssemblyName::Clone Method</span></span>
<span data-ttu-id="d10af-103">Tworzy kopię pobieżną to [iassemblyname —](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="d10af-103">Creates a shallow copy of this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d10af-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d10af-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] IAssemblyName **pName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d10af-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d10af-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="d10af-106">[out] Zwrócone kopii tego `IAssemblyName` obiektu.</span><span class="sxs-lookup"><span data-stu-id="d10af-106">[out] The returned copy of this `IAssemblyName` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d10af-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d10af-107">Requirements</span></span>  
 <span data-ttu-id="d10af-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d10af-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d10af-109">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="d10af-109">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d10af-110">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d10af-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d10af-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d10af-111">See also</span></span>

- [<span data-ttu-id="d10af-112">IAssemblyName, interfejs</span><span class="sxs-lookup"><span data-stu-id="d10af-112">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
