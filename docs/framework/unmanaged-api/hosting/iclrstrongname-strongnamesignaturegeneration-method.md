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
ms.openlocfilehash: e58ac181c4e472c469076b880ff71e0c6afa30fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178051"
---
# <a name="iclrstrongnamestrongnamesignaturegeneration-method"></a><span data-ttu-id="75fbe-102">ICLRStrongName::StrongNameSignatureGeneration — Metoda</span><span class="sxs-lookup"><span data-stu-id="75fbe-102">ICLRStrongName::StrongNameSignatureGeneration Method</span></span>
<span data-ttu-id="75fbe-103">Generuje podpis silnej nazwy dla określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="75fbe-103">Generates a strong name signature for the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75fbe-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="75fbe-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureGeneration (
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75fbe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="75fbe-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="75fbe-106">[w] Ścieżka do pliku, który zawiera manifest zestawu, dla którego zostanie wygenerowany podpis silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="75fbe-106">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="75fbe-107">[w] Nazwa kontenera klucza zawierającego parę kluczy publicznych/prywatnych.</span><span class="sxs-lookup"><span data-stu-id="75fbe-107">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="75fbe-108">Jeśli `pbKeyBlob` wartość `wszKeyContainer` null jest zerowa, należy określić prawidłowy kontener w ramach dostawcy usług kryptograficznych (CSP).</span><span class="sxs-lookup"><span data-stu-id="75fbe-108">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="75fbe-109">W takim przypadku para kluczy przechowywana w kontenerze jest używana do podpisywania pliku.</span><span class="sxs-lookup"><span data-stu-id="75fbe-109">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="75fbe-110">Jeśli `pbKeyBlob` nie ma wartości null, przyjmuje się, że para kluczy znajduje się w głównym obiekcie binarnym (BLOB).</span><span class="sxs-lookup"><span data-stu-id="75fbe-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="75fbe-111">Klucze muszą być 1024-bitowe klucze podpisywania Rivest-Shamir-Adleman (RSA).</span><span class="sxs-lookup"><span data-stu-id="75fbe-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="75fbe-112">Żadne inne typy kluczy są obecnie obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="75fbe-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="75fbe-113">[w] Wskaźnik do pary kluczy publicznych/prywatnych.</span><span class="sxs-lookup"><span data-stu-id="75fbe-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="75fbe-114">Ta para jest w formacie utworzonym `CryptExportKey` przez funkcję Win32.</span><span class="sxs-lookup"><span data-stu-id="75fbe-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="75fbe-115">Jeśli `pbKeyBlob` ma wartość null, `wszKeyContainer` przyjmuje się, że kontener kluczy określony przez zawiera parę kluczy.</span><span class="sxs-lookup"><span data-stu-id="75fbe-115">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="75fbe-116">[w] Rozmiar w bajtach `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="75fbe-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="75fbe-117">[na zewnątrz] Wskaźnik do lokalizacji, do której środowisko uruchomieniowe języka wspólnego zwraca podpis.</span><span class="sxs-lookup"><span data-stu-id="75fbe-117">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="75fbe-118">Jeśli `ppbSignatureBlob` wartość null ma wartość null, środowisko `wszFilePath`wykonawcze przechowuje podpis w pliku określonym przez program .</span><span class="sxs-lookup"><span data-stu-id="75fbe-118">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="75fbe-119">Jeśli `ppbSignatureBlob` nie jest null, środowisko uruchomieniowe języka wspólnego przydziela miejsce, w którym do zwrócenia podpisu.</span><span class="sxs-lookup"><span data-stu-id="75fbe-119">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="75fbe-120">Wywołujący musi zwolnić to miejsce przy użyciu [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="75fbe-120">The caller must free this space by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="75fbe-121">[na zewnątrz] Rozmiar w bajtach zwróconego podpisu.</span><span class="sxs-lookup"><span data-stu-id="75fbe-121">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="75fbe-122">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="75fbe-122">Return Value</span></span>  
 <span data-ttu-id="75fbe-123">`S_OK`jeśli metoda została pomyślnie ukończona; w przeciwnym razie wartość HRESULT wskazująca błąd (zobacz [typowe wartości HRESULT](/windows/win32/seccrypto/common-hresult-values) dla listy).</span><span class="sxs-lookup"><span data-stu-id="75fbe-123">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75fbe-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="75fbe-124">Remarks</span></span>  
 <span data-ttu-id="75fbe-125">Określ `wszFilePath` wartość null, aby obliczyć rozmiar podpisu bez tworzenia podpisu.</span><span class="sxs-lookup"><span data-stu-id="75fbe-125">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="75fbe-126">Podpis może być przechowywany bezpośrednio w pliku lub zwrócony do wywołującego.</span><span class="sxs-lookup"><span data-stu-id="75fbe-126">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75fbe-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="75fbe-127">Requirements</span></span>  
 <span data-ttu-id="75fbe-128">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75fbe-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75fbe-129">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="75fbe-129">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="75fbe-130">**Biblioteka:** Uwzględnione jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="75fbe-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="75fbe-131">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75fbe-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75fbe-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="75fbe-132">See also</span></span>

- [<span data-ttu-id="75fbe-133">StrongNameSignatureGenerationEx, metoda</span><span class="sxs-lookup"><span data-stu-id="75fbe-133">StrongNameSignatureGenerationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="75fbe-134">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="75fbe-134">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
