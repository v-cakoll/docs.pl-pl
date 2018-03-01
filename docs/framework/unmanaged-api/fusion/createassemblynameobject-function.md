---
title: "CreateAssemblyNameObject — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2d2616bd7aee878ebbc1d196cb1ac5f90ae7bd04
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="createassemblynameobject-function"></a><span data-ttu-id="6d9e7-102">CreateAssemblyNameObject — Funkcja</span><span class="sxs-lookup"><span data-stu-id="6d9e7-102">CreateAssemblyNameObject Function</span></span>
<span data-ttu-id="6d9e7-103">Pobiera wskaźnika interfejsu do [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) wystąpienia, który reprezentuje unikatową tożsamość zestawu o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="6d9e7-103">Gets an interface pointer to an [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d9e7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6d9e7-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyNameObject (  
    [out] LPASSEMBLYNAME  *ppAssemblyNameObj,  
    [in]  LPCWSTR         szAssemblyName,  
    [in]  DWORD           dwFlags,  
    [in]  LPVOID          pvReserved  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6d9e7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6d9e7-105">Parameters</span></span>  
 `ppAssemblyNameObj`  
 <span data-ttu-id="6d9e7-106">[out] Zwrócona `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="6d9e7-106">[out] The returned `IAssemblyName`.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="6d9e7-107">[in] Nazwa zestawu, do których chcesz utworzyć nowe `IAssemblyName` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="6d9e7-107">[in] The name of the assembly for which to create the new `IAssemblyName` instance.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="6d9e7-108">[in] Flagi do przekazania do konstruktora obiektu.</span><span class="sxs-lookup"><span data-stu-id="6d9e7-108">[in] Flags to pass to the object constructor.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="6d9e7-109">[in] Zarezerwowane dla przyszłego rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="6d9e7-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="6d9e7-110">`pvReserved`musi być odwołanie o wartości null.</span><span class="sxs-lookup"><span data-stu-id="6d9e7-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d9e7-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6d9e7-111">Requirements</span></span>  
 <span data-ttu-id="6d9e7-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d9e7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d9e7-113">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="6d9e7-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="6d9e7-114">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6d9e7-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6d9e7-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d9e7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d9e7-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6d9e7-116">See Also</span></span>  
 [<span data-ttu-id="6d9e7-117">IAssemblyName, interfejs</span><span class="sxs-lookup"><span data-stu-id="6d9e7-117">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="6d9e7-118">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="6d9e7-118">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
