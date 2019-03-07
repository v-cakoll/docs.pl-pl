---
title: ICLRStrongName::StrongNameTokenFromAssembly — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromAssembly
helpviewer_keywords:
- ICLRStrongName::StrongNameTokenFromAssembly method [.NET Framework hosting]
- StrongNameTokenFromAssembly method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: fc725afb-b66b-4015-aa44-1c0d1304197f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 78c7ee4073357af09bdd3b0edd3d848458069da9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484813"
---
# <a name="iclrstrongnamestrongnametokenfromassembly-method"></a><span data-ttu-id="7ff3e-102">ICLRStrongName::StrongNameTokenFromAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="7ff3e-102">ICLRStrongName::StrongNameTokenFromAssembly Method</span></span>
<span data-ttu-id="7ff3e-103">Tworzy token silnej nazwy z określonego pliku zestawu.</span><span class="sxs-lookup"><span data-stu-id="7ff3e-103">Creates a strong name token from the specified assembly file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ff3e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7ff3e-104">Syntax</span></span>  
  
```  
HRESULT StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ff3e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7ff3e-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="7ff3e-106">[in] Ścieżka do pliku wykonalnego (PE) pliku zestawu.</span><span class="sxs-lookup"><span data-stu-id="7ff3e-106">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="7ff3e-107">[out] Token zwracany silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="7ff3e-107">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="7ff3e-108">[out] Rozmiar w bajtach, token silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="7ff3e-108">[out] The size, in bytes, of the strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7ff3e-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7ff3e-109">Return Value</span></span>  
 <span data-ttu-id="7ff3e-110">`S_OK` Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje błąd (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).</span><span class="sxs-lookup"><span data-stu-id="7ff3e-110">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ff3e-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7ff3e-111">Remarks</span></span>  
 <span data-ttu-id="7ff3e-112">Token silna nazwa jest skrócona forma klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="7ff3e-112">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="7ff3e-113">Token jest 64-bitową wartość skrótu, utworzona na podstawie klucza publicznego używany do podpisywania zestawu.</span><span class="sxs-lookup"><span data-stu-id="7ff3e-113">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="7ff3e-114">Token jest częścią silnej nazwy zestawu i może zostać odczytany z metadanych zestawu.</span><span class="sxs-lookup"><span data-stu-id="7ff3e-114">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="7ff3e-115">Po utworzeniu tokenu należy wywołać [iclrstrongname::strongnamefreebuffer —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metodę, aby zwolnić alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="7ff3e-115">After the token is created, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ff3e-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7ff3e-116">Requirements</span></span>  
 <span data-ttu-id="7ff3e-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ff3e-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ff3e-118">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="7ff3e-118">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7ff3e-119">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7ff3e-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7ff3e-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ff3e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ff3e-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7ff3e-121">See also</span></span>
- [<span data-ttu-id="7ff3e-122">StrongNameTokenFromAssemblyEx, metoda</span><span class="sxs-lookup"><span data-stu-id="7ff3e-122">StrongNameTokenFromAssemblyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [<span data-ttu-id="7ff3e-123">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="7ff3e-123">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
