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
ms.openlocfilehash: b2c381d093069f5ee86be1b19d75f5c2d69ad9fa
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791309"
---
# <a name="icordebugtypeenumeratetypeparameters-method"></a><span data-ttu-id="904dd-102">ICorDebugType::EnumerateTypeParameters — Metoda</span><span class="sxs-lookup"><span data-stu-id="904dd-102">ICorDebugType::EnumerateTypeParameters Method</span></span>
<span data-ttu-id="904dd-103">Pobiera wskaźnik interfejsu do ICorDebugTypeEnum, który zawiera <xref:System.Type> parametry klasy, do których odwołuje się ten ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="904dd-103">Gets an interface pointer to an ICorDebugTypeEnum that contains the <xref:System.Type> parameters of the class referenced by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="904dd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="904dd-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum   **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="904dd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="904dd-105">Parameters</span></span>  
 `ppTyParEnum`  
 <span data-ttu-id="904dd-106">określoną Wskaźnik do adresu `ICorDebugTypeEnum`, który zawiera parametry typu.</span><span class="sxs-lookup"><span data-stu-id="904dd-106">[out] A pointer to the address of an `ICorDebugTypeEnum` that contains the parameters of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="904dd-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="904dd-107">Remarks</span></span>  
 <span data-ttu-id="904dd-108">Można użyć `EnumerateTypeParameters`, jeśli wartość CorElementType — zwracana przez [ICorDebugType:: GetType](icordebugtype-gettype-method.md) to ELEMENT_TYPE_CLASS, ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, ELEMENT_TYPE_PTR lub ELEMENT_TYPE_FNPTR.</span><span class="sxs-lookup"><span data-stu-id="904dd-108">You can use `EnumerateTypeParameters` if the CorElementType value returned by [ICorDebugType::GetType](icordebugtype-gettype-method.md) is ELEMENT_TYPE_CLASS, ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, ELEMENT_TYPE_PTR, or ELEMENT_TYPE_FNPTR.</span></span> <span data-ttu-id="904dd-109">Liczba parametrów i ich kolejność zależy od typu:</span><span class="sxs-lookup"><span data-stu-id="904dd-109">The number of parameters and their order depends on the type:</span></span>  
  
- <span data-ttu-id="904dd-110">ELEMENT_TYPE_CLASS lub ELEMENT_TYPE_VALUETYPE: liczba parametrów typu zawartych w `ICorDebugTypeEnum`, które ta metoda zwraca, będzie zależeć od liczby parametrów typu formalnego dla odpowiadającej klasy.</span><span class="sxs-lookup"><span data-stu-id="904dd-110">ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE: The number of type parameters contained in the `ICorDebugTypeEnum` that this method returns, will depend on the number of formal type parameters for the corresponding class.</span></span> <span data-ttu-id="904dd-111">Na przykład, jeśli typ to `class Dict<String,int32>`, wówczas `EnumerateTypeParameters` zwróci `ICorDebugTypeEnum`, który zawiera obiekty reprezentujące `String` i `int32` w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="904dd-111">For example, if the type is `class Dict<String,int32>`, then `EnumerateTypeParameters` will return an `ICorDebugTypeEnum` that contains objects representing `String` and `int32` in sequence.</span></span>  
  
- <span data-ttu-id="904dd-112">ELEMENT_TYPE_FNPTR: liczba parametrów typu zawartych w `ICorDebugTypeEnum` będzie większa niż liczba argumentów akceptowanych przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="904dd-112">ELEMENT_TYPE_FNPTR: The number of type parameters contained in the `ICorDebugTypeEnum` will be one greater than the number of arguments accepted by the function.</span></span> <span data-ttu-id="904dd-113">Pierwszy parametr typu zawarty w `ICorDebugTypeEnum` jest typem zwracanym dla funkcji, a kolejne parametry typu są parametrami funkcji.</span><span class="sxs-lookup"><span data-stu-id="904dd-113">The first type parameter contained in the `ICorDebugTypeEnum` is the return type for the function, and the subsequent type parameters are the function's parameters.</span></span>  
  
- <span data-ttu-id="904dd-114">ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF lub ELEMENT_TYPE_PTR: zostanie zwrócony jeden parametr typu.</span><span class="sxs-lookup"><span data-stu-id="904dd-114">ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, or ELEMENT_TYPE_PTR: One type parameter will be returned.</span></span> <span data-ttu-id="904dd-115">Na przykład, jeśli typ jest typem tablicy, takim jak `int32[]`,`EnumerateTypeParameters` zwróci `ICorDebugTypeEnum`, który zawiera obiekt reprezentujący `int32`.</span><span class="sxs-lookup"><span data-stu-id="904dd-115">For example, if the type is an array type such as `int32[]`,`EnumerateTypeParameters` will return an `ICorDebugTypeEnum` that contains an object representing `int32`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="904dd-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="904dd-116">Requirements</span></span>  
 <span data-ttu-id="904dd-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="904dd-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="904dd-118">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="904dd-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="904dd-119">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="904dd-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="904dd-120">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="904dd-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
