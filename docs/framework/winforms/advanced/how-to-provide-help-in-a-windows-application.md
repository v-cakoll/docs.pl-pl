---
title: 'Porady: zapewnianie pomocy w aplikacji Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Help [Windows Forms], Windows applications
- HTML Help [Windows Forms], Windows Forms
- Windows applications [Windows Forms], providing Help
- HelpProvider component [Windows Forms]
- forms [Windows Forms], providing Help
ms.assetid: 7c4e5cec-2bd2-4f0b-8d75-c2b88929bd61
ms.openlocfilehash: 405de333ce936a864047e827e60f56a930059e26
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2020
ms.locfileid: "84143631"
---
# <a name="how-to-provide-help-in-a-windows-application"></a>Porady: zapewnianie pomocy w aplikacji Windows

Można używać <xref:System.Windows.Forms.HelpProvider> składnika do dołączania tematów pomocy w pliku pomocy do określonych kontrolek na Windows Forms. Plik pomocy może być w formacie HTML lub HTMLHelp 1. x lub większym.

## <a name="provide-help"></a>Zapewnianie pomocy

1. W programie Visual Studio z **przybornika**przeciągnij <xref:System.Windows.Forms.HelpProvider> składnik do formularza.

     Składnik zostanie umieszczony w zasobniku u dołu Projektant formularzy systemu Windows.

2. W oknie **Właściwości** Ustaw <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> Właściwość na plik. chm,. Col lub. htm.

3. Wybierz inny formant w formularzu, a następnie w oknie **Właściwości** Ustaw <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> Właściwość.

     Jest to ciąg przesyłany przez <xref:System.Windows.Forms.HelpProvider> składnik do pliku pomocy w celu zawezwania odpowiedniego tematu pomocy.

4. W oknie **Właściwości** Ustaw <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> Właściwość na wartość <xref:System.Windows.Forms.HelpNavigator> wyliczenia.

     Określa sposób, w jaki Właściwość **HelpKeyword** jest przenoszona do systemu pomocy. W poniższej tabeli przedstawiono możliwe ustawienia i ich opisy.

    |Nazwa elementu członkowskiego|Opis|
    |-----------------|-----------------|
    |AssociateIndex|Określa, że indeks określonego tematu jest wykonywany w określonym adresie URL.|
    |Znajdowanie|Określa, że zostanie wyświetlona strona wyszukiwania określonego adresu URL.|
    |Indeks|Określa, że jest wyświetlany indeks określonego adresu URL.|
    |KeywordIndex|Określa słowo kluczowe do wyszukania i akcję do wykonania w określonym adresie URL.|
    |TableOfContents|Określa, że jest wyświetlany Spis treści pliku pomocy HTML 1,0.|
    |Temat|Określa, że jest wyświetlany temat, do którego odwołuje się określony adres URL.|

 W czasie wykonywania naciśnij klawisz F1, gdy formant — dla którego ustawiono właściwości **HelpKeyword** i **HelpNavigator** — fokus spowoduje otwarcie pliku pomocy skojarzonego z tym <xref:System.Windows.Forms.HelpProvider> składnikiem.

 Obecnie Właściwość **HelpNamespace** obsługuje pliki pomocy w następujących trzech formatach: HTMLHelp 1. x, HTMLHelp 2,0 i HTML. W związku z tym można ustawić właściwość **HelpNamespace** na `http://` adres, na przykład stronę sieci Web. Jeśli to zrobisz, spowoduje to otwarcie domyślnej przeglądarki na stronie sieci Web z ciągiem określonym we właściwości **HelpKeyword** używanym jako zakotwiczenie. Kotwica służy do przechodzenia do określonej części strony HTML.

> [!IMPORTANT]
> Należy zachować ostrożność, aby sprawdzić wszystkie informacje wysyłane z klienta przed użyciem go w aplikacji. Złośliwi użytkownicy mogą próbować wysłać lub wstrzyknąć skrypt wykonywalny, instrukcje SQL lub inny kod. Przed wyświetleniem danych wejściowych użytkownika Zapisz je w bazie danych lub pracuj z nią, sprawdź, czy nie zawiera potencjalnie niebezpiecznych informacji. Typowym sposobem zaznaczania jest użycie wyrażenia regularnego w celu wyszukania słów kluczowych, takich jak "skrypt", gdy otrzymujesz dane wejściowe od użytkownika.

Możesz również użyć <xref:System.Windows.Forms.HelpProvider> składnika, aby wyświetlić Pomoc podręczną, nawet jeśli została skonfigurowana do wyświetlania plików pomocy dla formantów na Windows Forms. Aby uzyskać więcej informacji, zobacz [How to: Display podręczny help-up](how-to-display-pop-up-help.md).

## <a name="see-also"></a>Zobacz także

- [Instrukcje: wyświetlanie pomocy podręcznej](how-to-display-pop-up-help.md)
- [Pomoc do kontrolek przy użyciu etykietek narzędzi](control-help-using-tooltips.md)
- [Integrowanie pomocy użytkownika z formularzami Windows Forms](integrating-user-help-in-windows-forms.md)
- [Windows Forms](../index.md)
