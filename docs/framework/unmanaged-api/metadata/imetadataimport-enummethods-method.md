---
title: "IMetaDataImport::EnumMethods — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumMethods
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumMethods
helpviewer_keywords:
- IMetaDataImport::EnumMethods method [.NET Framework metadata]
- EnumMethods method [.NET Framework metadata]
ms.assetid: 8cc3b0c3-d97d-4f71-9e7d-ef2a92b4959a
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d56c87d7073886d13e530501168801c6c69d9ce9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenummethods-method"></a><span data-ttu-id="74ac7-102">IMetaDataImport::EnumMethods — Metoda</span><span class="sxs-lookup"><span data-stu-id="74ac7-102">IMetaDataImport::EnumMethods Method</span></span>
<span data-ttu-id="74ac7-103">Wylicza tokeny MethodDef reprezentujący metody określonego typu.</span><span class="sxs-lookup"><span data-stu-id="74ac7-103">Enumerates MethodDef tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74ac7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="74ac7-104">Syntax</span></span>  
  
```  
HRESULT EnumMethods (  
   [in, out] HCORENUM   *phEnum,   
   [in]  mdTypeDef      cl,   
   [out] mdMethodDef    rMethods[],   
   [in]  ULONG          cMax,   
   [out] ULONG          *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="74ac7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="74ac7-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="74ac7-106">[w, out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="74ac7-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="74ac7-107">Musi to być wartość NULL dla pierwsze wywołanie tej metody.</span><span class="sxs-lookup"><span data-stu-id="74ac7-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="74ac7-108">[in] Element TypeDef token reprezentujący typ z metody wyliczania.</span><span class="sxs-lookup"><span data-stu-id="74ac7-108">[in] A TypeDef token representing the type with the methods to enumerate.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="74ac7-109">[out] Tablica do przechowywania tokenów MethodDef.</span><span class="sxs-lookup"><span data-stu-id="74ac7-109">[out] The array to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="74ac7-110">[in] Maksymalny rozmiar MethodDef `rMethods` tablicy.</span><span class="sxs-lookup"><span data-stu-id="74ac7-110">[in] The maximum size of the MethodDef `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="74ac7-111">[out] Liczba tokenów MethodDef zwracane w `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="74ac7-111">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="74ac7-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="74ac7-112">Return Value</span></span>  
  
|<span data-ttu-id="74ac7-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="74ac7-113">HRESULT</span></span>|<span data-ttu-id="74ac7-114">Opis</span><span class="sxs-lookup"><span data-stu-id="74ac7-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="74ac7-115">`EnumMethods`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="74ac7-115">`EnumMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="74ac7-116">Nie ma żadnych tokenów MethodDef do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="74ac7-116">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="74ac7-117">W takim przypadku `pcTokens` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="74ac7-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="74ac7-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="74ac7-118">Requirements</span></span>  
 <span data-ttu-id="74ac7-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74ac7-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74ac7-120">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="74ac7-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="74ac7-121">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="74ac7-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="74ac7-122">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74ac7-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74ac7-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="74ac7-123">See Also</span></span>  
 [<span data-ttu-id="74ac7-124">IMetaDataImport — interfejs</span><span class="sxs-lookup"><span data-stu-id="74ac7-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="74ac7-125">IMetaDataImport2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="74ac7-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
