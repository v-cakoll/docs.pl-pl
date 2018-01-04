---
title: "IMetaDataDispenserEx::GetCORSystemDirectory — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenserEx.GetCORSystemDirectory
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenserEx::GetCORSystemDirectory
helpviewer_keywords:
- IMetaDataDispenserEx::GetCORSystemDirectory method [.NET Framework metadata]
- GetCORSystemDirectory method [.NET Framework metadata]
ms.assetid: d9e0f3b6-e106-4820-bada-5bfba34ce360
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e93f544e504949b496881369c15905ef43a0d2f6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatadispenserexgetcorsystemdirectory-method"></a><span data-ttu-id="ef676-102">IMetaDataDispenserEx::GetCORSystemDirectory — Metoda</span><span class="sxs-lookup"><span data-stu-id="ef676-102">IMetaDataDispenserEx::GetCORSystemDirectory Method</span></span>
<span data-ttu-id="ef676-103">Pobiera katalog, który zawiera bieżące środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="ef676-103">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="ef676-104">Ta metoda jest obsługiwana tylko przez debugery poza procesem.</span><span class="sxs-lookup"><span data-stu-id="ef676-104">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="ef676-105">Wywoływane z innego składnika, zwróci E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="ef676-105">If called from another component, it will return E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef676-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="ef676-106">Syntax</span></span>  
  
```  
HRESULT GetCORSystemDirectory (  
    [out] LPWSTR      szBuffer,   
    [in]  DWORD       cchBuffer,   
    [out] DWORD*      pchBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ef676-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="ef676-107">Parameters</span></span>  
 `szBuffer`  
 <span data-ttu-id="ef676-108">[out] Bufor odbioru nazwę katalogu.</span><span class="sxs-lookup"><span data-stu-id="ef676-108">[out] The buffer to receive the directory name.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="ef676-109">[in] Rozmiar w bajtach z `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="ef676-109">[in] The size, in bytes, of `szBuffer`.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="ef676-110">[out] Liczba bajtów zwrócona faktycznie w `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="ef676-110">[out] The number of bytes actually returned in `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef676-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ef676-111">Requirements</span></span>  
 <span data-ttu-id="ef676-112">**Platforma:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef676-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef676-113">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ef676-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ef676-114">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ef676-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ef676-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef676-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef676-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ef676-116">See Also</span></span>  
 [<span data-ttu-id="ef676-117">IMetaDataDispenserEx, interfejs</span><span class="sxs-lookup"><span data-stu-id="ef676-117">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="ef676-118">IMetaDataDispenser, interfejs</span><span class="sxs-lookup"><span data-stu-id="ef676-118">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
