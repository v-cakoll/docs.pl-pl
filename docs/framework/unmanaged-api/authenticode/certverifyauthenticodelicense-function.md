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
ms.openlocfilehash: 8736da6c8db876b3dadb3b906a586633be176cf6
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038322"
---
# <a name="certverifyauthenticodelicense-function"></a><span data-ttu-id="77c3b-102">Funkcja CertVerifyAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="77c3b-102">CertVerifyAuthenticodeLicense Function</span></span>
<span data-ttu-id="77c3b-103">Weryfikuje ważność licencji XrML Authenticode.</span><span class="sxs-lookup"><span data-stu-id="77c3b-103">Verifies the validity of an Authenticode XrML license.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77c3b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="77c3b-104">Syntax</span></span>  
  
```cpp  
HRESULT CertVerifyAuthenticodeLicense (  
    [in]   PCRYPT_DATA_BLOB                   pLicenseBlob,  
    [in]   OPTIONAL DWORD                     dwFlags,  
    [out]  PAXL_AUTHENTICODE_SIGNER_INFO      pSignerInfo,  
    [out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77c3b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="77c3b-105">Parameters</span></span>  
 `pLicenseBlob`  
 <span data-ttu-id="77c3b-106">podczas Licencja na umowę XrML Authenticode do zweryfikowania.</span><span class="sxs-lookup"><span data-stu-id="77c3b-106">[in] The Authenticode XrML license to be verified.</span></span>  
  
 <span data-ttu-id="77c3b-107">Zobacz strukturę [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .</span><span class="sxs-lookup"><span data-stu-id="77c3b-107">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="77c3b-108">podczas Obowiązkowe.</span><span class="sxs-lookup"><span data-stu-id="77c3b-108">[in] Optional.</span></span> <span data-ttu-id="77c3b-109">Kombinacja następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="77c3b-109">A combination of following values:</span></span>  
  
- <span data-ttu-id="77c3b-110">AXL_REVOCATION_NO_CHECK</span><span class="sxs-lookup"><span data-stu-id="77c3b-110">AXL_REVOCATION_NO_CHECK</span></span>  
  
- <span data-ttu-id="77c3b-111">AXL_REVOCATION_CHECK_END_CERT_ONLY</span><span class="sxs-lookup"><span data-stu-id="77c3b-111">AXL_REVOCATION_CHECK_END_CERT_ONLY</span></span>  
  
- <span data-ttu-id="77c3b-112">AXL_REVOCATION_CHECK_ENTIRE_CHAIN</span><span class="sxs-lookup"><span data-stu-id="77c3b-112">AXL_REVOCATION_CHECK_ENTIRE_CHAIN</span></span>  
  
- <span data-ttu-id="77c3b-113">AXL_URL_CACHE_ONLY_RETRIEVAL</span><span class="sxs-lookup"><span data-stu-id="77c3b-113">AXL_URL_CACHE_ONLY_RETRIEVAL</span></span>  
  
- <span data-ttu-id="77c3b-114">AXL_LIFETIME_SIGNING</span><span class="sxs-lookup"><span data-stu-id="77c3b-114">AXL_LIFETIME_SIGNING</span></span>  
  
- <span data-ttu-id="77c3b-115">AXL_TRUST_MICROSOFT_ROOT_ONLY</span><span class="sxs-lookup"><span data-stu-id="77c3b-115">AXL_TRUST_MICROSOFT_ROOT_ONLY</span></span>  
  
 `pSignerInfo`  
 <span data-ttu-id="77c3b-116">określoną , Aby uzyskać informacje dotyczące osoby podpisującej.</span><span class="sxs-lookup"><span data-stu-id="77c3b-116">[out] To receive the signer's information.</span></span> <span data-ttu-id="77c3b-117">Jeśli licencja nie została podpisana `dwError` , jest ustawiona na TRUST_E_NOSIGNATURE.</span><span class="sxs-lookup"><span data-stu-id="77c3b-117">If the license wasn't signed, `dwError` is set to TRUST_E_NOSIGNATURE.</span></span> <span data-ttu-id="77c3b-118">Jest on odpowiedzialny za zwolnienie zasobów przy użyciu funkcji [CertFreeAuthenticodeSignerInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodesignerinfo-function.md) po użyciu.</span><span class="sxs-lookup"><span data-stu-id="77c3b-118">It is the caller's responsibility to free resources by using the [CertFreeAuthenticodeSignerInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodesignerinfo-function.md) function after use.</span></span>  
  
 <span data-ttu-id="77c3b-119">Zobacz [strukturę AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md).</span><span class="sxs-lookup"><span data-stu-id="77c3b-119">See [AXL_AUTHENTICODE_SIGNER_INFO Structure](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md).</span></span>  
  
 `pTimestamperInfo`  
 <span data-ttu-id="77c3b-120">określoną W celu uzyskania informacji o sygnaturze czasowej, jeśli są dostępne.</span><span class="sxs-lookup"><span data-stu-id="77c3b-120">[out] To receive time stamper's information, if available.</span></span> <span data-ttu-id="77c3b-121">Jeśli licencja nie była sygnaturą czasową, `dwError` jest ustawiona na TRUST_E_NOSIGNATURE.</span><span class="sxs-lookup"><span data-stu-id="77c3b-121">If the license was not time-stamped, `dwError` is set to TRUST_E_NOSIGNATURE.</span></span> <span data-ttu-id="77c3b-122">Jest on odpowiedzialny za zwolnienie zasobów przy użyciu funkcji [CertFreeAuthenticodeTimestamperInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodetimestamperinfo-function.md) po użyciu.</span><span class="sxs-lookup"><span data-stu-id="77c3b-122">It is the caller's responsibility to free resources by using the [CertFreeAuthenticodeTimestamperInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodetimestamperinfo-function.md) function after use.</span></span>  
  
 <span data-ttu-id="77c3b-123">Zobacz [strukturę AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md).</span><span class="sxs-lookup"><span data-stu-id="77c3b-123">See [AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="77c3b-124">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="77c3b-124">Return Value</span></span>  
 <span data-ttu-id="77c3b-125">Zwraca `S_OK` w przypadku powodzenia.</span><span class="sxs-lookup"><span data-stu-id="77c3b-125">Returns `S_OK` if successful.</span></span> <span data-ttu-id="77c3b-126">W przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="77c3b-126">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77c3b-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="77c3b-127">See also</span></span>

- [<span data-ttu-id="77c3b-128">Authenticode</span><span class="sxs-lookup"><span data-stu-id="77c3b-128">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
- [<span data-ttu-id="77c3b-129">GetHashFromHandle, metoda</span><span class="sxs-lookup"><span data-stu-id="77c3b-129">GetHashFromHandle Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)
- [<span data-ttu-id="77c3b-130">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="77c3b-130">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
