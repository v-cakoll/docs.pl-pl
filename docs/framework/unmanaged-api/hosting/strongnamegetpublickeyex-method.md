---
title: StrongNameGetPublicKeyEx — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName2.StrongNameGetPublicKeyEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StrongNameGetPublicKeyEx
helpviewer_keywords:
- StrongNameGetPublicKeyEx method, ICLRStrongName2 interface [.NET Framework hosting]
- ICLRStrongName2::StrongNameGetPublicKeyEx method [.NET Framework hosting]
ms.assetid: 63d8260c-fb32-4f8f-a357-768afd570f68
topic_type:
- apiref
ms.openlocfilehash: 1904a98f254a988ce035847a4cdeede182aa07bf
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006379"
---
# <a name="strongnamegetpublickeyex-method"></a><span data-ttu-id="83778-102">StrongNameGetPublicKeyEx — Metoda</span><span class="sxs-lookup"><span data-stu-id="83778-102">StrongNameGetPublicKeyEx Method</span></span>
<span data-ttu-id="83778-103">Pobiera klucz publiczny z pary kluczy publiczny/prywatny i określa algorytm skrótu i algorytm podpisu.</span><span class="sxs-lookup"><span data-stu-id="83778-103">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83778-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="83778-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetPublicKey (
    [in]  LPCWSTR   pwzKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
    [in]  ULONG     uHashAlgId,  
    [in]  ULONG     uReserved,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83778-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="83778-105">Parameters</span></span>  
 `pwzKeyContainer`  
 <span data-ttu-id="83778-106">podczas Nazwa kontenera kluczy, który zawiera parę kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="83778-106">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="83778-107">Jeśli `pbKeyBlob` ma wartość null, `szKeyContainer` należy określić prawidłowy kontener w ramach dostawcy usług kryptograficznych (CSP).</span><span class="sxs-lookup"><span data-stu-id="83778-107">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="83778-108">W takim przypadku `StrongNameGetPublicKeyEx` metoda wyodrębnia klucz publiczny z pary kluczy przechowywanej w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="83778-108">In this case, the `StrongNameGetPublicKeyEx` method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="83778-109">Jeśli `pbKeyBlob` wartość nie jest równa null, przyjmuje się, że para kluczy jest zawarta w kluczowym dużym obiekcie binarnym (BLOB).</span><span class="sxs-lookup"><span data-stu-id="83778-109">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="83778-110">Klucze muszą być 1024-bitowe Rivest-Shamir-Adleman (RSA) kluczy podpisywania.</span><span class="sxs-lookup"><span data-stu-id="83778-110">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="83778-111">W tej chwili nie są obsługiwane żadne inne typy kluczy.</span><span class="sxs-lookup"><span data-stu-id="83778-111">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="83778-112">podczas Wskaźnik do pary kluczy publicznych/prywatnych.</span><span class="sxs-lookup"><span data-stu-id="83778-112">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="83778-113">Ta para jest w formacie utworzonym przez funkcję Win32 `CryptExportKey` .</span><span class="sxs-lookup"><span data-stu-id="83778-113">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="83778-114">Jeśli `pbKeyBlob` ma wartość null, zakłada się, że kontener kluczy określony przez `szKeyContainer` ma zawierać parę kluczy.</span><span class="sxs-lookup"><span data-stu-id="83778-114">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="83778-115">podczas Rozmiar, w bajtach, z `pbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="83778-115">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="83778-116">określoną Zwrócony obiekt BLOB klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="83778-116">[out] The returned public key BLOB.</span></span> <span data-ttu-id="83778-117">`ppbPublicKeyBlob`Parametr jest przypisywany przez środowisko uruchomieniowe języka wspólnego i zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="83778-117">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="83778-118">Obiekt wywołujący musi zwolnić pamięć przy użyciu metody [ICLRStrongName:: StrongNameFreeBuffer —](iclrstrongname-strongnamefreebuffer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="83778-118">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="83778-119">określoną Rozmiar zwróconego obiektu BLOB klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="83778-119">[out] The size of the returned public key BLOB.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="83778-120">podczas Algorytm wyznaczania wartości skrótu zestawu.</span><span class="sxs-lookup"><span data-stu-id="83778-120">[in] The assembly hash algorithm.</span></span> <span data-ttu-id="83778-121">Zapoznaj się z sekcją uwagi, aby uzyskać listę zaakceptowanych wartości.</span><span class="sxs-lookup"><span data-stu-id="83778-121">See the Remarks section for a list of accepted values.</span></span>  
  
 `uReserved`  
 <span data-ttu-id="83778-122">podczas Zarezerwowane do użytku w przyszłości; Wartością domyślną jest null.</span><span class="sxs-lookup"><span data-stu-id="83778-122">[in] Reserved for future use; defaults to null.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="83778-123">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="83778-123">Return Value</span></span>  
 <span data-ttu-id="83778-124">`S_OK`Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT wskazująca niepowodzenie (zobacz [typowe wartości HRESULT](/windows/win32/seccrypto/common-hresult-values) dla listy).</span><span class="sxs-lookup"><span data-stu-id="83778-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83778-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="83778-125">Remarks</span></span>  
 <span data-ttu-id="83778-126">Klucz publiczny jest zawarty w strukturze [PublicKeyBlob —](../strong-naming/publickeyblob-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="83778-126">The public key is contained in a [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83778-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="83778-127">Remarks</span></span>  
 <span data-ttu-id="83778-128">W poniższej tabeli przedstawiono zestaw akceptowanych wartości `uHashAlgId` parametru.</span><span class="sxs-lookup"><span data-stu-id="83778-128">The following table shows the set of accepted values for the `uHashAlgId` parameter.</span></span>  
  
|<span data-ttu-id="83778-129">Nazwa</span><span class="sxs-lookup"><span data-stu-id="83778-129">Name</span></span>|<span data-ttu-id="83778-130">Wartość</span><span class="sxs-lookup"><span data-stu-id="83778-130">Value</span></span>|  
|----------|-----------|  
|<span data-ttu-id="83778-131">Brak</span><span class="sxs-lookup"><span data-stu-id="83778-131">None</span></span>|<span data-ttu-id="83778-132">0</span><span class="sxs-lookup"><span data-stu-id="83778-132">0</span></span>|  
|<span data-ttu-id="83778-133">SHA-1</span><span class="sxs-lookup"><span data-stu-id="83778-133">SHA-1</span></span>|<span data-ttu-id="83778-134">0x8004</span><span class="sxs-lookup"><span data-stu-id="83778-134">0x8004</span></span>|  
|<span data-ttu-id="83778-135">SHA-256</span><span class="sxs-lookup"><span data-stu-id="83778-135">SHA-256</span></span>|<span data-ttu-id="83778-136">0x800c</span><span class="sxs-lookup"><span data-stu-id="83778-136">0x800c</span></span>|  
|<span data-ttu-id="83778-137">SHA-384</span><span class="sxs-lookup"><span data-stu-id="83778-137">SHA-384</span></span>|<span data-ttu-id="83778-138">0x800d</span><span class="sxs-lookup"><span data-stu-id="83778-138">0x800d</span></span>|  
|<span data-ttu-id="83778-139">SHA-512</span><span class="sxs-lookup"><span data-stu-id="83778-139">SHA-512</span></span>|<span data-ttu-id="83778-140">0x800e</span><span class="sxs-lookup"><span data-stu-id="83778-140">0x800e</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="83778-141">Wymagania</span><span class="sxs-lookup"><span data-stu-id="83778-141">Requirements</span></span>  
 <span data-ttu-id="83778-142">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83778-142">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83778-143">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="83778-143">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="83778-144">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="83778-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="83778-145">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83778-145">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83778-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="83778-146">See also</span></span>

- [<span data-ttu-id="83778-147">StrongNameTokenFromPublicKey, metoda</span><span class="sxs-lookup"><span data-stu-id="83778-147">StrongNameTokenFromPublicKey Method</span></span>](iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="83778-148">PublicKeyBlob — Struktura</span><span class="sxs-lookup"><span data-stu-id="83778-148">PublicKeyBlob Structure</span></span>](../strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="83778-149">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="83778-149">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
- [<span data-ttu-id="83778-150">StrongNameGetPublicKey, metoda</span><span class="sxs-lookup"><span data-stu-id="83778-150">StrongNameGetPublicKey Method</span></span>](iclrstrongname-strongnamegetpublickey-method.md)
