---
title: ICorDebugFrameEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFrameEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrameEnum::Next
helpviewer_keywords:
- ICorDebugFrameEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugFrameEnum interface [.NET Framework debugging]
ms.assetid: 0bc96acb-6179-4328-a447-cda562ce9e98
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 68098895b2ad7f5c08d30f222777e52d4ee3f063
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995803"
---
# <a name="icordebugframeenumnext-method"></a><span data-ttu-id="4902a-102">ICorDebugFrameEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="4902a-102">ICorDebugFrameEnum::Next Method</span></span>
<span data-ttu-id="4902a-103">Pobiera określoną liczbę wystąpień ICorDebugFrame, zaczynając od bieżącej pozycji.</span><span class="sxs-lookup"><span data-stu-id="4902a-103">Gets the specified number of ICorDebugFrame instances, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4902a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4902a-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugFrame *frames[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4902a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4902a-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="4902a-106">[in] Liczba `ICorDebugFrame` wystąpienia mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="4902a-106">[in] The number of `ICorDebugFrame` instances to be retrieved.</span></span>  
  
 `frames`  
 <span data-ttu-id="4902a-107">[out] Tablica wskaźników, z których każdy wskazuje `ICorDebugFrame` obiektu.</span><span class="sxs-lookup"><span data-stu-id="4902a-107">[out] An array of pointers, each of which points to an `ICorDebugFrame` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="4902a-108">[out] Wskaźnik do liczby `ICorDebugFrame` wystąpień rzeczywistego zwrotu.</span><span class="sxs-lookup"><span data-stu-id="4902a-108">[out] A pointer to the number of `ICorDebugFrame` instances actually returned.</span></span> <span data-ttu-id="4902a-109">Ta wartość może mieć wartości null Jeśli `celt` jeden.</span><span class="sxs-lookup"><span data-stu-id="4902a-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4902a-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4902a-110">Requirements</span></span>  
 <span data-ttu-id="4902a-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4902a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4902a-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4902a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4902a-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4902a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4902a-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4902a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
