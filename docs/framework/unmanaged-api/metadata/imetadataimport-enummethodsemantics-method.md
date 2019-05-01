---
title: IMetaDataImport::EnumMethodSemantics — Metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 16cfa6df6251cd67860155cb8092e77a835eaaef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992423"
---
# <a name="imetadataimportenummethodsemantics-method"></a><span data-ttu-id="5382d-102">IMetaDataImport::EnumMethodSemantics — Metoda</span><span class="sxs-lookup"><span data-stu-id="5382d-102">IMetaDataImport::EnumMethodSemantics Method</span></span>
<span data-ttu-id="5382d-103">Wylicza właściwości i zdarzenia zmiany właściwości, do których odnosi się określonej metody.</span><span class="sxs-lookup"><span data-stu-id="5382d-103">Enumerates the properties and the property-change events to which the specified method is related.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5382d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5382d-104">Syntax</span></span>  
  
```  
HRESULT EnumMethodSemantics (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,   
   [out] mdToken         rEventProp[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcEventProp  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5382d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5382d-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="5382d-106">[out w] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="5382d-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="5382d-107">Musi to być wartość NULL dla pierwszego wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="5382d-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="5382d-108">[in] Token MethodDef, który ogranicza zakres wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5382d-108">[in] A MethodDef token that limits the scope of the enumeration.</span></span>  
  
 `rEventProp`  
 <span data-ttu-id="5382d-109">[out] Tablica do przechowywania właściwości lub zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="5382d-109">[out] The array used to store the events or properties.</span></span>  
  
 `cMax`  
 <span data-ttu-id="5382d-110">[in] Maksymalny rozmiar `rEventProp` tablicy.</span><span class="sxs-lookup"><span data-stu-id="5382d-110">[in] The maximum size of the `rEventProp` array.</span></span>  
  
 `pcEventProp`  
 <span data-ttu-id="5382d-111">[out] Numer zdarzenia lub właściwości zwracane w `rEventProp`.</span><span class="sxs-lookup"><span data-stu-id="5382d-111">[out] The number of events or properties returned in `rEventProp`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5382d-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5382d-112">Return Value</span></span>  
  
|<span data-ttu-id="5382d-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5382d-113">HRESULT</span></span>|<span data-ttu-id="5382d-114">Opis</span><span class="sxs-lookup"><span data-stu-id="5382d-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="5382d-115">`EnumMethodSemantics` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="5382d-115">`EnumMethodSemantics` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="5382d-116">Brak zdarzeń i właściwości do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5382d-116">There are no events or properties to enumerate.</span></span> <span data-ttu-id="5382d-117">W takim przypadku `pcEventProp` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="5382d-117">In that case, `pcEventProp` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5382d-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5382d-118">Remarks</span></span>  
 <span data-ttu-id="5382d-119">Zdefiniuj wiele typów środowiska wykonawczego języka wspólnego *właściwość* `Changed` zdarzeń i `On` *właściwość* `Changed` metody odnoszące się do ich właściwości.</span><span class="sxs-lookup"><span data-stu-id="5382d-119">Many common language runtime types define *Property*`Changed` events and `On`*Property*`Changed` methods related to their properties.</span></span> <span data-ttu-id="5382d-120">Na przykład <xref:System.Windows.Forms.Control?displayProperty=nameWithType> typ definiuje <xref:System.Windows.Forms.Control.Font%2A> właściwości <xref:System.Windows.Forms.Control.FontChanged> zdarzenia i <xref:System.Windows.Forms.Control.OnFontChanged%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5382d-120">For example, the <xref:System.Windows.Forms.Control?displayProperty=nameWithType> type defines a <xref:System.Windows.Forms.Control.Font%2A> property, a <xref:System.Windows.Forms.Control.FontChanged> event, and an <xref:System.Windows.Forms.Control.OnFontChanged%2A> method.</span></span> <span data-ttu-id="5382d-121">Metoda dostępu set <xref:System.Windows.Forms.Control.Font%2A> wywołaniach właściwości <xref:System.Windows.Forms.Control.OnFontChanged%2A> metody, która z kolei wywołuje <xref:System.Windows.Forms.Control.FontChanged> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5382d-121">The set accessor method of the <xref:System.Windows.Forms.Control.Font%2A> property calls <xref:System.Windows.Forms.Control.OnFontChanged%2A> method, which in turn raises the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span> <span data-ttu-id="5382d-122">Możesz wywołać `EnumMethodSemantics` przy użyciu MethodDef dla <xref:System.Windows.Forms.Control.OnFontChanged%2A> uzyskać odwołania do <xref:System.Windows.Forms.Control.Font%2A> właściwości i <xref:System.Windows.Forms.Control.FontChanged> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5382d-122">You would call `EnumMethodSemantics` using the MethodDef for <xref:System.Windows.Forms.Control.OnFontChanged%2A> to get references to the <xref:System.Windows.Forms.Control.Font%2A> property and the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5382d-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5382d-123">Requirements</span></span>  
 <span data-ttu-id="5382d-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5382d-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5382d-125">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="5382d-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5382d-126">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5382d-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5382d-127">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5382d-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5382d-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5382d-128">See also</span></span>

- [<span data-ttu-id="5382d-129">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="5382d-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="5382d-130">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="5382d-130">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
