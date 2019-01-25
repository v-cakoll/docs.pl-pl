---
title: Authenticode (niezarządzana dokumentacja interfejsu API)
ms.date: 03/30/2017
ms.assetid: 7e8cc303-6e77-4116-aa8b-7ea297a3a467
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ee0aca905c488bc3d285d69e431e79740bf8b7b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54623771"
---
# <a name="authenticode-unmanaged-api-reference"></a><span data-ttu-id="45367-102">Authenticode (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="45367-102">Authenticode (Unmanaged API Reference)</span></span>
<span data-ttu-id="45367-103">Obsługuje moduł tworzenia i weryfikacji licencji Authenticode XrML.</span><span class="sxs-lookup"><span data-stu-id="45367-103">Supports the Authenticode XrML license creation and verification module.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="45367-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="45367-104">In This Section</span></span>  
 [<span data-ttu-id="45367-105">Funkcja _AxlGetIssuerPublicKeyHash</span><span class="sxs-lookup"><span data-stu-id="45367-105">_AxlGetIssuerPublicKeyHash Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axlgetissuerpublickeyhash-function.md)  
 <span data-ttu-id="45367-106">Pobiera Skrót SHA-1 klucza publicznego skojarzonego z kluczem prywatnym, który jest używany do podpisywania określonego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="45367-106">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
 [<span data-ttu-id="45367-107">Funkcja _AxlPublicKeyBlobToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="45367-107">_AxlPublicKeyBlobToPublicKeyToken Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axlpublickeyblobtopublickeytoken-function.md)  
 <span data-ttu-id="45367-108">Oblicza silnej nazwy token klucza publicznego z formatu publickeyblob — dostawcy usług Kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="45367-108">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
 [<span data-ttu-id="45367-109">Funkcja _AxlRSAKeyValueToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="45367-109">_AxlRSAKeyValueToPublicKeyToken Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axlrsakeyvaluetopublickeytoken-function.md)  
 <span data-ttu-id="45367-110">Konwertuje wyznaczanie modułu i wykładnik silnej nazwy token klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="45367-110">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
 [<span data-ttu-id="45367-111">Funkcja CertFreeAuthenticodeSignerInfo</span><span class="sxs-lookup"><span data-stu-id="45367-111">CertFreeAuthenticodeSignerInfo Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodesignerinfo-function.md)  
 <span data-ttu-id="45367-112">Zwalnia zasoby przydzielone do struktura AXL_AUTHENTICODE_SIGNER_INFO.</span><span class="sxs-lookup"><span data-stu-id="45367-112">Frees resources allocated for the AXL_AUTHENTICODE_SIGNER_INFO structure.</span></span>  
  
 [<span data-ttu-id="45367-113">Funkcja CertFreeAuthenticodeTimestamperInfo</span><span class="sxs-lookup"><span data-stu-id="45367-113">CertFreeAuthenticodeTimestamperInfo Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodetimestamperinfo-function.md)  
 <span data-ttu-id="45367-114">Zwalnia zasoby przydzielone do struktura AXL_AUTHENTICODE_TIMESTAMPER_INFO.</span><span class="sxs-lookup"><span data-stu-id="45367-114">Frees resources allocated for the AXL_AUTHENTICODE_TIMESTAMPER_INFO structure.</span></span>  
  
 [<span data-ttu-id="45367-115">Funkcja CertTimestampAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="45367-115">CertTimestampAuthenticodeLicense Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/certtimestampauthenticodelicense-function.md)  
 <span data-ttu-id="45367-116">Licencja Authenticode XrML utworzone przez CertCreateAuthenticodeLicense sygnatury czasowe.</span><span class="sxs-lookup"><span data-stu-id="45367-116">Time stamps an Authenticode XrML license created by CertCreateAuthenticodeLicense.</span></span>  
  
 [<span data-ttu-id="45367-117">Funkcja CertVerifyAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="45367-117">CertVerifyAuthenticodeLicense Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/certverifyauthenticodelicense-function.md)  
 <span data-ttu-id="45367-118">Sprawdza poprawność licencję Authenticode XrML.</span><span class="sxs-lookup"><span data-stu-id="45367-118">Verifies the validity of an Authenticode XrML license.</span></span>  
  
 [<span data-ttu-id="45367-119">Struktura AXL_AUTHENTICODE_SIGNER_INFO</span><span class="sxs-lookup"><span data-stu-id="45367-119">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md)  
 <span data-ttu-id="45367-120">Definiuje informacje podpisu Authenticode.</span><span class="sxs-lookup"><span data-stu-id="45367-120">Defines the Authenticode signer information.</span></span>  
  
 [<span data-ttu-id="45367-121">Struktura AXL_AUTHENTICODE_TIMESTAMPER_INFO</span><span class="sxs-lookup"><span data-stu-id="45367-121">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md)  
 <span data-ttu-id="45367-122">Definiuje informacje stamper czasu Authenticode.</span><span class="sxs-lookup"><span data-stu-id="45367-122">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45367-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="45367-123">See also</span></span>
- [<span data-ttu-id="45367-124">Niezarządzane interfejsy API — informacje</span><span class="sxs-lookup"><span data-stu-id="45367-124">Unmanaged API Reference</span></span>](../../../../docs/framework/unmanaged-api/index.md)
