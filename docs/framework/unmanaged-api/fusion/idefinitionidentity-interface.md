---
title: IDefinitionIdentity — Interfejs
ms.date: 03/30/2017
api_name:
- IDefinitionIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDefinitionIdentity
helpviewer_keywords:
- IDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: ce5ba888-5fbe-4efd-91cf-f0ff94d8428b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84c595bfdcca84ee43a53e2ea913cc978ae0953e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796526"
---
# <a name="idefinitionidentity-interface"></a><span data-ttu-id="8e71a-102">IDefinitionIdentity — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8e71a-102">IDefinitionIdentity Interface</span></span>
<span data-ttu-id="8e71a-103">Reprezentuje unikatowy podpis kodu, który definiuje aplikację w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="8e71a-103">Represents the unique signature of the code that defines the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8e71a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8e71a-104">Methods</span></span>  
  
|<span data-ttu-id="8e71a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8e71a-105">Method</span></span>|<span data-ttu-id="8e71a-106">Opis</span><span class="sxs-lookup"><span data-stu-id="8e71a-106">Description</span></span>|  
|------------|-----------------|  
|`IDefinitionIdentity::Clone`|<span data-ttu-id="8e71a-107">Pobiera wskaźnik interfejsu do nowego `IDefinitionIdentity` obiektu, który jest identyczny z tym `IDefinitionIdentity`, z wyjątkiem określonych zmian atrybutów.</span><span class="sxs-lookup"><span data-stu-id="8e71a-107">Gets an interface pointer to a new `IDefinitionIdentity` object that is identical to this `IDefinitionIdentity`, except for the specified attribute changes.</span></span>|  
|`IDefinitionIdentity::EnumAttributes`|<span data-ttu-id="8e71a-108">Pobiera wskaźnik interfejsu do obiektu [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md) , który zawiera atrybuty skojarzone z tym `IDefinitionIdentity`elementem.</span><span class="sxs-lookup"><span data-stu-id="8e71a-108">Gets an interface pointer to an [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md) object that contains the attributes associated with this `IDefinitionIdentity`.</span></span>|  
|`IDefinitionIdentity::GetAttribute`|<span data-ttu-id="8e71a-109">Pobiera wartość atrybutu o określonej nazwie w określonym obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="8e71a-109">Gets the value of the attribute with the specified name in the specified namespace.</span></span>|  
|`IDefinitionIdentity::SetAttribute`|<span data-ttu-id="8e71a-110">Ustawia atrybut, który ma określoną nazwę w określonym obszarze nazw do określonej wartości.</span><span class="sxs-lookup"><span data-stu-id="8e71a-110">Sets the attribute that has the specified name in the specified namespace to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8e71a-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8e71a-111">Requirements</span></span>  
 <span data-ttu-id="8e71a-112">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e71a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e71a-113">**Nagłówki** Izolacja. h</span><span class="sxs-lookup"><span data-stu-id="8e71a-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="8e71a-114">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e71a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e71a-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8e71a-115">See also</span></span>

- [<span data-ttu-id="8e71a-116">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="8e71a-116">Fusion Interfaces</span></span>](fusion-interfaces.md)
