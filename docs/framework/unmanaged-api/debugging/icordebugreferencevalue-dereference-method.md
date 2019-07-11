---
title: ICorDebugReferenceValue::Dereference — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.Dereference
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::Dereference
helpviewer_keywords:
- ICorDebugReferenceValue::Dereference method [.NET Framework debugging]
- Dereference method [.NET Framework debugging]
ms.assetid: 5ec8cf76-3deb-4ce6-9a49-77a4c35d80b9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f2ea7ebff122622a0db46160d23574619664f8ad
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745022"
---
# <a name="icordebugreferencevaluedereference-method"></a><span data-ttu-id="26187-102">ICorDebugReferenceValue::Dereference — Metoda</span><span class="sxs-lookup"><span data-stu-id="26187-102">ICorDebugReferenceValue::Dereference Method</span></span>
<span data-ttu-id="26187-103">Pobiera obiekt, do którego istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="26187-103">Gets the object that is referenced.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26187-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="26187-104">Syntax</span></span>  
  
```cpp  
HRESULT Dereference (  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26187-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="26187-105">Parameters</span></span>  
 `ppValue`  
 <span data-ttu-id="26187-106">[out] Wskaźnik na adres ICorDebugValue, który reprezentuje obiekt, na który wskazuje ten obiekt ICorDebugReferenceValue.</span><span class="sxs-lookup"><span data-stu-id="26187-106">[out] A pointer to the address of an ICorDebugValue that represents the object to which this ICorDebugReferenceValue object points.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26187-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="26187-107">Remarks</span></span>  
 <span data-ttu-id="26187-108">`ICorDebugValue` Obiekt jest prawidłowy tylko w przypadku, gdy odwołanie, nie ma jeszcze wyłączone.</span><span class="sxs-lookup"><span data-stu-id="26187-108">The `ICorDebugValue` object is valid only while its reference has not yet been disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26187-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="26187-109">Requirements</span></span>  
 <span data-ttu-id="26187-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26187-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26187-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="26187-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="26187-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="26187-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26187-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26187-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
