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
ms.openlocfilehash: 6c2bb6f0324c461f59bd98a70333b176e79a16a6
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039590"
---
# <a name="certtimestampauthenticodelicense-function"></a><span data-ttu-id="2811c-102">Funkcja CertTimestampAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="2811c-102">CertTimestampAuthenticodeLicense Function</span></span>
<span data-ttu-id="2811c-103">Sygnatura czasowa oznacza licencję z kodem XrML Authenticode.</span><span class="sxs-lookup"><span data-stu-id="2811c-103">Time-stamps an Authenticode XrML license.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2811c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2811c-104">Syntax</span></span>  
  
```cpp  
HRESULT CertTimestampAuthenticodeLicense (  
    [in]  PCRYPT_DATA_BLOB   pSignedLicenseBlob,  
    [in]  LPCWSTR            pwszTimestampURI,  
    [out] PCRYPT_DATA_BLOB   pTimestampSignatureBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2811c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2811c-105">Parameters</span></span>  
 `pSignedLicenseBlob`  
 <span data-ttu-id="2811c-106">podczas Sygnatura czasowa podpisanej licencji na technologię Authenticode.</span><span class="sxs-lookup"><span data-stu-id="2811c-106">[in] The signed Authenticode XrML license to be time-stamped.</span></span> <span data-ttu-id="2811c-107">Zobacz strukturę [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .</span><span class="sxs-lookup"><span data-stu-id="2811c-107">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `pwszTimestampURI`  
 <span data-ttu-id="2811c-108">podczas Identyfikator URI serwera sygnatur czasowych.</span><span class="sxs-lookup"><span data-stu-id="2811c-108">[in] The time-stamp server's URI.</span></span>  
  
 `pTimestampSignatureBlob`  
 <span data-ttu-id="2811c-109">określoną Wskaźnik do CRYPT_DATA_BLOB, aby otrzymać sygnaturę sygnatury czasowej zakodowaną algorytmem Base64.</span><span class="sxs-lookup"><span data-stu-id="2811c-109">[out] A pointer to CRYPT_DATA_BLOB to receive the base64-encoded time-stamp signature.</span></span> <span data-ttu-id="2811c-110">Jest on odpowiedzialny `pTimestampSignatureBlob` za bezpłatne -> `pbData` korzystanie z `HepFree()` programu.</span><span class="sxs-lookup"><span data-stu-id="2811c-110">It is the caller's responsibility to free `pTimestampSignatureBlob`->`pbData` with `HepFree()` after use.</span></span> <span data-ttu-id="2811c-111">Zobacz strukturę [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .</span><span class="sxs-lookup"><span data-stu-id="2811c-111">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2811c-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2811c-112">Remarks</span></span>  
 <span data-ttu-id="2811c-113">Sygnatura czasowa jest w rzeczywistości certyfikatem PKCS #7 SignedData, którego zawartość jest binarną formą SignatureValue z podpisu licencji.</span><span class="sxs-lookup"><span data-stu-id="2811c-113">The time-stamp signature is actually a PKCS #7 SignedData message whose content is the binary form of the SignatureValue from the license's signature.</span></span> <span data-ttu-id="2811c-114">Zasadniczo to pełni rolę sygnatury z licencją.</span><span class="sxs-lookup"><span data-stu-id="2811c-114">Basically, this acts as a counter-signature of the license.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2811c-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2811c-115">Return Value</span></span>  
 <span data-ttu-id="2811c-116">`S_OK`Jeśli funkcja się powiedzie.</span><span class="sxs-lookup"><span data-stu-id="2811c-116">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="2811c-117">W przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="2811c-117">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2811c-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2811c-118">See also</span></span>

- [<span data-ttu-id="2811c-119">Authenticode</span><span class="sxs-lookup"><span data-stu-id="2811c-119">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
