---
title: "Uzyskiwanie szczegółów atrybutów tekstu mieszanego przy użyciu automatyzacji interfejsu użytkownika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d0e4c005-abd1-42bb-92a4-5faf87097311
caps.latest.revision: "11"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 0588ec764aabf5aa0e88477838d949a294f3064e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="obtain-mixed-text-attribute-details-using-ui-automation"></a>Uzyskiwanie szczegółów atrybutów tekstu mieszanego przy użyciu automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie przedstawiono sposób użycia [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] do Uzyskiwanie szczegółów atrybutów tekstu z zakres tekstu, obejmującej wiele wartości atrybutów. Zakres tekstu może odpowiadać bieżącej lokalizacji karetki (lub degeneracji zaznaczenia) w dokumencie, ciągłe zaznaczenia tekstu, Kolekcja zaznaczonych fragmentów tekstu rozłączne lub całej zawartości tekstowej dokumentu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje sposób uzyskiwania <xref:System.Windows.Automation.TextPattern.FontNameAttribute> z zakresu tekstu gdzie <xref:System.Windows.Automation.Text.TextPatternRange.GetAttributeValue%2A> zwraca <xref:System.Windows.Automation.TextPattern.MixedAttributeValue> obiektu.  
  
 [!code-csharp[FindText#RetrieveMixedAttributes](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#retrievemixedattributes)]
 [!code-vb[FindText#RetrieveMixedAttributes](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#retrievemixedattributes)]  
  
 <xref:System.Windows.Automation.TextPattern> — Wzorzec kontrolki, w połączeniu z <xref:System.Windows.Automation.Text.TextPatternRange> klasy, obsługuje atrybutów tekstu podstawowego, właściwości i metod. Dla funkcji specyficznych dla formantu, który nie jest obsługiwany przez <xref:System.Windows.Automation.TextPattern> lub <xref:System.Windows.Automation.Text.TextPatternRange>, <xref:System.Windows.Automation.AutomationElement> klasa dostarcza metody dla automatyzacji interfejsu użytkownika klienta dostępu do modelu odpowiedni obiekt natywny.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd automatyzacji interfejsu użytkownika — TextPattern](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)  
 [Dodawanie zawartości do pola tekstowego przy użyciu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)  
 [Znajdowanie i wyróżnianie tekstu przy użyciu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)  
 [Przegląd wzorców formantu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Wzorce formantów automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Uzyskiwanie atrybutów tekstu przy użyciu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/obtain-text-attributes-using-ui-automation.md)
