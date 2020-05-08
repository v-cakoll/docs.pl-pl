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
ms.openlocfilehash: 12dc5466d5be73b327f171c389c41c55901f2915
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894957"
---
# <a name="icordebugassemblyenumeratemodules-method"></a><span data-ttu-id="22b32-102">ICorDebugAssembly::EnumerateModules — Metoda</span><span class="sxs-lookup"><span data-stu-id="22b32-102">ICorDebugAssembly::EnumerateModules Method</span></span>
<span data-ttu-id="22b32-103">Pobiera moduł wyliczający dla modułów zawartych w `ICorDebugAssembly`.</span><span class="sxs-lookup"><span data-stu-id="22b32-103">Gets an enumerator for the modules contained in the `ICorDebugAssembly`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22b32-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="22b32-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateModules (  
    [out] ICorDebugModuleEnum **ppModules  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22b32-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="22b32-105">Parameters</span></span>  
 `ppModules`  
 <span data-ttu-id="22b32-106">określoną Wskaźnik do adresu interfejsu ICorDebugModuleEnum, który jest modułem wyliczającym.</span><span class="sxs-lookup"><span data-stu-id="22b32-106">[out] A pointer to the address of the ICorDebugModuleEnum interface that is the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22b32-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="22b32-107">Requirements</span></span>  
 <span data-ttu-id="22b32-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22b32-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22b32-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="22b32-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="22b32-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="22b32-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22b32-111">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22b32-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
