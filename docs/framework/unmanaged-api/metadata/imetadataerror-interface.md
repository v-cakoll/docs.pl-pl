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
ms.openlocfilehash: 1c264bfd31f8cd31bacf2d194ddbd07338569294
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447173"
---
# <a name="imetadataerror-interface"></a><span data-ttu-id="f82d5-102">IMetaDataError — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f82d5-102">IMetaDataError Interface</span></span>
<span data-ttu-id="f82d5-103">Udostępnia mechanizm wywołania zwrotnego dla usługi raportowania błędów podczas scalania metadanych.</span><span class="sxs-lookup"><span data-stu-id="f82d5-103">Provides a callback mechanism for reporting errors during the metadata merge.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f82d5-104">`IMetaDataError` Interfejs musi być implementowana przez klienta.</span><span class="sxs-lookup"><span data-stu-id="f82d5-104">The `IMetaDataError` interface must be implemented by the client.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f82d5-105">Metody</span><span class="sxs-lookup"><span data-stu-id="f82d5-105">Methods</span></span>  
  
|<span data-ttu-id="f82d5-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="f82d5-106">Method</span></span>|<span data-ttu-id="f82d5-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f82d5-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f82d5-108">OnError, metoda</span><span class="sxs-lookup"><span data-stu-id="f82d5-108">OnError Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-onerror-method.md)|<span data-ttu-id="f82d5-109">Zapewnia powiadomienie błędów występujących podczas scalania metadanych.</span><span class="sxs-lookup"><span data-stu-id="f82d5-109">Provides notification of errors that occur during the metadata merge.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f82d5-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f82d5-110">Requirements</span></span>  
 <span data-ttu-id="f82d5-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f82d5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f82d5-112">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f82d5-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f82d5-113">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f82d5-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f82d5-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f82d5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f82d5-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f82d5-115">See Also</span></span>  
 [<span data-ttu-id="f82d5-116">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="f82d5-116">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
