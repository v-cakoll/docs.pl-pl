---
title: Omówienie
description: Dowiedz się, jak za pomocą Windows Forms tworzyć inteligentnych klientów spełniających potrzeby współczesnych przedsiębiorstw i użytkowników końcowych.
ms.date: 03/30/2017
helpviewer_keywords:
- smart clients
- Windows Forms, about Windows Forms
ms.assetid: 3a2b6284-c8d6-4e1c-8c69-0bed38f38cd4
ms.openlocfilehash: 820d5bae54ecb5a868314197d6a7e45e097b57de
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325991"
---
# <a name="windows-forms-overview"></a>Przegląd Windows Forms

W poniższych omówieniach omówiono zalety inteligentnych aplikacji klienckich, główne funkcje programowania Windows Forms, a także sposób korzystania z Windows Forms do tworzenia inteligentnych klientów, którzy spełniają wymagania współczesnych przedsiębiorstw i użytkowników końcowych.

## <a name="windows-forms-and-smart-client-apps"></a>Windows Forms i inteligentne aplikacje klienckie

 Windows Forms tworzenia inteligentnych klientów. *Klienci inteligentni* są rozbudowanymi graficznie aplikacjami, które są łatwe do wdrożenia i aktualizacji, mogą współpracować w przypadku, gdy są połączone z Internetem lub z nimi odłączane, a także mogą uzyskiwać dostęp do zasobów na komputerze lokalnym w bezpieczniejszy sposób niż tradycyjne aplikacje systemu Windows.

### <a name="build-rich-interactive-user-interfaces"></a>Kompiluj rozbudowane, interaktywne interfejsy użytkownika

 Windows Forms to inteligentna technologia klienta dla .NET Framework, zestaw bibliotek zarządzanych, które upraszczają typowe zadania aplikacji, takie jak odczytywanie i zapisywanie w systemie plików. W przypadku korzystania ze środowiska programistycznego, takiego jak Visual Studio, można utworzyć Windows Forms aplikacje inteligentnego klienta, które wyświetlają informacje, żądają danych wejściowych od użytkowników i komunikują się z komputerami zdalnymi za pośrednictwem sieci.

 W Windows Forms *formularz* jest obszarem wizualnym, na którym są wyświetlane informacje dla użytkownika. Zazwyczaj tworzysz Windows Forms aplikacje przez dodanie formantów do formularzy i opracowywanie odpowiedzi do akcji użytkownika, takich jak kliknięcia myszą lub naciśnięcia klawiszy. *Kontrolka* to dyskretny element interfejsu użytkownika, który wyświetla dane lub akceptuje dane wejściowe.

 Gdy użytkownik robi coś w formularzu lub jednej z jego kontrolek, akcja generuje zdarzenie. Aplikacja reaguje na te zdarzenia za pomocą kodu i przetwarza zdarzenia, gdy wystąpią. Aby uzyskać więcej informacji, zobacz [Tworzenie programów obsługi zdarzeń w Windows Forms](creating-event-handlers-in-windows-forms.md).

 Windows Forms zawiera różne kontrolki, które można dodać do formularzy: kontrolki, które wyświetlają pola tekstowe, przyciski, pola rozwijane, przyciski radiowe, a nawet strony sieci Web. Aby uzyskać listę wszystkich kontrolek, których można użyć na formularzu, zobacz [kontrolki do użycia na Windows Forms](./controls/controls-to-use-on-windows-forms.md). Jeśli istniejący formant nie spełnia Twoich potrzeb, Windows Forms również obsługuje tworzenie własnych niestandardowych formantów przy użyciu <xref:System.Windows.Forms.UserControl> klasy.

 Windows Forms ma rozbudowane kontrolki interfejsu użytkownika, które emulują funkcje aplikacji wysokiej klasy, takich jak Microsoft Office. Korzystając z <xref:System.Windows.Forms.ToolStrip> <xref:System.Windows.Forms.MenuStrip> kontrolki i, można tworzyć paski narzędzi i menu, które zawierają tekst i obrazy, wyświetlać podmenu i hostować inne kontrolki, takie jak pola tekstowe i pola kombi.

 Za pomocą przeciągania i upuszczania **Projektant formularzy systemu Windows** w programie Visual Studio można łatwo tworzyć aplikacje Windows Forms. Po prostu zaznacz kontrolki z kursorem i Dodaj je w dowolnym miejscu w formularzu. Projektant udostępnia narzędzia, takie jak linie siatki i linie przyciągania, aby zastanowić się, że kontrolki nie są dostosowywane. Niezależnie od tego, czy używasz programu Visual Studio, czy kompilować w wierszu polecenia, możesz <xref:System.Windows.Forms.FlowLayoutPanel> użyć <xref:System.Windows.Forms.TableLayoutPanel> formantów i, <xref:System.Windows.Forms.SplitContainer> Aby utworzyć zaawansowane układy formularzy w krótszym czasie.

 Na koniec, jeśli trzeba utworzyć własne niestandardowe elementy interfejsu użytkownika, <xref:System.Drawing> przestrzeń nazw zawiera duży wybór klas do renderowania linii, okręgów i innych kształtów bezpośrednio w formularzu.

> [!NOTE]
> Kontrolki Windows Forms nie są przeznaczone do organizowania w różnych domenach aplikacji. Z tego powodu firma Microsoft nie obsługuje przekazywania kontrolki Windows Forms między <xref:System.AppDomain> granicami, mimo że <xref:System.Windows.Controls.Control> Typ podstawowy <xref:System.MarshalByRefObject> wydaje się wskazywać, że jest to możliwe. Windows Forms aplikacje, które mają wiele domen aplikacji, są obsługiwane, o ile nie przechodzą żadnych kontrolek Windows Forms między granicami domeny aplikacji.

#### <a name="create-forms-and-controls"></a>Tworzenie formularzy i kontrolek

Informacje krok po kroku dotyczące korzystania z tych funkcji można znaleźć w następujących tematach pomocy.

|Opis|Temat pomocy|
|-----------------|----------------|
|Używanie formantów na formularzach|[Porady: dodawanie formantów do formularzy systemu Windows](./controls/how-to-add-controls-to-windows-forms.md)|
|Korzystanie z <xref:System.Windows.Forms.ToolStrip> kontrolki|[Instrukcje: tworzenie podstawowych kontrolek ToolStrip z elementami standardowymi przy użyciu narzędzia Projektant](./controls/create-a-basic-wf-toolstrip-with-standard-items-using-the-designer.md)|
|Tworzenie grafiki przy użyciu<xref:System.Drawing>|[Wprowadzenie do programowania grafiki](./advanced/getting-started-with-graphics-programming.md)|
|Tworzenie niestandardowych formantów|[Instrukcje: dziedziczenie z klasy UserControl](./controls/how-to-inherit-from-the-usercontrol-class.md)|

### <a name="display-and-manipulate-data"></a>Wyświetlanie i manipulowanie danymi
 Wiele aplikacji musi wyświetlać dane z bazy danych, pliku XML, usługi sieci Web XML lub innego źródła danych. Windows Forms zapewnia elastyczną kontrolkę, która nazywa <xref:System.Windows.Forms.DataGridView> formant do wyświetlania takich danych tabelarycznych w tradycyjnym formacie wiersza i kolumny, tak aby każda część danych zajmowała własną komórkę. Korzystając z programu <xref:System.Windows.Forms.DataGridView> , można dostosować wygląd poszczególnych komórek, zablokować dowolne wiersze i kolumny w miejscu oraz wyświetlać złożone kontrolki wewnątrz komórek, między innymi.

 Łączenie ze źródłami danych za pośrednictwem sieci to proste zadanie z Windows Forms inteligentnymi klientami. <xref:System.Windows.Forms.BindingSource>Składnik reprezentuje połączenie ze źródłem danych i udostępnia metody wiązania danych z kontrolkami, nawigowanie do poprzednich i następnych rekordów, edytowanie rekordów i zapisywanie zmian z powrotem do oryginalnego źródła. <xref:System.Windows.Forms.BindingNavigator>Kontrolka udostępnia prosty interfejs <xref:System.Windows.Forms.BindingSource> dla składnika, dla którego użytkownicy mogą przechodzić między rekordami.

 Formanty powiązane z danymi można łatwo tworzyć przy użyciu okna źródła danych. W oknie są wyświetlane źródła danych, takie jak bazy danych, usługi sieci Web i obiekty w projekcie. Formanty powiązane z danymi można tworzyć, przeciągając elementy z tego okna na formularze w projekcie. Dane można także powiązać z danymi istniejącymi kontrolkami, przeciągając obiekty z okna źródła danych do istniejących kontrolek.

 Innym typem powiązania danych, którymi można zarządzać w Windows Forms jest *Ustawienia*. Większość inteligentnych aplikacji klienckich musi przechowywać pewne informacje o stanie czasu wykonywania, takie jak ostatni znany rozmiar formularzy i zachować dane preferencji użytkownika, takie jak domyślne lokalizacje plików zapisanych. Funkcja ustawienia aplikacji eliminuje te wymagania, udostępniając łatwy sposób przechowywania obu typów ustawień na komputerze klienckim. Po zdefiniowaniu tych ustawień przy użyciu programu Visual Studio lub edytora kodu ustawienia są utrwalane jako XML i automatycznie odczytywane w pamięci w czasie wykonywania.

#### <a name="display-and-manipulate-data"></a>Wyświetlanie i manipulowanie danymi

Informacje krok po kroku dotyczące korzystania z tych funkcji można znaleźć w następujących tematach pomocy.

|Opis|Temat pomocy|
|-----------------|----------------|
|Korzystanie z <xref:System.Windows.Forms.BindingSource> składnika|[Instrukcje: powiązywanie kontrolek formularzy Windows Forms ze składnikiem BindingSource przy użyciu narzędzia Projektant](./controls/bind-wf-controls-with-the-bindingsource.md)|
|Praca ze źródłami danych ADO.NET|[Instrukcje: filtrowanie i sortowanie danych ADO.NET za pomocą składnika BindingSource formularzy Windows Forms](./controls/sort-and-filter-ado-net-data-with-wf-bindingsource-component.md)|
|Korzystanie z okna źródła danych|[Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio)|
|Korzystanie z ustawień aplikacji|[Instrukcje: tworzenie ustawień aplikacji](./advanced/how-to-create-application-settings.md)|

### <a name="deploy-apps-to-client-computers"></a>Wdrażanie aplikacji na komputerach klienckich

Po napisaniu aplikacji należy wysłać ją do użytkowników, aby mogli ją instalować i uruchamiać na własnych komputerach klienckich. Korzystając z technologii ClickOnce, można wdrożyć aplikacje z poziomu programu Visual Studio za pomocą zaledwie kilku kliknięć i udostępnić użytkownikom adresy URL wskazujące aplikację w sieci Web. Technologia ClickOnce zarządza wszystkimi elementami i zależnościami w aplikacji i gwarantuje, że aplikacja jest poprawnie zainstalowana na komputerze klienckim.

Aplikacje ClickOnce można skonfigurować tak, aby były uruchamiane tylko wtedy, gdy użytkownik jest połączony z siecią lub do uruchamiania w trybie online i offline. Po określeniu, że aplikacja powinna obsługiwać działanie w trybie offline, ClickOnce dodaje link do aplikacji w menu **Start** użytkownika. Następnie użytkownik może otworzyć aplikację bez użycia adresu URL.

Po zaktualizowaniu aplikacji należy opublikować nowy manifest wdrożenia i nową kopię aplikacji na serwerze sieci Web. Technologia ClickOnce wykryje, że dostępna jest aktualizacja, a następnie uaktualnienie instalacji użytkownika. do aktualizowania starych zestawów nie jest wymagane programowanie niestandardowe.

#### <a name="deploy-clickonce-apps"></a>Wdrażanie aplikacji ClickOnce

Aby zapoznać się z pełnym wprowadzeniem do technologii ClickOnce, zobacz [zabezpieczenia i wdrażanie technologii ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment). Informacje krok po kroku dotyczące korzystania z tych funkcji można znaleźć w następujących tematach pomocy:

|Opis|Temat pomocy|
|-----------------|----------------|
|Wdrażanie aplikacji za pomocą technologii ClickOnce|[Instrukcje: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](/visualstudio/deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard)<br /><br /> [Wskazówki: ręczne wdrażanie aplikacji ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)|
|Aktualizowanie wdrożenia ClickOnce|[Porady: zarządzanie aktualizacji dla aplikacji ClickOnce](/visualstudio/deployment/how-to-manage-updates-for-a-clickonce-application)|
|Zarządzanie zabezpieczeniami przy użyciu technologii ClickOnce|[Instrukcje: włączenie ustawień zabezpieczeń technologii ClickOnce](/visualstudio/deployment/how-to-enable-clickonce-security-settings)|

### <a name="other-controls-and-features"></a>Inne kontrolki i funkcje

W Windows Forms istnieje wiele innych funkcji, które umożliwiają szybkie i łatwe wdrażanie typowych zadań, takich jak obsługa tworzenia okien dialogowych, drukowanie, Dodawanie pomocy i dokumentacji oraz lokalizowanie aplikacji w wielu językach. Ponadto Windows Forms opiera się na niezawodnym systemie zabezpieczeń .NET Framework. Dzięki temu systemowi można wydać klientom więcej bezpiecznych aplikacji.

#### <a name="implement-other-controls-and-features"></a>Zaimplementuj inne kontrolki i funkcje

Informacje krok po kroku dotyczące korzystania z tych funkcji można znaleźć w następujących tematach pomocy.

|Opis|Temat pomocy|
|-----------------|----------------|
|Drukowanie zawartości formularza|[Instrukcje: drukowanie grafiki w formularzach Windows Forms](./advanced/how-to-print-graphics-in-windows-forms.md)<br /><br /> [Instrukcje: wyświetlanie podglądu wydruku w formularzach Windows Forms](./advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)|
|Dowiedz się więcej o zabezpieczeniach Windows Forms|[Przegląd zabezpieczeń w formularzach systemu Windows](security-in-windows-forms-overview.md)|

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do formularzy systemu Windows](getting-started-with-windows-forms.md)
- [Tworzenie nowego formularza systemu Windows](creating-a-new-windows-form.md)
- [ToolStrip — Informacje o formancie](./controls/toolstrip-control-overview-windows-forms.md)
- [DataGridView — Informacje o formancie](./controls/datagridview-control-overview-windows-forms.md)
- [BindingSource — Informacje o składniku](./controls/bindingsource-component-overview.md)
- [Przegląd ustawień aplikacji](./advanced/application-settings-overview.md)
- [Bezpieczeństwo i wdrażanie technologii ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment)
