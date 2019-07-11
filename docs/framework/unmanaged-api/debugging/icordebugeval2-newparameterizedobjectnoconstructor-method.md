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
ms.openlocfilehash: e4434f5d0eaa45c9cfcbadb20b29564f0643a2dc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754434"
---
# <a name="icordebugeval2newparameterizedobjectnoconstructor-method"></a><span data-ttu-id="405f2-102">ICorDebugEval2::NewParameterizedObjectNoConstructor — Metoda</span><span class="sxs-lookup"><span data-stu-id="405f2-102">ICorDebugEval2::NewParameterizedObjectNoConstructor Method</span></span>
<span data-ttu-id="405f2-103">Tworzy nowy typ sparametryzowany obiekt określonej klasy bez próby wywołania metody konstruktora.</span><span class="sxs-lookup"><span data-stu-id="405f2-103">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="405f2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="405f2-104">Syntax</span></span>  
  
```cpp  
HRESULT NewParameterizedObjectNoConstructor (  
    [in] ICorDebugClass        *pClass,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="405f2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="405f2-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="405f2-106">[in] Wskaźnik do obiektu ICorDebugClass, który reprezentuje klasę obiektu, który ma zostać utworzona.</span><span class="sxs-lookup"><span data-stu-id="405f2-106">[in] A pointer to an ICorDebugClass object that represents the class of the object to be instantiated.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="405f2-107">[in] Przekazany liczby argumentów typu.</span><span class="sxs-lookup"><span data-stu-id="405f2-107">[in] The number of type arguments passed.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="405f2-108">[in] Tablica wskaźników, z których każdy wskazuje na obiekt ICorDebugType, który reprezentuje argument typu obiektu, który zostanie on uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="405f2-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument for the object that is being instantiated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="405f2-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="405f2-109">Remarks</span></span>  
 <span data-ttu-id="405f2-110">`NewParameterizedObjectNoConstructor` Metoda zakończy się niepowodzeniem, jeśli niepoprawną liczbę argumentów typu lub zostaną przekazane nieprawidłowe typy argumentów typu.</span><span class="sxs-lookup"><span data-stu-id="405f2-110">The `NewParameterizedObjectNoConstructor` method will fail if an incorrect number of type arguments or the wrong types of type arguments are passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="405f2-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="405f2-111">Requirements</span></span>  
 <span data-ttu-id="405f2-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="405f2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="405f2-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="405f2-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="405f2-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="405f2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="405f2-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="405f2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
