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
ms.openlocfilehash: 8632799b68ae8f92835d1774472bc1432d886f3b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793481"
---
# <a name="icordebugeval2createvaluefortype-method"></a><span data-ttu-id="a3c8f-102">ICorDebugEval2::CreateValueForType — Metoda</span><span class="sxs-lookup"><span data-stu-id="a3c8f-102">ICorDebugEval2::CreateValueForType Method</span></span>
<span data-ttu-id="a3c8f-103">Pobiera wskaźnik do nowego ICorDebugValue określonego typu z początkową wartością zero lub null.</span><span class="sxs-lookup"><span data-stu-id="a3c8f-103">Gets a pointer to a new ICorDebugValue of the specified type, with an initial value of zero or null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3c8f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a3c8f-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateValueForType (  
    [in] ICorDebugType         *pType,  
    [out] ICorDebugValue       **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3c8f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a3c8f-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="a3c8f-106">podczas Wskaźnik do obiektu ICorDebugType, który reprezentuje typ.</span><span class="sxs-lookup"><span data-stu-id="a3c8f-106">[in] Pointer to an ICorDebugType object that represents the type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="a3c8f-107">określoną Wskaźnik na adres `ICorDebugValue` obiektu, który reprezentuje wartość.</span><span class="sxs-lookup"><span data-stu-id="a3c8f-107">[out] Pointer to the address of an `ICorDebugValue` object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3c8f-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a3c8f-108">Remarks</span></span>  
 <span data-ttu-id="a3c8f-109">`CreateValueForType` generalizes [:: SetValue](icordebugeval-createvalue-method.md) , umożliwiając określenie dowolnego typu obiektu, w tym typów skonstruowanych, takich jak `List<int>`.</span><span class="sxs-lookup"><span data-stu-id="a3c8f-109">`CreateValueForType` generalizes [ICorDebugEval::CreateValue](icordebugeval-createvalue-method.md) by allowing you to specify an arbitrary object type, including constructed types such as `List<int>`.</span></span> <span data-ttu-id="a3c8f-110">Jedynym celem tej metody jest wygenerowanie wartości, która może zostać przeniesiona do oceny funkcji.</span><span class="sxs-lookup"><span data-stu-id="a3c8f-110">The only purpose of this method is to generate a value that can be passed to a function evaluation.</span></span>  
  
 <span data-ttu-id="a3c8f-111">Typ musi być klasą lub typem wartości.</span><span class="sxs-lookup"><span data-stu-id="a3c8f-111">The type must be a class or a value type.</span></span> <span data-ttu-id="a3c8f-112">Nie można użyć tej metody do tworzenia wartości tablicy lub wartości ciągu.</span><span class="sxs-lookup"><span data-stu-id="a3c8f-112">You cannot use this method to create array values or string values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3c8f-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a3c8f-113">Requirements</span></span>  
 <span data-ttu-id="a3c8f-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3c8f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3c8f-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a3c8f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a3c8f-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a3c8f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3c8f-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3c8f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
