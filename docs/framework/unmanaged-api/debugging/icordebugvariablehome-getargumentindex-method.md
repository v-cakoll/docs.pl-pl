---
title: 'ICorDebugVariableHome:: GetArgumentIndex, Metoda'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetArgumentIndex
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetArgumentIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetArgumentIndex method [.NET Framework debugging]
- GetArgumentIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: e86fcc72-388d-4009-ab21-8f9c3323e9a3
topic_type:
- apiref
ms.openlocfilehash: 86b2815c6f95c674c49bba7455e8497192bd8bac
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125152"
---
# <a name="icordebugvariablehomegetargumentindex-method"></a><span data-ttu-id="d0aea-102">ICorDebugVariableHome:: GetArgumentIndex, Metoda</span><span class="sxs-lookup"><span data-stu-id="d0aea-102">ICorDebugVariableHome::GetArgumentIndex Method</span></span>

<span data-ttu-id="d0aea-103">Pobiera indeks argumentu funkcji.</span><span class="sxs-lookup"><span data-stu-id="d0aea-103">Gets the index of a function argument.</span></span>

## <a name="syntax"></a><span data-ttu-id="d0aea-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d0aea-104">Syntax</span></span>

```cpp
HRESULT GetArgumentIndex(
    [out] ULONG32* pArgumentIndex
);
```

## <a name="parameters"></a><span data-ttu-id="d0aea-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d0aea-105">Parameters</span></span>

`pArgumentIndex`\
<span data-ttu-id="d0aea-106">określoną Wskaźnik do indeksu argumentów.</span><span class="sxs-lookup"><span data-stu-id="d0aea-106">[out] A pointer to the argument index.</span></span>

## <a name="return-value"></a><span data-ttu-id="d0aea-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d0aea-107">Return Value</span></span>

<span data-ttu-id="d0aea-108">Metoda zwraca następujące wartości.</span><span class="sxs-lookup"><span data-stu-id="d0aea-108">The method returns the following values.</span></span>

|<span data-ttu-id="d0aea-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="d0aea-109">Value</span></span>|<span data-ttu-id="d0aea-110">Opis</span><span class="sxs-lookup"><span data-stu-id="d0aea-110">Description</span></span>|
|-----------|-----------------|
|`S_OK`|<span data-ttu-id="d0aea-111">Wywołanie metody zwróciło prawidłowy indeks argumentu.</span><span class="sxs-lookup"><span data-stu-id="d0aea-111">The method call returned a valid argument index.</span></span>|
|`E_FAIL`|<span data-ttu-id="d0aea-112">Bieżące wystąpienie [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) reprezentuje zmienną lokalną.</span><span class="sxs-lookup"><span data-stu-id="d0aea-112">The current [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance represents a local variable.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d0aea-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d0aea-113">Remarks</span></span>

<span data-ttu-id="d0aea-114">Indeks argumentu może służyć do pobierania metadanych dla tego argumentu.</span><span class="sxs-lookup"><span data-stu-id="d0aea-114">The argument index can be used to retrieve metadata for this argument.</span></span>

## <a name="requirements"></a><span data-ttu-id="d0aea-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d0aea-115">Requirements</span></span>

<span data-ttu-id="d0aea-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0aea-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="d0aea-117">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d0aea-117">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="d0aea-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d0aea-118">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="d0aea-119">**Wersje .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0aea-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="d0aea-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d0aea-120">See also</span></span>

- [<span data-ttu-id="d0aea-121">ICorDebugVariableHome, interfejs</span><span class="sxs-lookup"><span data-stu-id="d0aea-121">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
