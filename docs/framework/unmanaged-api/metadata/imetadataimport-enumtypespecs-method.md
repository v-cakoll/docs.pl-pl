---
title: "IMetaDataImport::EnumTypeSpecs — Metoda"
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
- IMetaDataImport.EnumTypeSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeSpecs
helpviewer_keywords:
- EnumTypeSpecs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeSpecs method [.NET Framework metadata]
ms.assetid: 75331c7b-988b-436c-9eb9-a270d37b4f06
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9e34a3086474918c913a366c02bbf9eadf313b43
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenumtypespecs-method"></a><span data-ttu-id="70410-102">IMetaDataImport::EnumTypeSpecs — Metoda</span><span class="sxs-lookup"><span data-stu-id="70410-102">IMetaDataImport::EnumTypeSpecs Method</span></span>
<span data-ttu-id="70410-103">Wylicza tokenów elementu TypeSpec zdefiniowany w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="70410-103">Enumerates TypeSpec tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70410-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="70410-104">Syntax</span></span>  
  
```  
HRESULT EnumTypeSpecs (  
   [in, out] HCORENUM    *phEnum,  
   [out] mdTypeSpec      rTypeSpecs[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTypeSpecs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="70410-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="70410-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="70410-106">[w, out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="70410-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="70410-107">Ta wartość musi być równa NULL, pierwsze wywołanie tej metody.</span><span class="sxs-lookup"><span data-stu-id="70410-107">This value must be NULL for the first call of this method.</span></span>  
  
 `rTypeSpecs`  
 <span data-ttu-id="70410-108">[out] Tablica używany do przechowywania tokenów elementu TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="70410-108">[out] The array used to store the TypeSpec tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="70410-109">[in] Maksymalny rozmiar `rTypeSpecs` tablicy.</span><span class="sxs-lookup"><span data-stu-id="70410-109">[in] The maximum size of the `rTypeSpecs` array.</span></span>  
  
 `pcTypeSpecs`  
 <span data-ttu-id="70410-110">[out] Liczba tokenów elementu TypeSpec zwracane w `rTypeSpecs`.</span><span class="sxs-lookup"><span data-stu-id="70410-110">[out] The number of TypeSpec tokens returned in `rTypeSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="70410-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="70410-111">Return Value</span></span>  
  
|<span data-ttu-id="70410-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="70410-112">HRESULT</span></span>|<span data-ttu-id="70410-113">Opis</span><span class="sxs-lookup"><span data-stu-id="70410-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="70410-114">`EnumTypeSpecs`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="70410-114">`EnumTypeSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="70410-115">Nie ma żadnych tokenów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="70410-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="70410-116">W takim przypadku `pcTypeSpecs` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="70410-116">In that case, `pcTypeSpecs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70410-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="70410-117">Remarks</span></span>  
 <span data-ttu-id="70410-118">Element TypeSpec tokenów są tworzone przez [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="70410-118">The TypeSpec tokens are created by the [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70410-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="70410-119">Requirements</span></span>  
 <span data-ttu-id="70410-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70410-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70410-121">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="70410-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="70410-122">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="70410-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="70410-123">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70410-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70410-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="70410-124">See Also</span></span>  
 [<span data-ttu-id="70410-125">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="70410-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="70410-126">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="70410-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
