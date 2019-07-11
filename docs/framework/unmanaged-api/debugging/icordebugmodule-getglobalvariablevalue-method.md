---
title: ICorDebugModule::GetGlobalVariableValue — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetGlobalVariableValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetGlobalVariableValue
helpviewer_keywords:
- ICorDebugModule::GetGlobalVariableValue method [.NET Framework debugging]
- GetGlobalVariableValue method [.NET Framework debugging]
ms.assetid: bbc0881c-6a59-41a0-b5ee-2f3d1b71684c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd79299dcfdb03b703c2cab214ba448631daa6f2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763481"
---
# <a name="icordebugmodulegetglobalvariablevalue-method"></a><span data-ttu-id="0013f-102">ICorDebugModule::GetGlobalVariableValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="0013f-102">ICorDebugModule::GetGlobalVariableValue Method</span></span>
<span data-ttu-id="0013f-103">Pobiera wartość określonej zmiennej globalnej.</span><span class="sxs-lookup"><span data-stu-id="0013f-103">Gets the value of the specified global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0013f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0013f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGlobalVariableValue(  
    [in]  mdFieldDef      fieldDef,  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0013f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0013f-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="0013f-106">[in] `mdFieldDef` Token, który odwołuje się do metadanych opisujących zmiennej globalnej.</span><span class="sxs-lookup"><span data-stu-id="0013f-106">[in] An `mdFieldDef` token that references the metadata describing the global variable.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="0013f-107">[out] Wskaźnik na adres obiektu ICorDebugValue, który reprezentuje wartość określonej zmiennej globalnej.</span><span class="sxs-lookup"><span data-stu-id="0013f-107">[out] A pointer to the address of an ICorDebugValue object that represents the value of the specified global variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0013f-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0013f-108">Requirements</span></span>  
 <span data-ttu-id="0013f-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0013f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0013f-110">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0013f-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0013f-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0013f-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0013f-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0013f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
