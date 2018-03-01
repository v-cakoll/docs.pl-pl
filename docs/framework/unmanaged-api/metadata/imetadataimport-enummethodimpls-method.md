---
title: "IMetaDataImport::EnumMethodImpls — Metoda"
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
- IMetaDataImport.EnumMethodImpls
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodImpls
helpviewer_keywords:
- EnumMethodImpls method [.NET Framework metadata]
- IMetaDataImport::EnumMethodImpls method [.NET Framework metadata]
ms.assetid: 4e0f865d-88b5-44bd-be35-492622e5e08e
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e3350fb4513604a0edc47cbf47e257648ff0d75a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenummethodimpls-method"></a><span data-ttu-id="7bb8d-102">IMetaDataImport::EnumMethodImpls — Metoda</span><span class="sxs-lookup"><span data-stu-id="7bb8d-102">IMetaDataImport::EnumMethodImpls Method</span></span>
<span data-ttu-id="7bb8d-103">Wylicza MethodBody i MethodDeclaration tokeny reprezentujący metody określonego typu.</span><span class="sxs-lookup"><span data-stu-id="7bb8d-103">Enumerates MethodBody and MethodDeclaration tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bb8d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7bb8d-104">Syntax</span></span>  
  
```  
HRESULT EnumMethodImpls (  
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   td,   
   [out]     mdToken     rMethodBody[],   
   [out]     mdToken     rMethodDecl[],   
   [in]      ULONG       cMax,   
   [in]      ULONG       *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7bb8d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7bb8d-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="7bb8d-106">[w, out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="7bb8d-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="7bb8d-107">Musi to być wartość NULL dla pierwsze wywołanie tej metody.</span><span class="sxs-lookup"><span data-stu-id="7bb8d-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="7bb8d-108">[in] Element TypeDef token dla typu którego implementacje metod do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="7bb8d-108">[in] A TypeDef token for the type whose method implementations to enumerate.</span></span>  
  
 `rMethodBody`  
 <span data-ttu-id="7bb8d-109">[out] Tablica do przechowywania tokenów MethodBody.</span><span class="sxs-lookup"><span data-stu-id="7bb8d-109">[out] The array to store the MethodBody tokens.</span></span>  
  
 `rMethodDecl`  
 <span data-ttu-id="7bb8d-110">[out] Tablica do przechowywania tokenów MethodDeclaration.</span><span class="sxs-lookup"><span data-stu-id="7bb8d-110">[out] The array to store the MethodDeclaration tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="7bb8d-111">[in] Maksymalny rozmiar `rMethodBody` i `rMethodDecl` tablic.</span><span class="sxs-lookup"><span data-stu-id="7bb8d-111">[in] The maximum size of the `rMethodBody` and `rMethodDecl` arrays.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="7bb8d-112">[in] Rzeczywista liczba metod zwracane w `rMethodBody` i `rMethodDecl`.</span><span class="sxs-lookup"><span data-stu-id="7bb8d-112">[in] The actual number of methods returned in `rMethodBody` and `rMethodDecl`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7bb8d-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7bb8d-113">Return Value</span></span>  
  
|<span data-ttu-id="7bb8d-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7bb8d-114">HRESULT</span></span>|<span data-ttu-id="7bb8d-115">Opis</span><span class="sxs-lookup"><span data-stu-id="7bb8d-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="7bb8d-116">`EnumMethodImpls`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="7bb8d-116">`EnumMethodImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="7bb8d-117">Nie ma żadnych tokenów — metoda wyliczania.</span><span class="sxs-lookup"><span data-stu-id="7bb8d-117">There are no method tokens to enumerate.</span></span> <span data-ttu-id="7bb8d-118">W takim przypadku `pcTokens` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="7bb8d-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7bb8d-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7bb8d-119">Requirements</span></span>  
 <span data-ttu-id="7bb8d-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7bb8d-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bb8d-121">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7bb8d-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7bb8d-122">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7bb8d-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7bb8d-123">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bb8d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bb8d-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7bb8d-124">See Also</span></span>  
 [<span data-ttu-id="7bb8d-125">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="7bb8d-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="7bb8d-126">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="7bb8d-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
