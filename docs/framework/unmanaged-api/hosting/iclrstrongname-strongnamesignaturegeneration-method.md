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
ms.openlocfilehash: a8c9eab719f6a4f233490e544f67cf779ea10b20
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763044"
---
# <a name="iclrstrongnamestrongnamesignaturegeneration-method"></a><span data-ttu-id="7c9cb-102">ICLRStrongName::StrongNameSignatureGeneration — Metoda</span><span class="sxs-lookup"><span data-stu-id="7c9cb-102">ICLRStrongName::StrongNameSignatureGeneration Method</span></span>
<span data-ttu-id="7c9cb-103">Generuje podpis silnej nazwy dla określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="7c9cb-103">Generates a strong name signature for the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c9cb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7c9cb-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="7c9cb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7c9cb-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="7c9cb-106">podczas Ścieżka do pliku zawierającego manifest zestawu, dla którego zostanie wygenerowany podpis silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="7c9cb-106">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="7c9cb-107">podczas Nazwa kontenera kluczy, który zawiera parę kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="7c9cb-107">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="7c9cb-108">Jeśli `pbKeyBlob` ma wartość null, `wszKeyContainer` należy określić prawidłowy kontener w ramach dostawcy usług kryptograficznych (CSP).</span><span class="sxs-lookup"><span data-stu-id="7c9cb-108">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="7c9cb-109">W takim przypadku para kluczy przechowywana w kontenerze jest używana do podpisania pliku.</span><span class="sxs-lookup"><span data-stu-id="7c9cb-109">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="7c9cb-110">Jeśli `pbKeyBlob` wartość nie jest równa null, przyjmuje się, że para kluczy jest zawarta w kluczowym dużym obiekcie binarnym (BLOB).</span><span class="sxs-lookup"><span data-stu-id="7c9cb-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="7c9cb-111">Klucze muszą być 1024-bitowe Rivest-Shamir-Adleman (RSA) kluczy podpisywania.</span><span class="sxs-lookup"><span data-stu-id="7c9cb-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="7c9cb-112">W tej chwili nie są obsługiwane żadne inne typy kluczy.</span><span class="sxs-lookup"><span data-stu-id="7c9cb-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="7c9cb-113">podczas Wskaźnik do pary kluczy publicznych/prywatnych.</span><span class="sxs-lookup"><span data-stu-id="7c9cb-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="7c9cb-114">Ta para jest w formacie utworzonym przez funkcję Win32 `CryptExportKey` .</span><span class="sxs-lookup"><span data-stu-id="7c9cb-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="7c9cb-115">Jeśli `pbKeyBlob` ma wartość null, zakłada się, że kontener kluczy określony przez `wszKeyContainer` ma zawierać parę kluczy.</span><span class="sxs-lookup"><span data-stu-id="7c9cb-115">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="7c9cb-116">podczas Rozmiar, w bajtach, z `pbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="7c9cb-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="7c9cb-117">określoną Wskaźnik do lokalizacji, do której aparat plików wykonywalnych języka wspólnego zwraca sygnaturę.</span><span class="sxs-lookup"><span data-stu-id="7c9cb-117">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="7c9cb-118">Jeśli `ppbSignatureBlob` ma wartość null, środowisko uruchomieniowe zapisuje podpis w pliku określonym przez `wszFilePath` .</span><span class="sxs-lookup"><span data-stu-id="7c9cb-118">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="7c9cb-119">Jeśli `ppbSignatureBlob` wartość nie jest równa null, środowisko uruchomieniowe języka wspólnego przydziela miejsce do zwrócenia sygnatury.</span><span class="sxs-lookup"><span data-stu-id="7c9cb-119">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="7c9cb-120">Obiekt wywołujący musi zwolnić to miejsce przy użyciu metody [ICLRStrongName:: StrongNameFreeBuffer —](iclrstrongname-strongnamefreebuffer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7c9cb-120">The caller must free this space by using the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="7c9cb-121">określoną Rozmiar zwróconej sygnatury w bajtach.</span><span class="sxs-lookup"><span data-stu-id="7c9cb-121">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7c9cb-122">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7c9cb-122">Return Value</span></span>  
 <span data-ttu-id="7c9cb-123">`S_OK`Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT wskazująca niepowodzenie (zobacz [typowe wartości HRESULT](/windows/win32/seccrypto/common-hresult-values) dla listy).</span><span class="sxs-lookup"><span data-stu-id="7c9cb-123">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7c9cb-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7c9cb-124">Remarks</span></span>  
 <span data-ttu-id="7c9cb-125">Określ wartość null dla `wszFilePath` , aby obliczyć rozmiar podpisu bez tworzenia podpisu.</span><span class="sxs-lookup"><span data-stu-id="7c9cb-125">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="7c9cb-126">Podpis może być przechowywany bezpośrednio w pliku lub zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="7c9cb-126">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c9cb-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7c9cb-127">Requirements</span></span>  
 <span data-ttu-id="7c9cb-128">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c9cb-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c9cb-129">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="7c9cb-129">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7c9cb-130">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7c9cb-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7c9cb-131">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c9cb-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c9cb-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7c9cb-132">See also</span></span>

- [<span data-ttu-id="7c9cb-133">StrongNameSignatureGenerationEx, metoda</span><span class="sxs-lookup"><span data-stu-id="7c9cb-133">StrongNameSignatureGenerationEx Method</span></span>](iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="7c9cb-134">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="7c9cb-134">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
