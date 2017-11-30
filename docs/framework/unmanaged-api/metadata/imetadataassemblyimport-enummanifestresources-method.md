---
title: "IMetaDataAssemblyImport::EnumManifestResources — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.EnumManifestResources
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::EnumManifestResources
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumManifestResources method [.NET Framework metadata]
- EnumManifestResources method [.NET Framework metadata]
ms.assetid: 9543b111-5705-40c9-935c-a3ffc7a581aa
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 25d8b63e2f40566164274715e562960eafbb83e5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyimportenummanifestresources-method"></a><span data-ttu-id="9fe6d-102">IMetaDataAssemblyImport::EnumManifestResources — Metoda</span><span class="sxs-lookup"><span data-stu-id="9fe6d-102">IMetaDataAssemblyImport::EnumManifestResources Method</span></span>
<span data-ttu-id="9fe6d-103">Pobiera wskaźnik, aby moduł wyliczający dla zasobów w bieżącym manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="9fe6d-103">Gets a pointer to an enumerator for the resources referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fe6d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9fe6d-104">Syntax</span></span>  
  
```  
HRESULT EnumManifestResources (  
    [in, out] HCORENUM         *phEnum,   
    [out] mdManifestResource   rManifestResources[],   
    [in]  ULONG                cMax,   
    [out] ULONG                *pcTokens  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="9fe6d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9fe6d-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="9fe6d-106">[w, out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="9fe6d-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="9fe6d-107">Musi to być wartość null wartość przy `EnumManifestResources` metoda jest wywoływana po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="9fe6d-107">This must be a null value when the `EnumManifestResources` method is called for the first time.</span></span>  
  
 `rManifestResources`  
 <span data-ttu-id="9fe6d-108">[out] Tablica używany do przechowywania `mdManifestResource` tokenów metadanych.</span><span class="sxs-lookup"><span data-stu-id="9fe6d-108">[out] The array used to store the `mdManifestResource` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="9fe6d-109">[in] Maksymalna liczba `mdManifestResource` tokenów, które można umieścić w `rManifestResources`.</span><span class="sxs-lookup"><span data-stu-id="9fe6d-109">[in] The maximum number of `mdManifestResource` tokens that can be placed in `rManifestResources`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="9fe6d-110">[out] Liczba `mdManifestResource` tokeny faktycznie umieszczone w `rManifestResources`.</span><span class="sxs-lookup"><span data-stu-id="9fe6d-110">[out] The number of `mdManifestResource` tokens actually placed in `rManifestResources`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9fe6d-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9fe6d-111">Return Value</span></span>  
  
|<span data-ttu-id="9fe6d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9fe6d-112">HRESULT</span></span>|<span data-ttu-id="9fe6d-113">Opis</span><span class="sxs-lookup"><span data-stu-id="9fe6d-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="9fe6d-114">`EnumManifestResources`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="9fe6d-114">`EnumManifestResources` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="9fe6d-115">Nie ma żadnych tokenów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="9fe6d-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="9fe6d-116">W takim przypadku `pcTokens` jest ustawiony na zero.</span><span class="sxs-lookup"><span data-stu-id="9fe6d-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9fe6d-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9fe6d-117">Requirements</span></span>  
 <span data-ttu-id="9fe6d-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fe6d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fe6d-119">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9fe6d-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9fe6d-120">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9fe6d-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9fe6d-121">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fe6d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fe6d-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9fe6d-122">See Also</span></span>  
 [<span data-ttu-id="9fe6d-123">IMetaDataAssemblyImport — interfejs</span><span class="sxs-lookup"><span data-stu-id="9fe6d-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
