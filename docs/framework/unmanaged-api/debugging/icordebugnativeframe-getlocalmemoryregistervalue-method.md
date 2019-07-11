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
ms.openlocfilehash: 5b8b871377db6da95a3d824461671241d7b163f5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746256"
---
# <a name="icordebugnativeframegetlocalmemoryregistervalue-method"></a><span data-ttu-id="e4d7e-102">ICorDebugNativeFrame::GetLocalMemoryRegisterValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="e4d7e-102">ICorDebugNativeFrame::GetLocalMemoryRegisterValue Method</span></span>
<span data-ttu-id="e4d7e-103">Pobiera wartość argumentu lub zmiennej lokalnej, którego word niski i wysoki word są przechowywane w określonej rejestru i lokalizację w pamięci, odpowiednio dla tej ramki natywne.</span><span class="sxs-lookup"><span data-stu-id="e4d7e-103">Gets the value of an argument or local variable, of which the low word and high word are stored in the specified register and memory location, respectively, for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4d7e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e4d7e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalMemoryRegisterValue (  
    [in] CORDB_ADDRESS      highWordAddress,  
    [in] CorDebugRegister   lowWordRegister,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4d7e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e4d7e-105">Parameters</span></span>  
 `highWordAddress`  
 <span data-ttu-id="e4d7e-106">[in] A `CORDB_ADDRESS` wartość, która określa lokalizację w pamięci zawierających wyraz wysokiej wartości.</span><span class="sxs-lookup"><span data-stu-id="e4d7e-106">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the high word of the value.</span></span>  
  
 `lowWordRegister`  
 <span data-ttu-id="e4d7e-107">[in] Wartość wyliczenia "Cordebugregister —", określający rejestru zawierające niskich słowo wartości.</span><span class="sxs-lookup"><span data-stu-id="e4d7e-107">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="e4d7e-108">[in] Liczba całkowita określająca rozmiar podpisu metadanych binarny, który odwołuje się do niej `pvSigBlob` parametru.</span><span class="sxs-lookup"><span data-stu-id="e4d7e-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="e4d7e-109">[in] A `PCCOR_SIGNATURE` wartość, która wskazuje podpisu metadanych binarny o typie wartości.</span><span class="sxs-lookup"><span data-stu-id="e4d7e-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="e4d7e-110">[out] Wskaźnik na adres "ICorDebugValue" obiekt reprezentujący pobrana wartość, która jest przechowywana w określonej lokalizacji w rejestrze i pamięci.</span><span class="sxs-lookup"><span data-stu-id="e4d7e-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register and memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4d7e-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e4d7e-111">Requirements</span></span>  
 <span data-ttu-id="e4d7e-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4d7e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4d7e-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e4d7e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e4d7e-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4d7e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4d7e-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4d7e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4d7e-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e4d7e-116">See also</span></span>
