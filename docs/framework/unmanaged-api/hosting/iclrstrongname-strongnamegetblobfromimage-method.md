---
title: "ICLRStrongName::StrongNameGetBlobFromImage — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameGetBlobFromImage
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameGetBlobFromImage
helpviewer_keywords:
- StrongNameGetBlobFromImage method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameGetBlobFromImage method [.NET Framework hosting]
ms.assetid: 0f5a2ec8-e776-4fd8-bda6-937b6834575a
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ff2ec30068903397d9f8d736f4f270c8d3c1669f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnamegetblobfromimage-method"></a><span data-ttu-id="4b3dd-102">ICLRStrongName::StrongNameGetBlobFromImage — Metoda</span><span class="sxs-lookup"><span data-stu-id="4b3dd-102">ICLRStrongName::StrongNameGetBlobFromImage Method</span></span>
<span data-ttu-id="4b3dd-103">Pobiera zestawu obraz to binarna reprezentacja pod adresem określonym pamięci.</span><span class="sxs-lookup"><span data-stu-id="4b3dd-103">Gets a binary representation of the assembly image at the specified memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b3dd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4b3dd-104">Syntax</span></span>  
  
```  
HRESULT StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4b3dd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4b3dd-105">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="4b3dd-106">[in] Adres pamięci manifest zestawu mapowane.</span><span class="sxs-lookup"><span data-stu-id="4b3dd-106">[in] The memory address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="4b3dd-107">[in] Rozmiar w bajtach obrazu w `pbBase`.</span><span class="sxs-lookup"><span data-stu-id="4b3dd-107">[in] The size, in bytes, of the image at `pbBase`.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="4b3dd-108">[in] Bufor zawiera binarna reprezentacja obrazu.</span><span class="sxs-lookup"><span data-stu-id="4b3dd-108">[in] A buffer to contain the binary representation of the image.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="4b3dd-109">[w, out] Żądane maksymalny rozmiar w bajtach `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="4b3dd-109">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="4b3dd-110">Po powrocie, rzeczywisty rozmiar w bajtach z `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="4b3dd-110">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4b3dd-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4b3dd-111">Return Value</span></span>  
 <span data-ttu-id="4b3dd-112">`S_OK`Jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje niepowodzenie (zobacz [wspólne wartości HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) lista).</span><span class="sxs-lookup"><span data-stu-id="4b3dd-112">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b3dd-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4b3dd-113">Requirements</span></span>  
 <span data-ttu-id="4b3dd-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b3dd-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b3dd-115">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="4b3dd-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="4b3dd-116">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4b3dd-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4b3dd-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b3dd-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b3dd-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4b3dd-118">See Also</span></span>  
 [<span data-ttu-id="4b3dd-119">StrongNameGetBlob, metoda</span><span class="sxs-lookup"><span data-stu-id="4b3dd-119">StrongNameGetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)  
 [<span data-ttu-id="4b3dd-120">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="4b3dd-120">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
