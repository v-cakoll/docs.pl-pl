---
title: "IMetaDataImport::EnumUserStrings — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataImport.EnumUserStrings
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumUserStrings
helpviewer_keywords:
- IMetaDataImport::EnumUserStrings method [.NET Framework metadata]
- EnumUserStrings method [.NET Framework metadata]
ms.assetid: 2b1f1418-4be8-4cdb-b418-b3abccc527a7
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3d9c802318203db2ccd6043cded3c7730b18b0cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenumuserstrings-method"></a><span data-ttu-id="d3db7-102">IMetaDataImport::EnumUserStrings — Metoda</span><span class="sxs-lookup"><span data-stu-id="d3db7-102">IMetaDataImport::EnumUserStrings Method</span></span>
<span data-ttu-id="d3db7-103">Wylicza tokeny ciąg reprezentujący ustalony ciągów w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="d3db7-103">Enumerates String tokens representing hard-coded strings in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3db7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d3db7-104">Syntax</span></span>  
  
```  
HRESULT EnumUserStrings (  
   [in, out]  HCORENUM    *phEnum,  
   [out]  mdString        rStrings[],  
   [in]   ULONG           cMax,  
   [out]  ULONG           *pcStrings  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d3db7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d3db7-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="d3db7-106">[w, out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="d3db7-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="d3db7-107">Musi to być wartość NULL dla pierwsze wywołanie tej metody.</span><span class="sxs-lookup"><span data-stu-id="d3db7-107">This must be NULL for the first call of this method.</span></span>  
  
 `rStrings`  
 <span data-ttu-id="d3db7-108">[out] Tablica używany do przechowywania tokenów ciągu.</span><span class="sxs-lookup"><span data-stu-id="d3db7-108">[out] The array used to store the String tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="d3db7-109">[in] Maksymalny rozmiar `rStrings` tablicy.</span><span class="sxs-lookup"><span data-stu-id="d3db7-109">[in] The maximum size of the `rStrings` array.</span></span>  
  
 `pcStrings`  
 <span data-ttu-id="d3db7-110">[out] Liczba tokenów ciąg zwrócony w `rStrings`.</span><span class="sxs-lookup"><span data-stu-id="d3db7-110">[out] The number of String tokens returned in `rStrings`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d3db7-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d3db7-111">Return Value</span></span>  
  
|<span data-ttu-id="d3db7-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d3db7-112">HRESULT</span></span>|<span data-ttu-id="d3db7-113">Opis</span><span class="sxs-lookup"><span data-stu-id="d3db7-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="d3db7-114">`EnumUserStrings`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d3db7-114">`EnumUserStrings` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="d3db7-115">Nie ma żadnych tokenów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="d3db7-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="d3db7-116">W takim przypadku `pcStrings` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="d3db7-116">In that case, `pcStrings` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3db7-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d3db7-117">Remarks</span></span>  
 <span data-ttu-id="d3db7-118">Ciąg tokenów są tworzone przez [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="d3db7-118">The String tokens are created by the [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) method.</span></span> <span data-ttu-id="d3db7-119">Ta metoda jest przeznaczony do użycia w przeglądarce metadanych, a nie przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="d3db7-119">This method is designed to be used by a metadata browser rather than by a compiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3db7-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d3db7-120">Requirements</span></span>  
 <span data-ttu-id="d3db7-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3db7-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3db7-122">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d3db7-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d3db7-123">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d3db7-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d3db7-124">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3db7-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3db7-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d3db7-125">See Also</span></span>  
 [<span data-ttu-id="d3db7-126">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="d3db7-126">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="d3db7-127">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d3db7-127">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
