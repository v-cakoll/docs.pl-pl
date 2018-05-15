---
title: Funkcja CertFreeAuthenticodeTimestamperInfo
ms.date: 03/30/2017
api_name:
- CertFreeAuthenticodeTimestamperInfo
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 3eb14c49-68c2-4516-ac89-e5bd7473831c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9c37a9af6a1532d03fa04ca151605cef7ab5244e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="595a0-102">Funkcja CertFreeAuthenticodeTimestamperInfo</span><span class="sxs-lookup"><span data-stu-id="595a0-102">CertFreeAuthenticodeTimestamperInfo Function</span></span>
<span data-ttu-id="595a0-103">Zwalnia zasoby przydzielone dla [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="595a0-103">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="595a0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="595a0-104">Syntax</span></span>  
  
```  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="595a0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="595a0-105">Parameters</span></span>  
 `pTimestamperInfo`  
 <span data-ttu-id="595a0-106">[w, out] Informacje o stamper czasu do zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="595a0-106">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="595a0-107">Zobacz [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="595a0-107">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="595a0-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="595a0-108">Return Value</span></span>  
 <span data-ttu-id="595a0-109">`S_OK` Jeśli funkcja zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="595a0-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="595a0-110">W przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="595a0-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="595a0-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="595a0-111">See Also</span></span>  
 [<span data-ttu-id="595a0-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="595a0-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
