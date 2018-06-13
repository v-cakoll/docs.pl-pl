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
ms.openlocfilehash: 1c77f946b14fcb5ddc786488ab42e37eb868fbc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448282"
---
# <a name="imetadataimportgetnestedclassprops-method"></a><span data-ttu-id="871f7-102">IMetaDataImport::GetNestedClassProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="871f7-102">IMetaDataImport::GetNestedClassProps Method</span></span>
<span data-ttu-id="871f7-103">Pobiera TypeDef token nadrzędnego <xref:System.Type> określonego typu zagnieżdżonego.</span><span class="sxs-lookup"><span data-stu-id="871f7-103">Gets the TypeDef token for the parent <xref:System.Type> of the specified nested type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="871f7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="871f7-104">Syntax</span></span>  
  
```  
HRESULT GetNestedClassProps (  
   [in]   mdTypeDef      tdNestedClass,  
   [out]  mdTypeDef      *ptdEnclosingClass  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="871f7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="871f7-105">Parameters</span></span>  
 `tdNestedClass`  
 <span data-ttu-id="871f7-106">[in] Element TypeDef token reprezentujący <xref:System.Type> do zwrócenia klasy nadrzędnej dla tokenu.</span><span class="sxs-lookup"><span data-stu-id="871f7-106">[in] A TypeDef token representing the <xref:System.Type> to return the parent class token for.</span></span>  
  
 `ptdEnclosingClass`  
 <span data-ttu-id="871f7-107">[out] Wskaźnik do TypeDef token dla <xref:System.Type> który `tdNestedClass` jest zagnieżdżony w.</span><span class="sxs-lookup"><span data-stu-id="871f7-107">[out] A pointer to the TypeDef token for the <xref:System.Type> that `tdNestedClass` is nested in.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="871f7-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="871f7-108">Requirements</span></span>  
 <span data-ttu-id="871f7-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="871f7-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="871f7-110">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="871f7-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="871f7-111">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="871f7-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="871f7-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="871f7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="871f7-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="871f7-113">See Also</span></span>  
 [<span data-ttu-id="871f7-114">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="871f7-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="871f7-115">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="871f7-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
