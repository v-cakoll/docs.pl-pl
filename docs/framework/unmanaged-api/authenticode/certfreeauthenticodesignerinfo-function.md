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
ms.openlocfilehash: 84f15dc49d14e781f69d0f9da8f314eb71d8c034
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401619"
---
# <a name="certfreeauthenticodesignerinfo-function"></a><span data-ttu-id="c4147-102">Funkcja CertFreeAuthenticodeSignerInfo</span><span class="sxs-lookup"><span data-stu-id="c4147-102">CertFreeAuthenticodeSignerInfo Function</span></span>
<span data-ttu-id="c4147-103">Zwalnia zasoby przydzielone dla [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="c4147-103">Frees resources allocated for the [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4147-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c4147-104">Syntax</span></span>  
  
```  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c4147-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c4147-105">Parameters</span></span>  
 `pSignerInfo`  
 <span data-ttu-id="c4147-106">[w, out] Informacje o osobie podpisującej do zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="c4147-106">[in, out] Signer information to be released.</span></span> <span data-ttu-id="c4147-107">Zobacz [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="c4147-107">See the [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c4147-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c4147-108">Return Value</span></span>  
 <span data-ttu-id="c4147-109">`S_OK` Jeśli funkcja zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="c4147-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="c4147-110">W przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="c4147-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4147-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c4147-111">See Also</span></span>  
 [<span data-ttu-id="c4147-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="c4147-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
