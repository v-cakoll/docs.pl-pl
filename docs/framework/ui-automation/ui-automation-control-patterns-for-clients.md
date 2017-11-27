---
title: "Wzorce formantów automatyzacji interfejsu użytkownika dla klientów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, control patterns for clients
- control patterns, UI Automation clients
ms.assetid: 571561d8-5f49-43a9-a054-87735194e013
caps.latest.revision: "24"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 1d556b3da13b70a0a5e69eb72905e04a01dffa9b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ui-automation-control-patterns-for-clients"></a>Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym omówieniu przedstawiono wzorce formantu dla klientów automatyzacji interfejsu użytkownika. Zawiera informacje dotyczące automatyzacji interfejsu użytkownika klienta służy wzorce kontroli dostępu do informacji o [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)].  
  
 Wzorce formantu umożliwiają klasyfikowanie i udostępniać funkcje formantu niezależnie od typu formantu lub wygląd formantu. Klienci automatyzacji interfejsu użytkownika można sprawdzić <xref:System.Windows.Automation.AutomationElement> ustalenie kontroli wzorce są obsługiwane i należy zapewnić zachowanie formantu.  
  
 Aby uzyskać pełną listę wzorców formantu, zobacz [Przegląd wzorców formantu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
<a name="uiautomation_getting_control_patterns"></a>   
## <a name="getting-control-patterns"></a>Pobieranie wzorców formantu  
 Klienci pobierają wzorca formantu z <xref:System.Windows.Automation.AutomationElement> wywołując jedną <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A?displayProperty=nameWithType> lub <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A?displayProperty=nameWithType>.  
  
 Klienci mogą używać <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> metody lub osoby `IsPatternAvailable` właściwości (na przykład <xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>) do ustalenia, czy wzorzec lub grupy wzorców jest obsługiwana na <xref:System.Windows.Automation.AutomationElement>. Jednak jest bardziej wydajne, aby spróbować uzyskać wzorca formantu i testowania dla `null` odwołania, niż można sprawdzić obsługiwanych właściwości i pobrać wzorca formantu, ponieważ jej wynikiem mniejszej liczby wywołań między procesami.  
  
 W poniższym przykładzie pokazano, jak uzyskać <xref:System.Windows.Automation.TextPattern> — wzorzec formantu z <xref:System.Windows.Automation.AutomationElement>.  
  
 [!code-csharp[UIATextPattern_snip#1037](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#1037)]  
  
<a name="uiautomation_properties_on_control_patterns"></a>   
## <a name="retrieving-properties-on-control-patterns"></a>Podczas pobierania właściwości wzorce formantu  
 Klienci mogą pobierać wartości właściwości formantu wzorce, wywołując jedną <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> lub <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> i rzutowanie obiektu zwracanych do odpowiedniego typu. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, zobacz [właściwości automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
 Oprócz `GetPropertyValue` metod, wartości właściwości mogą zostać pobrane za pośrednictwem [!INCLUDE[TLA#tla_clr](../../../includes/tlasharptla-clr-md.md)] metod dostępu, aby uzyskać dostęp do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości wzorca.  
  
<a name="uiautomation_with_variable_patterns"></a>   
## <a name="controls-with-variable-patterns"></a>Formanty z wzorce zmiennych  
 Niektóre typy formantów obsługuje różne wzorce w zależności od ich stanu lub sposób, w którym jest używana formantu. Przykłady formantów, które mogą mieć wzorce zmiennych są widoki list (miniatury, Kafelki, ikony, lista, szczegóły), [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] wykresów (koło, wiersz paska wartość komórki z formułą) [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)]w obszaru (normalny, układ sieci Web konspektu, układ wydruku drukowanie dokumentów Wersja zapoznawcza), a [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] karnacji.  
  
 Formanty, implementacja typy formantów niestandardowych mogą mieć dowolny zbiór wzorce kontrolki, które są wymagane do reprezentowania ich funkcje.  
  
## <a name="see-also"></a>Zobacz też  
 [Wzorce formantów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-patterns.md)  
 [Wzorzec tekstu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-text-pattern.md)  
 [Wywoływanie formantu przy użyciu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/invoke-a-control-using-ui-automation.md)  
 [Pobierz stan przełączenia pola wyboru przy użyciu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/get-the-toggle-state-of-a-check-box-using-ui-automation.md)  
 [Mapowanie wzorców formantów dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)  
 [Wstaw TextPattern przykładowy tekst](http://msdn.microsoft.com/en-us/67353f93-7ee2-42f2-ab76-5c078cf6ca16)  
 [TextPattern wyszukiwania i przykładowe zaznaczenia](http://msdn.microsoft.com/en-us/0a3bca57-8b72-489d-a57c-da85b7a22c7f)  
 [Klasy InvokePattern i przykładowego elementu Menu klasy ExpandCollapsePattern](http://msdn.microsoft.com/en-us/b7fa141c-e2d1-4da2-a27f-81a7d1172210)
