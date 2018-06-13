---
title: ICorDebugVariableHomeEnum::Next — metoda
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHomeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHomeEnum::Next
helpviewer_keywords:
- ICorDebugVariableHomeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: eb9ea96c-5b58-4655-8104-094fc8b393b8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d5ab18d6c2ae8bbf47a3bcd7cb892530be4f8f4e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421587"
---
# <a name="icordebugvariablehomeenumnext-method"></a><span data-ttu-id="990d5-102">ICorDebugVariableHomeEnum::Next — metoda</span><span class="sxs-lookup"><span data-stu-id="990d5-102">ICorDebugVariableHomeEnum::Next Method</span></span>
<span data-ttu-id="990d5-103">Pobiera określoną liczbę [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) wystąpień, które zawierają informacje o zmiennych lokalnych i argumenty w funkcji.</span><span class="sxs-lookup"><span data-stu-id="990d5-103">Gets the specified number of [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="990d5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="990d5-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] ICorDebugVariableHome *homes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="990d5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="990d5-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="990d5-106">[in] Liczba obiektów, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="990d5-106">[in] The number of objects to be retrieved.</span></span>  
  
 `homes`  
 <span data-ttu-id="990d5-107">Tablicy wskaźników, z których każdy wskazuje [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) obiektu, który zawiera informacje o lokalnej zmiennej lub argumentu funkcji.</span><span class="sxs-lookup"><span data-stu-id="990d5-107">An array of pointers, each of which points to a [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object that provides information about  a local variable or argument of a function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="990d5-108">[out] Liczba wystąpień zwrócona faktycznie w obiektach.</span><span class="sxs-lookup"><span data-stu-id="990d5-108">[out] The number of instances actually returned in objects.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="990d5-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="990d5-109">Return Value</span></span>  
 <span data-ttu-id="990d5-110">Metoda zwraca następujące wartości.</span><span class="sxs-lookup"><span data-stu-id="990d5-110">The method returns the following values.</span></span>  
  
|<span data-ttu-id="990d5-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="990d5-111">HRESULT</span></span>|<span data-ttu-id="990d5-112">Opis</span><span class="sxs-lookup"><span data-stu-id="990d5-112">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="990d5-113">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="990d5-113">The method completed successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="990d5-114">Rzeczywista liczba wystąpień pobrać, zgodnie z opisem w `pceltFetched`, jest mniejsza niż liczba wystąpień żądanie.</span><span class="sxs-lookup"><span data-stu-id="990d5-114">The actual number of instances retrieved, as reflected in `pceltFetched`, is less than the number of instances requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="990d5-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="990d5-115">Remarks</span></span>  
 <span data-ttu-id="990d5-116">[ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) metoda pobiera maksymalnie `celt` obiektów, zaczynając od bieżąca pozycja modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="990d5-116">The [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) method retrieves a maximum of  `celt` objects starting at the current position of the enumerator.</span></span> <span data-ttu-id="990d5-117">Gdy metoda zwróci wartość, `pceltFetched` zawiera rzeczywistą liczbę obiektów pobrane.</span><span class="sxs-lookup"><span data-stu-id="990d5-117">When the method returns, `pceltFetched` contains the actual number of objects retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="990d5-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="990d5-118">Requirements</span></span>  
 <span data-ttu-id="990d5-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="990d5-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="990d5-120">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="990d5-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="990d5-121">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="990d5-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="990d5-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="990d5-122">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="990d5-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="990d5-123">See Also</span></span>  
 [<span data-ttu-id="990d5-124">ICorDebugVariableHomeEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="990d5-124">ICorDebugVariableHomeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
 [<span data-ttu-id="990d5-125">ICorDebugVariableHome, interfejs</span><span class="sxs-lookup"><span data-stu-id="990d5-125">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
