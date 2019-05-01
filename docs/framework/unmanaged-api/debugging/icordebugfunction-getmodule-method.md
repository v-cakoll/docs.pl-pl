---
title: ICorDebugFunction::GetModule — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetModule
helpviewer_keywords:
- ICorDebugFunction::GetModule method [.NET Framework debugging]
- GetModule method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: 5031a5d3-2564-412a-9007-e36d4631308a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1cefe84c482df3b20b5939e031ad76647f295d3e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995621"
---
# <a name="icordebugfunctiongetmodule-method"></a><span data-ttu-id="eecfe-102">ICorDebugFunction::GetModule — Metoda</span><span class="sxs-lookup"><span data-stu-id="eecfe-102">ICorDebugFunction::GetModule Method</span></span>
<span data-ttu-id="eecfe-103">Pobiera moduł, w którym ta funkcja jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="eecfe-103">Gets the module in which this function is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eecfe-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="eecfe-104">Syntax</span></span>  
  
```  
HRESULT GetModule (  
    [out] ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eecfe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eecfe-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="eecfe-106">[out] Wskaźnik na adres ICorDebugModule obiekt, który reprezentuje moduł, w którym ta funkcja jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="eecfe-106">[out] A pointer to the address of an ICorDebugModule object that represents the module in which this function is defined.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eecfe-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="eecfe-107">Requirements</span></span>  
 <span data-ttu-id="eecfe-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eecfe-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eecfe-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eecfe-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eecfe-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eecfe-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eecfe-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eecfe-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
