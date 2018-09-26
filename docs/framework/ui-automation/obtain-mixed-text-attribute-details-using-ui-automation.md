---
title: Uzyskiwanie szczegółów atrybutów tekstu mieszanego przy użyciu automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d0e4c005-abd1-42bb-92a4-5faf87097311
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: b425aa4194e688a3814570cc47b8aa3b7ea97ee8
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47087414"
---
# <a name="obtain-mixed-text-attribute-details-using-ui-automation"></a>Uzyskiwanie szczegółów atrybutów tekstu mieszanego przy użyciu automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: automatyzacji interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie pokazano, jak używać [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] na uzyskiwanie szczegółów atrybutów tekstu z zakresu tekstu, który obejmuje wiele wartości atrybutów. Zakres tekstu może odpowiadać w bieżącej lokalizacji karetki (lub zdegenerowanym zaznaczenia) w dokumencie, wyboru ciągłego, tekstu, zbiór zaznaczenia tekstu rozłączne lub całej zawartości tekstowej dokumentu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje sposób uzyskiwania <xref:System.Windows.Automation.TextPattern.FontNameAttribute> z zakresu tekstu gdzie <xref:System.Windows.Automation.Text.TextPatternRange.GetAttributeValue%2A> zwraca <xref:System.Windows.Automation.TextPattern.MixedAttributeValue> obiektu.  
  
 [!code-csharp[FindText#RetrieveMixedAttributes](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#retrievemixedattributes)]
 [!code-vb[FindText#RetrieveMixedAttributes](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#retrievemixedattributes)]  
  
 <xref:System.Windows.Automation.TextPattern> — Wzorzec kontrolki, w połączeniu z sekcją <xref:System.Windows.Automation.Text.TextPatternRange> klasy, obsługuje podstawowe atrybuty, właściwości i metody. Dla funkcji specyficznej dla kontroli, która nie jest obsługiwana przez <xref:System.Windows.Automation.TextPattern> lub <xref:System.Windows.Automation.Text.TextPatternRange>, <xref:System.Windows.Automation.AutomationElement> klasa dostarcza metody dla klientów automatyzacji interfejsu użytkownika dostępu odpowiedni model obiektów natywnych.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd automatyzacji interfejsu użytkownika — TextPattern](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)  
 [Dodawanie zawartości do pola tekstowego przy użyciu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)  
 [Znajdowanie i wyróżnianie tekstu przy użyciu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Uzyskiwanie atrybutów tekstu przy użyciu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/obtain-text-attributes-using-ui-automation.md)
