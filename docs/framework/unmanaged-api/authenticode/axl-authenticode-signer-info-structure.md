---
title: Struktura AXL_AUTHENTICODE_SIGNER_INFO
ms.date: 03/30/2017
ms.assetid: 81c0f8b4-ce35-4716-8651-b642d40648a2
ms.openlocfilehash: 00132bb378d69c0db9fe9d762407707346238917
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132511"
---
# <a name="axl_authenticode_signer_info-structure"></a><span data-ttu-id="91e57-102">Struktura AXL_AUTHENTICODE_SIGNER_INFO</span><span class="sxs-lookup"><span data-stu-id="91e57-102">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>
<span data-ttu-id="91e57-103">Definiuje informacje o podpisie Authenticode.</span><span class="sxs-lookup"><span data-stu-id="91e57-103">Defines the Authenticode signer information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91e57-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="91e57-104">Syntax</span></span>  
  
```cpp  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    LPCWSTR pwszHash  
    LPCWSTR pwszDescription;  
    LPCWSTR pwszDescriptionUrl;  
    PCCERT_CHAIN_CONTEXT pChainContext  
} AXL_AUTHENTICODE_SIGNER_INFO, * PAXL_AUTHENTICODE_SIGNER_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="91e57-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="91e57-105">Members</span></span>  
  
|<span data-ttu-id="91e57-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="91e57-106">Member</span></span>|<span data-ttu-id="91e57-107">Opis</span><span class="sxs-lookup"><span data-stu-id="91e57-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="91e57-108">Rozmiar tej struktury.</span><span class="sxs-lookup"><span data-stu-id="91e57-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="91e57-109">Kod błędu.</span><span class="sxs-lookup"><span data-stu-id="91e57-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="91e57-110">Algorytm wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="91e57-110">The hash algorithm.</span></span>|  
|`pwszHash`|<span data-ttu-id="91e57-111">Wartość skrótu.</span><span class="sxs-lookup"><span data-stu-id="91e57-111">The hash.</span></span>|  
|`pwszDescription`|<span data-ttu-id="91e57-112">Opis.</span><span class="sxs-lookup"><span data-stu-id="91e57-112">The description.</span></span>|  
|`pwszDescriptionUrl`|<span data-ttu-id="91e57-113">Adres URL opisu.</span><span class="sxs-lookup"><span data-stu-id="91e57-113">The URL of the description.</span></span>|  
|`pChainContext`|<span data-ttu-id="91e57-114">Kontekst łańcucha osoby podpisującej.</span><span class="sxs-lookup"><span data-stu-id="91e57-114">The chain context of the signer.</span></span> <span data-ttu-id="91e57-115">Zobacz strukturę [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) .</span><span class="sxs-lookup"><span data-stu-id="91e57-115">See the [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="91e57-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="91e57-116">See also</span></span>

- [<span data-ttu-id="91e57-117">Authenticode</span><span class="sxs-lookup"><span data-stu-id="91e57-117">Authenticode</span></span>](index.md)
