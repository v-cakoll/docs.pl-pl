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
ms.openlocfilehash: 21a69d120cc732ca6659f77abc9f8ea0c993271e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437786"
---
# <a name="imetadataimportfindtyperef-method"></a><span data-ttu-id="84ea8-102">IMetaDataImport::FindTypeRef — Metoda</span><span class="sxs-lookup"><span data-stu-id="84ea8-102">IMetaDataImport::FindTypeRef Method</span></span>
<span data-ttu-id="84ea8-103">Pobiera wskaźnik do tokenu TypeRef dla odwołania <xref:System.Type>, które znajduje się w określonym zakresie i ma określoną nazwę.</span><span class="sxs-lookup"><span data-stu-id="84ea8-103">Gets a pointer to the TypeRef token for the <xref:System.Type> reference that is in the specified scope and that has the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84ea8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="84ea8-104">Syntax</span></span>  
  
```cpp  
HRESULT FindTypeRef (  
   [in] mdToken        tkResolutionScope,  
   [in]  LPCWSTR       szName,  
   [out] mdTypeRef     *ptr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84ea8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="84ea8-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="84ea8-106">podczas Element ModuleRef, AssemblyRef lub TypeRef, który określa odpowiednio moduł, zestaw lub typ, w którym zdefiniowano odwołanie do typu.</span><span class="sxs-lookup"><span data-stu-id="84ea8-106">[in] A ModuleRef, AssemblyRef, or TypeRef token that specifies the module, assembly, or type, respectively, in which the type reference is defined.</span></span>  
  
 `szName`  
 <span data-ttu-id="84ea8-107">podczas Nazwa odwołania do typu do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="84ea8-107">[in] The name of the type reference to search for.</span></span>  
  
 `ptr`  
 <span data-ttu-id="84ea8-108">określoną Wskaźnik do zgodnego tokenu TypeRef.</span><span class="sxs-lookup"><span data-stu-id="84ea8-108">[out] A pointer to the matching TypeRef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84ea8-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="84ea8-109">Requirements</span></span>  
 <span data-ttu-id="84ea8-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84ea8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84ea8-111">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="84ea8-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="84ea8-112">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="84ea8-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="84ea8-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84ea8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84ea8-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="84ea8-114">See also</span></span>

- [<span data-ttu-id="84ea8-115">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="84ea8-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="84ea8-116">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="84ea8-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
