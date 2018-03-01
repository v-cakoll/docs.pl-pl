---
title: "ICLRStrongName::StrongNameTokenFromAssemblyEx — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5b8b3437d8c07cd57a4791995890cab1b06aafc6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnametokenfromassemblyex-method"></a><span data-ttu-id="73df8-102">ICLRStrongName::StrongNameTokenFromAssemblyEx — Metoda</span><span class="sxs-lookup"><span data-stu-id="73df8-102">ICLRStrongName::StrongNameTokenFromAssemblyEx Method</span></span>
<span data-ttu-id="73df8-103">Tworzy token silnej nazwy z określonego pliku zestawu i zwraca klucz publiczny, który reprezentuje token.</span><span class="sxs-lookup"><span data-stu-id="73df8-103">Creates a strong name token from the specified assembly file, and returns the public key that the token represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73df8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="73df8-104">Syntax</span></span>  
  
```  
HRESULT StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="73df8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="73df8-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="73df8-106">[in] Ścieżka do pliku wykonywalnego przenośnego (PE) dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="73df8-106">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="73df8-107">[out] Token zwrócony silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="73df8-107">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="73df8-108">[out] Rozmiar w bajtach tokenu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="73df8-108">[out] The size, in bytes, of the strong name token.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="73df8-109">[out] Zwrócony klucz publiczny.</span><span class="sxs-lookup"><span data-stu-id="73df8-109">[out] The returned public key.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="73df8-110">[out] Rozmiar w bajtach klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="73df8-110">[out] The size, in bytes, of the public key.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="73df8-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="73df8-111">Return Value</span></span>  
 <span data-ttu-id="73df8-112">`S_OK`Jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje niepowodzenie (zobacz [wspólne wartości HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) lista).</span><span class="sxs-lookup"><span data-stu-id="73df8-112">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73df8-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="73df8-113">Remarks</span></span>  
 <span data-ttu-id="73df8-114">Token silnej nazwy jest skrócona forma klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="73df8-114">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="73df8-115">Token jest 64-bitową wartość skrótu, utworzona na podstawie klucza publicznego używany do podpisywania zestawu.</span><span class="sxs-lookup"><span data-stu-id="73df8-115">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="73df8-116">Token jest częścią silnej nazwy zestawu i może zostać odczytany z metadanych zestawu.</span><span class="sxs-lookup"><span data-stu-id="73df8-116">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="73df8-117">Po klucz jest pobierana i jest tworzony token, należy wywołać [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metodę, aby zwolnić alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="73df8-117">After the key is retrieved and the token is created, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73df8-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="73df8-118">Requirements</span></span>  
 <span data-ttu-id="73df8-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73df8-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73df8-120">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="73df8-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="73df8-121">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="73df8-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="73df8-122">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73df8-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73df8-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="73df8-123">See Also</span></span>  
 [<span data-ttu-id="73df8-124">StrongNameTokenFromAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="73df8-124">StrongNameTokenFromAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)  
 [<span data-ttu-id="73df8-125">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="73df8-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
