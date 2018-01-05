---
title: "ICLRStrongName::StrongNameGetBlob — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRStrongName.StrongNameGetBlob
- ICLRStrongName.StrongNameGetBlob
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameGetBlob
helpviewer_keywords:
- ICLRStrongName::StrongNameGetBlob method [.NET Framework hosting]
- StrongNameGetBlob method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: a24218f8-7196-44be-b7a2-ee9cdd7a85c4
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f1882936723667b616ff930af00ee899f446521e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnamegetblob-method"></a><span data-ttu-id="f91cb-102">ICLRStrongName::StrongNameGetBlob — Metoda</span><span class="sxs-lookup"><span data-stu-id="f91cb-102">ICLRStrongName::StrongNameGetBlob Method</span></span>
<span data-ttu-id="f91cb-103">Wstawia określony bufor binarna reprezentacja pliku wykonywalnego pod określonym adresem.</span><span class="sxs-lookup"><span data-stu-id="f91cb-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f91cb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f91cb-104">Syntax</span></span>  
  
```  
HRESULT StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f91cb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f91cb-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="f91cb-106">[in] Nieprawidłowa ścieżka do pliku wykonywalnego do załadowania.</span><span class="sxs-lookup"><span data-stu-id="f91cb-106">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="f91cb-107">[in] Bufor, do którego można załadować pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="f91cb-107">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="f91cb-108">[w, out] Żądane maksymalny rozmiar w bajtach `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="f91cb-108">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="f91cb-109">Po powrocie, rzeczywisty rozmiar w bajtach z `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="f91cb-109">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f91cb-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f91cb-110">Return Value</span></span>  
 <span data-ttu-id="f91cb-111">`S_OK`Jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje niepowodzenie (zobacz [wspólne wartości HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) lista).</span><span class="sxs-lookup"><span data-stu-id="f91cb-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f91cb-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f91cb-112">Requirements</span></span>  
 <span data-ttu-id="f91cb-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f91cb-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f91cb-114">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="f91cb-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f91cb-115">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f91cb-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f91cb-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f91cb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f91cb-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f91cb-117">See Also</span></span>  
 [<span data-ttu-id="f91cb-118">StrongNameGetBlobFromImage, metoda</span><span class="sxs-lookup"><span data-stu-id="f91cb-118">StrongNameGetBlobFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)  
 [<span data-ttu-id="f91cb-119">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="f91cb-119">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
