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
ms.openlocfilehash: 961c1e0468ab99baca387b7d6ada4733629b7ffa
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492234"
---
# <a name="imetadataimportenummemberswithname-method"></a><span data-ttu-id="6997e-102">IMetaDataImport::EnumMembersWithName — Metoda</span><span class="sxs-lookup"><span data-stu-id="6997e-102">IMetaDataImport::EnumMembersWithName Method</span></span>
<span data-ttu-id="6997e-103">Wylicza tokenów MemberDef reprezentujących elementy członkowskie określonego typu o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="6997e-103">Enumerates MemberDef tokens representing members of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6997e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6997e-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="6997e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6997e-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="6997e-106">[out w] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="6997e-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="6997e-107">[in] TypeDef token reprezentujący typ z elementami członkowskimi do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="6997e-107">[in] A TypeDef token representing the type with members to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="6997e-108">[in] Nazwa elementu członkowskiego, który ogranicza zakres modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="6997e-108">[in] The member name that limits the scope of the enumerator.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="6997e-109">[out] Tablica do przechowywania tokenów MemberDef.</span><span class="sxs-lookup"><span data-stu-id="6997e-109">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="6997e-110">[in] Maksymalny rozmiar `rMembers` tablicy.</span><span class="sxs-lookup"><span data-stu-id="6997e-110">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="6997e-111">[out] Rzeczywista liczba tokenów MemberDef zwracane w `rMembers`.</span><span class="sxs-lookup"><span data-stu-id="6997e-111">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6997e-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6997e-112">Remarks</span></span>  
 <span data-ttu-id="6997e-113">Ta metoda wylicza pola i metody, ale nie do właściwości lub zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="6997e-113">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="6997e-114">W odróżnieniu od [IMetaDataImport::EnumMembers](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md), `EnumMembersWithName` odrzuca wszystkie tokeny pól i elementów członkowskich, które nie mają określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="6997e-114">Unlike [IMetaDataImport::EnumMembers](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md), `EnumMembersWithName` discards all field and member tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6997e-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6997e-115">Return Value</span></span>  
  
|<span data-ttu-id="6997e-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6997e-116">HRESULT</span></span>|<span data-ttu-id="6997e-117">Opis</span><span class="sxs-lookup"><span data-stu-id="6997e-117">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="6997e-118">`EnumTypeDefs` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="6997e-118">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="6997e-119">Nie ma żadnych tokeny MemberDef do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="6997e-119">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="6997e-120">W takim przypadku `pcTokens` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="6997e-120">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6997e-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6997e-121">Requirements</span></span>  
 <span data-ttu-id="6997e-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6997e-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6997e-123">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="6997e-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6997e-124">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6997e-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6997e-125">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6997e-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6997e-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6997e-126">See also</span></span>
- [<span data-ttu-id="6997e-127">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="6997e-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="6997e-128">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="6997e-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
