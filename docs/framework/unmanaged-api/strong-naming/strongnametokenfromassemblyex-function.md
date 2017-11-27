---
title: "StrongNameTokenFromAssemblyEx — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameTokenFromAssemblyEx
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameTokenFromAssemblyEx
helpviewer_keywords: StrongNameTokenFromAssemblyEx function [.NET Framework strong naming]
ms.assetid: 67a8a9f2-dee3-44b2-a1c0-f307a3bdf90f
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ef530595d92995124c590e70ac5ffc32a228c67a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="strongnametokenfromassemblyex-function"></a><span data-ttu-id="d076d-102">StrongNameTokenFromAssemblyEx — Funkcja</span><span class="sxs-lookup"><span data-stu-id="d076d-102">StrongNameTokenFromAssemblyEx Function</span></span>
<span data-ttu-id="d076d-103">Tworzy token silnej nazwy z określonego pliku zestawu i zwraca klucz publiczny, który reprezentuje token.</span><span class="sxs-lookup"><span data-stu-id="d076d-103">Creates a strong name token from the specified assembly file, and returns the public key that the token represents.</span></span>  
  
 <span data-ttu-id="d076d-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="d076d-104">This function has been deprecated.</span></span> <span data-ttu-id="d076d-105">Użyj [ICLRStrongName::StrongNameTokenFromAssemblyEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="d076d-105">Use the [ICLRStrongName::StrongNameTokenFromAssemblyEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d076d-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="d076d-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d076d-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="d076d-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="d076d-108">[in] Ścieżka do pliku wykonywalnego przenośnego (PE) dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="d076d-108">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="d076d-109">[out] Token zwrócony silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="d076d-109">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="d076d-110">[out] Rozmiar w bajtach tokenu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="d076d-110">[out] The size, in bytes, of the strong name token.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="d076d-111">[out] Zwrócony klucz publiczny.</span><span class="sxs-lookup"><span data-stu-id="d076d-111">[out] The returned public key.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="d076d-112">[out] Rozmiar w bajtach klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="d076d-112">[out] The size, in bytes, of the public key.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d076d-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d076d-113">Return Value</span></span>  
 <span data-ttu-id="d076d-114">`true`Po pomyślnym ukończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="d076d-114">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d076d-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d076d-115">Remarks</span></span>  
 <span data-ttu-id="d076d-116">Token silnej nazwy jest skrócona forma klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="d076d-116">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="d076d-117">Token jest 64-bitową wartość skrótu, utworzona na podstawie klucza publicznego używany do podpisywania zestawu.</span><span class="sxs-lookup"><span data-stu-id="d076d-117">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="d076d-118">Token jest częścią silnej nazwy zestawu i może zostać odczytany z metadanych zestawu.</span><span class="sxs-lookup"><span data-stu-id="d076d-118">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="d076d-119">Po klucz jest pobierana i jest tworzony token, należy wywołać [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) funkcji, aby zwolnić alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="d076d-119">After the key is retrieved and the token is created, you should call the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="d076d-120">Jeśli `StrongNameTokenFromAssemblyEx` funkcji nie powiodło się, wywołania [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcji, aby pobrać ostatniego wygenerowany błąd.</span><span class="sxs-lookup"><span data-stu-id="d076d-120">If the `StrongNameTokenFromAssemblyEx` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d076d-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d076d-121">Requirements</span></span>  
 <span data-ttu-id="d076d-122">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d076d-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d076d-123">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="d076d-123">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="d076d-124">**Biblioteka:** uwzględnione jako zasób w mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="d076d-124">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="d076d-125">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d076d-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d076d-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d076d-126">See Also</span></span>  
 [<span data-ttu-id="d076d-127">StrongNameTokenFromAssemblyEx — metoda</span><span class="sxs-lookup"><span data-stu-id="d076d-127">StrongNameTokenFromAssemblyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)  
 [<span data-ttu-id="d076d-128">StrongNameTokenFromAssembly — metoda</span><span class="sxs-lookup"><span data-stu-id="d076d-128">StrongNameTokenFromAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)  
 [<span data-ttu-id="d076d-129">ICLRStrongName — interfejs</span><span class="sxs-lookup"><span data-stu-id="d076d-129">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
