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
ms.openlocfilehash: 00e747e43f67533771665313f4d420e4725945cd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988094"
---
# <a name="icordebugmodulegetglobalvariablevalue-method"></a><span data-ttu-id="08781-102">ICorDebugModule::GetGlobalVariableValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="08781-102">ICorDebugModule::GetGlobalVariableValue Method</span></span>
<span data-ttu-id="08781-103">Pobiera wartość określonej zmiennej globalnej.</span><span class="sxs-lookup"><span data-stu-id="08781-103">Gets the value of the specified global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08781-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="08781-104">Syntax</span></span>  
  
```  
HRESULT GetGlobalVariableValue(  
    [in]  mdFieldDef      fieldDef,  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08781-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="08781-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="08781-106">[in] `mdFieldDef` Token, który odwołuje się do metadanych opisujących zmiennej globalnej.</span><span class="sxs-lookup"><span data-stu-id="08781-106">[in] An `mdFieldDef` token that references the metadata describing the global variable.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="08781-107">[out] Wskaźnik na adres obiektu ICorDebugValue, który reprezentuje wartość określonej zmiennej globalnej.</span><span class="sxs-lookup"><span data-stu-id="08781-107">[out] A pointer to the address of an ICorDebugValue object that represents the value of the specified global variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08781-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="08781-108">Requirements</span></span>  
 <span data-ttu-id="08781-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08781-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08781-110">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="08781-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="08781-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="08781-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08781-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08781-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
