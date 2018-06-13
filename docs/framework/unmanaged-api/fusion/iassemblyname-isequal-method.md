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
ms.openlocfilehash: 043394541f5ed91b85a57f4cb13c61cca442bfec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431844"
---
# <a name="iassemblynameisequal-method"></a><span data-ttu-id="f6c8d-102">IAssemblyName::IsEqual — Metoda</span><span class="sxs-lookup"><span data-stu-id="f6c8d-102">IAssemblyName::IsEqual Method</span></span>
<span data-ttu-id="f6c8d-103">Określa, czy określonej [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) obiekt jest taki sam `IAssemblyName`zgodnie flagi porównania określony.</span><span class="sxs-lookup"><span data-stu-id="f6c8d-103">Determines whether a specified [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6c8d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f6c8d-104">Syntax</span></span>  
  
```  
HRESULT IsEqual (  
    [in] IAssemblyName  *pName,  
    [in] DWORD          dwCmpFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f6c8d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6c8d-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="f6c8d-106">[in] `IAssemblyName` Obiektu, do którego należy to porównać `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="f6c8d-106">[in] The `IAssemblyName` object to which to compare this `IAssemblyName`.</span></span>  
  
 `dwCmpFlags`  
 <span data-ttu-id="f6c8d-107">[in] Bitowe połączenie [ASM_CMP_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cmp-flags-enumeration.md) wartości, które wpływają porównania.</span><span class="sxs-lookup"><span data-stu-id="f6c8d-107">[in] A bitwise combination of [ASM_CMP_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cmp-flags-enumeration.md) values that influence the comparison.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6c8d-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f6c8d-108">Requirements</span></span>  
 <span data-ttu-id="f6c8d-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6c8d-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6c8d-110">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="f6c8d-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f6c8d-111">**NET Framework w wersji:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6c8d-111">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6c8d-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f6c8d-112">See Also</span></span>  
 [<span data-ttu-id="f6c8d-113">IAssemblyName, interfejs</span><span class="sxs-lookup"><span data-stu-id="f6c8d-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="f6c8d-114">Wyliczenia łączenia</span><span class="sxs-lookup"><span data-stu-id="f6c8d-114">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
