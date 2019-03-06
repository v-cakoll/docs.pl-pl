---
title: Metoda ICorDebugVariableHome::GetArgumentIndex
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2457dff3063e47f1fb9d040caac1bc08441e1739
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57366832"
---
# <a name="icordebugvariablehomegetargumentindex-method"></a><span data-ttu-id="9f431-102">Metoda ICorDebugVariableHome::GetArgumentIndex</span><span class="sxs-lookup"><span data-stu-id="9f431-102">ICorDebugVariableHome::GetArgumentIndex Method</span></span>

<span data-ttu-id="9f431-103">Pobiera indeks argumentu funkcji.</span><span class="sxs-lookup"><span data-stu-id="9f431-103">Gets the index of a function argument.</span></span>

## <a name="syntax"></a><span data-ttu-id="9f431-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9f431-104">Syntax</span></span>

```cpp
HRESULT GetArgumentIndex(
    [out] ULONG32* pArgumentIndex
);
```

## <a name="parameters"></a><span data-ttu-id="9f431-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9f431-105">Parameters</span></span>

`pArgumentIndex`\
<span data-ttu-id="9f431-106">[out] Wskaźnik do indeksu argumentu.</span><span class="sxs-lookup"><span data-stu-id="9f431-106">[out] A pointer to the argument index.</span></span>

## <a name="return-value"></a><span data-ttu-id="9f431-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9f431-107">Return Value</span></span>

<span data-ttu-id="9f431-108">Metoda zwraca następujące wartości.</span><span class="sxs-lookup"><span data-stu-id="9f431-108">The method returns the following values.</span></span>

|<span data-ttu-id="9f431-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="9f431-109">Value</span></span>|<span data-ttu-id="9f431-110">Opis</span><span class="sxs-lookup"><span data-stu-id="9f431-110">Description</span></span>|
|-----------|-----------------|
|`S_OK`|<span data-ttu-id="9f431-111">Wywołanie metody zwracane indeksu nieprawidłowy argument.</span><span class="sxs-lookup"><span data-stu-id="9f431-111">The method call returned a valid argument index.</span></span>|
|`E_FAIL`|<span data-ttu-id="9f431-112">Bieżący [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) wystąpienie reprezentuje zmienną lokalną.</span><span class="sxs-lookup"><span data-stu-id="9f431-112">The current [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance represents a local variable.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9f431-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9f431-113">Remarks</span></span>

<span data-ttu-id="9f431-114">Indeks argument może służyć do pobierania metadanych dla tego argumentu.</span><span class="sxs-lookup"><span data-stu-id="9f431-114">The argument index can be used to retrieve metadata for this argument.</span></span>

## <a name="requirements"></a><span data-ttu-id="9f431-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9f431-115">Requirements</span></span>

<span data-ttu-id="9f431-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f431-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="9f431-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9f431-117">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="9f431-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9f431-118">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="9f431-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f431-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="9f431-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9f431-120">See also</span></span>

- [<span data-ttu-id="9f431-121">ICorDebugVariableHome, interfejs</span><span class="sxs-lookup"><span data-stu-id="9f431-121">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
