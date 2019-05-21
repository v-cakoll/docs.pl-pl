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
ms.openlocfilehash: 2f9c0a9791db28cebd055ca446fdff16b9e276a4
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2019
ms.locfileid: "65959610"
---
# <a name="how-to-provide-help-in-a-windows-application"></a>Instrukcje: Zapewnianie pomocy w aplikacji Windows

Aby włączyć korzystanie z <xref:System.Windows.Forms.HelpProvider> składnika, aby dołączyć tematów pomocy w pliku pomocy do określonych formantów na formularzach Windows Forms. Może to być plik Pomocy HTML lub HTMLHelp 1.x lub większa formatu.

## <a name="provide-help"></a>Zapewnianie pomocy

1. W programie Visual Studio z **przybornika**, przeciągnij <xref:System.Windows.Forms.HelpProvider> składnika do formularza.

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
> Uważaj sprawdzić wszelkie informacje wysłane przez klienta, zanim użyjesz go w aplikacji. Złośliwi użytkownicy mogą próbować wysyłać ani wstawić skrypt pliku wykonywalnego, instrukcji SQL lub inny kod. Zanim wyświetlić dane wejściowe użytkownika, zapisz go w bazie danych lub pracować z nim Sprawdź, czy nie zawiera informacji o potencjalnie niebezpieczną. Typowym sposobem na sprawdzenie ma użyć wyrażeń regularnych do wyszukiwania słów kluczowych, takich jak "Skrypt" po otrzymaniu danych wejściowych od użytkownika.

Można również użyć <xref:System.Windows.Forms.HelpProvider> składnika, aby wyświetlić Pomoc podręczną, nawet jeśli jest skonfigurowany do wyświetlania plików pomocy dla formantów na formularzach Windows. Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie pomocy podręcznej](how-to-display-pop-up-help.md).

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Wyświetlanie pomocy podręcznej](how-to-display-pop-up-help.md)
- [Pomoc do kontrolek przy użyciu etykietek narzędzi](control-help-using-tooltips.md)
- [Integrowanie pomocy użytkownika z formularzami Windows Forms](integrating-user-help-in-windows-forms.md)
- [Windows Forms](../index.md)
