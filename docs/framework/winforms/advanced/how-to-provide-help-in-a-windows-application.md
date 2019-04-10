---
title: 'Instrukcje: Zapewnianie pomocy w aplikacji Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Help [Windows Forms], Windows applications
- HTML Help [Windows Forms], Windows Forms
- Windows applications [Windows Forms], providing Help
- HelpProvider component [Windows Forms]
- forms [Windows Forms], providing Help
ms.assetid: 7c4e5cec-2bd2-4f0b-8d75-c2b88929bd61
ms.openlocfilehash: cbecb82acb22915af96fa26f08e441b4f6686c4a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59312722"
---
# <a name="how-to-provide-help-in-a-windows-application"></a>Instrukcje: Zapewnianie pomocy w aplikacji Windows
Można również użyć <xref:System.Windows.Forms.HelpProvider> składnika, aby dołączyć tematów pomocy w pliku pomocy do określonych formantów na formularzach Windows Forms. Może to być plik Pomocy HTML lub HTMLHelp 1.x lub większa formatu.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-provide-help"></a>Zapewnienie pomocy  
  
1. Z **przybornika**, przeciągnij <xref:System.Windows.Forms.HelpProvider> składnika do formularza.  
  
     Składnik będą znajdować się w pasku w dolnej części projektanta Windows Forms.  
  
2. W **właściwości** oknie <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> właściwość chm, .col lub .htm w pliku pomocy.  
  
3. Wybierz inny formant na formularzu, a następnie w **właściwości** oknie <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> właściwości.  
  
     Jest to ciąg przekazany przez <xref:System.Windows.Forms.HelpProvider> składnik do pliku pomocy wezwać odpowiedniego tematu Pomocy.  
  
4. W **właściwości** oknie <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> właściwości na wartość <xref:System.Windows.Forms.HelpNavigator> wyliczenia.  
  
     Określa sposób, w którym **HelpKeyword** właściwość jest przekazywana do systemu pomocy. W poniższej tabeli przedstawiono ustawienia możliwe i ich opisy.  
  
    |Nazwa elementu członkowskiego|Opis|  
    |-----------------|-----------------|  
    |AssociateIndex|Określa, że indeks dla określonego tematu odbywa się w określonym adresie URL.|  
    |Znajdowanie|Określa, czy są wyświetlane na stronie wyszukiwania określonego adresu URL.|  
    |Indeks|Określa, czy są wyświetlane na indeks określonego adresu URL.|  
    |KeywordIndex|Określa słowo kluczowe do wyszukania i akcję do wykonania w określonym adresie URL.|  
    |TableOfContents|Określa, czy jest wyświetlana tabela zawartość pliku Pomocy HTML 1.0.|  
    |Temat|Określa, czy są wyświetlane na temat odwołuje się określony adres URL.|  
  
 W czasie wykonywania, naciskając klawisz F1 podczas kontroli — dla którego ustawiono **HelpKeyword** i **HelpNavigator** właściwości — ma fokus zostanie otwarty plik pomocy skojarzony z tym <xref:System.Windows.Forms.HelpProvider> składnika.  
  
 Obecnie **HelpNamespace** właściwość obsługuje pliki pomocy w trzech formatach podanych poniżej: HTMLHelp 1.x, HTMLHelp 2.0 i HTML. W związku z tym, można ustawić **HelpNamespace** właściwości do adresu http://, takich jak strony sieci Web. Jeśli zostanie to zrobione, zostanie otwarty w domyślnej przeglądarce strony sieci Web przy użyciu parametrów określonych w **HelpKeyword** właściwość używana jako zakotwiczenia. Zakotwiczenia jest używana do przechodzenia do określonej części strony HTML.  
  
> [!IMPORTANT]
>  Uważaj sprawdzić wszelkie informacje wysłane przez klienta, zanim użyjesz go w aplikacji. Złośliwi użytkownicy mogą próbować wysyłać ani wstawić skrypt pliku wykonywalnego, instrukcji SQL lub inny kod. Zanim wyświetlić dane wejściowe użytkownika, zapisz go w bazie danych lub pracować z nim Sprawdź, czy nie zawiera informacji o potencjalnie niebezpieczną. Typowym sposobem na sprawdzenie ma użyć wyrażeń regularnych do wyszukiwania słów kluczowych, takich jak "Skrypt" po otrzymaniu danych wejściowych od użytkownika.  
  
 Można również użyć <xref:System.Windows.Forms.HelpProvider> składnika, aby wyświetlić Pomoc podręczną, nawet jeśli jest skonfigurowany do wyświetlania plików pomocy dla formantów na formularzach Windows. Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie pomocy podręcznej](how-to-display-pop-up-help.md).  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Wyświetlanie pomocy podręcznej](how-to-display-pop-up-help.md)
- [Pomoc w kontroli przy użyciu ToolTips](control-help-using-tooltips.md)
- [Integrowanie pomocy użytkownika z formularzami systemu Windows](integrating-user-help-in-windows-forms.md)
- [Windows Forms](../index.md)
