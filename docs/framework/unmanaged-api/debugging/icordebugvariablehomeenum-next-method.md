---
title: Metoda ICorDebugVariableHomeEnum::Next
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
ms.openlocfilehash: be1ba87ae979911dd21647569725eafa2c80ffa6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59080731"
---
# <a name="icordebugvariablehomeenumnext-method"></a><span data-ttu-id="f33e7-102">Metoda ICorDebugVariableHomeEnum::Next</span><span class="sxs-lookup"><span data-stu-id="f33e7-102">ICorDebugVariableHomeEnum::Next Method</span></span>
<span data-ttu-id="f33e7-103">Pobiera określoną liczbę [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) wystąpień, które zawierają informacje dotyczące zmiennych lokalnych i argumenty w funkcji.</span><span class="sxs-lookup"><span data-stu-id="f33e7-103">Gets the specified number of [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f33e7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f33e7-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] ICorDebugVariableHome *homes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f33e7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f33e7-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="f33e7-106">[in] Liczba obiektów, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="f33e7-106">[in] The number of objects to be retrieved.</span></span>  
  
 `homes`  
 <span data-ttu-id="f33e7-107">Tablica wskaźników, z których każdy wskazuje [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) obiekt, który zawiera informacje dotyczące lokalnej zmiennej lub argumentu funkcji.</span><span class="sxs-lookup"><span data-stu-id="f33e7-107">An array of pointers, each of which points to a [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object that provides information about  a local variable or argument of a function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="f33e7-108">[out] Liczba wystąpień zwrócona w rzeczywistości w obiektach.</span><span class="sxs-lookup"><span data-stu-id="f33e7-108">[out] The number of instances actually returned in objects.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f33e7-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f33e7-109">Return Value</span></span>  
 <span data-ttu-id="f33e7-110">Metoda zwraca następujące wartości.</span><span class="sxs-lookup"><span data-stu-id="f33e7-110">The method returns the following values.</span></span>  
  
|<span data-ttu-id="f33e7-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f33e7-111">HRESULT</span></span>|<span data-ttu-id="f33e7-112">Opis</span><span class="sxs-lookup"><span data-stu-id="f33e7-112">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="f33e7-113">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f33e7-113">The method completed successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="f33e7-114">Rzeczywista liczba wystąpień pobierane, zgodnie z opisem w `pceltFetched`, jest mniejsza od liczby wystąpień na żądanie.</span><span class="sxs-lookup"><span data-stu-id="f33e7-114">The actual number of instances retrieved, as reflected in `pceltFetched`, is less than the number of instances requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f33e7-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f33e7-115">Remarks</span></span>  
 <span data-ttu-id="f33e7-116">[ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) metoda pobiera maksymalnie `celt` obiektów, począwszy od bieżącego położenia obiektu modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="f33e7-116">The [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) method retrieves a maximum of  `celt` objects starting at the current position of the enumerator.</span></span> <span data-ttu-id="f33e7-117">Po powrocie z metody `pceltFetched` zawiera rzeczywista liczba pobrane obiekty.</span><span class="sxs-lookup"><span data-stu-id="f33e7-117">When the method returns, `pceltFetched` contains the actual number of objects retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f33e7-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f33e7-118">Requirements</span></span>  
 <span data-ttu-id="f33e7-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f33e7-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f33e7-120">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f33e7-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f33e7-121">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f33e7-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f33e7-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f33e7-122">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f33e7-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f33e7-123">See also</span></span>

- [<span data-ttu-id="f33e7-124">ICorDebugVariableHomeEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="f33e7-124">ICorDebugVariableHomeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)
- [<span data-ttu-id="f33e7-125">ICorDebugVariableHome, interfejs</span><span class="sxs-lookup"><span data-stu-id="f33e7-125">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
