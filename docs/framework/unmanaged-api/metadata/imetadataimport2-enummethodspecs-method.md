---
title: "IMetaDataImport2::EnumMethodSpecs — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2.EnumMethodSpecs
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2::EnumMethodSpecs
helpviewer_keywords:
- IMetaDataImport2::EnumMethodSpecs method [.NET Framework metadata]
- EnumMethodSpecs method [.NET Framework metadata]
ms.assetid: b3fc1e6c-bcb6-4915-baf8-7dc0a31b8724
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: db1968c73d5a1c6e0687bc86f249c70b6c21712c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimport2enummethodspecs-method"></a><span data-ttu-id="1dfdc-102">IMetaDataImport2::EnumMethodSpecs — Metoda</span><span class="sxs-lookup"><span data-stu-id="1dfdc-102">IMetaDataImport2::EnumMethodSpecs Method</span></span>
<span data-ttu-id="1dfdc-103">Pobiera moduł wyliczający dla tablicy tokenów MethodSpec skojarzone z określonym MethodDef lub MemberRef token.</span><span class="sxs-lookup"><span data-stu-id="1dfdc-103">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dfdc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1dfdc-104">Syntax</span></span>  
  
```  
HRESULT EnumMethodSpecs (  
    [in, out] HCORENUM      *phEnum,   
    [in]      mdToken       tk,  
    [out]     mdMethodSpec  rMethodSpecs[],  
    [in]      ULONG         cMax,  
    [out]     ULONG         *pcMethodSpecs  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="1dfdc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1dfdc-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="1dfdc-106">[w, out] Wskaźnik do modułu wyliczającego dla `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="1dfdc-106">[in, out] A pointer to the enumerator for `rMethodSpecs`.</span></span>  
  
 `tk`  
 <span data-ttu-id="1dfdc-107">[in] Tokenu MemberRef lub MethodDef, który reprezentuje metodę, której tokeny MethodSpec są mają zostać wyliczone.</span><span class="sxs-lookup"><span data-stu-id="1dfdc-107">[in] The MemberRef or MethodDef token that represents the method whose MethodSpec tokens are to be enumerated.</span></span> <span data-ttu-id="1dfdc-108">Jeśli wartość `tk` jest 0 (zero), będzie można wyliczyć wszystkich tokenów elementu MethodSpec w zakresie.</span><span class="sxs-lookup"><span data-stu-id="1dfdc-108">If the value of `tk` is 0 (zero), all MethodSpec tokens in the scope will be enumerated.</span></span>  
  
 `rMethodSpecs`  
 <span data-ttu-id="1dfdc-109">[out] Tablica MethodSpec do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="1dfdc-109">[out] The array of MethodSpec tokens to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="1dfdc-110">[in] Żądana maksymalna liczba tokenów do umieszczenia w `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="1dfdc-110">[in] The requested maximum number of tokens to place in `rMethodSpecs`.</span></span>  
  
 `pcMethodSpecs`  
 <span data-ttu-id="1dfdc-111">[out] Zwrócona liczba tokenów umieszczonych w `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="1dfdc-111">[out] The returned number of tokens placed in `rMethodSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1dfdc-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1dfdc-112">Return Value</span></span>  
  
|<span data-ttu-id="1dfdc-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1dfdc-113">HRESULT</span></span>|<span data-ttu-id="1dfdc-114">Opis</span><span class="sxs-lookup"><span data-stu-id="1dfdc-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="1dfdc-115">`EnumMethodSpecs`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="1dfdc-115">`EnumMethodSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="1dfdc-116">`phEnum`nie ma żadnych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="1dfdc-116">`phEnum` has no member elements.</span></span> <span data-ttu-id="1dfdc-117">W takim przypadku `pcMethodSpecs` jest równa 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="1dfdc-117">In this case, `pcMethodSpecs` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1dfdc-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1dfdc-118">Requirements</span></span>  
 <span data-ttu-id="1dfdc-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1dfdc-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1dfdc-120">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1dfdc-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1dfdc-121">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1dfdc-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1dfdc-122">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1dfdc-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dfdc-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1dfdc-123">See Also</span></span>  
 [<span data-ttu-id="1dfdc-124">IMetaDataImport2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="1dfdc-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="1dfdc-125">IMetaDataImport — interfejs</span><span class="sxs-lookup"><span data-stu-id="1dfdc-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
