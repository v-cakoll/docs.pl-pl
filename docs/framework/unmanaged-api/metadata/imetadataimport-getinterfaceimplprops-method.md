---
title: IMetaDataImport::GetInterfaceImplProps — Metoda
ms.date: 02/25/2019
api_name:
- IMetaDataImport.GetInterfaceImplProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetInterfaceImplProps
helpviewer_keywords:
- IMetaDataImport::GetInterfaceImplProps method [.NET Framework metadata]
- GetInterfaceImpProps method [.NET Framework metadata]
ms.assetid: be3f5985-b1e4-4036-8602-c16e8508d4af
topic_type:
- apiref
ms.openlocfilehash: 1c9d9647084aa729817eeeb17ee3f5cd320c0d29
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491251"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a><span data-ttu-id="d2cae-102">IMetaDataImport::GetInterfaceImplProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="d2cae-102">IMetaDataImport::GetInterfaceImplProps Method</span></span>
<span data-ttu-id="d2cae-103">Pobiera wskaźnik do tokenów metadanych <xref:System.Type> , który implementuje określoną metodę i dla interfejsu, który deklaruje tę metodę.</span><span class="sxs-lookup"><span data-stu-id="d2cae-103">Gets a pointer to the metadata tokens for the <xref:System.Type> that implements the specified method, and for the interface that declares that method.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="d2cae-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d2cae-104">Syntax</span></span>  
  
```cpp  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2cae-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d2cae-105">Parameters</span></span>  
 `iiImpl`  
 <span data-ttu-id="d2cae-106">podczas Token metadanych reprezentujący metodę zwracającą tokeny klasy i interfejsu dla.</span><span class="sxs-lookup"><span data-stu-id="d2cae-106">[in] The metadata token representing the method to return the class and interface tokens for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="d2cae-107">określoną Token metadanych reprezentujący klasę implementującą metodę.</span><span class="sxs-lookup"><span data-stu-id="d2cae-107">[out] The metadata token representing the class that implements the method.</span></span>  
  
 `ptkIface`  
 <span data-ttu-id="d2cae-108">określoną Token metadanych reprezentujący interfejs, który definiuje zaimplementowaną metodę.</span><span class="sxs-lookup"><span data-stu-id="d2cae-108">[out] The metadata token representing the interface that defines the implemented method.</span></span>  

## <a name="remarks"></a><span data-ttu-id="d2cae-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d2cae-109">Remarks</span></span>

 <span data-ttu-id="d2cae-110">Uzyskujesz wartość dla `iImpl` przez wywołanie metody [EnumInterfaceImpls —](imetadataimport-enuminterfaceimpls-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d2cae-110">You obtain the value for `iImpl` by calling the [EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md) method.</span></span>

 <span data-ttu-id="d2cae-111">Załóżmy na przykład, że Klasa ma `mdTypeDef` wartość tokenu 0x02000007 i implementuje trzy interfejsy, których typy mają tokeny:</span><span class="sxs-lookup"><span data-stu-id="d2cae-111">For example, suppose that a class has an `mdTypeDef` token value of 0x02000007 and that it implements three interfaces whose types have tokens:</span></span>

- <span data-ttu-id="d2cae-112">0x02000003 (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="d2cae-112">0x02000003 (TypeDef)</span></span>
- <span data-ttu-id="d2cae-113">0x0100000A (TypeRef)</span><span class="sxs-lookup"><span data-stu-id="d2cae-113">0x0100000A (TypeRef)</span></span>
- <span data-ttu-id="d2cae-114">0x0200001C (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="d2cae-114">0x0200001C (TypeDef)</span></span>

<span data-ttu-id="d2cae-115">Koncepcyjnie te informacje są przechowywane w tabeli implementacji interfejsu jako:</span><span class="sxs-lookup"><span data-stu-id="d2cae-115">Conceptually, this information is stored into an interface implementation table as:</span></span>

| <span data-ttu-id="d2cae-116">Numer wiersza</span><span class="sxs-lookup"><span data-stu-id="d2cae-116">Row number</span></span> | <span data-ttu-id="d2cae-117">Token klasy</span><span class="sxs-lookup"><span data-stu-id="d2cae-117">Class token</span></span> | <span data-ttu-id="d2cae-118">Token interfejsu</span><span class="sxs-lookup"><span data-stu-id="d2cae-118">Interface token</span></span> |
|------------|-------------|-----------------|
| <span data-ttu-id="d2cae-119">4</span><span class="sxs-lookup"><span data-stu-id="d2cae-119">4</span></span>          |             |                 |
| <span data-ttu-id="d2cae-120">5</span><span class="sxs-lookup"><span data-stu-id="d2cae-120">5</span></span>          | <span data-ttu-id="d2cae-121">02000007</span><span class="sxs-lookup"><span data-stu-id="d2cae-121">02000007</span></span>    | <span data-ttu-id="d2cae-122">02000003</span><span class="sxs-lookup"><span data-stu-id="d2cae-122">02000003</span></span>        |
| <span data-ttu-id="d2cae-123">6</span><span class="sxs-lookup"><span data-stu-id="d2cae-123">6</span></span>          | <span data-ttu-id="d2cae-124">02000007</span><span class="sxs-lookup"><span data-stu-id="d2cae-124">02000007</span></span>    | <span data-ttu-id="d2cae-125">0100000A</span><span class="sxs-lookup"><span data-stu-id="d2cae-125">0100000A</span></span>        |
| <span data-ttu-id="d2cae-126">7</span><span class="sxs-lookup"><span data-stu-id="d2cae-126">7</span></span>          |             |                 |
| <span data-ttu-id="d2cae-127">8</span><span class="sxs-lookup"><span data-stu-id="d2cae-127">8</span></span>          | <span data-ttu-id="d2cae-128">02000007</span><span class="sxs-lookup"><span data-stu-id="d2cae-128">02000007</span></span>    | <span data-ttu-id="d2cae-129">0200001C</span><span class="sxs-lookup"><span data-stu-id="d2cae-129">0200001C</span></span>        |

<span data-ttu-id="d2cae-130">Odwołaj, token jest wartością 4-bajtową:</span><span class="sxs-lookup"><span data-stu-id="d2cae-130">Recall, the token is a 4-byte value:</span></span>

- <span data-ttu-id="d2cae-131">Dolne 3 bajty mają numer wiersza lub identyfikator RID.</span><span class="sxs-lookup"><span data-stu-id="d2cae-131">The lower 3 bytes hold the row number, or RID.</span></span>
- <span data-ttu-id="d2cae-132">Górny bajt zawiera typ tokenu — 0x09 dla `mdtInterfaceImpl` .</span><span class="sxs-lookup"><span data-stu-id="d2cae-132">The upper byte holds the token type – 0x09 for `mdtInterfaceImpl`.</span></span>

<span data-ttu-id="d2cae-133">`GetInterfaceImplProps`zwraca informacje przechowywane w wierszu, którego token jest udostępniany w `iImpl` argumencie.</span><span class="sxs-lookup"><span data-stu-id="d2cae-133">`GetInterfaceImplProps` returns the information held in the row whose token you provide in the `iImpl` argument.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="d2cae-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d2cae-134">Requirements</span></span>  
 <span data-ttu-id="d2cae-135">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2cae-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2cae-136">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d2cae-136">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d2cae-137">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d2cae-137">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d2cae-138">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2cae-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2cae-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d2cae-139">See also</span></span>

- [<span data-ttu-id="d2cae-140">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d2cae-140">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="d2cae-141">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d2cae-141">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
