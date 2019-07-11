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
ms.openlocfilehash: 680d9c959c57620ff38f8e785c670b451e5805b0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741233"
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="75f35-102">Funkcja CertFreeAuthenticodeTimestamperInfo</span><span class="sxs-lookup"><span data-stu-id="75f35-102">CertFreeAuthenticodeTimestamperInfo Function</span></span>
<span data-ttu-id="75f35-103">Zwalnia zasoby przydzielone [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="75f35-103">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75f35-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="75f35-104">Syntax</span></span>  
  
```cpp  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75f35-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="75f35-105">Parameters</span></span>  
 `pTimestamperInfo`  
 <span data-ttu-id="75f35-106">[out w] Czas stamper informacje mogą być wprowadzane.</span><span class="sxs-lookup"><span data-stu-id="75f35-106">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="75f35-107">Zobacz [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="75f35-107">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="75f35-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="75f35-108">Return Value</span></span>  
 <span data-ttu-id="75f35-109">`S_OK` Jeśli funkcja się powiedzie.</span><span class="sxs-lookup"><span data-stu-id="75f35-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="75f35-110">W przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="75f35-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75f35-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="75f35-111">See also</span></span>

- [<span data-ttu-id="75f35-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="75f35-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
