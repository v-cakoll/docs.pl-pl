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
ms.openlocfilehash: be2845d1d660d86447cfbb6f2845a8e68b727e66
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175515"
---
# <a name="imetadataimportenumfields-method"></a><span data-ttu-id="b76e2-102">IMetaDataImport::EnumFields — Metoda</span><span class="sxs-lookup"><span data-stu-id="b76e2-102">IMetaDataImport::EnumFields Method</span></span>
<span data-ttu-id="b76e2-103">Wylicza tokeny FieldDef dla typu, do którego odwołuje się określony token TypeDef.</span><span class="sxs-lookup"><span data-stu-id="b76e2-103">Enumerates FieldDef tokens for the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b76e2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b76e2-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFields (
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   cl,
   [out]     mdFieldDef  rFields[],
   [in]      ULONG       cMax,
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b76e2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b76e2-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="b76e2-106">[w, na zewnątrz] Wskaźnik do wyliczacza.</span><span class="sxs-lookup"><span data-stu-id="b76e2-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="b76e2-107">[w] TypeDef token klasy, których pola mają być wyliczone.</span><span class="sxs-lookup"><span data-stu-id="b76e2-107">[in] The TypeDef token of the class whose fields are to be enumerated.</span></span>  
  
 `rFields`  
 <span data-ttu-id="b76e2-108">[na zewnątrz] Lista tokenów FieldDef.</span><span class="sxs-lookup"><span data-stu-id="b76e2-108">[out] The list of FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b76e2-109">[w] Maksymalny rozmiar `rFields` tablicy.</span><span class="sxs-lookup"><span data-stu-id="b76e2-109">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="b76e2-110">[na zewnątrz] Rzeczywista liczba tokenów FieldDef `rFields`zwrócona w .</span><span class="sxs-lookup"><span data-stu-id="b76e2-110">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b76e2-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b76e2-111">Return Value</span></span>  
  
|<span data-ttu-id="b76e2-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b76e2-112">HRESULT</span></span>|<span data-ttu-id="b76e2-113">Opis</span><span class="sxs-lookup"><span data-stu-id="b76e2-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="b76e2-114">`EnumFields`zwrócono pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="b76e2-114">`EnumFields` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="b76e2-115">Nie ma żadnych pól do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="b76e2-115">There are no fields to enumerate.</span></span> <span data-ttu-id="b76e2-116">W takim `pcTokens` przypadku wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="b76e2-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b76e2-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b76e2-117">Requirements</span></span>  
 <span data-ttu-id="b76e2-118">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b76e2-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b76e2-119">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="b76e2-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b76e2-120">**Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b76e2-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b76e2-121">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b76e2-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b76e2-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b76e2-122">See also</span></span>

- [<span data-ttu-id="b76e2-123">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b76e2-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="b76e2-124">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="b76e2-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
