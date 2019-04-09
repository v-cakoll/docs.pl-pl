---
title: 'Środki zaradcze: Implementacji niestandardowego IMessageFilter.PreFilterMessage'
ms.date: 03/30/2017
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ebb3283d089f4e823db051cd7ee450a1df6b866e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096943"
---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a>Środki zaradcze: Implementacji niestandardowego IMessageFilter.PreFilterMessage
W aplikacjach Windows Forms, przeznaczonych dla wersji programu .NET Framework począwszy od [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], niestandardowe <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementacji może bezpiecznie filtr komunikatów, kiedy <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> metoda jest wywoływana, gdy <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementacji:  
  
-   Wykonuje jedno lub oba z następujących czynności:  
  
    -   Dodaje filtr komunikatu przez wywołanie metody <xref:System.Windows.Forms.Application.AddMessageFilter%2A> metody.  
  
    -   Usuwa filtr komunikatu przez wywołanie metody <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> metody. Metoda.  
  
-   **I** pompy komunikatów przez wywołanie metody <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> metody.  
  
## <a name="impact"></a>Wpływ  
 Ta zmiana dotyczy tylko aplikacji Windows Forms, przeznaczonych dla wersji programu .NET Framework począwszy od [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].  
  
 W przypadku aplikacji Windows Forms przeznaczone dla poprzednich wersji programu .NET Framework, throw takich implementacji w niektórych przypadkach <xref:System.IndexOutOfRangeException> wyjątek podczas <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> wywoływana jest metoda  
  
## <a name="mitigation"></a>Ograniczenie  
 Jeśli ta zmiana jest niepożądany, aplikacje przeznaczone na platformę [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] lub nowszej wersji można zrezygnować z go, dodając następujące ustawienie konfiguracji, aby [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcję pliku konfiguracji aplikacji:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />   
</runtime>  
```  
  
 Ponadto aplikacje poprzedniej wersji programu .NET Framework, które są uruchomione w [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] lub nowszej wersji można jednak to zachowanie, dodając następujące ustawienie konfiguracji, aby [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)sekcję pliku konfiguracji aplikacji:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />   
</runtime>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Zmiany przekierowania](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
