---
title: IDefinitionAppId — Interfejs
ms.date: 03/30/2017
api_name:
- IDefinitionAppId
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDefinitionAppId
helpviewer_keywords:
- IDefinitionAppId interface [.NET Framework fusion]
ms.assetid: e72f2550-bdec-4a20-a2f4-2e14847266c1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4e8bb31967a6ad515761e6cd03657f2c834debe5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54545559"
---
# <a name="idefinitionappid-interface"></a><span data-ttu-id="5299b-102">IDefinitionAppId — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5299b-102">IDefinitionAppId Interface</span></span>
<span data-ttu-id="5299b-103">Reprezentuje unikatowy identyfikator dla kodu, który definiuje aplikacji w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="5299b-103">Represents a unique identifier for the code that defines the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5299b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5299b-104">Methods</span></span>  
  
|<span data-ttu-id="5299b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="5299b-105">Method</span></span>|<span data-ttu-id="5299b-106">Opis</span><span class="sxs-lookup"><span data-stu-id="5299b-106">Description</span></span>|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|<span data-ttu-id="5299b-107">Pobiera ciąg formatowania, która przedstawia kod w tym `IDefinitionAppId` obiektu.</span><span class="sxs-lookup"><span data-stu-id="5299b-107">Gets a formatted string that represents the code in this `IDefinitionAppId` object.</span></span>|  
|`IDefinitionAppId::put_Codebase`|<span data-ttu-id="5299b-108">Ustawia kod to `IDefinitionAppId` wartość ciągu sformatowaną jak określony obiekt.</span><span class="sxs-lookup"><span data-stu-id="5299b-108">Sets the code of this `IDefinitionAppId` object to the specified formatted string value.</span></span>|  
|`IDefinitionAppId::EnumAppPath`|<span data-ttu-id="5299b-109">Pobiera wskaźnik interfejsu do [ienumdefinitionidentity —](../../../../docs/framework/unmanaged-api/fusion/ienumdefinitionidentity-interface.md) obiekt, który zawiera zestawów w bieżącej ścieżce aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5299b-109">Gets an interface pointer to an [IEnumDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/ienumdefinitionidentity-interface.md) object that contains the assemblies in the current application path.</span></span>|  
|`IDefinitionAppId::SetAppPath`|<span data-ttu-id="5299b-110">Ustawia ścieżkę aplikacji dla zestawu w bieżącym zakresie wartości odwołuje się określony [idefinitionidentity —](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="5299b-110">Sets the application path for the assembly in the current scope to the value referenced by the specified [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) object.</span></span>|  
|`IDefinitionAppId::get_SubscriptionId`|<span data-ttu-id="5299b-111">Pobiera wskaźnik do reprezentację ciągu identyfikatora tokenu dla subskrypcji w tym `IDefinitionAppId` obiektu.</span><span class="sxs-lookup"><span data-stu-id="5299b-111">Gets a pointer to a string representation of the token identifier for a subscription to this `IDefinitionAppId` object.</span></span>|  
|`IDefinitionAppId::put_SubscriptionId`|<span data-ttu-id="5299b-112">Ustawia token identyfikator subskrypcji to `IDefinitionAppId` obiektu określona wartość ciągu.</span><span class="sxs-lookup"><span data-stu-id="5299b-112">Sets the token identifier for a subscription to this `IDefinitionAppId` object to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5299b-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5299b-113">Requirements</span></span>  
 <span data-ttu-id="5299b-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5299b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5299b-115">**Nagłówek:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="5299b-115">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="5299b-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5299b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5299b-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5299b-117">See also</span></span>
- [<span data-ttu-id="5299b-118">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="5299b-118">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
