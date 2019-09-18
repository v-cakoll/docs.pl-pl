---
title: Uzyskiwanie szczegółów atrybutów tekstu mieszanego przy użyciu automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d0e4c005-abd1-42bb-92a4-5faf87097311
ms.openlocfilehash: 13ebc6aefe925ecefe48a9b0fa8cf7a6ecd3c454
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71042952"
---
# <a name="obtain-mixed-text-attribute-details-using-ui-automation"></a>Uzyskiwanie szczegółów atrybutów tekstu mieszanego przy użyciu automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.  
  
 W tym temacie pokazano, jak [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] za pomocą programu uzyskiwać szczegóły atrybutów tekstu z zakresu tekstu, który obejmuje wiele wartości atrybutów. Zakres tekstu może odpowiadać bieżącej lokalizacji karetki (lub wygenerowania zaznaczenia) w dokumencie, ciągłym wyborze tekstu, kolekcji rozłączonych opcji tekstowych lub całej zawartości tekstowej dokumentu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje, jak uzyskać od zakresu <xref:System.Windows.Automation.TextPattern.FontNameAttribute> tekstu, gdzie <xref:System.Windows.Automation.Text.TextPatternRange.GetAttributeValue%2A> zwraca <xref:System.Windows.Automation.TextPattern.MixedAttributeValue> obiekt.  
  
[!code-csharp[FindText#RetrieveMixedAttributes](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#retrievemixedattributes)]
[!code-vb[FindText#RetrieveMixedAttributes](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#retrievemixedattributes)]  
  
 Wzorzec kontrolki, w połączeniu <xref:System.Windows.Automation.Text.TextPatternRange> z klasą, obsługuje podstawowe atrybuty tekstu, właściwości i metody. <xref:System.Windows.Automation.TextPattern> W przypadku funkcji specyficznych dla kontroli, które nie <xref:System.Windows.Automation.TextPattern> są <xref:System.Windows.Automation.Text.TextPatternRange>obsługiwane przez <xref:System.Windows.Automation.AutomationElement> program lub, Klasa dostarcza metody dla klienta automatyzacji interfejsu użytkownika w celu uzyskania dostępu do odpowiedniego modelu obiektów macierzystych.  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd automatyzacji interfejsu użytkownika — TextPattern](ui-automation-textpattern-overview.md)
- [Dodawanie zawartości do pola tekstowego przy użyciu automatyzacji interfejsu użytkownika](add-content-to-a-text-box-using-ui-automation.md)
- [Znajdowanie i wyróżnianie tekstu przy użyciu automatyzacji interfejsu użytkownika](find-and-highlight-text-using-ui-automation.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](ui-automation-control-patterns-for-clients.md)
- [Uzyskiwanie atrybutów tekstu przy użyciu automatyzacji interfejsu użytkownika](obtain-text-attributes-using-ui-automation.md)
