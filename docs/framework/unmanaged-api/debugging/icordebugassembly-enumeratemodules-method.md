---
title: ICorDebugAssembly::EnumerateModules — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.EnumerateModules
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::EnumerateModules
helpviewer_keywords:
- ICorDebugAssembly::EnumerateModules method [.NET Framework debugging]
- EnumerateModules method [.NET Framework debugging]
ms.assetid: c7ba51a1-0dd5-4452-b471-232febe0f897
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0f763151f4e450c48eb9304936541243af06bdca
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485320"
---
# <a name="icordebugassemblyenumeratemodules-method"></a><span data-ttu-id="3b9f9-102">ICorDebugAssembly::EnumerateModules — Metoda</span><span class="sxs-lookup"><span data-stu-id="3b9f9-102">ICorDebugAssembly::EnumerateModules Method</span></span>
<span data-ttu-id="3b9f9-103">Pobiera moduł wyliczający dla modułów zawarte w `ICorDebugAssembly`.</span><span class="sxs-lookup"><span data-stu-id="3b9f9-103">Gets an enumerator for the modules contained in the `ICorDebugAssembly`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b9f9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3b9f9-104">Syntax</span></span>  
  
```  
HRESULT EnumerateModules (  
    [out] ICorDebugModuleEnum **ppModules  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b9f9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3b9f9-105">Parameters</span></span>  
 `ppModules`  
 <span data-ttu-id="3b9f9-106">[out] Wskaźnik na adres icordebugmoduleenum — interfejs, który jest moduł wyliczający.</span><span class="sxs-lookup"><span data-stu-id="3b9f9-106">[out] A pointer to the address of the ICorDebugModuleEnum interface that is the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b9f9-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3b9f9-107">Requirements</span></span>  
 <span data-ttu-id="3b9f9-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b9f9-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b9f9-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3b9f9-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3b9f9-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3b9f9-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3b9f9-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b9f9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
