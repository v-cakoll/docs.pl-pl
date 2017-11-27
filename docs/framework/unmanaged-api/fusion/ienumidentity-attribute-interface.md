---
title: "IEnumIDENTITY_ATTRIBUTE — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IEnumIDENTITY_ATTRIBUTE
api_location: fusion.dll
api_type: COM
f1_keywords: IEnumIDENTITY_ATTRIBUTE
helpviewer_keywords: IEnumIDENTITY_ATTRIBUTE interface [.NET Framework fusion]
ms.assetid: c2ec2748-e9ae-4e1b-80db-6fcec5cb81a1
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f88e400556421e0908e0a0b115f66ec3221124c2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ienumidentityattribute-interface"></a><span data-ttu-id="bca3c-102">IEnumIDENTITY_ATTRIBUTE — Interfejs</span><span class="sxs-lookup"><span data-stu-id="bca3c-102">IEnumIDENTITY_ATTRIBUTE Interface</span></span>
<span data-ttu-id="bca3c-103">Służy jako moduł wyliczający dla atrybutów obiektu kodu w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="bca3c-103">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bca3c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="bca3c-104">Methods</span></span>  
  
|<span data-ttu-id="bca3c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="bca3c-105">Method</span></span>|<span data-ttu-id="bca3c-106">Opis</span><span class="sxs-lookup"><span data-stu-id="bca3c-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumIDENTITY_ATTRIBUTE::Clone`|<span data-ttu-id="bca3c-107">Pobiera wskaźnika interfejsu na nowy `IEnumIDENTITY_ATTRIBUTE` zawierający członkowie to `IEnumIDENTITY_ATTRIBUTE`.</span><span class="sxs-lookup"><span data-stu-id="bca3c-107">Gets an interface pointer to a new `IEnumIDENTITY_ATTRIBUTE` that contains the same members as this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer`|<span data-ttu-id="bca3c-108">Zapisuje dane zawarte w elementach to `IEnumIDENTITY_ATTRIBUTE` w buforze określone dane.</span><span class="sxs-lookup"><span data-stu-id="bca3c-108">Writes the data contained in the elements of this `IEnumIDENTITY_ATTRIBUTE` to the specified data buffer.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Next`|<span data-ttu-id="bca3c-109">Pobiera określoną liczbę atrybutów, zaczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="bca3c-109">Gets the specified number of attributes, starting at the current position.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Reset`|<span data-ttu-id="bca3c-110">Przesuwa wskaźnik instrukcji na początku `IEnumIDENTITY_ATTRIBUTE`.</span><span class="sxs-lookup"><span data-stu-id="bca3c-110">Moves the instruction pointer to the beginning of this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Skip`|<span data-ttu-id="bca3c-111">Przenosi do przodu wskaźnik instrukcji przez określoną liczbę elementów, licząc w bieżącym położeniu.</span><span class="sxs-lookup"><span data-stu-id="bca3c-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bca3c-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bca3c-112">Requirements</span></span>  
 <span data-ttu-id="bca3c-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bca3c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bca3c-114">**Nagłówek:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="bca3c-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="bca3c-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bca3c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bca3c-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bca3c-116">See Also</span></span>  
 [<span data-ttu-id="bca3c-117">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="bca3c-117">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
