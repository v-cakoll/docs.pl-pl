---
title: Przenoszenie tekstu przy użyciu automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, traversing text
- text, traversing
- traversing text
ms.assetid: 3ddb3b7b-1d6b-4dba-8678-5a68e868aadb
ms.openlocfilehash: fe0b27e1185412a09bafc1ecdcf94d3f3c586c51
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946357"
---
# <a name="traverse-text-using-ui-automation"></a>Przenoszenie tekstu przy użyciu automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.  
  
 W tym temacie pokazano, jak [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] użyć do przechodzenia zawartości tekstowej dokumentu przez <xref:System.Windows.Automation.Text.TextUnit> przyrosty.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje sposób przechodzenia zawartości dostawcy tekstu automatyzacji interfejsu użytkownika. Metoda przenosi punkty <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> końcowe<xref:System.Windows.Automation.Text.TextPatternRange>i. <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> Ten zakres tekstu jest zazwyczaj zakresem degeneracji reprezentującym punkt wstawiania tekstu.  
  
> [!NOTE]
> Ponieważ tylko tekstowe obiekty osadzone są uważane za część strumienia tekstu, obiekty osadzone, takie jak obrazy, nie wpływają `Move` lub nie zwraca wartości.  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#Navigate](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#navigate)]
[!code-vb[FindText#Navigate](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#navigate)]  
  
 Każda metoda przy <xref:System.Windows.Automation.Text.TextUnit> użyciu będzie przełożyć na następną największą <xref:System.Windows.Automation.Text.TextUnit> obsługiwaną wartość <xref:System.Windows.Automation.Text.TextUnit> , jeśli dana kontrolka nie jest obsługiwana.  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd automatyzacji interfejsu użytkownika — TextPattern](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)
- [Dodawanie zawartości do pola tekstowego przy użyciu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)
- [Znajdowanie i wyróżnianie tekstu przy użyciu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
