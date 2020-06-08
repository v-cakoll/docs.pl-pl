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
ms.openlocfilehash: cc3bc5140da0634b5172f6253de3de37bff487f1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492039"
---
# <a name="imetadataimportenummembers-method"></a><span data-ttu-id="1c0cc-102">IMetaDataImport::EnumMembers — Metoda</span><span class="sxs-lookup"><span data-stu-id="1c0cc-102">IMetaDataImport::EnumMembers Method</span></span>
<span data-ttu-id="1c0cc-103">Wylicza tokeny MemberDef reprezentujące składowe określonego typu.</span><span class="sxs-lookup"><span data-stu-id="1c0cc-103">Enumerates MemberDef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c0cc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1c0cc-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMembers (
   [in, out]  HCORENUM    *phEnum,
   [in]  mdTypeDef   cl,
   [out] mdToken     rMembers[],
   [in]  ULONG       cMax,
   [out] ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c0cc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1c0cc-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="1c0cc-106">[in. out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="1c0cc-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="1c0cc-107">podczas Token TypeDef reprezentujący typ, którego składowe mają zostać wyliczone.</span><span class="sxs-lookup"><span data-stu-id="1c0cc-107">[in] A TypeDef token representing the type whose members are to be enumerated.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="1c0cc-108">określoną Tablica użyta do przechowywania tokenów MemberDef.</span><span class="sxs-lookup"><span data-stu-id="1c0cc-108">[out] The array used to hold the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="1c0cc-109">podczas Maksymalny rozmiar `rMembers` tablicy.</span><span class="sxs-lookup"><span data-stu-id="1c0cc-109">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="1c0cc-110">określoną Rzeczywista liczba tokenów MemberDef zwrócona w `rMembers` .</span><span class="sxs-lookup"><span data-stu-id="1c0cc-110">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1c0cc-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1c0cc-111">Return Value</span></span>  
  
|<span data-ttu-id="1c0cc-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1c0cc-112">HRESULT</span></span>|<span data-ttu-id="1c0cc-113">Opis</span><span class="sxs-lookup"><span data-stu-id="1c0cc-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="1c0cc-114">`EnumMembers`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="1c0cc-114">`EnumMembers` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="1c0cc-115">Brak tokenów MemberDef do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="1c0cc-115">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="1c0cc-116">W takim przypadku `pcTokens` jest równa zero.</span><span class="sxs-lookup"><span data-stu-id="1c0cc-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c0cc-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1c0cc-117">Remarks</span></span>  
 <span data-ttu-id="1c0cc-118">Podczas wyliczania kolekcji elementów członkowskich klasy `EnumMembers` zwraca tylko elementy członkowskie (pola i metody, ale **nie** właściwości ani zdarzenia) zdefiniowane bezpośrednio w klasie.</span><span class="sxs-lookup"><span data-stu-id="1c0cc-118">When enumerating collections of members for a class, `EnumMembers` returns only members (fields and methods, but **not** properties or events) defined directly on the class.</span></span> <span data-ttu-id="1c0cc-119">Nie zwraca żadnych elementów członkowskich, które dziedziczy Klasa, nawet jeśli Klasa dostarcza implementację dla tych dziedziczonych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="1c0cc-119">It does not return any members that the class inherits, even if the class provides an implementation for those inherited members.</span></span> <span data-ttu-id="1c0cc-120">Aby wyliczyć dziedziczone elementy członkowskie, obiekt wywołujący musi jawnie przeprowadzić łańcuch dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="1c0cc-120">To enumerate inherited members, the caller must explicitly walk the inheritance chain.</span></span> <span data-ttu-id="1c0cc-121">Należy zauważyć, że reguły dla łańcucha dziedziczenia mogą się różnić w zależności od języka lub kompilatora, który emituje oryginalne metadane.</span><span class="sxs-lookup"><span data-stu-id="1c0cc-121">Note that the rules for the inheritance chain may vary depending on the language or compiler that emitted the original metadata.</span></span>

 <span data-ttu-id="1c0cc-122">Właściwości i zdarzenia nie są wyliczane przez `EnumMembers` .</span><span class="sxs-lookup"><span data-stu-id="1c0cc-122">Properties and events are not enumerated by `EnumMembers`.</span></span> <span data-ttu-id="1c0cc-123">Aby wyliczyć te, użyj [EnumProperties —](imetadataimport-enumproperties-method.md) lub [EnumEvents —](imetadataimport-enumevents-method.md).</span><span class="sxs-lookup"><span data-stu-id="1c0cc-123">To enumerate those, use [EnumProperties](imetadataimport-enumproperties-method.md) or [EnumEvents](imetadataimport-enumevents-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="1c0cc-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1c0cc-124">Requirements</span></span>  
 <span data-ttu-id="1c0cc-125">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c0cc-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c0cc-126">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="1c0cc-126">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1c0cc-127">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1c0cc-127">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1c0cc-128">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c0cc-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c0cc-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1c0cc-129">See also</span></span>

- [<span data-ttu-id="1c0cc-130">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1c0cc-130">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="1c0cc-131">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="1c0cc-131">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
