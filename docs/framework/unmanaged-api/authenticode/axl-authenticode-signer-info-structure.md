---
title: Struktura AXL_AUTHENTICODE_SIGNER_INFO
ms.date: 03/30/2017
ms.assetid: 81c0f8b4-ce35-4716-8651-b642d40648a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b9f54c7c57d122ac1214b9f31cc4e1d1cddd71c
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44039189"
---
# <a name="axlauthenticodesignerinfo-structure"></a><span data-ttu-id="ac91b-102">Struktura AXL_AUTHENTICODE_SIGNER_INFO</span><span class="sxs-lookup"><span data-stu-id="ac91b-102">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>
<span data-ttu-id="ac91b-103">Definiuje informacje podpisu Authenticode.</span><span class="sxs-lookup"><span data-stu-id="ac91b-103">Defines the Authenticode signer information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac91b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ac91b-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="ac91b-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ac91b-105">Members</span></span>  
  
|<span data-ttu-id="ac91b-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="ac91b-106">Member</span></span>|<span data-ttu-id="ac91b-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ac91b-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="ac91b-108">Rozmiar tej struktury.</span><span class="sxs-lookup"><span data-stu-id="ac91b-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="ac91b-109">Kod błędu.</span><span class="sxs-lookup"><span data-stu-id="ac91b-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="ac91b-110">Algorytm wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="ac91b-110">The hash algorithm.</span></span>|  
|`pwszHash`|<span data-ttu-id="ac91b-111">Skrót.</span><span class="sxs-lookup"><span data-stu-id="ac91b-111">The hash.</span></span>|  
|`pwszDescription`|<span data-ttu-id="ac91b-112">Opis.</span><span class="sxs-lookup"><span data-stu-id="ac91b-112">The description.</span></span>|  
|`pwszDescriptionUrl`|<span data-ttu-id="ac91b-113">Adres URL opisu.</span><span class="sxs-lookup"><span data-stu-id="ac91b-113">The URL of the description.</span></span>|  
|`pChainContext`|<span data-ttu-id="ac91b-114">Kontekst łańcuch osoby podpisującej.</span><span class="sxs-lookup"><span data-stu-id="ac91b-114">The chain context of the signer.</span></span> <span data-ttu-id="ac91b-115">Zobacz [CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context) struktury.</span><span class="sxs-lookup"><span data-stu-id="ac91b-115">See the [CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ac91b-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ac91b-116">See Also</span></span>  
 [<span data-ttu-id="ac91b-117">Authenticode</span><span class="sxs-lookup"><span data-stu-id="ac91b-117">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
