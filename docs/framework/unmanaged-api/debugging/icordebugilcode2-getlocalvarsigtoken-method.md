---
title: Metoda ICorDebugILCode2::GetLocalVarSigToken
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- cpp
api_name:
- ICorDebugILCode2.GetLocalVarSigToken
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 17665b77-1342-4115-94fd-9f45b0ecfb0f
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 47004375194438b1ef0aaf61144ba6f16278545b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilcode2getlocalvarsigtoken-method"></a><span data-ttu-id="d1250-102">Metoda ICorDebugILCode2::GetLocalVarSigToken</span><span class="sxs-lookup"><span data-stu-id="d1250-102">ICorDebugILCode2::GetLocalVarSigToken Method</span></span>
<span data-ttu-id="d1250-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="d1250-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="d1250-104">Pobiera token metadanych dla zmiennej podpisu lokalnego dla funkcji, która jest reprezentowana przez to wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="d1250-104">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1250-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d1250-105">Syntax</span></span>  
  
```cpp
HRESULT GetLocalVarSigToken(  
   [out] mdSignature *pmdSig  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d1250-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d1250-106">Parameters</span></span>  
 `pmdSig`  
 <span data-ttu-id="d1250-107">[out] Wskaźnik do `mdSignature` tokenu dla zmiennej podpisu lokalnego dla tej funkcji, lub `mdSignatureNil` Jeśli nie istnieje sygnatura nie (Jeśli funkcja nie ma żadnych zmiennych lokalnych).</span><span class="sxs-lookup"><span data-stu-id="d1250-107">[out] A pointer to the `mdSignature` token for the local variable signature for this function, or `mdSignatureNil` if there is no signature (that is, if the function doesn't have any local variables).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1250-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d1250-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1250-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d1250-109">Requirements</span></span>  
 <span data-ttu-id="d1250-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1250-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1250-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d1250-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d1250-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1250-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1250-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1250-113">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1250-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d1250-114">See Also</span></span>  
 [<span data-ttu-id="d1250-115">ICorDebugILCode2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1250-115">ICorDebugILCode2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)  
 [<span data-ttu-id="d1250-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="d1250-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
