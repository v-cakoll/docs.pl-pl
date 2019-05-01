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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8c639204fa207774b0e362f1ba8fe71937494ae2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988997"
---
# <a name="icordebugeval2newparameterizedarray-method"></a><span data-ttu-id="01054-102">ICorDebugEval2::NewParameterizedArray — Metoda</span><span class="sxs-lookup"><span data-stu-id="01054-102">ICorDebugEval2::NewParameterizedArray Method</span></span>
<span data-ttu-id="01054-103">Przydziela nową tablicę typu określonego elementu i wymiary.</span><span class="sxs-lookup"><span data-stu-id="01054-103">Allocates a new array of the specified element type and dimensions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01054-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="01054-104">Syntax</span></span>  
  
```  
HRESULT NewParameterizedArray(  
    [in] ICorDebugType          *pElementType,  
    [in] ULONG32                rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01054-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="01054-105">Parameters</span></span>  
 `pElementType`  
 <span data-ttu-id="01054-106">[in] Wskaźnik do obiektu ICorDebugType, który reprezentuje typ elementu przechowywanego w tablicy.</span><span class="sxs-lookup"><span data-stu-id="01054-106">[in] A pointer to an ICorDebugType object that represents the type of element stored in the array.</span></span>  
  
 `rank`  
 <span data-ttu-id="01054-107">[in] Liczba wymiarów tablicy.</span><span class="sxs-lookup"><span data-stu-id="01054-107">[in] The number of dimensions of the array.</span></span> <span data-ttu-id="01054-108">W programie .NET Framework 2.0 ta wartość musi wynosić 1.</span><span class="sxs-lookup"><span data-stu-id="01054-108">In the .NET Framework version 2.0, this value must be 1.</span></span>  
  
 `dims`  
 <span data-ttu-id="01054-109">[in] Rozmiar w bajtach każdego wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="01054-109">[in] The size, in bytes, of each dimension of the array.</span></span>  
  
 `lowBounds`  
 <span data-ttu-id="01054-110">[in] Opcjonalnie.</span><span class="sxs-lookup"><span data-stu-id="01054-110">[in] Optional.</span></span> <span data-ttu-id="01054-111">Dolna granica każdego wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="01054-111">The lower bound of each dimension of the array.</span></span> <span data-ttu-id="01054-112">Jeśli ta wartość zostanie pominięty, dolną granicę równą zero zakłada, że dla każdego wymiaru.</span><span class="sxs-lookup"><span data-stu-id="01054-112">If this value is omitted, a lower bound of zero is assumed for each dimension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01054-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="01054-113">Remarks</span></span>  
 <span data-ttu-id="01054-114">Elementy tablicy mogą być wystąpień typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="01054-114">The elements of the array may be instances of a generic type.</span></span> <span data-ttu-id="01054-115">Tablica zawsze jest tworzony w domenie aplikacji, w którym wątek jest obecnie uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="01054-115">The array is always created in the application domain in which the thread is currently running.</span></span> <span data-ttu-id="01054-116">W programie .NET Framework 2.0, wartość `rank` musi mieć wartość 1.</span><span class="sxs-lookup"><span data-stu-id="01054-116">In the .NET Framework 2.0, the value of `rank` must be 1.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01054-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="01054-117">Requirements</span></span>  
 <span data-ttu-id="01054-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01054-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01054-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="01054-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="01054-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01054-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01054-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01054-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
