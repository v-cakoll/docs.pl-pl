---
title: ICLRStrongName::StrongNameSignatureGenerationEx — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureGenerationEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureGenerationEx
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureGenerationEx method [.NET Framework hosting]
- StrongNameSignatureGenerationEx method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: c3f34584-c6e2-41fd-bb44-e44da8546309
topic_type:
- apiref
ms.openlocfilehash: 3529eceb179cc4b08d39f83d97d001a16e716918
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763062"
---
# <a name="iclrstrongnamestrongnamesignaturegenerationex-method"></a><span data-ttu-id="0d5ba-102">ICLRStrongName::StrongNameSignatureGenerationEx — Metoda</span><span class="sxs-lookup"><span data-stu-id="0d5ba-102">ICLRStrongName::StrongNameSignatureGenerationEx Method</span></span>
<span data-ttu-id="0d5ba-103">Generuje podpis silnej nazwy dla określonego zestawu, zgodnie z określonymi flagami.</span><span class="sxs-lookup"><span data-stu-id="0d5ba-103">Generates a strong name signature for the specified assembly, according to the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d5ba-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0d5ba-104">Syntax</span></span>  
  
```cpp
HRESULT StrongNameSignatureGenerationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob,  
    [in]  DWORD     dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d5ba-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0d5ba-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="0d5ba-106">podczas Ścieżka do pliku zawierającego manifest zestawu, dla którego zostanie wygenerowany podpis silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="0d5ba-106">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="0d5ba-107">podczas Nazwa kontenera kluczy, który zawiera parę kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="0d5ba-107">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="0d5ba-108">Jeśli `pbKeyBlob` ma wartość null, `wszKeyContainer` należy określić prawidłowy kontener w ramach dostawcy usług kryptograficznych (CSP).</span><span class="sxs-lookup"><span data-stu-id="0d5ba-108">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="0d5ba-109">W takim przypadku para kluczy przechowywana w kontenerze jest używana do podpisania pliku.</span><span class="sxs-lookup"><span data-stu-id="0d5ba-109">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="0d5ba-110">Jeśli `pbKeyBlob` wartość nie jest równa null, przyjmuje się, że para kluczy jest zawarta w kluczowym dużym obiekcie binarnym (BLOB).</span><span class="sxs-lookup"><span data-stu-id="0d5ba-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="0d5ba-111">podczas Wskaźnik do pary kluczy publicznych/prywatnych.</span><span class="sxs-lookup"><span data-stu-id="0d5ba-111">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="0d5ba-112">Ta para jest w formacie utworzonym przez funkcję Win32 `CryptExportKey` .</span><span class="sxs-lookup"><span data-stu-id="0d5ba-112">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="0d5ba-113">Jeśli `pbKeyBlob` ma wartość null, zakłada się, że kontener kluczy określony przez `wszKeyContainer` ma zawierać parę kluczy.</span><span class="sxs-lookup"><span data-stu-id="0d5ba-113">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="0d5ba-114">podczas Rozmiar, w bajtach, z `pbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="0d5ba-114">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="0d5ba-115">określoną Wskaźnik do lokalizacji, do której aparat plików wykonywalnych języka wspólnego zwraca sygnaturę.</span><span class="sxs-lookup"><span data-stu-id="0d5ba-115">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="0d5ba-116">Jeśli `ppbSignatureBlob` ma wartość null, środowisko uruchomieniowe zapisuje podpis w pliku określonym przez `wszFilePath` .</span><span class="sxs-lookup"><span data-stu-id="0d5ba-116">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="0d5ba-117">Jeśli `ppbSignatureBlob` wartość nie jest równa null, środowisko uruchomieniowe języka wspólnego przydziela miejsce do zwrócenia sygnatury.</span><span class="sxs-lookup"><span data-stu-id="0d5ba-117">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="0d5ba-118">Obiekt wywołujący musi zwolnić to miejsce przy użyciu metody [ICLRStrongName:: StrongNameFreeBuffer —](iclrstrongname-strongnamefreebuffer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="0d5ba-118">The caller must free this space using the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="0d5ba-119">określoną Rozmiar zwróconej sygnatury w bajtach.</span><span class="sxs-lookup"><span data-stu-id="0d5ba-119">[out] The size, in bytes, of the returned signature.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="0d5ba-120">podczas Co najmniej jedna z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="0d5ba-120">[in] One or more of the following values:</span></span>  
  
- <span data-ttu-id="0d5ba-121">`SN_SIGN_ALL_FILES`(0x00000001) — Oblicz ponownie wszystkie skróty dla połączonych modułów.</span><span class="sxs-lookup"><span data-stu-id="0d5ba-121">`SN_SIGN_ALL_FILES` (0x00000001) - Recompute all hashes for linked modules.</span></span>  
  
- <span data-ttu-id="0d5ba-122">`SN_TEST_SIGN`(0x00000002)-podpisz zestaw.</span><span class="sxs-lookup"><span data-stu-id="0d5ba-122">`SN_TEST_SIGN` (0x00000002) - Test-sign the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0d5ba-123">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0d5ba-123">Return Value</span></span>  
 <span data-ttu-id="0d5ba-124">`S_OK`Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT wskazująca niepowodzenie (zobacz [typowe wartości HRESULT](/windows/win32/seccrypto/common-hresult-values) dla listy).</span><span class="sxs-lookup"><span data-stu-id="0d5ba-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d5ba-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0d5ba-125">Remarks</span></span>  
 <span data-ttu-id="0d5ba-126">Określ wartość null dla `wszFilePath` , aby obliczyć rozmiar podpisu bez tworzenia podpisu.</span><span class="sxs-lookup"><span data-stu-id="0d5ba-126">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="0d5ba-127">Podpis może być przechowywany bezpośrednio w pliku lub zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="0d5ba-127">The signature can be either stored directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="0d5ba-128">Jeśli `SN_SIGN_ALL_FILES` jest określony, ale klucz publiczny nie jest uwzględniony (jednocześnie `pbKeyBlob` i ma `wszFilePath` wartość null), skróty dla połączonych modułów są ponownie obliczane, ale zestaw nie jest jeszcze podpisany.</span><span class="sxs-lookup"><span data-stu-id="0d5ba-128">If `SN_SIGN_ALL_FILES` is specified but a public key is not included (both `pbKeyBlob` and `wszFilePath` are null), hashes for linked modules are recomputed, but the assembly is not re-signed.</span></span>  
  
 <span data-ttu-id="0d5ba-129">Jeśli `SN_TEST_SIGN` jest określony, nagłówek środowiska uruchomieniowego języka wspólnego nie zostanie zmodyfikowany w celu wskazania, że zestaw jest podpisany silną nazwą.</span><span class="sxs-lookup"><span data-stu-id="0d5ba-129">If `SN_TEST_SIGN` is specified, the common language runtime header is not modified to indicate that the assembly is signed with a strong name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d5ba-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0d5ba-130">Requirements</span></span>  
 <span data-ttu-id="0d5ba-131">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d5ba-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d5ba-132">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="0d5ba-132">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="0d5ba-133">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0d5ba-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0d5ba-134">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d5ba-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d5ba-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0d5ba-135">See also</span></span>

- [<span data-ttu-id="0d5ba-136">StrongNameSignatureGeneration, metoda</span><span class="sxs-lookup"><span data-stu-id="0d5ba-136">StrongNameSignatureGeneration Method</span></span>](iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="0d5ba-137">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="0d5ba-137">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
