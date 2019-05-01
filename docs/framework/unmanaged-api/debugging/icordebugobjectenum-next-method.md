---
title: ICorDebugObjectEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugObjectEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectEnum::Next
helpviewer_keywords:
- Next method, ICorDebugObjectEnum interface [.NET Framework debugging]
- ICorDebugObjectEnum::Next method [.NET Framework debugging]
ms.assetid: 10093e3d-26b6-4ad7-8ef3-bbf66243fc02
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6998be3daf0ab6a6290a3400b96c32227df3e022
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942379"
---
# <a name="icordebugobjectenumnext-method"></a><span data-ttu-id="a8a13-102">ICorDebugObjectEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="a8a13-102">ICorDebugObjectEnum::Next Method</span></span>
<span data-ttu-id="a8a13-103">Pobiera względnych adresów wirtualnych (RVA) określoną liczbę obiektów z wyliczenia, zaczynając od bieżącej pozycji.</span><span class="sxs-lookup"><span data-stu-id="a8a13-103">Gets the relative virtual addresses (RVAs) of the specified number of objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8a13-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a8a13-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]    
        CORDB_ADDRESS objects[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8a13-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a8a13-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="a8a13-106">[in] Liczba obiektów, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="a8a13-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="a8a13-107">[out] Tablica wskaźników, z których każdy wskazuje obiekt CORDB_ADDRESS.</span><span class="sxs-lookup"><span data-stu-id="a8a13-107">[out] An array of pointers, each of which points to a CORDB_ADDRESS object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="a8a13-108">[out] Wskaźnik do liczby obiektów rzeczywistego zwrotu.</span><span class="sxs-lookup"><span data-stu-id="a8a13-108">[out] Pointer to the number of objects actually returned.</span></span> <span data-ttu-id="a8a13-109">Ta wartość może mieć wartości null Jeśli `celt` jeden.</span><span class="sxs-lookup"><span data-stu-id="a8a13-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8a13-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a8a13-110">Requirements</span></span>  
 <span data-ttu-id="a8a13-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8a13-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8a13-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a8a13-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a8a13-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a8a13-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8a13-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8a13-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8a13-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a8a13-115">See also</span></span>
