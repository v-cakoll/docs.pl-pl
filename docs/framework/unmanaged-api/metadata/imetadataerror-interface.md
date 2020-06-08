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
ms.openlocfilehash: 46370da4e61dc90f2386170745da4f95ac7de63b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492775"
---
# <a name="imetadataerror-interface"></a><span data-ttu-id="f3cb6-102">IMetaDataError — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f3cb6-102">IMetaDataError Interface</span></span>
<span data-ttu-id="f3cb6-103">Zapewnia mechanizm wywołania zwrotnego do raportowania błędów podczas scalania metadanych.</span><span class="sxs-lookup"><span data-stu-id="f3cb6-103">Provides a callback mechanism for reporting errors during the metadata merge.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f3cb6-104">`IMetaDataError`Interfejs musi być zaimplementowany przez klienta.</span><span class="sxs-lookup"><span data-stu-id="f3cb6-104">The `IMetaDataError` interface must be implemented by the client.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f3cb6-105">Metody</span><span class="sxs-lookup"><span data-stu-id="f3cb6-105">Methods</span></span>  
  
|<span data-ttu-id="f3cb6-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="f3cb6-106">Method</span></span>|<span data-ttu-id="f3cb6-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f3cb6-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f3cb6-108">OnError — Metoda</span><span class="sxs-lookup"><span data-stu-id="f3cb6-108">OnError Method</span></span>](imetadataerror-onerror-method.md)|<span data-ttu-id="f3cb6-109">Zawiera powiadomienie o błędach występujących podczas scalania metadanych.</span><span class="sxs-lookup"><span data-stu-id="f3cb6-109">Provides notification of errors that occur during the metadata merge.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f3cb6-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f3cb6-110">Requirements</span></span>  
 <span data-ttu-id="f3cb6-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3cb6-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3cb6-112">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f3cb6-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f3cb6-113">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f3cb6-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f3cb6-114">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3cb6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3cb6-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f3cb6-115">See also</span></span>

- [<span data-ttu-id="f3cb6-116">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="f3cb6-116">Metadata Interfaces</span></span>](metadata-interfaces.md)
