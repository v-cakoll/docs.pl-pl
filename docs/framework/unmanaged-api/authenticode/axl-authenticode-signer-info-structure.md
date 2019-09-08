---
title: Struktura AXL_AUTHENTICODE_SIGNER_INFO
ms.date: 03/30/2017
ms.assetid: 81c0f8b4-ce35-4716-8651-b642d40648a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9aaa0258b53b6b39874c8c99c71ecf53cbdb8f97
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787079"
---
# <a name="axl_authenticode_signer_info-structure"></a><span data-ttu-id="2da36-102">Struktura AXL_AUTHENTICODE_SIGNER_INFO</span><span class="sxs-lookup"><span data-stu-id="2da36-102">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>
<span data-ttu-id="2da36-103">Definiuje informacje o podpisie Authenticode.</span><span class="sxs-lookup"><span data-stu-id="2da36-103">Defines the Authenticode signer information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2da36-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2da36-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="2da36-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="2da36-105">Members</span></span>  
  
|<span data-ttu-id="2da36-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="2da36-106">Member</span></span>|<span data-ttu-id="2da36-107">Opis</span><span class="sxs-lookup"><span data-stu-id="2da36-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="2da36-108">Rozmiar tej struktury.</span><span class="sxs-lookup"><span data-stu-id="2da36-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="2da36-109">Kod błędu.</span><span class="sxs-lookup"><span data-stu-id="2da36-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="2da36-110">Algorytm wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="2da36-110">The hash algorithm.</span></span>|  
|`pwszHash`|<span data-ttu-id="2da36-111">Wartość skrótu.</span><span class="sxs-lookup"><span data-stu-id="2da36-111">The hash.</span></span>|  
|`pwszDescription`|<span data-ttu-id="2da36-112">Opis.</span><span class="sxs-lookup"><span data-stu-id="2da36-112">The description.</span></span>|  
|`pwszDescriptionUrl`|<span data-ttu-id="2da36-113">Adres URL opisu.</span><span class="sxs-lookup"><span data-stu-id="2da36-113">The URL of the description.</span></span>|  
|`pChainContext`|<span data-ttu-id="2da36-114">Kontekst łańcucha osoby podpisującej.</span><span class="sxs-lookup"><span data-stu-id="2da36-114">The chain context of the signer.</span></span> <span data-ttu-id="2da36-115">Zobacz strukturę [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) .</span><span class="sxs-lookup"><span data-stu-id="2da36-115">See the [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2da36-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2da36-116">See also</span></span>

- [<span data-ttu-id="2da36-117">Authenticode</span><span class="sxs-lookup"><span data-stu-id="2da36-117">Authenticode</span></span>](index.md)
