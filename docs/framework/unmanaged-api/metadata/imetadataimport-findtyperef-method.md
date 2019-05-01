---
title: IMetaDataImport::FindTypeRef — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindTypeRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindTypeRef
helpviewer_keywords:
- IMetaDataImport::FindTypeRef method [.NET Framework metadata]
- FindTypeRef method [.NET Framework metadata]
ms.assetid: 1b2bbf3f-943e-412e-b66c-e802431b055c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: acc006894f05536ed76bac60b0fde9277a460813
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777848"
---
# <a name="imetadataimportfindtyperef-method"></a><span data-ttu-id="77cc5-102">IMetaDataImport::FindTypeRef — Metoda</span><span class="sxs-lookup"><span data-stu-id="77cc5-102">IMetaDataImport::FindTypeRef Method</span></span>
<span data-ttu-id="77cc5-103">Pobiera wskaźnik do TypeRef tokenu do <xref:System.Type> odwołania, który znajduje się w podanym zakresie i który ma określoną nazwę.</span><span class="sxs-lookup"><span data-stu-id="77cc5-103">Gets a pointer to the TypeRef token for the <xref:System.Type> reference that is in the specified scope and that has the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77cc5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="77cc5-104">Syntax</span></span>  
  
```  
HRESULT FindTypeRef (  
   [in] mdToken        tkResolutionScope,  
   [in]  LPCWSTR       szName,  
   [out] mdTypeRef     *ptr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77cc5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="77cc5-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="77cc5-106">[in] Element ModuleRef, elementu AssemblyRef lub TypeRef token, który określa moduł, zestawu lub typu, odpowiednio, w której typ odwołania jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="77cc5-106">[in] A ModuleRef, AssemblyRef, or TypeRef token that specifies the module, assembly, or type, respectively, in which the type reference is defined.</span></span>  
  
 `szName`  
 <span data-ttu-id="77cc5-107">[in] Nazwa odwołania typu do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="77cc5-107">[in] The name of the type reference to search for.</span></span>  
  
 `ptr`  
 <span data-ttu-id="77cc5-108">[out] Wskaźnik do dopasowania token TypeRef.</span><span class="sxs-lookup"><span data-stu-id="77cc5-108">[out] A pointer to the matching TypeRef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77cc5-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="77cc5-109">Requirements</span></span>  
 <span data-ttu-id="77cc5-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77cc5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77cc5-111">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="77cc5-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="77cc5-112">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="77cc5-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="77cc5-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77cc5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77cc5-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="77cc5-114">See also</span></span>

- [<span data-ttu-id="77cc5-115">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="77cc5-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="77cc5-116">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="77cc5-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
