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
ms.openlocfilehash: 700bcc5b818c452d3642d325fb6fe19cbb162474
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141444"
---
# <a name="strongnamegetpublickeyex-method"></a><span data-ttu-id="1d400-102">StrongNameGetPublicKeyEx — Metoda</span><span class="sxs-lookup"><span data-stu-id="1d400-102">StrongNameGetPublicKeyEx Method</span></span>
<span data-ttu-id="1d400-103">Pobiera klucz publiczny z pary kluczy publiczny/prywatny i określa algorytm skrótu i algorytm podpisu.</span><span class="sxs-lookup"><span data-stu-id="1d400-103">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d400-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1d400-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="1d400-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1d400-105">Parameters</span></span>  
 `pwzKeyContainer`  
 <span data-ttu-id="1d400-106">podczas Nazwa kontenera kluczy, który zawiera parę kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="1d400-106">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="1d400-107">Jeśli `pbKeyBlob` ma wartość null, `szKeyContainer` musi określić prawidłowego kontenera w ramach dostawcy usług kryptograficznych (CSP).</span><span class="sxs-lookup"><span data-stu-id="1d400-107">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="1d400-108">W takim przypadku Metoda `StrongNameGetPublicKeyEx` wyodrębnia klucz publiczny z pary kluczy przechowywanej w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="1d400-108">In this case, the `StrongNameGetPublicKeyEx` method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="1d400-109">Jeśli `pbKeyBlob` nie ma wartości null, przyjmuje się, że para kluczy jest zawarta w kluczowym dużym obiekcie binarnym (BLOB).</span><span class="sxs-lookup"><span data-stu-id="1d400-109">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="1d400-110">Klucze muszą być 1024-bitowe Rivest-Shamir-Adleman (RSA) kluczy podpisywania.</span><span class="sxs-lookup"><span data-stu-id="1d400-110">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="1d400-111">W tej chwili nie są obsługiwane żadne inne typy kluczy.</span><span class="sxs-lookup"><span data-stu-id="1d400-111">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="1d400-112">podczas Wskaźnik do pary kluczy publicznych/prywatnych.</span><span class="sxs-lookup"><span data-stu-id="1d400-112">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="1d400-113">Ta para jest w formacie utworzonym przez funkcję `CryptExportKey` Win32.</span><span class="sxs-lookup"><span data-stu-id="1d400-113">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="1d400-114">Jeśli `pbKeyBlob` ma wartość null, założono, że kontener kluczy określony przez `szKeyContainer` zostanie zawierający parę kluczy.</span><span class="sxs-lookup"><span data-stu-id="1d400-114">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="1d400-115">podczas Rozmiar w bajtach `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="1d400-115">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="1d400-116">określoną Zwrócony obiekt BLOB klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="1d400-116">[out] The returned public key BLOB.</span></span> <span data-ttu-id="1d400-117">Parametr `ppbPublicKeyBlob` jest przypisywany przez środowisko uruchomieniowe języka wspólnego i zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="1d400-117">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="1d400-118">Obiekt wywołujący musi zwolnić pamięć przy użyciu metody [ICLRStrongName:: StrongNameFreeBuffer —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1d400-118">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="1d400-119">określoną Rozmiar zwróconego obiektu BLOB klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="1d400-119">[out] The size of the returned public key BLOB.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="1d400-120">podczas Algorytm wyznaczania wartości skrótu zestawu.</span><span class="sxs-lookup"><span data-stu-id="1d400-120">[in] The assembly hash algorithm.</span></span> <span data-ttu-id="1d400-121">Zapoznaj się z sekcją uwagi, aby uzyskać listę zaakceptowanych wartości.</span><span class="sxs-lookup"><span data-stu-id="1d400-121">See the Remarks section for a list of accepted values.</span></span>  
  
 `uReserved`  
 <span data-ttu-id="1d400-122">podczas Zarezerwowane do użytku w przyszłości; Wartością domyślną jest null.</span><span class="sxs-lookup"><span data-stu-id="1d400-122">[in] Reserved for future use; defaults to null.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1d400-123">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1d400-123">Return Value</span></span>  
 <span data-ttu-id="1d400-124">`S_OK`, jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT wskazująca niepowodzenie (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).</span><span class="sxs-lookup"><span data-stu-id="1d400-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d400-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1d400-125">Remarks</span></span>  
 <span data-ttu-id="1d400-126">Klucz publiczny jest zawarty w strukturze [PublicKeyBlob —](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="1d400-126">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d400-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1d400-127">Remarks</span></span>  
 <span data-ttu-id="1d400-128">W poniższej tabeli przedstawiono zestaw akceptowanych wartości dla parametru `uHashAlgId`.</span><span class="sxs-lookup"><span data-stu-id="1d400-128">The following table shows the set of accepted values for the `uHashAlgId` parameter.</span></span>  
  
|<span data-ttu-id="1d400-129">Nazwa</span><span class="sxs-lookup"><span data-stu-id="1d400-129">Name</span></span>|<span data-ttu-id="1d400-130">Wartość</span><span class="sxs-lookup"><span data-stu-id="1d400-130">Value</span></span>|  
|----------|-----------|  
|<span data-ttu-id="1d400-131">Brak</span><span class="sxs-lookup"><span data-stu-id="1d400-131">None</span></span>|<span data-ttu-id="1d400-132">0</span><span class="sxs-lookup"><span data-stu-id="1d400-132">0</span></span>|  
|<span data-ttu-id="1d400-133">SHA-1</span><span class="sxs-lookup"><span data-stu-id="1d400-133">SHA-1</span></span>|<span data-ttu-id="1d400-134">0x8004</span><span class="sxs-lookup"><span data-stu-id="1d400-134">0x8004</span></span>|  
|<span data-ttu-id="1d400-135">SHA-256</span><span class="sxs-lookup"><span data-stu-id="1d400-135">SHA-256</span></span>|<span data-ttu-id="1d400-136">0x800c</span><span class="sxs-lookup"><span data-stu-id="1d400-136">0x800c</span></span>|  
|<span data-ttu-id="1d400-137">SHA-384</span><span class="sxs-lookup"><span data-stu-id="1d400-137">SHA-384</span></span>|<span data-ttu-id="1d400-138">0x800d</span><span class="sxs-lookup"><span data-stu-id="1d400-138">0x800d</span></span>|  
|<span data-ttu-id="1d400-139">SHA-512</span><span class="sxs-lookup"><span data-stu-id="1d400-139">SHA-512</span></span>|<span data-ttu-id="1d400-140">0x800e</span><span class="sxs-lookup"><span data-stu-id="1d400-140">0x800e</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1d400-141">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1d400-141">Requirements</span></span>  
 <span data-ttu-id="1d400-142">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d400-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d400-143">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="1d400-143">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1d400-144">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1d400-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1d400-145">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d400-145">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d400-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1d400-146">See also</span></span>

- [<span data-ttu-id="1d400-147">StrongNameTokenFromPublicKey, metoda</span><span class="sxs-lookup"><span data-stu-id="1d400-147">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="1d400-148">PublicKeyBlob, struktura</span><span class="sxs-lookup"><span data-stu-id="1d400-148">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="1d400-149">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="1d400-149">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="1d400-150">StrongNameGetPublicKey, metoda</span><span class="sxs-lookup"><span data-stu-id="1d400-150">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
