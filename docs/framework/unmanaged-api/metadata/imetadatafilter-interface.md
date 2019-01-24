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
ms.openlocfilehash: 0e1975a5063217299ddbcdce6f625d5a1285d5b4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54642558"
---
# <a name="imetadatafilter-interface"></a><span data-ttu-id="4a236-102">IMetaDataFilter — Interfejs</span><span class="sxs-lookup"><span data-stu-id="4a236-102">IMetaDataFilter Interface</span></span>
<span data-ttu-id="4a236-103">Zawiera metody służące do oznaczenia i filtrowanie tokeny metadanych, aby uniknąć powtarzania czynności, które już zostały podjęte.</span><span class="sxs-lookup"><span data-stu-id="4a236-103">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4a236-104">Metody</span><span class="sxs-lookup"><span data-stu-id="4a236-104">Methods</span></span>  
  
|<span data-ttu-id="4a236-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="4a236-105">Method</span></span>|<span data-ttu-id="4a236-106">Opis</span><span class="sxs-lookup"><span data-stu-id="4a236-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4a236-107">IsTokenMarked, metoda</span><span class="sxs-lookup"><span data-stu-id="4a236-107">IsTokenMarked Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-istokenmarked-method.md)|<span data-ttu-id="4a236-108">Pobiera wartość wskazującą, czy token określonych metadanych została przetworzona.</span><span class="sxs-lookup"><span data-stu-id="4a236-108">Gets a value indicating whether the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="4a236-109">MarkToken, metoda</span><span class="sxs-lookup"><span data-stu-id="4a236-109">MarkToken Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-marktoken-method.md)|<span data-ttu-id="4a236-110">Ustawia wartość wskazującą, przetworzeniu token określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="4a236-110">Sets a value indicating that the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="4a236-111">UnmarkAll, metoda</span><span class="sxs-lookup"><span data-stu-id="4a236-111">UnmarkAll Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-unmarkall-method.md)|<span data-ttu-id="4a236-112">Usuwa znaki przetwarzania z wszystkich tokenów w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="4a236-112">Removes the processing marks from all the tokens in the current metadata scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4a236-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4a236-113">Requirements</span></span>  
 <span data-ttu-id="4a236-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a236-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a236-115">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="4a236-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4a236-116">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4a236-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4a236-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a236-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a236-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4a236-118">See also</span></span>
- [<span data-ttu-id="4a236-119">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="4a236-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
