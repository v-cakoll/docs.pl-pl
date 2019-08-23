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
ms.openlocfilehash: fdc52d0b94ce500b6560b60419d409f5cbd73b55
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932651"
---
# <a name="add-content-to-a-text-box-using-ui-automation"></a>Dodawanie zawartości do pola tekstowego przy użyciu automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.  
  
 Ten temat zawiera przykładowy kod, który demonstruje sposób użycia [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] do wstawiania tekstu w jednowierszowym polu tekstowym. Podano alternatywną metodę dla formantów tekstu wielowierszowego i sformatowanego [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , gdzie nie ma zastosowania. W celu porównania przykład ilustruje sposób użycia metod Win32 do osiągnięcia tych samych wyników.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przechodzi przez sekwencję formantów tekstowych w aplikacji docelowej. Każda kontrolka tekstowa jest testowana, aby <xref:System.Windows.Automation.ValuePattern> sprawdzić, czy obiekt można uzyskać z niego <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> przy użyciu metody. Jeśli kontrolka <xref:System.Windows.Automation.ValuePattern>tekstu obsługuje <xref:System.Windows.Automation.ValuePattern.SetValue%2A> , metoda służy do wstawiania ciągu zdefiniowanego przez użytkownika do kontrolki tekstowej. W przeciwnym razie metoda jest używana. <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType>  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## <a name="see-also"></a>Zobacz także

- [Przykład wstawiania TextPattern tekstu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))
