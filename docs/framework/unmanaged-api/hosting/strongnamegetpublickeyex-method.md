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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7cb1f55e1d8643feb2750e8ea468f608dc3d5d40
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61984259"
---
# <a name="strongnamegetpublickeyex-method"></a><span data-ttu-id="cbd5e-102">StrongNameGetPublicKeyEx — Metoda</span><span class="sxs-lookup"><span data-stu-id="cbd5e-102">StrongNameGetPublicKeyEx Method</span></span>
<span data-ttu-id="cbd5e-103">Pobiera klucz publiczny z pary kluczy publiczny/prywatny, a następnie określa algorytm wyznaczania wartości skrótu i algorytm podpisu.</span><span class="sxs-lookup"><span data-stu-id="cbd5e-103">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbd5e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cbd5e-104">Syntax</span></span>  
  
```  
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
  
## <a name="parameters"></a><span data-ttu-id="cbd5e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cbd5e-105">Parameters</span></span>  
 `pwzKeyContainer`  
 <span data-ttu-id="cbd5e-106">[in] Nazwa kontenera kluczy, który zawiera pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="cbd5e-106">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="cbd5e-107">Jeśli `pbKeyBlob` ma wartość null, `szKeyContainer` należy określić prawidłowy kontener w ramach dostawcy usług kryptograficznych (CSP).</span><span class="sxs-lookup"><span data-stu-id="cbd5e-107">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="cbd5e-108">W tym przypadku `StrongNameGetPublicKeyEx` metoda wyodrębnia klucz publiczny z pary kluczy, przechowywane w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="cbd5e-108">In this case, the `StrongNameGetPublicKeyEx` method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="cbd5e-109">Jeśli `pbKeyBlob` nie ma wartości null, zakłada, że pary kluczy muszą być zawarte w kluczowych duży obiekt binarny (BLOB).</span><span class="sxs-lookup"><span data-stu-id="cbd5e-109">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="cbd5e-110">Klucze muszą być Rivest-Shamir-Adleman 1024-bitowy (RSA) kluczy podpisywania.</span><span class="sxs-lookup"><span data-stu-id="cbd5e-110">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="cbd5e-111">Żadne inne typy kluczy są obsługiwane w tej chwili.</span><span class="sxs-lookup"><span data-stu-id="cbd5e-111">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="cbd5e-112">[in] Wskaźnik do pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="cbd5e-112">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="cbd5e-113">Ta para jest w formacie utworzone przez Win32 `CryptExportKey` funkcji.</span><span class="sxs-lookup"><span data-stu-id="cbd5e-113">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="cbd5e-114">Jeśli `pbKeyBlob` jest null, kontenerze klucza określonym przez `szKeyContainer` założono, że zawiera pary kluczy.</span><span class="sxs-lookup"><span data-stu-id="cbd5e-114">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="cbd5e-115">[in] Rozmiar w bajtach z `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="cbd5e-115">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="cbd5e-116">[out] Zwrócone klucza publicznego obiektu BLOB.</span><span class="sxs-lookup"><span data-stu-id="cbd5e-116">[out] The returned public key BLOB.</span></span> <span data-ttu-id="cbd5e-117">`ppbPublicKeyBlob` Parametr jest przydzielany przez środowisko uruchomieniowe języka wspólnego i zwracany do wywołującego.</span><span class="sxs-lookup"><span data-stu-id="cbd5e-117">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="cbd5e-118">Obiekt wywołujący musi zwolnić pamięć przy użyciu [iclrstrongname::strongnamefreebuffer —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="cbd5e-118">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="cbd5e-119">[out] Rozmiar zwróconego obiektu BLOB klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="cbd5e-119">[out] The size of the returned public key BLOB.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="cbd5e-120">[in] Algorytm wyznaczania wartości skrótu zestawu.</span><span class="sxs-lookup"><span data-stu-id="cbd5e-120">[in] The assembly hash algorithm.</span></span> <span data-ttu-id="cbd5e-121">Zobacz sekcję Spostrzeżenia, aby listy akceptowanych wartości.</span><span class="sxs-lookup"><span data-stu-id="cbd5e-121">See the Remarks section for a list of accepted values.</span></span>  
  
 `uReserved`  
 <span data-ttu-id="cbd5e-122">[in] Zarezerwowane dla przyszłego użytku; Wartość domyślna to null.</span><span class="sxs-lookup"><span data-stu-id="cbd5e-122">[in] Reserved for future use; defaults to null.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cbd5e-123">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cbd5e-123">Return Value</span></span>  
 <span data-ttu-id="cbd5e-124">`S_OK` Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje błąd (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).</span><span class="sxs-lookup"><span data-stu-id="cbd5e-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cbd5e-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cbd5e-125">Remarks</span></span>  
 <span data-ttu-id="cbd5e-126">Klucz publiczny jest zawarty w [publickeyblob —](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="cbd5e-126">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cbd5e-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cbd5e-127">Remarks</span></span>  
 <span data-ttu-id="cbd5e-128">W poniższej tabeli przedstawiono zestaw dopuszczalne wartości dla `uHashAlgId` parametru.</span><span class="sxs-lookup"><span data-stu-id="cbd5e-128">The following table shows the set of accepted values for the `uHashAlgId` parameter.</span></span>  
  
|<span data-ttu-id="cbd5e-129">Nazwa</span><span class="sxs-lookup"><span data-stu-id="cbd5e-129">Name</span></span>|<span data-ttu-id="cbd5e-130">Wartość</span><span class="sxs-lookup"><span data-stu-id="cbd5e-130">Value</span></span>|  
|----------|-----------|  
|<span data-ttu-id="cbd5e-131">Brak</span><span class="sxs-lookup"><span data-stu-id="cbd5e-131">None</span></span>|<span data-ttu-id="cbd5e-132">0</span><span class="sxs-lookup"><span data-stu-id="cbd5e-132">0</span></span>|  
|<span data-ttu-id="cbd5e-133">SHA-1</span><span class="sxs-lookup"><span data-stu-id="cbd5e-133">SHA-1</span></span>|<span data-ttu-id="cbd5e-134">0x8004</span><span class="sxs-lookup"><span data-stu-id="cbd5e-134">0x8004</span></span>|  
|<span data-ttu-id="cbd5e-135">SHA-256</span><span class="sxs-lookup"><span data-stu-id="cbd5e-135">SHA-256</span></span>|<span data-ttu-id="cbd5e-136">0x800c</span><span class="sxs-lookup"><span data-stu-id="cbd5e-136">0x800c</span></span>|  
|<span data-ttu-id="cbd5e-137">SHA-384</span><span class="sxs-lookup"><span data-stu-id="cbd5e-137">SHA-384</span></span>|<span data-ttu-id="cbd5e-138">0x800d</span><span class="sxs-lookup"><span data-stu-id="cbd5e-138">0x800d</span></span>|  
|<span data-ttu-id="cbd5e-139">SHA-512</span><span class="sxs-lookup"><span data-stu-id="cbd5e-139">SHA-512</span></span>|<span data-ttu-id="cbd5e-140">0x800e</span><span class="sxs-lookup"><span data-stu-id="cbd5e-140">0x800e</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cbd5e-141">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cbd5e-141">Requirements</span></span>  
 <span data-ttu-id="cbd5e-142">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbd5e-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbd5e-143">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="cbd5e-143">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="cbd5e-144">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cbd5e-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cbd5e-145">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbd5e-145">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbd5e-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cbd5e-146">See also</span></span>

- [<span data-ttu-id="cbd5e-147">StrongNameTokenFromPublicKey, metoda</span><span class="sxs-lookup"><span data-stu-id="cbd5e-147">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="cbd5e-148">PublicKeyBlob, struktura</span><span class="sxs-lookup"><span data-stu-id="cbd5e-148">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="cbd5e-149">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="cbd5e-149">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="cbd5e-150">StrongNameGetPublicKey, metoda</span><span class="sxs-lookup"><span data-stu-id="cbd5e-150">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
