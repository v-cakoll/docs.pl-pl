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
ms.openlocfilehash: 5114f74e80da925c7a153b9e481c54067152eaec
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108198"
---
# <a name="idefinitionappid-interface"></a><span data-ttu-id="dbc3a-102">IDefinitionAppId — Interfejs</span><span class="sxs-lookup"><span data-stu-id="dbc3a-102">IDefinitionAppId Interface</span></span>
<span data-ttu-id="dbc3a-103">Reprezentuje unikatowy identyfikator kodu, który definiuje aplikację w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="dbc3a-103">Represents a unique identifier for the code that defines the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dbc3a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="dbc3a-104">Methods</span></span>  
  
|<span data-ttu-id="dbc3a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="dbc3a-105">Method</span></span>|<span data-ttu-id="dbc3a-106">Opis</span><span class="sxs-lookup"><span data-stu-id="dbc3a-106">Description</span></span>|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|<span data-ttu-id="dbc3a-107">Pobiera sformatowany ciąg, który reprezentuje kod w tym obiekcie `IDefinitionAppId`.</span><span class="sxs-lookup"><span data-stu-id="dbc3a-107">Gets a formatted string that represents the code in this `IDefinitionAppId` object.</span></span>|  
|`IDefinitionAppId::put_Codebase`|<span data-ttu-id="dbc3a-108">Ustawia kod tego obiektu `IDefinitionAppId` na określoną wartość ciągu sformatowanego.</span><span class="sxs-lookup"><span data-stu-id="dbc3a-108">Sets the code of this `IDefinitionAppId` object to the specified formatted string value.</span></span>|  
|`IDefinitionAppId::EnumAppPath`|<span data-ttu-id="dbc3a-109">Pobiera wskaźnik interfejsu do obiektu [IEnumDefinitionIdentity —](ienumdefinitionidentity-interface.md) , który zawiera zestawy w bieżącej ścieżce aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dbc3a-109">Gets an interface pointer to an [IEnumDefinitionIdentity](ienumdefinitionidentity-interface.md) object that contains the assemblies in the current application path.</span></span>|  
|`IDefinitionAppId::SetAppPath`|<span data-ttu-id="dbc3a-110">Ustawia ścieżkę aplikacji dla zestawu w bieżącym zakresie do wartości, do której odwołuje się określony obiekt [IDefinitionIdentity —](idefinitionidentity-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="dbc3a-110">Sets the application path for the assembly in the current scope to the value referenced by the specified [IDefinitionIdentity](idefinitionidentity-interface.md) object.</span></span>|  
|`IDefinitionAppId::get_SubscriptionId`|<span data-ttu-id="dbc3a-111">Pobiera wskaźnik do ciągu reprezentującego Identyfikator tokenu dla subskrypcji dla tego obiektu `IDefinitionAppId`.</span><span class="sxs-lookup"><span data-stu-id="dbc3a-111">Gets a pointer to a string representation of the token identifier for a subscription to this `IDefinitionAppId` object.</span></span>|  
|`IDefinitionAppId::put_SubscriptionId`|<span data-ttu-id="dbc3a-112">Ustawia identyfikator tokenu dla subskrypcji dla tego obiektu `IDefinitionAppId` na określoną wartość ciągu.</span><span class="sxs-lookup"><span data-stu-id="dbc3a-112">Sets the token identifier for a subscription to this `IDefinitionAppId` object to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dbc3a-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dbc3a-113">Requirements</span></span>  
 <span data-ttu-id="dbc3a-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbc3a-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbc3a-115">**Nagłówek:** Izolacja. h</span><span class="sxs-lookup"><span data-stu-id="dbc3a-115">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="dbc3a-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbc3a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbc3a-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dbc3a-117">See also</span></span>

- [<span data-ttu-id="dbc3a-118">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="dbc3a-118">Fusion Interfaces</span></span>](fusion-interfaces.md)
