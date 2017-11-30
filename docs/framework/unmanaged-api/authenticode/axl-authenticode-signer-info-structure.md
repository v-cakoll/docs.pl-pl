---
title: Struktura AXL_AUTHENTICODE_SIGNER_INFO
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 81c0f8b4-ce35-4716-8651-b642d40648a2
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c53ca8073adda5cba497e9f45404024435cc161f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="axlauthenticodesignerinfo-structure"></a><span data-ttu-id="8bb40-102">Struktura AXL_AUTHENTICODE_SIGNER_INFO</span><span class="sxs-lookup"><span data-stu-id="8bb40-102">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>
<span data-ttu-id="8bb40-103">Definiuje informacje podpisu Authenticode.</span><span class="sxs-lookup"><span data-stu-id="8bb40-103">Defines the Authenticode signer information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bb40-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8bb40-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="8bb40-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="8bb40-105">Members</span></span>  
  
|<span data-ttu-id="8bb40-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="8bb40-106">Member</span></span>|<span data-ttu-id="8bb40-107">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb40-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="8bb40-108">Rozmiar tej struktury.</span><span class="sxs-lookup"><span data-stu-id="8bb40-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="8bb40-109">Kod błędu.</span><span class="sxs-lookup"><span data-stu-id="8bb40-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="8bb40-110">Algorytm wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="8bb40-110">The hash algorithm.</span></span>|  
|`pwszHash`|<span data-ttu-id="8bb40-111">Wartość skrótu.</span><span class="sxs-lookup"><span data-stu-id="8bb40-111">The hash.</span></span>|  
|`pwszDescription`|<span data-ttu-id="8bb40-112">Opis.</span><span class="sxs-lookup"><span data-stu-id="8bb40-112">The description.</span></span>|  
|`pwszDescriptionUrl`|<span data-ttu-id="8bb40-113">Adres URL opisu.</span><span class="sxs-lookup"><span data-stu-id="8bb40-113">The URL of the description.</span></span>|  
|`pChainContext`|<span data-ttu-id="8bb40-114">Kontekst łańcuch osoby podpisującej.</span><span class="sxs-lookup"><span data-stu-id="8bb40-114">The chain context of the signer.</span></span> <span data-ttu-id="8bb40-115">Zobacz [CERT_CONTEXT](http://msdn.microsoft.com/library/windows/desktop/aa377189.aspx) struktury.</span><span class="sxs-lookup"><span data-stu-id="8bb40-115">See the [CERT_CONTEXT](http://msdn.microsoft.com/library/windows/desktop/aa377189.aspx) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8bb40-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb40-116">See Also</span></span>  
 [<span data-ttu-id="8bb40-117">Authenticode</span><span class="sxs-lookup"><span data-stu-id="8bb40-117">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
