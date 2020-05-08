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
ms.openlocfilehash: 90fce1710f97341fb49be1d07f7af2edf8cb848c
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976086"
---
# <a name="icordebugeval2newparameterizedobjectnoconstructor-method"></a><span data-ttu-id="b7d4b-102">ICorDebugEval2::NewParameterizedObjectNoConstructor — Metoda</span><span class="sxs-lookup"><span data-stu-id="b7d4b-102">ICorDebugEval2::NewParameterizedObjectNoConstructor Method</span></span>
<span data-ttu-id="b7d4b-103">Tworzy wystąpienie nowego obiektu typu sparametryzowanego określonej klasy bez próby wywołania metody konstruktora.</span><span class="sxs-lookup"><span data-stu-id="b7d4b-103">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7d4b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b7d4b-104">Syntax</span></span>  
  
```cpp  
HRESULT NewParameterizedObjectNoConstructor (  
    [in] ICorDebugClass        *pClass,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7d4b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b7d4b-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="b7d4b-106">podczas Wskaźnik do obiektu ICorDebugClass, który reprezentuje klasę obiektu do wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="b7d4b-106">[in] A pointer to an ICorDebugClass object that represents the class of the object to be instantiated.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="b7d4b-107">podczas Liczba przezakończonych argumentów typu.</span><span class="sxs-lookup"><span data-stu-id="b7d4b-107">[in] The number of type arguments passed.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="b7d4b-108">podczas Tablica wskaźników, z których każdy wskazuje obiekt ICorDebugType, który reprezentuje argument typu dla obiektu, który jest tworzony.</span><span class="sxs-lookup"><span data-stu-id="b7d4b-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument for the object that is being instantiated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7d4b-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b7d4b-109">Remarks</span></span>  
 <span data-ttu-id="b7d4b-110">Metoda `NewParameterizedObjectNoConstructor` zakończy się niepowodzeniem, jeśli zostanie przeniesiona niepoprawna liczba argumentów typu lub nieprawidłowe typy argumentów typu.</span><span class="sxs-lookup"><span data-stu-id="b7d4b-110">The `NewParameterizedObjectNoConstructor` method will fail if an incorrect number of type arguments or the wrong types of type arguments are passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7d4b-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b7d4b-111">Requirements</span></span>  
 <span data-ttu-id="b7d4b-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7d4b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7d4b-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b7d4b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7d4b-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b7d4b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7d4b-115">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7d4b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
