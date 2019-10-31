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
ms.openlocfilehash: b55bd41039fce84a21c5d651d93b56f5d84b7611
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088177"
---
# <a name="icordebugassemblyenumeratemodules-method"></a><span data-ttu-id="80154-102">ICorDebugAssembly::EnumerateModules — Metoda</span><span class="sxs-lookup"><span data-stu-id="80154-102">ICorDebugAssembly::EnumerateModules Method</span></span>
<span data-ttu-id="80154-103">Pobiera moduł wyliczający dla modułów zawartych w `ICorDebugAssembly`.</span><span class="sxs-lookup"><span data-stu-id="80154-103">Gets an enumerator for the modules contained in the `ICorDebugAssembly`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80154-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="80154-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateModules (  
    [out] ICorDebugModuleEnum **ppModules  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80154-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="80154-105">Parameters</span></span>  
 `ppModules`  
 <span data-ttu-id="80154-106">określoną Wskaźnik do adresu interfejsu ICorDebugModuleEnum, który jest modułem wyliczającym.</span><span class="sxs-lookup"><span data-stu-id="80154-106">[out] A pointer to the address of the ICorDebugModuleEnum interface that is the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80154-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="80154-107">Requirements</span></span>  
 <span data-ttu-id="80154-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80154-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80154-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="80154-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="80154-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="80154-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80154-111">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80154-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
