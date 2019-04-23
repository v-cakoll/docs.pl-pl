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
ms.openlocfilehash: 177b61cab99d21a844298632020244fa424d8d2a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59176582"
---
# <a name="helpprovider-component-overview-windows-forms"></a>HelpProvider — Informacje o składniku (Formularze systemu Windows)
Formularze Windows [HelpProvider](helpprovider-component-windows-forms.md) składnik jest używany do kojarzenia pomocy HTML 1.x pliku pomocy (plik chm z HTML Help Workshop, lub do pliku .htm) za pomocą aplikacji Windows. Możesz podać pomoc na wiele sposobów:  
  
-   Podaj pomocy kontekstowej dla kontrolek na formularzach Windows Forms.  
  
-   Zapewniają pomoc kontekstowa w szczególności okno dialogowe lub określonych kontrolek w oknie dialogowym.  
  
-   Otwórz plik pomocy do określonych obszarów, takich jak strony głównej w spisie treści, indeksu lub funkcję wyszukiwania.  
  
## <a name="using-the-help-provider"></a>Za pomocą dostawcy pomocy  
 Dodawanie <xref:System.Windows.Forms.HelpProvider> składnik do formularza Windows umożliwia inne kontrolki na formularzu, należy udostępnić właściwości pomocy <xref:System.Windows.Forms.HelpProvider> składnika. Dzięki temu można zapewnić pomoc dla formantów w formularzu Windows. Można skojarzyć z pliku Pomocy <xref:System.Windows.Forms.HelpProvider> za pomocą składnika <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> właściwości. Należy określić typ pomocy udostępniane przez wywołanie metody <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> i podając wartość z zakresu od <xref:System.Windows.Forms.HelpNavigator> wyliczenie dla określonego formantu. Podasz — słowo kluczowe lub tematu pomocy, wywołując <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> metody.  
  
 Opcjonalnie, aby skojarzyć określony ciąg pomocy z inną kontrolką, należy użyć <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> metody. Ciąg, który należy powiązać z kontrolki przy użyciu tej metody jest wyświetlany w oknie podręcznym, gdy użytkownik naciśnie klawisz F1, gdy kontrolka jest ustawiony fokus.  
  
 Jeśli <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> nie został ustawiony, należy użyć <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> zapewnienie tekst pomocy. Jeśli ustawisz zarówno <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> i ciąg pomocy na podstawie pomocy <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> mają wyższy priorytet.  
  
> [!NOTE]
>  Mogą wystąpić problemy przy użyciu ścieżki względnej, określając ścieżkę do pliku pomocy w <xref:System.Windows.Forms.Help.ShowHelp%2A> metody lub <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> właściwość <xref:System.Windows.Forms.HelpProvider> kontroli. Jako takie Pamiętaj określić plik pomocy za pomocą ścieżki bezwzględnej.  
  
## <a name="see-also"></a>Zobacz także

- [Systemy Pomocy w aplikacjach Windows Forms](../advanced/help-systems-in-windows-forms-applications.md)
