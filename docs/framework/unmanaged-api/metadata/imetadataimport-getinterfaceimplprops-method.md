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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cb38c61e8dbd29a0ff87165b5daf49e733b34047
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466547"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a><span data-ttu-id="db056-102">IMetaDataImport::GetInterfaceImplProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="db056-102">IMetaDataImport::GetInterfaceImplProps Method</span></span>
<span data-ttu-id="db056-103">Pobiera wskaźnik do tokenów metadanych dla <xref:System.Type> implementującej określonej metody, a dla interfejsu, który deklaruje tej metody.</span><span class="sxs-lookup"><span data-stu-id="db056-103">Gets a pointer to the metadata tokens for the <xref:System.Type> that implements the specified method, and for the interface that declares that method.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="db056-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="db056-104">Syntax</span></span>  
  
```  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db056-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="db056-105">Parameters</span></span>  
 `iiImpl`  
 <span data-ttu-id="db056-106">[in] Token metadanych reprezentujący metodę do zwrócenia klas i interfejsu tokeny zabezpieczające.</span><span class="sxs-lookup"><span data-stu-id="db056-106">[in] The metadata token representing the method to return the class and interface tokens for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="db056-107">[out] Klasa, która implementuje metody reprezentująca token metadanych.</span><span class="sxs-lookup"><span data-stu-id="db056-107">[out] The metadata token representing the class that implements the method.</span></span>  
  
 `ptkIface`  
 <span data-ttu-id="db056-108">[out] Interfejs, który definiuje zaimplementowano metody reprezentująca token metadanych.</span><span class="sxs-lookup"><span data-stu-id="db056-108">[out] The metadata token representing the interface that defines the implemented method.</span></span>  

## <a name="remarks"></a><span data-ttu-id="db056-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="db056-109">Remarks</span></span>

 <span data-ttu-id="db056-110">Uzyskaj wartość `iImpl` przez wywołanie metody [enuminterfaceimpls —](imetadataimport-enuminterfaceimpls-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="db056-110">You obtain the value for `iImpl` by calling the [EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md) method.</span></span>
 
 <span data-ttu-id="db056-111">Na przykład załóżmy, że klasa ma `mdTypeDef` token wartość 0x02000007 i implementuje trzy interfejsy, których typy mają tokenów:</span><span class="sxs-lookup"><span data-stu-id="db056-111">For example, suppose that a class has an `mdTypeDef` token value of 0x02000007 and that it implements three interfaces whose types have tokens:</span></span> 

- <span data-ttu-id="db056-112">0x02000003 (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="db056-112">0x02000003 (TypeDef)</span></span>
- <span data-ttu-id="db056-113">0x0100000A (TypeRef)</span><span class="sxs-lookup"><span data-stu-id="db056-113">0x0100000A (TypeRef)</span></span>
- <span data-ttu-id="db056-114">0x0200001C (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="db056-114">0x0200001C (TypeDef)</span></span>

<span data-ttu-id="db056-115">Koncepcyjnym te informacje są przechowywane w tabeli implementacji interfejsu jako:</span><span class="sxs-lookup"><span data-stu-id="db056-115">Conceptually, this information is stored into an interface implementation table as:</span></span>

| <span data-ttu-id="db056-116">Numer wiersza</span><span class="sxs-lookup"><span data-stu-id="db056-116">Row number</span></span> | <span data-ttu-id="db056-117">Klasa tokenu</span><span class="sxs-lookup"><span data-stu-id="db056-117">Class token</span></span> | <span data-ttu-id="db056-118">Token interfejsu</span><span class="sxs-lookup"><span data-stu-id="db056-118">Interface token</span></span> |
|------------|-------------|-----------------|
| <span data-ttu-id="db056-119">4</span><span class="sxs-lookup"><span data-stu-id="db056-119">4</span></span>          |             |                 |
| <span data-ttu-id="db056-120">5</span><span class="sxs-lookup"><span data-stu-id="db056-120">5</span></span>          | <span data-ttu-id="db056-121">02000007</span><span class="sxs-lookup"><span data-stu-id="db056-121">02000007</span></span>    | <span data-ttu-id="db056-122">02000003</span><span class="sxs-lookup"><span data-stu-id="db056-122">02000003</span></span>        |
| <span data-ttu-id="db056-123">6</span><span class="sxs-lookup"><span data-stu-id="db056-123">6</span></span>          | <span data-ttu-id="db056-124">02000007</span><span class="sxs-lookup"><span data-stu-id="db056-124">02000007</span></span>    | <span data-ttu-id="db056-125">0100000A</span><span class="sxs-lookup"><span data-stu-id="db056-125">0100000A</span></span>        |
| <span data-ttu-id="db056-126">7</span><span class="sxs-lookup"><span data-stu-id="db056-126">7</span></span>          |             |                 |
| <span data-ttu-id="db056-127">8</span><span class="sxs-lookup"><span data-stu-id="db056-127">8</span></span>          | <span data-ttu-id="db056-128">02000007</span><span class="sxs-lookup"><span data-stu-id="db056-128">02000007</span></span>    | <span data-ttu-id="db056-129">0200001C</span><span class="sxs-lookup"><span data-stu-id="db056-129">0200001C</span></span>        |

<span data-ttu-id="db056-130">Pamiętasz, że token jest 4-bajtowych wartości:</span><span class="sxs-lookup"><span data-stu-id="db056-130">Recall, the token is a 4-byte value:</span></span>

- <span data-ttu-id="db056-131">Niższe 3 bajtów hold numerem wiersza lub identyfikatorów RID.</span><span class="sxs-lookup"><span data-stu-id="db056-131">The lower 3 bytes hold the row number, or RID.</span></span>
- <span data-ttu-id="db056-132">Górny bajtów zawiera typ tokenu — 0x09 `mdtInterfaceImpl`.</span><span class="sxs-lookup"><span data-stu-id="db056-132">The upper byte holds the token type – 0x09 for `mdtInterfaceImpl`.</span></span>

<span data-ttu-id="db056-133">`GetInterfaceImplProps` Zwraca informacje przechowywane w wierszu, którego token podane `iImpl` argumentu.</span><span class="sxs-lookup"><span data-stu-id="db056-133">`GetInterfaceImplProps` returns the information held in the row whose token you provide in the `iImpl` argument.</span></span> 
  
## <a name="requirements"></a><span data-ttu-id="db056-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="db056-134">Requirements</span></span>  
 <span data-ttu-id="db056-135">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db056-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db056-136">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="db056-136">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="db056-137">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="db056-137">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="db056-138">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db056-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db056-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="db056-139">See also</span></span>
- [<span data-ttu-id="db056-140">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="db056-140">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="db056-141">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="db056-141">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
