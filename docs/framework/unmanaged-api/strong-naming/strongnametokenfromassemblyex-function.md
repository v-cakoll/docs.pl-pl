---
title: StrongNameTokenFromAssemblyEx — Funkcja
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromAssemblyEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameTokenFromAssemblyEx
helpviewer_keywords:
- StrongNameTokenFromAssemblyEx function [.NET Framework strong naming]
ms.assetid: 67a8a9f2-dee3-44b2-a1c0-f307a3bdf90f
topic_type:
- apiref
ms.openlocfilehash: 8b7866b92be3195b0a767a823a0d7fb1c0aa4918
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73104245"
---
# <a name="strongnametokenfromassemblyex-function"></a><span data-ttu-id="fd660-102">StrongNameTokenFromAssemblyEx — Funkcja</span><span class="sxs-lookup"><span data-stu-id="fd660-102">StrongNameTokenFromAssemblyEx Function</span></span>
<span data-ttu-id="fd660-103">Tworzy token silnej nazwy z określonego pliku zestawu i zwraca klucz publiczny, który reprezentuje token.</span><span class="sxs-lookup"><span data-stu-id="fd660-103">Creates a strong name token from the specified assembly file, and returns the public key that the token represents.</span></span>  
  
 <span data-ttu-id="fd660-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="fd660-104">This function has been deprecated.</span></span> <span data-ttu-id="fd660-105">Zamiast tego użyj metody [ICLRStrongName:: StrongNameTokenFromAssemblyEx —](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="fd660-105">Use the [ICLRStrongName::StrongNameTokenFromAssemblyEx](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd660-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="fd660-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd660-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="fd660-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="fd660-108">podczas Ścieżka do przenośnego pliku wykonywalnego (PE) dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="fd660-108">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="fd660-109">określoną Zwrócony token silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="fd660-109">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="fd660-110">określoną Rozmiar (w bajtach) tokenu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="fd660-110">[out] The size, in bytes, of the strong name token.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="fd660-111">określoną Zwrócony klucz publiczny.</span><span class="sxs-lookup"><span data-stu-id="fd660-111">[out] The returned public key.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="fd660-112">określoną Rozmiar (w bajtach) klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="fd660-112">[out] The size, in bytes, of the public key.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fd660-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fd660-113">Return Value</span></span>  
 <span data-ttu-id="fd660-114">`true` po pomyślnym zakończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="fd660-114">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd660-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fd660-115">Remarks</span></span>  
 <span data-ttu-id="fd660-116">Token silnej nazwy to skrócona postać klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="fd660-116">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="fd660-117">Token jest 64-bitowym skrótem, który jest tworzony na podstawie klucza publicznego używanego do podpisywania zestawu.</span><span class="sxs-lookup"><span data-stu-id="fd660-117">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="fd660-118">Token jest częścią silnej nazwy zestawu i można go odczytać z metadanych zestawu.</span><span class="sxs-lookup"><span data-stu-id="fd660-118">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="fd660-119">Po pobraniu klucza i utworzeniu tokenu należy wywołać funkcję [StrongNameFreeBuffer —](strongnamefreebuffer-function.md) , aby zwolnić przydzieloną pamięć.</span><span class="sxs-lookup"><span data-stu-id="fd660-119">After the key is retrieved and the token is created, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="fd660-120">Jeśli funkcja `StrongNameTokenFromAssemblyEx` nie zakończy się pomyślnie, wywołaj funkcję [StrongNameErrorInfo —](strongnameerrorinfo-function.md) w celu pobrania ostatniego wygenerowanego błędu.</span><span class="sxs-lookup"><span data-stu-id="fd660-120">If the `StrongNameTokenFromAssemblyEx` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd660-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fd660-121">Requirements</span></span>  
 <span data-ttu-id="fd660-122">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd660-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd660-123">**Nagłówek:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="fd660-123">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="fd660-124">**Biblioteka:** Uwzględnione jako zasób w bibliotece mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="fd660-124">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="fd660-125">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd660-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd660-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fd660-126">See also</span></span>

- [<span data-ttu-id="fd660-127">StrongNameTokenFromAssemblyEx, metoda</span><span class="sxs-lookup"><span data-stu-id="fd660-127">StrongNameTokenFromAssemblyEx Method</span></span>](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [<span data-ttu-id="fd660-128">StrongNameTokenFromAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="fd660-128">StrongNameTokenFromAssembly Method</span></span>](../hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [<span data-ttu-id="fd660-129">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="fd660-129">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
