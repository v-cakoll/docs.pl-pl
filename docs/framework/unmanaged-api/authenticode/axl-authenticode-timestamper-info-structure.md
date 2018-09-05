---
title: Struktura AXL_AUTHENTICODE_TIMESTAMPER_INFO
ms.date: 03/30/2017
ms.assetid: 89e41a81-0f41-45ad-8f20-a120e4ff24fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d7f4fff4f2c2b3dd04625f4cf50b8b19a0ef6f39
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43525084"
---
# <a name="axlauthenticodetimestamperinfo-structure"></a><span data-ttu-id="d90a8-102">Struktura AXL_AUTHENTICODE_TIMESTAMPER_INFO</span><span class="sxs-lookup"><span data-stu-id="d90a8-102">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>
<span data-ttu-id="d90a8-103">Definiuje informacje stamper czasu Authenticode.</span><span class="sxs-lookup"><span data-stu-id="d90a8-103">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d90a8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d90a8-104">Syntax</span></span>  
  
```  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    FILETIME ftTimestamp  
    PCCERT_CHAIN_CONTEXT pChainContext;  
} AXL_AUTHENTICODE_TIMESTAMPER_INFO, * PAXL_AUTHENTICODE_TIMESTAMPER_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="d90a8-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="d90a8-105">Members</span></span>  
  
|<span data-ttu-id="d90a8-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="d90a8-106">Member</span></span>|<span data-ttu-id="d90a8-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d90a8-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="d90a8-108">Rozmiar tej struktury.</span><span class="sxs-lookup"><span data-stu-id="d90a8-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="d90a8-109">Kod błędu.</span><span class="sxs-lookup"><span data-stu-id="d90a8-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="d90a8-110">Algorytm wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="d90a8-110">The hash algorithm.</span></span>|  
|`ftTimestamp`|<span data-ttu-id="d90a8-111">Czas sygnaturę czasową.</span><span class="sxs-lookup"><span data-stu-id="d90a8-111">The time of the time stamp.</span></span>|  
|`pChainContext`|<span data-ttu-id="d90a8-112">Kontekst łańcucha stamper czasu.</span><span class="sxs-lookup"><span data-stu-id="d90a8-112">The time stamper’s chain context.</span></span>  <span data-ttu-id="d90a8-113">Zobacz [CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context) struktury.</span><span class="sxs-lookup"><span data-stu-id="d90a8-113">See the [CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d90a8-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d90a8-114">See Also</span></span>  
 [<span data-ttu-id="d90a8-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="d90a8-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
