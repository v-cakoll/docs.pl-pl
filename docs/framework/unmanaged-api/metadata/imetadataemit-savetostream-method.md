---
title: IMetaDataEmit::SaveToStream — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SaveToStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SaveToStream
helpviewer_keywords:
- IMetaDataEmit::SaveToStream method [.NET Framework metadata]
- SaveToStream method [.NET Framework metadata]
ms.assetid: e0290a49-3818-4a43-ad46-3014faa34f97
topic_type:
- apiref
ms.openlocfilehash: 87e00a69643b6bc403188fb0fdb6f9e3f3d82115
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84003883"
---
# <a name="imetadataemitsavetostream-method"></a><span data-ttu-id="dd8e4-102">IMetaDataEmit::SaveToStream — Metoda</span><span class="sxs-lookup"><span data-stu-id="dd8e4-102">IMetaDataEmit::SaveToStream Method</span></span>
<span data-ttu-id="dd8e4-103">Zapisuje wszystkie metadane w bieżącym zakresie do określonego `IStream` .</span><span class="sxs-lookup"><span data-stu-id="dd8e4-103">Saves all metadata in the current scope to the specified `IStream`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd8e4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dd8e4-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveToStream (
    [in]  IStream     *pIStream,  
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd8e4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dd8e4-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="dd8e4-106">podczas Zapisywalny strumień do zapisu.</span><span class="sxs-lookup"><span data-stu-id="dd8e4-106">[in] The writable stream to save to.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="dd8e4-107">podczas Rezerwacj.</span><span class="sxs-lookup"><span data-stu-id="dd8e4-107">[in] Reserved.</span></span> <span data-ttu-id="dd8e4-108">Musi być równa zero.</span><span class="sxs-lookup"><span data-stu-id="dd8e4-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd8e4-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dd8e4-109">Requirements</span></span>  
 <span data-ttu-id="dd8e4-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd8e4-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd8e4-111">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="dd8e4-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dd8e4-112">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="dd8e4-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dd8e4-113">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd8e4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd8e4-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dd8e4-114">See also</span></span>

- [<span data-ttu-id="dd8e4-115">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="dd8e4-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="dd8e4-116">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="dd8e4-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
