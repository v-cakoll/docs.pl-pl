---
title: Przenoszenie tekstu przy użyciu automatyzacji interfejsu użytkownika
description: Zobacz przykład sposobu przechodzenia zawartości tekstowej dokumentu przy użyciu automatyzacji interfejsu użytkownika firmy Microsoft w przyrostach TextUnit.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, traversing text
- text, traversing
- traversing text
ms.assetid: 3ddb3b7b-1d6b-4dba-8678-5a68e868aadb
ms.openlocfilehash: 0b4269d043fd6cd0cc5da9825714aab4ead701f9
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168081"
---
# <a name="traverse-text-using-ui-automation"></a>Przenoszenie tekstu przy użyciu automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W tym temacie pokazano, jak użyć [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] do przechodzenia zawartości tekstowej dokumentu przez <xref:System.Windows.Automation.Text.TextUnit> przyrosty.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje sposób przechodzenia zawartości dostawcy tekstu automatyzacji interfejsu użytkownika. <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A>Metoda przenosi <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> punkty końcowe i <xref:System.Windows.Automation.Text.TextPatternRange> . Ten zakres tekstu jest zazwyczaj zakresem degeneracji reprezentującym punkt wstawiania tekstu.  
  
> [!NOTE]
> Ponieważ tylko tekstowe obiekty osadzone są uważane za część strumienia tekstu, obiekty osadzone, takie jak obrazy, nie wpływają `Move` lub nie zwraca wartości.  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#Navigate](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#navigate)]
[!code-vb[FindText#Navigate](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#navigate)]  
  
 Każda metoda przy użyciu <xref:System.Windows.Automation.Text.TextUnit> będzie przełożyć na następną największą <xref:System.Windows.Automation.Text.TextUnit> obsługiwaną wartość, jeśli dana <xref:System.Windows.Automation.Text.TextUnit> kontrolka nie jest obsługiwana.  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd automatyzacji interfejsu użytkownika — TextPattern](ui-automation-textpattern-overview.md)
- [Dodawanie zawartości do pola tekstowego przy użyciu automatyzacji interfejsu użytkownika](add-content-to-a-text-box-using-ui-automation.md)
- [Znajdowanie i wyróżnianie tekstu przy użyciu automatyzacji interfejsu użytkownika](find-and-highlight-text-using-ui-automation.md)
- [Wzorce formantów automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](ui-automation-control-patterns-for-clients.md)
