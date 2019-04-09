---
title: ICLRStrongName::StrongNameSignatureGeneration — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureGeneration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureGeneration
helpviewer_keywords:
- StrongNameSignatureGeneration method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameSignatureGeneration method [.NET Framework hosting]
ms.assetid: 4cdb1284-947a-4ed4-94c1-c5ff5cdfce56
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 679afd7b1053043a7cc43304a544a516024a4696
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165787"
---
# <a name="iclrstrongnamestrongnamesignaturegeneration-method"></a><span data-ttu-id="2e6e6-102">ICLRStrongName::StrongNameSignatureGeneration — Metoda</span><span class="sxs-lookup"><span data-stu-id="2e6e6-102">ICLRStrongName::StrongNameSignatureGeneration Method</span></span>
<span data-ttu-id="2e6e6-103">Generuje podpisu silnej nazwy dla określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="2e6e6-103">Generates a strong name signature for the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e6e6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2e6e6-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureGeneration (   
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e6e6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2e6e6-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="2e6e6-106">[in] Ścieżka do pliku, który zawiera manifest zestawu, dla którego zostanie wygenerowany podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="2e6e6-106">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="2e6e6-107">[in] Nazwa kontenera kluczy, który zawiera pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="2e6e6-107">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="2e6e6-108">Jeśli `pbKeyBlob` ma wartość null, `wszKeyContainer` należy określić prawidłowy kontener w ramach dostawcy usług kryptograficznych (CSP).</span><span class="sxs-lookup"><span data-stu-id="2e6e6-108">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="2e6e6-109">W tym przypadku parę kluczy, przechowywane w kontenerze służy do podpisywania pliku.</span><span class="sxs-lookup"><span data-stu-id="2e6e6-109">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="2e6e6-110">Jeśli `pbKeyBlob` nie ma wartości null, zakłada, że pary kluczy muszą być zawarte w kluczowych duży obiekt binarny (BLOB).</span><span class="sxs-lookup"><span data-stu-id="2e6e6-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="2e6e6-111">Klucze muszą być Rivest-Shamir-Adleman 1024-bitowy (RSA) kluczy podpisywania.</span><span class="sxs-lookup"><span data-stu-id="2e6e6-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="2e6e6-112">Żadne inne typy kluczy są obsługiwane w tej chwili.</span><span class="sxs-lookup"><span data-stu-id="2e6e6-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="2e6e6-113">[in] Wskaźnik do pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="2e6e6-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="2e6e6-114">Ta para jest w formacie utworzone przez Win32 `CryptExportKey` funkcji.</span><span class="sxs-lookup"><span data-stu-id="2e6e6-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="2e6e6-115">Jeśli `pbKeyBlob` jest null, kontenerze klucza określonym przez `wszKeyContainer` założono, że zawiera pary kluczy.</span><span class="sxs-lookup"><span data-stu-id="2e6e6-115">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="2e6e6-116">[in] Rozmiar w bajtach z `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="2e6e6-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="2e6e6-117">[out] Wskaźnik do lokalizacji, do której środowisko uruchomieniowe języka wspólnego zwraca podpis.</span><span class="sxs-lookup"><span data-stu-id="2e6e6-117">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="2e6e6-118">Jeśli `ppbSignatureBlob` jest wartość null, środowisko uruchomieniowe przechowuje podpisu w pliku określonym przez `wszFilePath`.</span><span class="sxs-lookup"><span data-stu-id="2e6e6-118">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="2e6e6-119">Jeśli `ppbSignatureBlob` jest inna niż null, środowisko uruchomieniowe języka wspólnego przydziela miejsce, w której ma zostać zwrócone podpis.</span><span class="sxs-lookup"><span data-stu-id="2e6e6-119">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="2e6e6-120">Obiekt wywołujący należy zwolnić miejsce to przy użyciu [iclrstrongname::strongnamefreebuffer —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="2e6e6-120">The caller must free this space by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="2e6e6-121">[out] Rozmiar w bajtach sygnatury zwracanego.</span><span class="sxs-lookup"><span data-stu-id="2e6e6-121">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2e6e6-122">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2e6e6-122">Return Value</span></span>  
 `S_OK` <span data-ttu-id="2e6e6-123">Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje błąd (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).</span><span class="sxs-lookup"><span data-stu-id="2e6e6-123">if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e6e6-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2e6e6-124">Remarks</span></span>  
 <span data-ttu-id="2e6e6-125">Określ wartość null w przypadku `wszFilePath` do obliczania rozmiaru podpisu bez tworzenia podpisu.</span><span class="sxs-lookup"><span data-stu-id="2e6e6-125">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="2e6e6-126">Podpis może być przechowywany bezpośrednio w pliku lub zwracane do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="2e6e6-126">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e6e6-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2e6e6-127">Requirements</span></span>  
 <span data-ttu-id="2e6e6-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e6e6-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e6e6-129">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="2e6e6-129">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="2e6e6-130">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2e6e6-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="2e6e6-131">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="2e6e6-131">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2e6e6-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2e6e6-132">See also</span></span>

- [<span data-ttu-id="2e6e6-133">StrongNameSignatureGenerationEx, metoda</span><span class="sxs-lookup"><span data-stu-id="2e6e6-133">StrongNameSignatureGenerationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="2e6e6-134">ICLRStrongName — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2e6e6-134">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
