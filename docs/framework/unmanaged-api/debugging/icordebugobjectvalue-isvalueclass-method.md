---
title: ICorDebugObjectValue::IsValueClass — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue.IsValueClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue::IsValueClass
helpviewer_keywords:
- ICorDebugObjectValue::IsValueClass method [.NET Framework debugging]
- IsValueClass method [.NET Framework debugging]
ms.assetid: 13d89a4a-5d9d-4a79-9600-5e2a98c3d166
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71e32211e6ab16fb5e4e2c624dbad3af5fd6b09f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994529"
---
# <a name="icordebugobjectvalueisvalueclass-method"></a><span data-ttu-id="43bb2-102">ICorDebugObjectValue::IsValueClass — Metoda</span><span class="sxs-lookup"><span data-stu-id="43bb2-102">ICorDebugObjectValue::IsValueClass Method</span></span>
<span data-ttu-id="43bb2-103">Pobiera wartość wskazującą, czy wartość tego obiektu jest typem wartości.</span><span class="sxs-lookup"><span data-stu-id="43bb2-103">Gets a value that indicates whether this object value is a value type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43bb2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="43bb2-104">Syntax</span></span>  
  
```  
HRESULT IsValueClass (  
    [out] BOOL               *pbIsValueClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43bb2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="43bb2-105">Parameters</span></span>  
 `pbIsValueClass`  
 <span data-ttu-id="43bb2-106">[out] Wskaźnik na wartość logiczną, która jest `true` Jeśli wartość obiektu reprezentowanego przez ten "ICorDebugObjectValue", jest typem wartości, a nie typu referencyjnego; w przeciwnym razie `pbIsValueClass` jest `false`.</span><span class="sxs-lookup"><span data-stu-id="43bb2-106">[out] A pointer to a Boolean value that is `true` if the object value, represented by this "ICorDebugObjectValue", is a value type rather than a reference type; otherwise, `pbIsValueClass` is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43bb2-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="43bb2-107">Requirements</span></span>  
 <span data-ttu-id="43bb2-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43bb2-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43bb2-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="43bb2-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="43bb2-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="43bb2-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="43bb2-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43bb2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43bb2-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="43bb2-112">See also</span></span>
