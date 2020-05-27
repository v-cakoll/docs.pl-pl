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
ms.openlocfilehash: a18583ce807ffa672811f3a0cd1e744233f6eb30
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008836"
---
# <a name="imetadataemitsetclasslayout-method"></a><span data-ttu-id="e5be2-102">IMetaDataEmit::SetClassLayout — Metoda</span><span class="sxs-lookup"><span data-stu-id="e5be2-102">IMetaDataEmit::SetClassLayout Method</span></span>
<span data-ttu-id="e5be2-103">Uzupełnia układ pól dla klasy, która została zdefiniowana przez poprzednie wywołanie [metody DefineTypeDef —](imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="e5be2-103">Completes the layout of fields for a class that has been defined by a prior call to [DefineTypeDef Method](imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5be2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e5be2-104">Syntax</span></span>  
  
```cpp  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,
    [in]  DWORD               dwPackSize,
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],
    [in]  ULONG               ulClassSize
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5be2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e5be2-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="e5be2-106">podczas `mdTypeDef`Token określający klasę, która ma zostać ustanowiona.</span><span class="sxs-lookup"><span data-stu-id="e5be2-106">[in] An `mdTypeDef` token that specifies the class to be laid out.</span></span>  
  
 `dwPackSize`  
 <span data-ttu-id="e5be2-107">podczas Rozmiar pakowania: 1, 2, 4, 8 lub 16 bajtów.</span><span class="sxs-lookup"><span data-stu-id="e5be2-107">[in] The packing size: 1, 2, 4, 8 or 16 bytes.</span></span> <span data-ttu-id="e5be2-108">Rozmiar pakowania to liczba bajtów między sąsiednimi polami.</span><span class="sxs-lookup"><span data-stu-id="e5be2-108">The packing size is the number of bytes between adjacent fields.</span></span>  
  
 `rFieldOffsets`  
 <span data-ttu-id="e5be2-109">podczas Tablica struktur [COR_FIELD_OFFSET](cor-field-offset-structure.md) , z których każdy określa pole klasy i przesunięcie pola w klasie.</span><span class="sxs-lookup"><span data-stu-id="e5be2-109">[in] An array of [COR_FIELD_OFFSET](cor-field-offset-structure.md) structures, each of which specifies a field of the class and the field's offset within the class.</span></span> <span data-ttu-id="e5be2-110">Przerwij tablicę za pomocą `mdTokenNil` .</span><span class="sxs-lookup"><span data-stu-id="e5be2-110">Terminate the array with `mdTokenNil`.</span></span>  
  
 `ulClassSize`  
 <span data-ttu-id="e5be2-111">podczas Rozmiar klasy w bajtach.</span><span class="sxs-lookup"><span data-stu-id="e5be2-111">[in] The size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5be2-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e5be2-112">Remarks</span></span>  
 <span data-ttu-id="e5be2-113">Klasa jest początkowo definiowana przez wywołanie metody [IMetaDataEmit::D efinetypedef](imetadataemit-definetypedef-method.md) i określenie jednego z trzech układów dla pól klasy: automatyczne, sekwencyjne lub jawne.</span><span class="sxs-lookup"><span data-stu-id="e5be2-113">The class is initially defined by calling the [IMetaDataEmit::DefineTypeDef](imetadataemit-definetypedef-method.md) method, and specifying one of three layouts for the fields of the class: automatic, sequential, or explicit.</span></span> <span data-ttu-id="e5be2-114">Zwykle należy używać automatycznego układu i pozwolić, aby środowisko uruchomieniowe było najlepszym sposobem ułożenia pól.</span><span class="sxs-lookup"><span data-stu-id="e5be2-114">Normally, you would use automatic layout and let the runtime choose the best way to lay out the fields.</span></span>  
  
 <span data-ttu-id="e5be2-115">Jednakże można chcieć, aby pola zostały określone zgodnie z rozmieszczeniem, które jest używane w kodzie niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="e5be2-115">However, you might want the fields laid out according to the arrangement that unmanaged code uses.</span></span> <span data-ttu-id="e5be2-116">W takim przypadku wybierz Układ sekwencyjny lub jawny i Wywołaj, `SetClassLayout` Aby zakończyć układ pól:</span><span class="sxs-lookup"><span data-stu-id="e5be2-116">In this case, choose either sequential or explicit layout and call `SetClassLayout` to complete the layout of the fields:</span></span>  
  
- <span data-ttu-id="e5be2-117">Układ sekwencyjny: Określ rozmiar pakowania.</span><span class="sxs-lookup"><span data-stu-id="e5be2-117">Sequential layout: Specify the packing size.</span></span> <span data-ttu-id="e5be2-118">Pole jest wyrównane do rozmiaru naturalnego lub rozmiaru pakowania, w zależności od tego, czy jest to mniejsze przesunięcie pola.</span><span class="sxs-lookup"><span data-stu-id="e5be2-118">A field is aligned according to either its natural size or the packing size, whichever results in the smaller offset of the field.</span></span> <span data-ttu-id="e5be2-119">Ustaw wartość `rFieldOffsets` i `ulClassSize` na zero.</span><span class="sxs-lookup"><span data-stu-id="e5be2-119">Set `rFieldOffsets` and `ulClassSize` to zero.</span></span>  
  
- <span data-ttu-id="e5be2-120">Układ jawny: Określ przesunięcie każdego pola lub Określ rozmiar klasy oraz rozmiar pakowania.</span><span class="sxs-lookup"><span data-stu-id="e5be2-120">Explicit layout: Either specify the offset of each field or specify the class size and the packing size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5be2-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e5be2-121">Requirements</span></span>  
 <span data-ttu-id="e5be2-122">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5be2-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5be2-123">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e5be2-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e5be2-124">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e5be2-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e5be2-125">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5be2-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5be2-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e5be2-126">See also</span></span>

- [<span data-ttu-id="e5be2-127">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e5be2-127">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="e5be2-128">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="e5be2-128">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
