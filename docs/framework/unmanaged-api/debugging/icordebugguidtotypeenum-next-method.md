---
title: ICorDebugGuidToTypeEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugGuidToTypeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGuidToTypeEnum::Next
helpviewer_keywords:
- ICorDebugGuidToTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: c9937666-8e18-484d-9fe0-b9ac95199530
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 160ddbf9be8eb9f3b99d159aa8b36a22b58a9f55
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025809"
---
# <a name="icordebugguidtotypeenumnext-method"></a><span data-ttu-id="1b89c-102">ICorDebugGuidToTypeEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="1b89c-102">ICorDebugGuidToTypeEnum::Next Method</span></span>
<span data-ttu-id="1b89c-103">Pobiera określoną liczbę [cordebugguidtotypemapping —](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) wystąpień, które mapują identyfikatory GUID do informacji o typie.</span><span class="sxs-lookup"><span data-stu-id="1b89c-103">Gets the specified number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b89c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1b89c-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched] CorDebugGuidToTypeMapping values[  ],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b89c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1b89c-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="1b89c-106">[in] Liczba obiektów mapowania typu GUID do pobrania.</span><span class="sxs-lookup"><span data-stu-id="1b89c-106">[in] The number of GUID-to-type mapping objects to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="1b89c-107">[out] Tablica wskaźników, z których każdy wskazuje [cordebugguidtotypemapping —](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) obiekt, który mapuje jego odpowiedni obiekt ICorDebugType GUID środowiska wykonawczego Windows.</span><span class="sxs-lookup"><span data-stu-id="1b89c-107">[out] An array of pointers, each of which points to a [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) object that maps a Windows Runtime GUID to its corresponding ICorDebugType object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="1b89c-108">[out] Wskaźnik do liczby [cordebugguidtotypemapping —](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) obiekty, które faktycznie są zwracane w `values`.</span><span class="sxs-lookup"><span data-stu-id="1b89c-108">[out] A pointer to the number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objects actually returned in `values`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b89c-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1b89c-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b89c-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1b89c-110">Requirements</span></span>  
 <span data-ttu-id="1b89c-111">**Platformy:** Środowisko wykonawcze systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1b89c-111">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="1b89c-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1b89c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1b89c-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b89c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b89c-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b89c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b89c-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1b89c-115">See also</span></span>

- [<span data-ttu-id="1b89c-116">ICorDebugGuidToTypeEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="1b89c-116">ICorDebugGuidToTypeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)
- [<span data-ttu-id="1b89c-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="1b89c-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
