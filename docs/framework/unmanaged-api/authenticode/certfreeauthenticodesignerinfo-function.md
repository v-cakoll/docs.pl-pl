---
title: Funkcja CertFreeAuthenticodeSignerInfo
ms.date: 03/30/2017
api_name:
- CertFreeAuthenticodeSignerInfo
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 8029633c-b6e4-4665-a7c2-89607c3247ef
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4282be8e57c965e14398a9284002b1191c5169fa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54708041"
---
# <a name="certfreeauthenticodesignerinfo-function"></a><span data-ttu-id="9abd7-102">Funkcja CertFreeAuthenticodeSignerInfo</span><span class="sxs-lookup"><span data-stu-id="9abd7-102">CertFreeAuthenticodeSignerInfo Function</span></span>
<span data-ttu-id="9abd7-103">Zwalnia zasoby przydzielone [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="9abd7-103">Frees resources allocated for the [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9abd7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9abd7-104">Syntax</span></span>  
  
```  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9abd7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9abd7-105">Parameters</span></span>  
 `pSignerInfo`  
 <span data-ttu-id="9abd7-106">[out w] Osoby podpisującej informacji do wydania.</span><span class="sxs-lookup"><span data-stu-id="9abd7-106">[in, out] Signer information to be released.</span></span> <span data-ttu-id="9abd7-107">Zobacz [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="9abd7-107">See the [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9abd7-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9abd7-108">Return Value</span></span>  
 <span data-ttu-id="9abd7-109">`S_OK` Jeśli funkcja się powiedzie.</span><span class="sxs-lookup"><span data-stu-id="9abd7-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="9abd7-110">W przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="9abd7-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9abd7-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9abd7-111">See also</span></span>
- [<span data-ttu-id="9abd7-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="9abd7-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
