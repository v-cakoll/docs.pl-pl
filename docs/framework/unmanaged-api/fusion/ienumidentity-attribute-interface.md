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
ms.openlocfilehash: 7e6bc57fb470a5c12549bb5f9445ecf1551425a4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107842"
---
# <a name="ienumidentity_attribute-interface"></a><span data-ttu-id="dcc35-102">IEnumIDENTITY_ATTRIBUTE — Interfejs</span><span class="sxs-lookup"><span data-stu-id="dcc35-102">IEnumIDENTITY_ATTRIBUTE Interface</span></span>
<span data-ttu-id="dcc35-103">Służy jako moduł wyliczający dla atrybutów obiektu kodu w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="dcc35-103">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dcc35-104">Metody</span><span class="sxs-lookup"><span data-stu-id="dcc35-104">Methods</span></span>  
  
|<span data-ttu-id="dcc35-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="dcc35-105">Method</span></span>|<span data-ttu-id="dcc35-106">Opis</span><span class="sxs-lookup"><span data-stu-id="dcc35-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumIDENTITY_ATTRIBUTE::Clone`|<span data-ttu-id="dcc35-107">Pobiera wskaźnik interfejsu do nowego `IEnumIDENTITY_ATTRIBUTE`, który zawiera te same elementy członkowskie co ten `IEnumIDENTITY_ATTRIBUTE`.</span><span class="sxs-lookup"><span data-stu-id="dcc35-107">Gets an interface pointer to a new `IEnumIDENTITY_ATTRIBUTE` that contains the same members as this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer`|<span data-ttu-id="dcc35-108">Zapisuje dane zawarte w elementach tego `IEnumIDENTITY_ATTRIBUTE` do określonego buforu danych.</span><span class="sxs-lookup"><span data-stu-id="dcc35-108">Writes the data contained in the elements of this `IEnumIDENTITY_ATTRIBUTE` to the specified data buffer.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Next`|<span data-ttu-id="dcc35-109">Pobiera określoną liczbę atrybutów, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="dcc35-109">Gets the specified number of attributes, starting at the current position.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Reset`|<span data-ttu-id="dcc35-110">Przenosi wskaźnik instrukcji na początek tego `IEnumIDENTITY_ATTRIBUTE`.</span><span class="sxs-lookup"><span data-stu-id="dcc35-110">Moves the instruction pointer to the beginning of this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Skip`|<span data-ttu-id="dcc35-111">Przesuwa wskaźnik instrukcji do przodu o określoną liczbę elementów, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="dcc35-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dcc35-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dcc35-112">Requirements</span></span>  
 <span data-ttu-id="dcc35-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcc35-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcc35-114">**Nagłówek:** Izolacja. h</span><span class="sxs-lookup"><span data-stu-id="dcc35-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="dcc35-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcc35-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcc35-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dcc35-116">See also</span></span>

- [<span data-ttu-id="dcc35-117">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="dcc35-117">Fusion Interfaces</span></span>](fusion-interfaces.md)
