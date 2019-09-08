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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 48cdd550e5d8c7c75a603d74456e99a066d5c599
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798969"
---
# <a name="strongnamesignaturegeneration-function"></a><span data-ttu-id="73908-102">StrongNameSignatureGeneration — Funkcja</span><span class="sxs-lookup"><span data-stu-id="73908-102">StrongNameSignatureGeneration Function</span></span>
<span data-ttu-id="73908-103">Generuje podpis silnej nazwy dla określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="73908-103">Generates a strong name signature for the specified assembly.</span></span>  
  
 <span data-ttu-id="73908-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="73908-104">This function has been deprecated.</span></span> <span data-ttu-id="73908-105">Zamiast tego użyj metody [ICLRStrongName:: StrongNameSignatureGeneration —](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md) .</span><span class="sxs-lookup"><span data-stu-id="73908-105">Use the [ICLRStrongName::StrongNameSignatureGeneration](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73908-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="73908-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="73908-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="73908-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="73908-108">podczas Ścieżka do pliku zawierającego manifest zestawu, dla którego zostanie wygenerowany podpis silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="73908-108">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="73908-109">podczas Nazwa kontenera kluczy, który zawiera parę kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="73908-109">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="73908-110">Jeśli `pbKeyBlob` ma wartość null `wszKeyContainer` , należy określić prawidłowy kontener w ramach dostawcy usług kryptograficznych (CSP).</span><span class="sxs-lookup"><span data-stu-id="73908-110">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="73908-111">W takim przypadku para kluczy przechowywana w kontenerze jest używana do podpisania pliku.</span><span class="sxs-lookup"><span data-stu-id="73908-111">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="73908-112">Jeśli `pbKeyBlob` wartość nie jest równa null, przyjmuje się, że para kluczy jest zawarta w kluczowym dużym obiekcie binarnym (BLOB).</span><span class="sxs-lookup"><span data-stu-id="73908-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="73908-113">Klucze muszą być 1024-bitowe Rivest-Shamir-Adleman (RSA) kluczy podpisywania.</span><span class="sxs-lookup"><span data-stu-id="73908-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="73908-114">W tej chwili nie są obsługiwane żadne inne typy kluczy.</span><span class="sxs-lookup"><span data-stu-id="73908-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="73908-115">podczas Wskaźnik do pary kluczy publicznych/prywatnych.</span><span class="sxs-lookup"><span data-stu-id="73908-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="73908-116">Ta para jest w formacie utworzonym przez funkcję Win32 `CryptExportKey` .</span><span class="sxs-lookup"><span data-stu-id="73908-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="73908-117">Jeśli `pbKeyBlob` ma wartość null, zakłada się, że `wszKeyContainer` kontener kluczy określony przez ma zawierać parę kluczy.</span><span class="sxs-lookup"><span data-stu-id="73908-117">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="73908-118">podczas Rozmiar, w bajtach, z `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="73908-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="73908-119">określoną Wskaźnik do lokalizacji, do której aparat plików wykonywalnych języka wspólnego zwraca sygnaturę.</span><span class="sxs-lookup"><span data-stu-id="73908-119">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="73908-120">Jeśli `ppbSignatureBlob` ma wartość null, środowisko uruchomieniowe zapisuje podpis w pliku określonym przez `wszFilePath`.</span><span class="sxs-lookup"><span data-stu-id="73908-120">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="73908-121">Jeśli `ppbSignatureBlob` wartość nie jest równa null, środowisko uruchomieniowe języka wspólnego przydziela miejsce do zwrócenia sygnatury.</span><span class="sxs-lookup"><span data-stu-id="73908-121">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="73908-122">Obiekt wywołujący musi zwolnić to miejsce przy użyciu funkcji [StrongNameFreeBuffer —](strongnamefreebuffer-function.md) .</span><span class="sxs-lookup"><span data-stu-id="73908-122">The caller must free this space using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="73908-123">określoną Rozmiar zwróconej sygnatury w bajtach.</span><span class="sxs-lookup"><span data-stu-id="73908-123">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="73908-124">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="73908-124">Return Value</span></span>  
 <span data-ttu-id="73908-125">`true`Po pomyślnym zakończeniu; w przeciwnym razie. `false`</span><span class="sxs-lookup"><span data-stu-id="73908-125">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73908-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="73908-126">Remarks</span></span>  
 <span data-ttu-id="73908-127">Określ wartość null `wszFilePath` dla, aby obliczyć rozmiar podpisu bez tworzenia podpisu.</span><span class="sxs-lookup"><span data-stu-id="73908-127">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="73908-128">Podpis może być przechowywany bezpośrednio w pliku lub zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="73908-128">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="73908-129">Jeśli funkcja nie zakończy się pomyślnie, wywołaj funkcję StrongNameErrorInfo — w celu pobrania ostatniego wygenerowanego błędu. [](strongnameerrorinfo-function.md) `StrongNameSignatureGeneration`</span><span class="sxs-lookup"><span data-stu-id="73908-129">If the `StrongNameSignatureGeneration` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73908-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="73908-130">Requirements</span></span>  
 <span data-ttu-id="73908-131">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73908-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73908-132">**Nagłówki** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="73908-132">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="73908-133">**Biblioteki** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="73908-133">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="73908-134">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73908-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73908-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="73908-135">See also</span></span>

- [<span data-ttu-id="73908-136">StrongNameSignatureGeneration, metoda</span><span class="sxs-lookup"><span data-stu-id="73908-136">StrongNameSignatureGeneration Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="73908-137">StrongNameSignatureGenerationEx, metoda</span><span class="sxs-lookup"><span data-stu-id="73908-137">StrongNameSignatureGenerationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="73908-138">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="73908-138">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
