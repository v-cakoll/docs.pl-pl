---
title: StrongNameTokenFromAssembly — Funkcja
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromAssembly
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameTokenFromAssembly
helpviewer_keywords:
- StrongNameTokenFromAssembly function [.NET Framework strong naming]
ms.assetid: 0a4b47ee-02f6-4a98-864e-a6f11ca3f2d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 484dacd4d9803139edf3fd5bad22c164d50de3dc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757239"
---
# <a name="strongnametokenfromassembly-function"></a><span data-ttu-id="a1062-102">StrongNameTokenFromAssembly — Funkcja</span><span class="sxs-lookup"><span data-stu-id="a1062-102">StrongNameTokenFromAssembly Function</span></span>
<span data-ttu-id="a1062-103">Tworzy token silnej nazwy z określonego pliku zestawu.</span><span class="sxs-lookup"><span data-stu-id="a1062-103">Creates a strong name token from the specified assembly file.</span></span>  
  
 <span data-ttu-id="a1062-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="a1062-104">This function has been deprecated.</span></span> <span data-ttu-id="a1062-105">Użyj [iclrstrongname::strongnametokenfromassembly —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="a1062-105">Use the [ICLRStrongName::StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1062-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="a1062-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1062-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="a1062-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="a1062-108">[in] Ścieżka do pliku wykonalnego (PE) pliku zestawu.</span><span class="sxs-lookup"><span data-stu-id="a1062-108">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="a1062-109">[out] Token zwracany silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="a1062-109">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="a1062-110">[out] Rozmiar w bajtach, token silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="a1062-110">[out] The size, in bytes, of the strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a1062-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a1062-111">Return Value</span></span>  
 <span data-ttu-id="a1062-112">`true` Po pomyślnym zakończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="a1062-112">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1062-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a1062-113">Remarks</span></span>  
 <span data-ttu-id="a1062-114">Token silna nazwa jest skrócona forma klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="a1062-114">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="a1062-115">Token jest 64-bitową wartość skrótu, utworzona na podstawie klucza publicznego używany do podpisywania zestawu.</span><span class="sxs-lookup"><span data-stu-id="a1062-115">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="a1062-116">Token jest częścią silnej nazwy zestawu i może zostać odczytany z metadanych zestawu.</span><span class="sxs-lookup"><span data-stu-id="a1062-116">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="a1062-117">Po utworzeniu tokenu należy wywołać [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) funkcję, aby zwolnić alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="a1062-117">After the token is created, you should call the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="a1062-118">Jeśli `StrongNameTokenFromAssembly` funkcja nie jest ukończone pomyślnie, wywołaj [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcję, aby pobrać ostatni błąd wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="a1062-118">If the `StrongNameTokenFromAssembly` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1062-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a1062-119">Requirements</span></span>  
 <span data-ttu-id="a1062-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1062-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1062-121">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="a1062-121">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="a1062-122">**Biblioteka:** Dołączony jako zasób w mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="a1062-122">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="a1062-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1062-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1062-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a1062-124">See also</span></span>

- [<span data-ttu-id="a1062-125">StrongNameTokenFromAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="a1062-125">StrongNameTokenFromAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [<span data-ttu-id="a1062-126">StrongNameTokenFromAssemblyEx, metoda</span><span class="sxs-lookup"><span data-stu-id="a1062-126">StrongNameTokenFromAssemblyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [<span data-ttu-id="a1062-127">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="a1062-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
