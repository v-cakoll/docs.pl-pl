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
ms.openlocfilehash: 27c16cb5d85ddffc1646bee893c5644682812025
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560584"
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="1a9ba-102">Funkcja CertFreeAuthenticodeTimestamperInfo</span><span class="sxs-lookup"><span data-stu-id="1a9ba-102">CertFreeAuthenticodeTimestamperInfo Function</span></span>
<span data-ttu-id="1a9ba-103">Zwalnia zasoby przydzielone [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="1a9ba-103">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a9ba-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1a9ba-104">Syntax</span></span>  
  
```  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1a9ba-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1a9ba-105">Parameters</span></span>  
 `pTimestamperInfo`  
 <span data-ttu-id="1a9ba-106">[out w] Czas stamper informacje mogą być wprowadzane.</span><span class="sxs-lookup"><span data-stu-id="1a9ba-106">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="1a9ba-107">Zobacz [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="1a9ba-107">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1a9ba-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1a9ba-108">Return Value</span></span>  
 <span data-ttu-id="1a9ba-109">`S_OK` Jeśli funkcja się powiedzie.</span><span class="sxs-lookup"><span data-stu-id="1a9ba-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="1a9ba-110">W przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="1a9ba-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a9ba-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1a9ba-111">See also</span></span>
- [<span data-ttu-id="1a9ba-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="1a9ba-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
