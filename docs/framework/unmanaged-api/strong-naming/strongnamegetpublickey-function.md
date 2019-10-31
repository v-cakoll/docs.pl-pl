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
ms.openlocfilehash: 966a2a628f30f1999688da7b6ba435c1d6cb830c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73094665"
---
# <a name="strongnamegetpublickey-function"></a><span data-ttu-id="ed3a6-102">StrongNameGetPublicKey — Funkcja</span><span class="sxs-lookup"><span data-stu-id="ed3a6-102">StrongNameGetPublicKey Function</span></span>
<span data-ttu-id="ed3a6-103">Pobiera klucz publiczny z pary kluczy prywatnych/publicznych.</span><span class="sxs-lookup"><span data-stu-id="ed3a6-103">Gets the public key from a private/public key pair.</span></span> <span data-ttu-id="ed3a6-104">Para kluczy może być podana jako nazwa kontenera klucza w ramach dostawcy usług kryptograficznych (CSP) lub jako pierwotna kolekcja bajtów.</span><span class="sxs-lookup"><span data-stu-id="ed3a6-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
 <span data-ttu-id="ed3a6-105">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="ed3a6-105">This function has been deprecated.</span></span> <span data-ttu-id="ed3a6-106">Zamiast tego użyj metody [ICLRStrongName:: StrongNameGetPublicKey —](../hosting/iclrstrongname-strongnamegetpublickey-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ed3a6-106">Use the [ICLRStrongName::StrongNameGetPublicKey](../hosting/iclrstrongname-strongnamegetpublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed3a6-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="ed3a6-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetPublicKey (   
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed3a6-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="ed3a6-108">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="ed3a6-109">podczas Nazwa kontenera kluczy, który zawiera parę kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="ed3a6-109">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="ed3a6-110">Jeśli `pbKeyBlob` ma wartość null, `szKeyContainer` musi określić prawidłowy kontener w ramach dostawcy CSP.</span><span class="sxs-lookup"><span data-stu-id="ed3a6-110">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="ed3a6-111">W takim przypadku `StrongNameGetPublicKey` wyodrębnia klucz publiczny z pary kluczy przechowywanej w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="ed3a6-111">In this case, `StrongNameGetPublicKey` extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="ed3a6-112">Jeśli `pbKeyBlob` nie ma wartości null, przyjmuje się, że para kluczy jest zawarta w kluczowym dużym obiekcie binarnym (BLOB).</span><span class="sxs-lookup"><span data-stu-id="ed3a6-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="ed3a6-113">Klucze muszą być 1024-bitowe Rivest-Shamir-Adleman (RSA) kluczy podpisywania.</span><span class="sxs-lookup"><span data-stu-id="ed3a6-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="ed3a6-114">W tej chwili nie są obsługiwane żadne inne typy kluczy.</span><span class="sxs-lookup"><span data-stu-id="ed3a6-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="ed3a6-115">podczas Wskaźnik do pary kluczy publicznych/prywatnych.</span><span class="sxs-lookup"><span data-stu-id="ed3a6-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="ed3a6-116">Ta para jest w formacie utworzonym przez funkcję `CryptExportKey` Win32.</span><span class="sxs-lookup"><span data-stu-id="ed3a6-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="ed3a6-117">Jeśli `pbKeyBlob` ma wartość null, założono, że kontener kluczy określony przez `szKeyContainer` zostanie zawierający parę kluczy.</span><span class="sxs-lookup"><span data-stu-id="ed3a6-117">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="ed3a6-118">podczas Rozmiar w bajtach `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="ed3a6-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="ed3a6-119">określoną Zwrócony obiekt BLOB klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="ed3a6-119">[out] The returned public key BLOB.</span></span> <span data-ttu-id="ed3a6-120">Parametr `ppbPublicKeyBlob` jest przypisywany przez środowisko uruchomieniowe języka wspólnego i zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="ed3a6-120">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="ed3a6-121">Obiekt wywołujący musi zwolnić pamięć przy użyciu funkcji [StrongNameFreeBuffer —](strongnamefreebuffer-function.md) .</span><span class="sxs-lookup"><span data-stu-id="ed3a6-121">The caller must free the memory by using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="ed3a6-122">określoną Rozmiar zwróconego obiektu BLOB klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="ed3a6-122">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ed3a6-123">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ed3a6-123">Return Value</span></span>  
 <span data-ttu-id="ed3a6-124">`true` po pomyślnym zakończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="ed3a6-124">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed3a6-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ed3a6-125">Remarks</span></span>  
 <span data-ttu-id="ed3a6-126">Klucz publiczny jest zawarty w strukturze [PublicKeyBlob —](publickeyblob-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="ed3a6-126">The public key is contained in a [PublicKeyBlob](publickeyblob-structure.md) structure.</span></span>  
  
 <span data-ttu-id="ed3a6-127">Jeśli funkcja `StrongNameGetPublicKey` nie zakończy się pomyślnie, wywołaj funkcję [StrongNameErrorInfo —](strongnameerrorinfo-function.md) w celu pobrania ostatniego wygenerowanego błędu.</span><span class="sxs-lookup"><span data-stu-id="ed3a6-127">If the `StrongNameGetPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed3a6-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ed3a6-128">Requirements</span></span>  
 <span data-ttu-id="ed3a6-129">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed3a6-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed3a6-130">**Nagłówek:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="ed3a6-130">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="ed3a6-131">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ed3a6-131">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ed3a6-132">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed3a6-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed3a6-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ed3a6-133">See also</span></span>

- [<span data-ttu-id="ed3a6-134">StrongNameGetPublicKey, metoda</span><span class="sxs-lookup"><span data-stu-id="ed3a6-134">StrongNameGetPublicKey Method</span></span>](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="ed3a6-135">StrongNameTokenFromPublicKey, metoda</span><span class="sxs-lookup"><span data-stu-id="ed3a6-135">StrongNameTokenFromPublicKey Method</span></span>](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="ed3a6-136">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="ed3a6-136">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="ed3a6-137">PublicKeyBlob, struktura</span><span class="sxs-lookup"><span data-stu-id="ed3a6-137">PublicKeyBlob Structure</span></span>](publickeyblob-structure.md)
