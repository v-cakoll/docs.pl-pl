---
title: "ICLRStrongName::StrongNameGetPublicKey — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameGetPublicKey
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameGetPublicKey method [.NET Framework hosting]
ms.assetid: a31dcaa9-a404-4c1d-8cc7-081827c52935
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4b7ace87a5eff5235d85507bda649e55ea18fd93
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongnamestrongnamegetpublickey-method"></a><span data-ttu-id="902e3-102">ICLRStrongName::StrongNameGetPublicKey — Metoda</span><span class="sxs-lookup"><span data-stu-id="902e3-102">ICLRStrongName::StrongNameGetPublicKey Method</span></span>
<span data-ttu-id="902e3-103">Pobiera klucz publiczny z pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="902e3-103">Gets the public key from a public/private key pair.</span></span> <span data-ttu-id="902e3-104">Pary kluczy można podać jako nazwa kontenera klucza dostawcy usług kryptograficznych (CSP) lub jako kolekcję pierwotnych bajtów.</span><span class="sxs-lookup"><span data-stu-id="902e3-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="902e3-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="902e3-105">Syntax</span></span>  
  
```  
HRESULT StrongNameGetPublicKey (   
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="902e3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="902e3-106">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="902e3-107">[in] Nazwa kontenera klucza, który zawiera pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="902e3-107">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="902e3-108">Jeśli `pbKeyBlob` ma wartość null, `szKeyContainer` należy określić prawidłowy kontener w ramach dostawcy usług Kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="902e3-108">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="902e3-109">W takim przypadku [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) metody wyodrębnia klucza publicznego z pary kluczy przechowywanych w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="902e3-109">In this case, the [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="902e3-110">Jeśli `pbKeyBlob` nie ma wartości null, zakłada, że pary kluczy muszą być zawarte w klucza dużego obiektu binarnego (BLOB).</span><span class="sxs-lookup"><span data-stu-id="902e3-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="902e3-111">Klucze muszą być Rivest-Shamir-Adleman (RSA 1024-bitowe) kluczy podpisywania.</span><span class="sxs-lookup"><span data-stu-id="902e3-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="902e3-112">Żadne inne typy klucze są obsługiwane w tej chwili.</span><span class="sxs-lookup"><span data-stu-id="902e3-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="902e3-113">[in] Wskaźnik do pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="902e3-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="902e3-114">Tej pary jest w formacie utworzone przez Win32 `CryptExportKey` funkcji.</span><span class="sxs-lookup"><span data-stu-id="902e3-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="902e3-115">Jeśli `pbKeyBlob` jest null, określony przez kontener klucza `szKeyContainer` założono, że zawiera pary kluczy.</span><span class="sxs-lookup"><span data-stu-id="902e3-115">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="902e3-116">[in] Rozmiar w bajtach z `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="902e3-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="902e3-117">[out] Zwrócony klucza publicznego obiektu BLOB.</span><span class="sxs-lookup"><span data-stu-id="902e3-117">[out] The returned public key BLOB.</span></span> <span data-ttu-id="902e3-118">`ppbPublicKeyBlob` Parametr jest przydzielany przez środowisko uruchomieniowe języka wspólnego i zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="902e3-118">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="902e3-119">Obiekt wywołujący musi zwolnić pamięć przy użyciu [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="902e3-119">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="902e3-120">[out] Rozmiar zwróconego obiektu BLOB klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="902e3-120">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="902e3-121">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="902e3-121">Return Value</span></span>  
 <span data-ttu-id="902e3-122">`S_OK`Jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje niepowodzenie (zobacz [wspólne wartości HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) lista).</span><span class="sxs-lookup"><span data-stu-id="902e3-122">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="902e3-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="902e3-123">Remarks</span></span>  
 <span data-ttu-id="902e3-124">Klucz publiczny jest zawarta w [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="902e3-124">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="902e3-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="902e3-125">Requirements</span></span>  
 <span data-ttu-id="902e3-126">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="902e3-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="902e3-127">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="902e3-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="902e3-128">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="902e3-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="902e3-129">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="902e3-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="902e3-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="902e3-130">See Also</span></span>  
 [<span data-ttu-id="902e3-131">StrongNameTokenFromPublicKey — metoda</span><span class="sxs-lookup"><span data-stu-id="902e3-131">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)  
 [<span data-ttu-id="902e3-132">Publickeyblob — struktura</span><span class="sxs-lookup"><span data-stu-id="902e3-132">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
 [<span data-ttu-id="902e3-133">ICLRStrongName — interfejs</span><span class="sxs-lookup"><span data-stu-id="902e3-133">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
