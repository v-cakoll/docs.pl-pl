---
title: Funkcja CertVerifyAuthenticodeLicense
ms.date: 03/30/2017
api_name:
- CertVerifyAuthenticodeLicense
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 00118de7-33c6-41c4-8e1f-5d5e35e0da83
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c10d5f363d454a64f9052315514e896f90f7081
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44208851"
---
# <a name="certverifyauthenticodelicense-function"></a><span data-ttu-id="53d87-102">Funkcja CertVerifyAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="53d87-102">CertVerifyAuthenticodeLicense Function</span></span>
<span data-ttu-id="53d87-103">Sprawdza poprawność licencję Authenticode XrML.</span><span class="sxs-lookup"><span data-stu-id="53d87-103">Verifies the validity of an Authenticode XrML license.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53d87-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="53d87-104">Syntax</span></span>  
  
```  
HRESULT CertVerifyAuthenticodeLicense (  
    [in]   PCRYPT_DATA_BLOB                   pLicenseBlob,  
    [in]   OPTIONAL DWORD                     dwFlags,  
    [out]  PAXL_AUTHENTICODE_SIGNER_INFO      pSignerInfo,  
    [out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO pTimestamperInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="53d87-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="53d87-105">Parameters</span></span>  
 `pLicenseBlob`  
 <span data-ttu-id="53d87-106">[in] Licencja Authenticode XrML do weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="53d87-106">[in] The Authenticode XrML license to be verified.</span></span>  
  
 <span data-ttu-id="53d87-107">Zobacz [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) struktury.</span><span class="sxs-lookup"><span data-stu-id="53d87-107">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="53d87-108">[in] Opcjonalnie.</span><span class="sxs-lookup"><span data-stu-id="53d87-108">[in] Optional.</span></span> <span data-ttu-id="53d87-109">Kombinacją następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="53d87-109">A combination of following values:</span></span>  
  
-   <span data-ttu-id="53d87-110">AXL_REVOCATION_NO_CHECK</span><span class="sxs-lookup"><span data-stu-id="53d87-110">AXL_REVOCATION_NO_CHECK</span></span>  
  
-   <span data-ttu-id="53d87-111">AXL_REVOCATION_CHECK_END_CERT_ONLY</span><span class="sxs-lookup"><span data-stu-id="53d87-111">AXL_REVOCATION_CHECK_END_CERT_ONLY</span></span>  
  
-   <span data-ttu-id="53d87-112">AXL_REVOCATION_CHECK_ENTIRE_CHAIN</span><span class="sxs-lookup"><span data-stu-id="53d87-112">AXL_REVOCATION_CHECK_ENTIRE_CHAIN</span></span>  
  
-   <span data-ttu-id="53d87-113">AXL_URL_CACHE_ONLY_RETRIEVAL</span><span class="sxs-lookup"><span data-stu-id="53d87-113">AXL_URL_CACHE_ONLY_RETRIEVAL</span></span>  
  
-   <span data-ttu-id="53d87-114">AXL_LIFETIME_SIGNING</span><span class="sxs-lookup"><span data-stu-id="53d87-114">AXL_LIFETIME_SIGNING</span></span>  
  
-   <span data-ttu-id="53d87-115">AXL_TRUST_MICROSOFT_ROOT_ONLY</span><span class="sxs-lookup"><span data-stu-id="53d87-115">AXL_TRUST_MICROSOFT_ROOT_ONLY</span></span>  
  
 `pSignerInfo`  
 <span data-ttu-id="53d87-116">[out] Aby odbierać informacje podpisującej.</span><span class="sxs-lookup"><span data-stu-id="53d87-116">[out] To receive the signer's information.</span></span> <span data-ttu-id="53d87-117">Jeśli licencja nie został podpisany, `dwError` jest ustawiona na TRUST_E_NOSIGNATURE.</span><span class="sxs-lookup"><span data-stu-id="53d87-117">If the license wasn't signed, `dwError` is set to TRUST_E_NOSIGNATURE.</span></span> <span data-ttu-id="53d87-118">Jest odpowiedzialny za obiektu wywołującego, aby zwolnić zasoby przy użyciu [CertFreeAuthenticodeSignerInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodesignerinfo-function.md) funkcji po ich użyciu.</span><span class="sxs-lookup"><span data-stu-id="53d87-118">It is the caller's responsibility to free resources by using the [CertFreeAuthenticodeSignerInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodesignerinfo-function.md) function after use.</span></span>  
  
 <span data-ttu-id="53d87-119">Zobacz [struktura AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md).</span><span class="sxs-lookup"><span data-stu-id="53d87-119">See [AXL_AUTHENTICODE_SIGNER_INFO Structure](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md).</span></span>  
  
 `pTimestamperInfo`  
 <span data-ttu-id="53d87-120">[out] Do odbierania informacji stamper czasu, jeśli jest dostępny.</span><span class="sxs-lookup"><span data-stu-id="53d87-120">[out] To receive time stamper's information, if available.</span></span> <span data-ttu-id="53d87-121">Jeśli licencja nie sygnaturami czasowymi, `dwError` jest ustawiona na TRUST_E_NOSIGNATURE.</span><span class="sxs-lookup"><span data-stu-id="53d87-121">If the license was not time-stamped, `dwError` is set to TRUST_E_NOSIGNATURE.</span></span> <span data-ttu-id="53d87-122">Jest odpowiedzialny za obiektu wywołującego, aby zwolnić zasoby przy użyciu [CertFreeAuthenticodeTimestamperInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodetimestamperinfo-function.md) funkcji po ich użyciu.</span><span class="sxs-lookup"><span data-stu-id="53d87-122">It is the caller's responsibility to free resources by using the [CertFreeAuthenticodeTimestamperInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodetimestamperinfo-function.md) function after use.</span></span>  
  
 <span data-ttu-id="53d87-123">Zobacz [struktura AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md).</span><span class="sxs-lookup"><span data-stu-id="53d87-123">See [AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="53d87-124">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="53d87-124">Return Value</span></span>  
 <span data-ttu-id="53d87-125">Zwraca `S_OK` w przypadku powodzenia.</span><span class="sxs-lookup"><span data-stu-id="53d87-125">Returns `S_OK` if successful.</span></span> <span data-ttu-id="53d87-126">W przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="53d87-126">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53d87-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="53d87-127">See Also</span></span>  
 [<span data-ttu-id="53d87-128">Authenticode</span><span class="sxs-lookup"><span data-stu-id="53d87-128">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)  
 [<span data-ttu-id="53d87-129">GetHashFromHandle, metoda</span><span class="sxs-lookup"><span data-stu-id="53d87-129">GetHashFromHandle Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)  
 [<span data-ttu-id="53d87-130">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="53d87-130">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
