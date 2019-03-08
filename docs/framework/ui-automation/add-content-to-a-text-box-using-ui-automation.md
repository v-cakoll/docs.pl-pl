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
ms.openlocfilehash: af9450685452bb25d54a5cd28295092addf6bb20
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2019
ms.locfileid: "57680246"
---
# <a name="add-content-to-a-text-box-using-ui-automation"></a>Dodawanie zawartości do pola tekstowego przy użyciu automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Ten temat zawiera przykładowy kod, który demonstruje sposób używania [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] umożliwia wstawianie tekstu w polu tekstu jednowierszowego. Alternatywna metoda jest przewidziana kontrolek tekstu wielowierszowego i oferuje szeroki wachlarz gdzie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nie ma zastosowania. Dla celów porównawczych w przykładzie pokazano sposób użycia metod Win32 na takie same wyniki.  
  
## <a name="example"></a>Przykład  
 Krokach w poniższym przykładzie za pośrednictwem sekwencji kontrolek tekstu w aplikacji docelowej. Każdy formant tekstu jest testowany, aby sprawdzić, czy <xref:System.Windows.Automation.ValuePattern> obiektu można uzyskać za pomocą <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> metody. Jeśli obsługuje kontrolki tekstu <xref:System.Windows.Automation.ValuePattern>, <xref:System.Windows.Automation.ValuePattern.SetValue%2A> metoda służy do wstawiania ciągiem zdefiniowanym przez użytkownika do kontrolki tekstu. W przeciwnym razie <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> metoda jest używana.  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## <a name="see-also"></a>Zobacz także
- [Przykładowy tekst wstawienia TextPattern](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))
