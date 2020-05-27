---
title: IMetaDataEmit::SetCustomAttributeValue — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetCustomAttributeValue
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetCustomAttributeValue
helpviewer_keywords:
- SetCustomAttributeValue method [.NET Framework metadata]
- IMetaDataEmit::SetCustomAttributeValue method [.NET Framework metadata]
ms.assetid: f721c863-9642-4e64-917a-65f9e55c25b9
topic_type:
- apiref
ms.openlocfilehash: 6e24db7da7abbdb597b8ff64515e8053667af3ff
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008771"
---
# <a name="imetadataemitsetcustomattributevalue-method"></a><span data-ttu-id="20095-102">IMetaDataEmit::SetCustomAttributeValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="20095-102">IMetaDataEmit::SetCustomAttributeValue Method</span></span>
<span data-ttu-id="20095-103">Ustawia lub aktualizuje wartość atrybutu niestandardowego zdefiniowanego przez poprzednie wywołanie do [IMetaDataEmit::D efinecustomattribute](imetadataemit-definecustomattribute-method.md).</span><span class="sxs-lookup"><span data-stu-id="20095-103">Sets or updates the value of a custom attribute defined by a prior call to [IMetaDataEmit::DefineCustomAttribute](imetadataemit-definecustomattribute-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20095-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="20095-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCustomAttributeValue (
    [in]  mdCustomAttribute       pcv,
    [in]  void const              *pCustomAttribute,
    [in]  ULONG                   cbCustomAttribute
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20095-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="20095-105">Parameters</span></span>  
 `pcv`  
 <span data-ttu-id="20095-106">podczas Token docelowego atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="20095-106">[in] The token of the target custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="20095-107">podczas Wskaźnik do tablicy zawierającej atrybut niestandardowy.</span><span class="sxs-lookup"><span data-stu-id="20095-107">[in] A pointer to the array that contains the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="20095-108">podczas Rozmiar atrybutu niestandardowego w bajtach.</span><span class="sxs-lookup"><span data-stu-id="20095-108">[in] The size, in bytes, of the custom attribute.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20095-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="20095-109">Requirements</span></span>  
 <span data-ttu-id="20095-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20095-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20095-111">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="20095-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="20095-112">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="20095-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="20095-113">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20095-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20095-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="20095-114">See also</span></span>

- [<span data-ttu-id="20095-115">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="20095-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="20095-116">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="20095-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
