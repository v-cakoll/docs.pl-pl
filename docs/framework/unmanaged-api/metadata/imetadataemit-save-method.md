---
title: IMetaDataEmit::Save — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.Save
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::Save
helpviewer_keywords:
- Save method, IMetaDataEmit interface [.NET Framework metadata]
- IMetaDataEmit::Save method [.NET Framework metadata]
ms.assetid: c1de8400-adfe-4a71-b828-a1d0cc1ea505
topic_type:
- apiref
ms.openlocfilehash: 23f6a301c4c11be92e05dbac0d4f69817d857a28
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84003964"
---
# <a name="imetadataemitsave-method"></a><span data-ttu-id="2d304-102">IMetaDataEmit::Save — Metoda</span><span class="sxs-lookup"><span data-stu-id="2d304-102">IMetaDataEmit::Save Method</span></span>
<span data-ttu-id="2d304-103">Zapisuje wszystkie metadane w bieżącym zakresie do pliku pod określonym adresem.</span><span class="sxs-lookup"><span data-stu-id="2d304-103">Saves all metadata in the current scope to the file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d304-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2d304-104">Syntax</span></span>  
  
```cpp  
HRESULT Save (
    [in]  LPCWSTR     szFile,
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d304-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2d304-105">Parameters</span></span>  
 `wzFile`  
 <span data-ttu-id="2d304-106">podczas Nazwa pliku, w którym ma zostać zapisana.</span><span class="sxs-lookup"><span data-stu-id="2d304-106">[in] The name of the file to save to.</span></span> <span data-ttu-id="2d304-107">Jeśli ta wartość jest równa null, kopia znajdująca się w pamięci zostanie zapisana w ostatnio używanej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="2d304-107">If this value is null, the in-memory copy will be saved to the last location that was used.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="2d304-108">podczas Rezerwacj.</span><span class="sxs-lookup"><span data-stu-id="2d304-108">[in] Reserved.</span></span> <span data-ttu-id="2d304-109">Musi być równa zero.</span><span class="sxs-lookup"><span data-stu-id="2d304-109">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d304-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2d304-110">Requirements</span></span>  
 <span data-ttu-id="2d304-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d304-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d304-112">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2d304-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2d304-113">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2d304-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2d304-114">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d304-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d304-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d304-115">See also</span></span>

- [<span data-ttu-id="2d304-116">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2d304-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="2d304-117">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="2d304-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
