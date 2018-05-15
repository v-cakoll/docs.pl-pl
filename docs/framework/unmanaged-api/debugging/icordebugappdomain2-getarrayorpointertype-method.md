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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb3f0ca6d930b22f30fe9bbc5b5a04bf1e034f34
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugappdomain2getarrayorpointertype-method"></a><span data-ttu-id="b892c-102">ICorDebugAppDomain2::GetArrayOrPointerType — Metoda</span><span class="sxs-lookup"><span data-stu-id="b892c-102">ICorDebugAppDomain2::GetArrayOrPointerType Method</span></span>
<span data-ttu-id="b892c-103">Pobiera tablicę określonego typu lub wskaźnik lub odwołanie do określonego typu.</span><span class="sxs-lookup"><span data-stu-id="b892c-103">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b892c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b892c-104">Syntax</span></span>  
  
```  
HRESULT GetArrayOrPointerType (  
    [in]  CorElementType    elementType,  
    [in]  ULONG32           nRank,  
    [in]  ICorDebugType     *pTypeArg,  
    [out] ICorDebugType     **ppType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b892c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b892c-105">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="b892c-106">[in] Wartość wyliczenia CorElementType określający typ podstawowy natywnego (tablicy, wskaźnika lub odwołania) ma zostać utworzony.</span><span class="sxs-lookup"><span data-stu-id="b892c-106">[in] A value of the CorElementType enumeration that specifies the underlying native type (an array, pointer, or reference) to be created.</span></span>  
  
 `nRank`  
 <span data-ttu-id="b892c-107">[in] Ranga (to znaczy, że liczba wymiarów) tablicy.</span><span class="sxs-lookup"><span data-stu-id="b892c-107">[in] The rank (that is, number of dimensions) of the array.</span></span> <span data-ttu-id="b892c-108">Ta wartość musi wynosić 0, jeśli `elementType` Określa typ wskaźnika lub odwołania.</span><span class="sxs-lookup"><span data-stu-id="b892c-108">This value must be 0 if `elementType` specifies a pointer or reference type.</span></span>  
  
 `pTypeArg`  
 <span data-ttu-id="b892c-109">[in] Wskaźnik do obiektu ICorDebugType, który reprezentuje typ tablicy, wskaźnika lub odwołania do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="b892c-109">[in] A pointer to an ICorDebugType object that represents the type of array, pointer, or reference to be created.</span></span>  
  
 `ppType`  
 <span data-ttu-id="b892c-110">[out] Wskaźnik do adresu `ICorDebugType` typu obiektu, który reprezentuje skonstruowane tablicy, typ wskaźnika lub odwołania.</span><span class="sxs-lookup"><span data-stu-id="b892c-110">[out] A pointer to the address of an `ICorDebugType` object that represents the constructed array, pointer type, or reference type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b892c-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b892c-111">Remarks</span></span>  
 <span data-ttu-id="b892c-112">Wartość *elementType* musi mieć jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="b892c-112">The value of *elementType* must be one of the following:</span></span>  
  
-   <span data-ttu-id="b892c-113">POPRAWNOŚCI ELEMENTU ELEMENT_TYPE_PTR</span><span class="sxs-lookup"><span data-stu-id="b892c-113">ELEMENT_TYPE_PTR</span></span>  
  
-   <span data-ttu-id="b892c-114">ELEMENT_TYPE_BYREF</span><span class="sxs-lookup"><span data-stu-id="b892c-114">ELEMENT_TYPE_BYREF</span></span>  
  
-   <span data-ttu-id="b892c-115">ELEMENT_TYPE_ARRAY lub ELEMENT_TYPE_SZARRAY</span><span class="sxs-lookup"><span data-stu-id="b892c-115">ELEMENT_TYPE_ARRAY or ELEMENT_TYPE_SZARRAY</span></span>  
  
 <span data-ttu-id="b892c-116">Jeśli wartość *elementType* poprawności elementu ELEMENT_TYPE_PTR lub ELEMENT_TYPE_BYREF, *nRank* musi mieć wartość zero.</span><span class="sxs-lookup"><span data-stu-id="b892c-116">If the value of *elementType* is ELEMENT_TYPE_PTR or ELEMENT_TYPE_BYREF, *nRank* must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b892c-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b892c-117">Requirements</span></span>  
 <span data-ttu-id="b892c-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b892c-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b892c-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b892c-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b892c-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b892c-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b892c-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b892c-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
