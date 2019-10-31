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
ms.openlocfilehash: 243000a2399b4938a3ad7f732c64e2f79b664f51
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131060"
---
# <a name="icordebugilcode2getlocalvarsigtoken-method"></a><span data-ttu-id="4ceb9-102">Metoda ICorDebugILCode2::GetLocalVarSigToken</span><span class="sxs-lookup"><span data-stu-id="4ceb9-102">ICorDebugILCode2::GetLocalVarSigToken Method</span></span>
<span data-ttu-id="4ceb9-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="4ceb9-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="4ceb9-104">Pobiera token metadanych lokalnej zmiennej sygnatury dla funkcji reprezentowanej przez to wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="4ceb9-104">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ceb9-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4ceb9-105">Syntax</span></span>  
  
```cpp
HRESULT GetLocalVarSigToken(  
   [out] mdSignature *pmdSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ceb9-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4ceb9-106">Parameters</span></span>  
 `pmdSig`  
 <span data-ttu-id="4ceb9-107">określoną Wskaźnik do `mdSignature` token dla zmiennej lokalnej dla tej funkcji lub `mdSignatureNil`, jeśli nie ma sygnatury (czyli jeśli funkcja nie ma żadnych zmiennych lokalnych).</span><span class="sxs-lookup"><span data-stu-id="4ceb9-107">[out] A pointer to the `mdSignature` token for the local variable signature for this function, or `mdSignatureNil` if there is no signature (that is, if the function doesn't have any local variables).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4ceb9-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4ceb9-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ceb9-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4ceb9-109">Requirements</span></span>  
 <span data-ttu-id="4ceb9-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ceb9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ceb9-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4ceb9-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4ceb9-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4ceb9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4ceb9-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ceb9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ceb9-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4ceb9-114">See also</span></span>

- [<span data-ttu-id="4ceb9-115">ICorDebugILCode2, interfejs</span><span class="sxs-lookup"><span data-stu-id="4ceb9-115">ICorDebugILCode2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)
- [<span data-ttu-id="4ceb9-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="4ceb9-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
