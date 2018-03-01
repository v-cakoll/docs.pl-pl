---
title: "IAssemblyName::IsEqual — Metoda"
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
- IAssemblyName.IsEqual
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::IsEqual
helpviewer_keywords:
- IsEqual method [.NET Framework fusion]
- IAssemblyName::IsEqual method [.NET Framework fusion]
ms.assetid: 6dfc220f-d0d4-45b3-bfce-5829f817766f
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 454226d45474abea67b944e8437cf53be5c8ed1f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblynameisequal-method"></a><span data-ttu-id="1f434-102">IAssemblyName::IsEqual — Metoda</span><span class="sxs-lookup"><span data-stu-id="1f434-102">IAssemblyName::IsEqual Method</span></span>
<span data-ttu-id="1f434-103">Określa, czy określonej [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) obiekt jest taki sam `IAssemblyName`zgodnie flagi porównania określony.</span><span class="sxs-lookup"><span data-stu-id="1f434-103">Determines whether a specified [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f434-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1f434-104">Syntax</span></span>  
  
```  
HRESULT IsEqual (  
    [in] IAssemblyName  *pName,  
    [in] DWORD          dwCmpFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1f434-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1f434-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="1f434-106">[in] `IAssemblyName` Obiektu, do którego należy to porównać `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="1f434-106">[in] The `IAssemblyName` object to which to compare this `IAssemblyName`.</span></span>  
  
 `dwCmpFlags`  
 <span data-ttu-id="1f434-107">[in] Bitowe połączenie [ASM_CMP_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cmp-flags-enumeration.md) wartości, które wpływają porównania.</span><span class="sxs-lookup"><span data-stu-id="1f434-107">[in] A bitwise combination of [ASM_CMP_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cmp-flags-enumeration.md) values that influence the comparison.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f434-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1f434-108">Requirements</span></span>  
 <span data-ttu-id="1f434-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f434-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f434-110">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="1f434-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="1f434-111">**NET Framework w wersji:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f434-111">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f434-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1f434-112">See Also</span></span>  
 [<span data-ttu-id="1f434-113">IAssemblyName, interfejs</span><span class="sxs-lookup"><span data-stu-id="1f434-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="1f434-114">Wyliczenia łączenia</span><span class="sxs-lookup"><span data-stu-id="1f434-114">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
