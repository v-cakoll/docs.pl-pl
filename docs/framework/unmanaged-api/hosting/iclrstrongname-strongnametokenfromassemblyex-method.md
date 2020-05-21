---
title: ICLRStrongName::StrongNameTokenFromAssemblyEx — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromAssemblyEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromAssemblyEx
helpviewer_keywords:
- StrongNameTokenFromAssemblyEx method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameTokenFromAssemblyEx method [.NET Framework hosting]
ms.assetid: 648ea90e-5e60-40a0-a56a-3e61bf2fba7c
topic_type:
- apiref
ms.openlocfilehash: e504aa067d51ec62d42f019c3a9e40538e374ea1
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762620"
---
# <a name="iclrstrongnamestrongnametokenfromassemblyex-method"></a><span data-ttu-id="b4c05-102">ICLRStrongName::StrongNameTokenFromAssemblyEx — Metoda</span><span class="sxs-lookup"><span data-stu-id="b4c05-102">ICLRStrongName::StrongNameTokenFromAssemblyEx Method</span></span>
<span data-ttu-id="b4c05-103">Tworzy token silnej nazwy z określonego pliku zestawu i zwraca klucz publiczny, który reprezentuje token.</span><span class="sxs-lookup"><span data-stu-id="b4c05-103">Creates a strong name token from the specified assembly file, and returns the public key that the token represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4c05-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b4c05-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4c05-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b4c05-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="b4c05-106">podczas Ścieżka do przenośnego pliku wykonywalnego (PE) dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="b4c05-106">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="b4c05-107">określoną Zwrócony token silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="b4c05-107">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="b4c05-108">określoną Rozmiar (w bajtach) tokenu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="b4c05-108">[out] The size, in bytes, of the strong name token.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="b4c05-109">określoną Zwrócony klucz publiczny.</span><span class="sxs-lookup"><span data-stu-id="b4c05-109">[out] The returned public key.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="b4c05-110">określoną Rozmiar (w bajtach) klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="b4c05-110">[out] The size, in bytes, of the public key.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b4c05-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b4c05-111">Return Value</span></span>  
 <span data-ttu-id="b4c05-112">`S_OK`Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT wskazująca niepowodzenie (zobacz [typowe wartości HRESULT](/windows/win32/seccrypto/common-hresult-values) dla listy).</span><span class="sxs-lookup"><span data-stu-id="b4c05-112">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4c05-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b4c05-113">Remarks</span></span>  
 <span data-ttu-id="b4c05-114">Token silnej nazwy to skrócona postać klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="b4c05-114">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="b4c05-115">Token jest 64-bitowym skrótem, który jest tworzony na podstawie klucza publicznego używanego do podpisywania zestawu.</span><span class="sxs-lookup"><span data-stu-id="b4c05-115">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="b4c05-116">Token jest częścią silnej nazwy zestawu i można go odczytać z metadanych zestawu.</span><span class="sxs-lookup"><span data-stu-id="b4c05-116">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="b4c05-117">Po pobraniu klucza i utworzeniu tokenu należy wywołać metodę [ICLRStrongName:: StrongNameFreeBuffer —](iclrstrongname-strongnamefreebuffer-method.md) , aby zwolnić przydzieloną pamięć.</span><span class="sxs-lookup"><span data-stu-id="b4c05-117">After the key is retrieved and the token is created, you should call the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4c05-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b4c05-118">Requirements</span></span>  
 <span data-ttu-id="b4c05-119">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4c05-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4c05-120">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="b4c05-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b4c05-121">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b4c05-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b4c05-122">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4c05-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4c05-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b4c05-123">See also</span></span>

- [<span data-ttu-id="b4c05-124">StrongNameTokenFromAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="b4c05-124">StrongNameTokenFromAssembly Method</span></span>](iclrstrongname-strongnametokenfromassembly-method.md)
- [<span data-ttu-id="b4c05-125">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="b4c05-125">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
