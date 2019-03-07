---
title: ICorDebugNativeFrame::GetLocalMemoryValue — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalMemoryValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalMemoryValue
helpviewer_keywords:
- GetLocalMemoryValue method [.NET Framework debugging]
- ICorDebugNativeFrame::GetLocalMemoryValue method [.NET Framework debugging]
ms.assetid: b600b3a2-9908-42d8-8093-ab6f39e9a2c9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5a35072b788321d22cec6de2f05a2863341417dc
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474764"
---
# <a name="icordebugnativeframegetlocalmemoryvalue-method"></a><span data-ttu-id="2aac5-102">ICorDebugNativeFrame::GetLocalMemoryValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="2aac5-102">ICorDebugNativeFrame::GetLocalMemoryValue Method</span></span>
<span data-ttu-id="2aac5-103">Pobiera wartość argumentu lub zmiennej lokalnej, która jest przechowywana w określonej lokalizacji pamięci dla tej ramki natywne.</span><span class="sxs-lookup"><span data-stu-id="2aac5-103">Gets the value of an argument or local variable that is stored in the specified memory location for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2aac5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2aac5-104">Syntax</span></span>  
  
```  
HRESULT GetLocalMemoryValue (  
    [in]  CORDB_ADDRESS      address,  
    [in]  ULONG              cbSigBlob,  
    [in]  PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2aac5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2aac5-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="2aac5-106">[in] A `CORDB_ADDRESS` wartość, która określa lokalizację zawierającą wartość w pamięci.</span><span class="sxs-lookup"><span data-stu-id="2aac5-106">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="2aac5-107">[in] Liczba całkowita określająca rozmiar podpisu metadanych binarny, który odwołuje się do niej `pvSigBlob` parametru.</span><span class="sxs-lookup"><span data-stu-id="2aac5-107">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="2aac5-108">[in] A `PCCOR_SIGNATURE` wartość, która wskazuje podpisu metadanych binarny o typie wartości.</span><span class="sxs-lookup"><span data-stu-id="2aac5-108">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="2aac5-109">[out] Wskaźnik na adres "ICorDebugValue" obiekt reprezentujący pobrana wartość, która jest przechowywana w określonej lokalizacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="2aac5-109">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2aac5-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2aac5-110">Requirements</span></span>  
 <span data-ttu-id="2aac5-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2aac5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2aac5-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2aac5-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2aac5-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2aac5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2aac5-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2aac5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2aac5-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2aac5-115">See also</span></span>

