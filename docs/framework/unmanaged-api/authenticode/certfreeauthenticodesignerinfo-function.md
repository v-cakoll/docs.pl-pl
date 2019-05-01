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
ms.openlocfilehash: bdb764417b757cd7388c49d7e5cac9a960074820
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941631"
---
# <a name="certfreeauthenticodesignerinfo-function"></a><span data-ttu-id="83e1e-102">Funkcja CertFreeAuthenticodeSignerInfo</span><span class="sxs-lookup"><span data-stu-id="83e1e-102">CertFreeAuthenticodeSignerInfo Function</span></span>
<span data-ttu-id="83e1e-103">Zwalnia zasoby przydzielone [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="83e1e-103">Frees resources allocated for the [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83e1e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="83e1e-104">Syntax</span></span>  
  
```  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83e1e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="83e1e-105">Parameters</span></span>  
 `pSignerInfo`  
 <span data-ttu-id="83e1e-106">[out w] Osoby podpisującej informacji do wydania.</span><span class="sxs-lookup"><span data-stu-id="83e1e-106">[in, out] Signer information to be released.</span></span> <span data-ttu-id="83e1e-107">Zobacz [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="83e1e-107">See the [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="83e1e-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="83e1e-108">Return Value</span></span>  
 <span data-ttu-id="83e1e-109">`S_OK` Jeśli funkcja się powiedzie.</span><span class="sxs-lookup"><span data-stu-id="83e1e-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="83e1e-110">W przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="83e1e-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83e1e-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="83e1e-111">See also</span></span>

- [<span data-ttu-id="83e1e-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="83e1e-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
