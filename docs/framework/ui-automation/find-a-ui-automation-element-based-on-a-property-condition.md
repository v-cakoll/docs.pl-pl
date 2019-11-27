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
ms.openlocfilehash: 3ca609551955b32ad8b63296975ce10f097d9c30
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433585"
---
# <a name="find-a-ui-automation-element-based-on-a-property-condition"></a>Znajdź element automatyzacji interfejsu użytkownika na podstawie warunku właściwości
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 Ten temat zawiera przykładowy kod pokazujący sposób lokalizowania elementu w drzewie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] w oparciu o określoną właściwość lub właściwości.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie określono zestaw warunków właściwości, które identyfikują określony element (lub elementy) zainteresowania w drzewie <xref:System.Windows.Automation.AutomationElement>. Wyszukiwanie wszystkich pasujących elementów jest następnie wykonywane z użyciem metody <xref:System.Windows.Automation.AutomationElement.FindAll%2A>, która obejmuje szereg <xref:System.Windows.Automation.AndCondition> operacji logicznych, aby ograniczyć liczbę pasujących elementów.  
  
> [!NOTE]
> Podczas wyszukiwania z <xref:System.Windows.Automation.AutomationElement.RootElement%2A>należy podjąć próbę uzyskania tylko bezpośrednich elementów podrzędnych. Wyszukiwanie elementów podrzędnych może się powtarzać przez setki lub nawet tysiące elementów, prawdopodobnie w wyniku przepełnienia stosu. Jeśli próbujesz uzyskać określony element na niższym poziomie, należy rozpocząć wyszukiwanie od okna aplikacji lub kontenera na niższym poziomie.  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
  
## <a name="see-also"></a>Zobacz także

- [Przykład elementu menu InvokePattern i ExpandCollapsePattern](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771636(v=vs.90))
- [Uzyskiwanie elementów automatyzacji interfejsu użytkownika](obtaining-ui-automation-elements.md)
- [Używanie właściwości AutomationID](use-the-automationid-property.md)
