---
title: IMetaDataFilter — Interfejs
ms.date: 03/30/2017
api_name:
- IMetaDataFilter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter
helpviewer_keywords:
- IMetaDataFilter interface [.NET Framework metadata]
ms.assetid: ec0856ef-8c56-40ba-bf60-86e0ce8b337f
topic_type:
- apiref
ms.openlocfilehash: e8b15f478eb3b94b7cdcab3b69d54e7cc99be13b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440168"
---
# <a name="imetadatafilter-interface"></a><span data-ttu-id="7db92-102">IMetaDataFilter — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7db92-102">IMetaDataFilter Interface</span></span>
<span data-ttu-id="7db92-103">Zapewnia metody oznaczania i filtrowania tokenów metadanych, aby uniknąć powtarzających się akcji, które zostały już wykonane.</span><span class="sxs-lookup"><span data-stu-id="7db92-103">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7db92-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7db92-104">Methods</span></span>  
  
|<span data-ttu-id="7db92-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7db92-105">Method</span></span>|<span data-ttu-id="7db92-106">Opis</span><span class="sxs-lookup"><span data-stu-id="7db92-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7db92-107">IsTokenMarked, metoda</span><span class="sxs-lookup"><span data-stu-id="7db92-107">IsTokenMarked Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-istokenmarked-method.md)|<span data-ttu-id="7db92-108">Pobiera wartość wskazującą, czy określony token metadanych został przetworzony.</span><span class="sxs-lookup"><span data-stu-id="7db92-108">Gets a value indicating whether the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="7db92-109">MarkToken, metoda</span><span class="sxs-lookup"><span data-stu-id="7db92-109">MarkToken Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-marktoken-method.md)|<span data-ttu-id="7db92-110">Ustawia wartość wskazującą, że określony token metadanych został przetworzony.</span><span class="sxs-lookup"><span data-stu-id="7db92-110">Sets a value indicating that the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="7db92-111">UnmarkAll, metoda</span><span class="sxs-lookup"><span data-stu-id="7db92-111">UnmarkAll Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-unmarkall-method.md)|<span data-ttu-id="7db92-112">Usuwa znaczniki przetwarzania ze wszystkich tokenów w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="7db92-112">Removes the processing marks from all the tokens in the current metadata scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7db92-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7db92-113">Requirements</span></span>  
 <span data-ttu-id="7db92-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7db92-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7db92-115">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="7db92-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7db92-116">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7db92-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7db92-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7db92-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7db92-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7db92-118">See also</span></span>

- [<span data-ttu-id="7db92-119">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="7db92-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
