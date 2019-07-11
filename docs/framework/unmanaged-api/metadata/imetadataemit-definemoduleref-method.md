---
title: IMetaDataEmit::DefineModuleRef — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineModuleRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineModuleRef
helpviewer_keywords:
- DefineModuleRef method [.NET Framework metadata]
- IMetaDataEmit::DefineModuleRef method [.NET Framework metadata]
ms.assetid: f2833594-d90b-4a71-9a53-34b12470c64a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 19f1839aa2c4ca810e76c1745103a00c6f5ea5a3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777576"
---
# <a name="imetadataemitdefinemoduleref-method"></a><span data-ttu-id="3b787-102">IMetaDataEmit::DefineModuleRef — Metoda</span><span class="sxs-lookup"><span data-stu-id="3b787-102">IMetaDataEmit::DefineModuleRef Method</span></span>
<span data-ttu-id="3b787-103">Tworzy podpisu metadanych dla modułu o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="3b787-103">Creates the metadata signature for a module with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b787-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3b787-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineModuleRef (     
    [in]  LPCWSTR           szName,   
    [out] mdModuleRef       *pmur   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b787-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3b787-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="3b787-106">[in] Nazwa drugiego pliku metadanych zwykle biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="3b787-106">[in] The name of the other metadata file, typically a DLL.</span></span> <span data-ttu-id="3b787-107">Jest to tylko nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="3b787-107">This is the file name only.</span></span> <span data-ttu-id="3b787-108">Nie należy używać pełnej nazwy ścieżki.</span><span class="sxs-lookup"><span data-stu-id="3b787-108">Do not use a full path name.</span></span>  
  
 `pmur`  
 <span data-ttu-id="3b787-109">[out] Przypisane `mdModuleRef` tokenu.</span><span class="sxs-lookup"><span data-stu-id="3b787-109">[out] The assigned `mdModuleRef` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b787-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3b787-110">Requirements</span></span>  
 <span data-ttu-id="3b787-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b787-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b787-112">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="3b787-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3b787-113">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3b787-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3b787-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b787-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b787-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3b787-115">See also</span></span>

- [<span data-ttu-id="3b787-116">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="3b787-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="3b787-117">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="3b787-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
