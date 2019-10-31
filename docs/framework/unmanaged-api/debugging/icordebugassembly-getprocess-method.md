---
title: ICorDebugAssembly::GetProcess — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetProcess
helpviewer_keywords:
- ICorDebugAssembly::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: ea52be06-0a16-4f57-afca-4287d72e76c4
topic_type:
- apiref
ms.openlocfilehash: 49b234b065eb66dc2ec0bc7e991117c5b54a92f3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73196347"
---
# <a name="icordebugassemblygetprocess-method"></a><span data-ttu-id="d1127-102">ICorDebugAssembly::GetProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="d1127-102">ICorDebugAssembly::GetProcess Method</span></span>
<span data-ttu-id="d1127-103">Pobiera wskaźnik interfejsu do procesu, w którym działa to wystąpienie ICorDebugAssembly.</span><span class="sxs-lookup"><span data-stu-id="d1127-103">Gets an interface pointer to the process in which this ICorDebugAssembly instance is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1127-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d1127-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1127-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d1127-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="d1127-106">określoną Wskaźnik do interfejsu ICorDebugProcess, który reprezentuje proces.</span><span class="sxs-lookup"><span data-stu-id="d1127-106">[out] A pointer to an ICorDebugProcess interface that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1127-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d1127-107">Requirements</span></span>  
 <span data-ttu-id="d1127-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1127-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1127-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d1127-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d1127-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d1127-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1127-111">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1127-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
