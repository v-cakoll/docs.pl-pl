---
title: Struktura AXL_AUTHENTICODE_TIMESTAMPER_INFO
ms.date: 03/30/2017
ms.assetid: 89e41a81-0f41-45ad-8f20-a120e4ff24fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d7f4fff4f2c2b3dd04625f4cf50b8b19a0ef6f39
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2018
ms.locfileid: "43254662"
---
# <a name="axlauthenticodetimestamperinfo-structure"></a><span data-ttu-id="d3a56-102">Struktura AXL_AUTHENTICODE_TIMESTAMPER_INFO</span><span class="sxs-lookup"><span data-stu-id="d3a56-102">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>
<span data-ttu-id="d3a56-103">Definiuje informacje stamper czasu Authenticode.</span><span class="sxs-lookup"><span data-stu-id="d3a56-103">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3a56-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d3a56-104">Syntax</span></span>  
  
```  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    FILETIME ftTimestamp  
    PCCERT_CHAIN_CONTEXT pChainContext;  
} AXL_AUTHENTICODE_TIMESTAMPER_INFO, * PAXL_AUTHENTICODE_TIMESTAMPER_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="d3a56-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="d3a56-105">Members</span></span>  
  
|<span data-ttu-id="d3a56-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="d3a56-106">Member</span></span>|<span data-ttu-id="d3a56-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d3a56-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="d3a56-108">Rozmiar tej struktury.</span><span class="sxs-lookup"><span data-stu-id="d3a56-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="d3a56-109">Kod błędu.</span><span class="sxs-lookup"><span data-stu-id="d3a56-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="d3a56-110">Algorytm wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="d3a56-110">The hash algorithm.</span></span>|  
|`ftTimestamp`|<span data-ttu-id="d3a56-111">Czas sygnaturę czasową.</span><span class="sxs-lookup"><span data-stu-id="d3a56-111">The time of the time stamp.</span></span>|  
|`pChainContext`|<span data-ttu-id="d3a56-112">Kontekst łańcucha stamper czasu.</span><span class="sxs-lookup"><span data-stu-id="d3a56-112">The time stamper’s chain context.</span></span>  <span data-ttu-id="d3a56-113">Zobacz [CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context) struktury.</span><span class="sxs-lookup"><span data-stu-id="d3a56-113">See the [CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d3a56-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d3a56-114">See Also</span></span>  
 [<span data-ttu-id="d3a56-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="d3a56-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
