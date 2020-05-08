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
ms.openlocfilehash: fd7acaa8bcb4d53893855bcd25ff68cf26e30354
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976164"
---
# <a name="icordebugeval2createvaluefortype-method"></a><span data-ttu-id="532ea-102">ICorDebugEval2::CreateValueForType — Metoda</span><span class="sxs-lookup"><span data-stu-id="532ea-102">ICorDebugEval2::CreateValueForType Method</span></span>
<span data-ttu-id="532ea-103">Pobiera wskaźnik do nowego ICorDebugValue określonego typu z początkową wartością zero lub null.</span><span class="sxs-lookup"><span data-stu-id="532ea-103">Gets a pointer to a new ICorDebugValue of the specified type, with an initial value of zero or null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="532ea-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="532ea-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateValueForType (  
    [in] ICorDebugType         *pType,  
    [out] ICorDebugValue       **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="532ea-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="532ea-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="532ea-106">podczas Wskaźnik do obiektu ICorDebugType, który reprezentuje typ.</span><span class="sxs-lookup"><span data-stu-id="532ea-106">[in] Pointer to an ICorDebugType object that represents the type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="532ea-107">określoną Wskaźnik na adres `ICorDebugValue` obiektu, który reprezentuje wartość.</span><span class="sxs-lookup"><span data-stu-id="532ea-107">[out] Pointer to the address of an `ICorDebugValue` object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="532ea-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="532ea-108">Remarks</span></span>  
 <span data-ttu-id="532ea-109">`CreateValueForType`generalizes [ICorDebugEval:: SetValue](icordebugeval-createvalue-method.md) , umożliwiając określenie dowolnego typu obiektu, w tym konstruowanych typów, takich jak `List<int>`.</span><span class="sxs-lookup"><span data-stu-id="532ea-109">`CreateValueForType` generalizes [ICorDebugEval::CreateValue](icordebugeval-createvalue-method.md) by allowing you to specify an arbitrary object type, including constructed types such as `List<int>`.</span></span> <span data-ttu-id="532ea-110">Jedynym celem tej metody jest wygenerowanie wartości, która może zostać przeniesiona do oceny funkcji.</span><span class="sxs-lookup"><span data-stu-id="532ea-110">The only purpose of this method is to generate a value that can be passed to a function evaluation.</span></span>  
  
 <span data-ttu-id="532ea-111">Typ musi być klasą lub typem wartości.</span><span class="sxs-lookup"><span data-stu-id="532ea-111">The type must be a class or a value type.</span></span> <span data-ttu-id="532ea-112">Nie można użyć tej metody do tworzenia wartości tablicy lub wartości ciągu.</span><span class="sxs-lookup"><span data-stu-id="532ea-112">You cannot use this method to create array values or string values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="532ea-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="532ea-113">Requirements</span></span>  
 <span data-ttu-id="532ea-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="532ea-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="532ea-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="532ea-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="532ea-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="532ea-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="532ea-117">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="532ea-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
