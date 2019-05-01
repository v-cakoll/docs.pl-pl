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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049846"
---
# <a name="imetadataimport2enummethodspecs-method"></a><span data-ttu-id="51825-102">IMetaDataImport2::EnumMethodSpecs — Metoda</span><span class="sxs-lookup"><span data-stu-id="51825-102">IMetaDataImport2::EnumMethodSpecs Method</span></span>
<span data-ttu-id="51825-103">Pobiera moduł wyliczający dla tablicy tokenów MethodSpec skojarzone z określonym MethodDef lub MemberRef tokenu.</span><span class="sxs-lookup"><span data-stu-id="51825-103">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51825-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="51825-104">Syntax</span></span>  
  
```  
HRESULT EnumMethodSpecs (  
    [in, out] HCORENUM      *phEnum,   
    [in]      mdToken       tk,  
    [out]     mdMethodSpec  rMethodSpecs[],  
    [in]      ULONG         cMax,  
    [out]     ULONG         *pcMethodSpecs  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="51825-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="51825-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="51825-106">[out w] Wskaźnik do modułu wyliczającego dla `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="51825-106">[in, out] A pointer to the enumerator for `rMethodSpecs`.</span></span>  
  
 `tk`  
 <span data-ttu-id="51825-107">[in] Token MemberRef lub MethodDef, który reprezentuje metodę, w których tokeny MethodSpec są do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="51825-107">[in] The MemberRef or MethodDef token that represents the method whose MethodSpec tokens are to be enumerated.</span></span> <span data-ttu-id="51825-108">Jeśli wartość `tk` wynosi 0 (zero), będzie można wyliczyć wszystkie tokeny MethodSpec w zakresie.</span><span class="sxs-lookup"><span data-stu-id="51825-108">If the value of `tk` is 0 (zero), all MethodSpec tokens in the scope will be enumerated.</span></span>  
  
 `rMethodSpecs`  
 <span data-ttu-id="51825-109">[out] Tablica MethodSpec do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="51825-109">[out] The array of MethodSpec tokens to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="51825-110">[in] Żądana maksymalna liczba tokenów do umieszczenia w `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="51825-110">[in] The requested maximum number of tokens to place in `rMethodSpecs`.</span></span>  
  
 `pcMethodSpecs`  
 <span data-ttu-id="51825-111">[out] Zwrócona liczba tokenów umieszczone w `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="51825-111">[out] The returned number of tokens placed in `rMethodSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="51825-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="51825-112">Return Value</span></span>  
  
|<span data-ttu-id="51825-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="51825-113">HRESULT</span></span>|<span data-ttu-id="51825-114">Opis</span><span class="sxs-lookup"><span data-stu-id="51825-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="51825-115">`EnumMethodSpecs` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="51825-115">`EnumMethodSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="51825-116">`phEnum` nie ma żadnych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="51825-116">`phEnum` has no member elements.</span></span> <span data-ttu-id="51825-117">W tym przypadku `pcMethodSpecs` jest ustawiona na 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="51825-117">In this case, `pcMethodSpecs` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="51825-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="51825-118">Requirements</span></span>  
 <span data-ttu-id="51825-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51825-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51825-120">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="51825-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="51825-121">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="51825-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="51825-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51825-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51825-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="51825-123">See also</span></span>

- [<span data-ttu-id="51825-124">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="51825-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="51825-125">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="51825-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
