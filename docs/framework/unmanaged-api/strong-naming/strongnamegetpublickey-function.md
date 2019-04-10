---
title: StrongNameGetPublicKey — Funkcja
ms.date: 03/30/2017
api_name:
- StrongNameGetPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey function [.NET Framework strong naming]
ms.assetid: 5b58c87f-3f72-40df-9b9a-291076931cc3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e0e38a85b688d66e9f44bd8026bb4c9e141a6eb7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59229293"
---
# <a name="strongnamegetpublickey-function"></a><span data-ttu-id="ef02a-102">StrongNameGetPublicKey — Funkcja</span><span class="sxs-lookup"><span data-stu-id="ef02a-102">StrongNameGetPublicKey Function</span></span>
<span data-ttu-id="ef02a-103">Pobiera klucz publiczny z pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="ef02a-103">Gets the public key from a private/public key pair.</span></span> <span data-ttu-id="ef02a-104">Pary kluczy można podać jako nazwę kontenera kluczy w dostawcy usług kryptograficznych (CSP) lub jako kolekcję pierwotnych bajtów.</span><span class="sxs-lookup"><span data-stu-id="ef02a-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
 <span data-ttu-id="ef02a-105">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="ef02a-105">This function has been deprecated.</span></span> <span data-ttu-id="ef02a-106">Użyj [iclrstrongname::strongnamegetpublickey —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="ef02a-106">Use the [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef02a-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="ef02a-107">Syntax</span></span>  
  
```  
BOOLEAN StrongNameGetPublicKey (   
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef02a-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="ef02a-108">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="ef02a-109">[in] Nazwa kontenera kluczy, który zawiera pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="ef02a-109">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="ef02a-110">Jeśli `pbKeyBlob` ma wartość null, `szKeyContainer` należy określić prawidłowy kontener w ramach dostawcy usług Kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="ef02a-110">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="ef02a-111">W tym przypadku `StrongNameGetPublicKey` wyodrębnia klucz publiczny z pary kluczy, przechowywane w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="ef02a-111">In this case, `StrongNameGetPublicKey` extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="ef02a-112">Jeśli `pbKeyBlob` nie ma wartości null, zakłada, że pary kluczy muszą być zawarte w kluczowych duży obiekt binarny (BLOB).</span><span class="sxs-lookup"><span data-stu-id="ef02a-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="ef02a-113">Klucze muszą być Rivest-Shamir-Adleman 1024-bitowy (RSA) kluczy podpisywania.</span><span class="sxs-lookup"><span data-stu-id="ef02a-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="ef02a-114">Żadne inne typy kluczy są obsługiwane w tej chwili.</span><span class="sxs-lookup"><span data-stu-id="ef02a-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="ef02a-115">[in] Wskaźnik do pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="ef02a-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="ef02a-116">Ta para jest w formacie utworzone przez Win32 `CryptExportKey` funkcji.</span><span class="sxs-lookup"><span data-stu-id="ef02a-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="ef02a-117">Jeśli `pbKeyBlob` jest null, kontenerze klucza określonym przez `szKeyContainer` założono, że zawiera pary kluczy.</span><span class="sxs-lookup"><span data-stu-id="ef02a-117">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="ef02a-118">[in] Rozmiar w bajtach z `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="ef02a-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="ef02a-119">[out] Zwrócone klucza publicznego obiektu BLOB.</span><span class="sxs-lookup"><span data-stu-id="ef02a-119">[out] The returned public key BLOB.</span></span> <span data-ttu-id="ef02a-120">`ppbPublicKeyBlob` Parametr jest przydzielany przez środowisko uruchomieniowe języka wspólnego i zwracany do wywołującego.</span><span class="sxs-lookup"><span data-stu-id="ef02a-120">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="ef02a-121">Obiekt wywołujący musi zwolnić pamięć przy użyciu [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="ef02a-121">The caller must free the memory by using the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="ef02a-122">[out] Rozmiar zwróconego obiektu BLOB klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="ef02a-122">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ef02a-123">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ef02a-123">Return Value</span></span>  
 `true` <span data-ttu-id="ef02a-124">Po pomyślnym zakończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="ef02a-124">on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef02a-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ef02a-125">Remarks</span></span>  
 <span data-ttu-id="ef02a-126">Klucz publiczny jest zawarty w [publickeyblob —](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="ef02a-126">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
 <span data-ttu-id="ef02a-127">Jeśli `StrongNameGetPublicKey` funkcja nie jest ukończone pomyślnie, wywołaj [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcję, aby pobrać ostatni błąd wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="ef02a-127">If the `StrongNameGetPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef02a-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ef02a-128">Requirements</span></span>  
 <span data-ttu-id="ef02a-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef02a-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef02a-130">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="ef02a-130">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="ef02a-131">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ef02a-131">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="ef02a-132">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="ef02a-132">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ef02a-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ef02a-133">See also</span></span>

- [<span data-ttu-id="ef02a-134">StrongNameGetPublicKey, metoda</span><span class="sxs-lookup"><span data-stu-id="ef02a-134">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="ef02a-135">StrongNameTokenFromPublicKey, metoda</span><span class="sxs-lookup"><span data-stu-id="ef02a-135">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="ef02a-136">ICLRStrongName — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ef02a-136">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="ef02a-137">PublicKeyBlob — Struktura</span><span class="sxs-lookup"><span data-stu-id="ef02a-137">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
