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
ms.openlocfilehash: fcdd4a3f07b4499fd2388b5d165c409da9150466
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176932"
---
# <a name="strongnamegetpublickey-function"></a><span data-ttu-id="78362-102">StrongNameGetPublicKey — Funkcja</span><span class="sxs-lookup"><span data-stu-id="78362-102">StrongNameGetPublicKey Function</span></span>
<span data-ttu-id="78362-103">Pobiera klucz publiczny z pary klucza prywatnego/publicznego.</span><span class="sxs-lookup"><span data-stu-id="78362-103">Gets the public key from a private/public key pair.</span></span> <span data-ttu-id="78362-104">Para kluczy może być podana jako nazwa kontenera klucza w dostawcy usług kryptograficznych (CSP) lub jako nieprzetworzona kolekcja bajtów.</span><span class="sxs-lookup"><span data-stu-id="78362-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
 <span data-ttu-id="78362-105">Ta funkcja została przestarzała.</span><span class="sxs-lookup"><span data-stu-id="78362-105">This function has been deprecated.</span></span> <span data-ttu-id="78362-106">Zamiast tego należy użyć metody [ICLRStrongName::StrongNameGetPublicKey.](../hosting/iclrstrongname-strongnamegetpublickey-method.md)</span><span class="sxs-lookup"><span data-stu-id="78362-106">Use the [ICLRStrongName::StrongNameGetPublicKey](../hosting/iclrstrongname-strongnamegetpublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78362-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="78362-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetPublicKey (
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78362-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="78362-108">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="78362-109">[w] Nazwa kontenera klucza zawierającego parę kluczy publicznych/prywatnych.</span><span class="sxs-lookup"><span data-stu-id="78362-109">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="78362-110">Jeśli `pbKeyBlob` wartość `szKeyContainer` null jest zerowa, należy określić prawidłowy kontener w ramach usługi CSP.</span><span class="sxs-lookup"><span data-stu-id="78362-110">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="78362-111">W takim `StrongNameGetPublicKey` przypadku wyodrębnia klucz publiczny z pary kluczy przechowywanych w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="78362-111">In this case, `StrongNameGetPublicKey` extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="78362-112">Jeśli `pbKeyBlob` nie ma wartości null, przyjmuje się, że para kluczy znajduje się w głównym obiekcie binarnym (BLOB).</span><span class="sxs-lookup"><span data-stu-id="78362-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="78362-113">Klucze muszą być 1024-bitowe klucze podpisywania Rivest-Shamir-Adleman (RSA).</span><span class="sxs-lookup"><span data-stu-id="78362-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="78362-114">Żadne inne typy kluczy są obecnie obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="78362-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="78362-115">[w] Wskaźnik do pary kluczy publicznych/prywatnych.</span><span class="sxs-lookup"><span data-stu-id="78362-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="78362-116">Ta para jest w formacie utworzonym `CryptExportKey` przez funkcję Win32.</span><span class="sxs-lookup"><span data-stu-id="78362-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="78362-117">Jeśli `pbKeyBlob` ma wartość null, `szKeyContainer` przyjmuje się, że kontener kluczy określony przez zawiera parę kluczy.</span><span class="sxs-lookup"><span data-stu-id="78362-117">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="78362-118">[w] Rozmiar w bajtach `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="78362-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="78362-119">[na zewnątrz] Zwrócony obiekt BLOB klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="78362-119">[out] The returned public key BLOB.</span></span> <span data-ttu-id="78362-120">Parametr `ppbPublicKeyBlob` jest przydzielany przez środowisko uruchomieniowe języka wspólnego i zwracany do wywołującego.</span><span class="sxs-lookup"><span data-stu-id="78362-120">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="78362-121">Wywołujący musi zwolnić pamięć przy użyciu [Funkcji StrongNameFreeBuffer.](strongnamefreebuffer-function.md)</span><span class="sxs-lookup"><span data-stu-id="78362-121">The caller must free the memory by using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="78362-122">[na zewnątrz] Rozmiar zwracanego obiektu BLOB klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="78362-122">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="78362-123">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="78362-123">Return Value</span></span>  
 <span data-ttu-id="78362-124">`true`po pomyślnym zakończeniu; w `false`przeciwnym razie , .</span><span class="sxs-lookup"><span data-stu-id="78362-124">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78362-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="78362-125">Remarks</span></span>  
 <span data-ttu-id="78362-126">Klucz publiczny znajduje się w [strukturze PublicKeyBlob.](publickeyblob-structure.md)</span><span class="sxs-lookup"><span data-stu-id="78362-126">The public key is contained in a [PublicKeyBlob](publickeyblob-structure.md) structure.</span></span>  
  
 <span data-ttu-id="78362-127">Jeśli `StrongNameGetPublicKey` funkcja nie zakończy się pomyślnie, wywołaj funkcję [StrongNameErrorInfo,](strongnameerrorinfo-function.md) aby pobrać ostatni wygenerowany błąd.</span><span class="sxs-lookup"><span data-stu-id="78362-127">If the `StrongNameGetPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78362-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="78362-128">Requirements</span></span>  
 <span data-ttu-id="78362-129">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78362-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78362-130">**Nagłówek:** StrongName.h (Nazwa siła)-h</span><span class="sxs-lookup"><span data-stu-id="78362-130">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="78362-131">**Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="78362-131">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="78362-132">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78362-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78362-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="78362-133">See also</span></span>

- [<span data-ttu-id="78362-134">StrongNameGetPublicKey, metoda</span><span class="sxs-lookup"><span data-stu-id="78362-134">StrongNameGetPublicKey Method</span></span>](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="78362-135">StrongNameTokenFromPublicKey, metoda</span><span class="sxs-lookup"><span data-stu-id="78362-135">StrongNameTokenFromPublicKey Method</span></span>](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="78362-136">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="78362-136">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="78362-137">PublicKeyBlob — Struktura</span><span class="sxs-lookup"><span data-stu-id="78362-137">PublicKeyBlob Structure</span></span>](publickeyblob-structure.md)
