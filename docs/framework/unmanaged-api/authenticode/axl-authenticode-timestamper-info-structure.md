---
title: Struktura AXL_AUTHENTICODE_TIMESTAMPER_INFO
ms.date: 03/30/2017
ms.assetid: 89e41a81-0f41-45ad-8f20-a120e4ff24fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c89845008307e4cfb00d0f9b9a168a43ba5378c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402366"
---
# <a name="axlauthenticodetimestamperinfo-structure"></a><span data-ttu-id="88773-102">Struktura AXL_AUTHENTICODE_TIMESTAMPER_INFO</span><span class="sxs-lookup"><span data-stu-id="88773-102">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>
<span data-ttu-id="88773-103">Definiuje informacje stamper czasu Authenticode.</span><span class="sxs-lookup"><span data-stu-id="88773-103">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88773-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="88773-104">Syntax</span></span>  
  
```  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    FILETIME ftTimestamp  
    PCCERT_CHAIN_CONTEXT pChainContext;  
} AXL_AUTHENTICODE_TIMESTAMPER_INFO, * PAXL_AUTHENTICODE_TIMESTAMPER_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="88773-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="88773-105">Members</span></span>  
  
|<span data-ttu-id="88773-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="88773-106">Member</span></span>|<span data-ttu-id="88773-107">Opis</span><span class="sxs-lookup"><span data-stu-id="88773-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="88773-108">Rozmiar tej struktury.</span><span class="sxs-lookup"><span data-stu-id="88773-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="88773-109">Kod błędu.</span><span class="sxs-lookup"><span data-stu-id="88773-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="88773-110">Algorytm wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="88773-110">The hash algorithm.</span></span>|  
|`ftTimestamp`|<span data-ttu-id="88773-111">Czas sygnaturę czasową.</span><span class="sxs-lookup"><span data-stu-id="88773-111">The time of the time stamp.</span></span>|  
|`pChainContext`|<span data-ttu-id="88773-112">Kontekst łańcucha stamper czasu.</span><span class="sxs-lookup"><span data-stu-id="88773-112">The time stamper’s chain context.</span></span>  <span data-ttu-id="88773-113">Zobacz [CERT_CONTEXT](http://msdn.microsoft.com/library/windows/desktop/aa377189.aspx) struktury.</span><span class="sxs-lookup"><span data-stu-id="88773-113">See the [CERT_CONTEXT](http://msdn.microsoft.com/library/windows/desktop/aa377189.aspx) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="88773-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="88773-114">See Also</span></span>  
 [<span data-ttu-id="88773-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="88773-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
