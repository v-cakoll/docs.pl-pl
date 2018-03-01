---
title: "IMetaDataImport::EnumMethodSemantics — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataImport.EnumMethodSemantics
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodSemantics
helpviewer_keywords:
- EnumMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::EnumMethodSemantics method [.NET Framework metadata]
ms.assetid: e7e3c630-9691-46d6-94df-b5593a7bb08a
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 883505076fa9ff4f335c08b069e801ebda1ebb2d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenummethodsemantics-method"></a><span data-ttu-id="cf072-102">IMetaDataImport::EnumMethodSemantics — Metoda</span><span class="sxs-lookup"><span data-stu-id="cf072-102">IMetaDataImport::EnumMethodSemantics Method</span></span>
<span data-ttu-id="cf072-103">Wylicza właściwości i zdarzenia zmiany właściwości, których dotyczy określonej metody.</span><span class="sxs-lookup"><span data-stu-id="cf072-103">Enumerates the properties and the property-change events to which the specified method is related.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf072-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cf072-104">Syntax</span></span>  
  
```  
HRESULT EnumMethodSemantics (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,   
   [out] mdToken         rEventProp[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcEventProp  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cf072-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cf072-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="cf072-106">[w, out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="cf072-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="cf072-107">Musi to być wartość NULL dla pierwsze wywołanie tej metody.</span><span class="sxs-lookup"><span data-stu-id="cf072-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="cf072-108">[in] Token MethodDef, który ogranicza zakres wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="cf072-108">[in] A MethodDef token that limits the scope of the enumeration.</span></span>  
  
 `rEventProp`  
 <span data-ttu-id="cf072-109">[out] Tablica używany do przechowywania zdarzeń lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="cf072-109">[out] The array used to store the events or properties.</span></span>  
  
 `cMax`  
 <span data-ttu-id="cf072-110">[in] Maksymalny rozmiar `rEventProp` tablicy.</span><span class="sxs-lookup"><span data-stu-id="cf072-110">[in] The maximum size of the `rEventProp` array.</span></span>  
  
 `pcEventProp`  
 <span data-ttu-id="cf072-111">[out] Liczba zdarzeń lub właściwości zwracane w `rEventProp`.</span><span class="sxs-lookup"><span data-stu-id="cf072-111">[out] The number of events or properties returned in `rEventProp`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cf072-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cf072-112">Return Value</span></span>  
  
|<span data-ttu-id="cf072-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cf072-113">HRESULT</span></span>|<span data-ttu-id="cf072-114">Opis</span><span class="sxs-lookup"><span data-stu-id="cf072-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="cf072-115">`EnumMethodSemantics`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="cf072-115">`EnumMethodSemantics` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="cf072-116">Nie ma żadnych zdarzeń lub właściwości do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="cf072-116">There are no events or properties to enumerate.</span></span> <span data-ttu-id="cf072-117">W takim przypadku `pcEventProp` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="cf072-117">In that case, `pcEventProp` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf072-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cf072-118">Remarks</span></span>  
 <span data-ttu-id="cf072-119">Zdefiniuj wiele typów środowiska uruchomieniowego języka wspólnego *właściwości* `Changed` zdarzeń i `On` *właściwości* `Changed` metody odnoszące się do ich właściwości.</span><span class="sxs-lookup"><span data-stu-id="cf072-119">Many common language runtime types define *Property*`Changed` events and `On`*Property*`Changed` methods related to their properties.</span></span> <span data-ttu-id="cf072-120">Na przykład <xref:System.Windows.Forms.Control?displayProperty=nameWithType> definiuje typ <xref:System.Windows.Forms.Control.Font%2A> właściwości, <xref:System.Windows.Forms.Control.FontChanged> zdarzenia i <xref:System.Windows.Forms.Control.OnFontChanged%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="cf072-120">For example, the <xref:System.Windows.Forms.Control?displayProperty=nameWithType> type defines a <xref:System.Windows.Forms.Control.Font%2A> property, a <xref:System.Windows.Forms.Control.FontChanged> event, and an <xref:System.Windows.Forms.Control.OnFontChanged%2A> method.</span></span> <span data-ttu-id="cf072-121">Metoda dostępu set <xref:System.Windows.Forms.Control.Font%2A> wywołaniach właściwości <xref:System.Windows.Forms.Control.OnFontChanged%2A> metodę, która z kolei wywołuje <xref:System.Windows.Forms.Control.FontChanged> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="cf072-121">The set accessor method of the <xref:System.Windows.Forms.Control.Font%2A> property calls <xref:System.Windows.Forms.Control.OnFontChanged%2A> method, which in turn raises the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span> <span data-ttu-id="cf072-122">Możesz wywołać `EnumMethodSemantics` przy użyciu elementu MethodDef dla <xref:System.Windows.Forms.Control.OnFontChanged%2A> można pobrać odwołań do <xref:System.Windows.Forms.Control.Font%2A> właściwości i <xref:System.Windows.Forms.Control.FontChanged> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="cf072-122">You would call `EnumMethodSemantics` using the MethodDef for <xref:System.Windows.Forms.Control.OnFontChanged%2A> to get references to the <xref:System.Windows.Forms.Control.Font%2A> property and the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf072-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cf072-123">Requirements</span></span>  
 <span data-ttu-id="cf072-124">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf072-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf072-125">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cf072-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cf072-126">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cf072-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cf072-127">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf072-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf072-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cf072-128">See Also</span></span>  
 [<span data-ttu-id="cf072-129">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="cf072-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="cf072-130">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="cf072-130">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
