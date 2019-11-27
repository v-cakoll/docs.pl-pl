---
title: Uzyskiwanie szczegółów atrybutów tekstu mieszanego przy użyciu automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d0e4c005-abd1-42bb-92a4-5faf87097311
ms.openlocfilehash: 9f2cba1f602cedf3a13bd909b4dc2f1a7b4ab972
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443123"
---
# <a name="obtain-mixed-text-attribute-details-using-ui-automation"></a>Uzyskiwanie szczegółów atrybutów tekstu mieszanego przy użyciu automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W tym temacie pokazano, jak za pomocą [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] uzyskać szczegóły atrybutów tekstu z zakresu tekstu, który obejmuje wiele wartości atrybutów. Zakres tekstu może odpowiadać bieżącej lokalizacji karetki (lub wygenerowania zaznaczenia) w dokumencie, ciągłym wyborze tekstu, kolekcji rozłączonych opcji tekstowych lub całej zawartości tekstowej dokumentu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje, jak uzyskać <xref:System.Windows.Automation.TextPattern.FontNameAttribute> z zakresu tekstu, gdzie <xref:System.Windows.Automation.Text.TextPatternRange.GetAttributeValue%2A> zwraca obiekt <xref:System.Windows.Automation.TextPattern.MixedAttributeValue>.  
  
[!code-csharp[FindText#RetrieveMixedAttributes](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#retrievemixedattributes)]
[!code-vb[FindText#RetrieveMixedAttributes](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#retrievemixedattributes)]  
  
 <xref:System.Windows.Automation.TextPattern> wzorzec kontrolki, w połączeniu z klasą <xref:System.Windows.Automation.Text.TextPatternRange>, obsługuje podstawowe atrybuty tekstu, właściwości i metody. W przypadku funkcji specyficznych dla kontroli, które nie są obsługiwane przez <xref:System.Windows.Automation.TextPattern> lub <xref:System.Windows.Automation.Text.TextPatternRange>, Klasa <xref:System.Windows.Automation.AutomationElement> udostępnia metody dla klienta automatyzacji interfejsu użytkownika w celu uzyskania dostępu do odpowiedniego modelu obiektów macierzystych.  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd automatyzacji interfejsu użytkownika — TextPattern](ui-automation-textpattern-overview.md)
- [Dodawanie zawartości do pola tekstowego przy użyciu automatyzacji interfejsu użytkownika](add-content-to-a-text-box-using-ui-automation.md)
- [Znajdowanie i wyróżnianie tekstu przy użyciu automatyzacji interfejsu użytkownika](find-and-highlight-text-using-ui-automation.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](ui-automation-control-patterns-for-clients.md)
- [Uzyskiwanie atrybutów tekstu przy użyciu automatyzacji interfejsu użytkownika](obtain-text-attributes-using-ui-automation.md)
