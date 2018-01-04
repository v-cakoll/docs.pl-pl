---
title: "ICorDebugVariableHomeEnum::Next — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHomeEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHomeEnum::Next
helpviewer_keywords:
- ICorDebugVariableHomeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: eb9ea96c-5b58-4655-8104-094fc8b393b8
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3bab158cbbe2eaf6e52ae0df6a0eed86d3d0b8ce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvariablehomeenumnext-method"></a><span data-ttu-id="e20f6-102">ICorDebugVariableHomeEnum::Next — metoda</span><span class="sxs-lookup"><span data-stu-id="e20f6-102">ICorDebugVariableHomeEnum::Next Method</span></span>
<span data-ttu-id="e20f6-103">Pobiera określoną liczbę [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) wystąpień, które zawierają informacje o zmiennych lokalnych i argumenty w funkcji.</span><span class="sxs-lookup"><span data-stu-id="e20f6-103">Gets the specified number of [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e20f6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e20f6-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] ICorDebugVariableHome *homes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e20f6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e20f6-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="e20f6-106">[in] Liczba obiektów, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="e20f6-106">[in] The number of objects to be retrieved.</span></span>  
  
 `homes`  
 <span data-ttu-id="e20f6-107">Tablicy wskaźników, z których każdy wskazuje [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) obiektu, który zawiera informacje o lokalnej zmiennej lub argumentu funkcji.</span><span class="sxs-lookup"><span data-stu-id="e20f6-107">An array of pointers, each of which points to a [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object that provides information about  a local variable or argument of a function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="e20f6-108">[out] Liczba wystąpień zwrócona faktycznie w obiektach.</span><span class="sxs-lookup"><span data-stu-id="e20f6-108">[out] The number of instances actually returned in objects.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e20f6-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e20f6-109">Return Value</span></span>  
 <span data-ttu-id="e20f6-110">Metoda zwraca następujące wartości.</span><span class="sxs-lookup"><span data-stu-id="e20f6-110">The method returns the following values.</span></span>  
  
|<span data-ttu-id="e20f6-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e20f6-111">HRESULT</span></span>|<span data-ttu-id="e20f6-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e20f6-112">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="e20f6-113">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e20f6-113">The method completed successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="e20f6-114">Rzeczywista liczba wystąpień pobrać, zgodnie z opisem w `pceltFetched`, jest mniejsza niż liczba wystąpień żądanie.</span><span class="sxs-lookup"><span data-stu-id="e20f6-114">The actual number of instances retrieved, as reflected in `pceltFetched`, is less than the number of instances requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e20f6-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e20f6-115">Remarks</span></span>  
 <span data-ttu-id="e20f6-116">[ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) metoda pobiera maksymalnie `celt` obiektów, zaczynając od bieżąca pozycja modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="e20f6-116">The [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) method retrieves a maximum of  `celt` objects starting at the current position of the enumerator.</span></span> <span data-ttu-id="e20f6-117">Gdy metoda zwróci wartość, `pceltFetched` zawiera rzeczywistą liczbę obiektów pobrane.</span><span class="sxs-lookup"><span data-stu-id="e20f6-117">When the method returns, `pceltFetched` contains the actual number of objects retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e20f6-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e20f6-118">Requirements</span></span>  
 <span data-ttu-id="e20f6-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e20f6-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e20f6-120">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e20f6-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e20f6-121">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e20f6-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e20f6-122">**Wersje programu .NET framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e20f6-122">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e20f6-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e20f6-123">See Also</span></span>  
 [<span data-ttu-id="e20f6-124">ICorDebugVariableHomeEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="e20f6-124">ICorDebugVariableHomeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
 [<span data-ttu-id="e20f6-125">ICorDebugVariableHome, interfejs</span><span class="sxs-lookup"><span data-stu-id="e20f6-125">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
