---
title: "ICorDebugEval2::CreateValueForType — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 18e7eb5fc30c27fd2c4865dc61e2f75dc9e96068
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugeval2createvaluefortype-method"></a><span data-ttu-id="ac5ae-102">ICorDebugEval2::CreateValueForType — Metoda</span><span class="sxs-lookup"><span data-stu-id="ac5ae-102">ICorDebugEval2::CreateValueForType Method</span></span>
<span data-ttu-id="ac5ae-103">Pobiera wskaźnik do nowego ICorDebugValue określonego typu o wartości początkowej zero lub wartość null.</span><span class="sxs-lookup"><span data-stu-id="ac5ae-103">Gets a pointer to a new ICorDebugValue of the specified type, with an initial value of zero or null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac5ae-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ac5ae-104">Syntax</span></span>  
  
```  
HRESULT CreateValueForType (  
    [in] ICorDebugType         *pType,  
    [out] ICorDebugValue       **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ac5ae-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ac5ae-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="ac5ae-106">[in] Wskaźnik do obiektu ICorDebugType, który reprezentuje typ.</span><span class="sxs-lookup"><span data-stu-id="ac5ae-106">[in] Pointer to an ICorDebugType object that represents the type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="ac5ae-107">[out] Wskaźnik do adresu `ICorDebugValue` obiekt, który reprezentuje wartość.</span><span class="sxs-lookup"><span data-stu-id="ac5ae-107">[out] Pointer to the address of an `ICorDebugValue` object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac5ae-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ac5ae-108">Remarks</span></span>  
 <span data-ttu-id="ac5ae-109">`CreateValueForType`stanowi uogólnienie [ICorDebugEval::CreateValue](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md) , umożliwiając określenie typu dowolnego obiektu, w tym konstruować typów takich jak `List<int>`.</span><span class="sxs-lookup"><span data-stu-id="ac5ae-109">`CreateValueForType` generalizes [ICorDebugEval::CreateValue](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md) by allowing you to specify an arbitrary object type, including constructed types such as `List<int>`.</span></span> <span data-ttu-id="ac5ae-110">Jedynym celem tej metody polega na generowaniu wartości, które mogą zostać przekazane do obliczania funkcji.</span><span class="sxs-lookup"><span data-stu-id="ac5ae-110">The only purpose of this method is to generate a value that can be passed to a function evaluation.</span></span>  
  
 <span data-ttu-id="ac5ae-111">Typ musi być klasą lub typem wartości.</span><span class="sxs-lookup"><span data-stu-id="ac5ae-111">The type must be a class or a value type.</span></span> <span data-ttu-id="ac5ae-112">Tej metody nie można użyć do utworzenia tablicy wartości lub wartości ciągu.</span><span class="sxs-lookup"><span data-stu-id="ac5ae-112">You cannot use this method to create array values or string values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac5ae-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ac5ae-113">Requirements</span></span>  
 <span data-ttu-id="ac5ae-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac5ae-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac5ae-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ac5ae-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ac5ae-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac5ae-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac5ae-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac5ae-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
