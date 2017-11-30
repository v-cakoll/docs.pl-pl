---
title: "IMetaDataAssemblyImport::EnumAssemblyRefs — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.EnumAssemblyRefs
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::EnumAssemblyRefs
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs method [.NET Framework metadata]
- EnumAssemblyRefs method [.NET Framework metadata]
ms.assetid: 8844d0dd-730e-4592-8a7b-c1462d312c70
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 24a289ed42a99cd26c7829d9a5789ac3027026c0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyimportenumassemblyrefs-method"></a><span data-ttu-id="af0df-102">IMetaDataAssemblyImport::EnumAssemblyRefs — Metoda</span><span class="sxs-lookup"><span data-stu-id="af0df-102">IMetaDataAssemblyImport::EnumAssemblyRefs Method</span></span>
<span data-ttu-id="af0df-103">Wylicza `mdAssemblyRef` wystąpień, które są zdefiniowane w manifeście zestawu.</span><span class="sxs-lookup"><span data-stu-id="af0df-103">Enumerates the `mdAssemblyRef` instances that are defined in the assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af0df-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="af0df-104">Syntax</span></span>  
  
```  
HRESULT EnumAssemblyRefs (  
    [in, out] HCORENUM        *phEnum,   
    [out]     mdAssemblyRef   rAssemblyRefs[],   
    [in]      ULONG           cMax,   
    [out]     ULONG           *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="af0df-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="af0df-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="af0df-106">[w, out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="af0df-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="af0df-107">Musi to być wartość null wartość przy `EnumAssemblyRefs` metoda jest wywoływana po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="af0df-107">This must be a null value when the `EnumAssemblyRefs` method is called for the first time.</span></span>  
  
 `rAssemblyRefs`  
 <span data-ttu-id="af0df-108">[out] Wyliczanie `mdAssemblyRef` tokenów metadanych.</span><span class="sxs-lookup"><span data-stu-id="af0df-108">[out] The enumeration of `mdAssemblyRef` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="af0df-109">[in] Maksymalna liczba tokenów, które można umieścić w `rAssemblyRefs` tablicy.</span><span class="sxs-lookup"><span data-stu-id="af0df-109">[in] The maximum number of tokens that can be placed in the `rAssemblyRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="af0df-110">[out] Liczba tokenów faktycznie umieszczonych w `rAssemblyRefs`.</span><span class="sxs-lookup"><span data-stu-id="af0df-110">[out] The number of tokens actually placed in `rAssemblyRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="af0df-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="af0df-111">Return Value</span></span>  
  
|<span data-ttu-id="af0df-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="af0df-112">HRESULT</span></span>|<span data-ttu-id="af0df-113">Opis</span><span class="sxs-lookup"><span data-stu-id="af0df-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="af0df-114">`EnumAssemblyRefs`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="af0df-114">`EnumAssemblyRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="af0df-115">Nie ma żadnych tokenów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="af0df-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="af0df-116">W takim przypadku `pcTokens` jest ustawiony na zero.</span><span class="sxs-lookup"><span data-stu-id="af0df-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="af0df-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="af0df-117">Requirements</span></span>  
 <span data-ttu-id="af0df-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af0df-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af0df-119">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="af0df-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="af0df-120">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="af0df-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="af0df-121">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af0df-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af0df-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="af0df-122">See Also</span></span>  
 [<span data-ttu-id="af0df-123">IMetaDataAssemblyImport — interfejs</span><span class="sxs-lookup"><span data-stu-id="af0df-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
