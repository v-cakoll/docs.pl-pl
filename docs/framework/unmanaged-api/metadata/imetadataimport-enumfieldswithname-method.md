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
ms.openlocfilehash: 68261b165847a5c3ee29adbc4908451fb00c5443
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492268"
---
# <a name="imetadataimportenumfieldswithname-method"></a><span data-ttu-id="86c9e-102">IMetaDataImport::EnumFieldsWithName — Metoda</span><span class="sxs-lookup"><span data-stu-id="86c9e-102">IMetaDataImport::EnumFieldsWithName Method</span></span>
<span data-ttu-id="86c9e-103">Wylicza tokeny FieldDef określonego typu o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="86c9e-103">Enumerates FieldDef tokens of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86c9e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="86c9e-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="86c9e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="86c9e-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="86c9e-106">[in. out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="86c9e-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="86c9e-107">podczas Token typu, którego pola mają zostać wyliczone.</span><span class="sxs-lookup"><span data-stu-id="86c9e-107">[in] The token of the type whose fields are to be enumerated.</span></span>  
  
 `szName`  
 <span data-ttu-id="86c9e-108">podczas Nazwa pola, która ogranicza zakres wyliczania.</span><span class="sxs-lookup"><span data-stu-id="86c9e-108">[in] The field name that limits the scope of the enumeration.</span></span>  
  
 `rFields`  
 <span data-ttu-id="86c9e-109">określoną Tablica służąca do przechowywania tokenów FieldDef.</span><span class="sxs-lookup"><span data-stu-id="86c9e-109">[out] Array used to store the FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="86c9e-110">podczas Maksymalny rozmiar `rFields` tablicy.</span><span class="sxs-lookup"><span data-stu-id="86c9e-110">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="86c9e-111">określoną Rzeczywista liczba tokenów FieldDef zwrócona w `rFields` .</span><span class="sxs-lookup"><span data-stu-id="86c9e-111">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86c9e-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="86c9e-112">Remarks</span></span>  
 <span data-ttu-id="86c9e-113">W przeciwieństwie do [IMetaDataImport:: EnumFields —](imetadataimport-enumfields-method.md), `EnumFieldsWithName` odrzuca wszystkie tokeny pola, które nie mają określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="86c9e-113">Unlike [IMetaDataImport::EnumFields](imetadataimport-enumfields-method.md), `EnumFieldsWithName` discards all field tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="86c9e-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="86c9e-114">Return Value</span></span>  
  
|<span data-ttu-id="86c9e-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="86c9e-115">HRESULT</span></span>|<span data-ttu-id="86c9e-116">Opis</span><span class="sxs-lookup"><span data-stu-id="86c9e-116">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="86c9e-117">`EnumFieldsWithName`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="86c9e-117">`EnumFieldsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="86c9e-118">Brak pól do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="86c9e-118">There are no fields to enumerate.</span></span> <span data-ttu-id="86c9e-119">W takim przypadku `pcTokens` jest równa zero.</span><span class="sxs-lookup"><span data-stu-id="86c9e-119">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="86c9e-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="86c9e-120">Requirements</span></span>  
 <span data-ttu-id="86c9e-121">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86c9e-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86c9e-122">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="86c9e-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="86c9e-123">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="86c9e-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="86c9e-124">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86c9e-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86c9e-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86c9e-125">See also</span></span>

- [<span data-ttu-id="86c9e-126">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="86c9e-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="86c9e-127">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="86c9e-127">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
