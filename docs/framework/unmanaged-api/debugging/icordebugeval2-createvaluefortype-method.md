---
title: ICorDebugEval2::CreateValueForType — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.CreateValueForType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::CreateValueForType
helpviewer_keywords:
- CreateValueForType method [.NET Framework debugging]
- ICorDebugEval2::CreateValueForType method [.NET Framework debugging]
ms.assetid: ea38ae20-7e0a-427a-be77-d78fae719d82
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ffddb8242b6627239a99bd9223b98762910b831
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753239"
---
# <a name="icordebugeval2createvaluefortype-method"></a><span data-ttu-id="d2cf1-102">ICorDebugEval2::CreateValueForType — Metoda</span><span class="sxs-lookup"><span data-stu-id="d2cf1-102">ICorDebugEval2::CreateValueForType Method</span></span>
<span data-ttu-id="d2cf1-103">Pobiera wskaźnik do nowego ICorDebugValue określonego typu o wartości początkowej zero lub wartość null.</span><span class="sxs-lookup"><span data-stu-id="d2cf1-103">Gets a pointer to a new ICorDebugValue of the specified type, with an initial value of zero or null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2cf1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d2cf1-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateValueForType (  
    [in] ICorDebugType         *pType,  
    [out] ICorDebugValue       **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2cf1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d2cf1-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="d2cf1-106">[in] Wskaźnik do obiektu ICorDebugType, który reprezentuje typ.</span><span class="sxs-lookup"><span data-stu-id="d2cf1-106">[in] Pointer to an ICorDebugType object that represents the type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="d2cf1-107">[out] Wskaźnik na adres `ICorDebugValue` obiekt, który reprezentuje wartość.</span><span class="sxs-lookup"><span data-stu-id="d2cf1-107">[out] Pointer to the address of an `ICorDebugValue` object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2cf1-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d2cf1-108">Remarks</span></span>  
 <span data-ttu-id="d2cf1-109">`CreateValueForType` stanowi uogólnienie [ICorDebugEval::CreateValue](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md) , umożliwiając określenie typu dowolnego obiektu, w tym skonstruowany typy takie jak `List<int>`.</span><span class="sxs-lookup"><span data-stu-id="d2cf1-109">`CreateValueForType` generalizes [ICorDebugEval::CreateValue](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md) by allowing you to specify an arbitrary object type, including constructed types such as `List<int>`.</span></span> <span data-ttu-id="d2cf1-110">Jedynym celem tej metody jest do generowania wartości, które mogą być przekazywane do obliczania funkcji.</span><span class="sxs-lookup"><span data-stu-id="d2cf1-110">The only purpose of this method is to generate a value that can be passed to a function evaluation.</span></span>  
  
 <span data-ttu-id="d2cf1-111">Typ musi być klasą lub typu wartości.</span><span class="sxs-lookup"><span data-stu-id="d2cf1-111">The type must be a class or a value type.</span></span> <span data-ttu-id="d2cf1-112">Ta metoda nie można użyć do utworzenia tablicy wartości lub wartości ciągu.</span><span class="sxs-lookup"><span data-stu-id="d2cf1-112">You cannot use this method to create array values or string values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2cf1-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d2cf1-113">Requirements</span></span>  
 <span data-ttu-id="d2cf1-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2cf1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2cf1-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d2cf1-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d2cf1-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d2cf1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2cf1-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2cf1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
