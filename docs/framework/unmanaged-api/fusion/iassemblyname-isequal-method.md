---
title: IAssemblyName::IsEqual — Metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 80402234d9374fa4f16e1f8bb315536a9bdfb2c2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697215"
---
# <a name="iassemblynameisequal-method"></a><span data-ttu-id="d0855-102">IAssemblyName::IsEqual — Metoda</span><span class="sxs-lookup"><span data-stu-id="d0855-102">IAssemblyName::IsEqual Method</span></span>
<span data-ttu-id="d0855-103">Określa, czy określony [iassemblyname —](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) obiekt jest taki sam tym `IAssemblyName`zgodnie z flagi porównania określony.</span><span class="sxs-lookup"><span data-stu-id="d0855-103">Determines whether a specified [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0855-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d0855-104">Syntax</span></span>  
  
```  
HRESULT IsEqual (  
    [in] IAssemblyName  *pName,  
    [in] DWORD          dwCmpFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0855-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d0855-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="d0855-106">[in] `IAssemblyName` Obiekt, do którego można to porównać `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="d0855-106">[in] The `IAssemblyName` object to which to compare this `IAssemblyName`.</span></span>  
  
 `dwCmpFlags`  
 <span data-ttu-id="d0855-107">[in] Bitowa kombinacja [asm_cmp_flags —](../../../../docs/framework/unmanaged-api/fusion/asm-cmp-flags-enumeration.md) wartości, które mają wpływ na wynik porównania.</span><span class="sxs-lookup"><span data-stu-id="d0855-107">[in] A bitwise combination of [ASM_CMP_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cmp-flags-enumeration.md) values that influence the comparison.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0855-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d0855-108">Requirements</span></span>  
 <span data-ttu-id="d0855-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0855-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0855-110">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="d0855-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d0855-111">**NET Framework w wersji:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0855-111">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0855-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d0855-112">See also</span></span>

- [<span data-ttu-id="d0855-113">IAssemblyName, interfejs</span><span class="sxs-lookup"><span data-stu-id="d0855-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="d0855-114">Wyliczenia łączenia</span><span class="sxs-lookup"><span data-stu-id="d0855-114">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
