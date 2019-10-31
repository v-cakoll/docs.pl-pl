---
title: IEnumReferenceIdentity — Interfejs
ms.date: 03/30/2017
api_name:
- IEnumReferenceIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumReferenceIdentity
helpviewer_keywords:
- IEnumReferenceIdentity interface [.NET Framework fusion]
ms.assetid: a17b3155-7216-4e16-8c9f-abce21f549e7
topic_type:
- apiref
ms.openlocfilehash: 1305b9ebe3cd87ba002ee87610ff309d015a44e6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131744"
---
# <a name="ienumreferenceidentity-interface"></a><span data-ttu-id="31c10-102">IEnumReferenceIdentity — Interfejs</span><span class="sxs-lookup"><span data-stu-id="31c10-102">IEnumReferenceIdentity Interface</span></span>
<span data-ttu-id="31c10-103">Służy jako moduł wyliczający dla kolekcji obiektów `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="31c10-103">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="31c10-104">Metody</span><span class="sxs-lookup"><span data-stu-id="31c10-104">Methods</span></span>  
  
|<span data-ttu-id="31c10-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="31c10-105">Method</span></span>|<span data-ttu-id="31c10-106">Opis</span><span class="sxs-lookup"><span data-stu-id="31c10-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|<span data-ttu-id="31c10-107">Pobiera wskaźnik interfejsu do nowego `IEnumReferenceIdentity`, który zawiera te same elementy członkowskie co ten `IEnumReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="31c10-107">Gets an interface pointer to a new `IEnumReferenceIdentity` that contains the same members as this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Next`|<span data-ttu-id="31c10-108">Pobiera określoną liczbę `IReferenceIdentity` obiektów, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="31c10-108">Gets the specified number of `IReferenceIdentity` objects, starting at the current position.</span></span>|  
|`IEnumReferenceIdentity::Reset`|<span data-ttu-id="31c10-109">Przenosi wskaźnik instrukcji na początek tego `IEnumReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="31c10-109">Moves the instruction pointer to the beginning of this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Skip`|<span data-ttu-id="31c10-110">Przesuwa wskaźnik instrukcji do przodu o określoną liczbę elementów, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="31c10-110">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="31c10-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="31c10-111">Requirements</span></span>  
 <span data-ttu-id="31c10-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31c10-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31c10-113">**Nagłówek:** Izolacja. h</span><span class="sxs-lookup"><span data-stu-id="31c10-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="31c10-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31c10-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31c10-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="31c10-115">See also</span></span>

- [<span data-ttu-id="31c10-116">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="31c10-116">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="31c10-117">IReferenceIdentity, interfejs</span><span class="sxs-lookup"><span data-stu-id="31c10-117">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)
