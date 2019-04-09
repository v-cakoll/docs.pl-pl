---
title: IMetaDataImport::EnumFieldsWithName — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumFieldsWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumFieldsWithName
helpviewer_keywords:
- IMetaDataImport::EnumFieldsWithName method [.NET Framework metadata]
- EnumFieldsWithName method [.NET Framework metadata]
ms.assetid: 42145e8d-000f-4d0b-ae43-c08201190fa2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cf624695136a9397937f05b28dec18493c8e12d7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59153663"
---
# <a name="imetadataimportenumfieldswithname-method"></a><span data-ttu-id="4e2a5-102">IMetaDataImport::EnumFieldsWithName — Metoda</span><span class="sxs-lookup"><span data-stu-id="4e2a5-102">IMetaDataImport::EnumFieldsWithName Method</span></span>
<span data-ttu-id="4e2a5-103">Wylicza tokenów FieldDef określonego typu o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="4e2a5-103">Enumerates FieldDef tokens of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e2a5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4e2a5-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="4e2a5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4e2a5-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="4e2a5-106">[out w] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="4e2a5-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="4e2a5-107">[in] Token typu, w których pola są do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="4e2a5-107">[in] The token of the type whose fields are to be enumerated.</span></span>  
  
 `szName`  
 <span data-ttu-id="4e2a5-108">[in] Nazwa pola, która ogranicza zakres wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="4e2a5-108">[in] The field name that limits the scope of the enumeration.</span></span>  
  
 `rFields`  
 <span data-ttu-id="4e2a5-109">[out] Tablica do przechowywania tokenów FieldDef.</span><span class="sxs-lookup"><span data-stu-id="4e2a5-109">[out] Array used to store the FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="4e2a5-110">[in] Maksymalny rozmiar `rFields` tablicy.</span><span class="sxs-lookup"><span data-stu-id="4e2a5-110">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="4e2a5-111">[out] Rzeczywista liczba tokenów FieldDef zwracane w `rFields`.</span><span class="sxs-lookup"><span data-stu-id="4e2a5-111">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e2a5-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4e2a5-112">Remarks</span></span>  
 <span data-ttu-id="4e2a5-113">W odróżnieniu od [IMetaDataImport::EnumFields](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md), `EnumFieldsWithName` odrzuca wszystkie tokeny pola, które nie mają określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="4e2a5-113">Unlike [IMetaDataImport::EnumFields](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md), `EnumFieldsWithName` discards all field tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4e2a5-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4e2a5-114">Return Value</span></span>  
  
|<span data-ttu-id="4e2a5-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4e2a5-115">HRESULT</span></span>|<span data-ttu-id="4e2a5-116">Opis</span><span class="sxs-lookup"><span data-stu-id="4e2a5-116">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|`EnumFieldsWithName` <span data-ttu-id="4e2a5-117">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="4e2a5-117">returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="4e2a5-118">Nie ma żadnych pól do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="4e2a5-118">There are no fields to enumerate.</span></span> <span data-ttu-id="4e2a5-119">W takim przypadku `pcTokens` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="4e2a5-119">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4e2a5-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4e2a5-120">Requirements</span></span>  
 <span data-ttu-id="4e2a5-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e2a5-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e2a5-122">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="4e2a5-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4e2a5-123">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4e2a5-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="4e2a5-124">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="4e2a5-124">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4e2a5-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4e2a5-125">See also</span></span>

- [<span data-ttu-id="4e2a5-126">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="4e2a5-126">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="4e2a5-127">IMetaDataImport2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="4e2a5-127">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
