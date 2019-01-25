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
ms.openlocfilehash: fb97c545d2d57ef589b5a7a5b3618eaa2b6f364f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54687001"
---
# <a name="idefinitionidentity-interface"></a><span data-ttu-id="ed3f4-102">IDefinitionIdentity — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ed3f4-102">IDefinitionIdentity Interface</span></span>
<span data-ttu-id="ed3f4-103">Reprezentuje unikatowy podpis kodu, który definiuje aplikacji w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="ed3f4-103">Represents the unique signature of the code that defines the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ed3f4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ed3f4-104">Methods</span></span>  
  
|<span data-ttu-id="ed3f4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ed3f4-105">Method</span></span>|<span data-ttu-id="ed3f4-106">Opis</span><span class="sxs-lookup"><span data-stu-id="ed3f4-106">Description</span></span>|  
|------------|-----------------|  
|`IDefinitionIdentity::Clone`|<span data-ttu-id="ed3f4-107">Pobiera wskaźnik interfejsu do nowego `IDefinitionIdentity` obiektu, który jest identyczny z tym `IDefinitionIdentity`, z wyjątkiem zmiany określonego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="ed3f4-107">Gets an interface pointer to a new `IDefinitionIdentity` object that is identical to this `IDefinitionIdentity`, except for the specified attribute changes.</span></span>|  
|`IDefinitionIdentity::EnumAttributes`|<span data-ttu-id="ed3f4-108">Pobiera wskaźnik interfejsu do [ienumidentity_attribute —](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md) obiekt, który zawiera atrybuty skojarzone z tym `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="ed3f4-108">Gets an interface pointer to an [IEnumIDENTITY_ATTRIBUTE](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md) object that contains the attributes associated with this `IDefinitionIdentity`.</span></span>|  
|`IDefinitionIdentity::GetAttribute`|<span data-ttu-id="ed3f4-109">Pobiera wartość atrybutu o określonej nazwie w określonej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ed3f4-109">Gets the value of the attribute with the specified name in the specified namespace.</span></span>|  
|`IDefinitionIdentity::SetAttribute`|<span data-ttu-id="ed3f4-110">Ustawia atrybut, który ma określoną nazwę w określonej przestrzeni nazw z podaną wartością.</span><span class="sxs-lookup"><span data-stu-id="ed3f4-110">Sets the attribute that has the specified name in the specified namespace to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ed3f4-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ed3f4-111">Requirements</span></span>  
 <span data-ttu-id="ed3f4-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed3f4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed3f4-113">**Nagłówek:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="ed3f4-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="ed3f4-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed3f4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed3f4-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ed3f4-115">See also</span></span>
- [<span data-ttu-id="ed3f4-116">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="ed3f4-116">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
