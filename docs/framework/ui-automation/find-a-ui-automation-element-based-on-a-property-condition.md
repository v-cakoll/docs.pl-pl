---
title: Znajdź element automatyzacji interfejsu użytkownika na podstawie warunku właściwości
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- elements, finding by property conditions
- UI Automation, finding elements by property conditions
ms.assetid: 3acaee5a-6ce8-4c3e-81c8-67e59eb74477
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 4c4f14f79960b98618a4f6a3450b1e1a2c05f731
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45597475"
---
# <a name="find-a-ui-automation-element-based-on-a-property-condition"></a>Znajdź element automatyzacji interfejsu użytkownika na podstawie warunku właściwości
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: automatyzacji interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Ten temat zawiera przykładowy kod, który pokazuje, jak można zlokalizować elementu z [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa na podstawie określoną właściwość lub właściwości.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zestaw warunków właściwości są określone, zidentyfikuj niektórych elementu (lub elementów) zainteresowania w <xref:System.Windows.Automation.AutomationElement> drzewa. Następnie zostanie przeprowadzone wyszukiwanie dla wszystkich elementów zgodnych z <xref:System.Windows.Automation.AutomationElement.FindAll%2A> metodę, która zawiera szereg <xref:System.Windows.Automation.AndCondition> operacji logicznych, aby ograniczyć liczbę zgodnych elementów.  
  
> [!NOTE]
>  Podczas wyszukiwania z <xref:System.Windows.Automation.AutomationElement.RootElement%2A>, należy spróbować uzyskać tylko bezpośrednie elementy podrzędne. Wyszukiwanie elementów podrzędnych może wykonać iterację setek lub nawet tysięcy elementów, które prawdopodobnie spowodowało przepełnienie stosu. Jeśli próbujesz uzyskać określony element na niższym poziomie, należy rozpocząć wyszukiwanie z okna aplikacji lub kontenerów na niższym poziomie.  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy InvokePattern i przykładowych elementów Menu klasy ExpandCollapsePattern](https://msdn.microsoft.com/library/b7fa141c-e2d1-4da2-a27f-81a7d1172210)  
 [Uzyskiwanie elementów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)  
 [Używanie właściwości AutomationID](../../../docs/framework/ui-automation/use-the-automationid-property.md)
