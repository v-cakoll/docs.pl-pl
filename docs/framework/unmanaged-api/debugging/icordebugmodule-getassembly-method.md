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
ms.openlocfilehash: 78bfc91bdd0f9fa68252c6a07e1362807eb507b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416026"
---
# <a name="icordebugmodulegetassembly-method"></a><span data-ttu-id="5f238-102">ICorDebugModule::GetAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="5f238-102">ICorDebugModule::GetAssembly Method</span></span>
<span data-ttu-id="5f238-103">Pobiera zestaw zawierający dla tego modułu.</span><span class="sxs-lookup"><span data-stu-id="5f238-103">Gets the containing assembly for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f238-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5f238-104">Syntax</span></span>  
  
```  
HRESULT GetAssembly(  
    [out] ICorDebugAssembly **ppAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5f238-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5f238-105">Parameters</span></span>  
 `ppAssembly`  
 <span data-ttu-id="5f238-106">[out] Wskaźnik do obiektu ICorDebugAssembly, który reprezentuje zestaw zawierający ten moduł.</span><span class="sxs-lookup"><span data-stu-id="5f238-106">[out] A pointer to an ICorDebugAssembly object that represents the assembly containing this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f238-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5f238-107">Requirements</span></span>  
 <span data-ttu-id="5f238-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f238-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f238-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5f238-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5f238-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5f238-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5f238-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f238-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
