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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 81f1eb4236bab72caf4421342e1f54d6d2f32607
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43536686"
---
# <a name="iclrstrongnamestrongnamesignaturegenerationex-method"></a><span data-ttu-id="7f55d-102">ICLRStrongName::StrongNameSignatureGenerationEx — Metoda</span><span class="sxs-lookup"><span data-stu-id="7f55d-102">ICLRStrongName::StrongNameSignatureGenerationEx Method</span></span>
<span data-ttu-id="7f55d-103">Generuje podpisu silnej nazwy dla określonego zestawu, zgodnie z określone flagi.</span><span class="sxs-lookup"><span data-stu-id="7f55d-103">Generates a strong name signature for the specified assembly, according to the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f55d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7f55d-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="7f55d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7f55d-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="7f55d-106">[in] Ścieżka do pliku, który zawiera manifest zestawu, dla którego zostanie wygenerowany podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="7f55d-106">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="7f55d-107">[in] Nazwa kontenera kluczy, który zawiera pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="7f55d-107">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="7f55d-108">Jeśli `pbKeyBlob` ma wartość null, `wszKeyContainer` należy określić prawidłowy kontener w ramach dostawcy usług kryptograficznych (CSP).</span><span class="sxs-lookup"><span data-stu-id="7f55d-108">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="7f55d-109">W tym przypadku parę kluczy, przechowywane w kontenerze służy do podpisywania pliku.</span><span class="sxs-lookup"><span data-stu-id="7f55d-109">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="7f55d-110">Jeśli `pbKeyBlob` nie ma wartości null, zakłada, że pary kluczy muszą być zawarte w kluczowych duży obiekt binarny (BLOB).</span><span class="sxs-lookup"><span data-stu-id="7f55d-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="7f55d-111">[in] Wskaźnik do pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="7f55d-111">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="7f55d-112">Ta para jest w formacie utworzone przez Win32 `CryptExportKey` funkcji.</span><span class="sxs-lookup"><span data-stu-id="7f55d-112">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="7f55d-113">Jeśli `pbKeyBlob` jest null, kontenerze klucza określonym przez `wszKeyContainer` założono, że zawiera pary kluczy.</span><span class="sxs-lookup"><span data-stu-id="7f55d-113">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="7f55d-114">[in] Rozmiar w bajtach z `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="7f55d-114">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="7f55d-115">[out] Wskaźnik do lokalizacji, do której środowisko uruchomieniowe języka wspólnego zwraca podpis.</span><span class="sxs-lookup"><span data-stu-id="7f55d-115">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="7f55d-116">Jeśli `ppbSignatureBlob` jest wartość null, środowisko uruchomieniowe przechowuje podpisu w pliku określonym przez `wszFilePath`.</span><span class="sxs-lookup"><span data-stu-id="7f55d-116">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="7f55d-117">Jeśli `ppbSignatureBlob` jest inna niż null, środowisko uruchomieniowe języka wspólnego przydziela miejsce, w której ma zostać zwrócone podpis.</span><span class="sxs-lookup"><span data-stu-id="7f55d-117">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="7f55d-118">Obiekt wywołujący musi zwolnić tego miejsca przy użyciu [iclrstrongname::strongnamefreebuffer —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="7f55d-118">The caller must free this space using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="7f55d-119">[out] Rozmiar w bajtach sygnatury zwracanego.</span><span class="sxs-lookup"><span data-stu-id="7f55d-119">[out] The size, in bytes, of the returned signature.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="7f55d-120">[in] Jeden lub więcej z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="7f55d-120">[in] One or more of the following values:</span></span>  
  
-   <span data-ttu-id="7f55d-121">`SN_SIGN_ALL_FILES` (0x00000001) - ponownie obliczyć skrótów wszystkich modułów połączonych.</span><span class="sxs-lookup"><span data-stu-id="7f55d-121">`SN_SIGN_ALL_FILES` (0x00000001) - Recompute all hashes for linked modules.</span></span>  
  
-   <span data-ttu-id="7f55d-122">`SN_TEST_SIGN` (0x00000002) - test podpisanie zestawu.</span><span class="sxs-lookup"><span data-stu-id="7f55d-122">`SN_TEST_SIGN` (0x00000002) - Test-sign the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7f55d-123">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7f55d-123">Return Value</span></span>  
 <span data-ttu-id="7f55d-124">`S_OK` Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje błąd (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).</span><span class="sxs-lookup"><span data-stu-id="7f55d-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f55d-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7f55d-125">Remarks</span></span>  
 <span data-ttu-id="7f55d-126">Określ wartość null w przypadku `wszFilePath` do obliczania rozmiaru podpisu bez tworzenia podpisu.</span><span class="sxs-lookup"><span data-stu-id="7f55d-126">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="7f55d-127">Podpis mogą być przechowywane bezpośrednio w pliku albo zwracany do wywołującego.</span><span class="sxs-lookup"><span data-stu-id="7f55d-127">The signature can be either stored directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="7f55d-128">Jeśli `SN_SIGN_ALL_FILES` jest określony, ale klucz publiczny nie jest uwzględniony (zarówno `pbKeyBlob` i `wszFilePath` mają wartość null), skróty dla połączonych modułów są obliczane ponownie, ale zestaw nie jest ponownie podpisany.</span><span class="sxs-lookup"><span data-stu-id="7f55d-128">If `SN_SIGN_ALL_FILES` is specified but a public key is not included (both `pbKeyBlob` and `wszFilePath` are null), hashes for linked modules are recomputed, but the assembly is not re-signed.</span></span>  
  
 <span data-ttu-id="7f55d-129">Jeśli `SN_TEST_SIGN` określono typowego nagłówka środowiska uruchomieniowego języka nie jest modyfikowany w celu wskazania, że zestaw jest podpisany silną nazwą.</span><span class="sxs-lookup"><span data-stu-id="7f55d-129">If `SN_TEST_SIGN` is specified, the common language runtime header is not modified to indicate that the assembly is signed with a strong name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f55d-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7f55d-130">Requirements</span></span>  
 <span data-ttu-id="7f55d-131">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f55d-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f55d-132">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="7f55d-132">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7f55d-133">**Biblioteka:** dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7f55d-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7f55d-134">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f55d-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f55d-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7f55d-135">See Also</span></span>  
 [<span data-ttu-id="7f55d-136">StrongNameSignatureGeneration, metoda</span><span class="sxs-lookup"><span data-stu-id="7f55d-136">StrongNameSignatureGeneration Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)  
 [<span data-ttu-id="7f55d-137">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="7f55d-137">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
