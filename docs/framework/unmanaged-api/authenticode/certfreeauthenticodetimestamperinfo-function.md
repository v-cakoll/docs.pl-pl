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
ms.openlocfilehash: 082ed24eb65de12f337ab4a379b088da0f6eea5a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497382"
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="1806f-102">Funkcja CertFreeAuthenticodeTimestamperInfo</span><span class="sxs-lookup"><span data-stu-id="1806f-102">CertFreeAuthenticodeTimestamperInfo Function</span></span>
<span data-ttu-id="1806f-103">Zwalnia zasoby przydzielone [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="1806f-103">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1806f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1806f-104">Syntax</span></span>  
  
```  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1806f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1806f-105">Parameters</span></span>  
 `pTimestamperInfo`  
 <span data-ttu-id="1806f-106">[out w] Czas stamper informacje mogą być wprowadzane.</span><span class="sxs-lookup"><span data-stu-id="1806f-106">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="1806f-107">Zobacz [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="1806f-107">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1806f-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1806f-108">Return Value</span></span>  
 <span data-ttu-id="1806f-109">`S_OK` Jeśli funkcja się powiedzie.</span><span class="sxs-lookup"><span data-stu-id="1806f-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="1806f-110">W przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="1806f-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1806f-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1806f-111">See also</span></span>
- [<span data-ttu-id="1806f-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="1806f-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
