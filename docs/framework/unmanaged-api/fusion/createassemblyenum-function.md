---
title: CreateAssemblyEnum — Funkcja
ms.date: 03/30/2017
api_name:
- CreateAssemblyEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyEnum
helpviewer_keywords:
- CreateAssemblyEnum function [.NET Framework fusion]
ms.assetid: 3506df38-6cea-42f6-946e-4287863bcfb3
topic_type:
- apiref
ms.openlocfilehash: 0e54027806cef07fad4740c3bf5226fd26c72570
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108778"
---
# <a name="createassemblyenum-function"></a><span data-ttu-id="04129-102">CreateAssemblyEnum — Funkcja</span><span class="sxs-lookup"><span data-stu-id="04129-102">CreateAssemblyEnum Function</span></span>
<span data-ttu-id="04129-103">Pobiera wskaźnik do wystąpienia [IAssemblyEnum](iassemblyenum-interface.md) , które może wyliczyć obiekty w zestawie przy użyciu określonego [IAssemblyName](iassemblyname-interface.md).</span><span class="sxs-lookup"><span data-stu-id="04129-103">Gets a pointer to an [IAssemblyEnum](iassemblyenum-interface.md) instance that can enumerate the objects in the assembly with the specified [IAssemblyName](iassemblyname-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04129-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="04129-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyEnum (  
    [out] IAssemblyEnum  **pEnum,  
    [in]  IUnknown       *pUnkReserved,  
    [in]  IAssemblyName  *pName,  
    [in]  DWORD          dwFlags,  
    [in]  LPVOID         pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="04129-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="04129-105">Parameters</span></span>  
 `pEnum`  
 <span data-ttu-id="04129-106">określoną Wskaźnik do lokalizacji pamięci zawierającej żądany `IAssemblyEnum` wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="04129-106">[out] Pointer to a memory location that contains the requested `IAssemblyEnum` pointer.</span></span>  
  
 `pUnkReserved`  
 <span data-ttu-id="04129-107">podczas Zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="04129-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="04129-108">`pUnkReserved` musi być odwołaniem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="04129-108">`pUnkReserved` must be a null reference.</span></span>  
  
 `pName`  
 <span data-ttu-id="04129-109">podczas `IAssemblyName` żądanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="04129-109">[in] The `IAssemblyName` of the requested assembly.</span></span> <span data-ttu-id="04129-110">Ta nazwa jest używana do filtrowania wyliczania.</span><span class="sxs-lookup"><span data-stu-id="04129-110">This name is used to filter the enumeration.</span></span> <span data-ttu-id="04129-111">Może ona mieć wartość null, aby wyliczyć wszystkie zestawy w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="04129-111">It can be null to enumerate all assemblies in the global assembly cache.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="04129-112">podczas Flagi modyfikujące zachowanie modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="04129-112">[in] Flags for modifying the enumerator's behavior.</span></span> <span data-ttu-id="04129-113">Ten parametr zawiera dokładnie jeden bit z wyliczenia [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="04129-113">This parameter contains exactly one bit from the [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) enumeration.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="04129-114">podczas Zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="04129-114">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="04129-115">`pvReserved` musi być odwołaniem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="04129-115">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04129-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="04129-116">Remarks</span></span>  
 <span data-ttu-id="04129-117">Parametr `dwFlags` zawiera dokładnie jeden bit z wyliczenia `ASM_CACHE_FLAGS`.</span><span class="sxs-lookup"><span data-stu-id="04129-117">The `dwFlags` parameter contains exactly one bit from the `ASM_CACHE_FLAGS` enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04129-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="04129-118">Requirements</span></span>  
 <span data-ttu-id="04129-119">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04129-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04129-120">**Nagłówek:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="04129-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="04129-121">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="04129-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="04129-122">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04129-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04129-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="04129-123">See also</span></span>

- [<span data-ttu-id="04129-124">IAssemblyEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="04129-124">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)
- [<span data-ttu-id="04129-125">IAssemblyName, interfejs</span><span class="sxs-lookup"><span data-stu-id="04129-125">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="04129-126">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="04129-126">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
