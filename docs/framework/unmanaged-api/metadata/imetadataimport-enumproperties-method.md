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
ms.openlocfilehash: d46e18707ff6b34e32a73aed81c2b7e57f769ed6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenumproperties-method"></a><span data-ttu-id="62767-102">IMetaDataImport::EnumProperties — Metoda</span><span class="sxs-lookup"><span data-stu-id="62767-102">IMetaDataImport::EnumProperties Method</span></span>
<span data-ttu-id="62767-103">Wylicza tokeny właściwości reprezentujący właściwości typu odwołuje się określony token TypeDef.</span><span class="sxs-lookup"><span data-stu-id="62767-103">Enumerates PropertyDef tokens representing the properties of the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62767-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="62767-104">Syntax</span></span>  
  
```  
HRESULT EnumProperties (  
   [in, out] HCORENUM    *phEnum,  
   [in]      mdTypeDef   td,  
   [out]     mdProperty  rProperties[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcProperties  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="62767-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="62767-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="62767-106">[w, out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="62767-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="62767-107">Musi to być wartość NULL dla pierwsze wywołanie tej metody.</span><span class="sxs-lookup"><span data-stu-id="62767-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="62767-108">[in] Element TypeDef token reprezentujący typ o właściwościach wyliczyć.</span><span class="sxs-lookup"><span data-stu-id="62767-108">[in] A TypeDef token representing the type with properties to enumerate.</span></span>  
  
 `rProperties`  
 <span data-ttu-id="62767-109">[out] Tablica używany do przechowywania tokenów właściwości.</span><span class="sxs-lookup"><span data-stu-id="62767-109">[out] The array used to store the PropertyDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="62767-110">[in] Maksymalny rozmiar `rProperties` tablicy.</span><span class="sxs-lookup"><span data-stu-id="62767-110">[in] The maximum size of the `rProperties` array.</span></span>  
  
 `pcProperties`  
 <span data-ttu-id="62767-111">[out] Liczby właściwości tokenów zwracanych w `rProperties`.</span><span class="sxs-lookup"><span data-stu-id="62767-111">[out] The number of PropertyDef tokens returned in `rProperties`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="62767-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="62767-112">Return Value</span></span>  
  
|<span data-ttu-id="62767-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="62767-113">HRESULT</span></span>|<span data-ttu-id="62767-114">Opis</span><span class="sxs-lookup"><span data-stu-id="62767-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="62767-115">`EnumProperties`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="62767-115">`EnumProperties` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="62767-116">Nie ma żadnych tokenów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="62767-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="62767-117">W takim przypadku `pcProperties` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="62767-117">In that case, `pcProperties` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="62767-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="62767-118">Requirements</span></span>  
 <span data-ttu-id="62767-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62767-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62767-120">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="62767-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="62767-121">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="62767-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="62767-122">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62767-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62767-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="62767-123">See Also</span></span>  
 [<span data-ttu-id="62767-124">IMetaDataImport — interfejs</span><span class="sxs-lookup"><span data-stu-id="62767-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="62767-125">IMetaDataImport2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="62767-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
