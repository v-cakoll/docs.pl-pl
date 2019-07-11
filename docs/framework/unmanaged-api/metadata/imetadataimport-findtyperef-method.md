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
ms.openlocfilehash: 8159b5245598993a2075fb402b280f9ab4cb2cfa
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782461"
---
# <a name="imetadataimportfindtyperef-method"></a><span data-ttu-id="b0810-102">IMetaDataImport::FindTypeRef — Metoda</span><span class="sxs-lookup"><span data-stu-id="b0810-102">IMetaDataImport::FindTypeRef Method</span></span>
<span data-ttu-id="b0810-103">Pobiera wskaźnik do TypeRef tokenu do <xref:System.Type> odwołania, który znajduje się w podanym zakresie i który ma określoną nazwę.</span><span class="sxs-lookup"><span data-stu-id="b0810-103">Gets a pointer to the TypeRef token for the <xref:System.Type> reference that is in the specified scope and that has the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0810-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b0810-104">Syntax</span></span>  
  
```cpp  
HRESULT FindTypeRef (  
   [in] mdToken        tkResolutionScope,  
   [in]  LPCWSTR       szName,  
   [out] mdTypeRef     *ptr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0810-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b0810-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="b0810-106">[in] Element ModuleRef, elementu AssemblyRef lub TypeRef token, który określa moduł, zestawu lub typu, odpowiednio, w której typ odwołania jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="b0810-106">[in] A ModuleRef, AssemblyRef, or TypeRef token that specifies the module, assembly, or type, respectively, in which the type reference is defined.</span></span>  
  
 `szName`  
 <span data-ttu-id="b0810-107">[in] Nazwa odwołania typu do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="b0810-107">[in] The name of the type reference to search for.</span></span>  
  
 `ptr`  
 <span data-ttu-id="b0810-108">[out] Wskaźnik do dopasowania token TypeRef.</span><span class="sxs-lookup"><span data-stu-id="b0810-108">[out] A pointer to the matching TypeRef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0810-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b0810-109">Requirements</span></span>  
 <span data-ttu-id="b0810-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0810-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0810-111">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="b0810-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b0810-112">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b0810-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b0810-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0810-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0810-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b0810-114">See also</span></span>

- [<span data-ttu-id="b0810-115">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="b0810-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="b0810-116">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="b0810-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
