---
title: ICorDebugNativeFrame::GetLocalMemoryRegisterValue — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalMemoryRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalMemoryRegisterValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalMemoryRegisterValue method [.NET Framework debugging]
- GetLocalMemoryRegisterValue method
ms.assetid: 33a19f6e-1029-4d53-af64-19591c6e58ee
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9b2244ec1be6fc0e5e19fac5adc7ecb38d68a0af
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59081154"
---
# <a name="icordebugnativeframegetlocalmemoryregistervalue-method"></a><span data-ttu-id="8eb87-102">ICorDebugNativeFrame::GetLocalMemoryRegisterValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="8eb87-102">ICorDebugNativeFrame::GetLocalMemoryRegisterValue Method</span></span>
<span data-ttu-id="8eb87-103">Pobiera wartość argumentu lub zmiennej lokalnej, którego word niski i wysoki word są przechowywane w określonej rejestru i lokalizację w pamięci, odpowiednio dla tej ramki natywne.</span><span class="sxs-lookup"><span data-stu-id="8eb87-103">Gets the value of an argument or local variable, of which the low word and high word are stored in the specified register and memory location, respectively, for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8eb87-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8eb87-104">Syntax</span></span>  
  
```  
HRESULT GetLocalMemoryRegisterValue (  
    [in] CORDB_ADDRESS      highWordAddress,  
    [in] CorDebugRegister   lowWordRegister,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8eb87-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8eb87-105">Parameters</span></span>  
 `highWordAddress`  
 <span data-ttu-id="8eb87-106">[in] A `CORDB_ADDRESS` wartość, która określa lokalizację w pamięci zawierających wyraz wysokiej wartości.</span><span class="sxs-lookup"><span data-stu-id="8eb87-106">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the high word of the value.</span></span>  
  
 `lowWordRegister`  
 <span data-ttu-id="8eb87-107">[in] Wartość wyliczenia "Cordebugregister —", określający rejestru zawierające niskich słowo wartości.</span><span class="sxs-lookup"><span data-stu-id="8eb87-107">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="8eb87-108">[in] Liczba całkowita określająca rozmiar podpisu metadanych binarny, który odwołuje się do niej `pvSigBlob` parametru.</span><span class="sxs-lookup"><span data-stu-id="8eb87-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="8eb87-109">[in] A `PCCOR_SIGNATURE` wartość, która wskazuje podpisu metadanych binarny o typie wartości.</span><span class="sxs-lookup"><span data-stu-id="8eb87-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="8eb87-110">[out] Wskaźnik na adres "ICorDebugValue" obiekt reprezentujący pobrana wartość, która jest przechowywana w określonej lokalizacji w rejestrze i pamięci.</span><span class="sxs-lookup"><span data-stu-id="8eb87-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register and memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8eb87-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8eb87-111">Requirements</span></span>  
 <span data-ttu-id="8eb87-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8eb87-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8eb87-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8eb87-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8eb87-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8eb87-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8eb87-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8eb87-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8eb87-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8eb87-116">See also</span></span>
