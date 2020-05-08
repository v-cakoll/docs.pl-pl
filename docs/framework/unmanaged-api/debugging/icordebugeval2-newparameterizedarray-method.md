---
title: ICorDebugEval2::NewParameterizedArray — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedArray
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedArray
helpviewer_keywords:
- ICorDebugEval2::NewParameterizedArray method [.NET Framework debugging]
- NewParameterizedArray method [.NET Framework debugging]
ms.assetid: 45efb8ba-c4de-4109-945f-e734d376b43c
topic_type:
- apiref
ms.openlocfilehash: 9d589bfc3093d03d87acb47ade0fc6c972bcd335
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976112"
---
# <a name="icordebugeval2newparameterizedarray-method"></a><span data-ttu-id="a8a8a-102">ICorDebugEval2::NewParameterizedArray — Metoda</span><span class="sxs-lookup"><span data-stu-id="a8a8a-102">ICorDebugEval2::NewParameterizedArray Method</span></span>
<span data-ttu-id="a8a8a-103">Przypisuje nową tablicę określonego typu elementu i wymiarów.</span><span class="sxs-lookup"><span data-stu-id="a8a8a-103">Allocates a new array of the specified element type and dimensions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8a8a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a8a8a-104">Syntax</span></span>  
  
```cpp  
HRESULT NewParameterizedArray(  
    [in] ICorDebugType          *pElementType,  
    [in] ULONG32                rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8a8a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a8a8a-105">Parameters</span></span>  
 `pElementType`  
 <span data-ttu-id="a8a8a-106">podczas Wskaźnik do obiektu ICorDebugType, który reprezentuje typ elementu przechowywanego w tablicy.</span><span class="sxs-lookup"><span data-stu-id="a8a8a-106">[in] A pointer to an ICorDebugType object that represents the type of element stored in the array.</span></span>  
  
 `rank`  
 <span data-ttu-id="a8a8a-107">podczas Liczba wymiarów tablicy.</span><span class="sxs-lookup"><span data-stu-id="a8a8a-107">[in] The number of dimensions of the array.</span></span> <span data-ttu-id="a8a8a-108">W .NET Framework w wersji 2,0 ta wartość musi być równa 1.</span><span class="sxs-lookup"><span data-stu-id="a8a8a-108">In the .NET Framework version 2.0, this value must be 1.</span></span>  
  
 `dims`  
 <span data-ttu-id="a8a8a-109">podczas Rozmiar, w bajtach, każdego wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="a8a8a-109">[in] The size, in bytes, of each dimension of the array.</span></span>  
  
 `lowBounds`  
 <span data-ttu-id="a8a8a-110">podczas Obowiązkowe.</span><span class="sxs-lookup"><span data-stu-id="a8a8a-110">[in] Optional.</span></span> <span data-ttu-id="a8a8a-111">Dolna granica każdego wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="a8a8a-111">The lower bound of each dimension of the array.</span></span> <span data-ttu-id="a8a8a-112">W przypadku pominięcia tej wartości dla każdego wymiaru zostanie przyjęta Dolna granica zero.</span><span class="sxs-lookup"><span data-stu-id="a8a8a-112">If this value is omitted, a lower bound of zero is assumed for each dimension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8a8a-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a8a8a-113">Remarks</span></span>  
 <span data-ttu-id="a8a8a-114">Elementy tablicy mogą być wystąpieniami typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="a8a8a-114">The elements of the array may be instances of a generic type.</span></span> <span data-ttu-id="a8a8a-115">Tablica jest zawsze tworzona w domenie aplikacji, w której jest aktualnie uruchomiony wątek.</span><span class="sxs-lookup"><span data-stu-id="a8a8a-115">The array is always created in the application domain in which the thread is currently running.</span></span> <span data-ttu-id="a8a8a-116">W .NET Framework 2,0 wartość `rank` musi być równa 1.</span><span class="sxs-lookup"><span data-stu-id="a8a8a-116">In the .NET Framework 2.0, the value of `rank` must be 1.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8a8a-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a8a8a-117">Requirements</span></span>  
 <span data-ttu-id="a8a8a-118">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8a8a-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8a8a-119">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a8a8a-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a8a8a-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a8a8a-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8a8a-121">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8a8a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
