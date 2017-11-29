---
title: "IAssemblyName::IsEqual — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyName.IsEqual
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyName::IsEqual
helpviewer_keywords:
- IsEqual method [.NET Framework fusion]
- IAssemblyName::IsEqual method [.NET Framework fusion]
ms.assetid: 6dfc220f-d0d4-45b3-bfce-5829f817766f
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 51a4fbe005a8e270b9fe6767ae5173bd027a191b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iassemblynameisequal-method"></a><span data-ttu-id="e85c2-102">IAssemblyName::IsEqual — Metoda</span><span class="sxs-lookup"><span data-stu-id="e85c2-102">IAssemblyName::IsEqual Method</span></span>
<span data-ttu-id="e85c2-103">Określa, czy określonej [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) obiekt jest taki sam `IAssemblyName`zgodnie flagi porównania określony.</span><span class="sxs-lookup"><span data-stu-id="e85c2-103">Determines whether a specified [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e85c2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e85c2-104">Syntax</span></span>  
  
```  
HRESULT IsEqual (  
    [in] IAssemblyName  *pName,  
    [in] DWORD          dwCmpFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e85c2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e85c2-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="e85c2-106">[in] `IAssemblyName` Obiektu, do którego należy to porównać `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="e85c2-106">[in] The `IAssemblyName` object to which to compare this `IAssemblyName`.</span></span>  
  
 `dwCmpFlags`  
 <span data-ttu-id="e85c2-107">[in] Bitowe połączenie [ASM_CMP_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cmp-flags-enumeration.md) wartości, które wpływają porównania.</span><span class="sxs-lookup"><span data-stu-id="e85c2-107">[in] A bitwise combination of [ASM_CMP_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cmp-flags-enumeration.md) values that influence the comparison.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e85c2-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e85c2-108">Requirements</span></span>  
 <span data-ttu-id="e85c2-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e85c2-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e85c2-110">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="e85c2-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="e85c2-111">**NET Framework w wersji:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e85c2-111">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e85c2-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e85c2-112">See Also</span></span>  
 [<span data-ttu-id="e85c2-113">IAssemblyName — interfejs</span><span class="sxs-lookup"><span data-stu-id="e85c2-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="e85c2-114">Wyliczenia łączenia</span><span class="sxs-lookup"><span data-stu-id="e85c2-114">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
