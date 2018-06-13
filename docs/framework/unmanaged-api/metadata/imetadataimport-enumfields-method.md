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
ms.openlocfilehash: bd8a2d373b801bd8238d50eecb388ef511bc34bc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446205"
---
# <a name="imetadataimportenumfields-method"></a><span data-ttu-id="a411a-102">IMetaDataImport::EnumFields — Metoda</span><span class="sxs-lookup"><span data-stu-id="a411a-102">IMetaDataImport::EnumFields Method</span></span>
<span data-ttu-id="a411a-103">Wylicza FieldDef tokeny dla typu odwołuje się określony token TypeDef.</span><span class="sxs-lookup"><span data-stu-id="a411a-103">Enumerates FieldDef tokens for the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a411a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a411a-104">Syntax</span></span>  
  
```  
HRESULT EnumFields (   
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   cl,   
   [out]     mdFieldDef  rFields[],   
   [in]      ULONG       cMax,   
   [out]     ULONG       *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a411a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a411a-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="a411a-106">[w, out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="a411a-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="a411a-107">[in] Token TypeDef klasy, których pola mają zostać wyliczone.</span><span class="sxs-lookup"><span data-stu-id="a411a-107">[in] The TypeDef token of the class whose fields are to be enumerated.</span></span>  
  
 `rFields`  
 <span data-ttu-id="a411a-108">[out] Lista tokenów FieldDef.</span><span class="sxs-lookup"><span data-stu-id="a411a-108">[out] The list of FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="a411a-109">[in] Maksymalny rozmiar `rFields` tablicy.</span><span class="sxs-lookup"><span data-stu-id="a411a-109">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="a411a-110">[out] Rzeczywista liczba tokenów FieldDef zwracane w `rFields`.</span><span class="sxs-lookup"><span data-stu-id="a411a-110">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a411a-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a411a-111">Return Value</span></span>  
  
|<span data-ttu-id="a411a-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a411a-112">HRESULT</span></span>|<span data-ttu-id="a411a-113">Opis</span><span class="sxs-lookup"><span data-stu-id="a411a-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="a411a-114">`EnumFields` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a411a-114">`EnumFields` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="a411a-115">Nie ma żadnych pól do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="a411a-115">There are no fields to enumerate.</span></span> <span data-ttu-id="a411a-116">W takim przypadku `pcTokens` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="a411a-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a411a-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a411a-117">Requirements</span></span>  
 <span data-ttu-id="a411a-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a411a-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a411a-119">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a411a-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a411a-120">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a411a-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a411a-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a411a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a411a-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a411a-122">See Also</span></span>  
 [<span data-ttu-id="a411a-123">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="a411a-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="a411a-124">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="a411a-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
