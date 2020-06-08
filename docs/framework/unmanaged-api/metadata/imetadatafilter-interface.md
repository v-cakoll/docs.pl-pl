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
ms.openlocfilehash: 821936d20a421739e8eb3d5df228888df7f022e3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503799"
---
# <a name="imetadatafilter-interface"></a><span data-ttu-id="b19db-102">IMetaDataFilter — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b19db-102">IMetaDataFilter Interface</span></span>
<span data-ttu-id="b19db-103">Zapewnia metody oznaczania i filtrowania tokenów metadanych, aby uniknąć powtarzających się akcji, które zostały już wykonane.</span><span class="sxs-lookup"><span data-stu-id="b19db-103">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b19db-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b19db-104">Methods</span></span>  
  
|<span data-ttu-id="b19db-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b19db-105">Method</span></span>|<span data-ttu-id="b19db-106">Opis</span><span class="sxs-lookup"><span data-stu-id="b19db-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b19db-107">IsTokenMarked — Metoda</span><span class="sxs-lookup"><span data-stu-id="b19db-107">IsTokenMarked Method</span></span>](imetadatafilter-istokenmarked-method.md)|<span data-ttu-id="b19db-108">Pobiera wartość wskazującą, czy określony token metadanych został przetworzony.</span><span class="sxs-lookup"><span data-stu-id="b19db-108">Gets a value indicating whether the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="b19db-109">MarkToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="b19db-109">MarkToken Method</span></span>](imetadatafilter-marktoken-method.md)|<span data-ttu-id="b19db-110">Ustawia wartość wskazującą, że określony token metadanych został przetworzony.</span><span class="sxs-lookup"><span data-stu-id="b19db-110">Sets a value indicating that the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="b19db-111">UnmarkAll — Metoda</span><span class="sxs-lookup"><span data-stu-id="b19db-111">UnmarkAll Method</span></span>](imetadatafilter-unmarkall-method.md)|<span data-ttu-id="b19db-112">Usuwa znaczniki przetwarzania ze wszystkich tokenów w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="b19db-112">Removes the processing marks from all the tokens in the current metadata scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b19db-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b19db-113">Requirements</span></span>  
 <span data-ttu-id="b19db-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b19db-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b19db-115">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b19db-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b19db-116">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b19db-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b19db-117">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b19db-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b19db-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b19db-118">See also</span></span>

- [<span data-ttu-id="b19db-119">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="b19db-119">Metadata Interfaces</span></span>](metadata-interfaces.md)
