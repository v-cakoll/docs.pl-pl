---
title: StrongNameGetPublicKeyEx — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName2.StrongNameGetPublicKeyEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StrongNameGetPublicKeyEx
helpviewer_keywords:
- StrongNameGetPublicKeyEx method, ICLRStrongName2 interface [.NET Framework hosting]
- ICLRStrongName2::StrongNameGetPublicKeyEx method [.NET Framework hosting]
ms.assetid: 63d8260c-fb32-4f8f-a357-768afd570f68
topic_type:
- apiref
ms.openlocfilehash: 93afe1afd9ea9637d039a8b4a4e81267d49c08b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176230"
---
# <a name="strongnamegetpublickeyex-method"></a><span data-ttu-id="b2344-102">StrongNameGetPublicKeyEx — Metoda</span><span class="sxs-lookup"><span data-stu-id="b2344-102">StrongNameGetPublicKeyEx Method</span></span>
<span data-ttu-id="b2344-103">Pobiera klucz publiczny z pary klucza publicznego/prywatnego i określa algorytm mieszania i algorytm podpisu.</span><span class="sxs-lookup"><span data-stu-id="b2344-103">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2344-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b2344-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetPublicKey (
    [in]  LPCWSTR   pwzKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
    [in]  ULONG     uHashAlgId,  
    [in]  ULONG     uReserved,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2344-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b2344-105">Parameters</span></span>  
 `pwzKeyContainer`  
 <span data-ttu-id="b2344-106">[w] Nazwa kontenera klucza zawierającego parę kluczy publicznych/prywatnych.</span><span class="sxs-lookup"><span data-stu-id="b2344-106">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="b2344-107">Jeśli `pbKeyBlob` wartość `szKeyContainer` null jest zerowa, należy określić prawidłowy kontener w ramach dostawcy usług kryptograficznych (CSP).</span><span class="sxs-lookup"><span data-stu-id="b2344-107">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="b2344-108">W takim przypadku `StrongNameGetPublicKeyEx` metoda wyodrębnia klucz publiczny z pary kluczy przechowywanych w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="b2344-108">In this case, the `StrongNameGetPublicKeyEx` method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="b2344-109">Jeśli `pbKeyBlob` nie ma wartości null, przyjmuje się, że para kluczy znajduje się w głównym obiekcie binarnym (BLOB).</span><span class="sxs-lookup"><span data-stu-id="b2344-109">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="b2344-110">Klucze muszą być 1024-bitowe klucze podpisywania Rivest-Shamir-Adleman (RSA).</span><span class="sxs-lookup"><span data-stu-id="b2344-110">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="b2344-111">Żadne inne typy kluczy są obecnie obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="b2344-111">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="b2344-112">[w] Wskaźnik do pary kluczy publicznych/prywatnych.</span><span class="sxs-lookup"><span data-stu-id="b2344-112">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="b2344-113">Ta para jest w formacie utworzonym `CryptExportKey` przez funkcję Win32.</span><span class="sxs-lookup"><span data-stu-id="b2344-113">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="b2344-114">Jeśli `pbKeyBlob` ma wartość null, `szKeyContainer` przyjmuje się, że kontener kluczy określony przez zawiera parę kluczy.</span><span class="sxs-lookup"><span data-stu-id="b2344-114">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="b2344-115">[w] Rozmiar w bajtach `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="b2344-115">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="b2344-116">[na zewnątrz] Zwrócony obiekt BLOB klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="b2344-116">[out] The returned public key BLOB.</span></span> <span data-ttu-id="b2344-117">Parametr `ppbPublicKeyBlob` jest przydzielany przez środowisko uruchomieniowe języka wspólnego i zwracany do wywołującego.</span><span class="sxs-lookup"><span data-stu-id="b2344-117">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="b2344-118">Wywołujący musi zwolnić pamięć przy użyciu [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="b2344-118">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="b2344-119">[na zewnątrz] Rozmiar zwracanego obiektu BLOB klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="b2344-119">[out] The size of the returned public key BLOB.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="b2344-120">[w] Algorytm mieszania zestawu.</span><span class="sxs-lookup"><span data-stu-id="b2344-120">[in] The assembly hash algorithm.</span></span> <span data-ttu-id="b2344-121">Zobacz uwagi sekcji listy zaakceptowanych wartości.</span><span class="sxs-lookup"><span data-stu-id="b2344-121">See the Remarks section for a list of accepted values.</span></span>  
  
 `uReserved`  
 <span data-ttu-id="b2344-122">[w] Zarezerwowane do wykorzystania w przyszłości; wartości null.</span><span class="sxs-lookup"><span data-stu-id="b2344-122">[in] Reserved for future use; defaults to null.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b2344-123">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b2344-123">Return Value</span></span>  
 <span data-ttu-id="b2344-124">`S_OK`jeśli metoda została pomyślnie ukończona; w przeciwnym razie wartość HRESULT wskazująca błąd (zobacz [typowe wartości HRESULT](/windows/win32/seccrypto/common-hresult-values) dla listy).</span><span class="sxs-lookup"><span data-stu-id="b2344-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2344-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b2344-125">Remarks</span></span>  
 <span data-ttu-id="b2344-126">Klucz publiczny znajduje się w [strukturze PublicKeyBlob.](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)</span><span class="sxs-lookup"><span data-stu-id="b2344-126">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2344-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b2344-127">Remarks</span></span>  
 <span data-ttu-id="b2344-128">W poniższej tabeli przedstawiono zestaw `uHashAlgId` zaakceptowanych wartości dla parametru.</span><span class="sxs-lookup"><span data-stu-id="b2344-128">The following table shows the set of accepted values for the `uHashAlgId` parameter.</span></span>  
  
|<span data-ttu-id="b2344-129">Nazwa</span><span class="sxs-lookup"><span data-stu-id="b2344-129">Name</span></span>|<span data-ttu-id="b2344-130">Wartość</span><span class="sxs-lookup"><span data-stu-id="b2344-130">Value</span></span>|  
|----------|-----------|  
|<span data-ttu-id="b2344-131">Brak</span><span class="sxs-lookup"><span data-stu-id="b2344-131">None</span></span>|<span data-ttu-id="b2344-132">0</span><span class="sxs-lookup"><span data-stu-id="b2344-132">0</span></span>|  
|<span data-ttu-id="b2344-133">SHA-1</span><span class="sxs-lookup"><span data-stu-id="b2344-133">SHA-1</span></span>|<span data-ttu-id="b2344-134">0x8004</span><span class="sxs-lookup"><span data-stu-id="b2344-134">0x8004</span></span>|  
|<span data-ttu-id="b2344-135">SHA-256</span><span class="sxs-lookup"><span data-stu-id="b2344-135">SHA-256</span></span>|<span data-ttu-id="b2344-136">0x800c</span><span class="sxs-lookup"><span data-stu-id="b2344-136">0x800c</span></span>|  
|<span data-ttu-id="b2344-137">SHA-384</span><span class="sxs-lookup"><span data-stu-id="b2344-137">SHA-384</span></span>|<span data-ttu-id="b2344-138">0x800d</span><span class="sxs-lookup"><span data-stu-id="b2344-138">0x800d</span></span>|  
|<span data-ttu-id="b2344-139">SHA-512</span><span class="sxs-lookup"><span data-stu-id="b2344-139">SHA-512</span></span>|<span data-ttu-id="b2344-140">0x800e</span><span class="sxs-lookup"><span data-stu-id="b2344-140">0x800e</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b2344-141">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b2344-141">Requirements</span></span>  
 <span data-ttu-id="b2344-142">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2344-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2344-143">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="b2344-143">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b2344-144">**Biblioteka:** Uwzględnione jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b2344-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b2344-145">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2344-145">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2344-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b2344-146">See also</span></span>

- [<span data-ttu-id="b2344-147">StrongNameTokenFromPublicKey, metoda</span><span class="sxs-lookup"><span data-stu-id="b2344-147">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="b2344-148">PublicKeyBlob — Struktura</span><span class="sxs-lookup"><span data-stu-id="b2344-148">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="b2344-149">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="b2344-149">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="b2344-150">StrongNameGetPublicKey, metoda</span><span class="sxs-lookup"><span data-stu-id="b2344-150">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
