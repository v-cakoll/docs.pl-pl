---
title: Windows Forms dodać elementu konfiguracji
ms.date: 04/07/2017
helpviewer_keywords:
- Windows Forms Add configuration element
- configuring Windows Forms applications
ms.assetid: 3e3e04de-99d1-4658-b716-44cb669d9589
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb607af0933ea64b7d67f8ed082ffce6e7d21f51
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913061"
---
# <a name="windows-forms-add-configuration-element"></a>Windows Forms dodać elementu konfiguracji

`<add>` Element dodaje wstępnie zdefiniowany klucz, który określa, czy aplikacja formularza systemu Windows obsługuje funkcje dodane do Windows Forms aplikacji w .NET Framework 4,7 lub nowszych.

## <a name="syntax"></a>Składnia

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="key-name" value="key-value" />
</System.Windows.Forms.ApplicationConfigurationSection>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

| Atrybut | Opis |
| --------- | ----------- |
| `key`     | Atrybut wymagany. Wstępnie zdefiniowana nazwa klucza odpowiadająca określonej Windows Forms funkcji dostosowywalnej. |
| `value`   | Atrybut wymagany. Wartość do przypisania `key`. |

### <a name="key-attribute-names-and-associated-values"></a>`key`nazwy atrybutów i skojarzone wartości

| `key`Nazwij | Wartości | Opis |
| ---------- | ------ | ----------- |
| "AnchorLayout.DisableSinglePassControlScaling" | "true"&#124;"false" | Wskazuje, czy kontrolki zakotwiczone są skalowane w jednym przebiegu. "true", aby wyłączyć pojedyncze skalowanie; w przeciwnym razie false. Aby uzyskać więcej informacji, zobacz sekcję "skalowanie pojedynczego przebiegu" w obszarze [uwagi](#remarks) . |
| "DpiAwareness" | "PerMonitorV2"&#124;"false" | Wskazuje, czy aplikacja obsługuje DPI. Ustaw klucz na wartość "PerMonitorV2", aby obsługiwać rozpoznawanie dpi; w przeciwnym razie ustaw dla niego wartość "false". Rozpoznawanie DPI to funkcja opcjonalna. Aby skorzystać z obsługi Windows Forms "wysokiej rozdzielczości DPI, należy ustawić jej wartość na" PerMonitorV2 ". Zobacz sekcję [uwagi](#remarks) , aby uzyskać więcej informacji. |
| "CheckedListBox.DisableHighDpiImprovements" | "true"&#124;"false" | Wskazuje, czy <xref:System.Windows.Forms.CheckedListBox> kontrolka wykorzystuje ulepszenia skalowania i układu wprowadzone w .NET Framework 4,7. "true", aby zrezygnować ze skalowania i ulepszeń układu; w przeciwnym razie "false". |
| "DataGridView.DisableHighDpiImprovements" | "true"&#124;"false" | Wskazuje, czy <xref:System.Windows.Forms.DataGridView> ulepszenia skalowania i regulacji układu wprowadzone w .NET Framework 4,7. "prawda", aby zrezygnować z świadomości DPI; "false" w przeciwnym razie. |
| "DisableDpiChangedMessageHandling" | "true"&#124;"false" | "true", aby zrezygnować z otrzymywania komunikatów związanych ze zmianami skalowania DPI; "false" w przeciwnym razie. Zobacz sekcję [uwagi](#remarks) , aby uzyskać więcej informacji. |
| EnableWindowsFormsHighDpiAutoResizing | "true"&#124;"false" | Wskazuje, czy rozmiar aplikacji Windows Forms jest automatycznie zmieniany z powodu zmian skalowania DPI. "prawda", aby włączyć automatyczną zmianę rozmiarów; w przeciwnym razie false. |
| "Form. DisableSinglePassControlScaling" | "true"&#124;"false" | Wskazuje, <xref:System.Windows.Forms.Form> czy element jest skalowany w jednym przebiegu. "true", aby wyłączyć skalowanie jednokrotne; w przeciwnym razie false. Aby uzyskać więcej informacji, zobacz sekcję "skalowanie pojedynczego przebiegu" w obszarze [uwagi](#remarks) . |
| "MonthCalendar. DisableSinglePassControlScaling" | "true"&#124;"false" | Wskazuje, <xref:System.Windows.Forms.MonthCalendar> czy kontrolka jest skalowana w jednym przebiegu. "true", aby wyłączyć skalowanie jednokrotne; w przeciwnym razie false. Aby uzyskać więcej informacji, zobacz sekcję "skalowanie pojedynczego przebiegu" w obszarze [uwagi](#remarks) . |
| "Toolstrip.DisableHighDpiImprovements" | "true"&#124;"false" | Wskazuje, czy <xref:System.Windows.Forms.ToolStrip> kontrolka wykorzystuje ulepszenia skalowania i układu wprowadzone w .NET Framework 4,7. "prawda", aby zrezygnować z świadomości DPI; "false" w przeciwnym razie. |

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |
| ------- | ----------- |
| [`<System.Windows.Forms.ApplicationConfigurationSection>`](index.md) | Konfiguruje obsługę nowych funkcji aplikacji Windows Forms. |

## <a name="remarks"></a>Uwagi

Począwszy od .NET Framework 4,7, `<System.Windows.Forms.ApplicationConfigurationSection>` element pozwala konfigurować aplikacje Windows Forms, aby korzystać z funkcji dodanych w ostatnich wersjach .NET Framework.

Element umożliwia dodanie jednego lub większej liczby elementów podrzędnych `<add>` , z których każdy definiuje określone ustawienie konfiguracji. `<System.Windows.Forms.ApplicationConfigurationSection>`

Aby zapoznać się z omówieniem Windows Forms wysokiej rozdzielczości DPI, zobacz [wysoka rozdzielczość DPI w programie Windows Forms](../../../winforms/high-dpi-support-in-windows-forms.md).

### <a name="dpiawareness"></a>DpiAwareness

Windows Forms aplikacje uruchamiane w wersjach systemu Windows, począwszy od systemu Windows 10 Creator Edition i wersje docelowa .NET Framework, począwszy od .NET Framework 4,7, można skonfigurować tak, aby korzystały z ulepszeń o wysokiej rozdzielczości DPI wprowadzonych w .NET Framework 4,7. Należą do nich następujące elementy:

- Obsługa dynamicznych scenariuszy DPI, w których użytkownik zmienia współczynnik DPI lub skalowania po uruchomieniu aplikacji Windows Forms.

- Ulepszenia skalowania i układu wielu kontrolek Windows Forms, takich jak <xref:System.Windows.Forms.MonthCalendar> kontrolka <xref:System.Windows.Forms.CheckedListBox> i kontrolka.

Wysoka rozdzielczość DPI to funkcja opcjonalna. Domyślnie wartość `DpiAwareness` to `false`. Możesz zadecydować, Windows Forms "obsłużyć świadomość dpi, ustawiając wartość tego klucza `PerMonitorV2` w pliku konfiguracji aplikacji. W przypadku włączenia rozpoznawania DPI wszystkie poszczególne funkcje DPI również są włączone. Należą do nich następujące elementy:

- Komunikaty o zmienionych wartościach `DisableDpiChangedMessageHandling` dpi, które są kontrolowane przez klucz.

- Dynamiczna obsługa dpi, która jest kontrolowana przez `EnableWindowsFormsHighDpiAutoResizing` klucz.

- `Form.DisableSinglePassControlScaling` Skalowanie pojedynczej kontroli, które jest kontrolowane przez poszczególne <xref:System.Windows.Forms.Form> kontrolki, przez `AnchorLayout.DisableSinglePassControlScaling` klucz `MonthCalendar.DisableSinglePassControlScaling` dla kontrolek zakotwiczonych i klucz dla <xref:System.Windows.Forms.MonthCalendar> kontrolki

- Skalowalność i skalowanie o wysokiej rozdzielczości DPI, które są `CheckListBox.DisableHighDpiImprovements` kontrolowane przez klucz <xref:System.Windows.Forms.CheckedListBox> dla kontrolki, `DataGridView.DisableHighDpiImprovements` <xref:System.Windows.Forms.DataGridView> przez `Toolstrip.DisableHighDpiImprovements` klucz dla kontrolki i klucz dla <xref:System.Windows.Forms.ToolStrip> kontrolki.

Pojedyncze domyślne ustawienie zgody udostępniane przez ustawienie `DpiAwareness` na `PerMonitorV2` jest ogólnie odpowiednie dla nowych aplikacji Windows Forms. Można jednak zrezygnować z indywidualnych ulepszeń o wysokiej rozdzielczości DPI przez dodanie odpowiedniego klucza do pliku konfiguracji aplikacji. Aby na przykład korzystać z wszystkich nowych funkcji DPI z wyjątkiem dynamicznego obsługi DPI, należy dodać następujący kod do pliku konfiguracji aplikacji:

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
   <add key="DpiAwareness" value="PerMonitorV2" />
   <!-- Disable dynamic DPI support -->
   <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" />
</System.Windows.Forms.ApplicationConfigurationSection>
```

Zazwyczaj należy zrezygnować z konkretnej funkcji, ponieważ została wybrana obsługa programistycznie.

Aby uzyskać więcej informacji o korzystaniu z obsługi wysokiej rozdzielczości DPI w aplikacjach Windows Forms, zobacz [Obsługa wysokiej rozdzielczości DPI w Windows Forms](../../../winforms/high-dpi-support-in-windows-forms.md).

### <a name="disabledpichangedmessagehandling"></a>DisableDpiChangedMessageHandling

Począwszy od .NET Framework 4,7, kontrolki Windows Forms zgłaszają wiele zdarzeń związanych ze zmianami skalowania DPI. Należą do <xref:System.Windows.Forms.Control.DpiChangedAfterParent>nich zdarzenia <xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, i <xref:System.Windows.Forms.Form.DpiChanged> . Wartość `DisableDpiChangedMessageHandling` klucza określa, czy te zdarzenia są zgłaszane w aplikacji Windows Forms.

### <a name="single-pass-scaling"></a>Skalowanie pojedynczego przebiegu

Skalowanie pojedyncze lub wieloprzebiegowe ma wpływ na postrzeganą czas odpowiedzi interfejsu użytkownika i wizualizację wyglądu elementów interfejsu użytkownika w miarę ich skalowania. Począwszy od .NET Framework 4,7, Windows Forms używa skalowania jednokrotnego. W poprzednich wersjach .NET Framework skalowanie było wykonywane przez wiele przebiegów, co spowodowało, że niektóre kontrolki są skalowane więcej niż jest to konieczne. Skalowanie pojedynczej części należy wyłączyć tylko wtedy, gdy aplikacja zależy od starego zachowania.

## <a name="see-also"></a>Zobacz także

- [Sekcja konfiguracji programu Windows Forms](index.md)
- [Obsługa wysokiej rozdzielczości DPI w Windows Forms](../../../winforms/high-dpi-support-in-windows-forms.md)
