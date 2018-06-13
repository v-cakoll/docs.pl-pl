---
title: 'Środki zaradcze: Implementacji niestandardowego IMessageFilter.PreFilterMessage'
ms.date: 03/30/2017
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 78d8ba7f872095920e7fda727f46fc10b989ed37
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33388290"
---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a>Środki zaradcze: Implementacji niestandardowego IMessageFilter.PreFilterMessage
W aplikacjach formularzy systemu Windows, które odnoszą się do wersji programu .NET Framework począwszy [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], niestandardowego <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementacji można bezpiecznie filtru komunikatów, kiedy <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> metoda jest wywoływana, gdy <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementacji:  
  
-   Wykonuje jedno lub oba następujące czynności:  
  
    -   Dodaje filtr komunikatu przez wywołanie metody <xref:System.Windows.Forms.Application.AddMessageFilter%2A> metody.  
  
    -   Usuwa filtr komunikatu przez wywołanie metody <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> metody. Metoda.  
  
-   **I** pompy wiadomości przez wywołanie metody <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> metody.  
  
## <a name="impact"></a>Wpływ  
 Ta zmiana wpływa tylko na aplikacje Windows Forms, przeznaczonych dla wersji systemu .NET Framework począwszy [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].  
  
 Dla aplikacji formularzy systemu Windows, które odnoszą się do poprzednich wersji programu .NET Framework, throw takie implementacje w niektórych przypadkach <xref:System.IndexOutOfRangeException> wyjątek podczas <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> metoda jest wywoływana  
  
## <a name="mitigation"></a>Ograniczenie  
 Jeśli ta zmiana jest niepożądane, aplikacje których docelowe [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] lub nowszej wersji, dodając następujące ustawienie konfiguracji, aby zrezygnować z jej [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcji pliku konfiguracji aplikacji:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />   
</runtime>  
```  
  
 Ponadto aplikacje docelowe poprzednie wersje programu .NET Framework, które działają w ramach [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] lub nowszym zgodzić się na ten problem, dodając następujące ustawienia konfiguracji do [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)sekcji pliku konfiguracji aplikacji:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />   
</runtime>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zmiany retargetingu](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
