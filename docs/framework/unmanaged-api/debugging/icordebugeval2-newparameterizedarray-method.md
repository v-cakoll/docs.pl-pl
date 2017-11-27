---
title: "ICorDebugEval2::NewParameterizedArray — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval2.NewParameterizedArray
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval2::NewParameterizedArray
helpviewer_keywords:
- ICorDebugEval2::NewParameterizedArray method [.NET Framework debugging]
- NewParameterizedArray method [.NET Framework debugging]
ms.assetid: 45efb8ba-c4de-4109-945f-e734d376b43c
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cf7f8fb0d3418f863f2cd1531dc32b7e64c2b8a5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugeval2newparameterizedarray-method"></a><span data-ttu-id="aae9f-102">ICorDebugEval2::NewParameterizedArray — Metoda</span><span class="sxs-lookup"><span data-stu-id="aae9f-102">ICorDebugEval2::NewParameterizedArray Method</span></span>
<span data-ttu-id="aae9f-103">Przydziela nowej tablicy o typie określonym elemencie i wymiary.</span><span class="sxs-lookup"><span data-stu-id="aae9f-103">Allocates a new array of the specified element type and dimensions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aae9f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="aae9f-104">Syntax</span></span>  
  
```  
HRESULT NewParameterizedArray(  
    [in] ICorDebugType          *pElementType,  
    [in] ULONG32                rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aae9f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aae9f-105">Parameters</span></span>  
 `pElementType`  
 <span data-ttu-id="aae9f-106">[in] Wskaźnik do obiektu ICorDebugType, który reprezentuje typ elementu przechowywane w tablicy.</span><span class="sxs-lookup"><span data-stu-id="aae9f-106">[in] A pointer to an ICorDebugType object that represents the type of element stored in the array.</span></span>  
  
 `rank`  
 <span data-ttu-id="aae9f-107">[in] Liczba wymiarów tablicy.</span><span class="sxs-lookup"><span data-stu-id="aae9f-107">[in] The number of dimensions of the array.</span></span> <span data-ttu-id="aae9f-108">W programie .NET Framework w wersji 2.0 ta wartość musi wynosić 1.</span><span class="sxs-lookup"><span data-stu-id="aae9f-108">In the .NET Framework version 2.0, this value must be 1.</span></span>  
  
 `dims`  
 <span data-ttu-id="aae9f-109">[in] Rozmiar w bajtach każdego wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="aae9f-109">[in] The size, in bytes, of each dimension of the array.</span></span>  
  
 `lowBounds`  
 <span data-ttu-id="aae9f-110">[in] Opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="aae9f-110">[in] Optional.</span></span> <span data-ttu-id="aae9f-111">Dolną granicę każdego wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="aae9f-111">The lower bound of each dimension of the array.</span></span> <span data-ttu-id="aae9f-112">W przypadku pominięcia tej wartości dolna granica zero zakłada, że dla każdego wymiaru.</span><span class="sxs-lookup"><span data-stu-id="aae9f-112">If this value is omitted, a lower bound of zero is assumed for each dimension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aae9f-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aae9f-113">Remarks</span></span>  
 <span data-ttu-id="aae9f-114">Elementy tablicy można instancji typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="aae9f-114">The elements of the array may be instances of a generic type.</span></span> <span data-ttu-id="aae9f-115">Tablicy zawsze jest tworzony w domenie aplikacji, w którym wątek jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="aae9f-115">The array is always created in the application domain in which the thread is currently running.</span></span> <span data-ttu-id="aae9f-116">W .NET Framework 2.0, wartość `rank` musi być równa 1.</span><span class="sxs-lookup"><span data-stu-id="aae9f-116">In the .NET Framework 2.0, the value of `rank` must be 1.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aae9f-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="aae9f-117">Requirements</span></span>  
 <span data-ttu-id="aae9f-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aae9f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aae9f-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aae9f-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aae9f-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aae9f-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aae9f-121">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aae9f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
