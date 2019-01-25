---
title: IMetaDataError — Interfejs
ms.date: 03/30/2017
api_name:
- IMetaDataError
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataError
helpviewer_keywords:
- IMetaDataError interface [.NET Framework metadata]
ms.assetid: 0020b62c-ea88-40c7-a9ee-16b064f81624
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fe2f683ae46d1ee6205f97536976a358e86fc53d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720382"
---
# <a name="imetadataerror-interface"></a><span data-ttu-id="5cf20-102">IMetaDataError — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5cf20-102">IMetaDataError Interface</span></span>
<span data-ttu-id="5cf20-103">Udostępnia mechanizm wywołania zwrotnego dla raportowania błędów podczas scalania metadanych.</span><span class="sxs-lookup"><span data-stu-id="5cf20-103">Provides a callback mechanism for reporting errors during the metadata merge.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5cf20-104">`IMetaDataError` Interfejsu muszą być zaimplementowane przez klienta.</span><span class="sxs-lookup"><span data-stu-id="5cf20-104">The `IMetaDataError` interface must be implemented by the client.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5cf20-105">Metody</span><span class="sxs-lookup"><span data-stu-id="5cf20-105">Methods</span></span>  
  
|<span data-ttu-id="5cf20-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="5cf20-106">Method</span></span>|<span data-ttu-id="5cf20-107">Opis</span><span class="sxs-lookup"><span data-stu-id="5cf20-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5cf20-108">OnError, metoda</span><span class="sxs-lookup"><span data-stu-id="5cf20-108">OnError Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-onerror-method.md)|<span data-ttu-id="5cf20-109">Zapewnia powiadomienie błędów występujących podczas scalania metadanych.</span><span class="sxs-lookup"><span data-stu-id="5cf20-109">Provides notification of errors that occur during the metadata merge.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5cf20-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5cf20-110">Requirements</span></span>  
 <span data-ttu-id="5cf20-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5cf20-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cf20-112">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="5cf20-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5cf20-113">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5cf20-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5cf20-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cf20-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cf20-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5cf20-115">See also</span></span>
- [<span data-ttu-id="5cf20-116">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="5cf20-116">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
