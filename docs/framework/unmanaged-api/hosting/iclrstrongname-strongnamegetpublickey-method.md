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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c8d97653a195ec0fc287455079f37b311c3d42e4
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43387160"
---
# <a name="iclrstrongnamestrongnamegetpublickey-method"></a><span data-ttu-id="b112a-102">ICLRStrongName::StrongNameGetPublicKey — Metoda</span><span class="sxs-lookup"><span data-stu-id="b112a-102">ICLRStrongName::StrongNameGetPublicKey Method</span></span>
<span data-ttu-id="b112a-103">Pobiera klucz publiczny z pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="b112a-103">Gets the public key from a public/private key pair.</span></span> <span data-ttu-id="b112a-104">Pary kluczy można podać jako nazwę kontenera kluczy w dostawcy usług kryptograficznych (CSP) lub jako kolekcję pierwotnych bajtów.</span><span class="sxs-lookup"><span data-stu-id="b112a-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b112a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b112a-105">Syntax</span></span>  
  
```  
HRESULT StrongNameGetPublicKey (   
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b112a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b112a-106">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="b112a-107">[in] Nazwa kontenera kluczy, który zawiera pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="b112a-107">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="b112a-108">Jeśli `pbKeyBlob` ma wartość null, `szKeyContainer` należy określić prawidłowy kontener w ramach dostawcy usług Kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="b112a-108">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="b112a-109">W tym przypadku [iclrstrongname::strongnamegetpublickey —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) metoda wyodrębnia klucz publiczny z pary kluczy, przechowywane w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="b112a-109">In this case, the [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="b112a-110">Jeśli `pbKeyBlob` nie ma wartości null, zakłada, że pary kluczy muszą być zawarte w kluczowych duży obiekt binarny (BLOB).</span><span class="sxs-lookup"><span data-stu-id="b112a-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="b112a-111">Klucze muszą być Rivest-Shamir-Adleman 1024-bitowy (RSA) kluczy podpisywania.</span><span class="sxs-lookup"><span data-stu-id="b112a-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="b112a-112">Żadne inne typy kluczy są obsługiwane w tej chwili.</span><span class="sxs-lookup"><span data-stu-id="b112a-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="b112a-113">[in] Wskaźnik do pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="b112a-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="b112a-114">Ta para jest w formacie utworzone przez Win32 `CryptExportKey` funkcji.</span><span class="sxs-lookup"><span data-stu-id="b112a-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="b112a-115">Jeśli `pbKeyBlob` jest null, kontenerze klucza określonym przez `szKeyContainer` założono, że zawiera pary kluczy.</span><span class="sxs-lookup"><span data-stu-id="b112a-115">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="b112a-116">[in] Rozmiar w bajtach z `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="b112a-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="b112a-117">[out] Zwrócone klucza publicznego obiektu BLOB.</span><span class="sxs-lookup"><span data-stu-id="b112a-117">[out] The returned public key BLOB.</span></span> <span data-ttu-id="b112a-118">`ppbPublicKeyBlob` Parametr jest przydzielany przez środowisko uruchomieniowe języka wspólnego i zwracany do wywołującego.</span><span class="sxs-lookup"><span data-stu-id="b112a-118">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="b112a-119">Obiekt wywołujący musi zwolnić pamięć przy użyciu [iclrstrongname::strongnamefreebuffer —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="b112a-119">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="b112a-120">[out] Rozmiar zwróconego obiektu BLOB klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="b112a-120">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b112a-121">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b112a-121">Return Value</span></span>  
 <span data-ttu-id="b112a-122">`S_OK` Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje błąd (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).</span><span class="sxs-lookup"><span data-stu-id="b112a-122">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b112a-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b112a-123">Remarks</span></span>  
 <span data-ttu-id="b112a-124">Klucz publiczny jest zawarty w [publickeyblob —](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="b112a-124">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b112a-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b112a-125">Requirements</span></span>  
 <span data-ttu-id="b112a-126">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b112a-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b112a-127">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="b112a-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b112a-128">**Biblioteka:** dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b112a-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b112a-129">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b112a-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b112a-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b112a-130">See Also</span></span>  
 [<span data-ttu-id="b112a-131">StrongNameTokenFromPublicKey, metoda</span><span class="sxs-lookup"><span data-stu-id="b112a-131">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)  
 [<span data-ttu-id="b112a-132">PublicKeyBlob, struktura</span><span class="sxs-lookup"><span data-stu-id="b112a-132">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
 [<span data-ttu-id="b112a-133">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="b112a-133">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
