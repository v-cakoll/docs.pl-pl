---
title: ICorDebugNativeFrame::GetLocalRegisterValue — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalRegisterValue
helpviewer_keywords:
- GetLocalRegisterValue method [.NET Framework debugging]
- ICorDebugNativeFrame::GetLocalRegisterValue method [.NET Framework debugging]
ms.assetid: 5ccb74f3-f891-430c-b70a-e370624edde2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e6512871bf9a5cb0219a470267d1be4ecd403b3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478365"
---
# <a name="icordebugnativeframegetlocalregistervalue-method"></a><span data-ttu-id="e91e0-102">ICorDebugNativeFrame::GetLocalRegisterValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="e91e0-102">ICorDebugNativeFrame::GetLocalRegisterValue Method</span></span>
<span data-ttu-id="e91e0-103">Pobiera wartość argumentu lub zmiennej lokalnej, która jest przechowywana w rejestrze określonej dla tej ramki natywne.</span><span class="sxs-lookup"><span data-stu-id="e91e0-103">Gets the value of an argument or local variable that is stored in the specified register for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e91e0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e91e0-104">Syntax</span></span>  
  
```  
HRESULT GetLocalRegisterValue (  
    [in]  CorDebugRegister   reg,  
    [in]  ULONG              cbSigBlob,  
    [in]  PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e91e0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e91e0-105">Parameters</span></span>  
 `reg`  
 <span data-ttu-id="e91e0-106">[in] Wartość wyliczenia "cordebugregister —", który określa rejestru zawierającego wartość.</span><span class="sxs-lookup"><span data-stu-id="e91e0-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="e91e0-107">[in] Liczba całkowita określająca rozmiar podpisu metadanych binarny, który odwołuje się do niej `pvSigBlob` parametru.</span><span class="sxs-lookup"><span data-stu-id="e91e0-107">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="e91e0-108">[in] A `PCCOR_SIGNATURE` wartość, która wskazuje podpisu metadanych binarny o typie wartości.</span><span class="sxs-lookup"><span data-stu-id="e91e0-108">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="e91e0-109">[out] Wskaźnik na adres "ICorDebugValue" obiekt reprezentujący pobrana wartość, która jest przechowywana w określonej rejestru.</span><span class="sxs-lookup"><span data-stu-id="e91e0-109">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e91e0-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e91e0-110">Remarks</span></span>  
 <span data-ttu-id="e91e0-111">`GetLocalRegisterValue` Metoda może być używana w ramka natywna lub just-in-time (JIT)-skompilowany ramki.</span><span class="sxs-lookup"><span data-stu-id="e91e0-111">The `GetLocalRegisterValue` method can be used either in a native frame or a just-in-time (JIT)-compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e91e0-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e91e0-112">Requirements</span></span>  
 <span data-ttu-id="e91e0-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e91e0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e91e0-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e91e0-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e91e0-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e91e0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e91e0-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e91e0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e91e0-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e91e0-117">See also</span></span>

