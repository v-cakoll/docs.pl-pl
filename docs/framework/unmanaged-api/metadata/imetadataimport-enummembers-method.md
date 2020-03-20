---
title: IMetaDataImport::EnumMembers — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMembers
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMembers
helpviewer_keywords:
- IMetaDataImport::EnumMembers method [.NET Framework metadata]
- EnumMembers method [.NET Framework metadata]
ms.assetid: 3fb8e178-342b-4c89-9bcf-f7f834e6cb77
topic_type:
- apiref
ms.openlocfilehash: 20c7a90f27defa18a5ef311d1f3a549b81fc5c40
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175489"
---
# <a name="imetadataimportenummembers-method"></a><span data-ttu-id="fa45a-102">IMetaDataImport::EnumMembers — Metoda</span><span class="sxs-lookup"><span data-stu-id="fa45a-102">IMetaDataImport::EnumMembers Method</span></span>
<span data-ttu-id="fa45a-103">Wylicza tokeny MemberDef reprezentujące członków określonego typu.</span><span class="sxs-lookup"><span data-stu-id="fa45a-103">Enumerates MemberDef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa45a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fa45a-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMembers (
   [in, out]  HCORENUM    *phEnum,
   [in]  mdTypeDef   cl,
   [out] mdToken     rMembers[],
   [in]  ULONG       cMax,
   [out] ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa45a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fa45a-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="fa45a-106">[w, na zewnątrz] Wskaźnik do wyliczacza.</span><span class="sxs-lookup"><span data-stu-id="fa45a-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="fa45a-107">[w] A TypeDef token reprezentujący typ, którego elementy członkowskie mają być wyliczone.</span><span class="sxs-lookup"><span data-stu-id="fa45a-107">[in] A TypeDef token representing the type whose members are to be enumerated.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="fa45a-108">[na zewnątrz] Tablica używana do przechowywania tokenów MemberDef.</span><span class="sxs-lookup"><span data-stu-id="fa45a-108">[out] The array used to hold the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="fa45a-109">[w] Maksymalny rozmiar `rMembers` tablicy.</span><span class="sxs-lookup"><span data-stu-id="fa45a-109">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="fa45a-110">[na zewnątrz] Rzeczywista liczba tokenów MemberDef `rMembers`zwrócona w .</span><span class="sxs-lookup"><span data-stu-id="fa45a-110">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fa45a-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fa45a-111">Return Value</span></span>  
  
|<span data-ttu-id="fa45a-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fa45a-112">HRESULT</span></span>|<span data-ttu-id="fa45a-113">Opis</span><span class="sxs-lookup"><span data-stu-id="fa45a-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="fa45a-114">`EnumMembers`zwrócono pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="fa45a-114">`EnumMembers` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="fa45a-115">Nie ma żadnych tokenów MemberDef do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="fa45a-115">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="fa45a-116">W takim `pcTokens` przypadku wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="fa45a-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa45a-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fa45a-117">Remarks</span></span>  
 <span data-ttu-id="fa45a-118">Podczas wyliczania kolekcji członków dla `EnumMembers` klasy zwraca tylko elementy członkowskie (pola i metody, ale **nie** właściwości lub zdarzenia) zdefiniowane bezpośrednio w klasie.</span><span class="sxs-lookup"><span data-stu-id="fa45a-118">When enumerating collections of members for a class, `EnumMembers` returns only members (fields and methods, but **not** properties or events) defined directly on the class.</span></span> <span data-ttu-id="fa45a-119">Nie zwraca żadnych elementów członkowskich, które dziedziczy klasa, nawet jeśli klasa zapewnia implementację dla tych członków dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="fa45a-119">It does not return any members that the class inherits, even if the class provides an implementation for those inherited members.</span></span> <span data-ttu-id="fa45a-120">Aby wyliczyć odziedziczone elementy członkowskie, obiektu wywołującego należy jawnie chodzić łańcucha dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="fa45a-120">To enumerate inherited members, the caller must explicitly walk the inheritance chain.</span></span> <span data-ttu-id="fa45a-121">Należy zauważyć, że reguły dla łańcucha dziedziczenia mogą się różnić w zależności od języka lub kompilatora, który emitował oryginalne metadane.</span><span class="sxs-lookup"><span data-stu-id="fa45a-121">Note that the rules for the inheritance chain may vary depending on the language or compiler that emitted the original metadata.</span></span>

 <span data-ttu-id="fa45a-122">Właściwości i zdarzenia nie są wyliczone przez `EnumMembers`.</span><span class="sxs-lookup"><span data-stu-id="fa45a-122">Properties and events are not enumerated by `EnumMembers`.</span></span> <span data-ttu-id="fa45a-123">Aby je wyliczyć, należy użyć [właściwości EnumProperties](imetadataimport-enumproperties-method.md) lub [EnumEvents](imetadataimport-enumevents-method.md).</span><span class="sxs-lookup"><span data-stu-id="fa45a-123">To enumerate those, use [EnumProperties](imetadataimport-enumproperties-method.md) or [EnumEvents](imetadataimport-enumevents-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="fa45a-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fa45a-124">Requirements</span></span>  
 <span data-ttu-id="fa45a-125">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa45a-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa45a-126">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="fa45a-126">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fa45a-127">**Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fa45a-127">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fa45a-128">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa45a-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa45a-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fa45a-129">See also</span></span>

- [<span data-ttu-id="fa45a-130">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="fa45a-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="fa45a-131">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="fa45a-131">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
