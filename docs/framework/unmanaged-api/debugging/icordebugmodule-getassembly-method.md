---
title: ICorDebugModule::GetAssembly — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetAssembly
helpviewer_keywords:
- ICorDebugModule::GetAssembly method [.NET Framework debugging]
- GetAssembly method [.NET Framework debugging]
ms.assetid: 989762c4-3d15-4485-b8ee-69e0fa8ec895
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8ee602c85a2f591365d40984184780f70e8532bf
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762699"
---
# <a name="icordebugmodulegetassembly-method"></a><span data-ttu-id="9ca45-102">ICorDebugModule::GetAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="9ca45-102">ICorDebugModule::GetAssembly Method</span></span>
<span data-ttu-id="9ca45-103">Pobiera zawierające zestaw dla tego modułu.</span><span class="sxs-lookup"><span data-stu-id="9ca45-103">Gets the containing assembly for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ca45-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9ca45-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssembly(  
    [out] ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ca45-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9ca45-105">Parameters</span></span>  
 `ppAssembly`  
 <span data-ttu-id="9ca45-106">[out] Wskaźnik do obiektu ICorDebugAssembly, który reprezentuje zestaw zawierający ten moduł.</span><span class="sxs-lookup"><span data-stu-id="9ca45-106">[out] A pointer to an ICorDebugAssembly object that represents the assembly containing this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ca45-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9ca45-107">Requirements</span></span>  
 <span data-ttu-id="9ca45-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ca45-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ca45-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9ca45-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9ca45-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ca45-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ca45-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ca45-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
