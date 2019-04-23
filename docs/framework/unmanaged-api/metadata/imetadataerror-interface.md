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
ms.openlocfilehash: 37f1f6055ec8fa68fe804780d2893d20c978e6bd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59188633"
---
# <a name="imetadataerror-interface"></a><span data-ttu-id="5864c-102">IMetaDataError — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5864c-102">IMetaDataError Interface</span></span>
<span data-ttu-id="5864c-103">Udostępnia mechanizm wywołania zwrotnego dla raportowania błędów podczas scalania metadanych.</span><span class="sxs-lookup"><span data-stu-id="5864c-103">Provides a callback mechanism for reporting errors during the metadata merge.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5864c-104">`IMetaDataError` Interfejsu muszą być zaimplementowane przez klienta.</span><span class="sxs-lookup"><span data-stu-id="5864c-104">The `IMetaDataError` interface must be implemented by the client.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5864c-105">Metody</span><span class="sxs-lookup"><span data-stu-id="5864c-105">Methods</span></span>  
  
|<span data-ttu-id="5864c-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="5864c-106">Method</span></span>|<span data-ttu-id="5864c-107">Opis</span><span class="sxs-lookup"><span data-stu-id="5864c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5864c-108">OnError, metoda</span><span class="sxs-lookup"><span data-stu-id="5864c-108">OnError Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-onerror-method.md)|<span data-ttu-id="5864c-109">Zapewnia powiadomienie błędów występujących podczas scalania metadanych.</span><span class="sxs-lookup"><span data-stu-id="5864c-109">Provides notification of errors that occur during the metadata merge.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5864c-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5864c-110">Requirements</span></span>  
 <span data-ttu-id="5864c-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5864c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5864c-112">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="5864c-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5864c-113">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5864c-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5864c-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5864c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5864c-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5864c-115">See also</span></span>

- [<span data-ttu-id="5864c-116">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="5864c-116">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
