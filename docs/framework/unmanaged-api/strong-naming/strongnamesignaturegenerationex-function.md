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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5d60b9a9ae566b5bd686b27b2e09861a8414979
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000236"
---
# <a name="strongnamesignaturegenerationex-function"></a><span data-ttu-id="6c619-102">StrongNameSignatureGenerationEx — Funkcja</span><span class="sxs-lookup"><span data-stu-id="6c619-102">StrongNameSignatureGenerationEx Function</span></span>
<span data-ttu-id="6c619-103">Generuje podpisu silnej nazwy dla określonego zestawu, zgodnie z określone flagi.</span><span class="sxs-lookup"><span data-stu-id="6c619-103">Generates a strong name signature for the specified assembly, according to the specified flags.</span></span>  
  
 <span data-ttu-id="6c619-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="6c619-104">This function has been deprecated.</span></span> <span data-ttu-id="6c619-105">Użyj [iclrstrongname::strongnamesignaturegenerationex —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="6c619-105">Use the [ICLRStrongName::StrongNameSignatureGenerationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c619-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="6c619-106">Syntax</span></span>  
  
```  
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
  
## <a name="parameters"></a><span data-ttu-id="6c619-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="6c619-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="6c619-108">[in] Ścieżka do pliku, który zawiera manifest zestawu, dla którego zostanie wygenerowany podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="6c619-108">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="6c619-109">[in] Nazwa kontenera kluczy, który zawiera pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="6c619-109">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="6c619-110">Jeśli `pbKeyBlob` ma wartość null, `wszKeyContainer` należy określić prawidłowy kontener w ramach dostawcy usług kryptograficznych (CSP).</span><span class="sxs-lookup"><span data-stu-id="6c619-110">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="6c619-111">W tym przypadku parę kluczy, przechowywane w kontenerze służy do podpisywania pliku.</span><span class="sxs-lookup"><span data-stu-id="6c619-111">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="6c619-112">Jeśli `pbKeyBlob` nie ma wartości null, zakłada, że pary kluczy muszą być zawarte w kluczowych duży obiekt binarny (BLOB).</span><span class="sxs-lookup"><span data-stu-id="6c619-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="6c619-113">[in] Wskaźnik do pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="6c619-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="6c619-114">Ta para jest w formacie utworzone przez Win32 `CryptExportKey` funkcji.</span><span class="sxs-lookup"><span data-stu-id="6c619-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="6c619-115">Jeśli `pbKeyBlob` jest null, kontenerze klucza określonym przez `wszKeyContainer` założono, że zawiera pary kluczy.</span><span class="sxs-lookup"><span data-stu-id="6c619-115">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="6c619-116">[in] Rozmiar w bajtach z `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="6c619-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="6c619-117">[out] Wskaźnik do lokalizacji, do której środowisko uruchomieniowe języka wspólnego zwraca podpis.</span><span class="sxs-lookup"><span data-stu-id="6c619-117">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="6c619-118">Jeśli `ppbSignatureBlob` jest wartość null, środowisko uruchomieniowe przechowuje podpisu w pliku określonym przez `wszFilePath`.</span><span class="sxs-lookup"><span data-stu-id="6c619-118">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="6c619-119">Jeśli `ppbSignatureBlob` jest inna niż null, środowisko uruchomieniowe języka wspólnego przydziela miejsce, w której ma zostać zwrócone podpis.</span><span class="sxs-lookup"><span data-stu-id="6c619-119">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="6c619-120">Obiekt wywołujący musi zwolnić tego miejsca przy użyciu [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="6c619-120">The caller must free this space using the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="6c619-121">[out] Rozmiar w bajtach sygnatury zwracanego.</span><span class="sxs-lookup"><span data-stu-id="6c619-121">[out] The size, in bytes, of the returned signature.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="6c619-122">[in] Jeden lub więcej z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="6c619-122">[in] One or more of the following values:</span></span>  
  
- <span data-ttu-id="6c619-123">`SN_SIGN_ALL_FILES` (0x00000001) - ponownie obliczyć skrótów wszystkich modułów połączonych.</span><span class="sxs-lookup"><span data-stu-id="6c619-123">`SN_SIGN_ALL_FILES` (0x00000001) - Recompute all hashes for linked modules.</span></span>  
  
- <span data-ttu-id="6c619-124">`SN_TEST_SIGN` (0x00000002) - test podpisanie zestawu.</span><span class="sxs-lookup"><span data-stu-id="6c619-124">`SN_TEST_SIGN` (0x00000002) - Test-sign the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6c619-125">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6c619-125">Return Value</span></span>  
 <span data-ttu-id="6c619-126">`true` Po pomyślnym zakończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="6c619-126">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c619-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6c619-127">Remarks</span></span>  
 <span data-ttu-id="6c619-128">Określ wartość null w przypadku `wszFilePath` do obliczania rozmiaru podpisu bez tworzenia podpisu.</span><span class="sxs-lookup"><span data-stu-id="6c619-128">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="6c619-129">Podpis mogą być przechowywane bezpośrednio w pliku albo zwracany do wywołującego.</span><span class="sxs-lookup"><span data-stu-id="6c619-129">The signature can be either stored directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="6c619-130">Jeśli `SN_SIGN_ALL_FILES` jest określony, ale klucz publiczny nie jest uwzględniony (zarówno `pbKeyBlob` i `wszFilePath` mają wartość null), skróty dla połączonych modułów są obliczane ponownie, ale zestaw nie jest ponownie podpisany.</span><span class="sxs-lookup"><span data-stu-id="6c619-130">If `SN_SIGN_ALL_FILES` is specified but a public key is not included (both `pbKeyBlob` and `wszFilePath` are null), hashes for linked modules are recomputed, but the assembly is not re-signed.</span></span>  
  
 <span data-ttu-id="6c619-131">Jeśli `SN_TEST_SIGN` określono typowego nagłówka środowiska uruchomieniowego języka nie jest modyfikowany w celu wskazania, że zestaw jest podpisany silną nazwą.</span><span class="sxs-lookup"><span data-stu-id="6c619-131">If `SN_TEST_SIGN` is specified, the common language runtime header is not modified to indicate that the assembly is signed with a strong name.</span></span>  
  
 <span data-ttu-id="6c619-132">Jeśli `StrongNameSignatureGenerationEx` funkcja nie jest ukończone pomyślnie, wywołaj [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcję, aby pobrać ostatni błąd wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="6c619-132">If the `StrongNameSignatureGenerationEx` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c619-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6c619-133">Requirements</span></span>  
 <span data-ttu-id="6c619-134">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c619-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c619-135">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="6c619-135">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="6c619-136">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6c619-136">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6c619-137">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c619-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c619-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6c619-138">See also</span></span>

- [<span data-ttu-id="6c619-139">StrongNameSignatureGenerationEx, metoda</span><span class="sxs-lookup"><span data-stu-id="6c619-139">StrongNameSignatureGenerationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="6c619-140">StrongNameSignatureGeneration, metoda</span><span class="sxs-lookup"><span data-stu-id="6c619-140">StrongNameSignatureGeneration Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="6c619-141">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="6c619-141">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
