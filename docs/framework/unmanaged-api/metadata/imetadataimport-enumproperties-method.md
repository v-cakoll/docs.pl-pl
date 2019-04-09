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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59176040"
---
# <a name="imetadataimportenumproperties-method"></a><span data-ttu-id="09aab-102">IMetaDataImport::EnumProperties — Metoda</span><span class="sxs-lookup"><span data-stu-id="09aab-102">IMetaDataImport::EnumProperties Method</span></span>
<span data-ttu-id="09aab-103">Wylicza tokenów właściwości reprezentujących właściwości typu odwołuje się określony token TypeDef.</span><span class="sxs-lookup"><span data-stu-id="09aab-103">Enumerates PropertyDef tokens representing the properties of the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09aab-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="09aab-104">Syntax</span></span>  
  
```  
HRESULT EnumProperties (  
   [in, out] HCORENUM    *phEnum,  
   [in]      mdTypeDef   td,  
   [out]     mdProperty  rProperties[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcProperties  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09aab-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="09aab-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="09aab-106">[out w] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="09aab-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="09aab-107">Musi to być wartość NULL dla pierwszego wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="09aab-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="09aab-108">[in] TypeDef token reprezentujący typ z właściwościami do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="09aab-108">[in] A TypeDef token representing the type with properties to enumerate.</span></span>  
  
 `rProperties`  
 <span data-ttu-id="09aab-109">[out] Tablica do przechowywania tokenów właściwości.</span><span class="sxs-lookup"><span data-stu-id="09aab-109">[out] The array used to store the PropertyDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="09aab-110">[in] Maksymalny rozmiar `rProperties` tablicy.</span><span class="sxs-lookup"><span data-stu-id="09aab-110">[in] The maximum size of the `rProperties` array.</span></span>  
  
 `pcProperties`  
 <span data-ttu-id="09aab-111">[out] Liczba tokenów właściwości zwracane w `rProperties`.</span><span class="sxs-lookup"><span data-stu-id="09aab-111">[out] The number of PropertyDef tokens returned in `rProperties`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="09aab-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="09aab-112">Return Value</span></span>  
  
|<span data-ttu-id="09aab-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="09aab-113">HRESULT</span></span>|<span data-ttu-id="09aab-114">Opis</span><span class="sxs-lookup"><span data-stu-id="09aab-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|`EnumProperties` <span data-ttu-id="09aab-115">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="09aab-115">returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="09aab-116">Nie ma żadnych tokeny do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="09aab-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="09aab-117">W takim przypadku `pcProperties` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="09aab-117">In that case, `pcProperties` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="09aab-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="09aab-118">Requirements</span></span>  
 <span data-ttu-id="09aab-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09aab-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09aab-120">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="09aab-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="09aab-121">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="09aab-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="09aab-122">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="09aab-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="09aab-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="09aab-123">See also</span></span>

- [<span data-ttu-id="09aab-124">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="09aab-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="09aab-125">IMetaDataImport2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="09aab-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
