---
title: IMetaDataImport::GetNestedClassProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNestedClassProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNestedClassProps
helpviewer_keywords:
- GetNestedClassProps method [.NET Framework metadata]
- IMetaDataImport::GetNestedClassProps method [.NET Framework metadata]
ms.assetid: 704d19f1-bdef-4745-af8c-6476eb246fb3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eb5820087001a207af0c2552f91b4c17f5f78ff7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074836"
---
# <a name="imetadataimportgetnestedclassprops-method"></a><span data-ttu-id="ce7a9-102">IMetaDataImport::GetNestedClassProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="ce7a9-102">IMetaDataImport::GetNestedClassProps Method</span></span>
<span data-ttu-id="ce7a9-103">Pobiera token do definicji typu nadrzędnego <xref:System.Type> określonego zagnieżdżonych typów.</span><span class="sxs-lookup"><span data-stu-id="ce7a9-103">Gets the TypeDef token for the parent <xref:System.Type> of the specified nested type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce7a9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ce7a9-104">Syntax</span></span>  
  
```  
HRESULT GetNestedClassProps (  
   [in]   mdTypeDef      tdNestedClass,  
   [out]  mdTypeDef      *ptdEnclosingClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce7a9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce7a9-105">Parameters</span></span>  
 `tdNestedClass`  
 <span data-ttu-id="ce7a9-106">[in] Element TypeDef token reprezentujący <xref:System.Type> do zwrócenia klasy nadrzędnej tokenu do.</span><span class="sxs-lookup"><span data-stu-id="ce7a9-106">[in] A TypeDef token representing the <xref:System.Type> to return the parent class token for.</span></span>  
  
 `ptdEnclosingClass`  
 <span data-ttu-id="ce7a9-107">[out] Wskaźnik do tokenu element TypeDef dla <xref:System.Type> , `tdNestedClass` jest zagnieżdżony w.</span><span class="sxs-lookup"><span data-stu-id="ce7a9-107">[out] A pointer to the TypeDef token for the <xref:System.Type> that `tdNestedClass` is nested in.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce7a9-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ce7a9-108">Requirements</span></span>  
 <span data-ttu-id="ce7a9-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce7a9-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce7a9-110">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="ce7a9-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ce7a9-111">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ce7a9-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="ce7a9-112">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="ce7a9-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ce7a9-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ce7a9-113">See also</span></span>

- [<span data-ttu-id="ce7a9-114">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ce7a9-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="ce7a9-115">IMetaDataImport2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ce7a9-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
