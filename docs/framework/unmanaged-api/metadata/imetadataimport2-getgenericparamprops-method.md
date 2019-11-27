---
title: IMetaDataImport2::GetGenericParamProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetGenericParamProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamProps method [.NET Framework metadata]
- GetGenericParamProps method [.NET Framework metadata]
ms.assetid: dbb21e67-712b-49e7-a27c-a1e73ffd46c5
topic_type:
- apiref
ms.openlocfilehash: a8c5dd263401002deaee3d21f1e41b41a29faec2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427299"
---
# <a name="imetadataimport2getgenericparamprops-method"></a><span data-ttu-id="15c8f-102">IMetaDataImport2::GetGenericParamProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="15c8f-102">IMetaDataImport2::GetGenericParamProps Method</span></span>
<span data-ttu-id="15c8f-103">Pobiera metadane skojarzone z parametrem ogólnym reprezentowanym przez określony token.</span><span class="sxs-lookup"><span data-stu-id="15c8f-103">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15c8f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="15c8f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGenericParamProps (  
   [in]  mdGenericParam  gp,  
   [out] ULONG           *pulParamSeq,  
   [out] DWORD           *pdwParamFlags,  
   [out] mdToken         *ptOwner,  
   [out] DWORD           *reserved,  
   [out] LPWSTR          wzName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15c8f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="15c8f-105">Parameters</span></span>  
 `gp`  
 <span data-ttu-id="15c8f-106">podczas Token reprezentujący parametr generyczny, dla którego mają być zwracane metadane.</span><span class="sxs-lookup"><span data-stu-id="15c8f-106">[in] The token that represents the generic parameter for which to return metadata.</span></span>  
  
 `pulParamSeq`  
 <span data-ttu-id="15c8f-107">określoną Pozycja porządkowa parametru `Type` w konstruktorze nadrzędnym lub metodzie.</span><span class="sxs-lookup"><span data-stu-id="15c8f-107">[out] The ordinal position of the `Type` parameter in the parent constructor or method.</span></span>  
  
 `pdwParamFlags`  
 <span data-ttu-id="15c8f-108">określoną Wartość wyliczenia [CorGenericParamAttr —](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) opisująca `Type` parametru generycznego.</span><span class="sxs-lookup"><span data-stu-id="15c8f-108">[out] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the `Type` for the generic parameter.</span></span>  
  
 `ptOwner`  
 <span data-ttu-id="15c8f-109">określoną Token TypeDef lub MethodDef, który reprezentuje właściciela parametru.</span><span class="sxs-lookup"><span data-stu-id="15c8f-109">[out] A TypeDef or MethodDef token that represents the owner of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="15c8f-110">określoną Zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="15c8f-110">[out] Reserved for future extensibility.</span></span>  
  
 `wzName`  
 <span data-ttu-id="15c8f-111">określoną Nazwa parametru generycznego.</span><span class="sxs-lookup"><span data-stu-id="15c8f-111">[out] The name of the generic parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="15c8f-112">podczas Rozmiar buforu `wzName`.</span><span class="sxs-lookup"><span data-stu-id="15c8f-112">[in] The size of the `wzName` buffer.</span></span>  
  
 `pchName`  
 <span data-ttu-id="15c8f-113">określoną Zwrócony rozmiar nazwy w znaki dwubajtowe.</span><span class="sxs-lookup"><span data-stu-id="15c8f-113">[out] The returned size of the name, in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15c8f-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="15c8f-114">Requirements</span></span>  
 <span data-ttu-id="15c8f-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15c8f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15c8f-116">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="15c8f-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="15c8f-117">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="15c8f-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="15c8f-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15c8f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15c8f-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="15c8f-119">See also</span></span>

- [<span data-ttu-id="15c8f-120">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="15c8f-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="15c8f-121">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="15c8f-121">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
