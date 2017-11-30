---
title: "IMetaDataEmit::SetClassLayout — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetClassLayout
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetClassLayout
helpviewer_keywords:
- IMetaDataEmit::SetClassLayout method [.NET Framework metadata]
- SetClassLayout method [.NET Framework metadata]
ms.assetid: 2576c449-388d-4434-a0e1-9f53991e11b6
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5a68d94cbea408bee90b117965f83f760ba7ea5c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsetclasslayout-method"></a><span data-ttu-id="911f1-102">IMetaDataEmit::SetClassLayout — Metoda</span><span class="sxs-lookup"><span data-stu-id="911f1-102">IMetaDataEmit::SetClassLayout Method</span></span>
<span data-ttu-id="911f1-103">Kończy układ pól dla klasy, która została zdefiniowana przez poprzednie wywołanie [DefineTypeDef — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="911f1-103">Completes the layout of fields for a class that has been defined by a prior call to [DefineTypeDef Method](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="911f1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="911f1-104">Syntax</span></span>  
  
```  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,   
    [in]  DWORD               dwPackSize,   
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],   
    [in]  ULONG               ulClassSize   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="911f1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="911f1-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="911f1-106">[in] `mdTypeDef` Token, który określa klasę, do którego układ określa się.</span><span class="sxs-lookup"><span data-stu-id="911f1-106">[in] An `mdTypeDef` token that specifies the class to be laid out.</span></span>  
  
 `dwPackSize`  
 <span data-ttu-id="911f1-107">[in] Rozmiar pakowania: 1, 2, 4, 8 lub 16 bajtów.</span><span class="sxs-lookup"><span data-stu-id="911f1-107">[in] The packing size: 1, 2, 4, 8 or 16 bytes.</span></span> <span data-ttu-id="911f1-108">Rozmiar pakowania jest to liczba bajtów między polami sąsiadujących ze sobą.</span><span class="sxs-lookup"><span data-stu-id="911f1-108">The packing size is the number of bytes between adjacent fields.</span></span>  
  
 `rFieldOffsets`  
 <span data-ttu-id="911f1-109">[in] Tablica [cor_field_offset —](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) struktury, z których każdy określa przesunięcie pola klasy i należące do klasy.</span><span class="sxs-lookup"><span data-stu-id="911f1-109">[in] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) structures, each of which specifies a field of the class and the field's offset within the class.</span></span> <span data-ttu-id="911f1-110">Przerwanie tablicy o `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="911f1-110">Terminate the array with `mdTokenNil`.</span></span>  
  
 `ulClassSize`  
 <span data-ttu-id="911f1-111">[in] Rozmiar w bajtach klasy.</span><span class="sxs-lookup"><span data-stu-id="911f1-111">[in] The size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="911f1-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="911f1-112">Remarks</span></span>  
 <span data-ttu-id="911f1-113">Klasa jest wstępnie zdefiniowana przez wywołanie metody [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) — metoda i określania jednego z trzech układów pola klasy: automatyczna, sekwencyjny lub jawny.</span><span class="sxs-lookup"><span data-stu-id="911f1-113">The class is initially defined by calling the [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) method, and specifying one of three layouts for the fields of the class: automatic, sequential, or explicit.</span></span> <span data-ttu-id="911f1-114">Możesz zazwyczaj używa automatyczny układ i let środowiska uruchomieniowego, wybierz najlepszy sposób, aby określić układ pól.</span><span class="sxs-lookup"><span data-stu-id="911f1-114">Normally, you would use automatic layout and let the runtime choose the best way to lay out the fields.</span></span>  
  
 <span data-ttu-id="911f1-115">Jednak może być pola, którego układ określa się zgodnie z rozmieszczeniem, który używa kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="911f1-115">However, you might want the fields laid out according to the arrangement that unmanaged code uses.</span></span> <span data-ttu-id="911f1-116">W takim przypadku wybierz układ sekwencyjny lub jawny i wywołanie `SetClassLayout` przeprowadzenie układ pól:</span><span class="sxs-lookup"><span data-stu-id="911f1-116">In this case, choose either sequential or explicit layout and call `SetClassLayout` to complete the layout of the fields:</span></span>  
  
-   <span data-ttu-id="911f1-117">Układ sekwencyjny: Określ rozmiar pakowania.</span><span class="sxs-lookup"><span data-stu-id="911f1-117">Sequential layout: Specify the packing size.</span></span> <span data-ttu-id="911f1-118">Pole jest wyrównany zgodnie z jego rozmiar fizyczne lub rozmiar pakowania, niezależnie od wyników w mniejszych przesunięcie pola.</span><span class="sxs-lookup"><span data-stu-id="911f1-118">A field is aligned according to either its natural size or the packing size, whichever results in the smaller offset of the field.</span></span> <span data-ttu-id="911f1-119">Ustaw `rFieldOffsets` i `ulClassSize` od zera.</span><span class="sxs-lookup"><span data-stu-id="911f1-119">Set `rFieldOffsets` and `ulClassSize` to zero.</span></span>  
  
-   <span data-ttu-id="911f1-120">Układ jawny: Określ przesunięcie każdego pola lub określić klasy i rozmiar pakowania.</span><span class="sxs-lookup"><span data-stu-id="911f1-120">Explicit layout: Either specify the offset of each field or specify the class size and the packing size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="911f1-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="911f1-121">Requirements</span></span>  
 <span data-ttu-id="911f1-122">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="911f1-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="911f1-123">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="911f1-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="911f1-124">**Biblioteka:** używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="911f1-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="911f1-125">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="911f1-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="911f1-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="911f1-126">See Also</span></span>  
 [<span data-ttu-id="911f1-127">IMetaDataEmit — interfejs</span><span class="sxs-lookup"><span data-stu-id="911f1-127">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="911f1-128">IMetaDataEmit2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="911f1-128">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
