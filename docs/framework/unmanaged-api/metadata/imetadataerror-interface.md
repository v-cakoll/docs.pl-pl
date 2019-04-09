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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59188633"
---
# <a name="imetadataerror-interface"></a><span data-ttu-id="f4e26-102">IMetaDataError — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f4e26-102">IMetaDataError Interface</span></span>
<span data-ttu-id="f4e26-103">Udostępnia mechanizm wywołania zwrotnego dla raportowania błędów podczas scalania metadanych.</span><span class="sxs-lookup"><span data-stu-id="f4e26-103">Provides a callback mechanism for reporting errors during the metadata merge.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f4e26-104">`IMetaDataError` Interfejsu muszą być zaimplementowane przez klienta.</span><span class="sxs-lookup"><span data-stu-id="f4e26-104">The `IMetaDataError` interface must be implemented by the client.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f4e26-105">Metody</span><span class="sxs-lookup"><span data-stu-id="f4e26-105">Methods</span></span>  
  
|<span data-ttu-id="f4e26-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="f4e26-106">Method</span></span>|<span data-ttu-id="f4e26-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f4e26-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f4e26-108">OnError, metoda</span><span class="sxs-lookup"><span data-stu-id="f4e26-108">OnError Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-onerror-method.md)|<span data-ttu-id="f4e26-109">Zapewnia powiadomienie błędów występujących podczas scalania metadanych.</span><span class="sxs-lookup"><span data-stu-id="f4e26-109">Provides notification of errors that occur during the metadata merge.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f4e26-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f4e26-110">Requirements</span></span>  
 <span data-ttu-id="f4e26-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4e26-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4e26-112">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="f4e26-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f4e26-113">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f4e26-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="f4e26-114">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="f4e26-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f4e26-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f4e26-115">See also</span></span>

- [<span data-ttu-id="f4e26-116">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="f4e26-116">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
