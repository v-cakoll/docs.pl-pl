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
ms.openlocfilehash: 42f5685a9a976be7a3a73badf286f77216e43106
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741244"
---
# <a name="certfreeauthenticodesignerinfo-function"></a><span data-ttu-id="2b55e-102">Funkcja CertFreeAuthenticodeSignerInfo</span><span class="sxs-lookup"><span data-stu-id="2b55e-102">CertFreeAuthenticodeSignerInfo Function</span></span>
<span data-ttu-id="2b55e-103">Zwalnia zasoby przydzielone [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="2b55e-103">Frees resources allocated for the [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b55e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2b55e-104">Syntax</span></span>  
  
```cpp  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b55e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2b55e-105">Parameters</span></span>  
 `pSignerInfo`  
 <span data-ttu-id="2b55e-106">[out w] Osoby podpisującej informacji do wydania.</span><span class="sxs-lookup"><span data-stu-id="2b55e-106">[in, out] Signer information to be released.</span></span> <span data-ttu-id="2b55e-107">Zobacz [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="2b55e-107">See the [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2b55e-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2b55e-108">Return Value</span></span>  
 <span data-ttu-id="2b55e-109">`S_OK` Jeśli funkcja się powiedzie.</span><span class="sxs-lookup"><span data-stu-id="2b55e-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="2b55e-110">W przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="2b55e-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b55e-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2b55e-111">See also</span></span>

- [<span data-ttu-id="2b55e-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="2b55e-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
