---
title: Struktura AXL_AUTHENTICODE_TIMESTAMPER_INFO
ms.date: 03/30/2017
ms.assetid: 89e41a81-0f41-45ad-8f20-a120e4ff24fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae7879e1f6598108d839287792ed441391764ae2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776647"
---
# <a name="axl_authenticode_timestamper_info-structure"></a><span data-ttu-id="af7bf-102">Struktura AXL_AUTHENTICODE_TIMESTAMPER_INFO</span><span class="sxs-lookup"><span data-stu-id="af7bf-102">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>
<span data-ttu-id="af7bf-103">Definiuje informacje o sygnaturze czasowym Authenticode.</span><span class="sxs-lookup"><span data-stu-id="af7bf-103">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af7bf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="af7bf-104">Syntax</span></span>  
  
```cpp  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    FILETIME ftTimestamp  
    PCCERT_CHAIN_CONTEXT pChainContext;  
} AXL_AUTHENTICODE_TIMESTAMPER_INFO, * PAXL_AUTHENTICODE_TIMESTAMPER_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="af7bf-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="af7bf-105">Members</span></span>  
  
|<span data-ttu-id="af7bf-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="af7bf-106">Member</span></span>|<span data-ttu-id="af7bf-107">Opis</span><span class="sxs-lookup"><span data-stu-id="af7bf-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="af7bf-108">Rozmiar tej struktury.</span><span class="sxs-lookup"><span data-stu-id="af7bf-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="af7bf-109">Kod błędu.</span><span class="sxs-lookup"><span data-stu-id="af7bf-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="af7bf-110">Algorytm wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="af7bf-110">The hash algorithm.</span></span>|  
|`ftTimestamp`|<span data-ttu-id="af7bf-111">Godzina sygnatury czasowej.</span><span class="sxs-lookup"><span data-stu-id="af7bf-111">The time of the time stamp.</span></span>|  
|`pChainContext`|<span data-ttu-id="af7bf-112">Kontekst łańcucha sygnatury czasowej.</span><span class="sxs-lookup"><span data-stu-id="af7bf-112">The time stamper’s chain context.</span></span>  <span data-ttu-id="af7bf-113">Zobacz strukturę [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) .</span><span class="sxs-lookup"><span data-stu-id="af7bf-113">See the [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="af7bf-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="af7bf-114">See also</span></span>

- [<span data-ttu-id="af7bf-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="af7bf-115">Authenticode</span></span>](index.md)
