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
ms.openlocfilehash: 545fe1e1d9e641d2225ad92c11453558dc4b97d1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491501"
---
# <a name="imetadataimportfindtyperef-method"></a><span data-ttu-id="41b40-102">IMetaDataImport::FindTypeRef — Metoda</span><span class="sxs-lookup"><span data-stu-id="41b40-102">IMetaDataImport::FindTypeRef Method</span></span>
<span data-ttu-id="41b40-103">Pobiera wskaźnik do tokenu TypeRef dla <xref:System.Type> odwołania, które znajduje się w określonym zakresie i ma określoną nazwę.</span><span class="sxs-lookup"><span data-stu-id="41b40-103">Gets a pointer to the TypeRef token for the <xref:System.Type> reference that is in the specified scope and that has the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41b40-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="41b40-104">Syntax</span></span>  
  
```cpp  
HRESULT FindTypeRef (  
   [in] mdToken        tkResolutionScope,  
   [in]  LPCWSTR       szName,  
   [out] mdTypeRef     *ptr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41b40-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="41b40-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="41b40-106">podczas Element ModuleRef, AssemblyRef lub TypeRef, który określa odpowiednio moduł, zestaw lub typ, w którym zdefiniowano odwołanie do typu.</span><span class="sxs-lookup"><span data-stu-id="41b40-106">[in] A ModuleRef, AssemblyRef, or TypeRef token that specifies the module, assembly, or type, respectively, in which the type reference is defined.</span></span>  
  
 `szName`  
 <span data-ttu-id="41b40-107">podczas Nazwa odwołania do typu do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="41b40-107">[in] The name of the type reference to search for.</span></span>  
  
 `ptr`  
 <span data-ttu-id="41b40-108">określoną Wskaźnik do zgodnego tokenu TypeRef.</span><span class="sxs-lookup"><span data-stu-id="41b40-108">[out] A pointer to the matching TypeRef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41b40-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="41b40-109">Requirements</span></span>  
 <span data-ttu-id="41b40-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41b40-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41b40-111">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="41b40-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="41b40-112">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="41b40-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="41b40-113">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41b40-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41b40-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="41b40-114">See also</span></span>

- [<span data-ttu-id="41b40-115">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="41b40-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="41b40-116">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="41b40-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
