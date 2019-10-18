---
title: Podstawy dotyczące aplikacji Windows Forms (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Windows applications
- Windows Forms, Visual Basic
ms.assetid: 0b919d30-7fd6-42db-85c8-543d15312441
ms.openlocfilehash: f1b70209d6daf412be56949f349c242a83578e71
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524760"
---
# <a name="windows-forms-application-basics-visual-basic"></a>Podstawy dotyczące aplikacji Windows Forms (Visual Basic)

Ważną częścią Visual Basic jest możliwość tworzenia Windows Forms aplikacji, które są uruchamiane lokalnie na komputerach użytkowników. Możesz użyć programu Visual Studio do utworzenia aplikacji i interfejsu użytkownika przy użyciu Windows Forms. Aplikacja Windows Forms jest oparta na klasach z przestrzeni nazw <xref:System.Windows.Forms>.

## <a name="designing-windows-forms-applications"></a>Projektowanie aplikacji Windows Forms

Możesz tworzyć Windows Forms i aplikacje usług systemu Windows za pomocą programu Visual Studio. Więcej informacji znajduje się w następujących tematach:

- [Wprowadzenie z Windows Forms](../../../framework/winforms/getting-started-with-windows-forms.md). Zawiera informacje dotyczące sposobu tworzenia i programu Windows Forms.

- [Kontrolki Windows Forms](../../../framework/winforms/controls/index.md). Zbiór tematów opisujących sposób używania formantów Windows Forms.

- [Aplikacje usług systemu Windows](../../../framework/windows-services/index.md). Zawiera listę tematów, które wyjaśniają sposób tworzenia usług systemu Windows.

## <a name="building-rich-interactive-user-interfaces"></a>Tworzenie rozbudowanych, interaktywnych interfejsów użytkownika

Windows Forms jest składnikiem inteligentnego klienta .NET Framework, zestawu bibliotek zarządzanych, które umożliwiają wykonywanie typowych zadań aplikacji, takich jak odczytywanie i zapisywanie w systemie plików. Za pomocą środowiska programistycznego, takiego jak Visual Studio, można tworzyć Windows Forms aplikacje, które wyświetlają informacje, żądają danych wejściowych od użytkowników i komunikują się z komputerami zdalnymi za pośrednictwem sieci.

W Windows Forms formularz jest obszarem wizualnym, na którym są wyświetlane informacje dla użytkownika. Często tworzysz Windows Forms aplikacje, umieszczając kontrolki na formularzach i opracowując odpowiedzi do akcji użytkownika, takich jak kliknięcia myszą lub naciśnięcia klawiszy. *Kontrolka* to dyskretny element interfejsu użytkownika, który wyświetla dane lub akceptuje dane wejściowe.

### <a name="events"></a>Zdarzenia

Gdy użytkownik robi coś w formularzu lub jednej z jego kontrolek, generuje zdarzenie. Aplikacja reaguje na te zdarzenia za pomocą kodu i przetwarza zdarzenia, gdy wystąpią. Aby uzyskać więcej informacji, zobacz [Tworzenie programów obsługi zdarzeń w Windows Forms](../../../framework/winforms/creating-event-handlers-in-windows-forms.md).

### <a name="controls"></a>Formanty

Windows Forms zawiera różne kontrolki, które można umieścić w formularzach: kontrolki, które wyświetlają pola tekstowe, przyciski, pola rozwijane, przyciski radiowe i nawet strony sieci Web. Aby uzyskać listę wszystkich kontrolek, których można użyć na formularzu, zobacz [kontrolki do użycia na Windows Forms](../../../framework/winforms/controls/controls-to-use-on-windows-forms.md). Jeśli istniejący formant nie spełnia Twoich potrzeb, Windows Forms również obsługuje tworzenie własnych niestandardowych formantów przy użyciu klasy <xref:System.Windows.Forms.UserControl>.

Windows Forms ma rozbudowane kontrolki interfejsu użytkownika, które emulują funkcje aplikacji wysokiej klasy, takich jak Microsoft Office. Za pomocą kontrolki <xref:System.Windows.Forms.ToolStrip> i <xref:System.Windows.Forms.MenuStrip>, można tworzyć paski narzędzi i menu, które zawierają tekst i obrazy, wyświetlać podmenu i hostować inne kontrolki, takie jak pola tekstowe i pola kombi.

Za pomocą narzędzia do przeciągania i upuszczania formularzy programu Visual Studio możesz łatwo tworzyć Windows Forms aplikacje: po prostu wybierz kontrolki z kursorem i umieść je w dowolnym miejscu w formularzu. Projektant udostępnia narzędzia takie jak linie siatki i "Przyciągaj linie", aby zastanowić się, że nie można dostosować formantów. Niezależnie od tego, czy używasz programu Visual Studio, czy kompilować w wierszu polecenia, można użyć formantów <xref:System.Windows.Forms.FlowLayoutPanel>, <xref:System.Windows.Forms.TableLayoutPanel> i <xref:System.Windows.Forms.SplitContainer> do tworzenia zaawansowanych układów formularzy o minimalnym czasie i wysiłku.

### <a name="custom-ui-elements"></a>Niestandardowe elementy interfejsu użytkownika

Na koniec, jeśli trzeba utworzyć własne niestandardowe elementy interfejsu użytkownika, przestrzeń nazw <xref:System.Drawing> zawiera wszystkie klasy potrzebne do renderowania linii, okręgów i innych kształtów bezpośrednio w formularzu.

Informacje krok po kroku dotyczące korzystania z tych funkcji można znaleźć w następujących tematach pomocy.

|Do|Zobacz|
|--------|---------|
|Tworzenie nowej aplikacji Windows Forms przy użyciu programu Visual Studio|[Samouczek 1: Tworzenie przeglądarki obrazów](/visualstudio/ide/tutorial-1-create-a-picture-viewer)|
|Używanie formantów na formularzach|[Instrukcje: dodawanie kontrolek do formularzy Windows Forms](../../../framework/winforms/controls/how-to-add-controls-to-windows-forms.md)|
|Tworzenie grafiki przy użyciu <xref:System.Drawing>|[Wprowadzenie do programowania grafiki](../../../framework/winforms/advanced/getting-started-with-graphics-programming.md)|
|Tworzenie niestandardowych kontrolek|[Instrukcje: dziedziczenie z klasy UserControl](../../../framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)|

## <a name="displaying-and-manipulating-data"></a>Wyświetlanie i manipulowanie danymi

Wiele aplikacji musi wyświetlać dane z bazy danych, pliku XML, usługi sieci Web XML lub innego źródła danych. Windows Forms zapewnia elastyczną kontrolkę o nazwie kontrolkę <xref:System.Windows.Forms.DataGridView> do renderowania takich danych tabelarycznych w tradycyjnym formacie wiersza i kolumny, tak aby każda część danych zajmowała swoją własną komórkę. Za pomocą <xref:System.Windows.Forms.DataGridView> można dostosować wygląd poszczególnych komórek, zablokować dowolne wiersze i kolumny w miejscu oraz wyświetlać złożone kontrolki wewnątrz komórek, między innymi.

Łączenie ze źródłami danych za pośrednictwem sieci to proste zadanie z Windows Forms inteligentnymi klientami. Składnik <xref:System.Windows.Forms.BindingSource>, nowy z Windows Forms w programie Visual Studio 2005 i .NET Framework 2,0, reprezentuje połączenie ze źródłem danych i udostępnia metody wiązania danych z kontrolkami, nawigowanie do poprzednich i następnych rekordów, edytowanie rekordów i zapisywanie zmiany z powrotem do oryginalnego źródła. Kontrolka <xref:System.Windows.Forms.BindingNavigator> udostępnia prosty interfejs między składnikiem <xref:System.Windows.Forms.BindingSource>, aby umożliwić użytkownikom Nawigowanie między rekordami.

### <a name="data-bound-controls"></a>Formanty powiązane z danymi

Kontrolki powiązane z danymi można łatwo tworzyć przy użyciu okna źródła danych, w którym są wyświetlane źródła danych, takie jak bazy danych, usługi sieci Web i obiekty w projekcie. Formanty powiązane z danymi można tworzyć, przeciągając elementy z tego okna na formularze w projekcie. Dane można także powiązać z danymi istniejącymi kontrolkami, przeciągając obiekty z okna źródła danych do istniejących kontrolek.

### <a name="settings"></a>Ustawienia

Innym typem powiązania danych, którymi można zarządzać w Windows Forms jest ustawienia. Większość aplikacji inteligentnych klienta musi przechowywać pewne informacje o stanie czasu wykonywania, takie jak ostatni znany rozmiar formularzy i zachować dane preferencji użytkownika, takie jak domyślne lokalizacje plików zapisanych. Funkcja ustawienia aplikacji eliminuje te wymagania, udostępniając łatwy sposób przechowywania obu typów ustawień na komputerze klienckim. Po zdefiniowaniu przy użyciu programu Visual Studio lub edytora kodu te ustawienia są utrwalane jako XML i automatycznie odczytywane w pamięci w czasie wykonywania.

Informacje krok po kroku dotyczące korzystania z tych funkcji można znaleźć w następujących tematach pomocy.

|Do|Zobacz|
|--------|---------|
|Korzystanie ze składnika <xref:System.Windows.Forms.BindingSource>|[Instrukcje: powiązywanie kontrolek formularzy Windows Forms ze składnikiem BindingSource przy użyciu narzędzia Projektant](../../../framework/winforms/controls/bind-wf-controls-with-the-bindingsource.md)|
|Współpraca ze źródłami danych ADO.NET|[Instrukcje: filtrowanie i sortowanie danych ADO.NET za pomocą składnika BindingSource formularzy Windows Forms](../../../framework/winforms/controls/sort-and-filter-ado-net-data-with-wf-bindingsource-component.md)|
|Korzystanie z okna źródła danych|[Przewodnik: wyświetlanie danych w formularzu systemu Windows](/visualstudio/data-tools/accessing-data-in-visual-studio)|

## <a name="deploying-applications-to-client-computers"></a>Wdrażanie aplikacji na komputerach klienckich

Po napisaniu aplikacji należy wysłać ją do użytkowników, aby mogli ją zainstalować i uruchamiać na własnych komputerach klienckich. Korzystając z technologii ClickOnce, można wdrażać aplikacje z poziomu programu Visual Studio za pomocą zaledwie kilku kliknięć i udostępnić użytkownikom adresy URL wskazujące aplikację w sieci Web. Technologia ClickOnce zarządza wszystkimi elementami i zależnościami w aplikacji i gwarantuje, że aplikacja jest poprawnie zainstalowana na komputerze klienckim.

Aplikacje ClickOnce można skonfigurować tak, aby były uruchamiane tylko wtedy, gdy użytkownik jest połączony z siecią lub do uruchamiania w trybie online i offline. Po określeniu, że aplikacja powinna obsługiwać działanie w trybie offline, ClickOnce dodaje link do aplikacji w menu **Start** użytkownika, dzięki czemu użytkownik może ją otworzyć bez użycia adresu URL.

Po zaktualizowaniu aplikacji należy opublikować nowy manifest wdrożenia i nową kopię aplikacji na serwerze sieci Web. Technologia ClickOnce wykrywa, czy jest dostępna aktualizacja i uaktualnia instalację użytkownika. do aktualizowania starych zestawów nie jest wymagane programowanie niestandardowe.

Aby zapoznać się z pełnym wprowadzeniem do technologii ClickOnce, zobacz [zabezpieczenia i wdrażanie technologii ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment). Informacje krok po kroku dotyczące korzystania z tych funkcji można znaleźć w następujących tematach pomocy:

|Do|Zobacz|
|--------|---------|
|Wdrażanie aplikacji przy użyciu technologii ClickOnce|[Instrukcje: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](/visualstudio/deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard)<br /><br /> [Przewodnik: ręczne wdrażanie aplikacji ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)|
|Aktualizowanie wdrożenia ClickOnce|[Instrukcje: zarządzanie aktualizacji dla aplikacji ClickOnce](/visualstudio/deployment/how-to-manage-updates-for-a-clickonce-application)|
|Zarządzanie zabezpieczeniami przy użyciu technologii ClickOnce|[Instrukcje: włączenie ustawień zabezpieczeń technologii ClickOnce](/visualstudio/deployment/how-to-enable-clickonce-security-settings)|

## <a name="other-controls-and-features"></a>Inne kontrolki i funkcje

W Windows Forms istnieje wiele innych funkcji, które umożliwiają szybkie i łatwe wdrażanie typowych zadań, takich jak obsługa tworzenia okien dialogowych, drukowanie, Dodawanie pomocy i dokumentacji oraz lokalizowanie aplikacji w wielu językach. Ponadto Windows Forms opiera się na niezawodnym systemie zabezpieczeń .NET Framework, co pozwala na wydawanie klientom bardziej bezpiecznych aplikacji.

Informacje krok po kroku dotyczące korzystania z tych funkcji można znaleźć w następujących tematach pomocy:

|Do|Zobacz|
|--------|---------|
|Drukowanie zawartości formularza|[Instrukcje: drukowanie grafiki w formularzach Windows Forms](../../../framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)<br /><br /> [Instrukcje: wyświetlanie podglądu wydruku w formularzach Windows Forms](../../../framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)|
|Dowiedz się więcej o zabezpieczeniach Windows Forms|[Przegląd zabezpieczeń w formularzach Windows Forms](../../../framework/winforms/security-in-windows-forms-overview.md)|

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- [Windows Forms — omówienie](../../../framework/winforms/windows-forms-overview.md)
- [My.Forms, obiekt](../../../visual-basic/language-reference/objects/my-forms-object.md)
