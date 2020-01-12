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
ms.openlocfilehash: 34614fe24127787a113bab4975a50f1c8d2d875e
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899499"
---
# <a name="iclrstrongnamestrongnamesignaturegenerationex-method"></a><span data-ttu-id="2479f-102">ICLRStrongName::StrongNameSignatureGenerationEx — Metoda</span><span class="sxs-lookup"><span data-stu-id="2479f-102">ICLRStrongName::StrongNameSignatureGenerationEx Method</span></span>
<span data-ttu-id="2479f-103">Generuje podpis silnej nazwy dla określonego zestawu, zgodnie z określonymi flagami.</span><span class="sxs-lookup"><span data-stu-id="2479f-103">Generates a strong name signature for the specified assembly, according to the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2479f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2479f-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="2479f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2479f-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="2479f-106">podczas Ścieżka do pliku zawierającego manifest zestawu, dla którego zostanie wygenerowany podpis silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="2479f-106">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="2479f-107">podczas Nazwa kontenera kluczy, który zawiera parę kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="2479f-107">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="2479f-108">Jeśli `pbKeyBlob` ma wartość null, `wszKeyContainer` musi określić prawidłowego kontenera w ramach dostawcy usług kryptograficznych (CSP).</span><span class="sxs-lookup"><span data-stu-id="2479f-108">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="2479f-109">W takim przypadku para kluczy przechowywana w kontenerze jest używana do podpisania pliku.</span><span class="sxs-lookup"><span data-stu-id="2479f-109">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="2479f-110">Jeśli `pbKeyBlob` nie ma wartości null, przyjmuje się, że para kluczy jest zawarta w kluczowym dużym obiekcie binarnym (BLOB).</span><span class="sxs-lookup"><span data-stu-id="2479f-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="2479f-111">podczas Wskaźnik do pary kluczy publicznych/prywatnych.</span><span class="sxs-lookup"><span data-stu-id="2479f-111">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="2479f-112">Ta para jest w formacie utworzonym przez funkcję `CryptExportKey` Win32.</span><span class="sxs-lookup"><span data-stu-id="2479f-112">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="2479f-113">Jeśli `pbKeyBlob` ma wartość null, założono, że kontener kluczy określony przez `wszKeyContainer` zostanie zawierający parę kluczy.</span><span class="sxs-lookup"><span data-stu-id="2479f-113">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="2479f-114">podczas Rozmiar w bajtach `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="2479f-114">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="2479f-115">określoną Wskaźnik do lokalizacji, do której aparat plików wykonywalnych języka wspólnego zwraca sygnaturę.</span><span class="sxs-lookup"><span data-stu-id="2479f-115">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="2479f-116">Jeśli `ppbSignatureBlob` ma wartość null, środowisko uruchomieniowe zapisuje podpis w pliku określonym przez `wszFilePath`.</span><span class="sxs-lookup"><span data-stu-id="2479f-116">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="2479f-117">Jeśli `ppbSignatureBlob` nie ma wartości null, środowisko uruchomieniowe języka wspólnego przydziela miejsce do zwrócenia sygnatury.</span><span class="sxs-lookup"><span data-stu-id="2479f-117">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="2479f-118">Obiekt wywołujący musi zwolnić to miejsce przy użyciu metody [ICLRStrongName:: StrongNameFreeBuffer —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2479f-118">The caller must free this space using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="2479f-119">określoną Rozmiar zwróconej sygnatury w bajtach.</span><span class="sxs-lookup"><span data-stu-id="2479f-119">[out] The size, in bytes, of the returned signature.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="2479f-120">podczas Co najmniej jedna z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="2479f-120">[in] One or more of the following values:</span></span>  
  
- <span data-ttu-id="2479f-121">`SN_SIGN_ALL_FILES` (0x00000001) — Oblicz ponownie wszystkie skróty dla połączonych modułów.</span><span class="sxs-lookup"><span data-stu-id="2479f-121">`SN_SIGN_ALL_FILES` (0x00000001) - Recompute all hashes for linked modules.</span></span>  
  
- <span data-ttu-id="2479f-122">`SN_TEST_SIGN` (0x00000002) — Przetestuj i podpisz zestaw.</span><span class="sxs-lookup"><span data-stu-id="2479f-122">`SN_TEST_SIGN` (0x00000002) - Test-sign the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2479f-123">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="2479f-123">Return Value</span></span>  
 <span data-ttu-id="2479f-124">`S_OK`, jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT wskazująca niepowodzenie (zobacz [typowe wartości HRESULT](/windows/win32/seccrypto/common-hresult-values) dla listy).</span><span class="sxs-lookup"><span data-stu-id="2479f-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2479f-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2479f-125">Remarks</span></span>  
 <span data-ttu-id="2479f-126">Określ wartość null dla `wszFilePath`, aby obliczyć rozmiar podpisu bez tworzenia podpisu.</span><span class="sxs-lookup"><span data-stu-id="2479f-126">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="2479f-127">Podpis może być przechowywany bezpośrednio w pliku lub zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="2479f-127">The signature can be either stored directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="2479f-128">Jeśli `SN_SIGN_ALL_FILES` jest określony, ale klucz publiczny nie jest uwzględniony (zarówno `pbKeyBlob`, jak i `wszFilePath` mają wartość null), skróty dla połączonych modułów są ponownie obliczane, ale zestaw nie został jeszcze podpisany.</span><span class="sxs-lookup"><span data-stu-id="2479f-128">If `SN_SIGN_ALL_FILES` is specified but a public key is not included (both `pbKeyBlob` and `wszFilePath` are null), hashes for linked modules are recomputed, but the assembly is not re-signed.</span></span>  
  
 <span data-ttu-id="2479f-129">Jeśli określono `SN_TEST_SIGN`, nagłówek środowiska uruchomieniowego języka wspólnego nie zostanie zmodyfikowany w celu wskazania, że zestaw jest podpisany przy użyciu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="2479f-129">If `SN_TEST_SIGN` is specified, the common language runtime header is not modified to indicate that the assembly is signed with a strong name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2479f-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2479f-130">Requirements</span></span>  
 <span data-ttu-id="2479f-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2479f-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2479f-132">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="2479f-132">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="2479f-133">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2479f-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2479f-134">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2479f-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2479f-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2479f-135">See also</span></span>

- [<span data-ttu-id="2479f-136">StrongNameSignatureGeneration, metoda</span><span class="sxs-lookup"><span data-stu-id="2479f-136">StrongNameSignatureGeneration Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="2479f-137">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="2479f-137">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
