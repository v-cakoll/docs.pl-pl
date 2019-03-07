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
ms.openlocfilehash: 18cf59553468e2408f3898d8233bd05d453db17b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471969"
---
# <a name="imetadataimportenumfields-method"></a><span data-ttu-id="42200-102">IMetaDataImport::EnumFields — Metoda</span><span class="sxs-lookup"><span data-stu-id="42200-102">IMetaDataImport::EnumFields Method</span></span>
<span data-ttu-id="42200-103">Wylicza FieldDef tokeny dla danego typu odwołuje się określony token TypeDef.</span><span class="sxs-lookup"><span data-stu-id="42200-103">Enumerates FieldDef tokens for the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42200-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="42200-104">Syntax</span></span>  
  
```  
HRESULT EnumFields (   
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   cl,   
   [out]     mdFieldDef  rFields[],   
   [in]      ULONG       cMax,   
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42200-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="42200-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="42200-106">[out w] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="42200-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="42200-107">[in] Token TypeDef klasy, których pola są do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="42200-107">[in] The TypeDef token of the class whose fields are to be enumerated.</span></span>  
  
 `rFields`  
 <span data-ttu-id="42200-108">[out] Lista tokenów FieldDef.</span><span class="sxs-lookup"><span data-stu-id="42200-108">[out] The list of FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="42200-109">[in] Maksymalny rozmiar `rFields` tablicy.</span><span class="sxs-lookup"><span data-stu-id="42200-109">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="42200-110">[out] Rzeczywista liczba tokenów FieldDef zwracane w `rFields`.</span><span class="sxs-lookup"><span data-stu-id="42200-110">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="42200-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="42200-111">Return Value</span></span>  
  
|<span data-ttu-id="42200-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="42200-112">HRESULT</span></span>|<span data-ttu-id="42200-113">Opis</span><span class="sxs-lookup"><span data-stu-id="42200-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="42200-114">`EnumFields` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="42200-114">`EnumFields` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="42200-115">Nie ma żadnych pól do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="42200-115">There are no fields to enumerate.</span></span> <span data-ttu-id="42200-116">W takim przypadku `pcTokens` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="42200-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="42200-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="42200-117">Requirements</span></span>  
 <span data-ttu-id="42200-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42200-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42200-119">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="42200-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="42200-120">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="42200-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="42200-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42200-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42200-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="42200-122">See also</span></span>
- [<span data-ttu-id="42200-123">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="42200-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="42200-124">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="42200-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
