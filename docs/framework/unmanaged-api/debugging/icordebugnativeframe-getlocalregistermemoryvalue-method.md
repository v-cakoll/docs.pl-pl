---
title: ICorDebugNativeFrame::GetLocalRegisterMemoryValue — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalRegisterMemoryValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalRegisterMemoryValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalRegisterMemoryValue method [.NET Framework debugging]
- GetLocalRegisterMemoryValue method [.NET Framework debugging]
ms.assetid: d350f69d-9aff-4f5a-8301-daea22dee2da
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a3a174953877d70a295e659220e71c337e45f392
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57495237"
---
# <a name="icordebugnativeframegetlocalregistermemoryvalue-method"></a><span data-ttu-id="49e07-102">ICorDebugNativeFrame::GetLocalRegisterMemoryValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="49e07-102">ICorDebugNativeFrame::GetLocalRegisterMemoryValue Method</span></span>
<span data-ttu-id="49e07-103">Pobiera wartość argumentu lub zmiennej lokalnej, z których word niski i wysoki word są przechowywane w lokalizacji w pamięci i określony rejestru, odpowiednio dla tej ramki natywne.</span><span class="sxs-lookup"><span data-stu-id="49e07-103">Gets the value of an argument or local variable, of which the low word and high word are stored in the memory location and specified register, respectively, for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49e07-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="49e07-104">Syntax</span></span>  
  
```  
HRESULT GetLocalRegisterMemoryValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CORDB_ADDRESS      lowWordAddress,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49e07-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="49e07-105">Parameters</span></span>  
 `highWordReg`  
 <span data-ttu-id="49e07-106">[in] Wartość wyliczenia "Cordebugregister —", określający rejestru zawierającego słowo wysokiej wartości.</span><span class="sxs-lookup"><span data-stu-id="49e07-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the high word of the value.</span></span>  
  
 `lowWordAddress`  
 <span data-ttu-id="49e07-107">[in] A `CORDB_ADDRESS` wartość, która określa lokalizację w pamięci zawierające niskich słowo wartości.</span><span class="sxs-lookup"><span data-stu-id="49e07-107">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="49e07-108">[in] Liczba całkowita określająca rozmiar podpisu metadanych binarny, który odwołuje się do niej `pvSigBlob` parametru.</span><span class="sxs-lookup"><span data-stu-id="49e07-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="49e07-109">[in] A `PCCOR_SIGNATURE` wartość, która wskazuje podpisu metadanych binarny o typie wartości.</span><span class="sxs-lookup"><span data-stu-id="49e07-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="49e07-110">[out] Wskaźnik na adres "ICorDebugValue" obiekt reprezentujący pobrana wartość, która jest przechowywana w określonej lokalizacji w rejestrze i pamięci.</span><span class="sxs-lookup"><span data-stu-id="49e07-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register and memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49e07-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="49e07-111">Requirements</span></span>  
 <span data-ttu-id="49e07-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49e07-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49e07-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="49e07-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="49e07-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="49e07-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49e07-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49e07-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49e07-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="49e07-116">See also</span></span>

