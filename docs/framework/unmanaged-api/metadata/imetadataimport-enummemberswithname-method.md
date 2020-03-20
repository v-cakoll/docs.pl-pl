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
ms.openlocfilehash: 7410f91a853f3a677a105dc2e12a86d723c9fad6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177320"
---
# <a name="imetadataimportenummemberswithname-method"></a><span data-ttu-id="40413-102">IMetaDataImport::EnumMembersWithName — Metoda</span><span class="sxs-lookup"><span data-stu-id="40413-102">IMetaDataImport::EnumMembersWithName Method</span></span>
<span data-ttu-id="40413-103">Wylicza tokeny MemberDef reprezentujące członków określonego typu o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="40413-103">Enumerates MemberDef tokens representing members of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40413-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="40413-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMembersWithName (  
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   cl,
   [in]      LPCWSTR     szName,
   [out]     mdToken     rMembers[],
   [in]      ULONG       cMax,
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40413-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="40413-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="40413-106">[w, na zewnątrz] Wskaźnik do wyliczacza.</span><span class="sxs-lookup"><span data-stu-id="40413-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="40413-107">[w] Token TypeDef reprezentujący typ z członkami do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="40413-107">[in] A TypeDef token representing the type with members to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="40413-108">[w] Nazwa elementu członkowskiego, która ogranicza zakres wyliczacza.</span><span class="sxs-lookup"><span data-stu-id="40413-108">[in] The member name that limits the scope of the enumerator.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="40413-109">[na zewnątrz] Tablica używana do przechowywania tokenów MemberDef.</span><span class="sxs-lookup"><span data-stu-id="40413-109">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="40413-110">[w] Maksymalny rozmiar `rMembers` tablicy.</span><span class="sxs-lookup"><span data-stu-id="40413-110">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="40413-111">[na zewnątrz] Rzeczywista liczba tokenów MemberDef `rMembers`zwrócona w .</span><span class="sxs-lookup"><span data-stu-id="40413-111">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40413-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="40413-112">Remarks</span></span>  
 <span data-ttu-id="40413-113">Ta metoda wylicza pola i metody, ale nie właściwości lub zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="40413-113">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="40413-114">W przeciwieństwie do [IMetaDataImport::EnumMembers,](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md) `EnumMembersWithName` odrzuca wszystkie tokeny pól i elementów członkowskich, które nie mają określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="40413-114">Unlike [IMetaDataImport::EnumMembers](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md), `EnumMembersWithName` discards all field and member tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="40413-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="40413-115">Return Value</span></span>  
  
|<span data-ttu-id="40413-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="40413-116">HRESULT</span></span>|<span data-ttu-id="40413-117">Opis</span><span class="sxs-lookup"><span data-stu-id="40413-117">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="40413-118">`EnumTypeDefs`zwrócono pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="40413-118">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="40413-119">Nie ma żadnych tokenów MemberDef do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="40413-119">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="40413-120">W takim `pcTokens` przypadku wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="40413-120">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="40413-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="40413-121">Requirements</span></span>  
 <span data-ttu-id="40413-122">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40413-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40413-123">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="40413-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="40413-124">**Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="40413-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="40413-125">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40413-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40413-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="40413-126">See also</span></span>

- [<span data-ttu-id="40413-127">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="40413-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="40413-128">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="40413-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
