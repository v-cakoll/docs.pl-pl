---
title: ICorDebugBoxValue::GetObject — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugBoxValue.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBoxValue::GetObject
helpviewer_keywords:
- ICorDebugBoxValue::GetObject method [.NET Framework debugging]
- GetObject method, ICorDebugBoxValue interface [.NET Framework debugging]
ms.assetid: 3a867a5b-bf94-493f-a4f5-b28685cf5325
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 30038d383e78c23715b844df0bee7c1124885a69
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745224"
---
# <a name="icordebugboxvaluegetobject-method"></a><span data-ttu-id="8a915-102">ICorDebugBoxValue::GetObject — Metoda</span><span class="sxs-lookup"><span data-stu-id="8a915-102">ICorDebugBoxValue::GetObject Method</span></span>
<span data-ttu-id="8a915-103">Pobiera wartości spakowanej.</span><span class="sxs-lookup"><span data-stu-id="8a915-103">Gets the boxed value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a915-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8a915-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a915-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8a915-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="8a915-106">[out] Wskaźnik na adres obiektu ICorDebugObjectValue, który reprezentuje wartości spakowanej.</span><span class="sxs-lookup"><span data-stu-id="8a915-106">[out] A pointer to the address of an ICorDebugObjectValue object that represents the boxed value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a915-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8a915-107">Requirements</span></span>  
 <span data-ttu-id="8a915-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a915-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a915-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8a915-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8a915-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a915-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a915-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a915-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
