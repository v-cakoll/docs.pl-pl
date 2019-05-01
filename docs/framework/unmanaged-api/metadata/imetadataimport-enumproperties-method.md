---
title: IMetaDataImport::EnumProperties — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumProperties
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumProperties
helpviewer_keywords:
- IMetaDataImport::EnumProperties method [.NET Framework metadata]
- EnumProperties method [.NET Framework metadata]
ms.assetid: 60573ad7-8821-4721-a068-3f7a6d25926a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 410fd7a702d3aa3812b4ea053c43fdaa507a474a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62042513"
---
# <a name="imetadataimportenumproperties-method"></a><span data-ttu-id="0eb73-102">IMetaDataImport::EnumProperties — Metoda</span><span class="sxs-lookup"><span data-stu-id="0eb73-102">IMetaDataImport::EnumProperties Method</span></span>
<span data-ttu-id="0eb73-103">Wylicza tokenów właściwości reprezentujących właściwości typu odwołuje się określony token TypeDef.</span><span class="sxs-lookup"><span data-stu-id="0eb73-103">Enumerates PropertyDef tokens representing the properties of the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0eb73-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0eb73-104">Syntax</span></span>  
  
```  
HRESULT EnumProperties (  
   [in, out] HCORENUM    *phEnum,  
   [in]      mdTypeDef   td,  
   [out]     mdProperty  rProperties[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcProperties  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0eb73-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0eb73-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="0eb73-106">[out w] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="0eb73-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="0eb73-107">Musi to być wartość NULL dla pierwszego wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="0eb73-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="0eb73-108">[in] TypeDef token reprezentujący typ z właściwościami do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="0eb73-108">[in] A TypeDef token representing the type with properties to enumerate.</span></span>  
  
 `rProperties`  
 <span data-ttu-id="0eb73-109">[out] Tablica do przechowywania tokenów właściwości.</span><span class="sxs-lookup"><span data-stu-id="0eb73-109">[out] The array used to store the PropertyDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="0eb73-110">[in] Maksymalny rozmiar `rProperties` tablicy.</span><span class="sxs-lookup"><span data-stu-id="0eb73-110">[in] The maximum size of the `rProperties` array.</span></span>  
  
 `pcProperties`  
 <span data-ttu-id="0eb73-111">[out] Liczba tokenów właściwości zwracane w `rProperties`.</span><span class="sxs-lookup"><span data-stu-id="0eb73-111">[out] The number of PropertyDef tokens returned in `rProperties`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0eb73-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0eb73-112">Return Value</span></span>  
  
|<span data-ttu-id="0eb73-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0eb73-113">HRESULT</span></span>|<span data-ttu-id="0eb73-114">Opis</span><span class="sxs-lookup"><span data-stu-id="0eb73-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="0eb73-115">`EnumProperties` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="0eb73-115">`EnumProperties` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="0eb73-116">Nie ma żadnych tokeny do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="0eb73-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="0eb73-117">W takim przypadku `pcProperties` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="0eb73-117">In that case, `pcProperties` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0eb73-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0eb73-118">Requirements</span></span>  
 <span data-ttu-id="0eb73-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0eb73-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0eb73-120">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="0eb73-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0eb73-121">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0eb73-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0eb73-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0eb73-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0eb73-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0eb73-123">See also</span></span>

- [<span data-ttu-id="0eb73-124">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="0eb73-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="0eb73-125">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="0eb73-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
