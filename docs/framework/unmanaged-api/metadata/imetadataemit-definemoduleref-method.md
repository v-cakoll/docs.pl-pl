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
ms.openlocfilehash: 94261b7796166cf482a7de990551890e4722dd3b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177738"
---
# <a name="imetadataemitdefinemoduleref-method"></a><span data-ttu-id="4b9c7-102">IMetaDataEmit::DefineModuleRef — Metoda</span><span class="sxs-lookup"><span data-stu-id="4b9c7-102">IMetaDataEmit::DefineModuleRef Method</span></span>
<span data-ttu-id="4b9c7-103">Tworzy podpis metadanych dla modułu o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="4b9c7-103">Creates the metadata signature for a module with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b9c7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4b9c7-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineModuleRef (
    [in]  LPCWSTR           szName,
    [out] mdModuleRef       *pmur
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b9c7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4b9c7-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="4b9c7-106">[w] Nazwa innego pliku metadanych, zazwyczaj biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="4b9c7-106">[in] The name of the other metadata file, typically a DLL.</span></span> <span data-ttu-id="4b9c7-107">Jest to tylko nazwa pliku.</span><span class="sxs-lookup"><span data-stu-id="4b9c7-107">This is the file name only.</span></span> <span data-ttu-id="4b9c7-108">Nie należy używać pełnej nazwy ścieżki.</span><span class="sxs-lookup"><span data-stu-id="4b9c7-108">Do not use a full path name.</span></span>  
  
 `pmur`  
 <span data-ttu-id="4b9c7-109">[na zewnątrz] Przypisany `mdModuleRef` token.</span><span class="sxs-lookup"><span data-stu-id="4b9c7-109">[out] The assigned `mdModuleRef` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b9c7-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4b9c7-110">Requirements</span></span>  
 <span data-ttu-id="4b9c7-111">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b9c7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b9c7-112">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="4b9c7-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4b9c7-113">**Biblioteka:** Używany jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4b9c7-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4b9c7-114">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b9c7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b9c7-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4b9c7-115">See also</span></span>

- [<span data-ttu-id="4b9c7-116">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="4b9c7-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="4b9c7-117">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="4b9c7-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
