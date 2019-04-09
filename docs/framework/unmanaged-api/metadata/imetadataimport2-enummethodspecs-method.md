---
title: IMetaDataImport2::EnumMethodSpecs — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumMethodSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumMethodSpecs
helpviewer_keywords:
- IMetaDataImport2::EnumMethodSpecs method [.NET Framework metadata]
- EnumMethodSpecs method [.NET Framework metadata]
ms.assetid: b3fc1e6c-bcb6-4915-baf8-7dc0a31b8724
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a3641fcda33a497293dbf87b419c8606847dc296
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130952"
---
# <a name="imetadataimport2enummethodspecs-method"></a><span data-ttu-id="d942f-102">IMetaDataImport2::EnumMethodSpecs — Metoda</span><span class="sxs-lookup"><span data-stu-id="d942f-102">IMetaDataImport2::EnumMethodSpecs Method</span></span>
<span data-ttu-id="d942f-103">Pobiera moduł wyliczający dla tablicy tokenów MethodSpec skojarzone z określonym MethodDef lub MemberRef tokenu.</span><span class="sxs-lookup"><span data-stu-id="d942f-103">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d942f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d942f-104">Syntax</span></span>  
  
```  
HRESULT EnumMethodSpecs (  
    [in, out] HCORENUM      *phEnum,   
    [in]      mdToken       tk,  
    [out]     mdMethodSpec  rMethodSpecs[],  
    [in]      ULONG         cMax,  
    [out]     ULONG         *pcMethodSpecs  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="d942f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d942f-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="d942f-106">[out w] Wskaźnik do modułu wyliczającego dla `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="d942f-106">[in, out] A pointer to the enumerator for `rMethodSpecs`.</span></span>  
  
 `tk`  
 <span data-ttu-id="d942f-107">[in] Token MemberRef lub MethodDef, który reprezentuje metodę, w których tokeny MethodSpec są do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="d942f-107">[in] The MemberRef or MethodDef token that represents the method whose MethodSpec tokens are to be enumerated.</span></span> <span data-ttu-id="d942f-108">Jeśli wartość `tk` wynosi 0 (zero), będzie można wyliczyć wszystkie tokeny MethodSpec w zakresie.</span><span class="sxs-lookup"><span data-stu-id="d942f-108">If the value of `tk` is 0 (zero), all MethodSpec tokens in the scope will be enumerated.</span></span>  
  
 `rMethodSpecs`  
 <span data-ttu-id="d942f-109">[out] Tablica MethodSpec do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="d942f-109">[out] The array of MethodSpec tokens to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="d942f-110">[in] Żądana maksymalna liczba tokenów do umieszczenia w `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="d942f-110">[in] The requested maximum number of tokens to place in `rMethodSpecs`.</span></span>  
  
 `pcMethodSpecs`  
 <span data-ttu-id="d942f-111">[out] Zwrócona liczba tokenów umieszczone w `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="d942f-111">[out] The returned number of tokens placed in `rMethodSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d942f-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d942f-112">Return Value</span></span>  
  
|<span data-ttu-id="d942f-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d942f-113">HRESULT</span></span>|<span data-ttu-id="d942f-114">Opis</span><span class="sxs-lookup"><span data-stu-id="d942f-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodSpecs` <span data-ttu-id="d942f-115">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="d942f-115">returned successfully.</span></span>|  
|`S_FALSE`|`phEnum` <span data-ttu-id="d942f-116">nie ma żadnych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="d942f-116">has no member elements.</span></span> <span data-ttu-id="d942f-117">W tym przypadku `pcMethodSpecs` jest ustawiona na 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="d942f-117">In this case, `pcMethodSpecs` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d942f-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d942f-118">Requirements</span></span>  
 <span data-ttu-id="d942f-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d942f-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d942f-120">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="d942f-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d942f-121">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d942f-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="d942f-122">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="d942f-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d942f-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d942f-123">See also</span></span>

- [<span data-ttu-id="d942f-124">IMetaDataImport2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d942f-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="d942f-125">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d942f-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
