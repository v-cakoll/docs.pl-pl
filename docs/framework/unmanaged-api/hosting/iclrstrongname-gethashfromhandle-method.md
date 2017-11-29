---
title: "ICLRStrongName::GetHashFromHandle — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRStrongName.GetHashFromHandle
- ICLRStrongName.StrongNameCompareAssemblies
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::GetHashFromHandle
helpviewer_keywords:
- GetHashFromHandle method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromHandle method [.NET Framework hosting]
ms.assetid: 3bedbb7d-3cdd-4175-b370-10ae734062db
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 01fefe99e82584267b3c0f3e0e528dd798affa15
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="iclrstrongnamegethashfromhandle-method"></a><span data-ttu-id="1896e-102">ICLRStrongName::GetHashFromHandle — Metoda</span><span class="sxs-lookup"><span data-stu-id="1896e-102">ICLRStrongName::GetHashFromHandle Method</span></span>
<span data-ttu-id="1896e-103">Generuje skrót za pośrednictwem zawartości pliku, który ma określone dojście do pliku, przy użyciu algorytmu wyznaczania wartości skrótu określonej.</span><span class="sxs-lookup"><span data-stu-id="1896e-103">Generates a hash over the contents of the file that has the specified file handle, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1896e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1896e-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1896e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1896e-105">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="1896e-106">[in] Dojście do pliku, który ma być mieszany.</span><span class="sxs-lookup"><span data-stu-id="1896e-106">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="1896e-107">[w, out] Stała, który określa algorytm wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="1896e-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="1896e-108">Użyj wartości zero dla domyślnego algorytmu.</span><span class="sxs-lookup"><span data-stu-id="1896e-108">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="1896e-109">[out] Bufor zwrócony wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="1896e-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="1896e-110">[in] Maksymalny rozmiar żądanej z `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="1896e-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="1896e-111">[out] Rozmiar w bajtach, zwracana `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="1896e-111">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1896e-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1896e-112">Return Value</span></span>  
 <span data-ttu-id="1896e-113">`S_OK`Jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje niepowodzenie (zobacz [wspólne wartości HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) lista).</span><span class="sxs-lookup"><span data-stu-id="1896e-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1896e-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1896e-114">Requirements</span></span>  
 <span data-ttu-id="1896e-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1896e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1896e-116">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="1896e-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1896e-117">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1896e-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1896e-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1896e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1896e-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1896e-119">See Also</span></span>  
 [<span data-ttu-id="1896e-120">ICLRStrongName — interfejs</span><span class="sxs-lookup"><span data-stu-id="1896e-120">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
