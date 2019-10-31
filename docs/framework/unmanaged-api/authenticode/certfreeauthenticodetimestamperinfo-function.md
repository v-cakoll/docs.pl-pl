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
ms.openlocfilehash: 4f0806e0273b111e3398fb8f2884231b96cf1116
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099770"
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="ae3f8-102">Funkcja CertFreeAuthenticodeTimestamperInfo</span><span class="sxs-lookup"><span data-stu-id="ae3f8-102">CertFreeAuthenticodeTimestamperInfo Function</span></span>
<span data-ttu-id="ae3f8-103">Zwalnia zasoby przydzieloną dla struktury [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="ae3f8-103">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae3f8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ae3f8-104">Syntax</span></span>  
  
```cpp  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae3f8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ae3f8-105">Parameters</span></span>  
 `pTimestamperInfo`  
 <span data-ttu-id="ae3f8-106">[in. out] Informacje o sygnaturze czasowej do zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="ae3f8-106">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="ae3f8-107">Zobacz strukturę [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="ae3f8-107">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ae3f8-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ae3f8-108">Return Value</span></span>  
 <span data-ttu-id="ae3f8-109">`S_OK`, jeśli funkcja się powiedzie.</span><span class="sxs-lookup"><span data-stu-id="ae3f8-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="ae3f8-110">W przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="ae3f8-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae3f8-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ae3f8-111">See also</span></span>

- [<span data-ttu-id="ae3f8-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="ae3f8-112">Authenticode</span></span>](index.md)
