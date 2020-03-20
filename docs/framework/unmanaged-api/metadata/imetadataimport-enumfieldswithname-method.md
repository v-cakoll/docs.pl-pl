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
ms.openlocfilehash: bb8b531a884c9d3c2f33aa4aec5c4dbeaafe2b66
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177343"
---
# <a name="imetadataimportenumfieldswithname-method"></a><span data-ttu-id="f292b-102">IMetaDataImport::EnumFieldsWithName — Metoda</span><span class="sxs-lookup"><span data-stu-id="f292b-102">IMetaDataImport::EnumFieldsWithName Method</span></span>
<span data-ttu-id="f292b-103">Wylicza tokeny FieldDef określonego typu o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="f292b-103">Enumerates FieldDef tokens of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f292b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f292b-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFieldsWithName (  
   [in, out] HCORENUM    *phEnum,
   [in]  mdTypeDef       cl,
   [in]  LPCWSTR         szName,
   [out] mdFieldDef      rFields[],
   [in]  ULONG           cMax,
   [out] ULONG           *pcTokens
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f292b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f292b-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="f292b-106">[w, na zewnątrz] Wskaźnik do wyliczacza.</span><span class="sxs-lookup"><span data-stu-id="f292b-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="f292b-107">[w] Token typu, którego pola mają być wyliczone.</span><span class="sxs-lookup"><span data-stu-id="f292b-107">[in] The token of the type whose fields are to be enumerated.</span></span>  
  
 `szName`  
 <span data-ttu-id="f292b-108">[w] Nazwa pola, która ogranicza zakres wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="f292b-108">[in] The field name that limits the scope of the enumeration.</span></span>  
  
 `rFields`  
 <span data-ttu-id="f292b-109">[na zewnątrz] Tablica używana do przechowywania tokenów FieldDef.</span><span class="sxs-lookup"><span data-stu-id="f292b-109">[out] Array used to store the FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="f292b-110">[w] Maksymalny rozmiar `rFields` tablicy.</span><span class="sxs-lookup"><span data-stu-id="f292b-110">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="f292b-111">[na zewnątrz] Rzeczywista liczba tokenów FieldDef `rFields`zwrócona w .</span><span class="sxs-lookup"><span data-stu-id="f292b-111">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f292b-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f292b-112">Remarks</span></span>  
 <span data-ttu-id="f292b-113">W przeciwieństwie do [IMetaDataImport::EnumFields,](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md) `EnumFieldsWithName` odrzuca wszystkie tokeny pól, które nie mają określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="f292b-113">Unlike [IMetaDataImport::EnumFields](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md), `EnumFieldsWithName` discards all field tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f292b-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f292b-114">Return Value</span></span>  
  
|<span data-ttu-id="f292b-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f292b-115">HRESULT</span></span>|<span data-ttu-id="f292b-116">Opis</span><span class="sxs-lookup"><span data-stu-id="f292b-116">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="f292b-117">`EnumFieldsWithName`zwrócono pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f292b-117">`EnumFieldsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="f292b-118">Nie ma żadnych pól do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="f292b-118">There are no fields to enumerate.</span></span> <span data-ttu-id="f292b-119">W takim `pcTokens` przypadku wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="f292b-119">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f292b-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f292b-120">Requirements</span></span>  
 <span data-ttu-id="f292b-121">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f292b-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f292b-122">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="f292b-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f292b-123">**Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f292b-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f292b-124">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f292b-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f292b-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f292b-125">See also</span></span>

- [<span data-ttu-id="f292b-126">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f292b-126">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="f292b-127">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="f292b-127">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
