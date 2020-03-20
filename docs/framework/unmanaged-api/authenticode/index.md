---
title: Authenticode (niezarządzana dokumentacja interfejsu API)
ms.date: 03/30/2017
ms.assetid: 7e8cc303-6e77-4116-aa8b-7ea297a3a467
ms.openlocfilehash: 1b8b2222950c75f7f9d2ec2704f722087645cd7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73132458"
---
# <a name="authenticode-unmanaged-api-reference"></a><span data-ttu-id="548b3-102">Authenticode (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="548b3-102">Authenticode (Unmanaged API Reference)</span></span>
<span data-ttu-id="548b3-103">Obsługuje moduł tworzenia i weryfikacji licencji Authenticode XrML.</span><span class="sxs-lookup"><span data-stu-id="548b3-103">Supports the Authenticode XrML license creation and verification module.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="548b3-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="548b3-104">In This Section</span></span>  
 [<span data-ttu-id="548b3-105">Funkcja _AxlGetIssuerPublicKeyHash</span><span class="sxs-lookup"><span data-stu-id="548b3-105">_AxlGetIssuerPublicKeyHash Function</span></span>](axlgetissuerpublickeyhash-function.md)  
 <span data-ttu-id="548b3-106">Pobiera skrót SHA-1 klucza publicznego skojarzonego z kluczem prywatnym używanym do podpisywania określonego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="548b3-106">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
 [<span data-ttu-id="548b3-107">Funkcja _AxlPublicKeyBlobToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="548b3-107">_AxlPublicKeyBlobToPublicKeyToken Function</span></span>](axlpublickeyblobtopublickeytoken-function.md)  
 <span data-ttu-id="548b3-108">Oblicza token klucza publicznego silnej nazwy z formatu CSP PUBLICKEYBLOB.</span><span class="sxs-lookup"><span data-stu-id="548b3-108">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
 [<span data-ttu-id="548b3-109">Funkcja _AxlRSAKeyValueToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="548b3-109">_AxlRSAKeyValueToPublicKeyToken Function</span></span>](axlrsakeyvaluetopublickeytoken-function.md)  
 <span data-ttu-id="548b3-110">Konwertuje moduł i wykładnik na token klucza publicznego silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="548b3-110">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
 [<span data-ttu-id="548b3-111">Funkcja CertFreeAuthenticodeSignerInfo</span><span class="sxs-lookup"><span data-stu-id="548b3-111">CertFreeAuthenticodeSignerInfo Function</span></span>](certfreeauthenticodesignerinfo-function.md)  
 <span data-ttu-id="548b3-112">Zwalnia zasoby przydzielone dla struktury AXL_AUTHENTICODE_SIGNER_INFO.</span><span class="sxs-lookup"><span data-stu-id="548b3-112">Frees resources allocated for the AXL_AUTHENTICODE_SIGNER_INFO structure.</span></span>  
  
 [<span data-ttu-id="548b3-113">Funkcja CertFreeAuthenticodeTimestamperInfo</span><span class="sxs-lookup"><span data-stu-id="548b3-113">CertFreeAuthenticodeTimestamperInfo Function</span></span>](certfreeauthenticodetimestamperinfo-function.md)  
 <span data-ttu-id="548b3-114">Zwalnia zasoby przydzielone dla struktury AXL_AUTHENTICODE_TIMESTAMPER_INFO.</span><span class="sxs-lookup"><span data-stu-id="548b3-114">Frees resources allocated for the AXL_AUTHENTICODE_TIMESTAMPER_INFO structure.</span></span>  
  
 [<span data-ttu-id="548b3-115">Funkcja CertTimestampAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="548b3-115">CertTimestampAuthenticodeLicense Function</span></span>](certtimestampauthenticodelicense-function.md)  
 <span data-ttu-id="548b3-116">Sygnalizuje licencję Authenticode XrML utworzoną przez CertCreateAuthenticodeLicense.</span><span class="sxs-lookup"><span data-stu-id="548b3-116">Time stamps an Authenticode XrML license created by CertCreateAuthenticodeLicense.</span></span>  
  
 [<span data-ttu-id="548b3-117">Funkcja CertVerifyAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="548b3-117">CertVerifyAuthenticodeLicense Function</span></span>](certverifyauthenticodelicense-function.md)  
 <span data-ttu-id="548b3-118">Weryfikuje ważność licencji Authenticode XrML.</span><span class="sxs-lookup"><span data-stu-id="548b3-118">Verifies the validity of an Authenticode XrML license.</span></span>  
  
 [<span data-ttu-id="548b3-119">Struktura AXL_AUTHENTICODE_SIGNER_INFO</span><span class="sxs-lookup"><span data-stu-id="548b3-119">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>](axl-authenticode-signer-info-structure.md)  
 <span data-ttu-id="548b3-120">Definiuje informacje o sygnatariuszu Authenticode.</span><span class="sxs-lookup"><span data-stu-id="548b3-120">Defines the Authenticode signer information.</span></span>  
  
 [<span data-ttu-id="548b3-121">Struktura AXL_AUTHENTICODE_TIMESTAMPER_INFO</span><span class="sxs-lookup"><span data-stu-id="548b3-121">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>](axl-authenticode-timestamper-info-structure.md)  
 <span data-ttu-id="548b3-122">Definiuje informacje o znaczniku czasu Authenticode.</span><span class="sxs-lookup"><span data-stu-id="548b3-122">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="548b3-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="548b3-123">See also</span></span>

- [<span data-ttu-id="548b3-124">Niezarządzany wykaz interfejsów API</span><span class="sxs-lookup"><span data-stu-id="548b3-124">Unmanaged API Reference</span></span>](../index.md)
