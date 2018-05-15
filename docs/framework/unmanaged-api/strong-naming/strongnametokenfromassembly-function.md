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
ms.openlocfilehash: 5f04d71e1709eed6c3a9f1af400f79b4722f4433
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="strongnametokenfromassembly-function"></a><span data-ttu-id="19996-102">StrongNameTokenFromAssembly — Funkcja</span><span class="sxs-lookup"><span data-stu-id="19996-102">StrongNameTokenFromAssembly Function</span></span>
<span data-ttu-id="19996-103">Tworzy token silnej nazwy z określonego pliku zestawu.</span><span class="sxs-lookup"><span data-stu-id="19996-103">Creates a strong name token from the specified assembly file.</span></span>  
  
 <span data-ttu-id="19996-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="19996-104">This function has been deprecated.</span></span> <span data-ttu-id="19996-105">Użyj [ICLRStrongName::StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="19996-105">Use the [ICLRStrongName::StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19996-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="19996-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="19996-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="19996-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="19996-108">[in] Ścieżka do pliku wykonywalnego przenośnego (PE) dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="19996-108">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="19996-109">[out] Token zwrócony silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="19996-109">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="19996-110">[out] Rozmiar w bajtach tokenu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="19996-110">[out] The size, in bytes, of the strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="19996-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="19996-111">Return Value</span></span>  
 <span data-ttu-id="19996-112">`true` Po pomyślnym ukończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="19996-112">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19996-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="19996-113">Remarks</span></span>  
 <span data-ttu-id="19996-114">Token silnej nazwy jest skrócona forma klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="19996-114">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="19996-115">Token jest 64-bitową wartość skrótu, utworzona na podstawie klucza publicznego używany do podpisywania zestawu.</span><span class="sxs-lookup"><span data-stu-id="19996-115">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="19996-116">Token jest częścią silnej nazwy zestawu i może zostać odczytany z metadanych zestawu.</span><span class="sxs-lookup"><span data-stu-id="19996-116">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="19996-117">Po utworzeniu token, należy wywołać [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) funkcji, aby zwolnić alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="19996-117">After the token is created, you should call the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="19996-118">Jeśli `StrongNameTokenFromAssembly` funkcji nie powiodło się, wywołania [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcji, aby pobrać ostatniego wygenerowany błąd.</span><span class="sxs-lookup"><span data-stu-id="19996-118">If the `StrongNameTokenFromAssembly` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19996-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="19996-119">Requirements</span></span>  
 <span data-ttu-id="19996-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19996-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19996-121">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="19996-121">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="19996-122">**Biblioteka:** uwzględnione jako zasób w mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="19996-122">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="19996-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19996-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19996-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="19996-124">See Also</span></span>  
 [<span data-ttu-id="19996-125">StrongNameTokenFromAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="19996-125">StrongNameTokenFromAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)  
 [<span data-ttu-id="19996-126">StrongNameTokenFromAssemblyEx, metoda</span><span class="sxs-lookup"><span data-stu-id="19996-126">StrongNameTokenFromAssemblyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)  
 [<span data-ttu-id="19996-127">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="19996-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
