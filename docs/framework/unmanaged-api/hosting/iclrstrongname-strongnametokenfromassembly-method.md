---
title: "ICLRStrongName::StrongNameTokenFromAssembly — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameTokenFromAssembly
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameTokenFromAssembly
helpviewer_keywords:
- ICLRStrongName::StrongNameTokenFromAssembly method [.NET Framework hosting]
- StrongNameTokenFromAssembly method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: fc725afb-b66b-4015-aa44-1c0d1304197f
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 455a04c3c5465ec263c5d2131ac8f3c4e34ea610
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnametokenfromassembly-method"></a><span data-ttu-id="e8ea2-102">ICLRStrongName::StrongNameTokenFromAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="e8ea2-102">ICLRStrongName::StrongNameTokenFromAssembly Method</span></span>
<span data-ttu-id="e8ea2-103">Tworzy token silnej nazwy z określonego pliku zestawu.</span><span class="sxs-lookup"><span data-stu-id="e8ea2-103">Creates a strong name token from the specified assembly file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8ea2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e8ea2-104">Syntax</span></span>  
  
```  
HRESULT StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e8ea2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e8ea2-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="e8ea2-106">[in] Ścieżka do pliku wykonywalnego przenośnego (PE) dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="e8ea2-106">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="e8ea2-107">[out] Token zwrócony silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="e8ea2-107">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="e8ea2-108">[out] Rozmiar w bajtach tokenu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="e8ea2-108">[out] The size, in bytes, of the strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e8ea2-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e8ea2-109">Return Value</span></span>  
 <span data-ttu-id="e8ea2-110">`S_OK`Jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje niepowodzenie (zobacz [wspólne wartości HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) lista).</span><span class="sxs-lookup"><span data-stu-id="e8ea2-110">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8ea2-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e8ea2-111">Remarks</span></span>  
 <span data-ttu-id="e8ea2-112">Token silnej nazwy jest skrócona forma klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="e8ea2-112">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="e8ea2-113">Token jest 64-bitową wartość skrótu, utworzona na podstawie klucza publicznego używany do podpisywania zestawu.</span><span class="sxs-lookup"><span data-stu-id="e8ea2-113">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="e8ea2-114">Token jest częścią silnej nazwy zestawu i może zostać odczytany z metadanych zestawu.</span><span class="sxs-lookup"><span data-stu-id="e8ea2-114">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="e8ea2-115">Po utworzeniu token, należy wywołać [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metodę, aby zwolnić alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="e8ea2-115">After the token is created, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8ea2-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e8ea2-116">Requirements</span></span>  
 <span data-ttu-id="e8ea2-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8ea2-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8ea2-118">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="e8ea2-118">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e8ea2-119">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e8ea2-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e8ea2-120">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8ea2-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8ea2-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e8ea2-121">See Also</span></span>  
 [<span data-ttu-id="e8ea2-122">StrongNameTokenFromAssemblyEx, metoda</span><span class="sxs-lookup"><span data-stu-id="e8ea2-122">StrongNameTokenFromAssemblyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)  
 [<span data-ttu-id="e8ea2-123">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="e8ea2-123">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
