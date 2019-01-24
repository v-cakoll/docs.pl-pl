---
title: ICorDebugBlockingObjectEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugBlockingObjectEnum.Next Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBlockingObjectEnum::Next
helpviewer_keywords:
- Next method, ICorDebugBlockingObjectEnum interface [.NET Framework debugging]
- ICorDebugBlockingObjectEnum::Next method [.NET Framework debugging]
ms.assetid: 0121753f-ebea-48d0-aeb2-ed7fda76dc60
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: def9d810917495165c7deda9e3dff158582a0e61
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566258"
---
# <a name="icordebugblockingobjectenumnext-method"></a><span data-ttu-id="ca399-102">ICorDebugBlockingObjectEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="ca399-102">ICorDebugBlockingObjectEnum::Next Method</span></span>
<span data-ttu-id="ca399-103">Pobiera określoną liczbę [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) obiektów z wyliczenia, zaczynając od bieżącej pozycji.</span><span class="sxs-lookup"><span data-stu-id="ca399-103">Gets the specified number of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca399-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ca399-104">Syntax</span></span>  
  
```  
HRESULT Next([in] ULONG  celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                           CorDebugBlockingObject values[],  
             [out] ULONG *pceltFetched;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ca399-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ca399-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="ca399-106">[in] Liczba obiektów do pobrania.</span><span class="sxs-lookup"><span data-stu-id="ca399-106">[in] The number of objects to retrieve.</span></span>  
  
 `values`  
 <span data-ttu-id="ca399-107">[out] Tablica wskaźników do [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) obiektów.</span><span class="sxs-lookup"><span data-stu-id="ca399-107">[out] An array of pointers to [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) objects.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="ca399-108">[out] Wskaźnik do liczby obiektów, które zostały pobrane.</span><span class="sxs-lookup"><span data-stu-id="ca399-108">[out] A pointer to the number of objects that were retrieved.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ca399-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ca399-109">Return Value</span></span>  
 <span data-ttu-id="ca399-110">Ta metoda zwraca następujące specyficzne wyniki HRESULT.</span><span class="sxs-lookup"><span data-stu-id="ca399-110">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="ca399-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ca399-111">HRESULT</span></span>|<span data-ttu-id="ca399-112">Opis</span><span class="sxs-lookup"><span data-stu-id="ca399-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ca399-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="ca399-113">S_OK</span></span>|<span data-ttu-id="ca399-114">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="ca399-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="ca399-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="ca399-115">S_FALSE</span></span>|<span data-ttu-id="ca399-116">`pceltFetched` nie równa się `celt`.</span><span class="sxs-lookup"><span data-stu-id="ca399-116">`pceltFetched` does not equal `celt`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca399-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ca399-117">Remarks</span></span>  
 <span data-ttu-id="ca399-118">Ta metoda funkcje, takie jak typowe wyliczający COM.</span><span class="sxs-lookup"><span data-stu-id="ca399-118">This method functions like a typical COM enumerator.</span></span>  
  
 <span data-ttu-id="ca399-119">Wartości tablicy wejściowej musi wynosić co najmniej o rozmiarze `celt`.</span><span class="sxs-lookup"><span data-stu-id="ca399-119">The input array values must be at least of size `celt`.</span></span> <span data-ttu-id="ca399-120">Tablica będzie wypełniona albo następnym `celt` wartości w wyliczeniu lub wszystkie pozostałe wartości w przypadku mniej niż `celt` pozostają.</span><span class="sxs-lookup"><span data-stu-id="ca399-120">The array will be filled with either the next `celt` values in the enumeration or with all remaining values if fewer than `celt` remain.</span></span> <span data-ttu-id="ca399-121">Po powrocie z tej metody `pceltFetched` zostaną wypełnione przy użyciu wartości, które zostały pobrane.</span><span class="sxs-lookup"><span data-stu-id="ca399-121">When this method returns, `pceltFetched` will be filled with the number of values that were retrieved.</span></span> <span data-ttu-id="ca399-122">Jeśli `values` zawiera nieprawidłowe wskaźniki lub punkty do buforu, który jest mniejszy niż `celt`, lub jeśli `pceltFetched` jest nieprawidłowego wskaźnika, wynik jest niezdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="ca399-122">If `values` contains invalid pointers or points to a buffer that is smaller than `celt`, or if `pceltFetched` is an invalid pointer, the result is undefined.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ca399-123">Mimo że [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury nie muszą zostać zwolnione, interfejs "ICorDebugValue" wewnątrz niej muszą zostać zwolnione.</span><span class="sxs-lookup"><span data-stu-id="ca399-123">Although the [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structure does not need to be released, the "ICorDebugValue" interface inside of it does need to be released.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca399-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ca399-124">Requirements</span></span>  
 <span data-ttu-id="ca399-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca399-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca399-126">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ca399-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ca399-127">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca399-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca399-128">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca399-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca399-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ca399-129">See also</span></span>
- [<span data-ttu-id="ca399-130">ICorDebugDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="ca399-130">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [<span data-ttu-id="ca399-131">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="ca399-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="ca399-132">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="ca399-132">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
