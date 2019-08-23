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
ms.openlocfilehash: cefc590bb3011b282392504a78ac5c393c58493e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965693"
---
# <a name="helpprovider-component-overview-windows-forms"></a>HelpProvider — Informacje o składniku (Formularze systemu Windows)
Windows Forms składnik [HelpProvider —](helpprovider-component-windows-forms.md) służy do kojarzenia pliku pomocy HTML pomocy 1. x (plik. chm, utworzony za pomocą programu HTML Help Workshop lub pliku. htm) z aplikacją systemu Windows. Możesz zapewnić pomoc na różne sposoby:  
  
- Zapewnianie pomocy kontekstowej dla formantów na Windows Forms.  
  
- Zapewnianie pomocy kontekstowej w konkretnym oknie dialogowym lub określonych kontrolkach w oknie dialogowym.  
  
- Otwórz plik pomocy do określonych obszarów, takich jak Strona główna spisu treści, indeks lub funkcja wyszukiwania.  
  
## <a name="using-the-help-provider"></a>Korzystanie z dostawcy pomocy  
 Dodanie składnika do formularza systemu Windows umożliwia innym kontrolom w formularzu uwidocznienie właściwości <xref:System.Windows.Forms.HelpProvider> pomocy składnika. <xref:System.Windows.Forms.HelpProvider> Dzięki temu można zapewnić pomoc dla kontrolek w formularzu systemu Windows. Można skojarzyć plik pomocy ze <xref:System.Windows.Forms.HelpProvider> składnikiem <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> za pomocą właściwości. Należy określić typ pomocy zapewnianej przez wywoływanie <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> i podanie wartości <xref:System.Windows.Forms.HelpNavigator> z wyliczenia dla określonej kontrolki. Podajesz słowo kluczowe lub temat pomocy, wywołując <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> metodę.  
  
 Opcjonalnie, aby skojarzyć określony ciąg pomocy z inną kontrolką, użyj <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> metody. Ciąg, który można skojarzyć z kontrolką przy użyciu tej metody jest wyświetlany w oknie podręcznym, gdy użytkownik naciśnie klawisz F1, gdy kontrolka ma fokus.  
  
 Jeśli <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> nie została ustawiona, należy użyć <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> , aby podać tekst pomocy. Jeśli ustawiono oba <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> parametry i ciąg pomocy, pierwszeństwo <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> ma pomoc na podstawie.  
  
> [!NOTE]
> Podczas określania ścieżki do pliku pomocy w <xref:System.Windows.Forms.Help.ShowHelp%2A> metodzie lub <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> właściwości <xref:System.Windows.Forms.HelpProvider> formantu mogą wystąpić problemy przy użyciu ścieżki względnej. W związku z tym Pamiętaj o określeniu pliku pomocy za pomocą bezwzględnej ścieżki pliku.  
  
## <a name="see-also"></a>Zobacz także

- [Systemy Pomocy w aplikacjach Windows Forms](../advanced/help-systems-in-windows-forms-applications.md)
