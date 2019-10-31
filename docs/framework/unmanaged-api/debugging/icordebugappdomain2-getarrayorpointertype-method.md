---
title: ICorDebugAppDomain2::GetArrayOrPointerType — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain2.GetArrayOrPointerType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2::GetArrayOrPointerType
helpviewer_keywords:
- GetArrayOrPointerType method [.NET Framework debugging]
- ICorDebugAppDomain2::GetArrayOrPointerType method [.NET Framework debugging]
ms.assetid: 97e493f5-3a62-4ec7-b42f-4af57bf71f57
topic_type:
- apiref
ms.openlocfilehash: 166f6bb50849df8550871958d7034fdf2a841abb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73089113"
---
# <a name="icordebugappdomain2getarrayorpointertype-method"></a><span data-ttu-id="37e52-102">ICorDebugAppDomain2::GetArrayOrPointerType — Metoda</span><span class="sxs-lookup"><span data-stu-id="37e52-102">ICorDebugAppDomain2::GetArrayOrPointerType Method</span></span>
<span data-ttu-id="37e52-103">Pobiera tablicę określonego typu lub wskaźnik lub odwołanie do określonego typu.</span><span class="sxs-lookup"><span data-stu-id="37e52-103">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37e52-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="37e52-104">Syntax</span></span>  
  
```cpp  
HRESULT GetArrayOrPointerType (  
    [in]  CorElementType    elementType,  
    [in]  ULONG32           nRank,  
    [in]  ICorDebugType     *pTypeArg,  
    [out] ICorDebugType     **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37e52-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="37e52-105">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="37e52-106">podczas Wartość wyliczenia CorElementType —, która określa odpowiedni typ natywny (tablicę, wskaźnik lub odwołanie), który ma zostać utworzony.</span><span class="sxs-lookup"><span data-stu-id="37e52-106">[in] A value of the CorElementType enumeration that specifies the underlying native type (an array, pointer, or reference) to be created.</span></span>  
  
 `nRank`  
 <span data-ttu-id="37e52-107">podczas Ranga (czyli liczba wymiarów) tablicy.</span><span class="sxs-lookup"><span data-stu-id="37e52-107">[in] The rank (that is, number of dimensions) of the array.</span></span> <span data-ttu-id="37e52-108">Ta wartość musi być równa 0, jeśli `elementType` określa wskaźnik lub typ referencyjny.</span><span class="sxs-lookup"><span data-stu-id="37e52-108">This value must be 0 if `elementType` specifies a pointer or reference type.</span></span>  
  
 `pTypeArg`  
 <span data-ttu-id="37e52-109">podczas Wskaźnik do obiektu ICorDebugType, który reprezentuje typ tablicy, wskaźnika lub odwołania, które mają zostać utworzone.</span><span class="sxs-lookup"><span data-stu-id="37e52-109">[in] A pointer to an ICorDebugType object that represents the type of array, pointer, or reference to be created.</span></span>  
  
 `ppType`  
 <span data-ttu-id="37e52-110">określoną Wskaźnik do adresu obiektu `ICorDebugType`, który reprezentuje skonstruowaną tablicę, typ wskaźnika lub typ referencyjny.</span><span class="sxs-lookup"><span data-stu-id="37e52-110">[out] A pointer to the address of an `ICorDebugType` object that represents the constructed array, pointer type, or reference type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37e52-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="37e52-111">Remarks</span></span>  
 <span data-ttu-id="37e52-112">Wartość *elementu ElementType* musi być jedną z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="37e52-112">The value of *elementType* must be one of the following:</span></span>  
  
- <span data-ttu-id="37e52-113">ELEMENT_TYPE_PTR</span><span class="sxs-lookup"><span data-stu-id="37e52-113">ELEMENT_TYPE_PTR</span></span>  
  
- <span data-ttu-id="37e52-114">ELEMENT_TYPE_BYREF</span><span class="sxs-lookup"><span data-stu-id="37e52-114">ELEMENT_TYPE_BYREF</span></span>  
  
- <span data-ttu-id="37e52-115">ELEMENT_TYPE_ARRAY lub ELEMENT_TYPE_SZARRAY</span><span class="sxs-lookup"><span data-stu-id="37e52-115">ELEMENT_TYPE_ARRAY or ELEMENT_TYPE_SZARRAY</span></span>  
  
 <span data-ttu-id="37e52-116">Jeśli wartość *elementu ElementType* to ELEMENT_TYPE_PTR lub ELEMENT_TYPE_BYREF, *nRank* musi mieć wartość zero.</span><span class="sxs-lookup"><span data-stu-id="37e52-116">If the value of *elementType* is ELEMENT_TYPE_PTR or ELEMENT_TYPE_BYREF, *nRank* must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37e52-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="37e52-117">Requirements</span></span>  
 <span data-ttu-id="37e52-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37e52-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37e52-119">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="37e52-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="37e52-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="37e52-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="37e52-121">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37e52-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
