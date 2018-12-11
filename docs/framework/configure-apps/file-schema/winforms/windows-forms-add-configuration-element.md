---
title: Windows Forms, Dodaj Element konfiguracji
ms.date: 04/07/2017
helpviewer_keywords:
- Windows Forms Add configuration element
- configuring Windows Forms applications
ms.assetid: 3e3e04de-99d1-4658-b716-44cb669d9589
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5cb0d058cd1ade65bfdc966819c0c41d9c1a9750
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53155096"
---
# <a name="windows-forms-add-configuration-element"></a>Windows Forms, Dodaj Element konfiguracji

`<add>` Elementu dodaje wstępnie zdefiniowanego klucza, który określa, czy aplikacja formularza Windows obsługuje funkcje dodane do aplikacji Windows Forms w programie .NET Framework 4.7 lub nowszej.

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
| `key`     | Atrybut wymagany. Wstępnie zdefiniowane nazwy klucza odnosi się do określonej funkcji można dostosowywać formularze Windows. |
| `value`   | Atrybut wymagany. Wartość do przypisania do `key`. |

### <a name="key-attribute-names-and-associated-values"></a>`key` nazwy atrybutów i skojarzone wartości

| `key` Nazwa | Wartości | Opis |
| ---------- | ------ | ----------- |
| "AnchorLayout.DisableSinglePassControlScaling" | "true"&#124;"false" | Wskazuje, czy formanty zakotwiczonej są skalowane w jednym przebiegu. "true", aby wyłączyć pojedynczego przekazywania skalowanie; w przeciwnym razie wartość false. Zobacz sekcję "Pojedynczego Powodzenie, skalowanie" w [uwagi](#Remarks) Aby uzyskać więcej informacji. |
| "DpiAwareness" | "PerMonitorV2"&#124;"false" | Wskazuje, czy aplikacja ma obsługującą ustawienia DPI. Ustaw klucz do "PerMonitorV2", aby obsługiwać rozpoznawanie Dpi; w przeciwnym wypadku ustaw ją na "false". Rozpoznawanie DPI to funkcja opcjonalna; Aby móc korzystać z pomocy technicznej Windows Forms o wysokiej rozdzielczości DPI, należy ustawić jej wartość na "PerMonitorV2". Zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji. |
| "CheckedListBox.DisableHighDpiImprovements" | "true"&#124;"false" | Wskazuje, czy <xref:System.Windows.Forms.CheckedListBox> kontroli korzysta z zalet skalowania i układ ulepszeń wprowadzonych w programie .NET Framework 4.7. "true", aby zrezygnować z usprawnień caling i układ. w przeciwnym razie wartość "false". |
| "DataGridView.DisableHighDpiImprovements" | "true"&#124;"false" | Wskazuje, czy <xref:System.Windows.Forms.DataGridView> kontrolować ulepszenia w zakresie skalowania i układu wprowadzone w programie .NET Framework 4.7. "true", aby zrezygnować z DPI awareness; "false" w przeciwnym razie. |
| "DisableDpiChangedMessageHandling" | "true"&#124;"false" | "true", aby zrezygnować z odbieraniem wiadomości związanych z skalowania zmiany; rozdzielczości "false" w przeciwnym razie. Zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji. |
| "EnableWindowsFormsHighDpiAutoResizing" | "true"&#124;"false" | Wskazuje, czy aplikacji Windows Forms automatycznie zmiany rozmiaru z powodu zmian skalowania DPI. "true", aby włączyć automatyczną zmianę rozmiaru; w przeciwnym razie wartość false. |
| "Form.DisableSinglePassControlScaling" | "true"&#124;"false" | Wskazuje, czy <xref:System.Windows.Forms.Form> jest skalowany w jednym przebiegu. "true", aby wyłączyć jednego przebiegu skalowanie; w przeciwnym razie wartość false. Zobacz sekcję "Pojedynczego Powodzenie, skalowanie" w [uwagi](#Remarks) Aby uzyskać więcej informacji. |
| "MonthCalendar.DisableSinglePassControlScaling" | "true"&#124;"false" | Wskazuje, czy <xref:System.Windows.Forms.MonthCalendar> kontroli jest skalowany w jednym przebiegu. "true", aby wyłączyć jednego przebiegu skalowanie; w przeciwnym razie wartość false. Zobacz sekcję "Pojedynczego Powodzenie, skalowanie" w [uwagi](#Remarks) Aby uzyskać więcej informacji. |
| "Toolstrip.DisableHighDpiImprovements" | "true"&#124;"false" | Wskazuje, czy <xref:System.Windows.Forms.ToolStrip> kontroli korzysta z zalet skalowania i układ ulepszeń wprowadzonych w programie .NET Framework 4.7. "true", aby zrezygnować z DPI awareness; "false" w przeciwnym razie. |

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |
| ------- | ----------- |
| [`<System.Windows.Forms.ApplicationConfigurationSection>`](../../../../../docs/framework/configure-apps/file-schema/winforms/index.md) | Konfiguruje obsługę nowych funkcji w aplikacji Windows Forms. |

## <a name="a-nameremarks--remarks"></a><a name="remarks" /> Uwagi

Począwszy od .NET Framework 4.7 `<System.Windows.Forms.ApplicationConfigurationSection>` elementu umożliwia skonfigurowanie aplikacji Windows Forms, aby wykorzystać funkcje dodane w najnowszych wersjach programu .NET Framework. 

`<System.Windows.Forms.ApplicationConfigurationSection>` Elementu umożliwia dodanie co najmniej jedną podrzędną `<add>` elementów, z których każdy definiuje ustawienia konfiguracji.  

Aby uzyskać omówienie obsługi Windows Forms o wysokiej rozdzielczości, zobacz [wysokiej rozdzielczości DPI pomocy technicznej w formularzach Windows Forms](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md).

### <a name="dpiawareness"></a>DpiAwareness

Aplikacje Windows Forms, z systemem w wersji Windows począwszy od systemu Windows 10 dla twórców Edition i wersji docelowej programu .NET Framework, począwszy od programu .NET Framework 4.7 można konfigurować z zalet wysokiej ulepszenia DPI wprowadzone w programie .NET Framework 4.7. Należą do nich następujące elementy:

- Obsługa dynamicznego scenariuszy DPI, w których użytkownik zmieni współczynnik skalowania lub DPI po aplikacji Windows Forms została uruchomiona.

- Ulepszenia skalowanie i układ liczby formularzy Windows Forms kontroluje, takich jak <xref:System.Windows.Forms.MonthCalendar> kontroli i <xref:System.Windows.Forms.CheckedListBox> kontroli. 

Wysokie DPI awareness to funkcja opcjonalna; Domyślnie wartość `DpiAwareness` jest `false`. Możesz zdecydować się na Windows Forms pomocy technicznej dla świadomości DPI, ustawiając wartość tego klucza na potrzeby `PerMonitorV2` w pliku konfiguracyjnym aplikacji. Jeśli rozpoznawanie DPI jest włączone, wszystkie poszczególne funkcje DPI również są włączone. Należą do nich następujące elementy:

- Wartość DPI zmienione wiadomości, które są kontrolowane przez `DisableDpiChangedMessageHandling` klucza.

- Dynamiczna obsługa rozdzielczości DPI, które są kontrolowane przez `EnableWindowsFormsHighDpiAutoResizing` klucza.

- Jednego przebiegu skalowania formantu, który jest kontrolowany przez `Form.DisableSinglePassControlScaling` dla poszczególnych <xref:System.Windows.Forms.Form> kontroluje, przez `AnchorLayout.DisableSinglePassControlScaling` klucza dla formantów zakotwiczonej i przez `MonthCalendar.DisableSinglePassControlScaling` klucza dla <xref:System.Windows.Forms.MonthCalendar> kontroli 

- Wysokiej rozdzielczości DPI skalowanie i układ ulepszenia, które jest kontrolowana przez `CheckListBox.DisableHighDpiImprovements` klucza dla <xref:System.Windows.Forms.CheckedListBox> kontrolować przez `DataGridView.DisableHighDpiImprovements` klucza dla <xref:System.Windows.Forms.DataGridView> kontroli i `Toolstrip.DisableHighDpiImprovements` klucza dla <xref:System.Windows.Forms.ToolStrip> kontroli.  

Pojedynczy uczestnictwo ustawieniem domyślnym podać, ustawiając `DpiAwareness` do `PerMonitorV2` jest zazwyczaj właściwa w przypadku nowych aplikacji Windows Forms. Jednak można następnie zrezygnować z poszczególnych wysokiej ulepszenia DPI, dodając odpowiedniego klucza do pliku konfiguracji aplikacji. Na przykład aby móc korzystać z wszystkich nowych featuers DPI z wyjątkiem dynamiczna obsługa rozdzielczości DPI, należy dodać następujące do pliku konfiguracyjnego aplikacji:

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
   <add key="DpiAwareness" value="PerMonitorV2" />
   <!-- Disable dynamic DPI support -->
   <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" />
</System.Windows.Forms.ApplicationConfigurationSection>
```
Zwykle możesz zrezygnować z określonej funkcji, ponieważ wybrano będzie przetwarzał programowo.

Aby uzyskać więcej informacji na zalety biorąc obsługa wysokiej rozdzielczości w aplikacjach Windows Forms, zobacz [wysokiej rozdzielczości DPI pomocy technicznej w formularzach Windows Forms](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md).
 
### <a name="disabledpichangedmessagehandling"></a>DisableDpiChangedMessageHandling

Począwszy od programu .NET Framework 4.7 kontrolek formularzy Windows Forms podniesienia liczby zdarzeń związanych ze zmianami w Skalowanie DPI. Obejmują one <xref:System.Windows.Forms.Control.DpiChangedAfterParent>, <xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, i <xref:System.Windows.Forms.Form.DpiChanged> zdarzenia. Wartość `DisableDpiChangedMessageHandling` klucz określa, czy te zdarzenia są wywoływane w aplikacji Windows Forms. 

### <a name="single-pass-scaling"></a>Skalowanie jednego przebiegu

Skalowanie w jednym lub wielu — dostęp próbny ma wpływ na postrzegany czas odpowiedzi interfejsu użytkownika i wygląd elementów interfejsu użytkownika, ponieważ są one skalowane. Począwszy od programu .NET Framework 4.7, formularze Windows używa skalowania w jednym przebiegu. W poprzednich wersjach programu .NET Framework skalowania została wykonana przy użyciu wielu przebiegów, które spowodowało niektóre formanty, które można skalować więcej niż było konieczne. Skalowanie z jednego przebiegu należy wyłączyć tylko wtedy, jeśli aplikacja jest zależna od starego zachowania.  

## <a name="see-also"></a>Zobacz także
 
[Sekcja konfiguracji programu Windows Forms](../../../../../docs/framework/configure-apps/file-schema/winforms/index.md)   
[Obsługa wysokiej rozdzielczości w formularzach Windows Forms](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)
