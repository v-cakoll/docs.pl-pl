---
title: "ICorDebugFrameEnum::Next — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFrameEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFrameEnum::Next
helpviewer_keywords:
- ICorDebugFrameEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugFrameEnum interface [.NET Framework debugging]
ms.assetid: 0bc96acb-6179-4328-a447-cda562ce9e98
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a2139661621d7ebe2bf20e96b400096393964b89
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugframeenumnext-method"></a><span data-ttu-id="8b4f3-102">ICorDebugFrameEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="8b4f3-102">ICorDebugFrameEnum::Next Method</span></span>
<span data-ttu-id="8b4f3-103">Pobiera określoną liczbę wystąpień ICorDebugFrame, zaczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="8b4f3-103">Gets the specified number of ICorDebugFrame instances, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b4f3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8b4f3-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugFrame *frames[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8b4f3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8b4f3-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="8b4f3-106">[in] Liczba `ICorDebugFrame` wystąpienia mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="8b4f3-106">[in] The number of `ICorDebugFrame` instances to be retrieved.</span></span>  
  
 `frames`  
 <span data-ttu-id="8b4f3-107">[out] Tablicy wskaźników, z których każdy wskazuje `ICorDebugFrame` obiektu.</span><span class="sxs-lookup"><span data-stu-id="8b4f3-107">[out] An array of pointers, each of which points to an `ICorDebugFrame` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="8b4f3-108">[out] Wskaźnik do liczby `ICorDebugFrame` wystąpienia faktycznie zwracane.</span><span class="sxs-lookup"><span data-stu-id="8b4f3-108">[out] A pointer to the number of `ICorDebugFrame` instances actually returned.</span></span> <span data-ttu-id="8b4f3-109">Ta wartość może mieć wartości zerowej Jeśli `celt` jeden.</span><span class="sxs-lookup"><span data-stu-id="8b4f3-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b4f3-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8b4f3-110">Requirements</span></span>  
 <span data-ttu-id="8b4f3-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b4f3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b4f3-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8b4f3-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8b4f3-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b4f3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b4f3-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b4f3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
