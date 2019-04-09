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
ms.openlocfilehash: 5ac7cf92fb9c57491ff45e664513c0e82f22db9f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111725"
---
# <a name="certtimestampauthenticodelicense-function"></a><span data-ttu-id="c46fb-102">Funkcja CertTimestampAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="c46fb-102">CertTimestampAuthenticodeLicense Function</span></span>
<span data-ttu-id="c46fb-103">Sygnatury czasowe wiadomość Authenticode XrML licencji.</span><span class="sxs-lookup"><span data-stu-id="c46fb-103">Time-stamps an Authenticode XrML license.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c46fb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c46fb-104">Syntax</span></span>  
  
```  
HRESULT CertTimestampAuthenticodeLicense (  
    [in]  PCRYPT_DATA_BLOB   pSignedLicenseBlob,  
    [in]  LPCWSTR            pwszTimestampURI,  
    [out] PCRYPT_DATA_BLOB   pTimestampSignatureBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c46fb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c46fb-105">Parameters</span></span>  
 `pSignedLicenseBlob`  
 <span data-ttu-id="c46fb-106">[in] Podpisem Authenticode XrML licencja na mieć sygnaturę czasową.</span><span class="sxs-lookup"><span data-stu-id="c46fb-106">[in] The signed Authenticode XrML license to be time-stamped.</span></span> <span data-ttu-id="c46fb-107">Zobacz [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) struktury.</span><span class="sxs-lookup"><span data-stu-id="c46fb-107">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
 `pwszTimestampURI`  
 <span data-ttu-id="c46fb-108">[in] Identyfikator URI serwera sygnaturę czasową.</span><span class="sxs-lookup"><span data-stu-id="c46fb-108">[in] The time-stamp server's URI.</span></span>  
  
 `pTimestampSignatureBlob`  
 <span data-ttu-id="c46fb-109">[out] Wskaźnik do CRYPT_DATA_BLOB otrzymywać sygnatury sygnatura czasowa algorytmem Base64.</span><span class="sxs-lookup"><span data-stu-id="c46fb-109">[out] A pointer to CRYPT_DATA_BLOB to receive the base64-encoded time-stamp signature.</span></span> <span data-ttu-id="c46fb-110">Odpowiada za wywołującego bezpłatne `pTimestampSignatureBlob` -> `pbData` z `HepFree()` po użyciu.</span><span class="sxs-lookup"><span data-stu-id="c46fb-110">It is the caller's responsibility to free `pTimestampSignatureBlob`->`pbData` with `HepFree()` after use.</span></span> <span data-ttu-id="c46fb-111">Zobacz [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) struktury.</span><span class="sxs-lookup"><span data-stu-id="c46fb-111">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c46fb-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c46fb-112">Remarks</span></span>  
 <span data-ttu-id="c46fb-113">Podpis sygnatura czasowa jest faktycznie PKCS #7 SignedData komunikatu informującego, których zawartość jest binarną formę SignatureValue z poziomu podpisu licencji.</span><span class="sxs-lookup"><span data-stu-id="c46fb-113">The time-stamp signature is actually a PKCS #7 SignedData message whose content is the binary form of the SignatureValue from the license's signature.</span></span> <span data-ttu-id="c46fb-114">Zasadniczo jest to zabezpieczenie kontrsygnatury licencji.</span><span class="sxs-lookup"><span data-stu-id="c46fb-114">Basically, this acts as a counter-signature of the license.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c46fb-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c46fb-115">Return Value</span></span>  
 `S_OK` <span data-ttu-id="c46fb-116">Jeśli funkcja się powiedzie.</span><span class="sxs-lookup"><span data-stu-id="c46fb-116">if the function succeeds.</span></span> <span data-ttu-id="c46fb-117">W przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="c46fb-117">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c46fb-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c46fb-118">See also</span></span>

- [<span data-ttu-id="c46fb-119">Authenticode</span><span class="sxs-lookup"><span data-stu-id="c46fb-119">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
