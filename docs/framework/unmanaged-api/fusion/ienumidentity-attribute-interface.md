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
ms.openlocfilehash: da6462a320b1f090940473f566ade91d36e74780
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ienumidentityattribute-interface"></a><span data-ttu-id="bb45d-102">IEnumIDENTITY_ATTRIBUTE — Interfejs</span><span class="sxs-lookup"><span data-stu-id="bb45d-102">IEnumIDENTITY_ATTRIBUTE Interface</span></span>
<span data-ttu-id="bb45d-103">Służy jako moduł wyliczający dla atrybutów obiektu kodu w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="bb45d-103">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bb45d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="bb45d-104">Methods</span></span>  
  
|<span data-ttu-id="bb45d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="bb45d-105">Method</span></span>|<span data-ttu-id="bb45d-106">Opis</span><span class="sxs-lookup"><span data-stu-id="bb45d-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumIDENTITY_ATTRIBUTE::Clone`|<span data-ttu-id="bb45d-107">Pobiera wskaźnika interfejsu na nowy `IEnumIDENTITY_ATTRIBUTE` zawierający członkowie to `IEnumIDENTITY_ATTRIBUTE`.</span><span class="sxs-lookup"><span data-stu-id="bb45d-107">Gets an interface pointer to a new `IEnumIDENTITY_ATTRIBUTE` that contains the same members as this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer`|<span data-ttu-id="bb45d-108">Zapisuje dane zawarte w elementach to `IEnumIDENTITY_ATTRIBUTE` w buforze określone dane.</span><span class="sxs-lookup"><span data-stu-id="bb45d-108">Writes the data contained in the elements of this `IEnumIDENTITY_ATTRIBUTE` to the specified data buffer.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Next`|<span data-ttu-id="bb45d-109">Pobiera określoną liczbę atrybutów, zaczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="bb45d-109">Gets the specified number of attributes, starting at the current position.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Reset`|<span data-ttu-id="bb45d-110">Przesuwa wskaźnik instrukcji na początku `IEnumIDENTITY_ATTRIBUTE`.</span><span class="sxs-lookup"><span data-stu-id="bb45d-110">Moves the instruction pointer to the beginning of this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Skip`|<span data-ttu-id="bb45d-111">Przenosi do przodu wskaźnik instrukcji przez określoną liczbę elementów, licząc w bieżącym położeniu.</span><span class="sxs-lookup"><span data-stu-id="bb45d-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bb45d-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bb45d-112">Requirements</span></span>  
 <span data-ttu-id="bb45d-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb45d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb45d-114">**Nagłówek:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="bb45d-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="bb45d-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb45d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb45d-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bb45d-116">See Also</span></span>  
 [<span data-ttu-id="bb45d-117">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="bb45d-117">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
