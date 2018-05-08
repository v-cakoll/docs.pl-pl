---
title: HelpProvider — Informacje o składniku (Formularze systemu Windows)
ms.date: 03/30/2017
f1_keywords:
- HelpProvider
helpviewer_keywords:
- HelpProvider component [Windows Forms], about HelpProvider component
- Help [Windows Forms], adding to Windows applications
- F1 Help [Windows Forms], adding to Windows Forms
- dialog boxes [Windows Forms], context-sensitive Help
- Windows Forms, context-sensitive Help
ms.assetid: 6b10c2cc-c577-4cb5-9669-e37b33416af9
ms.openlocfilehash: 5ad74b862c09734f3490210cb6898945a3c787fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="helpprovider-component-overview-windows-forms"></a>HelpProvider — Informacje o składniku (Formularze systemu Windows)
Formularze systemu Windows [helpprovider —](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md) składnik jest używany do skojarzenia z aplikacją Windows pomocy HTML 1.x pliku pomocy (plik .chm produkowanych Workshop pomocy HTML, lub plik htm). Zapewniają pomoc na wiele sposobów:  
  
-   Podaj pomocy kontekstowej dla formantów na formularzach systemu Windows.  
  
-   Podaj Pomoc kontekstowa w szczególności okno dialogowe lub określonych formantów w oknie dialogowym.  
  
-   Otwórz plik pomocy do określonych obszarów, takich jak strona główna spisu treści, indeksu lub funkcję wyszukiwania.  
  
## <a name="using-the-help-provider"></a>Przy użyciu dostawcy pomocy  
 Dodawanie <xref:System.Windows.Forms.HelpProvider> składnik do formularza systemu Windows umożliwia inne formanty na formularzu, aby udostępnić pomocy właściwości <xref:System.Windows.Forms.HelpProvider> składnika. Dzięki temu można zapewnić pomoc dla formantów w formularzu systemu Windows. Można skojarzyć plik pomocy z <xref:System.Windows.Forms.HelpProvider> przy użyciu składnika <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> właściwości. Określ typ pomoc wywoływania <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> i podawania wartości z <xref:System.Windows.Forms.HelpNavigator> wyliczenie dla określonego formantu. Podanie — słowo kluczowe lub tematu do pomocy przez wywołanie metody <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> metody.  
  
 Opcjonalnie, aby skojarzyć określony ciąg pomocy z formantem, należy użyć <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> metody. Ciąg, który należy powiązać z formantu przy użyciu tej metody jest wyświetlany w oknie podręcznym, gdy użytkownik naciśnie klawisz F1, gdy formant ma fokus.  
  
 Jeśli <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> nie został ustawiony, należy użyć <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> zapewnienie tekst pomocy. Jeśli ustawiono oba <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> i ciąg pomocy, na podstawie pomocy <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> mają wyższy priorytet.  
  
> [!NOTE]
>  Mogą wystąpić problemy przy użyciu ścieżki względnej podczas podając ścieżkę do pliku pomocy w <xref:System.Windows.Forms.Help.ShowHelp%2A> metody lub <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> właściwość <xref:System.Windows.Forms.HelpProvider> formantu. Tak należy użyć ścieżki bezwzględnej, aby określić plik pomocy.  
  
## <a name="see-also"></a>Zobacz też  
 [Systemy Pomocy w aplikacjach Windows Forms](../../../../docs/framework/winforms/advanced/help-systems-in-windows-forms-applications.md)
