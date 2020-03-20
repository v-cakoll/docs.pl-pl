---
title: StrongNameSignatureGeneration — Funkcja
ms.date: 03/30/2017
api_name:
- StrongNameSignatureGeneration
api_location:
- mscoree.dll
- mscorsn.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureGeneration
helpviewer_keywords:
- StrongNameSignatureGeneration function [.NET Framework strong naming]
ms.assetid: 839b765c-3e41-44ce-bf1b-dc10453db18e
ms.openlocfilehash: d7f481e5c61ec65d2e7414bd47227866f3435028
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176906"
---
# <a name="strongnamesignaturegeneration-function"></a><span data-ttu-id="f3fef-102">StrongNameSignatureGeneration — Funkcja</span><span class="sxs-lookup"><span data-stu-id="f3fef-102">StrongNameSignatureGeneration Function</span></span>
<span data-ttu-id="f3fef-103">Generuje podpis silnej nazwy dla określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="f3fef-103">Generates a strong name signature for the specified assembly.</span></span>  
  
 <span data-ttu-id="f3fef-104">Ta funkcja została przestarzała.</span><span class="sxs-lookup"><span data-stu-id="f3fef-104">This function has been deprecated.</span></span> <span data-ttu-id="f3fef-105">Zamiast tego należy użyć metody [ICLRStrongName::StrongNameSignatureGeneration.](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)</span><span class="sxs-lookup"><span data-stu-id="f3fef-105">Use the [ICLRStrongName::StrongNameSignatureGeneration](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3fef-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="f3fef-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureGeneration (
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3fef-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="f3fef-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="f3fef-108">[w] Ścieżka do pliku, który zawiera manifest zestawu, dla którego zostanie wygenerowany podpis silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="f3fef-108">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="f3fef-109">[w] Nazwa kontenera klucza zawierającego parę kluczy publicznych/prywatnych.</span><span class="sxs-lookup"><span data-stu-id="f3fef-109">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="f3fef-110">Jeśli `pbKeyBlob` wartość `wszKeyContainer` null jest zerowa, należy określić prawidłowy kontener w ramach dostawcy usług kryptograficznych (CSP).</span><span class="sxs-lookup"><span data-stu-id="f3fef-110">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="f3fef-111">W takim przypadku para kluczy przechowywana w kontenerze jest używana do podpisywania pliku.</span><span class="sxs-lookup"><span data-stu-id="f3fef-111">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="f3fef-112">Jeśli `pbKeyBlob` nie ma wartości null, przyjmuje się, że para kluczy znajduje się w głównym obiekcie binarnym (BLOB).</span><span class="sxs-lookup"><span data-stu-id="f3fef-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="f3fef-113">Klucze muszą być 1024-bitowe klucze podpisywania Rivest-Shamir-Adleman (RSA).</span><span class="sxs-lookup"><span data-stu-id="f3fef-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="f3fef-114">Żadne inne typy kluczy są obecnie obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="f3fef-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="f3fef-115">[w] Wskaźnik do pary kluczy publicznych/prywatnych.</span><span class="sxs-lookup"><span data-stu-id="f3fef-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="f3fef-116">Ta para jest w formacie utworzonym `CryptExportKey` przez funkcję Win32.</span><span class="sxs-lookup"><span data-stu-id="f3fef-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="f3fef-117">Jeśli `pbKeyBlob` ma wartość null, `wszKeyContainer` przyjmuje się, że kontener kluczy określony przez zawiera parę kluczy.</span><span class="sxs-lookup"><span data-stu-id="f3fef-117">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="f3fef-118">[w] Rozmiar w bajtach `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="f3fef-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="f3fef-119">[na zewnątrz] Wskaźnik do lokalizacji, do której środowisko uruchomieniowe języka wspólnego zwraca podpis.</span><span class="sxs-lookup"><span data-stu-id="f3fef-119">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="f3fef-120">Jeśli `ppbSignatureBlob` wartość null ma wartość null, środowisko `wszFilePath`wykonawcze przechowuje podpis w pliku określonym przez program .</span><span class="sxs-lookup"><span data-stu-id="f3fef-120">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="f3fef-121">Jeśli `ppbSignatureBlob` nie jest null, środowisko uruchomieniowe języka wspólnego przydziela miejsce, w którym do zwrócenia podpisu.</span><span class="sxs-lookup"><span data-stu-id="f3fef-121">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="f3fef-122">Wywołujący musi zwolnić to miejsce za pomocą [Funkcji StrongNameFreeBuffer.](strongnamefreebuffer-function.md)</span><span class="sxs-lookup"><span data-stu-id="f3fef-122">The caller must free this space using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="f3fef-123">[na zewnątrz] Rozmiar w bajtach zwróconego podpisu.</span><span class="sxs-lookup"><span data-stu-id="f3fef-123">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f3fef-124">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f3fef-124">Return Value</span></span>  
 <span data-ttu-id="f3fef-125">`true`po pomyślnym zakończeniu; w `false`przeciwnym razie , .</span><span class="sxs-lookup"><span data-stu-id="f3fef-125">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3fef-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f3fef-126">Remarks</span></span>  
 <span data-ttu-id="f3fef-127">Określ `wszFilePath` wartość null, aby obliczyć rozmiar podpisu bez tworzenia podpisu.</span><span class="sxs-lookup"><span data-stu-id="f3fef-127">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="f3fef-128">Podpis może być przechowywany bezpośrednio w pliku lub zwrócony do wywołującego.</span><span class="sxs-lookup"><span data-stu-id="f3fef-128">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="f3fef-129">Jeśli `StrongNameSignatureGeneration` funkcja nie zakończy się pomyślnie, wywołaj funkcję [StrongNameErrorInfo,](strongnameerrorinfo-function.md) aby pobrać ostatni wygenerowany błąd.</span><span class="sxs-lookup"><span data-stu-id="f3fef-129">If the `StrongNameSignatureGeneration` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3fef-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f3fef-130">Requirements</span></span>  
 <span data-ttu-id="f3fef-131">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3fef-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3fef-132">**Nagłówek:** StrongName.h (Nazwa siła)-h</span><span class="sxs-lookup"><span data-stu-id="f3fef-132">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="f3fef-133">**Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f3fef-133">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f3fef-134">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3fef-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3fef-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f3fef-135">See also</span></span>

- [<span data-ttu-id="f3fef-136">StrongNameSignatureGeneration, metoda</span><span class="sxs-lookup"><span data-stu-id="f3fef-136">StrongNameSignatureGeneration Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="f3fef-137">StrongNameSignatureGenerationEx, metoda</span><span class="sxs-lookup"><span data-stu-id="f3fef-137">StrongNameSignatureGenerationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="f3fef-138">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="f3fef-138">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
