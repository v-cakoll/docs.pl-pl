---
title: IMetaDataEmit::SetClassLayout — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetClassLayout
helpviewer_keywords:
- IMetaDataEmit::SetClassLayout method [.NET Framework metadata]
- SetClassLayout method [.NET Framework metadata]
ms.assetid: 2576c449-388d-4434-a0e1-9f53991e11b6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 80bf9de3eb274bf536b2794ba2ed14e7e9b553cc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050054"
---
# <a name="imetadataemitsetclasslayout-method"></a><span data-ttu-id="7094e-102">IMetaDataEmit::SetClassLayout — Metoda</span><span class="sxs-lookup"><span data-stu-id="7094e-102">IMetaDataEmit::SetClassLayout Method</span></span>
<span data-ttu-id="7094e-103">Kończy układ pól dla klasy, która została zdefiniowana przez wcześniejsze wywołanie [definetypedef — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="7094e-103">Completes the layout of fields for a class that has been defined by a prior call to [DefineTypeDef Method](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7094e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7094e-104">Syntax</span></span>  
  
```  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,   
    [in]  DWORD               dwPackSize,   
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],   
    [in]  ULONG               ulClassSize   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7094e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7094e-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="7094e-106">[in] `mdTypeDef` Tokenu, który określa klasy, która ma być rozmieszczony.</span><span class="sxs-lookup"><span data-stu-id="7094e-106">[in] An `mdTypeDef` token that specifies the class to be laid out.</span></span>  
  
 `dwPackSize`  
 <span data-ttu-id="7094e-107">[in] Rozmiar pakowania: 1, 2, 4, 8 lub 16 bajtów.</span><span class="sxs-lookup"><span data-stu-id="7094e-107">[in] The packing size: 1, 2, 4, 8 or 16 bytes.</span></span> <span data-ttu-id="7094e-108">Rozmiar pakowania to liczbę bajtów między sąsiadujące pola.</span><span class="sxs-lookup"><span data-stu-id="7094e-108">The packing size is the number of bytes between adjacent fields.</span></span>  
  
 `rFieldOffsets`  
 <span data-ttu-id="7094e-109">[in] Tablica [cor_field_offset —](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) struktur, z których każdy określa pola klasy i przesunięcie w klasie.</span><span class="sxs-lookup"><span data-stu-id="7094e-109">[in] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) structures, each of which specifies a field of the class and the field's offset within the class.</span></span> <span data-ttu-id="7094e-110">Zakończenie tablicy przy użyciu `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="7094e-110">Terminate the array with `mdTokenNil`.</span></span>  
  
 `ulClassSize`  
 <span data-ttu-id="7094e-111">[in] Rozmiar w bajtach klasy.</span><span class="sxs-lookup"><span data-stu-id="7094e-111">[in] The size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7094e-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7094e-112">Remarks</span></span>  
 <span data-ttu-id="7094e-113">Klasa jest wstępnie zdefiniowana przez wywołanie metody [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) metoda i określając jeden z trzech układów pola klasy: automatyczny, sekwencyjnych lub jawnego.</span><span class="sxs-lookup"><span data-stu-id="7094e-113">The class is initially defined by calling the [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) method, and specifying one of three layouts for the fields of the class: automatic, sequential, or explicit.</span></span> <span data-ttu-id="7094e-114">Zwykle będzie Użyj automatycznego układu i pozwól środowiska uruchomieniowego wybierasz najlepszą metodę, aby zmienić układ pól.</span><span class="sxs-lookup"><span data-stu-id="7094e-114">Normally, you would use automatic layout and let the runtime choose the best way to lay out the fields.</span></span>  
  
 <span data-ttu-id="7094e-115">Jednakże możesz zechcieć pola rozmieszczony zgodnie z rozmieszczenie niezarządzany kod używa.</span><span class="sxs-lookup"><span data-stu-id="7094e-115">However, you might want the fields laid out according to the arrangement that unmanaged code uses.</span></span> <span data-ttu-id="7094e-116">W takim przypadku wybierz Sekwencyjna lub jawnego układu i wywołania `SetClassLayout` do ukończenia układ pól:</span><span class="sxs-lookup"><span data-stu-id="7094e-116">In this case, choose either sequential or explicit layout and call `SetClassLayout` to complete the layout of the fields:</span></span>  
  
- <span data-ttu-id="7094e-117">Sekwencyjne układu: Określ rozmiar pakowania.</span><span class="sxs-lookup"><span data-stu-id="7094e-117">Sequential layout: Specify the packing size.</span></span> <span data-ttu-id="7094e-118">Pole jest wyrównany zgodnie z rozmiarem fizyczne lub rozmiar pakowania, niezależnie od wyników w mniejszych przesunięcie pola.</span><span class="sxs-lookup"><span data-stu-id="7094e-118">A field is aligned according to either its natural size or the packing size, whichever results in the smaller offset of the field.</span></span> <span data-ttu-id="7094e-119">Ustaw `rFieldOffsets` i `ulClassSize` do zera.</span><span class="sxs-lookup"><span data-stu-id="7094e-119">Set `rFieldOffsets` and `ulClassSize` to zero.</span></span>  
  
- <span data-ttu-id="7094e-120">Jawnego układu: Określ przesunięcie każdego pola lub określić rozmiar klasy i rozmiarem pakowania.</span><span class="sxs-lookup"><span data-stu-id="7094e-120">Explicit layout: Either specify the offset of each field or specify the class size and the packing size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7094e-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7094e-121">Requirements</span></span>  
 <span data-ttu-id="7094e-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7094e-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7094e-123">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="7094e-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7094e-124">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7094e-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7094e-125">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7094e-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7094e-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7094e-126">See also</span></span>

- [<span data-ttu-id="7094e-127">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="7094e-127">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="7094e-128">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="7094e-128">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
