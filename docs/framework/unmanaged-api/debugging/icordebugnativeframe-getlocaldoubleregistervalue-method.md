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
ms.openlocfilehash: ed7436ff73fa9cc19790859581930875f39e499e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746284"
---
# <a name="icordebugnativeframegetlocaldoubleregistervalue-method"></a><span data-ttu-id="9b77a-102">ICorDebugNativeFrame::GetLocalDoubleRegisterValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="9b77a-102">ICorDebugNativeFrame::GetLocalDoubleRegisterValue Method</span></span>
<span data-ttu-id="9b77a-103">Pobiera wartość argumentu lub zmiennej lokalnej, która jest przechowywana w dwóch rejestruje określony dla tej ramki natywne.</span><span class="sxs-lookup"><span data-stu-id="9b77a-103">Gets the value of an argument or local variable that is stored in the two specified registers for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b77a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9b77a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalDoubleRegisterValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CorDebugRegister   lowWordReg,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b77a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9b77a-105">Parameters</span></span>  
 `highWordReg`  
 <span data-ttu-id="9b77a-106">[in] Wartość wyliczenia "Cordebugregister —", określający rejestru zawierającego słowo wysokiej wartości.</span><span class="sxs-lookup"><span data-stu-id="9b77a-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the high word of the value.</span></span>  
  
 `lowWordReg`  
 <span data-ttu-id="9b77a-107">[in] Wartość `CorDebugRegister` wyliczenie, które określa rejestru zawierające niskich słowo wartości.</span><span class="sxs-lookup"><span data-stu-id="9b77a-107">[in] A value of the `CorDebugRegister` enumeration that specifies the register containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="9b77a-108">[in] Liczba całkowita określająca rozmiar podpisu metadanych binarny, który odwołuje się do niej `pvSigBlob` parametru.</span><span class="sxs-lookup"><span data-stu-id="9b77a-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="9b77a-109">[in] A `PCCOR_SIGNATURE` wartość, która wskazuje podpisu metadanych binarny o typie wartości.</span><span class="sxs-lookup"><span data-stu-id="9b77a-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="9b77a-110">[out] Wskaźnik na adres "ICorDebugValue" obiekt reprezentujący pobrana wartość, która jest przechowywana w określonej rejestrów.</span><span class="sxs-lookup"><span data-stu-id="9b77a-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified registers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b77a-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9b77a-111">Remarks</span></span>  
 <span data-ttu-id="9b77a-112">`GetLocalDoubleRegisterValue` Metoda może być używana w ramka natywna lub just-in-time (JIT)-skompilowany ramki.</span><span class="sxs-lookup"><span data-stu-id="9b77a-112">The `GetLocalDoubleRegisterValue` method can be used either in a native frame or a just-in-time (JIT)-compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b77a-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9b77a-113">Requirements</span></span>  
 <span data-ttu-id="9b77a-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b77a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b77a-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9b77a-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b77a-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b77a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b77a-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b77a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b77a-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9b77a-118">See also</span></span>
