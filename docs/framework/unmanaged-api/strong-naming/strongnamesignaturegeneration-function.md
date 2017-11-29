---
title: "StrongNameSignatureGeneration — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameSignatureGeneration
api_location:
- mscoree.dll
- mscorsn.dll
api_type: DLLExport
f1_keywords: StrongNameSignatureGeneration
helpviewer_keywords: StrongNameSignatureGeneration function [.NET Framework strong naming]
ms.assetid: 839b765c-3e41-44ce-bf1b-dc10453db18e
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 26900b73e4c0b8b7501a59c3706966df5cf46120
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamesignaturegeneration-function"></a><span data-ttu-id="4fe7e-102">StrongNameSignatureGeneration — Funkcja</span><span class="sxs-lookup"><span data-stu-id="4fe7e-102">StrongNameSignatureGeneration Function</span></span>
<span data-ttu-id="4fe7e-103">Generuje podpisu silnej nazwy dla określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="4fe7e-103">Generates a strong name signature for the specified assembly.</span></span>  
  
 <span data-ttu-id="4fe7e-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="4fe7e-104">This function has been deprecated.</span></span> <span data-ttu-id="4fe7e-105">Użyj [ICLRStrongName::StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="4fe7e-105">Use the [ICLRStrongName::StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fe7e-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="4fe7e-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureGeneration (   
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4fe7e-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="4fe7e-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="4fe7e-108">[in] Ścieżka do pliku, który zawiera manifest zestawu, dla którego zostanie wygenerowana podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="4fe7e-108">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="4fe7e-109">[in] Nazwa kontenera klucza, który zawiera pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="4fe7e-109">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="4fe7e-110">Jeśli `pbKeyBlob` ma wartość null, `wszKeyContainer` należy określić prawidłowy kontener w ramach dostawcy usług kryptograficznych (CSP).</span><span class="sxs-lookup"><span data-stu-id="4fe7e-110">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="4fe7e-111">W takim przypadku pary kluczy przechowywanych w kontenerze jest używany do podpisywania pliku.</span><span class="sxs-lookup"><span data-stu-id="4fe7e-111">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="4fe7e-112">Jeśli `pbKeyBlob` nie ma wartości null, zakłada, że pary kluczy muszą być zawarte w klucza dużego obiektu binarnego (BLOB).</span><span class="sxs-lookup"><span data-stu-id="4fe7e-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="4fe7e-113">Klucze muszą być Rivest-Shamir-Adleman (RSA 1024-bitowe) kluczy podpisywania.</span><span class="sxs-lookup"><span data-stu-id="4fe7e-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="4fe7e-114">Żadne inne typy klucze są obsługiwane w tej chwili.</span><span class="sxs-lookup"><span data-stu-id="4fe7e-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="4fe7e-115">[in] Wskaźnik do pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="4fe7e-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="4fe7e-116">Tej pary jest w formacie utworzone przez Win32 `CryptExportKey` funkcji.</span><span class="sxs-lookup"><span data-stu-id="4fe7e-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="4fe7e-117">Jeśli `pbKeyBlob` jest null, określony przez kontener klucza `wszKeyContainer` założono, że zawiera pary kluczy.</span><span class="sxs-lookup"><span data-stu-id="4fe7e-117">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="4fe7e-118">[in] Rozmiar w bajtach z `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="4fe7e-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="4fe7e-119">[out] Wskaźnik do lokalizacji, do którego środowisko uruchomieniowe języka wspólnego zwraca podpis.</span><span class="sxs-lookup"><span data-stu-id="4fe7e-119">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="4fe7e-120">Jeśli `ppbSignatureBlob` jest wartość null, środowisko uruchomieniowe przechowuje podpisu pliku określonego przez `wszFilePath`.</span><span class="sxs-lookup"><span data-stu-id="4fe7e-120">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="4fe7e-121">Jeśli `ppbSignatureBlob` jest niezerowa, środowisko uruchomieniowe języka wspólnego przydziela miejsce, do której należy zwrócić podpisu.</span><span class="sxs-lookup"><span data-stu-id="4fe7e-121">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="4fe7e-122">Obiekt wywołujący musi zwolnić przy użyciu tego miejsca [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="4fe7e-122">The caller must free this space using the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="4fe7e-123">[out] Rozmiar w bajtach zwrócony podpisu.</span><span class="sxs-lookup"><span data-stu-id="4fe7e-123">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4fe7e-124">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4fe7e-124">Return Value</span></span>  
 <span data-ttu-id="4fe7e-125">`true`Po pomyślnym ukończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="4fe7e-125">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4fe7e-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4fe7e-126">Remarks</span></span>  
 <span data-ttu-id="4fe7e-127">Określ wartość null dla `wszFilePath` obliczyć rozmiar podpisu bez tworzenia podpisu.</span><span class="sxs-lookup"><span data-stu-id="4fe7e-127">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="4fe7e-128">Podpis może być przechowywana bezpośrednio w pliku lub zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="4fe7e-128">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="4fe7e-129">Jeśli `StrongNameSignatureGeneration` funkcji nie powiodło się, wywołania [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcji, aby pobrać ostatniego wygenerowany błąd.</span><span class="sxs-lookup"><span data-stu-id="4fe7e-129">If the `StrongNameSignatureGeneration` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fe7e-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4fe7e-130">Requirements</span></span>  
 <span data-ttu-id="4fe7e-131">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4fe7e-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fe7e-132">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="4fe7e-132">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="4fe7e-133">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4fe7e-133">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4fe7e-134">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fe7e-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fe7e-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4fe7e-135">See Also</span></span>  
 [<span data-ttu-id="4fe7e-136">StrongNameSignatureGeneration — metoda</span><span class="sxs-lookup"><span data-stu-id="4fe7e-136">StrongNameSignatureGeneration Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)  
 [<span data-ttu-id="4fe7e-137">StrongNameSignatureGenerationEx — metoda</span><span class="sxs-lookup"><span data-stu-id="4fe7e-137">StrongNameSignatureGenerationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)  
 [<span data-ttu-id="4fe7e-138">ICLRStrongName — interfejs</span><span class="sxs-lookup"><span data-stu-id="4fe7e-138">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
