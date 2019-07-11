---
title: IAssemblyName::GetVersion — Metoda
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetVersion
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetVersion
helpviewer_keywords:
- IAssemblyName::GetVersion method [.NET Framework fusion]
- GetVersion method, IAssemblyName interface [.NET Framework fusion]
ms.assetid: 42230928-2c33-41fd-9519-d96efef6c7af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5b5f7ce6a4ce8f542b3c49fe4749bfde23ecf84
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744485"
---
# <a name="iassemblynamegetversion-method"></a><span data-ttu-id="e2468-102">IAssemblyName::GetVersion — Metoda</span><span class="sxs-lookup"><span data-stu-id="e2468-102">IAssemblyName::GetVersion Method</span></span>
<span data-ttu-id="e2468-103">Pobiera informacje o wersji dla zestawu odwołuje się ten [iassemblyname —](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="e2468-103">Gets the version information for the assembly referenced by this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2468-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e2468-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersion (  
    [out] LPDWORD pdwVersionHi,  
    [out] LPDWORD pdwVersionLow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2468-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e2468-105">Parameters</span></span>  
 `pdwVersionHi`  
 <span data-ttu-id="e2468-106">[out] Wysoka 32 bity wersji.</span><span class="sxs-lookup"><span data-stu-id="e2468-106">[out] The high 32 bits of the version.</span></span>  
  
 `pdwVersionLow`  
 <span data-ttu-id="e2468-107">[out] Niski 32 bity wersji.</span><span class="sxs-lookup"><span data-stu-id="e2468-107">[out] The low 32 bits of the version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2468-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e2468-108">Requirements</span></span>  
 <span data-ttu-id="e2468-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2468-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2468-110">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="e2468-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="e2468-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2468-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2468-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e2468-112">See also</span></span>

- [<span data-ttu-id="e2468-113">IAssemblyName, interfejs</span><span class="sxs-lookup"><span data-stu-id="e2468-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
