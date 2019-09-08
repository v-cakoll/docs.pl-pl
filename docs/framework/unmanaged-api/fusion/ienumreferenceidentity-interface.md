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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4c5d4bc1fa82f7623168050f4ee36f0ea3cd171e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796431"
---
# <a name="ienumreferenceidentity-interface"></a><span data-ttu-id="84cf2-102">IEnumReferenceIdentity — Interfejs</span><span class="sxs-lookup"><span data-stu-id="84cf2-102">IEnumReferenceIdentity Interface</span></span>
<span data-ttu-id="84cf2-103">Służy jako moduł wyliczający dla kolekcji `IReferenceIdentity` obiektów.</span><span class="sxs-lookup"><span data-stu-id="84cf2-103">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="84cf2-104">Metody</span><span class="sxs-lookup"><span data-stu-id="84cf2-104">Methods</span></span>  
  
|<span data-ttu-id="84cf2-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="84cf2-105">Method</span></span>|<span data-ttu-id="84cf2-106">Opis</span><span class="sxs-lookup"><span data-stu-id="84cf2-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|<span data-ttu-id="84cf2-107">Pobiera wskaźnik interfejsu do nowego `IEnumReferenceIdentity` , który zawiera te same składowe. `IEnumReferenceIdentity`</span><span class="sxs-lookup"><span data-stu-id="84cf2-107">Gets an interface pointer to a new `IEnumReferenceIdentity` that contains the same members as this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Next`|<span data-ttu-id="84cf2-108">Pobiera określoną liczbę `IReferenceIdentity` obiektów, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="84cf2-108">Gets the specified number of `IReferenceIdentity` objects, starting at the current position.</span></span>|  
|`IEnumReferenceIdentity::Reset`|<span data-ttu-id="84cf2-109">Przenosi wskaźnik instrukcji na początek tego `IEnumReferenceIdentity`elementu.</span><span class="sxs-lookup"><span data-stu-id="84cf2-109">Moves the instruction pointer to the beginning of this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Skip`|<span data-ttu-id="84cf2-110">Przesuwa wskaźnik instrukcji do przodu o określoną liczbę elementów, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="84cf2-110">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="84cf2-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="84cf2-111">Requirements</span></span>  
 <span data-ttu-id="84cf2-112">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84cf2-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84cf2-113">**Nagłówki** Izolacja. h</span><span class="sxs-lookup"><span data-stu-id="84cf2-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="84cf2-114">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84cf2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84cf2-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="84cf2-115">See also</span></span>

- [<span data-ttu-id="84cf2-116">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="84cf2-116">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="84cf2-117">IReferenceIdentity, interfejs</span><span class="sxs-lookup"><span data-stu-id="84cf2-117">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)
