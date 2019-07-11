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
ms.openlocfilehash: f6e9e5c199ad437290d7bf19d65b5f29a0abed5e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780109"
---
# <a name="strongnamegetpublickey-function"></a><span data-ttu-id="cd241-102">StrongNameGetPublicKey — Funkcja</span><span class="sxs-lookup"><span data-stu-id="cd241-102">StrongNameGetPublicKey Function</span></span>
<span data-ttu-id="cd241-103">Pobiera klucz publiczny z pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="cd241-103">Gets the public key from a private/public key pair.</span></span> <span data-ttu-id="cd241-104">Pary kluczy można podać jako nazwę kontenera kluczy w dostawcy usług kryptograficznych (CSP) lub jako kolekcję pierwotnych bajtów.</span><span class="sxs-lookup"><span data-stu-id="cd241-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
 <span data-ttu-id="cd241-105">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="cd241-105">This function has been deprecated.</span></span> <span data-ttu-id="cd241-106">Użyj [iclrstrongname::strongnamegetpublickey —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="cd241-106">Use the [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd241-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="cd241-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetPublicKey (   
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd241-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="cd241-108">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="cd241-109">[in] Nazwa kontenera kluczy, który zawiera pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="cd241-109">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="cd241-110">Jeśli `pbKeyBlob` ma wartość null, `szKeyContainer` należy określić prawidłowy kontener w ramach dostawcy usług Kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="cd241-110">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="cd241-111">W tym przypadku `StrongNameGetPublicKey` wyodrębnia klucz publiczny z pary kluczy, przechowywane w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="cd241-111">In this case, `StrongNameGetPublicKey` extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="cd241-112">Jeśli `pbKeyBlob` nie ma wartości null, zakłada, że pary kluczy muszą być zawarte w kluczowych duży obiekt binarny (BLOB).</span><span class="sxs-lookup"><span data-stu-id="cd241-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="cd241-113">Klucze muszą być Rivest-Shamir-Adleman 1024-bitowy (RSA) kluczy podpisywania.</span><span class="sxs-lookup"><span data-stu-id="cd241-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="cd241-114">Żadne inne typy kluczy są obsługiwane w tej chwili.</span><span class="sxs-lookup"><span data-stu-id="cd241-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="cd241-115">[in] Wskaźnik do pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="cd241-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="cd241-116">Ta para jest w formacie utworzone przez Win32 `CryptExportKey` funkcji.</span><span class="sxs-lookup"><span data-stu-id="cd241-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="cd241-117">Jeśli `pbKeyBlob` jest null, kontenerze klucza określonym przez `szKeyContainer` założono, że zawiera pary kluczy.</span><span class="sxs-lookup"><span data-stu-id="cd241-117">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="cd241-118">[in] Rozmiar w bajtach z `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="cd241-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="cd241-119">[out] Zwrócone klucza publicznego obiektu BLOB.</span><span class="sxs-lookup"><span data-stu-id="cd241-119">[out] The returned public key BLOB.</span></span> <span data-ttu-id="cd241-120">`ppbPublicKeyBlob` Parametr jest przydzielany przez środowisko uruchomieniowe języka wspólnego i zwracany do wywołującego.</span><span class="sxs-lookup"><span data-stu-id="cd241-120">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="cd241-121">Obiekt wywołujący musi zwolnić pamięć przy użyciu [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="cd241-121">The caller must free the memory by using the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="cd241-122">[out] Rozmiar zwróconego obiektu BLOB klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="cd241-122">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cd241-123">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cd241-123">Return Value</span></span>  
 <span data-ttu-id="cd241-124">`true` Po pomyślnym zakończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="cd241-124">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd241-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cd241-125">Remarks</span></span>  
 <span data-ttu-id="cd241-126">Klucz publiczny jest zawarty w [publickeyblob —](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="cd241-126">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
 <span data-ttu-id="cd241-127">Jeśli `StrongNameGetPublicKey` funkcja nie jest ukończone pomyślnie, wywołaj [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcję, aby pobrać ostatni błąd wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="cd241-127">If the `StrongNameGetPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd241-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cd241-128">Requirements</span></span>  
 <span data-ttu-id="cd241-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd241-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd241-130">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="cd241-130">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="cd241-131">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cd241-131">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cd241-132">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd241-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd241-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cd241-133">See also</span></span>

- [<span data-ttu-id="cd241-134">StrongNameGetPublicKey, metoda</span><span class="sxs-lookup"><span data-stu-id="cd241-134">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="cd241-135">StrongNameTokenFromPublicKey, metoda</span><span class="sxs-lookup"><span data-stu-id="cd241-135">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="cd241-136">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="cd241-136">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="cd241-137">PublicKeyBlob, struktura</span><span class="sxs-lookup"><span data-stu-id="cd241-137">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
