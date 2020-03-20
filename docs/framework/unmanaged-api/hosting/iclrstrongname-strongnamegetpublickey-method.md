---
title: ICLRStrongName::StrongNameGetPublicKey — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetPublicKey
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameGetPublicKey method [.NET Framework hosting]
ms.assetid: a31dcaa9-a404-4c1d-8cc7-081827c52935
topic_type:
- apiref
ms.openlocfilehash: cb96c7e17627205db0573e56fc8c2a29e7717434
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181938"
---
# <a name="iclrstrongnamestrongnamegetpublickey-method"></a><span data-ttu-id="a577a-102">ICLRStrongName::StrongNameGetPublicKey — Metoda</span><span class="sxs-lookup"><span data-stu-id="a577a-102">ICLRStrongName::StrongNameGetPublicKey Method</span></span>
<span data-ttu-id="a577a-103">Pobiera klucz publiczny z pary klucza publicznego/prywatnego.</span><span class="sxs-lookup"><span data-stu-id="a577a-103">Gets the public key from a public/private key pair.</span></span> <span data-ttu-id="a577a-104">Para kluczy może być podana jako nazwa kontenera klucza w dostawcy usług kryptograficznych (CSP) lub jako nieprzetworzona kolekcja bajtów.</span><span class="sxs-lookup"><span data-stu-id="a577a-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a577a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a577a-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetPublicKey (
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a577a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a577a-106">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="a577a-107">[w] Nazwa kontenera klucza zawierającego parę kluczy publicznych/prywatnych.</span><span class="sxs-lookup"><span data-stu-id="a577a-107">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="a577a-108">Jeśli `pbKeyBlob` wartość `szKeyContainer` null jest zerowa, należy określić prawidłowy kontener w ramach usługi CSP.</span><span class="sxs-lookup"><span data-stu-id="a577a-108">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="a577a-109">W takim przypadku [metoda ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) wyodrębnia klucz publiczny z pary kluczy przechowywanej w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="a577a-109">In this case, the [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="a577a-110">Jeśli `pbKeyBlob` nie ma wartości null, przyjmuje się, że para kluczy znajduje się w głównym obiekcie binarnym (BLOB).</span><span class="sxs-lookup"><span data-stu-id="a577a-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="a577a-111">Klucze muszą być 1024-bitowe klucze podpisywania Rivest-Shamir-Adleman (RSA).</span><span class="sxs-lookup"><span data-stu-id="a577a-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="a577a-112">Żadne inne typy kluczy są obecnie obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="a577a-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="a577a-113">[w] Wskaźnik do pary kluczy publicznych/prywatnych.</span><span class="sxs-lookup"><span data-stu-id="a577a-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="a577a-114">Ta para jest w formacie utworzonym `CryptExportKey` przez funkcję Win32.</span><span class="sxs-lookup"><span data-stu-id="a577a-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="a577a-115">Jeśli `pbKeyBlob` ma wartość null, `szKeyContainer` przyjmuje się, że kontener kluczy określony przez zawiera parę kluczy.</span><span class="sxs-lookup"><span data-stu-id="a577a-115">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="a577a-116">[w] Rozmiar w bajtach `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="a577a-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="a577a-117">[na zewnątrz] Zwrócony obiekt BLOB klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="a577a-117">[out] The returned public key BLOB.</span></span> <span data-ttu-id="a577a-118">Parametr `ppbPublicKeyBlob` jest przydzielany przez środowisko uruchomieniowe języka wspólnego i zwracany do wywołującego.</span><span class="sxs-lookup"><span data-stu-id="a577a-118">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="a577a-119">Wywołujący musi zwolnić pamięć przy użyciu [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="a577a-119">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="a577a-120">[na zewnątrz] Rozmiar zwracanego obiektu BLOB klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="a577a-120">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a577a-121">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a577a-121">Return Value</span></span>  
 <span data-ttu-id="a577a-122">`S_OK`jeśli metoda została pomyślnie ukończona; w przeciwnym razie wartość HRESULT wskazująca błąd (zobacz [typowe wartości HRESULT](/windows/win32/seccrypto/common-hresult-values) dla listy).</span><span class="sxs-lookup"><span data-stu-id="a577a-122">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a577a-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a577a-123">Remarks</span></span>  
 <span data-ttu-id="a577a-124">Klucz publiczny znajduje się w [strukturze PublicKeyBlob.](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)</span><span class="sxs-lookup"><span data-stu-id="a577a-124">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a577a-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a577a-125">Requirements</span></span>  
 <span data-ttu-id="a577a-126">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a577a-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a577a-127">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="a577a-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a577a-128">**Biblioteka:** Uwzględnione jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a577a-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a577a-129">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a577a-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a577a-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a577a-130">See also</span></span>

- [<span data-ttu-id="a577a-131">StrongNameTokenFromPublicKey, metoda</span><span class="sxs-lookup"><span data-stu-id="a577a-131">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="a577a-132">PublicKeyBlob — Struktura</span><span class="sxs-lookup"><span data-stu-id="a577a-132">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="a577a-133">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="a577a-133">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
