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
ms.openlocfilehash: ea451bdd645d2d4dea4c5dd00408e0bc51804803
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492073"
---
# <a name="imetadataimportenummemberswithname-method"></a><span data-ttu-id="9d72c-102">IMetaDataImport::EnumMembersWithName — Metoda</span><span class="sxs-lookup"><span data-stu-id="9d72c-102">IMetaDataImport::EnumMembersWithName Method</span></span>
<span data-ttu-id="9d72c-103">Wylicza tokeny MemberDef reprezentujące elementy członkowskie określonego typu o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="9d72c-103">Enumerates MemberDef tokens representing members of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d72c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9d72c-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="9d72c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9d72c-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="9d72c-106">[in. out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="9d72c-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="9d72c-107">podczas Token TypeDef reprezentujący typ z elementami członkowskimi do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="9d72c-107">[in] A TypeDef token representing the type with members to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="9d72c-108">podczas Nazwa elementu członkowskiego, który ogranicza zakres modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="9d72c-108">[in] The member name that limits the scope of the enumerator.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="9d72c-109">określoną Tablica służąca do przechowywania tokenów MemberDef.</span><span class="sxs-lookup"><span data-stu-id="9d72c-109">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="9d72c-110">podczas Maksymalny rozmiar `rMembers` tablicy.</span><span class="sxs-lookup"><span data-stu-id="9d72c-110">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="9d72c-111">określoną Rzeczywista liczba tokenów MemberDef zwrócona w `rMembers` .</span><span class="sxs-lookup"><span data-stu-id="9d72c-111">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d72c-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9d72c-112">Remarks</span></span>  
 <span data-ttu-id="9d72c-113">Ta metoda wylicza pola i metody, ale nie właściwości ani zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="9d72c-113">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="9d72c-114">W przeciwieństwie do [IMetaDataImport:: EnumMembers —](imetadataimport-enummembers-method.md), `EnumMembersWithName` odrzuca wszystkie tokeny pola i elementu członkowskiego, które nie mają określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="9d72c-114">Unlike [IMetaDataImport::EnumMembers](imetadataimport-enummembers-method.md), `EnumMembersWithName` discards all field and member tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d72c-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9d72c-115">Return Value</span></span>  
  
|<span data-ttu-id="9d72c-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9d72c-116">HRESULT</span></span>|<span data-ttu-id="9d72c-117">Opis</span><span class="sxs-lookup"><span data-stu-id="9d72c-117">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="9d72c-118">`EnumTypeDefs`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="9d72c-118">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="9d72c-119">Brak tokenów MemberDef do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="9d72c-119">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="9d72c-120">W takim przypadku `pcTokens` jest równa zero.</span><span class="sxs-lookup"><span data-stu-id="9d72c-120">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9d72c-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9d72c-121">Requirements</span></span>  
 <span data-ttu-id="9d72c-122">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d72c-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d72c-123">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9d72c-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9d72c-124">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9d72c-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9d72c-125">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d72c-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d72c-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9d72c-126">See also</span></span>

- [<span data-ttu-id="9d72c-127">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9d72c-127">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="9d72c-128">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="9d72c-128">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
