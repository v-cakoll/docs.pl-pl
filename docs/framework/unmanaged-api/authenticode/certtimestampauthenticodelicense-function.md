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
ms.openlocfilehash: 3c5e803c874e1254510f75189846d7cb12cb1ee2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132474"
---
# <a name="certtimestampauthenticodelicense-function"></a><span data-ttu-id="2f19a-102">Funkcja CertTimestampAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="2f19a-102">CertTimestampAuthenticodeLicense Function</span></span>
<span data-ttu-id="2f19a-103">Sygnatura czasowa oznacza licencję z kodem XrML Authenticode.</span><span class="sxs-lookup"><span data-stu-id="2f19a-103">Time-stamps an Authenticode XrML license.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f19a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2f19a-104">Syntax</span></span>  
  
```cpp  
HRESULT CertTimestampAuthenticodeLicense (  
    [in]  PCRYPT_DATA_BLOB   pSignedLicenseBlob,  
    [in]  LPCWSTR            pwszTimestampURI,  
    [out] PCRYPT_DATA_BLOB   pTimestampSignatureBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f19a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2f19a-105">Parameters</span></span>  
 `pSignedLicenseBlob`  
 <span data-ttu-id="2f19a-106">podczas Sygnatura czasowa podpisanej licencji na technologię Authenticode.</span><span class="sxs-lookup"><span data-stu-id="2f19a-106">[in] The signed Authenticode XrML license to be time-stamped.</span></span> <span data-ttu-id="2f19a-107">Zobacz strukturę [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .</span><span class="sxs-lookup"><span data-stu-id="2f19a-107">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `pwszTimestampURI`  
 <span data-ttu-id="2f19a-108">podczas Identyfikator URI serwera sygnatur czasowych.</span><span class="sxs-lookup"><span data-stu-id="2f19a-108">[in] The time-stamp server's URI.</span></span>  
  
 `pTimestampSignatureBlob`  
 <span data-ttu-id="2f19a-109">określoną Wskaźnik do CRYPT_DATA_BLOB, aby otrzymać sygnaturę sygnatury czasowej zakodowaną algorytmem Base64.</span><span class="sxs-lookup"><span data-stu-id="2f19a-109">[out] A pointer to CRYPT_DATA_BLOB to receive the base64-encoded time-stamp signature.</span></span> <span data-ttu-id="2f19a-110">Jest on odpowiedzialny za bezpłatny `pTimestampSignatureBlob`->`pbData` z `HepFree()` po użyciu.</span><span class="sxs-lookup"><span data-stu-id="2f19a-110">It is the caller's responsibility to free `pTimestampSignatureBlob`->`pbData` with `HepFree()` after use.</span></span> <span data-ttu-id="2f19a-111">Zobacz strukturę [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .</span><span class="sxs-lookup"><span data-stu-id="2f19a-111">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f19a-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2f19a-112">Remarks</span></span>  
 <span data-ttu-id="2f19a-113">Sygnatura czasowa jest w rzeczywistości certyfikatem PKCS #7 SignedData, którego zawartość jest binarną formą SignatureValue z podpisu licencji.</span><span class="sxs-lookup"><span data-stu-id="2f19a-113">The time-stamp signature is actually a PKCS #7 SignedData message whose content is the binary form of the SignatureValue from the license's signature.</span></span> <span data-ttu-id="2f19a-114">Zasadniczo to pełni rolę sygnatury z licencją.</span><span class="sxs-lookup"><span data-stu-id="2f19a-114">Basically, this acts as a counter-signature of the license.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2f19a-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2f19a-115">Return Value</span></span>  
 <span data-ttu-id="2f19a-116">`S_OK`, jeśli funkcja się powiedzie.</span><span class="sxs-lookup"><span data-stu-id="2f19a-116">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="2f19a-117">W przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="2f19a-117">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f19a-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2f19a-118">See also</span></span>

- [<span data-ttu-id="2f19a-119">Authenticode</span><span class="sxs-lookup"><span data-stu-id="2f19a-119">Authenticode</span></span>](index.md)
