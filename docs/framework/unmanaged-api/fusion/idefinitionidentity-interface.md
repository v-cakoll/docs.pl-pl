---
title: "IDefinitionIdentity — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDefinitionIdentity
api_location: fusion.dll
api_type: COM
f1_keywords: IDefinitionIdentity
helpviewer_keywords: IDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: ce5ba888-5fbe-4efd-91cf-f0ff94d8428b
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a63436f107a2604fd5620854339447a4af254e52
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="idefinitionidentity-interface"></a><span data-ttu-id="c7ca9-102">IDefinitionIdentity — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c7ca9-102">IDefinitionIdentity Interface</span></span>
<span data-ttu-id="c7ca9-103">Reprezentuje podpis unikatowy kod, który definiuje aplikacji w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="c7ca9-103">Represents the unique signature of the code that defines the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c7ca9-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c7ca9-104">Methods</span></span>  
  
|<span data-ttu-id="c7ca9-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c7ca9-105">Method</span></span>|<span data-ttu-id="c7ca9-106">Opis</span><span class="sxs-lookup"><span data-stu-id="c7ca9-106">Description</span></span>|  
|------------|-----------------|  
|`IDefinitionIdentity::Clone`|<span data-ttu-id="c7ca9-107">Pobiera wskaźnika interfejsu na nowy `IDefinitionIdentity` obiekt, który jest taki sam jak to `IDefinitionIdentity`, z wyjątkiem zmiany określonego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="c7ca9-107">Gets an interface pointer to a new `IDefinitionIdentity` object that is identical to this `IDefinitionIdentity`, except for the specified attribute changes.</span></span>|  
|`IDefinitionIdentity::EnumAttributes`|<span data-ttu-id="c7ca9-108">Pobiera wskaźnika interfejsu do [ienumidentity_attribute —](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md) obiekt zawierający atrybuty skojarzone z tym `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="c7ca9-108">Gets an interface pointer to an [IEnumIDENTITY_ATTRIBUTE](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md) object that contains the attributes associated with this `IDefinitionIdentity`.</span></span>|  
|`IDefinitionIdentity::GetAttribute`|<span data-ttu-id="c7ca9-109">Pobiera wartość atrybutu o określonej nazwie w określonej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c7ca9-109">Gets the value of the attribute with the specified name in the specified namespace.</span></span>|  
|`IDefinitionIdentity::SetAttribute`|<span data-ttu-id="c7ca9-110">Ustawia atrybut, który ma określoną nazwę w określonej przestrzeni nazw z podaną wartością.</span><span class="sxs-lookup"><span data-stu-id="c7ca9-110">Sets the attribute that has the specified name in the specified namespace to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c7ca9-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c7ca9-111">Requirements</span></span>  
 <span data-ttu-id="c7ca9-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7ca9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7ca9-113">**Nagłówek:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="c7ca9-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="c7ca9-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7ca9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7ca9-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c7ca9-115">See Also</span></span>  
 [<span data-ttu-id="c7ca9-116">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="c7ca9-116">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
