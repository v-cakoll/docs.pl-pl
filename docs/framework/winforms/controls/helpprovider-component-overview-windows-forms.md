---
title: HelpProvider, składnik — omówienie
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
ms.openlocfilehash: 74d35dfa39a605cb1e1e85cc3aeda834e1c60669
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738724"
---
# <a name="helpprovider-component-overview-windows-forms"></a>HelpProvider — Informacje o składniku (Formularze systemu Windows)
Windows Forms składnik [HelpProvider —](helpprovider-component-windows-forms.md) służy do kojarzenia pliku pomocy HTML pomocy 1. x (plik. chm, utworzony za pomocą programu HTML Help Workshop lub pliku. htm) z aplikacją systemu Windows. Możesz zapewnić pomoc na różne sposoby:  
  
- Zapewnianie pomocy kontekstowej dla formantów na Windows Forms.  
  
- Zapewnianie pomocy kontekstowej w konkretnym oknie dialogowym lub określonych kontrolkach w oknie dialogowym.  
  
- Otwórz plik pomocy do określonych obszarów, takich jak Strona główna spisu treści, indeks lub funkcja wyszukiwania.  
  
## <a name="using-the-help-provider"></a>Korzystanie z dostawcy pomocy  
 Dodanie składnika <xref:System.Windows.Forms.HelpProvider> do formularza systemu Windows umożliwia innym kontrolom w formularzu uwidocznienie właściwości pomocy składnika <xref:System.Windows.Forms.HelpProvider>. Dzięki temu można zapewnić pomoc dla kontrolek w formularzu systemu Windows. Można skojarzyć plik pomocy ze składnikiem <xref:System.Windows.Forms.HelpProvider> za pomocą właściwości <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>. Należy określić typ pomocy, wywołując <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> i dostarczając wartość z wyliczenia <xref:System.Windows.Forms.HelpNavigator> dla określonej kontrolki. Podajesz słowo kluczowe lub temat pomocy, wywołując metodę <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A>.  
  
 Opcjonalnie, aby skojarzyć określony ciąg pomocy z inną kontrolką, użyj metody <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A>. Ciąg, który można skojarzyć z kontrolką przy użyciu tej metody jest wyświetlany w oknie podręcznym, gdy użytkownik naciśnie klawisz F1, gdy kontrolka ma fokus.  
  
 Jeśli nie ustawiono <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>, musisz użyć <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A>, aby podać tekst pomocy. Jeśli ustawiono zarówno <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>, jak i ciąg pomocy, pierwszeństwo ma pomoc na podstawie <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>.  
  
> [!NOTE]
> Można napotkać problemy przy użyciu ścieżki względnej podczas określania ścieżki do pliku pomocy w metodzie <xref:System.Windows.Forms.Help.ShowHelp%2A> lub <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>j właściwości kontrolki <xref:System.Windows.Forms.HelpProvider>. W związku z tym Pamiętaj o określeniu pliku pomocy za pomocą bezwzględnej ścieżki pliku.  
  
## <a name="see-also"></a>Zobacz także

- [Systemy Pomocy w aplikacjach Windows Forms](../advanced/help-systems-in-windows-forms-applications.md)
