---
title: "IMetaDataImport::EnumCustomAttributes — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumCustomAttributes
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method [.NET Framework metadata]
- IMetaDataImport::EnumCustomAttributes method [.NET Framework metadata]
ms.assetid: 798513a0-68b1-4d04-bc5b-782a4445ea68
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4e45c15f3d09972d1c83c9b330965c4e8afd21b7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenumcustomattributes-method"></a><span data-ttu-id="1f447-102">IMetaDataImport::EnumCustomAttributes — Metoda</span><span class="sxs-lookup"><span data-stu-id="1f447-102">IMetaDataImport::EnumCustomAttributes Method</span></span>
<span data-ttu-id="1f447-103">Wylicza tokenów niestandardowych definicja atrybutu skojarzone z określonego typu lub elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="1f447-103">Enumerates custom attribute-definition tokens associated with the specified type or member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f447-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1f447-104">Syntax</span></span>  
  
```  
HRESULT EnumCustomAttributes (   
   [in, out] HCORENUM      *phEnum,  
   [in]  mdToken            tk,   
   [in]  mdToken            tkType,   
   [out] mdCustomAttribute  rCustomAttributes[],   
   [in]  ULONG              cMax,  
   [out, optional] ULONG   *pcCustomAttributes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1f447-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1f447-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="1f447-106">[w, out] Wskaźnik do zwrócony modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="1f447-106">[in, out] A pointer to the returned enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="1f447-107">[in] Token do zakresu wyliczenia lub zero dla wszystkich atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="1f447-107">[in] A token for the scope of the enumeration, or zero for all custom attributes.</span></span>  
  
 `tkType`  
 <span data-ttu-id="1f447-108">[in] Token dla konstruktora typu atrybutów, które mają zostać wyliczone lub `null` dla wszystkich typów.</span><span class="sxs-lookup"><span data-stu-id="1f447-108">[in] A token for the constructor of the type of the attributes to be enumerated, or `null` for all types.</span></span>  
  
 `rCustomAttributes`  
 <span data-ttu-id="1f447-109">[out] Tablica atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="1f447-109">[out] An array of custom attribute tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="1f447-110">[in] Maksymalny rozmiar `rCustomAttributes` tablicy.</span><span class="sxs-lookup"><span data-stu-id="1f447-110">[in] The maximum size of the `rCustomAttributes` array.</span></span>  
  
 `pcCustomAttributes`  
 <span data-ttu-id="1f447-111">[out, opcjonalnie] Rzeczywista liczba tokenów wartości zwracanych w `rCustomAttributes`.</span><span class="sxs-lookup"><span data-stu-id="1f447-111">[out, optional] The actual number of token values returned in `rCustomAttributes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1f447-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1f447-112">Return Value</span></span>  
  
|<span data-ttu-id="1f447-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1f447-113">HRESULT</span></span>|<span data-ttu-id="1f447-114">Opis</span><span class="sxs-lookup"><span data-stu-id="1f447-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="1f447-115">`EnumCustomAttributes`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="1f447-115">`EnumCustomAttributes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="1f447-116">Nie ma żadnych atrybutów niestandardowych do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="1f447-116">There are no custom attributes to enumerate.</span></span> <span data-ttu-id="1f447-117">W takim przypadku `pcCustomAttributes` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="1f447-117">In that case, `pcCustomAttributes` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1f447-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1f447-118">Requirements</span></span>  
 <span data-ttu-id="1f447-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f447-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f447-120">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1f447-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1f447-121">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1f447-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1f447-122">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f447-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f447-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1f447-123">See Also</span></span>  
 [<span data-ttu-id="1f447-124">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="1f447-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="1f447-125">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="1f447-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
