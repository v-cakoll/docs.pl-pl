---
title: "IMetaDataImport::EnumParams — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumParams
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumParams
helpviewer_keywords:
- IMetaDataImport::EnumParams method [.NET Framework metadata]
- EnumParams method [.NET Framework metadata]
ms.assetid: 52118dc9-fe6e-4b39-aa48-c3cc3ea4214d
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 51544a44ed4bae25d4214e25c717769a8446f0f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenumparams-method"></a><span data-ttu-id="c90a4-102">IMetaDataImport::EnumParams — Metoda</span><span class="sxs-lookup"><span data-stu-id="c90a4-102">IMetaDataImport::EnumParams Method</span></span>
<span data-ttu-id="c90a4-103">Wylicza tokenów ParamDef reprezentujący parametry metody odwołuje się określony token MethodDef.</span><span class="sxs-lookup"><span data-stu-id="c90a4-103">Enumerates ParamDef tokens representing the parameters of the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c90a4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c90a4-104">Syntax</span></span>  
  
```  
HRESULT EnumParams (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,  
   [out] mdParamDef      rParams[],  
   [in]  ULONG           cMax,  
   [out] ULONG          *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c90a4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c90a4-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="c90a4-106">[w, out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="c90a4-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="c90a4-107">Musi to być wartość NULL dla pierwsze wywołanie tej metody.</span><span class="sxs-lookup"><span data-stu-id="c90a4-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="c90a4-108">[in] Token MethodDef reprezentujący metody z parametrami wyliczyć.</span><span class="sxs-lookup"><span data-stu-id="c90a4-108">[in] A MethodDef token representing the method with the parameters to enumerate.</span></span>  
  
 `rParams`  
 <span data-ttu-id="c90a4-109">[out] Tablica używany do przechowywania tokenów ParamDef.</span><span class="sxs-lookup"><span data-stu-id="c90a4-109">[out] The array used to store the ParamDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="c90a4-110">[in] Maksymalny rozmiar `rParams` tablicy.</span><span class="sxs-lookup"><span data-stu-id="c90a4-110">[in] The maximum size of the `rParams` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="c90a4-111">[out] Liczba tokenów ParamDef zwracane w `rParams`.</span><span class="sxs-lookup"><span data-stu-id="c90a4-111">[out] The number of ParamDef tokens returned in `rParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c90a4-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c90a4-112">Return Value</span></span>  
  
|<span data-ttu-id="c90a4-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c90a4-113">HRESULT</span></span>|<span data-ttu-id="c90a4-114">Opis</span><span class="sxs-lookup"><span data-stu-id="c90a4-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="c90a4-115">`EnumParams`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="c90a4-115">`EnumParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="c90a4-116">Nie ma żadnych tokenów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="c90a4-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="c90a4-117">W takim przypadku `pcTokens` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="c90a4-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c90a4-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c90a4-118">Requirements</span></span>  
 <span data-ttu-id="c90a4-119">**Platforma:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c90a4-119">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c90a4-120">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c90a4-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c90a4-121">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c90a4-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c90a4-122">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c90a4-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c90a4-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c90a4-123">See Also</span></span>  
 [<span data-ttu-id="c90a4-124">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="c90a4-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="c90a4-125">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="c90a4-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
