---
title: 'ICorDebugVariableHomeEnum:: Next — Metoda'
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
ms.openlocfilehash: 9c2c16789fb61099c9b7c58154810739d225af1f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121920"
---
# <a name="icordebugvariablehomeenumnext-method"></a><span data-ttu-id="93a10-102">ICorDebugVariableHomeEnum:: Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="93a10-102">ICorDebugVariableHomeEnum::Next Method</span></span>
<span data-ttu-id="93a10-103">Pobiera określoną liczbę wystąpień [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) , które zawierają informacje o zmiennych lokalnych i argumentach w funkcji.</span><span class="sxs-lookup"><span data-stu-id="93a10-103">Gets the specified number of [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93a10-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="93a10-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] ICorDebugVariableHome *homes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="93a10-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="93a10-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="93a10-106">podczas Liczba obiektów do pobrania.</span><span class="sxs-lookup"><span data-stu-id="93a10-106">[in] The number of objects to be retrieved.</span></span>  
  
 `homes`  
 <span data-ttu-id="93a10-107">Tablica wskaźników, z których każdy wskazuje obiekt [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) , który zawiera informacje na temat zmiennej lokalnej lub argumentu funkcji.</span><span class="sxs-lookup"><span data-stu-id="93a10-107">An array of pointers, each of which points to a [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object that provides information about  a local variable or argument of a function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="93a10-108">określoną Liczba wystąpień faktycznie zwracanych w obiektach.</span><span class="sxs-lookup"><span data-stu-id="93a10-108">[out] The number of instances actually returned in objects.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="93a10-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="93a10-109">Return Value</span></span>  
 <span data-ttu-id="93a10-110">Metoda zwraca następujące wartości.</span><span class="sxs-lookup"><span data-stu-id="93a10-110">The method returns the following values.</span></span>  
  
|<span data-ttu-id="93a10-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="93a10-111">HRESULT</span></span>|<span data-ttu-id="93a10-112">Opis</span><span class="sxs-lookup"><span data-stu-id="93a10-112">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="93a10-113">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="93a10-113">The method completed successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="93a10-114">Rzeczywista liczba pobranych wystąpień uwzględnionych w `pceltFetched`jest mniejsza niż liczba żądanych wystąpień.</span><span class="sxs-lookup"><span data-stu-id="93a10-114">The actual number of instances retrieved, as reflected in `pceltFetched`, is less than the number of instances requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93a10-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="93a10-115">Remarks</span></span>  
 <span data-ttu-id="93a10-116">Metoda [ICorDebugVariableHomeEnum:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) pobiera maksymalnie `celt` obiektów, rozpoczynając od bieżącego położenia modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="93a10-116">The [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) method retrieves a maximum of  `celt` objects starting at the current position of the enumerator.</span></span> <span data-ttu-id="93a10-117">Gdy metoda zwraca, `pceltFetched` zawiera rzeczywistą liczbę pobranych obiektów.</span><span class="sxs-lookup"><span data-stu-id="93a10-117">When the method returns, `pceltFetched` contains the actual number of objects retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93a10-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="93a10-118">Requirements</span></span>  
 <span data-ttu-id="93a10-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93a10-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93a10-120">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="93a10-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="93a10-121">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="93a10-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93a10-122">**Wersje .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93a10-122">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93a10-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="93a10-123">See also</span></span>

- [<span data-ttu-id="93a10-124">ICorDebugVariableHomeEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="93a10-124">ICorDebugVariableHomeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)
- [<span data-ttu-id="93a10-125">ICorDebugVariableHome, interfejs</span><span class="sxs-lookup"><span data-stu-id="93a10-125">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
