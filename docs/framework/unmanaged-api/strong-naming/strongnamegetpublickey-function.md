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
ms.openlocfilehash: ae87ebd0b8225f14ca029fac80528d47f5a866cf
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799060"
---
# <a name="strongnamegetpublickey-function"></a><span data-ttu-id="93322-102">StrongNameGetPublicKey — Funkcja</span><span class="sxs-lookup"><span data-stu-id="93322-102">StrongNameGetPublicKey Function</span></span>
<span data-ttu-id="93322-103">Pobiera klucz publiczny z pary kluczy prywatnych/publicznych.</span><span class="sxs-lookup"><span data-stu-id="93322-103">Gets the public key from a private/public key pair.</span></span> <span data-ttu-id="93322-104">Para kluczy może być podana jako nazwa kontenera klucza w ramach dostawcy usług kryptograficznych (CSP) lub jako pierwotna kolekcja bajtów.</span><span class="sxs-lookup"><span data-stu-id="93322-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
 <span data-ttu-id="93322-105">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="93322-105">This function has been deprecated.</span></span> <span data-ttu-id="93322-106">Zamiast tego użyj metody [ICLRStrongName:: StrongNameGetPublicKey —](../hosting/iclrstrongname-strongnamegetpublickey-method.md) .</span><span class="sxs-lookup"><span data-stu-id="93322-106">Use the [ICLRStrongName::StrongNameGetPublicKey](../hosting/iclrstrongname-strongnamegetpublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93322-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="93322-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetPublicKey (   
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="93322-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="93322-108">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="93322-109">podczas Nazwa kontenera kluczy, który zawiera parę kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="93322-109">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="93322-110">Jeśli `pbKeyBlob` ma wartość null `szKeyContainer` , należy określić prawidłowy kontener w ramach dostawcy CSP.</span><span class="sxs-lookup"><span data-stu-id="93322-110">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="93322-111">W takim przypadku `StrongNameGetPublicKey` wyodrębnia klucz publiczny z pary kluczy przechowywanej w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="93322-111">In this case, `StrongNameGetPublicKey` extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="93322-112">Jeśli `pbKeyBlob` wartość nie jest równa null, przyjmuje się, że para kluczy jest zawarta w kluczowym dużym obiekcie binarnym (BLOB).</span><span class="sxs-lookup"><span data-stu-id="93322-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="93322-113">Klucze muszą być 1024-bitowe Rivest-Shamir-Adleman (RSA) kluczy podpisywania.</span><span class="sxs-lookup"><span data-stu-id="93322-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="93322-114">W tej chwili nie są obsługiwane żadne inne typy kluczy.</span><span class="sxs-lookup"><span data-stu-id="93322-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="93322-115">podczas Wskaźnik do pary kluczy publicznych/prywatnych.</span><span class="sxs-lookup"><span data-stu-id="93322-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="93322-116">Ta para jest w formacie utworzonym przez funkcję Win32 `CryptExportKey` .</span><span class="sxs-lookup"><span data-stu-id="93322-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="93322-117">Jeśli `pbKeyBlob` ma wartość null, zakłada się, że `szKeyContainer` kontener kluczy określony przez ma zawierać parę kluczy.</span><span class="sxs-lookup"><span data-stu-id="93322-117">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="93322-118">podczas Rozmiar, w bajtach, z `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="93322-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="93322-119">określoną Zwrócony obiekt BLOB klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="93322-119">[out] The returned public key BLOB.</span></span> <span data-ttu-id="93322-120">`ppbPublicKeyBlob` Parametr jest przypisywany przez środowisko uruchomieniowe języka wspólnego i zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="93322-120">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="93322-121">Obiekt wywołujący musi zwolnić pamięć przy użyciu funkcji [StrongNameFreeBuffer —](strongnamefreebuffer-function.md) .</span><span class="sxs-lookup"><span data-stu-id="93322-121">The caller must free the memory by using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="93322-122">określoną Rozmiar zwróconego obiektu BLOB klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="93322-122">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="93322-123">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="93322-123">Return Value</span></span>  
 <span data-ttu-id="93322-124">`true`Po pomyślnym zakończeniu; w przeciwnym razie. `false`</span><span class="sxs-lookup"><span data-stu-id="93322-124">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93322-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="93322-125">Remarks</span></span>  
 <span data-ttu-id="93322-126">Klucz publiczny jest zawarty w strukturze [PublicKeyBlob —](publickeyblob-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="93322-126">The public key is contained in a [PublicKeyBlob](publickeyblob-structure.md) structure.</span></span>  
  
 <span data-ttu-id="93322-127">Jeśli funkcja nie zakończy się pomyślnie, wywołaj funkcję StrongNameErrorInfo — w celu pobrania ostatniego wygenerowanego błędu. [](strongnameerrorinfo-function.md) `StrongNameGetPublicKey`</span><span class="sxs-lookup"><span data-stu-id="93322-127">If the `StrongNameGetPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93322-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="93322-128">Requirements</span></span>  
 <span data-ttu-id="93322-129">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93322-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93322-130">**Nagłówki** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="93322-130">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="93322-131">**Biblioteki** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="93322-131">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="93322-132">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93322-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93322-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="93322-133">See also</span></span>

- [<span data-ttu-id="93322-134">StrongNameGetPublicKey, metoda</span><span class="sxs-lookup"><span data-stu-id="93322-134">StrongNameGetPublicKey Method</span></span>](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="93322-135">StrongNameTokenFromPublicKey, metoda</span><span class="sxs-lookup"><span data-stu-id="93322-135">StrongNameTokenFromPublicKey Method</span></span>](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="93322-136">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="93322-136">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="93322-137">PublicKeyBlob, struktura</span><span class="sxs-lookup"><span data-stu-id="93322-137">PublicKeyBlob Structure</span></span>](publickeyblob-structure.md)
