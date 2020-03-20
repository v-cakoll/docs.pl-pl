---
title: IMetaDataEmit2::DefineGenericParam — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.DefineGenericParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::DefineGenericParam
helpviewer_keywords:
- IMetaDataEmit2::DefineGenericParam method [.NET Framework metadata]
- DefineGenericParam method [.NET Framework metadata]
ms.assetid: 47b2a3b6-907d-43dc-858d-1ae7dca1316a
topic_type:
- apiref
ms.openlocfilehash: 1868d13a9dbb73dbdf64e49c395bdbff02ce89d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177454"
---
# <a name="imetadataemit2definegenericparam-method"></a><span data-ttu-id="2ce45-102">IMetaDataEmit2::DefineGenericParam — Metoda</span><span class="sxs-lookup"><span data-stu-id="2ce45-102">IMetaDataEmit2::DefineGenericParam Method</span></span>
<span data-ttu-id="2ce45-103">Tworzy definicję parametru typu ogólnego i pobiera token do tego parametru typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="2ce45-103">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ce45-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2ce45-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineGenericParam (
    [in]  mdToken         tk,
    [in]  ULONG           ulParamSeq,
    [in]  DWORD           dwParamFlags,
    [in]  LPCWSTR         szname,
    [in]  DWORD           reserved,
    [in]  mdToken         rtkConstraints[],
    [out] mdGenericParam  *pgp  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ce45-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2ce45-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="2ce45-106">[w] Lub `mdTypeDef` `mdMethodDef` token, który reprezentuje metodę lub konstruktora, dla którego można zdefiniować parametr ogólny.</span><span class="sxs-lookup"><span data-stu-id="2ce45-106">[in] An `mdTypeDef` or `mdMethodDef` token that represents the method or constructor for which to define a generic parameter.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="2ce45-107">[w] Indeks parametru ogólnego.</span><span class="sxs-lookup"><span data-stu-id="2ce45-107">[in] The index of the generic parameter.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="2ce45-108">[w] Wartość wyliczania [CorGenericParamAttr,](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) która opisuje typ parametru ogólnego.</span><span class="sxs-lookup"><span data-stu-id="2ce45-108">[in] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szname`  
 <span data-ttu-id="2ce45-109">[w] Nazwa parametru.</span><span class="sxs-lookup"><span data-stu-id="2ce45-109">[in] The name of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="2ce45-110">[w] Ten parametr jest zarezerwowany dla przyszłej rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="2ce45-110">[in] This parameter is reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="2ce45-111">[w] Tablica typu zakończona z zerowym o zerowym zakończeniem.</span><span class="sxs-lookup"><span data-stu-id="2ce45-111">[in] A zero-terminated array of type constraints.</span></span> <span data-ttu-id="2ce45-112">Elementy członkowskie tablicy `mdTypeRef`muszą `mdTypeSpec` być tokenem `mdTypeDef`, lub metadanych.</span><span class="sxs-lookup"><span data-stu-id="2ce45-112">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
 `pgp`  
 <span data-ttu-id="2ce45-113">[na zewnątrz] Token reprezentujący parametr ogólny.</span><span class="sxs-lookup"><span data-stu-id="2ce45-113">[out] A token that represents the generic parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ce45-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2ce45-114">Requirements</span></span>  
 <span data-ttu-id="2ce45-115">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ce45-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ce45-116">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="2ce45-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2ce45-117">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2ce45-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2ce45-118">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ce45-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ce45-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2ce45-119">See also</span></span>

- [<span data-ttu-id="2ce45-120">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="2ce45-120">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="2ce45-121">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2ce45-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
