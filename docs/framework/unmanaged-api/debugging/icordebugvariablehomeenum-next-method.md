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
ms.openlocfilehash: 480317a4ec0515411f1ca8156a5bc4d06aa3f38a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablehomeenumnext-method"></a><span data-ttu-id="bd25e-102">ICorDebugVariableHomeEnum::Next — metoda</span><span class="sxs-lookup"><span data-stu-id="bd25e-102">ICorDebugVariableHomeEnum::Next Method</span></span>
<span data-ttu-id="bd25e-103">Pobiera określoną liczbę [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) wystąpień, które zawierają informacje o zmiennych lokalnych i argumenty w funkcji.</span><span class="sxs-lookup"><span data-stu-id="bd25e-103">Gets the specified number of [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd25e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bd25e-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] ICorDebugVariableHome *homes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bd25e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bd25e-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="bd25e-106">[in] Liczba obiektów, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="bd25e-106">[in] The number of objects to be retrieved.</span></span>  
  
 `homes`  
 <span data-ttu-id="bd25e-107">Tablicy wskaźników, z których każdy wskazuje [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) obiektu, który zawiera informacje o lokalnej zmiennej lub argumentu funkcji.</span><span class="sxs-lookup"><span data-stu-id="bd25e-107">An array of pointers, each of which points to a [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object that provides information about  a local variable or argument of a function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="bd25e-108">[out] Liczba wystąpień zwrócona faktycznie w obiektach.</span><span class="sxs-lookup"><span data-stu-id="bd25e-108">[out] The number of instances actually returned in objects.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bd25e-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bd25e-109">Return Value</span></span>  
 <span data-ttu-id="bd25e-110">Metoda zwraca następujące wartości.</span><span class="sxs-lookup"><span data-stu-id="bd25e-110">The method returns the following values.</span></span>  
  
|<span data-ttu-id="bd25e-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bd25e-111">HRESULT</span></span>|<span data-ttu-id="bd25e-112">Opis</span><span class="sxs-lookup"><span data-stu-id="bd25e-112">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="bd25e-113">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="bd25e-113">The method completed successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="bd25e-114">Rzeczywista liczba wystąpień pobrać, zgodnie z opisem w `pceltFetched`, jest mniejsza niż liczba wystąpień żądanie.</span><span class="sxs-lookup"><span data-stu-id="bd25e-114">The actual number of instances retrieved, as reflected in `pceltFetched`, is less than the number of instances requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd25e-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bd25e-115">Remarks</span></span>  
 <span data-ttu-id="bd25e-116">[ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) metoda pobiera maksymalnie `celt` obiektów, zaczynając od bieżąca pozycja modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="bd25e-116">The [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) method retrieves a maximum of  `celt` objects starting at the current position of the enumerator.</span></span> <span data-ttu-id="bd25e-117">Gdy metoda zwróci wartość, `pceltFetched` zawiera rzeczywistą liczbę obiektów pobrane.</span><span class="sxs-lookup"><span data-stu-id="bd25e-117">When the method returns, `pceltFetched` contains the actual number of objects retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd25e-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bd25e-118">Requirements</span></span>  
 <span data-ttu-id="bd25e-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd25e-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd25e-120">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bd25e-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bd25e-121">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd25e-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd25e-122">**Wersje programu .NET framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd25e-122">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd25e-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bd25e-123">See Also</span></span>  
 [<span data-ttu-id="bd25e-124">Interfejs ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="bd25e-124">ICorDebugVariableHomeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
 [<span data-ttu-id="bd25e-125">Interfejs ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="bd25e-125">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
