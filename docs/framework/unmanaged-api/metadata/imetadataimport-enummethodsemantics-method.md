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
ms.openlocfilehash: 213cbd955e3d47a49abde579a54af48641e225ec
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491930"
---
# <a name="imetadataimportenummethodsemantics-method"></a><span data-ttu-id="ed7dd-102">IMetaDataImport::EnumMethodSemantics — Metoda</span><span class="sxs-lookup"><span data-stu-id="ed7dd-102">IMetaDataImport::EnumMethodSemantics Method</span></span>
<span data-ttu-id="ed7dd-103">Wylicza właściwości i zdarzenia zmiany właściwości, z którymi powiązana jest określona metoda.</span><span class="sxs-lookup"><span data-stu-id="ed7dd-103">Enumerates the properties and the property-change events to which the specified method is related.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed7dd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ed7dd-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodSemantics (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,
   [out] mdToken         rEventProp[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcEventProp  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed7dd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ed7dd-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="ed7dd-106">[in. out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="ed7dd-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="ed7dd-107">Musi ona mieć wartość NULL dla pierwszego wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="ed7dd-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="ed7dd-108">podczas Token MethodDef, który ogranicza zakres wyliczania.</span><span class="sxs-lookup"><span data-stu-id="ed7dd-108">[in] A MethodDef token that limits the scope of the enumeration.</span></span>  
  
 `rEventProp`  
 <span data-ttu-id="ed7dd-109">określoną Tablica służąca do przechowywania zdarzeń lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="ed7dd-109">[out] The array used to store the events or properties.</span></span>  
  
 `cMax`  
 <span data-ttu-id="ed7dd-110">podczas Maksymalny rozmiar `rEventProp` tablicy.</span><span class="sxs-lookup"><span data-stu-id="ed7dd-110">[in] The maximum size of the `rEventProp` array.</span></span>  
  
 `pcEventProp`  
 <span data-ttu-id="ed7dd-111">określoną Liczba zwróconych zdarzeń lub właściwości `rEventProp` .</span><span class="sxs-lookup"><span data-stu-id="ed7dd-111">[out] The number of events or properties returned in `rEventProp`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ed7dd-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ed7dd-112">Return Value</span></span>  
  
|<span data-ttu-id="ed7dd-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ed7dd-113">HRESULT</span></span>|<span data-ttu-id="ed7dd-114">Opis</span><span class="sxs-lookup"><span data-stu-id="ed7dd-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="ed7dd-115">`EnumMethodSemantics`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="ed7dd-115">`EnumMethodSemantics` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="ed7dd-116">Brak zdarzeń lub właściwości do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="ed7dd-116">There are no events or properties to enumerate.</span></span> <span data-ttu-id="ed7dd-117">W takim przypadku `pcEventProp` jest równa zero.</span><span class="sxs-lookup"><span data-stu-id="ed7dd-117">In that case, `pcEventProp` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ed7dd-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ed7dd-118">Remarks</span></span>  
 <span data-ttu-id="ed7dd-119">Wiele typów środowiska uruchomieniowego języka wspólnego definiuje zdarzenia *Właściwości* `Changed` i `On` metody *Właściwości* `Changed` powiązane z ich właściwościami.</span><span class="sxs-lookup"><span data-stu-id="ed7dd-119">Many common language runtime types define *Property*`Changed` events and `On`*Property*`Changed` methods related to their properties.</span></span> <span data-ttu-id="ed7dd-120">Na przykład <xref:System.Windows.Forms.Control?displayProperty=nameWithType> Typ definiuje <xref:System.Windows.Forms.Control.Font%2A> Właściwość, <xref:System.Windows.Forms.Control.FontChanged> zdarzenie i <xref:System.Windows.Forms.Control.OnFontChanged%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="ed7dd-120">For example, the <xref:System.Windows.Forms.Control?displayProperty=nameWithType> type defines a <xref:System.Windows.Forms.Control.Font%2A> property, a <xref:System.Windows.Forms.Control.FontChanged> event, and an <xref:System.Windows.Forms.Control.OnFontChanged%2A> method.</span></span> <span data-ttu-id="ed7dd-121">Metoda dostępu set metody <xref:System.Windows.Forms.Control.Font%2A> wywołania właściwości <xref:System.Windows.Forms.Control.OnFontChanged%2A> , która z kolei podnosi <xref:System.Windows.Forms.Control.FontChanged> zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="ed7dd-121">The set accessor method of the <xref:System.Windows.Forms.Control.Font%2A> property calls <xref:System.Windows.Forms.Control.OnFontChanged%2A> method, which in turn raises the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span> <span data-ttu-id="ed7dd-122">Należy wywołać `EnumMethodSemantics` użycie elementu MethodDef dla, <xref:System.Windows.Forms.Control.OnFontChanged%2A> Aby uzyskać odwołania do <xref:System.Windows.Forms.Control.Font%2A> właściwości i <xref:System.Windows.Forms.Control.FontChanged> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ed7dd-122">You would call `EnumMethodSemantics` using the MethodDef for <xref:System.Windows.Forms.Control.OnFontChanged%2A> to get references to the <xref:System.Windows.Forms.Control.Font%2A> property and the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed7dd-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ed7dd-123">Requirements</span></span>  
 <span data-ttu-id="ed7dd-124">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed7dd-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed7dd-125">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ed7dd-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ed7dd-126">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ed7dd-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ed7dd-127">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed7dd-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed7dd-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ed7dd-128">See also</span></span>

- [<span data-ttu-id="ed7dd-129">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ed7dd-129">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="ed7dd-130">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="ed7dd-130">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
