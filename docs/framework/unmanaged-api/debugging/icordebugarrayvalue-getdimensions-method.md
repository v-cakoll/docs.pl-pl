---
title: ICorDebugArrayValue::GetDimensions — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetDimensions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetDimensions
helpviewer_keywords:
- ICorDebugArrayValue::GetDimensions method [.NET Framework debugging]
- GetDimensions method [.NET Framework debugging]
ms.assetid: 6c116592-134b-4ef2-a319-680e92d013aa
topic_type:
- apiref
ms.openlocfilehash: fa2be894af6e44d09c25a736f45acba56052f9fa
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895037"
---
# <a name="icordebugarrayvaluegetdimensions-method"></a><span data-ttu-id="c1035-102">ICorDebugArrayValue::GetDimensions — Metoda</span><span class="sxs-lookup"><span data-stu-id="c1035-102">ICorDebugArrayValue::GetDimensions Method</span></span>
<span data-ttu-id="c1035-103">Pobiera liczbę elementów w każdym wymiarze tej tablicy.</span><span class="sxs-lookup"><span data-stu-id="c1035-103">Gets the number of elements in each dimension of this array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1035-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c1035-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDimensions (  
    [in] ULONG32         cdim,  
    [out, size_is(cdim), length_is(cdim)]
        ULONG32          dims[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1035-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c1035-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="c1035-106">podczas Liczba wymiarów tego obiektu ICorDebugArrayValue.</span><span class="sxs-lookup"><span data-stu-id="c1035-106">[in] The number of dimensions of this ICorDebugArrayValue object.</span></span>  
  
 <span data-ttu-id="c1035-107">Ta wartość jest również rozmiarem `dims` tablicy, ponieważ jej rozmiar jest równy liczbie wymiarów `ICorDebugArrayValue` obiektu.</span><span class="sxs-lookup"><span data-stu-id="c1035-107">This value is also the size of the `dims` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `dims`  
 <span data-ttu-id="c1035-108">określoną Tablica liczb całkowitych, z których każdy określa liczbę elementów w wymiarze w tym `ICorDebugArrayValue` obiekcie.</span><span class="sxs-lookup"><span data-stu-id="c1035-108">[out] An array of integers, each of which specifies the number of elements in a dimension in this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1035-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c1035-109">Requirements</span></span>  
 <span data-ttu-id="c1035-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1035-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1035-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c1035-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c1035-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c1035-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c1035-113">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1035-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
