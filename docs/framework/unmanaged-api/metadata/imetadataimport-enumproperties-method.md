---
title: "IMetaDataImport::EnumProperties — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumProperties
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumProperties
helpviewer_keywords:
- IMetaDataImport::EnumProperties method [.NET Framework metadata]
- EnumProperties method [.NET Framework metadata]
ms.assetid: 60573ad7-8821-4721-a068-3f7a6d25926a
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 63ff10904440f55ec3fe6fb6aa581fbf560763e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenumproperties-method"></a><span data-ttu-id="a7d66-102">IMetaDataImport::EnumProperties — Metoda</span><span class="sxs-lookup"><span data-stu-id="a7d66-102">IMetaDataImport::EnumProperties Method</span></span>
<span data-ttu-id="a7d66-103">Wylicza tokeny właściwości reprezentujący właściwości typu odwołuje się określony token TypeDef.</span><span class="sxs-lookup"><span data-stu-id="a7d66-103">Enumerates PropertyDef tokens representing the properties of the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7d66-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a7d66-104">Syntax</span></span>  
  
```  
HRESULT EnumProperties (  
   [in, out] HCORENUM    *phEnum,  
   [in]      mdTypeDef   td,  
   [out]     mdProperty  rProperties[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcProperties  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a7d66-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7d66-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="a7d66-106">[w, out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="a7d66-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="a7d66-107">Musi to być wartość NULL dla pierwsze wywołanie tej metody.</span><span class="sxs-lookup"><span data-stu-id="a7d66-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="a7d66-108">[in] Element TypeDef token reprezentujący typ o właściwościach wyliczyć.</span><span class="sxs-lookup"><span data-stu-id="a7d66-108">[in] A TypeDef token representing the type with properties to enumerate.</span></span>  
  
 `rProperties`  
 <span data-ttu-id="a7d66-109">[out] Tablica używany do przechowywania tokenów właściwości.</span><span class="sxs-lookup"><span data-stu-id="a7d66-109">[out] The array used to store the PropertyDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="a7d66-110">[in] Maksymalny rozmiar `rProperties` tablicy.</span><span class="sxs-lookup"><span data-stu-id="a7d66-110">[in] The maximum size of the `rProperties` array.</span></span>  
  
 `pcProperties`  
 <span data-ttu-id="a7d66-111">[out] Liczby właściwości tokenów zwracanych w `rProperties`.</span><span class="sxs-lookup"><span data-stu-id="a7d66-111">[out] The number of PropertyDef tokens returned in `rProperties`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a7d66-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a7d66-112">Return Value</span></span>  
  
|<span data-ttu-id="a7d66-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a7d66-113">HRESULT</span></span>|<span data-ttu-id="a7d66-114">Opis</span><span class="sxs-lookup"><span data-stu-id="a7d66-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="a7d66-115">`EnumProperties`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a7d66-115">`EnumProperties` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="a7d66-116">Nie ma żadnych tokenów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="a7d66-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="a7d66-117">W takim przypadku `pcProperties` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="a7d66-117">In that case, `pcProperties` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a7d66-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a7d66-118">Requirements</span></span>  
 <span data-ttu-id="a7d66-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7d66-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7d66-120">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a7d66-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a7d66-121">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a7d66-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a7d66-122">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7d66-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7d66-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a7d66-123">See Also</span></span>  
 [<span data-ttu-id="a7d66-124">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="a7d66-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="a7d66-125">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="a7d66-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
