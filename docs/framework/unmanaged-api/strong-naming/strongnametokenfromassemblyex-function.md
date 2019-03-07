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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6f95ac4e4c21a2cbaab9f91c1257a868bdce65af
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499189"
---
# <a name="strongnametokenfromassemblyex-function"></a><span data-ttu-id="379d7-102">StrongNameTokenFromAssemblyEx — Funkcja</span><span class="sxs-lookup"><span data-stu-id="379d7-102">StrongNameTokenFromAssemblyEx Function</span></span>
<span data-ttu-id="379d7-103">Tworzy token silnej nazwy z określonego pliku zestawu i zwraca klucz publiczny, który reprezentuje token.</span><span class="sxs-lookup"><span data-stu-id="379d7-103">Creates a strong name token from the specified assembly file, and returns the public key that the token represents.</span></span>  
  
 <span data-ttu-id="379d7-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="379d7-104">This function has been deprecated.</span></span> <span data-ttu-id="379d7-105">Użyj [iclrstrongname::strongnametokenfromassemblyex —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="379d7-105">Use the [ICLRStrongName::StrongNameTokenFromAssemblyEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="379d7-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="379d7-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="379d7-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="379d7-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="379d7-108">[in] Ścieżka do pliku wykonalnego (PE) pliku zestawu.</span><span class="sxs-lookup"><span data-stu-id="379d7-108">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="379d7-109">[out] Token zwracany silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="379d7-109">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="379d7-110">[out] Rozmiar w bajtach, token silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="379d7-110">[out] The size, in bytes, of the strong name token.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="379d7-111">[out] Zwrócony klucz publiczny.</span><span class="sxs-lookup"><span data-stu-id="379d7-111">[out] The returned public key.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="379d7-112">[out] Rozmiar w bajtach klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="379d7-112">[out] The size, in bytes, of the public key.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="379d7-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="379d7-113">Return Value</span></span>  
 <span data-ttu-id="379d7-114">`true` Po pomyślnym zakończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="379d7-114">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="379d7-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="379d7-115">Remarks</span></span>  
 <span data-ttu-id="379d7-116">Token silna nazwa jest skrócona forma klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="379d7-116">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="379d7-117">Token jest 64-bitową wartość skrótu, utworzona na podstawie klucza publicznego używany do podpisywania zestawu.</span><span class="sxs-lookup"><span data-stu-id="379d7-117">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="379d7-118">Token jest częścią silnej nazwy zestawu i może zostać odczytany z metadanych zestawu.</span><span class="sxs-lookup"><span data-stu-id="379d7-118">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="379d7-119">Po na pobranie klucza i jest tworzony token, należy wywołać [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) funkcję, aby zwolnić alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="379d7-119">After the key is retrieved and the token is created, you should call the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="379d7-120">Jeśli `StrongNameTokenFromAssemblyEx` funkcja nie jest ukończone pomyślnie, wywołaj [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcję, aby pobrać ostatni błąd wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="379d7-120">If the `StrongNameTokenFromAssemblyEx` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="379d7-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="379d7-121">Requirements</span></span>  
 <span data-ttu-id="379d7-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="379d7-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="379d7-123">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="379d7-123">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="379d7-124">**Biblioteka:** Dołączony jako zasób w mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="379d7-124">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="379d7-125">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="379d7-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="379d7-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="379d7-126">See also</span></span>
- [<span data-ttu-id="379d7-127">StrongNameTokenFromAssemblyEx, metoda</span><span class="sxs-lookup"><span data-stu-id="379d7-127">StrongNameTokenFromAssemblyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [<span data-ttu-id="379d7-128">StrongNameTokenFromAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="379d7-128">StrongNameTokenFromAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [<span data-ttu-id="379d7-129">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="379d7-129">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
