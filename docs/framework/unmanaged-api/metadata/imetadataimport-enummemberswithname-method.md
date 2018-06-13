---
title: IMetaDataImport::EnumMembersWithName — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMembersWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMembersWithName
helpviewer_keywords:
- IMetaDataImport::EnumMembersWithName method [.NET Framework metadata]
- EnumMembersWithName method [.NET Framework metadata]
ms.assetid: 7c9e9120-3104-42f0-86ce-19a025f20dcc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e5fca698adc4d08d805fec2ff80af377366674b6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445958"
---
# <a name="imetadataimportenummemberswithname-method"></a><span data-ttu-id="66efe-102">IMetaDataImport::EnumMembersWithName — Metoda</span><span class="sxs-lookup"><span data-stu-id="66efe-102">IMetaDataImport::EnumMembersWithName Method</span></span>
<span data-ttu-id="66efe-103">Wylicza tokenów MemberDef reprezentujący elementy członkowskie określonego typu o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="66efe-103">Enumerates MemberDef tokens representing members of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66efe-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="66efe-104">Syntax</span></span>  
  
```  
HRESULT EnumMembersWithName (  
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   cl,   
   [in]      LPCWSTR     szName,   
   [out]     mdToken     rMembers[],   
   [in]      ULONG       cMax,   
   [out]     ULONG       *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="66efe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="66efe-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="66efe-106">[w, out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="66efe-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="66efe-107">[in] Element TypeDef token reprezentujący typ z elementami członkowskimi wyliczyć.</span><span class="sxs-lookup"><span data-stu-id="66efe-107">[in] A TypeDef token representing the type with members to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="66efe-108">[in] Nazwa elementu członkowskiego, która ogranicza zakres modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="66efe-108">[in] The member name that limits the scope of the enumerator.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="66efe-109">[out] Tablica używany do przechowywania tokenów MemberDef.</span><span class="sxs-lookup"><span data-stu-id="66efe-109">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="66efe-110">[in] Maksymalny rozmiar `rMembers` tablicy.</span><span class="sxs-lookup"><span data-stu-id="66efe-110">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="66efe-111">[out] Rzeczywista liczba tokenów MemberDef zwracane w `rMembers`.</span><span class="sxs-lookup"><span data-stu-id="66efe-111">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66efe-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="66efe-112">Remarks</span></span>  
 <span data-ttu-id="66efe-113">Ta metoda wylicza pól i metod, ale nie do właściwości lub zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="66efe-113">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="66efe-114">W odróżnieniu od [IMetaDataImport::EnumMembers](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md), `EnumMembersWithName` odrzuca wszystkie tokeny pola i elementu członkowskiego, które nie mają określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="66efe-114">Unlike [IMetaDataImport::EnumMembers](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md), `EnumMembersWithName` discards all field and member tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="66efe-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="66efe-115">Return Value</span></span>  
  
|<span data-ttu-id="66efe-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="66efe-116">HRESULT</span></span>|<span data-ttu-id="66efe-117">Opis</span><span class="sxs-lookup"><span data-stu-id="66efe-117">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="66efe-118">`EnumTypeDefs` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="66efe-118">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="66efe-119">Nie ma żadnych tokenów MemberDef do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="66efe-119">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="66efe-120">W takim przypadku `pcTokens` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="66efe-120">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="66efe-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="66efe-121">Requirements</span></span>  
 <span data-ttu-id="66efe-122">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66efe-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66efe-123">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="66efe-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="66efe-124">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="66efe-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="66efe-125">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66efe-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66efe-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="66efe-126">See Also</span></span>  
 [<span data-ttu-id="66efe-127">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="66efe-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="66efe-128">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="66efe-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
