---
title: ICorDebugModule::GetSize — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetSize method [.NET Framework debugging]
ms.assetid: 5c68375d-145d-46ef-a7c8-2dc4257472de
topic_type:
- apiref
ms.openlocfilehash: 402a0e8808b51fd4c09b254114292d4c851b2760
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129510"
---
# <a name="icordebugmodulegetsize-method"></a><span data-ttu-id="e37de-102">ICorDebugModule::GetSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="e37de-102">ICorDebugModule::GetSize Method</span></span>
<span data-ttu-id="e37de-103">Pobiera rozmiar (w bajtach) modułu.</span><span class="sxs-lookup"><span data-stu-id="e37de-103">Gets the size, in bytes, of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e37de-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e37de-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
    [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e37de-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e37de-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="e37de-106">określoną Rozmiar modułu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="e37de-106">[out] The size of the module in bytes.</span></span>  
  
 <span data-ttu-id="e37de-107">Jeśli moduł został wyprodukowany z generatora obrazu natywnego (NGen. exe), rozmiar modułu będzie równy zero.</span><span class="sxs-lookup"><span data-stu-id="e37de-107">If the module was produced from the native image generator (NGen.exe), the size of the module will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e37de-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e37de-108">Requirements</span></span>  
 <span data-ttu-id="e37de-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e37de-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e37de-110">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e37de-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e37de-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e37de-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e37de-112">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e37de-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
