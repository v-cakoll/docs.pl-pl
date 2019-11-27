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
ms.openlocfilehash: acb772a64c8f13405f2836bb5f4f308986dce414
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447654"
---
# <a name="imetadataimportenummembers-method"></a><span data-ttu-id="fc85f-102">IMetaDataImport::EnumMembers — Metoda</span><span class="sxs-lookup"><span data-stu-id="fc85f-102">IMetaDataImport::EnumMembers Method</span></span>
<span data-ttu-id="fc85f-103">Wylicza tokeny MemberDef reprezentujące składowe określonego typu.</span><span class="sxs-lookup"><span data-stu-id="fc85f-103">Enumerates MemberDef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc85f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fc85f-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMembers (   
   [in, out]  HCORENUM    *phEnum,   
   [in]  mdTypeDef   cl,   
   [out] mdToken     rMembers[],   
   [in]  ULONG       cMax,   
   [out] ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc85f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fc85f-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="fc85f-106">[in. out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="fc85f-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="fc85f-107">podczas Token TypeDef reprezentujący typ, którego składowe mają zostać wyliczone.</span><span class="sxs-lookup"><span data-stu-id="fc85f-107">[in] A TypeDef token representing the type whose members are to be enumerated.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="fc85f-108">określoną Tablica użyta do przechowywania tokenów MemberDef.</span><span class="sxs-lookup"><span data-stu-id="fc85f-108">[out] The array used to hold the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="fc85f-109">podczas Maksymalny rozmiar tablicy `rMembers`.</span><span class="sxs-lookup"><span data-stu-id="fc85f-109">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="fc85f-110">określoną Rzeczywista liczba tokenów MemberDef zwróconych w `rMembers`.</span><span class="sxs-lookup"><span data-stu-id="fc85f-110">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fc85f-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fc85f-111">Return Value</span></span>  
  
|<span data-ttu-id="fc85f-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fc85f-112">HRESULT</span></span>|<span data-ttu-id="fc85f-113">Opis</span><span class="sxs-lookup"><span data-stu-id="fc85f-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="fc85f-114">`EnumMembers` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="fc85f-114">`EnumMembers` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="fc85f-115">Brak tokenów MemberDef do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="fc85f-115">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="fc85f-116">W takim przypadku `pcTokens` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="fc85f-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc85f-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fc85f-117">Remarks</span></span>  
 <span data-ttu-id="fc85f-118">Podczas wyliczania kolekcji elementów członkowskich klasy `EnumMembers` zwraca tylko elementy członkowskie (pola i metody, ale **nie** właściwości ani zdarzenia) zdefiniowane bezpośrednio w klasie.</span><span class="sxs-lookup"><span data-stu-id="fc85f-118">When enumerating collections of members for a class, `EnumMembers` returns only members (fields and methods, but **not** properties or events) defined directly on the class.</span></span> <span data-ttu-id="fc85f-119">Nie zwraca żadnych elementów członkowskich, które dziedziczy Klasa, nawet jeśli Klasa dostarcza implementację dla tych dziedziczonych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="fc85f-119">It does not return any members that the class inherits, even if the class provides an implementation for those inherited members.</span></span> <span data-ttu-id="fc85f-120">Aby wyliczyć dziedziczone elementy członkowskie, obiekt wywołujący musi jawnie przeprowadzić łańcuch dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="fc85f-120">To enumerate inherited members, the caller must explicitly walk the inheritance chain.</span></span> <span data-ttu-id="fc85f-121">Należy zauważyć, że reguły dla łańcucha dziedziczenia mogą się różnić w zależności od języka lub kompilatora, który emituje oryginalne metadane.</span><span class="sxs-lookup"><span data-stu-id="fc85f-121">Note that the rules for the inheritance chain may vary depending on the language or compiler that emitted the original metadata.</span></span>
 
 <span data-ttu-id="fc85f-122">Właściwości i zdarzenia nie są wyliczane przez `EnumMembers`.</span><span class="sxs-lookup"><span data-stu-id="fc85f-122">Properties and events are not enumerated by `EnumMembers`.</span></span> <span data-ttu-id="fc85f-123">Aby wyliczyć te, użyj [EnumProperties —](imetadataimport-enumproperties-method.md) lub [EnumEvents —](imetadataimport-enumevents-method.md).</span><span class="sxs-lookup"><span data-stu-id="fc85f-123">To enumerate those, use [EnumProperties](imetadataimport-enumproperties-method.md) or [EnumEvents](imetadataimport-enumevents-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="fc85f-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fc85f-124">Requirements</span></span>  
 <span data-ttu-id="fc85f-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc85f-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc85f-126">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="fc85f-126">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fc85f-127">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fc85f-127">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fc85f-128">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc85f-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc85f-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fc85f-129">See also</span></span>

- [<span data-ttu-id="fc85f-130">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="fc85f-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="fc85f-131">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="fc85f-131">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
