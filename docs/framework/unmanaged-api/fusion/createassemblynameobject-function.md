---
title: CreateAssemblyNameObject — Funkcja
ms.date: 03/30/2017
api_name:
- CreateAssemblyNameObject
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyNameObject
helpviewer_keywords:
- CreateAssemblyNameObject function [.NET Framework fusion]
ms.assetid: 55c8b41e-fbe4-4ae0-aa29-68fbb2311691
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1412231b53763ce8e6c2400497396d2f178d8e7a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54666296"
---
# <a name="createassemblynameobject-function"></a><span data-ttu-id="50553-102">CreateAssemblyNameObject — Funkcja</span><span class="sxs-lookup"><span data-stu-id="50553-102">CreateAssemblyNameObject Function</span></span>
<span data-ttu-id="50553-103">Pobiera wskaźnik interfejsu do [iassemblyname —](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) wystąpienia, która reprezentuje unikatową tożsamość zestawu z określoną nazwą.</span><span class="sxs-lookup"><span data-stu-id="50553-103">Gets an interface pointer to an [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50553-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="50553-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyNameObject (  
    [out] LPASSEMBLYNAME  *ppAssemblyNameObj,  
    [in]  LPCWSTR         szAssemblyName,  
    [in]  DWORD           dwFlags,  
    [in]  LPVOID          pvReserved  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="50553-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="50553-105">Parameters</span></span>  
 `ppAssemblyNameObj`  
 <span data-ttu-id="50553-106">[out] Zwrócony `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="50553-106">[out] The returned `IAssemblyName`.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="50553-107">[in] Nazwa zestawu, dla której chcesz utworzyć nowy `IAssemblyName` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="50553-107">[in] The name of the assembly for which to create the new `IAssemblyName` instance.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="50553-108">[in] Flagi do przekazania do konstruktora obiektu.</span><span class="sxs-lookup"><span data-stu-id="50553-108">[in] Flags to pass to the object constructor.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="50553-109">[in] Zarezerwowane dla przyszłej rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="50553-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="50553-110">`pvReserved` musi być odwołanie o wartości null.</span><span class="sxs-lookup"><span data-stu-id="50553-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50553-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="50553-111">Requirements</span></span>  
 <span data-ttu-id="50553-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50553-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50553-113">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="50553-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="50553-114">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="50553-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="50553-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50553-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50553-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="50553-116">See also</span></span>
- [<span data-ttu-id="50553-117">IAssemblyName, interfejs</span><span class="sxs-lookup"><span data-stu-id="50553-117">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="50553-118">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="50553-118">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
