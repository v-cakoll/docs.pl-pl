---
title: IMetaDataEmit::SetFieldMarshal — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldMarshal
helpviewer_keywords:
- SetFieldMarshal method [.NET Framework metadata]
- IMetaDataEmit::SetFieldMarshal method [.NET Framework metadata]
ms.assetid: be232314-7f69-4855-bfab-63361bd22307
topic_type:
- apiref
ms.openlocfilehash: d0066c6590a9e0cf278e036111c2739f7cfaf679
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84003909"
---
# <a name="imetadataemitsetfieldmarshal-method"></a><span data-ttu-id="7caa3-102">IMetaDataEmit::SetFieldMarshal — Metoda</span><span class="sxs-lookup"><span data-stu-id="7caa3-102">IMetaDataEmit::SetFieldMarshal Method</span></span>
<span data-ttu-id="7caa3-103">Ustawia informacje o kierowaniu PInvoke dla parametru, zwraca metodę lub parametr metody, do którego odwołuje się określony token.</span><span class="sxs-lookup"><span data-stu-id="7caa3-103">Sets the PInvoke marshaling information for the field, method return, or method parameter referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7caa3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7caa3-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldMarshal (  
    [in]  mdToken          tk,
    [in]  PCCOR_SIGNATURE  pvNativeType,
    [in]  ULONG            cbNativeType
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7caa3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7caa3-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="7caa3-106">podczas Token dla docelowego elementu danych.</span><span class="sxs-lookup"><span data-stu-id="7caa3-106">[in] The token for target data item.</span></span> <span data-ttu-id="7caa3-107">Jest to albo `mdFieldDef` `mdParamDef` token.</span><span class="sxs-lookup"><span data-stu-id="7caa3-107">This is either a `mdFieldDef` or a `mdParamDef` token.</span></span>  
  
 `pvNativeType`  
 <span data-ttu-id="7caa3-108">podczas Sygnatura dla typu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="7caa3-108">[in] The signature for unmanaged type.</span></span>  
  
 `cbNativeType`  
 <span data-ttu-id="7caa3-109">podczas Liczba bajtów w `pvNativeType` .</span><span class="sxs-lookup"><span data-stu-id="7caa3-109">[in] The count of bytes in `pvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7caa3-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7caa3-110">Requirements</span></span>  
 <span data-ttu-id="7caa3-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7caa3-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7caa3-112">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="7caa3-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7caa3-113">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7caa3-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7caa3-114">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7caa3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7caa3-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7caa3-115">See also</span></span>

- [<span data-ttu-id="7caa3-116">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7caa3-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="7caa3-117">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="7caa3-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
