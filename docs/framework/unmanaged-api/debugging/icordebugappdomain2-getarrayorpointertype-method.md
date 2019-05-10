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
ms.openlocfilehash: 6cc38ef23a8b802d674a7a6dc4807371e432f73d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593515"
---
# <a name="icordebugappdomain2getarrayorpointertype-method"></a><span data-ttu-id="eea24-102">ICorDebugAppDomain2::GetArrayOrPointerType — Metoda</span><span class="sxs-lookup"><span data-stu-id="eea24-102">ICorDebugAppDomain2::GetArrayOrPointerType Method</span></span>
<span data-ttu-id="eea24-103">Pobiera tablicę elementów określonego typu lub wskaźnik lub odwołanie do określonego typu.</span><span class="sxs-lookup"><span data-stu-id="eea24-103">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eea24-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="eea24-104">Syntax</span></span>  
  
```  
HRESULT GetArrayOrPointerType (  
    [in]  CorElementType    elementType,  
    [in]  ULONG32           nRank,  
    [in]  ICorDebugType     *pTypeArg,  
    [out] ICorDebugType     **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eea24-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eea24-105">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="eea24-106">[in] Wartość corelementtype — wyliczenie, określający typ podstawowy natywnego (tablicy, wskaźnika lub odwołania) ma zostać utworzony.</span><span class="sxs-lookup"><span data-stu-id="eea24-106">[in] A value of the CorElementType enumeration that specifies the underlying native type (an array, pointer, or reference) to be created.</span></span>  
  
 `nRank`  
 <span data-ttu-id="eea24-107">[in] Ranga (oznacza to, że liczba wymiarów) tablicy.</span><span class="sxs-lookup"><span data-stu-id="eea24-107">[in] The rank (that is, number of dimensions) of the array.</span></span> <span data-ttu-id="eea24-108">Ta wartość musi wynosić 0, jeśli `elementType` Określa typ wskaźnika lub odwołania.</span><span class="sxs-lookup"><span data-stu-id="eea24-108">This value must be 0 if `elementType` specifies a pointer or reference type.</span></span>  
  
 `pTypeArg`  
 <span data-ttu-id="eea24-109">[in] Wskaźnik do obiektu ICorDebugType, który reprezentuje typ tablicy, wskaźnika lub odwołania do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="eea24-109">[in] A pointer to an ICorDebugType object that represents the type of array, pointer, or reference to be created.</span></span>  
  
 `ppType`  
 <span data-ttu-id="eea24-110">[out] Wskaźnik na adres `ICorDebugType` typ obiektu, który reprezentuje zbudowany tablicy, typ wskaźnika lub odwołania.</span><span class="sxs-lookup"><span data-stu-id="eea24-110">[out] A pointer to the address of an `ICorDebugType` object that represents the constructed array, pointer type, or reference type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eea24-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="eea24-111">Remarks</span></span>  
 <span data-ttu-id="eea24-112">Wartość *elementType* musi mieć jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="eea24-112">The value of *elementType* must be one of the following:</span></span>  
  
- <span data-ttu-id="eea24-113">ELEMENT_TYPE_PTR</span><span class="sxs-lookup"><span data-stu-id="eea24-113">ELEMENT_TYPE_PTR</span></span>  
  
- <span data-ttu-id="eea24-114">POLE</span><span class="sxs-lookup"><span data-stu-id="eea24-114">ELEMENT_TYPE_BYREF</span></span>  
  
- <span data-ttu-id="eea24-115">ELEMENT_TYPE_ARRAY lub ELEMENT_TYPE_SZARRAY</span><span class="sxs-lookup"><span data-stu-id="eea24-115">ELEMENT_TYPE_ARRAY or ELEMENT_TYPE_SZARRAY</span></span>  
  
 <span data-ttu-id="eea24-116">Jeśli wartość *elementType* ELEMENT_TYPE_PTR lub pole, *nRank* musi mieć wartość zero.</span><span class="sxs-lookup"><span data-stu-id="eea24-116">If the value of *elementType* is ELEMENT_TYPE_PTR or ELEMENT_TYPE_BYREF, *nRank* must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eea24-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="eea24-117">Requirements</span></span>  
 <span data-ttu-id="eea24-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eea24-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eea24-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eea24-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eea24-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eea24-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eea24-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eea24-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
