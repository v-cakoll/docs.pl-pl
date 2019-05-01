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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4196ff2cb2d4ebc401076f603a8a7fdc9b9c76ea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049963"
---
# <a name="imetadatafilter-interface"></a><span data-ttu-id="bac72-102">IMetaDataFilter — Interfejs</span><span class="sxs-lookup"><span data-stu-id="bac72-102">IMetaDataFilter Interface</span></span>
<span data-ttu-id="bac72-103">Zawiera metody służące do oznaczenia i filtrowanie tokeny metadanych, aby uniknąć powtarzania czynności, które już zostały podjęte.</span><span class="sxs-lookup"><span data-stu-id="bac72-103">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bac72-104">Metody</span><span class="sxs-lookup"><span data-stu-id="bac72-104">Methods</span></span>  
  
|<span data-ttu-id="bac72-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="bac72-105">Method</span></span>|<span data-ttu-id="bac72-106">Opis</span><span class="sxs-lookup"><span data-stu-id="bac72-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bac72-107">IsTokenMarked, metoda</span><span class="sxs-lookup"><span data-stu-id="bac72-107">IsTokenMarked Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-istokenmarked-method.md)|<span data-ttu-id="bac72-108">Pobiera wartość wskazującą, czy token określonych metadanych została przetworzona.</span><span class="sxs-lookup"><span data-stu-id="bac72-108">Gets a value indicating whether the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="bac72-109">MarkToken, metoda</span><span class="sxs-lookup"><span data-stu-id="bac72-109">MarkToken Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-marktoken-method.md)|<span data-ttu-id="bac72-110">Ustawia wartość wskazującą, przetworzeniu token określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="bac72-110">Sets a value indicating that the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="bac72-111">UnmarkAll, metoda</span><span class="sxs-lookup"><span data-stu-id="bac72-111">UnmarkAll Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-unmarkall-method.md)|<span data-ttu-id="bac72-112">Usuwa znaki przetwarzania z wszystkich tokenów w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="bac72-112">Removes the processing marks from all the tokens in the current metadata scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bac72-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bac72-113">Requirements</span></span>  
 <span data-ttu-id="bac72-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bac72-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bac72-115">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="bac72-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bac72-116">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bac72-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bac72-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bac72-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bac72-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bac72-118">See also</span></span>

- [<span data-ttu-id="bac72-119">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="bac72-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
