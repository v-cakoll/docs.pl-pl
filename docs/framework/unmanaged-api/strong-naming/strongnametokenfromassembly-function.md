---
title: "StrongNameTokenFromAssembly — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameTokenFromAssembly
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameTokenFromAssembly
helpviewer_keywords: StrongNameTokenFromAssembly function [.NET Framework strong naming]
ms.assetid: 0a4b47ee-02f6-4a98-864e-a6f11ca3f2d9
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a4d3e17f1dedd6ab346f3773f49b89d486b66e25
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="strongnametokenfromassembly-function"></a><span data-ttu-id="35240-102">StrongNameTokenFromAssembly — Funkcja</span><span class="sxs-lookup"><span data-stu-id="35240-102">StrongNameTokenFromAssembly Function</span></span>
<span data-ttu-id="35240-103">Tworzy token silnej nazwy z określonego pliku zestawu.</span><span class="sxs-lookup"><span data-stu-id="35240-103">Creates a strong name token from the specified assembly file.</span></span>  
  
 <span data-ttu-id="35240-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="35240-104">This function has been deprecated.</span></span> <span data-ttu-id="35240-105">Użyj [ICLRStrongName::StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="35240-105">Use the [ICLRStrongName::StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35240-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="35240-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="35240-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="35240-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="35240-108">[in] Ścieżka do pliku wykonywalnego przenośnego (PE) dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="35240-108">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="35240-109">[out] Token zwrócony silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="35240-109">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="35240-110">[out] Rozmiar w bajtach tokenu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="35240-110">[out] The size, in bytes, of the strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="35240-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="35240-111">Return Value</span></span>  
 <span data-ttu-id="35240-112">`true`Po pomyślnym ukończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="35240-112">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35240-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="35240-113">Remarks</span></span>  
 <span data-ttu-id="35240-114">Token silnej nazwy jest skrócona forma klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="35240-114">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="35240-115">Token jest 64-bitową wartość skrótu, utworzona na podstawie klucza publicznego używany do podpisywania zestawu.</span><span class="sxs-lookup"><span data-stu-id="35240-115">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="35240-116">Token jest częścią silnej nazwy zestawu i może zostać odczytany z metadanych zestawu.</span><span class="sxs-lookup"><span data-stu-id="35240-116">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="35240-117">Po utworzeniu token, należy wywołać [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) funkcji, aby zwolnić alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="35240-117">After the token is created, you should call the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="35240-118">Jeśli `StrongNameTokenFromAssembly` funkcji nie powiodło się, wywołania [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcji, aby pobrać ostatniego wygenerowany błąd.</span><span class="sxs-lookup"><span data-stu-id="35240-118">If the `StrongNameTokenFromAssembly` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35240-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="35240-119">Requirements</span></span>  
 <span data-ttu-id="35240-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35240-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35240-121">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="35240-121">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="35240-122">**Biblioteka:** uwzględnione jako zasób w mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="35240-122">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="35240-123">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35240-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35240-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="35240-124">See Also</span></span>  
 [<span data-ttu-id="35240-125">StrongNameTokenFromAssembly — metoda</span><span class="sxs-lookup"><span data-stu-id="35240-125">StrongNameTokenFromAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)  
 [<span data-ttu-id="35240-126">StrongNameTokenFromAssemblyEx — metoda</span><span class="sxs-lookup"><span data-stu-id="35240-126">StrongNameTokenFromAssemblyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)  
 [<span data-ttu-id="35240-127">ICLRStrongName — interfejs</span><span class="sxs-lookup"><span data-stu-id="35240-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
