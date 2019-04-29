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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645607"
---
# <a name="icordebugassemblyenumeratemodules-method"></a><span data-ttu-id="b798e-102">ICorDebugAssembly::EnumerateModules — Metoda</span><span class="sxs-lookup"><span data-stu-id="b798e-102">ICorDebugAssembly::EnumerateModules Method</span></span>
<span data-ttu-id="b798e-103">Pobiera moduł wyliczający dla modułów zawarte w `ICorDebugAssembly`.</span><span class="sxs-lookup"><span data-stu-id="b798e-103">Gets an enumerator for the modules contained in the `ICorDebugAssembly`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b798e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b798e-104">Syntax</span></span>  
  
```  
HRESULT EnumerateModules (  
    [out] ICorDebugModuleEnum **ppModules  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b798e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b798e-105">Parameters</span></span>  
 `ppModules`  
 <span data-ttu-id="b798e-106">[out] Wskaźnik na adres icordebugmoduleenum — interfejs, który jest moduł wyliczający.</span><span class="sxs-lookup"><span data-stu-id="b798e-106">[out] A pointer to the address of the ICorDebugModuleEnum interface that is the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b798e-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b798e-107">Requirements</span></span>  
 <span data-ttu-id="b798e-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b798e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b798e-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b798e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b798e-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b798e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b798e-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b798e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
