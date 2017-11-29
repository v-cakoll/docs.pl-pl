---
title: "IMetaDataImport::EnumFieldsWithName — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumFieldsWithName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumFieldsWithName
helpviewer_keywords:
- IMetaDataImport::EnumFieldsWithName method [.NET Framework metadata]
- EnumFieldsWithName method [.NET Framework metadata]
ms.assetid: 42145e8d-000f-4d0b-ae43-c08201190fa2
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2f6104f287350a9ac2f0eb5b82c05422a18a48a2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenumfieldswithname-method"></a><span data-ttu-id="ecef2-102">IMetaDataImport::EnumFieldsWithName — Metoda</span><span class="sxs-lookup"><span data-stu-id="ecef2-102">IMetaDataImport::EnumFieldsWithName Method</span></span>
<span data-ttu-id="ecef2-103">Wylicza tokenów FieldDef określonego typu o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="ecef2-103">Enumerates FieldDef tokens of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecef2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ecef2-104">Syntax</span></span>  
  
```  
HRESULT EnumFieldsWithName (  
   [in, out] HCORENUM    *phEnum,   
   [in]  mdTypeDef       cl,   
   [in]  LPCWSTR         szName,   
   [out] mdFieldDef      rFields[],   
   [in]  ULONG           cMax,   
   [out] ULONG           *pcTokens   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ecef2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ecef2-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="ecef2-106">[w, out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="ecef2-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="ecef2-107">[in] Token typu, których pola mają zostać wyliczone.</span><span class="sxs-lookup"><span data-stu-id="ecef2-107">[in] The token of the type whose fields are to be enumerated.</span></span>  
  
 `szName`  
 <span data-ttu-id="ecef2-108">[in] Nazwa pola, która ogranicza zakres wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="ecef2-108">[in] The field name that limits the scope of the enumeration.</span></span>  
  
 `rFields`  
 <span data-ttu-id="ecef2-109">[out] Tablica używany do przechowywania tokenów FieldDef.</span><span class="sxs-lookup"><span data-stu-id="ecef2-109">[out] Array used to store the FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="ecef2-110">[in] Maksymalny rozmiar `rFields` tablicy.</span><span class="sxs-lookup"><span data-stu-id="ecef2-110">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="ecef2-111">[out] Rzeczywista liczba tokenów FieldDef zwracane w `rFields`.</span><span class="sxs-lookup"><span data-stu-id="ecef2-111">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ecef2-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ecef2-112">Remarks</span></span>  
 <span data-ttu-id="ecef2-113">W odróżnieniu od [IMetaDataImport::EnumFields](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md), `EnumFieldsWithName` odrzuca wszystkie tokeny pola, które nie mają określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="ecef2-113">Unlike [IMetaDataImport::EnumFields](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md), `EnumFieldsWithName` discards all field tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ecef2-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ecef2-114">Return Value</span></span>  
  
|<span data-ttu-id="ecef2-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ecef2-115">HRESULT</span></span>|<span data-ttu-id="ecef2-116">Opis</span><span class="sxs-lookup"><span data-stu-id="ecef2-116">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="ecef2-117">`EnumFieldsWithName`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="ecef2-117">`EnumFieldsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="ecef2-118">Nie ma żadnych pól do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="ecef2-118">There are no fields to enumerate.</span></span> <span data-ttu-id="ecef2-119">W takim przypadku `pcTokens` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="ecef2-119">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ecef2-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ecef2-120">Requirements</span></span>  
 <span data-ttu-id="ecef2-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecef2-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecef2-122">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ecef2-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ecef2-123">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ecef2-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ecef2-124">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecef2-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecef2-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ecef2-125">See Also</span></span>  
 [<span data-ttu-id="ecef2-126">IMetaDataImport — interfejs</span><span class="sxs-lookup"><span data-stu-id="ecef2-126">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="ecef2-127">IMetaDataImport2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="ecef2-127">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
