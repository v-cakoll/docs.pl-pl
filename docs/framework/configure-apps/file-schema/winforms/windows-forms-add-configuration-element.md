---
title: Formularze systemu Windows, Dodaj Element konfiguracji
ms.date: 04/07/2017
helpviewer_keywords:
- Windows Forms Add configuration element
- configuring Windows Forms applications
ms.assetid: 3e3e04de-99d1-4658-b716-44cb669d9589
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 529dbccd5ddb4dd1f1456fb9a6043f3c5f7b378d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="windows-forms-add-configuration-element"></a>Formularze systemu Windows, Dodaj Element konfiguracji

`<add>` Element dodaje wstępnie zdefiniowany klucz, który określa, czy aplikacji formularzy systemu Windows obsługuje funkcje dodane do aplikacji formularzy systemu Windows w .NET Framework 4.7 lub nowszej.

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
| `key`     | Atrybut wymagany. Wstępnie zdefiniowane nazwy klucza, która odpowiada określonej funkcji dostosowania formularzy systemu Windows. |
| `value`   | Atrybut wymagany. Wartość do przypisania do `key`. |

### <a name="key-attribute-names-and-associated-values"></a>`key` nazwy atrybutów i skojarzone wartości

| `key` Nazwa | Wartości | Opis |
| ---------- | ------ | ----------- |
| "AnchorLayout.DisableSinglePassControlScaling" | "wartość prawda"&#124;"false" | Wskazuje, czy formanty zakotwiczonej są skalowane w jednym przebiegu. "true", aby wyłączyć jeden przekazać skalowanie; w przeciwnym razie wartość false. Zobacz sekcję "Jednym przekazać skalowanie" w [uwagi](#Remarks) Aby uzyskać więcej informacji. |
| "DpiAwareness" | "PerMonitorV2"&#124;"false" | Wskazuje, czy aplikacja ma obsługującą ustawienia DPI. Ustaw klucz do "PerMonitorV2" do obsługi rozpoznawania Dpi; w przeciwnym wypadku ustaw ją na "false". Rozpoznawanie DPI jest funkcji opcjonalnych; Aby skorzystać z pomocy technicznej formularzy systemu Windows wysokiej rozdzielczości, należy ustawić jej wartości "PerMonitorV2". Zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji. |
| "CheckedListBox.DisableHighDpiImprovements" | "wartość prawda"&#124;"false" | Wskazuje, czy <xref:System.Windows.Forms.CheckedListBox> kontroli wykorzystuje skalowanie i układu usprawnienia wprowadzone w .NET Framework 4.7. "true", aby zrezygnować z usprawnień caling i układu. w przeciwnym razie wartość "false". |
| "DataGridView.DisableHighDpiImprovements" | "wartość prawda"&#124;"false" | Wskazuje, czy <xref:System.Windows.Forms.DataGridView> kontrolować skalowanie i układu usprawnienia wprowadzone w .NET Framework 4.7. wartość "true" rezygnacji z świadomości DPI; "false" w przeciwnym razie wartość. |
| "DisableDpiChangedMessageHandling" | "wartość prawda"&#124;"false" | "true", aby zrezygnować z otrzymywania wiadomości dotyczące skalowania zmian; rozdzielczości "false" w przeciwnym razie wartość. Zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji. |
| "EnableWindowsFormsHighDpiAutoResizing" | "wartość prawda"&#124;"false" | Wskazuje, czy automatycznie rozmiaru aplikacji formularzy systemu Windows z powodu zmian skalowania DPI. "true", aby włączyć automatyczną zmianę rozmiaru; w przeciwnym razie wartość false. |
| "Form.DisableSinglePassControlScaling" | "wartość prawda"&#124;"false" | Wskazuje, czy <xref:System.Windows.Forms.Form> skalowania w jednym przebiegu. "true", aby wyłączyć jednego przebiegu skalowanie; w przeciwnym razie wartość false. Zobacz sekcję "Jednym przekazać skalowanie" w [uwagi](#Remarks) Aby uzyskać więcej informacji. |
| "MonthCalendar.DisableSinglePassControlScaling" | "wartość prawda"&#124;"false" | Wskazuje, czy <xref:System.Windows.Forms.MonthCalendar> skalowania formantu w jednym przebiegu. "true", aby wyłączyć jednego przebiegu skalowanie; w przeciwnym razie wartość false. Zobacz sekcję "Jednym przekazać skalowanie" w [uwagi](#Remarks) Aby uzyskać więcej informacji. |
| "Toolstrip.DisableHighDpiImprovements" | "wartość prawda"&#124;"false" | Wskazuje, czy <xref:System.Windows.Forms.ToolStrip> kontroli wykorzystuje skalowanie i układu usprawnienia wprowadzone w .NET Framework 4.7. wartość "true" rezygnacji z świadomości DPI; "false" w przeciwnym razie wartość. |

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |
| ------- | ----------- |
| [`<System.Windows.Forms.ApplicationConfigurationSection>`](../../../../../docs/framework/configure-apps/file-schema/winforms/index.md) | Konfiguruje obsługę nowych funkcji w aplikacji formularzy systemu Windows. |

## <a name="a-nameremarks--remarks"></a><a name="remarks" /> Uwagi

W programie .NET Framework 4.7, `<System.Windows.Forms.ApplicationConfigurationSection>` element pozwala na skonfigurowanie aplikacji formularzy systemu Windows, aby wykorzystać funkcje dodane w najnowszych wersjach programu .NET Framework. 

`<System.Windows.Forms.ApplicationConfigurationSection>` Element umożliwia dodanie jednego lub więcej podrzędnych `<add>` elementów, z których każdy definiuje ustawienie określonej konfiguracji.  

Omówienie obsługi wysokiej rozdzielczości formularzy systemu Windows, temacie [obsługuje wysokiej rozdzielczości DPI w formularzach systemu Windows](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md).

### <a name="dpiawareness"></a>DpiAwareness

Aby móc korzystać z wysokiej ulepszenia DPI wprowadzone w programie .NET Framework można skonfigurować aplikacji formularzy systemu Windows, które można uruchamiać w wersjach systemu Windows, począwszy od systemu Windows 10 twórców Edition i wersji docelowej platformy .NET, począwszy od .NET Framework 4.7 4.7. Należą do nich następujące elementy:

- Obsługa dynamicznego DPI scenariusze, w których użytkownik zmieni współczynnik DPI lub skalę po uruchomieniu aplikacji formularzy systemu Windows.

- Formanty ulepszenia skalowanie i układu liczby formularzy systemu Windows, takich jak <xref:System.Windows.Forms.MonthCalendar> kontroli i <xref:System.Windows.Forms.CheckedListBox> formantu. 

Wysokie DPI świadomości jest funkcji opcjonalnych; Domyślnie wartość `DpiAwareness` jest `false`. Można włączyć do obsługi formularzy systemu Windows dla świadomości DPI ustawiając wartość tego klucza, aby `PerMonitorV2` w pliku konfiguracyjnym aplikacji. Jeśli jest włączone rozpoznawanie DPI, wszystkie poszczególne funkcje DPI również są włączone. Należą do nich następujące elementy:

- Wartość DPI zmienione wiadomości, które są kontrolowane przez `DisableDpiChangedMessageHandling` klucza.

- Obsługa dynamicznego DPI, które są kontrolowane przez `EnableWindowsFormsHighDpiAutoResizing` klucza.

- Jednego przebiegu skalowania formantu, który jest kontrolowany przez `Form.DisableSinglePassControlScaling` dla poszczególnych <xref:System.Windows.Forms.Form> steruje przez `AnchorLayout.DisableSinglePassControlScaling` klucza zakotwiczonej formantów, a także `MonthCalendar.DisableSinglePassControlScaling` klucza dla <xref:System.Windows.Forms.MonthCalendar> formantu 

- Wysokie DPI skalowanie i układu ulepszenia, które jest kontrolowany przez `CheckListBox.DisableHighDpiImprovements` klucza dla <xref:System.Windows.Forms.CheckedListBox> kontroli przez `DataGridView.DisableHighDpiImprovements` klucza dla <xref:System.Windows.Forms.DataGridView> kontroli, a `Toolstrip.DisableHighDpiImprovements` klucza dla <xref:System.Windows.Forms.ToolStrip> formantu.  

Pojedynczy zdecydować się na ustawienie domyślne podać, ustawiając `DpiAwareness` do `PerMonitorV2` jest zazwyczaj odpowiednie dla nowych aplikacji formularzy systemu Windows. Jednak aby można następnie zrezygnować z poszczególnych ulepszenia wysokiej rozdzielczości, dodając odpowiedni klucz do pliku konfiguracji aplikacji. Na przykład aby wykorzystać wszystkie nowe featuers DPI z wyjątkiem dynamicznej obsługi DPI, czy dodać następujące do pliku konfiguracji aplikacji:

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
   <add key="DpiAwareness" value="PerMonitorV2" />
   <--! Disable dynamic DPI support -->
   <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" />
</System.Windows.Forms.ApplicationConfigurationSection>
```
Zwykle Aby zrezygnować z określonej funkcji ponieważ wybrano opcję obsługi ją programowo.

Aby uzyskać więcej informacji na skorzystaj obsługa wysokiej rozdzielczości w aplikacjach formularzy systemu Windows, zobacz [obsługuje wysokiej rozdzielczości DPI w formularzach systemu Windows](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md).
 
### <a name="disabledpichangedmessagehandling"></a>DisableDpiChangedMessageHandling

Formanty formularzy systemu Windows w programie .NET Framework 4.7, podnieść numer zdarzenia związane ze zmianami w Skalowanie DPI. Obejmują one <xref:System.Windows.Forms.Control.DpiChangedAfterParent>, <xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, i <xref:System.Windows.Forms.Form.DpiChanged> zdarzenia. Wartość `DisableDpiChangedMessageHandling` klucz określa, czy te zdarzenia są generowane w aplikacji formularzy systemu Windows. 

### <a name="single-pass-scaling"></a>Skalowanie jednego przebiegu

Jednego lub wielu pass skalowanie ma wpływ na postrzegany czas odpowiedzi interfejsu użytkownika i wyglądu elementy interfejsu użytkownika, ponieważ są one skalowane w. Począwszy od .NET Framework 4.7, formularze systemu Windows używa skalowania w jednym przebiegu. W poprzednich wersjach programu .NET Framework skalowanie została wykonana za pomocą wielu przebiegi, które spowodowało niektóre formanty skalowania ponad konieczne było. Skalowanie w jednym przebiegu należy wyłączyć tylko, jeśli poprzednie działanie zależy od aplikacji.  

## <a name="see-also"></a>Zobacz także
 
[Sekcja konfiguracji formularzy systemu Windows](../../../../../docs/framework/configure-apps/file-schema/winforms/index.md)   
[Obsługa wysokiej rozdzielczości w formularzach systemu Windows](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)
