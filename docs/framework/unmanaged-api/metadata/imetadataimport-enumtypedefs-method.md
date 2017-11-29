---
title: "IMetaDataImport::EnumTypeDefs — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumTypeDefs
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumTypeDefs
helpviewer_keywords:
- EnumTypeDefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeDefs method [.NET Framework metadata]
ms.assetid: 4e508711-da92-4381-aaf8-6803075cdaa2
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a07d9ff237e6d3838fffb068e3a9ebf9febf66fc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenumtypedefs-method"></a><span data-ttu-id="952a5-102">IMetaDataImport::EnumTypeDefs — Metoda</span><span class="sxs-lookup"><span data-stu-id="952a5-102">IMetaDataImport::EnumTypeDefs Method</span></span>
<span data-ttu-id="952a5-103">Wylicza tokeny TypeDef reprezentujący wszystkie typy w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="952a5-103">Enumerates TypeDef tokens representing all types within the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="952a5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="952a5-104">Syntax</span></span>  
  
```  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,   
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,   
   [out] ULONG      *pcTypeDefs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="952a5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="952a5-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="952a5-106">[out] Wskaźnik do nowego modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="952a5-106">[out] A pointer to the new enumerator.</span></span> <span data-ttu-id="952a5-107">Musi to być wartość NULL dla pierwsze wywołanie tej metody.</span><span class="sxs-lookup"><span data-stu-id="952a5-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeDefs`  
 <span data-ttu-id="952a5-108">[in] Tablica używany do przechowywania tokenów TypeDef.</span><span class="sxs-lookup"><span data-stu-id="952a5-108">[in] The array used to store the TypeDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="952a5-109">[in] Maksymalny rozmiar `rTypeDefs` tablicy.</span><span class="sxs-lookup"><span data-stu-id="952a5-109">[in] The maximum size of the `rTypeDefs` array.</span></span>  
  
 `pcTypeDefs`  
 <span data-ttu-id="952a5-110">[out] Liczba tokenów TypeDef zwracane w `rTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="952a5-110">[out] The number of TypeDef tokens returned in `rTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="952a5-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="952a5-111">Return Value</span></span>  
  
|<span data-ttu-id="952a5-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="952a5-112">HRESULT</span></span>|<span data-ttu-id="952a5-113">Opis</span><span class="sxs-lookup"><span data-stu-id="952a5-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="952a5-114">`EnumTypeDefs`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="952a5-114">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="952a5-115">Nie ma żadnych tokenów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="952a5-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="952a5-116">W takim przypadku `pcTypeDefs` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="952a5-116">In that case, `pcTypeDefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="952a5-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="952a5-117">Remarks</span></span>  
 <span data-ttu-id="952a5-118">TypeDef token reprezentuje typ, takich jak klasy lub interfejsu, jak również żadnego typu dodane za pośrednictwem mechanizm rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="952a5-118">The TypeDef token represents a type such as a class or an interface, as well as any type added via an extensibility mechanism.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="952a5-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="952a5-119">Requirements</span></span>  
 <span data-ttu-id="952a5-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="952a5-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="952a5-121">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="952a5-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="952a5-122">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="952a5-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="952a5-123">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="952a5-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="952a5-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="952a5-124">See Also</span></span>  
 [<span data-ttu-id="952a5-125">IMetaDataImport — interfejs</span><span class="sxs-lookup"><span data-stu-id="952a5-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="952a5-126">IMetaDataImport2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="952a5-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
