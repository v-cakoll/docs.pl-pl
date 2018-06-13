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
ms.openlocfilehash: 217b54a615d7c553e714ef87b3c2bb6a1919ae98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435378"
---
# <a name="iclrstrongnamestrongnamesignaturegeneration-method"></a><span data-ttu-id="4ae89-102">ICLRStrongName::StrongNameSignatureGeneration — Metoda</span><span class="sxs-lookup"><span data-stu-id="4ae89-102">ICLRStrongName::StrongNameSignatureGeneration Method</span></span>
<span data-ttu-id="4ae89-103">Generuje podpisu silnej nazwy dla określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="4ae89-103">Generates a strong name signature for the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ae89-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4ae89-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="4ae89-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4ae89-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="4ae89-106">[in] Ścieżka do pliku, który zawiera manifest zestawu, dla którego zostanie wygenerowana podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="4ae89-106">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="4ae89-107">[in] Nazwa kontenera klucza, który zawiera pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="4ae89-107">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="4ae89-108">Jeśli `pbKeyBlob` ma wartość null, `wszKeyContainer` należy określić prawidłowy kontener w ramach dostawcy usług kryptograficznych (CSP).</span><span class="sxs-lookup"><span data-stu-id="4ae89-108">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="4ae89-109">W takim przypadku pary kluczy przechowywanych w kontenerze jest używany do podpisywania pliku.</span><span class="sxs-lookup"><span data-stu-id="4ae89-109">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="4ae89-110">Jeśli `pbKeyBlob` nie ma wartości null, zakłada, że pary kluczy muszą być zawarte w klucza dużego obiektu binarnego (BLOB).</span><span class="sxs-lookup"><span data-stu-id="4ae89-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="4ae89-111">Klucze muszą być Rivest-Shamir-Adleman (RSA 1024-bitowe) kluczy podpisywania.</span><span class="sxs-lookup"><span data-stu-id="4ae89-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="4ae89-112">Żadne inne typy klucze są obsługiwane w tej chwili.</span><span class="sxs-lookup"><span data-stu-id="4ae89-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="4ae89-113">[in] Wskaźnik do pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="4ae89-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="4ae89-114">Tej pary jest w formacie utworzone przez Win32 `CryptExportKey` funkcji.</span><span class="sxs-lookup"><span data-stu-id="4ae89-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="4ae89-115">Jeśli `pbKeyBlob` jest null, określony przez kontener klucza `wszKeyContainer` założono, że zawiera pary kluczy.</span><span class="sxs-lookup"><span data-stu-id="4ae89-115">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="4ae89-116">[in] Rozmiar w bajtach z `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="4ae89-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="4ae89-117">[out] Wskaźnik do lokalizacji, do którego środowisko uruchomieniowe języka wspólnego zwraca podpis.</span><span class="sxs-lookup"><span data-stu-id="4ae89-117">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="4ae89-118">Jeśli `ppbSignatureBlob` jest wartość null, środowisko uruchomieniowe przechowuje podpisu pliku określonego przez `wszFilePath`.</span><span class="sxs-lookup"><span data-stu-id="4ae89-118">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="4ae89-119">Jeśli `ppbSignatureBlob` jest niezerowa, środowisko uruchomieniowe języka wspólnego przydziela miejsce, do której należy zwrócić podpisu.</span><span class="sxs-lookup"><span data-stu-id="4ae89-119">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="4ae89-120">Obiekt wywołujący musi miejsca to przy użyciu [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="4ae89-120">The caller must free this space by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="4ae89-121">[out] Rozmiar w bajtach zwrócony podpisu.</span><span class="sxs-lookup"><span data-stu-id="4ae89-121">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4ae89-122">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4ae89-122">Return Value</span></span>  
 <span data-ttu-id="4ae89-123">`S_OK` Jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje niepowodzenie (zobacz [wspólne wartości HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) lista).</span><span class="sxs-lookup"><span data-stu-id="4ae89-123">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4ae89-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4ae89-124">Remarks</span></span>  
 <span data-ttu-id="4ae89-125">Określ wartość null dla `wszFilePath` obliczyć rozmiar podpisu bez tworzenia podpisu.</span><span class="sxs-lookup"><span data-stu-id="4ae89-125">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="4ae89-126">Podpis może być przechowywana bezpośrednio w pliku lub zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="4ae89-126">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ae89-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4ae89-127">Requirements</span></span>  
 <span data-ttu-id="4ae89-128">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ae89-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ae89-129">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="4ae89-129">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="4ae89-130">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4ae89-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4ae89-131">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ae89-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ae89-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4ae89-132">See Also</span></span>  
 [<span data-ttu-id="4ae89-133">StrongNameSignatureGenerationEx, metoda</span><span class="sxs-lookup"><span data-stu-id="4ae89-133">StrongNameSignatureGenerationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)  
 [<span data-ttu-id="4ae89-134">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="4ae89-134">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
