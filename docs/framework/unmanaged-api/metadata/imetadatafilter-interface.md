---
title: "IMetaDataFilter — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataFilter
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataFilter
helpviewer_keywords: IMetaDataFilter interface [.NET Framework metadata]
ms.assetid: ec0856ef-8c56-40ba-bf60-86e0ce8b337f
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7c0afbb9be9af3ffe69ddfcac85b70de53a391ae
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="imetadatafilter-interface"></a><span data-ttu-id="405a4-102">IMetaDataFilter — Interfejs</span><span class="sxs-lookup"><span data-stu-id="405a4-102">IMetaDataFilter Interface</span></span>
<span data-ttu-id="405a4-103">Udostępnia metody dla oznaczenie i Filtrowanie tokenów metadanych, aby uniknąć powtarzania działania, które zostały już wykonane.</span><span class="sxs-lookup"><span data-stu-id="405a4-103">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="405a4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="405a4-104">Methods</span></span>  
  
|<span data-ttu-id="405a4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="405a4-105">Method</span></span>|<span data-ttu-id="405a4-106">Opis</span><span class="sxs-lookup"><span data-stu-id="405a4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="405a4-107">IsTokenMarked — metoda</span><span class="sxs-lookup"><span data-stu-id="405a4-107">IsTokenMarked Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-istokenmarked-method.md)|<span data-ttu-id="405a4-108">Pobiera wartość wskazującą, czy token określonych metadanych została przetworzona.</span><span class="sxs-lookup"><span data-stu-id="405a4-108">Gets a value indicating whether the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="405a4-109">MarkToken — metoda</span><span class="sxs-lookup"><span data-stu-id="405a4-109">MarkToken Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-marktoken-method.md)|<span data-ttu-id="405a4-110">Ustawia wartość wskazującą przetworzeniu token określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="405a4-110">Sets a value indicating that the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="405a4-111">UnmarkAll — metoda</span><span class="sxs-lookup"><span data-stu-id="405a4-111">UnmarkAll Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-unmarkall-method.md)|<span data-ttu-id="405a4-112">Usuwa znaczniki przetwarzania z wszystkich tokenów w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="405a4-112">Removes the processing marks from all the tokens in the current metadata scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="405a4-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="405a4-113">Requirements</span></span>  
 <span data-ttu-id="405a4-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="405a4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="405a4-115">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="405a4-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="405a4-116">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="405a4-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="405a4-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="405a4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="405a4-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="405a4-118">See Also</span></span>  
 [<span data-ttu-id="405a4-119">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="405a4-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
