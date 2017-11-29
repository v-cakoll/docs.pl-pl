---
title: "Authenticode (niezarządzana dokumentacja interfejsu API)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 7e8cc303-6e77-4116-aa8b-7ea297a3a467
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e90a13ebf46f1891061c78435b7ba47d68de001d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="authenticode-unmanaged-api-reference"></a><span data-ttu-id="e7382-102">Authenticode (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="e7382-102">Authenticode (Unmanaged API Reference)</span></span>
<span data-ttu-id="e7382-103">Obsługuje licencji Authenticode XrML modułu tworzenia i weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="e7382-103">Supports the Authenticode XrML license creation and verification module.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e7382-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="e7382-104">In This Section</span></span>  
 [<span data-ttu-id="e7382-105">Funkcja _AxlGetIssuerPublicKeyHash</span><span class="sxs-lookup"><span data-stu-id="e7382-105">_AxlGetIssuerPublicKeyHash Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axlgetissuerpublickeyhash-function.md)  
 <span data-ttu-id="e7382-106">Pobiera Skrót SHA-1 klucza publicznego skojarzonego z kluczem prywatnym, który jest używany do podpisywania określonego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="e7382-106">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
 [<span data-ttu-id="e7382-107">Funkcja _AxlPublicKeyBlobToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="e7382-107">_AxlPublicKeyBlobToPublicKeyToken Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axlpublickeyblobtopublickeytoken-function.md)  
 <span data-ttu-id="e7382-108">Oblicza silnej nazwy token klucza publicznego z formatu PUBLICKEYBLOB dostawcy usług Kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="e7382-108">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
 [<span data-ttu-id="e7382-109">Funkcja _AxlRSAKeyValueToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="e7382-109">_AxlRSAKeyValueToPublicKeyToken Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axlrsakeyvaluetopublickeytoken-function.md)  
 <span data-ttu-id="e7382-110">Konwertuje modulo i wykładnik silnej nazwy tokenu klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="e7382-110">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
 [<span data-ttu-id="e7382-111">Funkcja CertFreeAuthenticodeSignerInfo</span><span class="sxs-lookup"><span data-stu-id="e7382-111">CertFreeAuthenticodeSignerInfo Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodesignerinfo-function.md)  
 <span data-ttu-id="e7382-112">Zwalnia zasoby przydzielone dla struktura AXL_AUTHENTICODE_SIGNER_INFO.</span><span class="sxs-lookup"><span data-stu-id="e7382-112">Frees resources allocated for the AXL_AUTHENTICODE_SIGNER_INFO structure.</span></span>  
  
 [<span data-ttu-id="e7382-113">Funkcja CertFreeAuthenticodeTimestamperInfo</span><span class="sxs-lookup"><span data-stu-id="e7382-113">CertFreeAuthenticodeTimestamperInfo Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodetimestamperinfo-function.md)  
 <span data-ttu-id="e7382-114">Zwalnia zasoby przydzielone dla struktura AXL_AUTHENTICODE_TIMESTAMPER_INFO.</span><span class="sxs-lookup"><span data-stu-id="e7382-114">Frees resources allocated for the AXL_AUTHENTICODE_TIMESTAMPER_INFO structure.</span></span>  
  
 [<span data-ttu-id="e7382-115">Funkcja CertTimestampAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="e7382-115">CertTimestampAuthenticodeLicense Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/certtimestampauthenticodelicense-function.md)  
 <span data-ttu-id="e7382-116">Licencja Authenticode XrML utworzone przez CertCreateAuthenticodeLicense sygnatury czasowe.</span><span class="sxs-lookup"><span data-stu-id="e7382-116">Time stamps an Authenticode XrML license created by CertCreateAuthenticodeLicense.</span></span>  
  
 [<span data-ttu-id="e7382-117">Funkcja CertVerifyAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="e7382-117">CertVerifyAuthenticodeLicense Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/certverifyauthenticodelicense-function.md)  
 <span data-ttu-id="e7382-118">Sprawdza poprawność licencję Authenticode XrML.</span><span class="sxs-lookup"><span data-stu-id="e7382-118">Verifies the validity of an Authenticode XrML license.</span></span>  
  
 [<span data-ttu-id="e7382-119">Struktura AXL_AUTHENTICODE_SIGNER_INFO</span><span class="sxs-lookup"><span data-stu-id="e7382-119">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md)  
 <span data-ttu-id="e7382-120">Definiuje informacje podpisu Authenticode.</span><span class="sxs-lookup"><span data-stu-id="e7382-120">Defines the Authenticode signer information.</span></span>  
  
 [<span data-ttu-id="e7382-121">Struktura AXL_AUTHENTICODE_TIMESTAMPER_INFO</span><span class="sxs-lookup"><span data-stu-id="e7382-121">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md)  
 <span data-ttu-id="e7382-122">Definiuje informacje stamper czasu Authenticode.</span><span class="sxs-lookup"><span data-stu-id="e7382-122">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7382-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e7382-123">See Also</span></span>  
 [<span data-ttu-id="e7382-124">Niezarządzany wykaz interfejsów API</span><span class="sxs-lookup"><span data-stu-id="e7382-124">Unmanaged API Reference</span></span>](../../../../docs/framework/unmanaged-api/index.md)
