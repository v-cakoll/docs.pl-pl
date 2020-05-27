---
title: IMetaDataEmit::SetModuleProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetModuleProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetModuleProps
helpviewer_keywords:
- SetModuleProps method [.NET Framework metadata]
- IMetaDataEmit::SetModuleProps method [.NET Framework metadata]
ms.assetid: b74d7629-5f46-458f-8d67-2456a1e7030c
topic_type:
- apiref
ms.openlocfilehash: aee258c49e6726ebef990257456fd273b01b9ef0
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007848"
---
# <a name="imetadataemitsetmoduleprops-method"></a><span data-ttu-id="e8387-102">IMetaDataEmit::SetModuleProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="e8387-102">IMetaDataEmit::SetModuleProps Method</span></span>
<span data-ttu-id="e8387-103">Aktualizuje odwołania do modułu zdefiniowanego przez poprzednie wywołanie do [IMetaDataEmit::D efinemoduleref](imetadataemit-definemoduleref-method.md).</span><span class="sxs-lookup"><span data-stu-id="e8387-103">Updates references to a module defined by a prior call to [IMetaDataEmit::DefineModuleRef](imetadataemit-definemoduleref-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8387-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e8387-104">Syntax</span></span>  
  
```cpp  
HRESULT SetModuleProps (
    [in]  LPCWSTR     szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8387-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e8387-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="e8387-106">podczas Nazwa modułu w formacie Unicode.</span><span class="sxs-lookup"><span data-stu-id="e8387-106">[in] The module name in Unicode.</span></span> <span data-ttu-id="e8387-107">Jest to tylko nazwa pliku, a nie pełna nazwa ścieżki.</span><span class="sxs-lookup"><span data-stu-id="e8387-107">This is the file name only and not the full path name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8387-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e8387-108">Requirements</span></span>  
 <span data-ttu-id="e8387-109">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8387-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8387-110">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e8387-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e8387-111">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e8387-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e8387-112">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8387-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8387-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e8387-113">See also</span></span>

- [<span data-ttu-id="e8387-114">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e8387-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="e8387-115">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="e8387-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
