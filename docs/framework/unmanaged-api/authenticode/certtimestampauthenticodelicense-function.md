---
title: Funkcja CertTimestampAuthenticodeLicense
ms.date: 03/30/2017
api_name:
- CertTimestampAuthenticodeLicense
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: d468325a-21c5-43ce-8567-84e342b22308
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9987640f988f2239a01d2dfdbcd6b1684579d8bc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54601510"
---
# <a name="certtimestampauthenticodelicense-function"></a><span data-ttu-id="bbf0f-102">Funkcja CertTimestampAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="bbf0f-102">CertTimestampAuthenticodeLicense Function</span></span>
<span data-ttu-id="bbf0f-103">Sygnatury czasowe wiadomość Authenticode XrML licencji.</span><span class="sxs-lookup"><span data-stu-id="bbf0f-103">Time-stamps an Authenticode XrML license.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbf0f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bbf0f-104">Syntax</span></span>  
  
```  
HRESULT CertTimestampAuthenticodeLicense (  
    [in]  PCRYPT_DATA_BLOB   pSignedLicenseBlob,  
    [in]  LPCWSTR            pwszTimestampURI,  
    [out] PCRYPT_DATA_BLOB   pTimestampSignatureBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bbf0f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bbf0f-105">Parameters</span></span>  
 `pSignedLicenseBlob`  
 <span data-ttu-id="bbf0f-106">[in] Podpisem Authenticode XrML licencja na mieć sygnaturę czasową.</span><span class="sxs-lookup"><span data-stu-id="bbf0f-106">[in] The signed Authenticode XrML license to be time-stamped.</span></span> <span data-ttu-id="bbf0f-107">Zobacz [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) struktury.</span><span class="sxs-lookup"><span data-stu-id="bbf0f-107">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
 `pwszTimestampURI`  
 <span data-ttu-id="bbf0f-108">[in] Identyfikator URI serwera sygnaturę czasową.</span><span class="sxs-lookup"><span data-stu-id="bbf0f-108">[in] The time-stamp server's URI.</span></span>  
  
 `pTimestampSignatureBlob`  
 <span data-ttu-id="bbf0f-109">[out] Wskaźnik do CRYPT_DATA_BLOB otrzymywać sygnatury sygnatura czasowa algorytmem Base64.</span><span class="sxs-lookup"><span data-stu-id="bbf0f-109">[out] A pointer to CRYPT_DATA_BLOB to receive the base64-encoded time-stamp signature.</span></span> <span data-ttu-id="bbf0f-110">Odpowiada za wywołującego bezpłatne `pTimestampSignatureBlob` -> `pbData` z `HepFree()` po użyciu.</span><span class="sxs-lookup"><span data-stu-id="bbf0f-110">It is the caller's responsibility to free `pTimestampSignatureBlob`->`pbData` with `HepFree()` after use.</span></span> <span data-ttu-id="bbf0f-111">Zobacz [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) struktury.</span><span class="sxs-lookup"><span data-stu-id="bbf0f-111">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bbf0f-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bbf0f-112">Remarks</span></span>  
 <span data-ttu-id="bbf0f-113">Podpis sygnatura czasowa jest faktycznie PKCS #7 SignedData komunikatu informującego, których zawartość jest binarną formę SignatureValue z poziomu podpisu licencji.</span><span class="sxs-lookup"><span data-stu-id="bbf0f-113">The time-stamp signature is actually a PKCS #7 SignedData message whose content is the binary form of the SignatureValue from the license's signature.</span></span> <span data-ttu-id="bbf0f-114">Zasadniczo jest to zabezpieczenie kontrsygnatury licencji.</span><span class="sxs-lookup"><span data-stu-id="bbf0f-114">Basically, this acts as a counter-signature of the license.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bbf0f-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bbf0f-115">Return Value</span></span>  
 <span data-ttu-id="bbf0f-116">`S_OK` Jeśli funkcja się powiedzie.</span><span class="sxs-lookup"><span data-stu-id="bbf0f-116">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="bbf0f-117">W przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="bbf0f-117">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbf0f-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bbf0f-118">See also</span></span>
- [<span data-ttu-id="bbf0f-119">Authenticode</span><span class="sxs-lookup"><span data-stu-id="bbf0f-119">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
