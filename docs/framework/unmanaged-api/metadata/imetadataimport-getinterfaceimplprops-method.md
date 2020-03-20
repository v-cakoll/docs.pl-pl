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
ms.openlocfilehash: 4b8ddf7fec12d175f030c0ea0ed982c6fb334aee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175385"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a><span data-ttu-id="17e89-102">IMetaDataImport::GetInterfaceImplProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="17e89-102">IMetaDataImport::GetInterfaceImplProps Method</span></span>
<span data-ttu-id="17e89-103">Pobiera wskaźnik do tokenów metadanych dla <xref:System.Type> tego implementuje określoną metodę i dla interfejsu, który deklaruje tę metodę.</span><span class="sxs-lookup"><span data-stu-id="17e89-103">Gets a pointer to the metadata tokens for the <xref:System.Type> that implements the specified method, and for the interface that declares that method.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="17e89-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="17e89-104">Syntax</span></span>  
  
```cpp  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17e89-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="17e89-105">Parameters</span></span>  
 `iiImpl`  
 <span data-ttu-id="17e89-106">[w] Token metadanych reprezentujący metodę zwracania tokenów klasy i interfejsu.</span><span class="sxs-lookup"><span data-stu-id="17e89-106">[in] The metadata token representing the method to return the class and interface tokens for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="17e89-107">[na zewnątrz] Token metadanych reprezentujący klasę, która implementuje metodę.</span><span class="sxs-lookup"><span data-stu-id="17e89-107">[out] The metadata token representing the class that implements the method.</span></span>  
  
 `ptkIface`  
 <span data-ttu-id="17e89-108">[na zewnątrz] Token metadanych reprezentujący interfejs, który definiuje zaimplementowana metoda.</span><span class="sxs-lookup"><span data-stu-id="17e89-108">[out] The metadata token representing the interface that defines the implemented method.</span></span>  

## <a name="remarks"></a><span data-ttu-id="17e89-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="17e89-109">Remarks</span></span>

 <span data-ttu-id="17e89-110">Można uzyskać wartość `iImpl` dla wywołując [EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="17e89-110">You obtain the value for `iImpl` by calling the [EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md) method.</span></span>

 <span data-ttu-id="17e89-111">Załóżmy na przykład, `mdTypeDef` że klasa ma wartość tokenu 0x02000007 i implementuje trzy interfejsy, których typy mają tokeny:</span><span class="sxs-lookup"><span data-stu-id="17e89-111">For example, suppose that a class has an `mdTypeDef` token value of 0x02000007 and that it implements three interfaces whose types have tokens:</span></span>

- <span data-ttu-id="17e89-112">0x02000003 (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="17e89-112">0x02000003 (TypeDef)</span></span>
- <span data-ttu-id="17e89-113">0x0100000A (TypeRef)</span><span class="sxs-lookup"><span data-stu-id="17e89-113">0x0100000A (TypeRef)</span></span>
- <span data-ttu-id="17e89-114">0x0200001C (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="17e89-114">0x0200001C (TypeDef)</span></span>

<span data-ttu-id="17e89-115">Koncepcyjnie te informacje są przechowywane w tabeli implementacji interfejsu jako:</span><span class="sxs-lookup"><span data-stu-id="17e89-115">Conceptually, this information is stored into an interface implementation table as:</span></span>

| <span data-ttu-id="17e89-116">Numer wiersza</span><span class="sxs-lookup"><span data-stu-id="17e89-116">Row number</span></span> | <span data-ttu-id="17e89-117">Token klasy</span><span class="sxs-lookup"><span data-stu-id="17e89-117">Class token</span></span> | <span data-ttu-id="17e89-118">Token interfejsu</span><span class="sxs-lookup"><span data-stu-id="17e89-118">Interface token</span></span> |
|------------|-------------|-----------------|
| <span data-ttu-id="17e89-119">4</span><span class="sxs-lookup"><span data-stu-id="17e89-119">4</span></span>          |             |                 |
| <span data-ttu-id="17e89-120">5</span><span class="sxs-lookup"><span data-stu-id="17e89-120">5</span></span>          | <span data-ttu-id="17e89-121">02000007</span><span class="sxs-lookup"><span data-stu-id="17e89-121">02000007</span></span>    | <span data-ttu-id="17e89-122">02000003</span><span class="sxs-lookup"><span data-stu-id="17e89-122">02000003</span></span>        |
| <span data-ttu-id="17e89-123">6</span><span class="sxs-lookup"><span data-stu-id="17e89-123">6</span></span>          | <span data-ttu-id="17e89-124">02000007</span><span class="sxs-lookup"><span data-stu-id="17e89-124">02000007</span></span>    | <span data-ttu-id="17e89-125">0100000A</span><span class="sxs-lookup"><span data-stu-id="17e89-125">0100000A</span></span>        |
| <span data-ttu-id="17e89-126">7</span><span class="sxs-lookup"><span data-stu-id="17e89-126">7</span></span>          |             |                 |
| <span data-ttu-id="17e89-127">8</span><span class="sxs-lookup"><span data-stu-id="17e89-127">8</span></span>          | <span data-ttu-id="17e89-128">02000007</span><span class="sxs-lookup"><span data-stu-id="17e89-128">02000007</span></span>    | <span data-ttu-id="17e89-129">0200001C</span><span class="sxs-lookup"><span data-stu-id="17e89-129">0200001C</span></span>        |

<span data-ttu-id="17e89-130">Przypomnijmy, token jest wartością 4-bajtową:</span><span class="sxs-lookup"><span data-stu-id="17e89-130">Recall, the token is a 4-byte value:</span></span>

- <span data-ttu-id="17e89-131">Dolne 3 bajty przytrzymują numer wiersza lub RID.</span><span class="sxs-lookup"><span data-stu-id="17e89-131">The lower 3 bytes hold the row number, or RID.</span></span>
- <span data-ttu-id="17e89-132">Górny bajt zawiera typ tokenu — `mdtInterfaceImpl`0x09 dla .</span><span class="sxs-lookup"><span data-stu-id="17e89-132">The upper byte holds the token type – 0x09 for `mdtInterfaceImpl`.</span></span>

<span data-ttu-id="17e89-133">`GetInterfaceImplProps`zwraca informacje przechowywane w wierszu, którego `iImpl` token można podać w argumie.</span><span class="sxs-lookup"><span data-stu-id="17e89-133">`GetInterfaceImplProps` returns the information held in the row whose token you provide in the `iImpl` argument.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="17e89-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="17e89-134">Requirements</span></span>  
 <span data-ttu-id="17e89-135">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17e89-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17e89-136">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="17e89-136">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="17e89-137">**Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="17e89-137">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="17e89-138">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17e89-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17e89-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="17e89-139">See also</span></span>

- [<span data-ttu-id="17e89-140">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="17e89-140">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="17e89-141">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="17e89-141">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
