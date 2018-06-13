---
title: ICorDebugNativeFrame::GetLocalDoubleRegisterValue — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalDoubleRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalDoubleRegisterValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalDoubleRegisterValue method [.NET Framework debugging]
- GetLocalDoubleRegisterValue method [.NET Framework debugging]
ms.assetid: 1f838215-ac8a-434f-8ce6-03021d3098d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9de77f942a1b89b0ab11ef71229e491a5305cafc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420755"
---
# <a name="icordebugnativeframegetlocaldoubleregistervalue-method"></a><span data-ttu-id="677d7-102">ICorDebugNativeFrame::GetLocalDoubleRegisterValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="677d7-102">ICorDebugNativeFrame::GetLocalDoubleRegisterValue Method</span></span>
<span data-ttu-id="677d7-103">Pobiera wartość argumentu lub zmiennej lokalnej, która jest przechowywana w dwóch rejestruje określony dla tej ramki natywnego.</span><span class="sxs-lookup"><span data-stu-id="677d7-103">Gets the value of an argument or local variable that is stored in the two specified registers for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="677d7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="677d7-104">Syntax</span></span>  
  
```  
HRESULT GetLocalDoubleRegisterValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CorDebugRegister   lowWordReg,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="677d7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="677d7-105">Parameters</span></span>  
 `highWordReg`  
 <span data-ttu-id="677d7-106">[in] Wartość określająca rejestru zawierającego słowo wysokiej wartości wyliczenia "CorDebugRegister".</span><span class="sxs-lookup"><span data-stu-id="677d7-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the high word of the value.</span></span>  
  
 `lowWordReg`  
 <span data-ttu-id="677d7-107">[in] Wartość `CorDebugRegister` wyliczenie określający zawierające słowo niskiej wartości rejestru.</span><span class="sxs-lookup"><span data-stu-id="677d7-107">[in] A value of the `CorDebugRegister` enumeration that specifies the register containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="677d7-108">[in] Liczba całkowita określająca rozmiar podpisu metadanych binarny, który odwołuje się do niego `pvSigBlob` parametru.</span><span class="sxs-lookup"><span data-stu-id="677d7-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="677d7-109">[in] A `PCCOR_SIGNATURE` wartość, która wskazuje podpisu metadanych binarnego typu wartości.</span><span class="sxs-lookup"><span data-stu-id="677d7-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="677d7-110">[out] Wskaźnik do adresu "ICorDebugValue" obiekt reprezentujący pobrana wartość, która znajduje się w rejestrach określony.</span><span class="sxs-lookup"><span data-stu-id="677d7-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified registers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="677d7-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="677d7-111">Remarks</span></span>  
 <span data-ttu-id="677d7-112">`GetLocalDoubleRegisterValue` Metoda może być używana w ramka natywna lub just-in-time (JIT)-skompilowany ramki.</span><span class="sxs-lookup"><span data-stu-id="677d7-112">The `GetLocalDoubleRegisterValue` method can be used either in a native frame or a just-in-time (JIT)-compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="677d7-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="677d7-113">Requirements</span></span>  
 <span data-ttu-id="677d7-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="677d7-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="677d7-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="677d7-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="677d7-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="677d7-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="677d7-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="677d7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="677d7-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="677d7-118">See Also</span></span>  
 
