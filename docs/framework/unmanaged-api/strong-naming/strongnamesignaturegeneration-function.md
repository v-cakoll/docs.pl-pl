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
ms.openlocfilehash: 9ab6fcb64e4654302e411d4dcc587df2e0bf1dc1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125192"
---
# <a name="strongnamesignaturegeneration-function"></a><span data-ttu-id="4b938-102">StrongNameSignatureGeneration — Funkcja</span><span class="sxs-lookup"><span data-stu-id="4b938-102">StrongNameSignatureGeneration Function</span></span>
<span data-ttu-id="4b938-103">Generuje podpis silnej nazwy dla określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="4b938-103">Generates a strong name signature for the specified assembly.</span></span>  
  
 <span data-ttu-id="4b938-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="4b938-104">This function has been deprecated.</span></span> <span data-ttu-id="4b938-105">Zamiast tego użyj metody [ICLRStrongName:: StrongNameSignatureGeneration —](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4b938-105">Use the [ICLRStrongName::StrongNameSignatureGeneration](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b938-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="4b938-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="4b938-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="4b938-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="4b938-108">podczas Ścieżka do pliku zawierającego manifest zestawu, dla którego zostanie wygenerowany podpis silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="4b938-108">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="4b938-109">podczas Nazwa kontenera kluczy, który zawiera parę kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="4b938-109">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="4b938-110">Jeśli `pbKeyBlob` ma wartość null, `wszKeyContainer` musi określić prawidłowego kontenera w ramach dostawcy usług kryptograficznych (CSP).</span><span class="sxs-lookup"><span data-stu-id="4b938-110">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="4b938-111">W takim przypadku para kluczy przechowywana w kontenerze jest używana do podpisania pliku.</span><span class="sxs-lookup"><span data-stu-id="4b938-111">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="4b938-112">Jeśli `pbKeyBlob` nie ma wartości null, przyjmuje się, że para kluczy jest zawarta w kluczowym dużym obiekcie binarnym (BLOB).</span><span class="sxs-lookup"><span data-stu-id="4b938-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="4b938-113">Klucze muszą być 1024-bitowe Rivest-Shamir-Adleman (RSA) kluczy podpisywania.</span><span class="sxs-lookup"><span data-stu-id="4b938-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="4b938-114">W tej chwili nie są obsługiwane żadne inne typy kluczy.</span><span class="sxs-lookup"><span data-stu-id="4b938-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="4b938-115">podczas Wskaźnik do pary kluczy publicznych/prywatnych.</span><span class="sxs-lookup"><span data-stu-id="4b938-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="4b938-116">Ta para jest w formacie utworzonym przez funkcję `CryptExportKey` Win32.</span><span class="sxs-lookup"><span data-stu-id="4b938-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="4b938-117">Jeśli `pbKeyBlob` ma wartość null, założono, że kontener kluczy określony przez `wszKeyContainer` zostanie zawierający parę kluczy.</span><span class="sxs-lookup"><span data-stu-id="4b938-117">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="4b938-118">podczas Rozmiar w bajtach `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="4b938-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="4b938-119">określoną Wskaźnik do lokalizacji, do której aparat plików wykonywalnych języka wspólnego zwraca sygnaturę.</span><span class="sxs-lookup"><span data-stu-id="4b938-119">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="4b938-120">Jeśli `ppbSignatureBlob` ma wartość null, środowisko uruchomieniowe zapisuje podpis w pliku określonym przez `wszFilePath`.</span><span class="sxs-lookup"><span data-stu-id="4b938-120">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="4b938-121">Jeśli `ppbSignatureBlob` nie ma wartości null, środowisko uruchomieniowe języka wspólnego przydziela miejsce do zwrócenia sygnatury.</span><span class="sxs-lookup"><span data-stu-id="4b938-121">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="4b938-122">Obiekt wywołujący musi zwolnić to miejsce przy użyciu funkcji [StrongNameFreeBuffer —](strongnamefreebuffer-function.md) .</span><span class="sxs-lookup"><span data-stu-id="4b938-122">The caller must free this space using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="4b938-123">określoną Rozmiar zwróconej sygnatury w bajtach.</span><span class="sxs-lookup"><span data-stu-id="4b938-123">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4b938-124">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4b938-124">Return Value</span></span>  
 <span data-ttu-id="4b938-125">`true` po pomyślnym zakończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="4b938-125">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b938-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4b938-126">Remarks</span></span>  
 <span data-ttu-id="4b938-127">Określ wartość null dla `wszFilePath`, aby obliczyć rozmiar podpisu bez tworzenia podpisu.</span><span class="sxs-lookup"><span data-stu-id="4b938-127">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="4b938-128">Podpis może być przechowywany bezpośrednio w pliku lub zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="4b938-128">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="4b938-129">Jeśli funkcja `StrongNameSignatureGeneration` nie zakończy się pomyślnie, wywołaj funkcję [StrongNameErrorInfo —](strongnameerrorinfo-function.md) w celu pobrania ostatniego wygenerowanego błędu.</span><span class="sxs-lookup"><span data-stu-id="4b938-129">If the `StrongNameSignatureGeneration` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b938-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4b938-130">Requirements</span></span>  
 <span data-ttu-id="4b938-131">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b938-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b938-132">**Nagłówek:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="4b938-132">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="4b938-133">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4b938-133">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4b938-134">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b938-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b938-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4b938-135">See also</span></span>

- [<span data-ttu-id="4b938-136">StrongNameSignatureGeneration, metoda</span><span class="sxs-lookup"><span data-stu-id="4b938-136">StrongNameSignatureGeneration Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="4b938-137">StrongNameSignatureGenerationEx, metoda</span><span class="sxs-lookup"><span data-stu-id="4b938-137">StrongNameSignatureGenerationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="4b938-138">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="4b938-138">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
