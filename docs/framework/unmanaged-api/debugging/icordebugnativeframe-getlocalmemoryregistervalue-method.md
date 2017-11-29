---
title: "ICorDebugNativeFrame::GetLocalMemoryRegisterValue — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame.GetLocalMemoryRegisterValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame::GetLocalMemoryRegisterValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalMemoryRegisterValue method [.NET Framework debugging]
- GetLocalMemoryRegisterValue method
ms.assetid: 33a19f6e-1029-4d53-af64-19591c6e58ee
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5a1a2b845b3d09fd147937e39cf4e7bec8ee7c8f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugnativeframegetlocalmemoryregistervalue-method"></a><span data-ttu-id="20914-102">ICorDebugNativeFrame::GetLocalMemoryRegisterValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="20914-102">ICorDebugNativeFrame::GetLocalMemoryRegisterValue Method</span></span>
<span data-ttu-id="20914-103">Pobiera wartość argumentu lub zmiennej lokalnej, z których word niski i wysoki word są przechowywane w określonym rejestrze i lokalizacji pamięci odpowiednio dla tego natywną.</span><span class="sxs-lookup"><span data-stu-id="20914-103">Gets the value of an argument or local variable, of which the low word and high word are stored in the specified register and memory location, respectively, for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20914-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="20914-104">Syntax</span></span>  
  
```  
HRESULT GetLocalMemoryRegisterValue (  
    [in] CORDB_ADDRESS      highWordAddress,  
    [in] CorDebugRegister   lowWordRegister,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="20914-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="20914-105">Parameters</span></span>  
 `highWordAddress`  
 <span data-ttu-id="20914-106">[in] A `CORDB_ADDRESS` wartość, która określa lokalizację pamięci zawierające słowo wysokiej wartości.</span><span class="sxs-lookup"><span data-stu-id="20914-106">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the high word of the value.</span></span>  
  
 `lowWordRegister`  
 <span data-ttu-id="20914-107">[in] Wartość określająca rejestru zawierającego słowo niskiej wartości wyliczenia "CorDebugRegister".</span><span class="sxs-lookup"><span data-stu-id="20914-107">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="20914-108">[in] Liczba całkowita określająca rozmiar podpisu metadanych binarny, który odwołuje się do niego `pvSigBlob` parametru.</span><span class="sxs-lookup"><span data-stu-id="20914-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="20914-109">[in] A `PCCOR_SIGNATURE` wartość, która wskazuje podpisu metadanych binarnego typu wartości.</span><span class="sxs-lookup"><span data-stu-id="20914-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="20914-110">[out] Wskaźnik do adresu "ICorDebugValue" obiekt reprezentujący pobranej wartości przechowywane w określonej lokalizacji rejestru i pamięci.</span><span class="sxs-lookup"><span data-stu-id="20914-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register and memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20914-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="20914-111">Requirements</span></span>  
 <span data-ttu-id="20914-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20914-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20914-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="20914-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="20914-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20914-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20914-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20914-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20914-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="20914-116">See Also</span></span>  
 
