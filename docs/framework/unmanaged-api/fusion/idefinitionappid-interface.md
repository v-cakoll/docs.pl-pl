---
title: "IDefinitionAppId — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDefinitionAppId
api_location: fusion.dll
api_type: COM
f1_keywords: IDefinitionAppId
helpviewer_keywords: IDefinitionAppId interface [.NET Framework fusion]
ms.assetid: e72f2550-bdec-4a20-a2f4-2e14847266c1
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 382c82ff773d0ab1c046fc131fa87a4f74d19ea6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="idefinitionappid-interface"></a><span data-ttu-id="9ddd1-102">IDefinitionAppId — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9ddd1-102">IDefinitionAppId Interface</span></span>
<span data-ttu-id="9ddd1-103">Reprezentuje unikatowy identyfikator dla kodu, który definiuje aplikacji w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="9ddd1-103">Represents a unique identifier for the code that defines the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9ddd1-104">Metody</span><span class="sxs-lookup"><span data-stu-id="9ddd1-104">Methods</span></span>  
  
|<span data-ttu-id="9ddd1-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="9ddd1-105">Method</span></span>|<span data-ttu-id="9ddd1-106">Opis</span><span class="sxs-lookup"><span data-stu-id="9ddd1-106">Description</span></span>|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|<span data-ttu-id="9ddd1-107">Pobiera ciąg formatowania, który reprezentuje kod w tym `IDefinitionAppId` obiektu.</span><span class="sxs-lookup"><span data-stu-id="9ddd1-107">Gets a formatted string that represents the code in this `IDefinitionAppId` object.</span></span>|  
|`IDefinitionAppId::put_Codebase`|<span data-ttu-id="9ddd1-108">Ustawia kod to `IDefinitionAppId` wartość ciągu sformatowaną jak określony obiekt.</span><span class="sxs-lookup"><span data-stu-id="9ddd1-108">Sets the code of this `IDefinitionAppId` object to the specified formatted string value.</span></span>|  
|`IDefinitionAppId::EnumAppPath`|<span data-ttu-id="9ddd1-109">Pobiera wskaźnika interfejsu do [IEnumDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/ienumdefinitionidentity-interface.md) obiekt, który zawiera zestawy w ścieżce bieżącej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9ddd1-109">Gets an interface pointer to an [IEnumDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/ienumdefinitionidentity-interface.md) object that contains the assemblies in the current application path.</span></span>|  
|`IDefinitionAppId::SetAppPath`|<span data-ttu-id="9ddd1-110">Ustawia ścieżkę aplikacji dla zestawu w bieżącym zakresie wartości odwołuje się określony [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="9ddd1-110">Sets the application path for the assembly in the current scope to the value referenced by the specified [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) object.</span></span>|  
|`IDefinitionAppId::get_SubscriptionId`|<span data-ttu-id="9ddd1-111">Pobiera wskaźnik do reprezentację ciągu identyfikatora tokenu dla tej subskrypcji `IDefinitionAppId` obiektu.</span><span class="sxs-lookup"><span data-stu-id="9ddd1-111">Gets a pointer to a string representation of the token identifier for a subscription to this `IDefinitionAppId` object.</span></span>|  
|`IDefinitionAppId::put_SubscriptionId`|<span data-ttu-id="9ddd1-112">Ustawia token identyfikator subskrypcji do tego `IDefinitionAppId` obiektu określona wartość ciągu.</span><span class="sxs-lookup"><span data-stu-id="9ddd1-112">Sets the token identifier for a subscription to this `IDefinitionAppId` object to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9ddd1-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9ddd1-113">Requirements</span></span>  
 <span data-ttu-id="9ddd1-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ddd1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ddd1-115">**Nagłówek:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="9ddd1-115">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="9ddd1-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ddd1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ddd1-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9ddd1-117">See Also</span></span>  
 [<span data-ttu-id="9ddd1-118">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="9ddd1-118">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
