---
title: "IMetaDataImport::EnumTypeSpecs — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumTypeSpecs
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumTypeSpecs
helpviewer_keywords:
- EnumTypeSpecs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeSpecs method [.NET Framework metadata]
ms.assetid: 75331c7b-988b-436c-9eb9-a270d37b4f06
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a872af384a8df624178d8d37d5ad98a0b5c561d1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenumtypespecs-method"></a><span data-ttu-id="7cb09-102">IMetaDataImport::EnumTypeSpecs — Metoda</span><span class="sxs-lookup"><span data-stu-id="7cb09-102">IMetaDataImport::EnumTypeSpecs Method</span></span>
<span data-ttu-id="7cb09-103">Wylicza tokenów elementu TypeSpec zdefiniowany w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="7cb09-103">Enumerates TypeSpec tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cb09-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7cb09-104">Syntax</span></span>  
  
```  
HRESULT EnumTypeSpecs (  
   [in, out] HCORENUM    *phEnum,  
   [out] mdTypeSpec      rTypeSpecs[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTypeSpecs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7cb09-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7cb09-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="7cb09-106">[w, out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="7cb09-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="7cb09-107">Ta wartość musi być równa NULL, pierwsze wywołanie tej metody.</span><span class="sxs-lookup"><span data-stu-id="7cb09-107">This value must be NULL for the first call of this method.</span></span>  
  
 `rTypeSpecs`  
 <span data-ttu-id="7cb09-108">[out] Tablica używany do przechowywania tokenów elementu TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="7cb09-108">[out] The array used to store the TypeSpec tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="7cb09-109">[in] Maksymalny rozmiar `rTypeSpecs` tablicy.</span><span class="sxs-lookup"><span data-stu-id="7cb09-109">[in] The maximum size of the `rTypeSpecs` array.</span></span>  
  
 `pcTypeSpecs`  
 <span data-ttu-id="7cb09-110">[out] Liczba tokenów elementu TypeSpec zwracane w `rTypeSpecs`.</span><span class="sxs-lookup"><span data-stu-id="7cb09-110">[out] The number of TypeSpec tokens returned in `rTypeSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7cb09-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7cb09-111">Return Value</span></span>  
  
|<span data-ttu-id="7cb09-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7cb09-112">HRESULT</span></span>|<span data-ttu-id="7cb09-113">Opis</span><span class="sxs-lookup"><span data-stu-id="7cb09-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="7cb09-114">`EnumTypeSpecs`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="7cb09-114">`EnumTypeSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="7cb09-115">Nie ma żadnych tokenów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="7cb09-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="7cb09-116">W takim przypadku `pcTypeSpecs` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="7cb09-116">In that case, `pcTypeSpecs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7cb09-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7cb09-117">Remarks</span></span>  
 <span data-ttu-id="7cb09-118">Element TypeSpec tokenów są tworzone przez [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="7cb09-118">The TypeSpec tokens are created by the [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cb09-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7cb09-119">Requirements</span></span>  
 <span data-ttu-id="7cb09-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7cb09-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cb09-121">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7cb09-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7cb09-122">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7cb09-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7cb09-123">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cb09-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cb09-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7cb09-124">See Also</span></span>  
 [<span data-ttu-id="7cb09-125">IMetaDataImport — interfejs</span><span class="sxs-lookup"><span data-stu-id="7cb09-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="7cb09-126">IMetaDataImport2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="7cb09-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
