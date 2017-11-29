---
title: Funkcja CertVerifyAuthenticodeLicense
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CertVerifyAuthenticodeLicense
api_location: clr.dll
api_type: DLLExport
ms.assetid: 00118de7-33c6-41c4-8e1f-5d5e35e0da83
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 16d8067b4cd5d0a7b3db5be5b3b9ed4d689e1b0e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="certverifyauthenticodelicense-function"></a><span data-ttu-id="4da1a-102">Funkcja CertVerifyAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="4da1a-102">CertVerifyAuthenticodeLicense Function</span></span>
<span data-ttu-id="4da1a-103">Sprawdza poprawność licencję Authenticode XrML.</span><span class="sxs-lookup"><span data-stu-id="4da1a-103">Verifies the validity of an Authenticode XrML license.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4da1a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4da1a-104">Syntax</span></span>  
  
```  
HRESULT CertVerifyAuthenticodeLicense (  
    [in]   PCRYPT_DATA_BLOB                   pLicenseBlob,  
    [in]   OPTIONAL DWORD                     dwFlags,  
    [out]  PAXL_AUTHENTICODE_SIGNER_INFO      pSignerInfo,  
    [out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO pTimestamperInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4da1a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4da1a-105">Parameters</span></span>  
 `pLicenseBlob`  
 <span data-ttu-id="4da1a-106">[in] Licencja Authenticode XrML do weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="4da1a-106">[in] The Authenticode XrML license to be verified.</span></span>  
  
 <span data-ttu-id="4da1a-107">Zobacz [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) struktury.</span><span class="sxs-lookup"><span data-stu-id="4da1a-107">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="4da1a-108">[in] Opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="4da1a-108">[in] Optional.</span></span> <span data-ttu-id="4da1a-109">Kombinację następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="4da1a-109">A combination of following values:</span></span>  
  
-   <span data-ttu-id="4da1a-110">AXL_REVOCATION_NO_CHECK</span><span class="sxs-lookup"><span data-stu-id="4da1a-110">AXL_REVOCATION_NO_CHECK</span></span>  
  
-   <span data-ttu-id="4da1a-111">AXL_REVOCATION_CHECK_END_CERT_ONLY</span><span class="sxs-lookup"><span data-stu-id="4da1a-111">AXL_REVOCATION_CHECK_END_CERT_ONLY</span></span>  
  
-   <span data-ttu-id="4da1a-112">AXL_REVOCATION_CHECK_ENTIRE_CHAIN</span><span class="sxs-lookup"><span data-stu-id="4da1a-112">AXL_REVOCATION_CHECK_ENTIRE_CHAIN</span></span>  
  
-   <span data-ttu-id="4da1a-113">AXL_URL_CACHE_ONLY_RETRIEVAL</span><span class="sxs-lookup"><span data-stu-id="4da1a-113">AXL_URL_CACHE_ONLY_RETRIEVAL</span></span>  
  
-   <span data-ttu-id="4da1a-114">AXL_LIFETIME_SIGNING</span><span class="sxs-lookup"><span data-stu-id="4da1a-114">AXL_LIFETIME_SIGNING</span></span>  
  
-   <span data-ttu-id="4da1a-115">AXL_TRUST_MICROSOFT_ROOT_ONLY</span><span class="sxs-lookup"><span data-stu-id="4da1a-115">AXL_TRUST_MICROSOFT_ROOT_ONLY</span></span>  
  
 `pSignerInfo`  
 <span data-ttu-id="4da1a-116">[out] Aby odbierać informacje podpisującej.</span><span class="sxs-lookup"><span data-stu-id="4da1a-116">[out] To receive the signer's information.</span></span> <span data-ttu-id="4da1a-117">Jeśli licencja nie został podpisany, `dwError` ma ustawioną wartość TRUST_E_NOSIGNATURE.</span><span class="sxs-lookup"><span data-stu-id="4da1a-117">If the license wasn't signed, `dwError` is set to TRUST_E_NOSIGNATURE.</span></span> <span data-ttu-id="4da1a-118">Odpowiedzialność wywołującego, aby zwolnić zasoby przy użyciu [CertFreeAuthenticodeSignerInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodesignerinfo-function.md) funkcja po użyciu.</span><span class="sxs-lookup"><span data-stu-id="4da1a-118">It is the caller's responsibility to free resources by using the [CertFreeAuthenticodeSignerInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodesignerinfo-function.md) function after use.</span></span>  
  
 <span data-ttu-id="4da1a-119">Zobacz [struktura AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md).</span><span class="sxs-lookup"><span data-stu-id="4da1a-119">See [AXL_AUTHENTICODE_SIGNER_INFO Structure](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md).</span></span>  
  
 `pTimestamperInfo`  
 <span data-ttu-id="4da1a-120">[out] Do odbierania informacji stamper czasu, jeśli jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="4da1a-120">[out] To receive time stamper's information, if available.</span></span> <span data-ttu-id="4da1a-121">Jeśli licencja nie sygnaturami czasowymi `dwError` ma ustawioną wartość TRUST_E_NOSIGNATURE.</span><span class="sxs-lookup"><span data-stu-id="4da1a-121">If the license was not time-stamped, `dwError` is set to TRUST_E_NOSIGNATURE.</span></span> <span data-ttu-id="4da1a-122">Odpowiedzialność wywołującego, aby zwolnić zasoby przy użyciu [CertFreeAuthenticodeTimestamperInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodetimestamperinfo-function.md) funkcja po użyciu.</span><span class="sxs-lookup"><span data-stu-id="4da1a-122">It is the caller's responsibility to free resources by using the [CertFreeAuthenticodeTimestamperInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodetimestamperinfo-function.md) function after use.</span></span>  
  
 <span data-ttu-id="4da1a-123">Zobacz [struktura AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md).</span><span class="sxs-lookup"><span data-stu-id="4da1a-123">See [AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4da1a-124">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4da1a-124">Return Value</span></span>  
 <span data-ttu-id="4da1a-125">Zwraca `S_OK` w przypadku powodzenia.</span><span class="sxs-lookup"><span data-stu-id="4da1a-125">Returns `S_OK` if successful.</span></span> <span data-ttu-id="4da1a-126">W przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="4da1a-126">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4da1a-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4da1a-127">See Also</span></span>  
 [<span data-ttu-id="4da1a-128">Authenticode</span><span class="sxs-lookup"><span data-stu-id="4da1a-128">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)  
 [<span data-ttu-id="4da1a-129">GetHashFromHandle — metoda</span><span class="sxs-lookup"><span data-stu-id="4da1a-129">GetHashFromHandle Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)  
 [<span data-ttu-id="4da1a-130">ICLRStrongName — interfejs</span><span class="sxs-lookup"><span data-stu-id="4da1a-130">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
