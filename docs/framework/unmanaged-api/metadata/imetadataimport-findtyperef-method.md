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
ms.openlocfilehash: 6364f9091b399182a44f143cef9e47a4fe667913
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485034"
---
# <a name="imetadataimportfindtyperef-method"></a><span data-ttu-id="81acc-102">IMetaDataImport::FindTypeRef — Metoda</span><span class="sxs-lookup"><span data-stu-id="81acc-102">IMetaDataImport::FindTypeRef Method</span></span>
<span data-ttu-id="81acc-103">Pobiera wskaźnik do TypeRef tokenu do <xref:System.Type> odwołania, który znajduje się w podanym zakresie i który ma określoną nazwę.</span><span class="sxs-lookup"><span data-stu-id="81acc-103">Gets a pointer to the TypeRef token for the <xref:System.Type> reference that is in the specified scope and that has the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81acc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="81acc-104">Syntax</span></span>  
  
```  
HRESULT FindTypeRef (  
   [in] mdToken        tkResolutionScope,  
   [in]  LPCWSTR       szName,  
   [out] mdTypeRef     *ptr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81acc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="81acc-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="81acc-106">[in] Element ModuleRef, elementu AssemblyRef lub TypeRef token, który określa moduł, zestawu lub typu, odpowiednio, w której typ odwołania jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="81acc-106">[in] A ModuleRef, AssemblyRef, or TypeRef token that specifies the module, assembly, or type, respectively, in which the type reference is defined.</span></span>  
  
 `szName`  
 <span data-ttu-id="81acc-107">[in] Nazwa odwołania typu do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="81acc-107">[in] The name of the type reference to search for.</span></span>  
  
 `ptr`  
 <span data-ttu-id="81acc-108">[out] Wskaźnik do dopasowania token TypeRef.</span><span class="sxs-lookup"><span data-stu-id="81acc-108">[out] A pointer to the matching TypeRef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81acc-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="81acc-109">Requirements</span></span>  
 <span data-ttu-id="81acc-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81acc-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81acc-111">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="81acc-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="81acc-112">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="81acc-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="81acc-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81acc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81acc-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="81acc-114">See also</span></span>
- [<span data-ttu-id="81acc-115">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="81acc-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="81acc-116">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="81acc-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
