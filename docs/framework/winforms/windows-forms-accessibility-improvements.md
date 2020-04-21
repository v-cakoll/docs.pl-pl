---
title: Ulepszenia ułatwień dostępu formularzy systemu Windows
description: Dowiedz się więcej o sposobach, w jakie podstawowe formularze systemu Windows .NET próbują poprawić dostępność w porównaniu z formularzami systemu Windows programu .NET Framework.
ms.date: 04/20/2020
helpviewer_keywords:
- Windows Forms accessibility
- accessibility
author: M-Lipin
ms.openlocfilehash: 30eb8b3bd0aaf646ea23f4f036e822f9bba78dc4
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739753"
---
# <a name="accessibility-improvements-in-windows-forms-controls-for-net-core-30"></a>Ulepszenia ułatwień dostępu w formantach formularzy systemu Windows dla programu .NET Core 3.0

Formularze systemu Windows nadal ulepszają sposób działania z technologiami ułatwień dostępu, aby lepiej obsługiwać klientów formularzy systemu Windows. Te ulepszenia obejmują następujące zmiany:

- Zmiany w różnych obszarach interakcji z aplikacjami klienckimi ułatwień dostępu, w tym Narratorem.
- Zmiany w hierarchii dostępne (poprawa nawigacji za pośrednictwem drzewa automatyzacji interfejsu użytkownika).
- Zmiany w nawigacji za pomocą klawiatury.

> [!IMPORTANT]
> Zmiany ułatwień dostępu wprowadzone w systemie .NET Framework 4.7.1 za pośrednictwem platformy .NET Framework 4.8 są uwzględnione w systemie .NET Core 3.0 i powyżej i są domyślnie włączone. Program .NET Framework obsługiwał przełączniki zgodności, które umożliwiały aplikacjom rezygnację z nowego zachowania ułatwień dostępu. Z drugiej strony .NET Core nie obsługuje tych ustawień i nie zezwala aplikacjom na rezygnację z zachowania ułatwień dostępu.
  
Począwszy od programu .NET Core 3.0, aplikacje Windows Forms korzystają ze wszystkich nowych funkcji ułatwień dostępu (wprowadzonych w programie .NET Framework 4.7.1 - 4.8) bez dodatkowej konfiguracji.

## <a name="listbox-accessibility-support"></a>Obsługa ułatwień dostępu listbox

Następujące zmiany mają <xref:System.Windows.Forms.ListBox> zastosowanie do formantu:

- Włączona obsługa automatyzacji `ListBox` interfejsu użytkownika dla sterowania.
- Ulepszona `ListBox` obsługa ułatwień dostępu, dodając <xref:System.Windows.Automation.ScrollItemPattern> do `ListBox` elementów i zwiększając podnoszenie i obsługę zdarzeń ułatwień dostępu oraz nawigację Narratora za pośrednictwem elementów (nawigacja caps lock nie jest poprawna i nie rzuca nawigacji poza formantem przypadkowo).

## <a name="checkedlistbox-accessibility-support"></a>Obsługa ułatwień dostępu CheckedListBox

Następujące zmiany mają <xref:System.Windows.Forms.CheckedListBox> zastosowanie do formantu:

- Poprawiono `CheckedListBox` granice dostarczone przez właściwości ułatwień dostępu dla wpisów.
- Ulepszona `ListBox` `CheckedListBox` ogólna i dostępność: poprawione wartości właściwości i modelu zdarzeń.

## <a name="combobox-accessibility-support"></a>Obsługa ułatwień dostępu combobox

Następujące zmiany mają <xref:System.Windows.Forms.ComboBox> zastosowanie do formantu:

- Zaktualizowano proces `ComboBox` uzyskiwania obiektów ułatwień dostępu elementów, aby włączyć generowanie identyfikatorów elementów zamiast uzyskiwania kodów skrótów z elementów, co może być niebezpieczne w przypadku zastąpienia <xref:System.Object.GetHashCode%2A> funkcji.

## <a name="datagridview-accessibility-support"></a>Obsługa ułatwień dostępu DataGridView

Następujące zmiany mają <xref:System.Windows.Forms.DataGridView> zastosowanie do formantu:

- Poprawione `DataGridView.Bounds` przez właściwości ułatwień dostępu dla kolumn, wierszy, komórek i odpowiednich nagłówków, poprawiono wydajność obliczania prostokąta ograniczającego. Wszystkie granice dostępności są reprezentowane poprawnie, biorąc pod uwagę granice całego formantu, wraz z jego rzutnią.
- Poprawiona `Value.IsReadOnly` wartość właściwości zapewniająca dostępne aplikacje klienckie. Właściwość pokazuje `IsReadOnly` teraz poprawny stan dla komórek.
- Naprawiono błąd, który powodował podnoszenie <xref:System.Windows.Forms.DataGridView.CellParsing> zdarzeń przy pierwszej zmianie komórki. Wartość komórki można zmienić bez `DataGridView` żadnych problemów, w tym pierwszej interakcji sterowania.
- Poprawiono `DataGridView` kontrast kolorów tła podczas korzystania z motywów o wysokim kontraście systemu Windows. Zmieniono domyślny `DataGridView` kolor wsteczny podczas używania motywów HC#1, HC#2 i HC Black.

## <a name="propertygrid-accessibility-support"></a>Pomoc techniczna aplikacji PropertyGrid Accessibility

Następujące zmiany mają <xref:System.Windows.Forms.PropertyGrid> zastosowanie do formantu:

- Poprawione `PropertyGrid.Bounds` przez właściwości ułatwień dostępu dla wpisów siatki, zwiększona wydajność obliczania prostokąta ograniczającego. Na razie wszystkie granice dostępności są reprezentowane poprawnie, biorąc pod uwagę granice całego formantu, wraz z jego rzutnią.
- Poprawiono dostępne nazwy i opisy podkontroli, aby nie uwzględniać nazw typów formantu i aby uniknąć podwójnego ogłaszania nazw typów formantu.

## <a name="toolstrip-accessibility-support"></a>Pomoc techniczna dotycząca ułatwień dostępu toolstrip

Następujące zmiany mają <xref:System.Windows.Forms.ToolStrip> zastosowanie do formantu:

- Ulepszona `ToolStrip`nawigacja po , `MenuStrip`i `StatusStrip` elementy. Poprawiono `ToolStrip` `MenuStrip` i shift-tab nawigacji, back-pętli elementów menu po naciśnięciu shift-tab strzałka w górę, który przechodzi do dolnego elementu menu.
- Ulepszona nawigacja, `MenuStrip` poprawione menu dostępne typy kontroli dla podmenu, aby podmenu typu "Menu" zamiast "MenuItem".

## <a name="printpreviewcontrol-and-printpreviewdialog-accessibility-support"></a>Obsługa ułatwień dostępu PrintPreviewControl i PrintPreviewDialog

Następujące zmiany dotyczą kontrolek drukowania:

- Ulepszona dostępna nawigacja (w tym nawigacja Narratora) za pomocą elementów menu.
- Ulepszone motywy o wysokim kontraście obsługują i sprawiły, że element sterujący stał się bardziej kontrastowany.

## <a name="stringcollectioneditor-accessibility-support"></a>Obsługa ułatwień dostępu StringCollectionEditor

Projektant formularzy systemu Windows używa teraz edytora kolekcji ciągów z ulepszoną obsługą ułatwień dostępu.

## <a name="monthcalendar-accessibility-support-available-in-net-core-31"></a>Pomoc techniczna dotycząca ułatwień dostępu MonthCalendar (dostępna w systemie .NET Core 3.1)

Następujące zmiany mają <xref:System.Windows.Forms.MonthCalendar> zastosowanie do formantu:

- Dodano dostawców serwerów `MonthCalendar` automatyzacji interfejsu użytkownika do kontrolowania, dodano wzorzec siatki automatyzacji interfejsu użytkownika i dostawców wzorców tabel.
- Zmieniono typ formantu dostępnej _dla tabeli_ na typ formantu dostępny `MonthCalendar` dla _kalendarza,_ `MonthCalendar` z wyjątkiem przypadku, gdy formant ma poprzednią kontrolkę etykiety definiującą nazwę dostępną dla formantu, w tym konkretnym przypadku dostępny typ formantu staje się _tabelą_.
- Ulepszone ogłoszenie wybranej daty `MonthCalendar` kontroli.
- Ulepszona `MonthCalendar` obsługa sterowania czytnikami ekranu i innymi narzędziami ułatwień dostępu. W tej chwili użytkownicy mogą poruszać się po elementach sterowania i wchodzić w interakcje z tymi elementami za pomocą danych wejściowych tylko za pomocą klawiatury. W Narratorze użyj klawiszy CAPS + klawiszy strzałek, aby nawigować po elementach sterujących i caps + Enter, aby wywołać domyślną akcję elementu.
- Ulepszona nawigacja `MonthCalendar` klawiszy strzałek między elementami podrzędnymi dzięki prostokątowi ogniskowania: niebieski prostokąt ostrości narratora.
- Ulepszona dostępność dla `MonthCalendar` akcji testu trafień dla elementów sterujących, aby umożliwić uzyskanie `MonthCalendar` elementu dostęp do dzieci przez dostarczone współrzędne.

## <a name="tooltips-accessibility-available-in-net-core-31"></a>Dostępność etykietek narzędziowych (dostępna w systemie .NET Core 3.1)

- Dodano możliwość ogłaszania tekstu etykietki narzędzia przez aplikacje czytnika ekranu, takie jak NVDA i Narrator. Aplikacja czytnika ekranu może teraz ogłaszać tekst klawiatury lub myszki etykietki narzędzia dowolnego formantu Windows Forms skonfigurowanej do pokazywania etykietek narzędzi.

## <a name="ui-automation-support-for-datagridview-propertygrid-listbox-combobox-toolstrip-and-other-controls"></a>Obsługa automatyzacji interfejsu użytkownika dla datagridview, PropertyGrid, ListBox, ComboBox, ToolStrip i innych formantów

Obsługa automatyzacji interfejsu użytkownika jest włączona dla formantów w czasie wykonywania, ale nie jest używana w czasie projektowania. Aby zapoznać się z omówieniem automatyzacji interfejsu użytkownika, zobacz [Omówienie automatyzacji interfejsu użytkownika](https://docs.microsoft.com/dotnet/framework/ui-automation/ui-automation-overview).

## <a name="see-also"></a>Zobacz też

- [Najważniejsze wskazówki dotyczące ułatwień dostępu](../ui-automation/accessibility-best-practices.md).
