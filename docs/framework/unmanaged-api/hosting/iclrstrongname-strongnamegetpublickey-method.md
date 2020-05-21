---
title: ICLRStrongName::StrongNameGetPublicKey — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetPublicKey
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameGetPublicKey method [.NET Framework hosting]
ms.assetid: a31dcaa9-a404-4c1d-8cc7-081827c52935
topic_type:
- apiref
ms.openlocfilehash: 5a20bde64830617090c92afe5fae3a603cf9103b
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763137"
---
# <a name="iclrstrongnamestrongnamegetpublickey-method"></a><span data-ttu-id="ece24-102">ICLRStrongName::StrongNameGetPublicKey — Metoda</span><span class="sxs-lookup"><span data-stu-id="ece24-102">ICLRStrongName::StrongNameGetPublicKey Method</span></span>
<span data-ttu-id="ece24-103">Pobiera klucz publiczny z pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="ece24-103">Gets the public key from a public/private key pair.</span></span> <span data-ttu-id="ece24-104">Para kluczy może być podana jako nazwa kontenera klucza w ramach dostawcy usług kryptograficznych (CSP) lub jako pierwotna kolekcja bajtów.</span><span class="sxs-lookup"><span data-stu-id="ece24-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ece24-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="ece24-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetPublicKey (
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ece24-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ece24-106">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="ece24-107">podczas Nazwa kontenera kluczy, który zawiera parę kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="ece24-107">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="ece24-108">Jeśli `pbKeyBlob` ma wartość null, `szKeyContainer` należy określić prawidłowy kontener w ramach dostawcy CSP.</span><span class="sxs-lookup"><span data-stu-id="ece24-108">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="ece24-109">W takim przypadku Metoda [ICLRStrongName:: StrongNameGetPublicKey —](iclrstrongname-strongnamegetpublickey-method.md) wyodrębnia klucz publiczny z pary kluczy przechowywanej w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="ece24-109">In this case, the [ICLRStrongName::StrongNameGetPublicKey](iclrstrongname-strongnamegetpublickey-method.md) method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="ece24-110">Jeśli `pbKeyBlob` wartość nie jest równa null, przyjmuje się, że para kluczy jest zawarta w kluczowym dużym obiekcie binarnym (BLOB).</span><span class="sxs-lookup"><span data-stu-id="ece24-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="ece24-111">Klucze muszą być 1024-bitowe Rivest-Shamir-Adleman (RSA) kluczy podpisywania.</span><span class="sxs-lookup"><span data-stu-id="ece24-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="ece24-112">W tej chwili nie są obsługiwane żadne inne typy kluczy.</span><span class="sxs-lookup"><span data-stu-id="ece24-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="ece24-113">podczas Wskaźnik do pary kluczy publicznych/prywatnych.</span><span class="sxs-lookup"><span data-stu-id="ece24-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="ece24-114">Ta para jest w formacie utworzonym przez funkcję Win32 `CryptExportKey` .</span><span class="sxs-lookup"><span data-stu-id="ece24-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="ece24-115">Jeśli `pbKeyBlob` ma wartość null, zakłada się, że kontener kluczy określony przez `szKeyContainer` ma zawierać parę kluczy.</span><span class="sxs-lookup"><span data-stu-id="ece24-115">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="ece24-116">podczas Rozmiar, w bajtach, z `pbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="ece24-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="ece24-117">określoną Zwrócony obiekt BLOB klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="ece24-117">[out] The returned public key BLOB.</span></span> <span data-ttu-id="ece24-118">`ppbPublicKeyBlob`Parametr jest przypisywany przez środowisko uruchomieniowe języka wspólnego i zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="ece24-118">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="ece24-119">Obiekt wywołujący musi zwolnić pamięć przy użyciu metody [ICLRStrongName:: StrongNameFreeBuffer —](iclrstrongname-strongnamefreebuffer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ece24-119">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="ece24-120">określoną Rozmiar zwróconego obiektu BLOB klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="ece24-120">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ece24-121">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ece24-121">Return Value</span></span>  
 <span data-ttu-id="ece24-122">`S_OK`Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT wskazująca niepowodzenie (zobacz [typowe wartości HRESULT](/windows/win32/seccrypto/common-hresult-values) dla listy).</span><span class="sxs-lookup"><span data-stu-id="ece24-122">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ece24-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ece24-123">Remarks</span></span>  
 <span data-ttu-id="ece24-124">Klucz publiczny jest zawarty w strukturze [PublicKeyBlob —](../strong-naming/publickeyblob-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="ece24-124">The public key is contained in a [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ece24-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ece24-125">Requirements</span></span>  
 <span data-ttu-id="ece24-126">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ece24-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ece24-127">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="ece24-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ece24-128">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ece24-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ece24-129">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ece24-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ece24-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ece24-130">See also</span></span>

- [<span data-ttu-id="ece24-131">StrongNameTokenFromPublicKey, metoda</span><span class="sxs-lookup"><span data-stu-id="ece24-131">StrongNameTokenFromPublicKey Method</span></span>](iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="ece24-132">PublicKeyBlob — Struktura</span><span class="sxs-lookup"><span data-stu-id="ece24-132">PublicKeyBlob Structure</span></span>](../strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="ece24-133">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="ece24-133">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
