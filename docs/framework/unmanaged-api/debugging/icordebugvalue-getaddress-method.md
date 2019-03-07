---
title: ICorDebugValue::GetAddress — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetAddress
helpviewer_keywords:
- ICorDebugValue::GetAddress method [.NET Framework debugging]
- GetAddress method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: a247c792-45e1-4538-9e1f-b46acca4a463
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6f8a9c62a1be682d3f0259c27f311e2dcbb2f11
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492728"
---
# <a name="icordebugvaluegetaddress-method"></a><span data-ttu-id="bc6c3-102">ICorDebugValue::GetAddress — Metoda</span><span class="sxs-lookup"><span data-stu-id="bc6c3-102">ICorDebugValue::GetAddress Method</span></span>
<span data-ttu-id="bc6c3-103">Pobiera adres tego obiektu "ICorDebugValue", który jest w trakcie debugowania.</span><span class="sxs-lookup"><span data-stu-id="bc6c3-103">Gets the address of this "ICorDebugValue" object, which is in the process of being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc6c3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bc6c3-104">Syntax</span></span>  
  
```  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS   *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc6c3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bc6c3-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="bc6c3-106">[out] Wskaźnik do `CORDB_ADDRESS` obiekt, który określa adres obiektu tej wartości.</span><span class="sxs-lookup"><span data-stu-id="bc6c3-106">[out] Pointer to a `CORDB_ADDRESS` object that specifies the address of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc6c3-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bc6c3-107">Remarks</span></span>  
 <span data-ttu-id="bc6c3-108">Jeśli wartość jest niedostępna, zwracany jest 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="bc6c3-108">If the value is unavailable, 0 (zero) is returned.</span></span> <span data-ttu-id="bc6c3-109">To może się zdarzyć, jeśli wartość wynosi co najmniej częściowo w rejestrach ani przechowywane na uchwyt modułu odśmiecania pamięci (`GCHandle`).</span><span class="sxs-lookup"><span data-stu-id="bc6c3-109">This could happen if the value is at least partly in registers or stored in a garbage collector handle (`GCHandle`).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc6c3-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bc6c3-110">Requirements</span></span>  
 <span data-ttu-id="bc6c3-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc6c3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc6c3-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bc6c3-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bc6c3-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bc6c3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc6c3-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc6c3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc6c3-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bc6c3-115">See also</span></span>

