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
ms.openlocfilehash: e9b32980a5606629676549905d3c9956633f25b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178700"
---
# <a name="icordebugobjectenumnext-method"></a><span data-ttu-id="23035-102">ICorDebugObjectEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="23035-102">ICorDebugObjectEnum::Next Method</span></span>
<span data-ttu-id="23035-103">Pobiera względne adresy wirtualne (RVA) określonej liczby obiektów z wyliczenia, począwszy od bieżącej pozycji.</span><span class="sxs-lookup"><span data-stu-id="23035-103">Gets the relative virtual addresses (RVAs) of the specified number of objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23035-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="23035-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]
        CORDB_ADDRESS objects[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="23035-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="23035-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="23035-106">[w] Liczba obiektów do pobrania.</span><span class="sxs-lookup"><span data-stu-id="23035-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="23035-107">[na zewnątrz] Tablica wskaźników, z których każdy wskazuje na obiekt CORDB_ADDRESS.</span><span class="sxs-lookup"><span data-stu-id="23035-107">[out] An array of pointers, each of which points to a CORDB_ADDRESS object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="23035-108">[na zewnątrz] Wskaźnik do liczby obiektów faktycznie zwróconych.</span><span class="sxs-lookup"><span data-stu-id="23035-108">[out] Pointer to the number of objects actually returned.</span></span> <span data-ttu-id="23035-109">Ta wartość może `celt` być null, jeśli jest jednym.</span><span class="sxs-lookup"><span data-stu-id="23035-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23035-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="23035-110">Requirements</span></span>  
 <span data-ttu-id="23035-111">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23035-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23035-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="23035-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="23035-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="23035-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23035-114">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23035-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23035-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="23035-115">See also</span></span>
