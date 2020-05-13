---
title: ICorDebugType::EnumerateTypeParameters — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugType.EnumerateTypeParameters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::EnumerateTypeParameters
helpviewer_keywords:
- EnumerateTypeParameters method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::EnumerateTypeParameters method [.NET Framework debugging]
ms.assetid: 1ee1f6e6-1bd7-4ebb-83b8-ff9a08ca03de
topic_type:
- apiref
ms.openlocfilehash: dc6bf4f02c49788e640c6e230f864e3ca8e71b0d
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83380006"
---
# <a name="icordebugtypeenumeratetypeparameters-method"></a><span data-ttu-id="85975-102">ICorDebugType::EnumerateTypeParameters — Metoda</span><span class="sxs-lookup"><span data-stu-id="85975-102">ICorDebugType::EnumerateTypeParameters Method</span></span>
<span data-ttu-id="85975-103">Pobiera wskaźnik interfejsu do ICorDebugTypeEnum zawierającego <xref:System.Type> Parametry klasy, do której odwołuje się ten ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="85975-103">Gets an interface pointer to an ICorDebugTypeEnum that contains the <xref:System.Type> parameters of the class referenced by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85975-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="85975-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum   **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85975-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="85975-105">Parameters</span></span>  
 `ppTyParEnum`  
 <span data-ttu-id="85975-106">określoną Wskaźnik na adres `ICorDebugTypeEnum` , który zawiera parametry typu.</span><span class="sxs-lookup"><span data-stu-id="85975-106">[out] A pointer to the address of an `ICorDebugTypeEnum` that contains the parameters of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85975-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="85975-107">Remarks</span></span>  
 <span data-ttu-id="85975-108">Można użyć `EnumerateTypeParameters` , jeśli wartość CorElementType — zwrócona przez [ICorDebugType:: GetType](icordebugtype-gettype-method.md) ma ELEMENT_TYPE_CLASS, ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, ELEMENT_TYPE_PTR lub ELEMENT_TYPE_FNPTR.</span><span class="sxs-lookup"><span data-stu-id="85975-108">You can use `EnumerateTypeParameters` if the CorElementType value returned by [ICorDebugType::GetType](icordebugtype-gettype-method.md) is ELEMENT_TYPE_CLASS, ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, ELEMENT_TYPE_PTR, or ELEMENT_TYPE_FNPTR.</span></span> <span data-ttu-id="85975-109">Liczba parametrów i ich kolejność zależy od typu:</span><span class="sxs-lookup"><span data-stu-id="85975-109">The number of parameters and their order depends on the type:</span></span>  
  
- <span data-ttu-id="85975-110">ELEMENT_TYPE_CLASS lub ELEMENT_TYPE_VALUETYPE: liczba parametrów typu zawartych w `ICorDebugTypeEnum` tej metodzie, która zwraca wartość, będzie zależeć od liczby parametrów typu formalnego dla odpowiadającej klasy.</span><span class="sxs-lookup"><span data-stu-id="85975-110">ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE: The number of type parameters contained in the `ICorDebugTypeEnum` that this method returns, will depend on the number of formal type parameters for the corresponding class.</span></span> <span data-ttu-id="85975-111">Na przykład, jeśli typ to, zwróci wartość zawierającą `class Dict<String,int32>` `EnumerateTypeParameters` `ICorDebugTypeEnum` obiekty reprezentujące `String` i `int32` w kolejności.</span><span class="sxs-lookup"><span data-stu-id="85975-111">For example, if the type is `class Dict<String,int32>`, then `EnumerateTypeParameters` will return an `ICorDebugTypeEnum` that contains objects representing `String` and `int32` in sequence.</span></span>  
  
- <span data-ttu-id="85975-112">ELEMENT_TYPE_FNPTR: liczba parametrów typu zawartych w elemencie `ICorDebugTypeEnum` będzie większa niż liczba argumentów akceptowanych przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="85975-112">ELEMENT_TYPE_FNPTR: The number of type parameters contained in the `ICorDebugTypeEnum` will be one greater than the number of arguments accepted by the function.</span></span> <span data-ttu-id="85975-113">Pierwszy parametr typu zawarty w elemencie `ICorDebugTypeEnum` jest typem zwracanym dla funkcji, a kolejne parametry typu są parametrami funkcji.</span><span class="sxs-lookup"><span data-stu-id="85975-113">The first type parameter contained in the `ICorDebugTypeEnum` is the return type for the function, and the subsequent type parameters are the function's parameters.</span></span>  
  
- <span data-ttu-id="85975-114">ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF lub ELEMENT_TYPE_PTR: zostanie zwrócony jeden parametr typu.</span><span class="sxs-lookup"><span data-stu-id="85975-114">ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, or ELEMENT_TYPE_PTR: One type parameter will be returned.</span></span> <span data-ttu-id="85975-115">Na przykład, jeśli typ jest typem tablicowym, na przykład `int32[]` , zwróci `EnumerateTypeParameters` element `ICorDebugTypeEnum` zawierający obiekt reprezentujący `int32` .</span><span class="sxs-lookup"><span data-stu-id="85975-115">For example, if the type is an array type such as `int32[]`,`EnumerateTypeParameters` will return an `ICorDebugTypeEnum` that contains an object representing `int32`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85975-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="85975-116">Requirements</span></span>  
 <span data-ttu-id="85975-117">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85975-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85975-118">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="85975-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="85975-119">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="85975-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85975-120">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85975-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
