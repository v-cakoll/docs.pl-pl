---
title: "IAssemblyName::GetVersion — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyName.GetVersion
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyName::GetVersion
helpviewer_keywords:
- IAssemblyName::GetVersion method [.NET Framework fusion]
- GetVersion method, IAssemblyName interface [.NET Framework fusion]
ms.assetid: 42230928-2c33-41fd-9519-d96efef6c7af
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5a843ca1ebc12b0ae9aaf1d9dbb4e5d845fb61fe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="iassemblynamegetversion-method"></a><span data-ttu-id="38edc-102">IAssemblyName::GetVersion — Metoda</span><span class="sxs-lookup"><span data-stu-id="38edc-102">IAssemblyName::GetVersion Method</span></span>
<span data-ttu-id="38edc-103">Pobiera informacje o wersji dla zestawu odwołuje się ten [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="38edc-103">Gets the version information for the assembly referenced by this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38edc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="38edc-104">Syntax</span></span>  
  
```  
HRESULT GetVersion (  
    [out] LPDWORD pdwVersionHi,  
    [out] LPDWORD pdwVersionLow  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="38edc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="38edc-105">Parameters</span></span>  
 `pdwVersionHi`  
 <span data-ttu-id="38edc-106">[out] Starsze 32 bity wersji.</span><span class="sxs-lookup"><span data-stu-id="38edc-106">[out] The high 32 bits of the version.</span></span>  
  
 `pdwVersionLow`  
 <span data-ttu-id="38edc-107">[out] Niski 32 bity wersji.</span><span class="sxs-lookup"><span data-stu-id="38edc-107">[out] The low 32 bits of the version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38edc-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="38edc-108">Requirements</span></span>  
 <span data-ttu-id="38edc-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38edc-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38edc-110">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="38edc-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="38edc-111">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38edc-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38edc-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="38edc-112">See Also</span></span>  
 [<span data-ttu-id="38edc-113">IAssemblyName — interfejs</span><span class="sxs-lookup"><span data-stu-id="38edc-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
