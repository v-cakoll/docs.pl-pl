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
ms.openlocfilehash: 46d8013d43dc14807804502e4a0820a2928f917e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499241"
---
# <a name="strongnametokenfromassembly-function"></a><span data-ttu-id="948f4-102">StrongNameTokenFromAssembly — Funkcja</span><span class="sxs-lookup"><span data-stu-id="948f4-102">StrongNameTokenFromAssembly Function</span></span>
<span data-ttu-id="948f4-103">Tworzy token silnej nazwy z określonego pliku zestawu.</span><span class="sxs-lookup"><span data-stu-id="948f4-103">Creates a strong name token from the specified assembly file.</span></span>  
  
 <span data-ttu-id="948f4-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="948f4-104">This function has been deprecated.</span></span> <span data-ttu-id="948f4-105">Użyj [iclrstrongname::strongnametokenfromassembly —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="948f4-105">Use the [ICLRStrongName::StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="948f4-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="948f4-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="948f4-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="948f4-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="948f4-108">[in] Ścieżka do pliku wykonalnego (PE) pliku zestawu.</span><span class="sxs-lookup"><span data-stu-id="948f4-108">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="948f4-109">[out] Token zwracany silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="948f4-109">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="948f4-110">[out] Rozmiar w bajtach, token silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="948f4-110">[out] The size, in bytes, of the strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="948f4-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="948f4-111">Return Value</span></span>  
 <span data-ttu-id="948f4-112">`true` Po pomyślnym zakończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="948f4-112">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="948f4-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="948f4-113">Remarks</span></span>  
 <span data-ttu-id="948f4-114">Token silna nazwa jest skrócona forma klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="948f4-114">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="948f4-115">Token jest 64-bitową wartość skrótu, utworzona na podstawie klucza publicznego używany do podpisywania zestawu.</span><span class="sxs-lookup"><span data-stu-id="948f4-115">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="948f4-116">Token jest częścią silnej nazwy zestawu i może zostać odczytany z metadanych zestawu.</span><span class="sxs-lookup"><span data-stu-id="948f4-116">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="948f4-117">Po utworzeniu tokenu należy wywołać [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) funkcję, aby zwolnić alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="948f4-117">After the token is created, you should call the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="948f4-118">Jeśli `StrongNameTokenFromAssembly` funkcja nie jest ukończone pomyślnie, wywołaj [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcję, aby pobrać ostatni błąd wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="948f4-118">If the `StrongNameTokenFromAssembly` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="948f4-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="948f4-119">Requirements</span></span>  
 <span data-ttu-id="948f4-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="948f4-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="948f4-121">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="948f4-121">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="948f4-122">**Biblioteka:** Dołączony jako zasób w mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="948f4-122">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="948f4-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="948f4-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="948f4-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="948f4-124">See also</span></span>
- [<span data-ttu-id="948f4-125">StrongNameTokenFromAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="948f4-125">StrongNameTokenFromAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [<span data-ttu-id="948f4-126">StrongNameTokenFromAssemblyEx, metoda</span><span class="sxs-lookup"><span data-stu-id="948f4-126">StrongNameTokenFromAssemblyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [<span data-ttu-id="948f4-127">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="948f4-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
