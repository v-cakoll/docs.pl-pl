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
ms.openlocfilehash: 357a2ca0ffc733adb14a21624cbe28fb754c8240
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776729"
---
# <a name="certfreeauthenticodesignerinfo-function"></a><span data-ttu-id="f277f-102">Funkcja CertFreeAuthenticodeSignerInfo</span><span class="sxs-lookup"><span data-stu-id="f277f-102">CertFreeAuthenticodeSignerInfo Function</span></span>
<span data-ttu-id="f277f-103">Zwalnia zasoby przydzieloną dla struktury [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="f277f-103">Frees resources allocated for the [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f277f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f277f-104">Syntax</span></span>  
  
```cpp  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f277f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f277f-105">Parameters</span></span>  
 `pSignerInfo`  
 <span data-ttu-id="f277f-106">[in. out] Informacje o logowaniu do zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="f277f-106">[in, out] Signer information to be released.</span></span> <span data-ttu-id="f277f-107">Zobacz strukturę [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="f277f-107">See the [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f277f-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f277f-108">Return Value</span></span>  
 <span data-ttu-id="f277f-109">`S_OK`Jeśli funkcja się powiedzie.</span><span class="sxs-lookup"><span data-stu-id="f277f-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="f277f-110">W przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="f277f-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f277f-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f277f-111">See also</span></span>

- [<span data-ttu-id="f277f-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="f277f-112">Authenticode</span></span>](index.md)
