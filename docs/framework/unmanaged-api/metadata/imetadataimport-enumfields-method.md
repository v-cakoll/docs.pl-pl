---
title: IMetaDataImport::EnumFields — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumFields
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumFields
helpviewer_keywords:
- EnumFields method [.NET Framework metadata]
- IMetaDataImport::EnumFields method [.NET Framework metadata]
ms.assetid: 1d23247e-c58c-45db-afd8-83aa89cde18e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 313dbd11f1d033f0e15de651b9c130cc98c217e9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59192829"
---
# <a name="imetadataimportenumfields-method"></a><span data-ttu-id="8354f-102">IMetaDataImport::EnumFields — Metoda</span><span class="sxs-lookup"><span data-stu-id="8354f-102">IMetaDataImport::EnumFields Method</span></span>
<span data-ttu-id="8354f-103">Wylicza FieldDef tokeny dla danego typu odwołuje się określony token TypeDef.</span><span class="sxs-lookup"><span data-stu-id="8354f-103">Enumerates FieldDef tokens for the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8354f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8354f-104">Syntax</span></span>  
  
```  
HRESULT EnumFields (   
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   cl,   
   [out]     mdFieldDef  rFields[],   
   [in]      ULONG       cMax,   
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8354f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8354f-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="8354f-106">[out w] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="8354f-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="8354f-107">[in] Token TypeDef klasy, których pola są do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="8354f-107">[in] The TypeDef token of the class whose fields are to be enumerated.</span></span>  
  
 `rFields`  
 <span data-ttu-id="8354f-108">[out] Lista tokenów FieldDef.</span><span class="sxs-lookup"><span data-stu-id="8354f-108">[out] The list of FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="8354f-109">[in] Maksymalny rozmiar `rFields` tablicy.</span><span class="sxs-lookup"><span data-stu-id="8354f-109">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="8354f-110">[out] Rzeczywista liczba tokenów FieldDef zwracane w `rFields`.</span><span class="sxs-lookup"><span data-stu-id="8354f-110">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8354f-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8354f-111">Return Value</span></span>  
  
|<span data-ttu-id="8354f-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8354f-112">HRESULT</span></span>|<span data-ttu-id="8354f-113">Opis</span><span class="sxs-lookup"><span data-stu-id="8354f-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|`EnumFields` <span data-ttu-id="8354f-114">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="8354f-114">returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="8354f-115">Nie ma żadnych pól do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="8354f-115">There are no fields to enumerate.</span></span> <span data-ttu-id="8354f-116">W takim przypadku `pcTokens` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="8354f-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8354f-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8354f-117">Requirements</span></span>  
 <span data-ttu-id="8354f-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8354f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8354f-119">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="8354f-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8354f-120">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8354f-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="8354f-121">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="8354f-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8354f-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8354f-122">See also</span></span>

- [<span data-ttu-id="8354f-123">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8354f-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="8354f-124">IMetaDataImport2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8354f-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
