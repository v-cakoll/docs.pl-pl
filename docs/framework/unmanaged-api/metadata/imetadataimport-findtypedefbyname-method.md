---
title: "IMetaDataImport::FindTypeDefByName — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.FindTypeDefByName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::FindTypeDefByName
helpviewer_keywords:
- FindTypeDefByName method [.NET Framework metadata]
- IMetaDataImport::FindTypeDefByName method [.NET Framework metadata]
ms.assetid: f4c2cd88-ac28-4bad-9ab1-2cf9d2de41e6
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e4b3a5f9ff15e2b94e6d5c5e885605d8eabae711
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportfindtypedefbyname-method"></a><span data-ttu-id="ae381-102">IMetaDataImport::FindTypeDefByName — Metoda</span><span class="sxs-lookup"><span data-stu-id="ae381-102">IMetaDataImport::FindTypeDefByName Method</span></span>
<span data-ttu-id="ae381-103">Pobiera wskaźnik do metadanych elementu TypeDef token dla <xref:System.Type> o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="ae381-103">Gets a pointer to the TypeDef metadata token for the <xref:System.Type> with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae381-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ae381-104">Syntax</span></span>  
  
```  
HRESULT FindTypeDefByName  
   [in]  LPCWSTR       szTypeDef,  
   [in]  mdToken       tkEnclosingClass,  
   [out] mdTypeDef     *ptd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ae381-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ae381-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="ae381-106">[in] Nazwa typu, dla którego można pobrać token TypeDef.</span><span class="sxs-lookup"><span data-stu-id="ae381-106">[in] The name of the type for which to get the TypeDef token.</span></span>  
  
 `tkEnclosingClass`  
 <span data-ttu-id="ae381-107">[in] Token TypeDef lub TypeRef reprezentujący otaczającą klasę.</span><span class="sxs-lookup"><span data-stu-id="ae381-107">[in] A TypeDef or TypeRef token representing the enclosing class.</span></span> <span data-ttu-id="ae381-108">Jeśli typ do znalezienia nie jest klasą zagnieżdżoną, ustaw tę wartość NULL.</span><span class="sxs-lookup"><span data-stu-id="ae381-108">If the type to find is not a nested class, set this value to NULL.</span></span>  
  
 `ptd`  
 <span data-ttu-id="ae381-109">[out] Wskaźnik do dopasowania TypeDef token.</span><span class="sxs-lookup"><span data-stu-id="ae381-109">[out] A pointer to the matching TypeDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae381-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ae381-110">Requirements</span></span>  
 <span data-ttu-id="ae381-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae381-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae381-112">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ae381-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ae381-113">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ae381-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ae381-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae381-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae381-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ae381-115">See Also</span></span>  
 [<span data-ttu-id="ae381-116">IMetaDataImport — interfejs</span><span class="sxs-lookup"><span data-stu-id="ae381-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="ae381-117">IMetaDataImport2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="ae381-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
