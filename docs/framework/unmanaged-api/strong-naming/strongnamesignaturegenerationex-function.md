---
title: StrongNameSignatureGenerationEx — Funkcja
ms.date: 03/30/2017
api_name:
- StrongNameSignatureGenerationEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureGenerationEx
helpviewer_keywords:
- StrongNameSignatureGenerationEx function [.NET Framework strong naming]
ms.assetid: 9a75469e-aa49-4e32-ad48-3bafd5202f09
topic_type:
- apiref
ms.openlocfilehash: e8f63a6379af8f2b7b88c511840622d49d65d587
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141575"
---
# <a name="strongnamesignaturegenerationex-function"></a><span data-ttu-id="193fe-102">StrongNameSignatureGenerationEx — Funkcja</span><span class="sxs-lookup"><span data-stu-id="193fe-102">StrongNameSignatureGenerationEx Function</span></span>
<span data-ttu-id="193fe-103">Generuje podpis silnej nazwy dla określonego zestawu, zgodnie z określonymi flagami.</span><span class="sxs-lookup"><span data-stu-id="193fe-103">Generates a strong name signature for the specified assembly, according to the specified flags.</span></span>  
  
 <span data-ttu-id="193fe-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="193fe-104">This function has been deprecated.</span></span> <span data-ttu-id="193fe-105">Zamiast tego użyj metody [ICLRStrongName:: StrongNameSignatureGenerationEx —](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="193fe-105">Use the [ICLRStrongName::StrongNameSignatureGenerationEx](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="193fe-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="193fe-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureGenerationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob,  
    [in]  DWORD     dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="193fe-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="193fe-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="193fe-108">podczas Ścieżka do pliku zawierającego manifest zestawu, dla którego zostanie wygenerowany podpis silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="193fe-108">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="193fe-109">podczas Nazwa kontenera kluczy, który zawiera parę kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="193fe-109">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="193fe-110">Jeśli `pbKeyBlob` ma wartość null, `wszKeyContainer` musi określić prawidłowego kontenera w ramach dostawcy usług kryptograficznych (CSP).</span><span class="sxs-lookup"><span data-stu-id="193fe-110">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="193fe-111">W takim przypadku para kluczy przechowywana w kontenerze jest używana do podpisania pliku.</span><span class="sxs-lookup"><span data-stu-id="193fe-111">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="193fe-112">Jeśli `pbKeyBlob` nie ma wartości null, przyjmuje się, że para kluczy jest zawarta w kluczowym dużym obiekcie binarnym (BLOB).</span><span class="sxs-lookup"><span data-stu-id="193fe-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="193fe-113">podczas Wskaźnik do pary kluczy publicznych/prywatnych.</span><span class="sxs-lookup"><span data-stu-id="193fe-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="193fe-114">Ta para jest w formacie utworzonym przez funkcję `CryptExportKey` Win32.</span><span class="sxs-lookup"><span data-stu-id="193fe-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="193fe-115">Jeśli `pbKeyBlob` ma wartość null, założono, że kontener kluczy określony przez `wszKeyContainer` zostanie zawierający parę kluczy.</span><span class="sxs-lookup"><span data-stu-id="193fe-115">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="193fe-116">podczas Rozmiar w bajtach `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="193fe-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="193fe-117">określoną Wskaźnik do lokalizacji, do której aparat plików wykonywalnych języka wspólnego zwraca sygnaturę.</span><span class="sxs-lookup"><span data-stu-id="193fe-117">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="193fe-118">Jeśli `ppbSignatureBlob` ma wartość null, środowisko uruchomieniowe zapisuje podpis w pliku określonym przez `wszFilePath`.</span><span class="sxs-lookup"><span data-stu-id="193fe-118">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="193fe-119">Jeśli `ppbSignatureBlob` nie ma wartości null, środowisko uruchomieniowe języka wspólnego przydziela miejsce do zwrócenia sygnatury.</span><span class="sxs-lookup"><span data-stu-id="193fe-119">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="193fe-120">Obiekt wywołujący musi zwolnić to miejsce przy użyciu funkcji [StrongNameFreeBuffer —](strongnamefreebuffer-function.md) .</span><span class="sxs-lookup"><span data-stu-id="193fe-120">The caller must free this space using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="193fe-121">określoną Rozmiar zwróconej sygnatury w bajtach.</span><span class="sxs-lookup"><span data-stu-id="193fe-121">[out] The size, in bytes, of the returned signature.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="193fe-122">podczas Co najmniej jedna z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="193fe-122">[in] One or more of the following values:</span></span>  
  
- <span data-ttu-id="193fe-123">`SN_SIGN_ALL_FILES` (0x00000001) — Oblicz ponownie wszystkie skróty dla połączonych modułów.</span><span class="sxs-lookup"><span data-stu-id="193fe-123">`SN_SIGN_ALL_FILES` (0x00000001) - Recompute all hashes for linked modules.</span></span>  
  
- <span data-ttu-id="193fe-124">`SN_TEST_SIGN` (0x00000002) — Przetestuj i podpisz zestaw.</span><span class="sxs-lookup"><span data-stu-id="193fe-124">`SN_TEST_SIGN` (0x00000002) - Test-sign the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="193fe-125">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="193fe-125">Return Value</span></span>  
 <span data-ttu-id="193fe-126">`true` po pomyślnym zakończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="193fe-126">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="193fe-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="193fe-127">Remarks</span></span>  
 <span data-ttu-id="193fe-128">Określ wartość null dla `wszFilePath`, aby obliczyć rozmiar podpisu bez tworzenia podpisu.</span><span class="sxs-lookup"><span data-stu-id="193fe-128">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="193fe-129">Podpis może być przechowywany bezpośrednio w pliku lub zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="193fe-129">The signature can be either stored directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="193fe-130">Jeśli `SN_SIGN_ALL_FILES` jest określony, ale klucz publiczny nie jest uwzględniony (zarówno `pbKeyBlob`, jak i `wszFilePath` mają wartość null), skróty dla połączonych modułów są ponownie obliczane, ale zestaw nie został jeszcze podpisany.</span><span class="sxs-lookup"><span data-stu-id="193fe-130">If `SN_SIGN_ALL_FILES` is specified but a public key is not included (both `pbKeyBlob` and `wszFilePath` are null), hashes for linked modules are recomputed, but the assembly is not re-signed.</span></span>  
  
 <span data-ttu-id="193fe-131">Jeśli określono `SN_TEST_SIGN`, nagłówek środowiska uruchomieniowego języka wspólnego nie zostanie zmodyfikowany w celu wskazania, że zestaw jest podpisany przy użyciu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="193fe-131">If `SN_TEST_SIGN` is specified, the common language runtime header is not modified to indicate that the assembly is signed with a strong name.</span></span>  
  
 <span data-ttu-id="193fe-132">Jeśli funkcja `StrongNameSignatureGenerationEx` nie zakończy się pomyślnie, wywołaj funkcję [StrongNameErrorInfo —](strongnameerrorinfo-function.md) w celu pobrania ostatniego wygenerowanego błędu.</span><span class="sxs-lookup"><span data-stu-id="193fe-132">If the `StrongNameSignatureGenerationEx` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="193fe-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="193fe-133">Requirements</span></span>  
 <span data-ttu-id="193fe-134">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="193fe-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="193fe-135">**Nagłówek:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="193fe-135">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="193fe-136">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="193fe-136">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="193fe-137">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="193fe-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="193fe-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="193fe-138">See also</span></span>

- [<span data-ttu-id="193fe-139">StrongNameSignatureGenerationEx, metoda</span><span class="sxs-lookup"><span data-stu-id="193fe-139">StrongNameSignatureGenerationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="193fe-140">StrongNameSignatureGeneration, metoda</span><span class="sxs-lookup"><span data-stu-id="193fe-140">StrongNameSignatureGeneration Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="193fe-141">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="193fe-141">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
