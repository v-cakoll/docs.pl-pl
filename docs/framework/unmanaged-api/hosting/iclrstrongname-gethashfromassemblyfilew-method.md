---
title: "ICLRStrongName::GetHashFromAssemblyFileW — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.GetHashFromAssemblyFileW
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::GetHashFromAssemblyFileW
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFileW method [.NET Framework hosting]
- GetHashFromAssemblyFileW method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5d0b44a2-5a14-44a2-9a0e-e8682fd4e106
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 14b4e6dae97777873f458018acdaf0c3f5d4f070
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongnamegethashfromassemblyfilew-method"></a><span data-ttu-id="c7cf9-102">ICLRStrongName::GetHashFromAssemblyFileW — Metoda</span><span class="sxs-lookup"><span data-stu-id="c7cf9-102">ICLRStrongName::GetHashFromAssemblyFileW Method</span></span>
<span data-ttu-id="c7cf9-103">Generuje skrót za pośrednictwem zawartość pliku określona przez ciąg Unicode.</span><span class="sxs-lookup"><span data-stu-id="c7cf9-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7cf9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c7cf9-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c7cf9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c7cf9-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="c7cf9-106">[in] Ścieżka do pliku, aby być mieszany.</span><span class="sxs-lookup"><span data-stu-id="c7cf9-106">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="c7cf9-107">Ten parametr musi być ciągiem Unicode.</span><span class="sxs-lookup"><span data-stu-id="c7cf9-107">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="c7cf9-108">[w, out] Stała, który określa algorytm wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="c7cf9-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="c7cf9-109">Użyj wartości zero dla domyślny algorytm skrótu.</span><span class="sxs-lookup"><span data-stu-id="c7cf9-109">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="c7cf9-110">[out] Bufor zwrócony wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="c7cf9-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="c7cf9-111">[in] Maksymalny rozmiar żądanej z `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="c7cf9-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="c7cf9-112">[out] Zwrócony rozmiar w bajtach z `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="c7cf9-112">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c7cf9-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c7cf9-113">Return Value</span></span>  
 <span data-ttu-id="c7cf9-114">`S_OK`Jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje niepowodzenie (zobacz [wspólne wartości HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) lista).</span><span class="sxs-lookup"><span data-stu-id="c7cf9-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7cf9-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c7cf9-115">Requirements</span></span>  
 <span data-ttu-id="c7cf9-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7cf9-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7cf9-117">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="c7cf9-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c7cf9-118">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c7cf9-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c7cf9-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7cf9-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7cf9-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c7cf9-120">See Also</span></span>  
 [<span data-ttu-id="c7cf9-121">GetHashFromAssemblyFile — metoda</span><span class="sxs-lookup"><span data-stu-id="c7cf9-121">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)  
 [<span data-ttu-id="c7cf9-122">ICLRStrongName — interfejs</span><span class="sxs-lookup"><span data-stu-id="c7cf9-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
