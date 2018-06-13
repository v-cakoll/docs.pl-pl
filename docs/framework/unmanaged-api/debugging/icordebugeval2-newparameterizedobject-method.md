---
title: ICorDebugEval2::NewParameterizedObject — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedObject
helpviewer_keywords:
- NewParameterizedObject method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObject method [.NET Framework debugging]
ms.assetid: 3d705463-e640-4249-8036-4e8206d03cfe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f20c24984aadd05139d1a427b75bc65438539ff1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412808"
---
# <a name="icordebugeval2newparameterizedobject-method"></a><span data-ttu-id="43d13-102">ICorDebugEval2::NewParameterizedObject — Metoda</span><span class="sxs-lookup"><span data-stu-id="43d13-102">ICorDebugEval2::NewParameterizedObject Method</span></span>
<span data-ttu-id="43d13-103">Tworzy nowy obiekt sparametryzowany typ i wywołuje metodę konstruktora obiektu.</span><span class="sxs-lookup"><span data-stu-id="43d13-103">Instantiates a new parameterized type object and calls the object's constructor method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43d13-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="43d13-104">Syntax</span></span>  
  
```  
HRESULT NewParameterizedObject (  
    [in] ICorDebugFunction     *pConstructor,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="43d13-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="43d13-105">Parameters</span></span>  
 `pConstructor`  
 <span data-ttu-id="43d13-106">[in] Wskaźnik do obiektu ICorDebugFunction, który reprezentuje konstruktora można utworzyć wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="43d13-106">[in] A pointer to an ICorDebugFunction object that represents the constructor of the object to be instantiated.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="43d13-107">[in] Przekazany liczby argumentów typu.</span><span class="sxs-lookup"><span data-stu-id="43d13-107">[in] The number of type arguments passed.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="43d13-108">[in] Tablicy wskaźników, z których każdy wskazuje obiekt ICorDebugType, który reprezentuje typ argumentu dla obiekt, który jest uruchamianiu.</span><span class="sxs-lookup"><span data-stu-id="43d13-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument for the object that is being instantiated.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="43d13-109">[in] Liczba argumentów przekazanych do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="43d13-109">[in] The number of arguments passed to the constructor.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="43d13-110">[in] Tablicy wskaźników, z których każdy wskazuje obiekt ICorDebugValue, który reprezentuje wartość argumentu, który jest przekazywany do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="43d13-110">[in] An array of pointers, each of which points to an ICorDebugValue object that represents an argument value that is passed to the constructor.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="43d13-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="43d13-111">Remarks</span></span>  
 <span data-ttu-id="43d13-112">Konstruktor obiektu może potrwać <xref:System.Type> parametrów.</span><span class="sxs-lookup"><span data-stu-id="43d13-112">The object's constructor may take <xref:System.Type> parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43d13-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="43d13-113">Requirements</span></span>  
 <span data-ttu-id="43d13-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43d13-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43d13-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="43d13-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="43d13-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="43d13-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="43d13-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43d13-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
