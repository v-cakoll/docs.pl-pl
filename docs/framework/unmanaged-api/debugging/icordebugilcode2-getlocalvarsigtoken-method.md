---
title: Metoda ICorDebugILCode2::GetLocalVarSigToken
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9810a8a55fc9c5296bffa5106551f9734dcd61bb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59199911"
---
# <a name="icordebugilcode2getlocalvarsigtoken-method"></a><span data-ttu-id="d98ef-102">Metoda ICorDebugILCode2::GetLocalVarSigToken</span><span class="sxs-lookup"><span data-stu-id="d98ef-102">ICorDebugILCode2::GetLocalVarSigToken Method</span></span>
<span data-ttu-id="d98ef-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="d98ef-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="d98ef-104">Pobiera token metadanych dla lokalnej zmiennej podpisu dla funkcji, która jest reprezentowana przez to wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="d98ef-104">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d98ef-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d98ef-105">Syntax</span></span>  
  
```cpp
HRESULT GetLocalVarSigToken(  
   [out] mdSignature *pmdSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d98ef-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d98ef-106">Parameters</span></span>  
 `pmdSig`  
 <span data-ttu-id="d98ef-107">[out] Wskaźnik do `mdSignature` tokenu dla lokalnej zmiennej podpisu dla tej funkcji lub `mdSignatureNil` czy brak podpisu (to znaczy, jeśli funkcja nie ma żadnych zmiennych lokalnych).</span><span class="sxs-lookup"><span data-stu-id="d98ef-107">[out] A pointer to the `mdSignature` token for the local variable signature for this function, or `mdSignatureNil` if there is no signature (that is, if the function doesn't have any local variables).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d98ef-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d98ef-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d98ef-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d98ef-109">Requirements</span></span>  
 <span data-ttu-id="d98ef-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d98ef-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d98ef-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d98ef-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d98ef-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d98ef-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="d98ef-113">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="d98ef-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d98ef-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d98ef-114">See also</span></span>

- [<span data-ttu-id="d98ef-115">Interfejs ICorDebugILCode2</span><span class="sxs-lookup"><span data-stu-id="d98ef-115">ICorDebugILCode2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)
- [<span data-ttu-id="d98ef-116">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="d98ef-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
