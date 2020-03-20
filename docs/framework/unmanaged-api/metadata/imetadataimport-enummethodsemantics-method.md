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
ms.openlocfilehash: f20652a7f86576e64646a1f63c3e2c48b55cf811
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175463"
---
# <a name="imetadataimportenummethodsemantics-method"></a><span data-ttu-id="c0ecf-102">IMetaDataImport::EnumMethodSemantics — Metoda</span><span class="sxs-lookup"><span data-stu-id="c0ecf-102">IMetaDataImport::EnumMethodSemantics Method</span></span>
<span data-ttu-id="c0ecf-103">Wylicza właściwości i zdarzenia zmiany właściwości, z którymi jest powiązana określona metoda.</span><span class="sxs-lookup"><span data-stu-id="c0ecf-103">Enumerates the properties and the property-change events to which the specified method is related.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0ecf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c0ecf-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodSemantics (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,
   [out] mdToken         rEventProp[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcEventProp  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0ecf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c0ecf-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="c0ecf-106">[w, na zewnątrz] Wskaźnik do wyliczacza.</span><span class="sxs-lookup"><span data-stu-id="c0ecf-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="c0ecf-107">Musi to być null dla pierwszego wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="c0ecf-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="c0ecf-108">[w] Token MethodDef, który ogranicza zakres wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="c0ecf-108">[in] A MethodDef token that limits the scope of the enumeration.</span></span>  
  
 `rEventProp`  
 <span data-ttu-id="c0ecf-109">[na zewnątrz] Tablica używana do przechowywania zdarzeń lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="c0ecf-109">[out] The array used to store the events or properties.</span></span>  
  
 `cMax`  
 <span data-ttu-id="c0ecf-110">[w] Maksymalny rozmiar `rEventProp` tablicy.</span><span class="sxs-lookup"><span data-stu-id="c0ecf-110">[in] The maximum size of the `rEventProp` array.</span></span>  
  
 `pcEventProp`  
 <span data-ttu-id="c0ecf-111">[na zewnątrz] Liczba zdarzeń lub właściwości zwróconych w `rEventProp`.</span><span class="sxs-lookup"><span data-stu-id="c0ecf-111">[out] The number of events or properties returned in `rEventProp`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c0ecf-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c0ecf-112">Return Value</span></span>  
  
|<span data-ttu-id="c0ecf-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c0ecf-113">HRESULT</span></span>|<span data-ttu-id="c0ecf-114">Opis</span><span class="sxs-lookup"><span data-stu-id="c0ecf-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="c0ecf-115">`EnumMethodSemantics`zwrócono pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="c0ecf-115">`EnumMethodSemantics` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="c0ecf-116">Nie ma żadnych zdarzeń lub właściwości do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="c0ecf-116">There are no events or properties to enumerate.</span></span> <span data-ttu-id="c0ecf-117">W takim `pcEventProp` przypadku wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="c0ecf-117">In that case, `pcEventProp` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0ecf-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c0ecf-118">Remarks</span></span>  
 <span data-ttu-id="c0ecf-119">Wiele typowych typów środowiska uruchomieniowego języka *zdefiniować zdarzenia właściwości* `Changed` i `On`metody *właściwości* `Changed` związane z ich właściwości.</span><span class="sxs-lookup"><span data-stu-id="c0ecf-119">Many common language runtime types define *Property*`Changed` events and `On`*Property*`Changed` methods related to their properties.</span></span> <span data-ttu-id="c0ecf-120">Na przykład <xref:System.Windows.Forms.Control?displayProperty=nameWithType> typ definiuje <xref:System.Windows.Forms.Control.Font%2A> właściwość, <xref:System.Windows.Forms.Control.FontChanged> zdarzenie i <xref:System.Windows.Forms.Control.OnFontChanged%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="c0ecf-120">For example, the <xref:System.Windows.Forms.Control?displayProperty=nameWithType> type defines a <xref:System.Windows.Forms.Control.Font%2A> property, a <xref:System.Windows.Forms.Control.FontChanged> event, and an <xref:System.Windows.Forms.Control.OnFontChanged%2A> method.</span></span> <span data-ttu-id="c0ecf-121">Set metody <xref:System.Windows.Forms.Control.Font%2A> akcesora <xref:System.Windows.Forms.Control.OnFontChanged%2A> właściwości wywołuje metodę, <xref:System.Windows.Forms.Control.FontChanged> która z kolei wywołuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="c0ecf-121">The set accessor method of the <xref:System.Windows.Forms.Control.Font%2A> property calls <xref:System.Windows.Forms.Control.OnFontChanged%2A> method, which in turn raises the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span> <span data-ttu-id="c0ecf-122">Wywołanie `EnumMethodSemantics` przy użyciu MethodDef, <xref:System.Windows.Forms.Control.OnFontChanged%2A> aby uzyskać <xref:System.Windows.Forms.Control.Font%2A> odwołania <xref:System.Windows.Forms.Control.FontChanged> do właściwości i zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c0ecf-122">You would call `EnumMethodSemantics` using the MethodDef for <xref:System.Windows.Forms.Control.OnFontChanged%2A> to get references to the <xref:System.Windows.Forms.Control.Font%2A> property and the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0ecf-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c0ecf-123">Requirements</span></span>  
 <span data-ttu-id="c0ecf-124">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0ecf-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0ecf-125">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="c0ecf-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c0ecf-126">**Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c0ecf-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c0ecf-127">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0ecf-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0ecf-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c0ecf-128">See also</span></span>

- [<span data-ttu-id="c0ecf-129">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c0ecf-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="c0ecf-130">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="c0ecf-130">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
