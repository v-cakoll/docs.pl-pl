---
title: Dodawanie zawartości do pola tekstowego przy użyciu automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adding content to text boxes
- text boxes, adding content
- UI Automation, adding content to text boxes
ms.assetid: 8bdd1a73-1ecb-4a05-a891-a7827ebb767f
ms.openlocfilehash: 71385690c01d261b4ff1b495674bab377232e81d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447249"
---
# <a name="add-content-to-a-text-box-using-ui-automation"></a>Dodawanie zawartości do pola tekstowego przy użyciu automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 Ten temat zawiera przykładowy kod, który demonstruje sposób użycia [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] do wstawiania tekstu do jednowierszowego pola tekstowego. Podano alternatywną metodę dla formantów tekstu wielowierszowego i sformatowanego, w których [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nie ma zastosowania. W celu porównania przykład ilustruje sposób użycia metod Win32 do osiągnięcia tych samych wyników.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przechodzi przez sekwencję formantów tekstowych w aplikacji docelowej. Każda kontrolka Text jest testowana, aby sprawdzić, czy obiekt <xref:System.Windows.Automation.ValuePattern> można uzyskać z niego przy użyciu metody <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A>. Jeśli kontrolka Text obsługuje <xref:System.Windows.Automation.ValuePattern>, Metoda <xref:System.Windows.Automation.ValuePattern.SetValue%2A> służy do wstawiania ciągu zdefiniowanego przez użytkownika do kontrolki tekstowej. W przeciwnym razie zostanie użyta metoda <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType>.  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## <a name="see-also"></a>Zobacz także

- [Przykład wstawiania TextPattern tekstu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))
