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
ms.openlocfilehash: e4401ea8a70e7ace8d8efc5e0a6d29f6db51b3df
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503817"
---
# <a name="imetadataemit2definegenericparam-method"></a><span data-ttu-id="e7f2a-102">IMetaDataEmit2::DefineGenericParam — Metoda</span><span class="sxs-lookup"><span data-stu-id="e7f2a-102">IMetaDataEmit2::DefineGenericParam Method</span></span>
<span data-ttu-id="e7f2a-103">Tworzy definicję parametru typu ogólnego i pobiera token do tego parametru typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="e7f2a-103">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7f2a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e7f2a-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="e7f2a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e7f2a-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="e7f2a-106">podczas `mdTypeDef`Token lub `mdMethodDef` reprezentujący metodę lub konstruktora, dla którego ma zostać zdefiniowany parametr generyczny.</span><span class="sxs-lookup"><span data-stu-id="e7f2a-106">[in] An `mdTypeDef` or `mdMethodDef` token that represents the method or constructor for which to define a generic parameter.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="e7f2a-107">podczas Indeks parametru generycznego.</span><span class="sxs-lookup"><span data-stu-id="e7f2a-107">[in] The index of the generic parameter.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="e7f2a-108">podczas Wartość wyliczenia [CorGenericParamAttr —](corgenericparamattr-enumeration.md) opisująca typ parametru generycznego.</span><span class="sxs-lookup"><span data-stu-id="e7f2a-108">[in] A value of the [CorGenericParamAttr](corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szname`  
 <span data-ttu-id="e7f2a-109">podczas Nazwa parametru.</span><span class="sxs-lookup"><span data-stu-id="e7f2a-109">[in] The name of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="e7f2a-110">podczas Ten parametr jest zarezerwowany do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="e7f2a-110">[in] This parameter is reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="e7f2a-111">podczas Tablica zakończona zerem z ograniczeniami typu.</span><span class="sxs-lookup"><span data-stu-id="e7f2a-111">[in] A zero-terminated array of type constraints.</span></span> <span data-ttu-id="e7f2a-112">Elementy członkowskie tablicy muszą być `mdTypeDef` `mdTypeRef` `mdTypeSpec` tokenami, lub.</span><span class="sxs-lookup"><span data-stu-id="e7f2a-112">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
 `pgp`  
 <span data-ttu-id="e7f2a-113">określoną Token, który reprezentuje parametr generyczny.</span><span class="sxs-lookup"><span data-stu-id="e7f2a-113">[out] A token that represents the generic parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7f2a-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e7f2a-114">Requirements</span></span>  
 <span data-ttu-id="e7f2a-115">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7f2a-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7f2a-116">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e7f2a-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e7f2a-117">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e7f2a-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e7f2a-118">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7f2a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7f2a-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e7f2a-119">See also</span></span>

- [<span data-ttu-id="e7f2a-120">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="e7f2a-120">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="e7f2a-121">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e7f2a-121">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
