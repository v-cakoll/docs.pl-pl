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
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 4b3179333119d1ff516c6176298fa25514a9ba66
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33409779"
---
# <a name="add-content-to-a-text-box-using-ui-automation"></a>Dodawanie zawartości do pola tekstowego przy użyciu automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Ten temat zawiera przykładowy kod, który demonstruje sposób użycia [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] Wstawianie tekstu w polu tekstowym jeden wiersz. Alternatywna metoda podano wiele wierszy i sformatowanego tekstu formantów gdzie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nie ma zastosowania. Dla porównania w przykładzie pokazano sposób użycia metody Win32 na takie same wyniki.  
  
## <a name="example"></a>Przykład  
 Następujące przykładowe kroki przez sekwencję tekstu formantów w aplikacji docelowej. Każdej kontrolki tekstu jest testowany, aby sprawdzić, czy <xref:System.Windows.Automation.ValuePattern> obiektu można uzyskać za pomocą <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> metody. Jeśli formant tekstu obsługuje <xref:System.Windows.Automation.ValuePattern>, <xref:System.Windows.Automation.ValuePattern.SetValue%2A> metoda służy do wstawiania ciągu zdefiniowane przez użytkownika w formancie tekstu. W przeciwnym razie <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> metoda jest używana.  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wstaw TextPattern przykładowy tekst](http://msdn.microsoft.com/library/67353f93-7ee2-42f2-ab76-5c078cf6ca16)
