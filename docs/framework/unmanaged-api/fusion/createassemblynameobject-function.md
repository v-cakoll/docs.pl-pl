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
ms.openlocfilehash: cd8609bedcea28c1cb8559d378b5e171f3ad568e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61669965"
---
# <a name="createassemblynameobject-function"></a><span data-ttu-id="23073-102">CreateAssemblyNameObject — Funkcja</span><span class="sxs-lookup"><span data-stu-id="23073-102">CreateAssemblyNameObject Function</span></span>
<span data-ttu-id="23073-103">Pobiera wskaźnik interfejsu do [iassemblyname —](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) wystąpienia, która reprezentuje unikatową tożsamość zestawu z określoną nazwą.</span><span class="sxs-lookup"><span data-stu-id="23073-103">Gets an interface pointer to an [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23073-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="23073-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyNameObject (  
    [out] LPASSEMBLYNAME  *ppAssemblyNameObj,  
    [in]  LPCWSTR         szAssemblyName,  
    [in]  DWORD           dwFlags,  
    [in]  LPVOID          pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="23073-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="23073-105">Parameters</span></span>  
 `ppAssemblyNameObj`  
 <span data-ttu-id="23073-106">[out] Zwrócony `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="23073-106">[out] The returned `IAssemblyName`.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="23073-107">[in] Nazwa zestawu, dla której chcesz utworzyć nowy `IAssemblyName` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="23073-107">[in] The name of the assembly for which to create the new `IAssemblyName` instance.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="23073-108">[in] Flagi do przekazania do konstruktora obiektu.</span><span class="sxs-lookup"><span data-stu-id="23073-108">[in] Flags to pass to the object constructor.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="23073-109">[in] Zarezerwowane dla przyszłej rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="23073-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="23073-110">`pvReserved` musi być odwołanie o wartości null.</span><span class="sxs-lookup"><span data-stu-id="23073-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23073-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="23073-111">Requirements</span></span>  
 <span data-ttu-id="23073-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23073-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23073-113">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="23073-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="23073-114">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="23073-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="23073-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23073-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23073-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="23073-116">See also</span></span>

- [<span data-ttu-id="23073-117">IAssemblyName, interfejs</span><span class="sxs-lookup"><span data-stu-id="23073-117">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="23073-118">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="23073-118">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
