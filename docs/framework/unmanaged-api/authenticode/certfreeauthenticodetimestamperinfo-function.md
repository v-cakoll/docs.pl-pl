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
ms.openlocfilehash: a8ecada29528b065ddad0abc80a850ee0f347f6b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786995"
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="55f82-102">Funkcja CertFreeAuthenticodeTimestamperInfo</span><span class="sxs-lookup"><span data-stu-id="55f82-102">CertFreeAuthenticodeTimestamperInfo Function</span></span>
<span data-ttu-id="55f82-103">Zwalnia zasoby przydzieloną dla struktury [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="55f82-103">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55f82-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="55f82-104">Syntax</span></span>  
  
```cpp  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="55f82-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="55f82-105">Parameters</span></span>  
 `pTimestamperInfo`  
 <span data-ttu-id="55f82-106">[in. out] Informacje o sygnaturze czasowej do zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="55f82-106">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="55f82-107">Zobacz strukturę [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="55f82-107">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="55f82-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="55f82-108">Return Value</span></span>  
 <span data-ttu-id="55f82-109">`S_OK`Jeśli funkcja się powiedzie.</span><span class="sxs-lookup"><span data-stu-id="55f82-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="55f82-110">W przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="55f82-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55f82-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="55f82-111">See also</span></span>

- [<span data-ttu-id="55f82-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="55f82-112">Authenticode</span></span>](index.md)
