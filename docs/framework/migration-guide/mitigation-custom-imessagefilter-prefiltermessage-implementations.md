---
title: "Środki zaradcze: Implementacji niestandardowego IMessageFilter.PreFilterMessage"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 13b8fffdbab44d3bbbce8f1ed9ce0250dd892f7f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a><span data-ttu-id="dfb98-102">Środki zaradcze: Implementacji niestandardowego IMessageFilter.PreFilterMessage</span><span class="sxs-lookup"><span data-stu-id="dfb98-102">Mitigation: Custom IMessageFilter.PreFilterMessage Implementations</span></span>
<span data-ttu-id="dfb98-103">W aplikacjach formularzy systemu Windows, które odnoszą się do wersji programu .NET Framework począwszy [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], niestandardowego <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementacji można bezpiecznie filtru komunikatów, kiedy <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> metoda jest wywoływana, gdy <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementacji:</span><span class="sxs-lookup"><span data-stu-id="dfb98-103">In Windows Forms apps that target versions of the .NET Framework starting with the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], a custom <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation can safely filter messages when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> method is called if the <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation:</span></span>  
  
-   <span data-ttu-id="dfb98-104">Wykonuje jedno lub oba następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="dfb98-104">Does one or both of the following:</span></span>  
  
    -   <span data-ttu-id="dfb98-105">Dodaje filtr komunikatu przez wywołanie metody <xref:System.Windows.Forms.Application.AddMessageFilter%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="dfb98-105">Adds a message filter by calling the <xref:System.Windows.Forms.Application.AddMessageFilter%2A> method.</span></span>  
  
    -   <span data-ttu-id="dfb98-106">Usuwa filtr komunikatu przez wywołanie metody <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="dfb98-106">Removes a message filter by calling the <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> method.</span></span> <span data-ttu-id="dfb98-107">Metoda.</span><span class="sxs-lookup"><span data-stu-id="dfb98-107">method.</span></span>  
  
-   <span data-ttu-id="dfb98-108">**I** pompy wiadomości przez wywołanie metody <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="dfb98-108">**And** pumps messages by calling the <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="dfb98-109">Wpływ</span><span class="sxs-lookup"><span data-stu-id="dfb98-109">Impact</span></span>  
 <span data-ttu-id="dfb98-110">Ta zmiana wpływa tylko na aplikacje Windows Forms, przeznaczonych dla wersji systemu .NET Framework począwszy [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dfb98-110">This change only affects Windows Forms apps that target versions of the .NET Framework starting with the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].</span></span>  
  
 <span data-ttu-id="dfb98-111">Dla aplikacji formularzy systemu Windows, które odnoszą się do poprzednich wersji programu .NET Framework, throw takie implementacje w niektórych przypadkach <xref:System.IndexOutOfRangeException> wyjątek podczas <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> metoda jest wywoływana</span><span class="sxs-lookup"><span data-stu-id="dfb98-111">For Windows Forms apps that target previous versions of the .NET Framework, such implementations in some cases throw an <xref:System.IndexOutOfRangeException> exception when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> method is called</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="dfb98-112">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="dfb98-112">Mitigation</span></span>  
 <span data-ttu-id="dfb98-113">Jeśli ta zmiana jest niepożądane, aplikacje których docelowe [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] lub nowszej wersji, dodając następujące ustawienie konfiguracji, aby zrezygnować z jej [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcji pliku konfiguracji aplikacji:</span><span class="sxs-lookup"><span data-stu-id="dfb98-113">If this change is undesirable, apps that target the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] or a later version can opt out of it by adding the following configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />   
</runtime>  
```  
  
 <span data-ttu-id="dfb98-114">Ponadto aplikacje docelowe poprzednie wersje programu .NET Framework, które działają w ramach [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] lub nowszym zgodzić się na ten problem, dodając następujące ustawienia konfiguracji do [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)sekcji pliku konfiguracji aplikacji:</span><span class="sxs-lookup"><span data-stu-id="dfb98-114">In addition, apps that target previous versions of the .NET Framework but are running under the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] or a later version can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />   
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dfb98-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dfb98-115">See Also</span></span>  
 [<span data-ttu-id="dfb98-116">Zmiany retargetingu</span><span class="sxs-lookup"><span data-stu-id="dfb98-116">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
