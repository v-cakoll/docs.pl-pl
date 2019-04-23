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
ms.openlocfilehash: d725228f2a7359d415673fdcb90d0cabae1a40be
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59175529"
---
# <a name="ienumidentityattribute-interface"></a><span data-ttu-id="a48eb-102">IEnumIDENTITY_ATTRIBUTE — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a48eb-102">IEnumIDENTITY_ATTRIBUTE Interface</span></span>
<span data-ttu-id="a48eb-103">Służy jako moduł wyliczający dla atrybutów obiektu kodu w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="a48eb-103">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a48eb-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a48eb-104">Methods</span></span>  
  
|<span data-ttu-id="a48eb-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a48eb-105">Method</span></span>|<span data-ttu-id="a48eb-106">Opis</span><span class="sxs-lookup"><span data-stu-id="a48eb-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumIDENTITY_ATTRIBUTE::Clone`|<span data-ttu-id="a48eb-107">Pobiera wskaźnik interfejsu do nowego `IEnumIDENTITY_ATTRIBUTE` zawiera te same elementy członkowskie, ponieważ `IEnumIDENTITY_ATTRIBUTE`.</span><span class="sxs-lookup"><span data-stu-id="a48eb-107">Gets an interface pointer to a new `IEnumIDENTITY_ATTRIBUTE` that contains the same members as this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer`|<span data-ttu-id="a48eb-108">Zapisuje dane zawarte w elementach to `IEnumIDENTITY_ATTRIBUTE` do określonych danych buforu.</span><span class="sxs-lookup"><span data-stu-id="a48eb-108">Writes the data contained in the elements of this `IEnumIDENTITY_ATTRIBUTE` to the specified data buffer.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Next`|<span data-ttu-id="a48eb-109">Pobiera określoną liczbę atrybutów, zaczynając od bieżącej pozycji.</span><span class="sxs-lookup"><span data-stu-id="a48eb-109">Gets the specified number of attributes, starting at the current position.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Reset`|<span data-ttu-id="a48eb-110">Przesuwa wskaźnik instrukcji na początku `IEnumIDENTITY_ATTRIBUTE`.</span><span class="sxs-lookup"><span data-stu-id="a48eb-110">Moves the instruction pointer to the beginning of this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Skip`|<span data-ttu-id="a48eb-111">Przesuwa wskaźnik instrukcji do przodu o określoną liczbę elementów, zaczynając od bieżącej pozycji.</span><span class="sxs-lookup"><span data-stu-id="a48eb-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a48eb-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a48eb-112">Requirements</span></span>  
 <span data-ttu-id="a48eb-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a48eb-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a48eb-114">**Nagłówek:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="a48eb-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="a48eb-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a48eb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a48eb-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a48eb-116">See also</span></span>

- [<span data-ttu-id="a48eb-117">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="a48eb-117">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
