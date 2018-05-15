---
title: ICorDebugEval2::NewParameterizedObjectNoConstructor — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedObjectNoConstructor
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedObjectNoConstructor
helpviewer_keywords:
- NewParameterizedObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObjectNoConstructor method [.NET Framework debugging]
ms.assetid: f15b5b78-94f4-4eb9-b3b3-a621272f357c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aad5a285fc2280dc062b0f4cbb69977a7e605e9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugeval2newparameterizedobjectnoconstructor-method"></a><span data-ttu-id="343c9-102">ICorDebugEval2::NewParameterizedObjectNoConstructor — Metoda</span><span class="sxs-lookup"><span data-stu-id="343c9-102">ICorDebugEval2::NewParameterizedObjectNoConstructor Method</span></span>
<span data-ttu-id="343c9-103">Tworzy nowy obiekt sparametryzowany typ określonej klasy bez próba wywołania metody konstruktora.</span><span class="sxs-lookup"><span data-stu-id="343c9-103">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="343c9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="343c9-104">Syntax</span></span>  
  
```  
HRESULT NewParameterizedObjectNoConstructor (  
    [in] ICorDebugClass        *pClass,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="343c9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="343c9-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="343c9-106">[in] Wskaźnik do obiektu ICorDebugClass, który reprezentuje klasę, można utworzyć wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="343c9-106">[in] A pointer to an ICorDebugClass object that represents the class of the object to be instantiated.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="343c9-107">[in] Przekazany liczby argumentów typu.</span><span class="sxs-lookup"><span data-stu-id="343c9-107">[in] The number of type arguments passed.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="343c9-108">[in] Tablicy wskaźników, z których każdy wskazuje obiekt ICorDebugType, który reprezentuje typ argumentu dla obiekt, który jest uruchamianiu.</span><span class="sxs-lookup"><span data-stu-id="343c9-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument for the object that is being instantiated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="343c9-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="343c9-109">Remarks</span></span>  
 <span data-ttu-id="343c9-110">`NewParameterizedObjectNoConstructor` Metoda zakończy się niepowodzeniem, jeśli niepoprawną liczbę argumentów typu lub są przekazano nieprawidłowe typy argumentów typu.</span><span class="sxs-lookup"><span data-stu-id="343c9-110">The `NewParameterizedObjectNoConstructor` method will fail if an incorrect number of type arguments or the wrong types of type arguments are passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="343c9-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="343c9-111">Requirements</span></span>  
 <span data-ttu-id="343c9-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="343c9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="343c9-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="343c9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="343c9-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="343c9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="343c9-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="343c9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
