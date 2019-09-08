---
title: IEnumIDENTITY_ATTRIBUTE — Interfejs
ms.date: 03/30/2017
api_name:
- IEnumIDENTITY_ATTRIBUTE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumIDENTITY_ATTRIBUTE
helpviewer_keywords:
- IEnumIDENTITY_ATTRIBUTE interface [.NET Framework fusion]
ms.assetid: c2ec2748-e9ae-4e1b-80db-6fcec5cb81a1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dbb3ac150ebfe9fe3698427d8bb2bfb3e3347c07
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796466"
---
# <a name="ienumidentity_attribute-interface"></a><span data-ttu-id="06db5-102">IEnumIDENTITY_ATTRIBUTE — Interfejs</span><span class="sxs-lookup"><span data-stu-id="06db5-102">IEnumIDENTITY_ATTRIBUTE Interface</span></span>
<span data-ttu-id="06db5-103">Służy jako moduł wyliczający dla atrybutów obiektu kodu w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="06db5-103">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="06db5-104">Metody</span><span class="sxs-lookup"><span data-stu-id="06db5-104">Methods</span></span>  
  
|<span data-ttu-id="06db5-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="06db5-105">Method</span></span>|<span data-ttu-id="06db5-106">Opis</span><span class="sxs-lookup"><span data-stu-id="06db5-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumIDENTITY_ATTRIBUTE::Clone`|<span data-ttu-id="06db5-107">Pobiera wskaźnik interfejsu do nowego `IEnumIDENTITY_ATTRIBUTE` , który zawiera te same składowe. `IEnumIDENTITY_ATTRIBUTE`</span><span class="sxs-lookup"><span data-stu-id="06db5-107">Gets an interface pointer to a new `IEnumIDENTITY_ATTRIBUTE` that contains the same members as this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer`|<span data-ttu-id="06db5-108">Zapisuje dane zawarte w elementach tego `IEnumIDENTITY_ATTRIBUTE` obiektu do określonego buforu danych.</span><span class="sxs-lookup"><span data-stu-id="06db5-108">Writes the data contained in the elements of this `IEnumIDENTITY_ATTRIBUTE` to the specified data buffer.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Next`|<span data-ttu-id="06db5-109">Pobiera określoną liczbę atrybutów, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="06db5-109">Gets the specified number of attributes, starting at the current position.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Reset`|<span data-ttu-id="06db5-110">Przenosi wskaźnik instrukcji na początek tego `IEnumIDENTITY_ATTRIBUTE`elementu.</span><span class="sxs-lookup"><span data-stu-id="06db5-110">Moves the instruction pointer to the beginning of this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Skip`|<span data-ttu-id="06db5-111">Przesuwa wskaźnik instrukcji do przodu o określoną liczbę elementów, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="06db5-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="06db5-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="06db5-112">Requirements</span></span>  
 <span data-ttu-id="06db5-113">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06db5-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06db5-114">**Nagłówki** Izolacja. h</span><span class="sxs-lookup"><span data-stu-id="06db5-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="06db5-115">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06db5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06db5-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="06db5-116">See also</span></span>

- [<span data-ttu-id="06db5-117">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="06db5-117">Fusion Interfaces</span></span>](fusion-interfaces.md)
