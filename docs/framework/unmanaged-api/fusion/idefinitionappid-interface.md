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
ms.openlocfilehash: 2735355097a1f3f581b3a4bc74f08d8f2ebf3bd8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430383"
---
# <a name="idefinitionappid-interface"></a><span data-ttu-id="95a8f-102">IDefinitionAppId — Interfejs</span><span class="sxs-lookup"><span data-stu-id="95a8f-102">IDefinitionAppId Interface</span></span>
<span data-ttu-id="95a8f-103">Reprezentuje unikatowy identyfikator dla kodu, który definiuje aplikacji w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="95a8f-103">Represents a unique identifier for the code that defines the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="95a8f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="95a8f-104">Methods</span></span>  
  
|<span data-ttu-id="95a8f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="95a8f-105">Method</span></span>|<span data-ttu-id="95a8f-106">Opis</span><span class="sxs-lookup"><span data-stu-id="95a8f-106">Description</span></span>|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|<span data-ttu-id="95a8f-107">Pobiera ciąg formatowania, który reprezentuje kod w tym `IDefinitionAppId` obiektu.</span><span class="sxs-lookup"><span data-stu-id="95a8f-107">Gets a formatted string that represents the code in this `IDefinitionAppId` object.</span></span>|  
|`IDefinitionAppId::put_Codebase`|<span data-ttu-id="95a8f-108">Ustawia kod to `IDefinitionAppId` wartość ciągu sformatowaną jak określony obiekt.</span><span class="sxs-lookup"><span data-stu-id="95a8f-108">Sets the code of this `IDefinitionAppId` object to the specified formatted string value.</span></span>|  
|`IDefinitionAppId::EnumAppPath`|<span data-ttu-id="95a8f-109">Pobiera wskaźnika interfejsu do [IEnumDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/ienumdefinitionidentity-interface.md) obiekt, który zawiera zestawy w ścieżce bieżącej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="95a8f-109">Gets an interface pointer to an [IEnumDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/ienumdefinitionidentity-interface.md) object that contains the assemblies in the current application path.</span></span>|  
|`IDefinitionAppId::SetAppPath`|<span data-ttu-id="95a8f-110">Ustawia ścieżkę aplikacji dla zestawu w bieżącym zakresie wartości odwołuje się określony [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="95a8f-110">Sets the application path for the assembly in the current scope to the value referenced by the specified [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) object.</span></span>|  
|`IDefinitionAppId::get_SubscriptionId`|<span data-ttu-id="95a8f-111">Pobiera wskaźnik do reprezentację ciągu identyfikatora tokenu dla tej subskrypcji `IDefinitionAppId` obiektu.</span><span class="sxs-lookup"><span data-stu-id="95a8f-111">Gets a pointer to a string representation of the token identifier for a subscription to this `IDefinitionAppId` object.</span></span>|  
|`IDefinitionAppId::put_SubscriptionId`|<span data-ttu-id="95a8f-112">Ustawia token identyfikator subskrypcji do tego `IDefinitionAppId` obiektu określona wartość ciągu.</span><span class="sxs-lookup"><span data-stu-id="95a8f-112">Sets the token identifier for a subscription to this `IDefinitionAppId` object to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="95a8f-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="95a8f-113">Requirements</span></span>  
 <span data-ttu-id="95a8f-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95a8f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95a8f-115">**Nagłówek:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="95a8f-115">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="95a8f-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95a8f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95a8f-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="95a8f-117">See Also</span></span>  
 [<span data-ttu-id="95a8f-118">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="95a8f-118">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
