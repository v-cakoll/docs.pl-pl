---
ms.openlocfilehash: cc3c2c2be179842f87be8892d057a6c4138086cb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614875"
---
### <a name="accessibility-improvements-in-windows-forms-controls-for-net-472"></a>Ulepszenia ułatwień dostępu w kontrolkach Windows Forms dla platformy .NET 4.7.2

#### <a name="details"></a>Szczegóły

Windows Forms Framework ulepsza sposób działania z technologiami ułatwień dostępu w celu lepszego wsparcia Windows Forms klientów. Należą do nich następujące zmiany:

- Zmiany w celu usprawnienia wyświetlania w trybie duży kontrast.
- Zmiany w celu usprawnienia nawigowania po klawiaturze w kontrolkach DataGridView i MenuStrip.
- Zmiany interakcji z narratorem.

#### <a name="suggestion"></a>Sugestia

**Jak wybrać lub wycofać te zmiany** Aby aplikacja mogła korzystać z tych zmian, musi ona działać na .NET Framework 4.7.2 lub nowszym. Aplikacja może korzystać z tych zmian w jeden z następujących sposobów:

- Zostanie ponownie skompilowana w celu przekierowania .NET Framework 4.7.2. Te zmiany ułatwień dostępu są domyślnie włączone w Windows Forms aplikacjach przeznaczonych dla .NET Framework 4.7.2 lub nowszych.
- Jest ona przeznaczona dla .NET Framework 4.7.1 lub starszej wersji, a także [wyłączają](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) się ze starszych zachowań ułatwień dostępu, dodając następujący `<runtime>` przykład do sekcji w pliku konfiguracji aplikacji i ustawiając go na `false` , jak pokazano w poniższym przykładzie.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <startup>
    <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7"/>
  </startup>
  <runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
  </runtime>
</configuration>
```

Należy pamiętać, że aby skorzystać z funkcji ułatwień dostępu dodanych w .NET Framework 4.7.2, należy również zrezygnować z funkcji ułatwień dostępu .NET Framework 4.7.1. Aplikacje, które są przeznaczone dla .NET Framework 4.7.2 lub nowszych i chcą zachować starsze zachowanie ułatwień dostępu, mogą zrezygnować z używania starszych funkcji ułatwień dostępu przez jawne ustawienie tego przełącznika AppContext na `true` .

**Używanie kolorów zdefiniowanych w systemie operacyjnym w duży kontrast motywach**

- Strzałka listy rozwijanej <xref:System.Windows.Forms.ToolStripDropDownButton> obecnie używa kolorów zdefiniowanych przez system operacyjny w motywie duży kontrast.
- <xref:System.Windows.Forms.Button><xref:System.Windows.Forms.RadioButton>i <xref:System.Windows.Forms.CheckBox> kontrolek z <xref:System.Windows.Forms.ButtonBase.FlatStyle> ustawieniem <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> lub <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType> teraz używają kolorów zdefiniowanych przez system operacyjny w motywie duży kontrast, gdy to zaznaczone. Wcześniej kolory tekstu i tła nie były kontrastowe i trudno je odczytać.
- Kontrolki zawarte w elemencie <xref:System.Windows.Forms.GroupBox> , który ma <xref:System.Windows.Forms.Control.Enabled> ustawioną właściwość na, `false` będą teraz używały kolorów zdefiniowanych w systemie operacyjnym w duży kontrast motywie.
- <xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolStripComboBox> Kontrolki, i <xref:System.Windows.Forms.ToolStripDropDownButton> mają zwiększony współczynnik kontrastu jaskrawości w trybie duży kontrast.
- <xref:System.Windows.Forms.DataGridViewLinkCell>domyślnie użyje kolorów zdefiniowanych przez system operacyjny w trybie duży kontrast dla <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor?displayProperty=nameWithType> właściwości.
Uwaga: system Windows 10 zmienił wartości dla niektórych kolorów systemu o dużym kontraście. Platforma Windows Forms Framework jest oparta na platformie Win32. Aby uzyskać najlepsze środowisko, uruchom polecenie w najnowszej wersji systemu Windows i zapoznaj się z najnowszymi zmianami systemu operacyjnego przez dodanie pliku App. manifest do aplikacji testowej i cofnięcie komentarza do następującego kodu:

```xml
<!-- Windows 10 -->
<supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
```

**Ulepszona obsługa Narratora**

- Narrator ogłasza teraz wartość właściwości przy zapowiadaniu <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> tekstu <xref:System.Windows.Forms.ToolStripMenuItem> .
- Narrator wskazuje teraz, gdy <xref:System.Windows.Forms.ToolStripMenuItem> <xref:System.Windows.Forms.Control.Enabled> Właściwość ma ustawioną wartość `false` .
- Program Narrator reaguje teraz na stan pola wyboru, gdy <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> Właściwość jest ustawiona na `true` .
- Tryb skanowania Narratora kolejność fokusu jest teraz spójna z kolejnością wizualizacji kontrolek w oknie dialogowym pobierania ClickOnce.

**Ulepszona obsługa ułatwień dostępu DataGridView**

- Wiersze w a <xref:System.Windows.Forms.DataGridView> mogą teraz być sortowane przy użyciu klawiatury. Teraz użytkownik może użyć klawisza F3, aby posortować według bieżącej kolumny.
- Gdy <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> jest ustawiona na <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType> , nagłówek kolumny zmieni kolor, aby wskazać bieżącą kolumnę jako karty użytkownika przez komórki w bieżącym wierszu.
- <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Parent?displayProperty=nameWithType>Teraz Właściwość zwraca poprawną kontrolkę nadrzędną.

**Ulepszone podpowiedzi wizualne**

- <xref:System.Windows.Forms.RadioButton> <xref:System.Windows.Forms.CheckBox> Kontrolki i z pustą <xref:System.Windows.Forms.ButtonBase.Text> właściwością będą teraz wyświetlały wskaźnik ostrości po odebraniu fokusu.

**Ulepszona obsługa siatki właściwości**

- <xref:System.Windows.Forms.PropertyGrid>Elementy podrzędne kontrolki zwracają teraz `true` do właściwości tylko wtedy, <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> gdy element PropertyGrid jest włączony.
- <xref:System.Windows.Forms.PropertyGrid>Elementy podrzędne kontrolki zwracają teraz `false` do <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> właściwości tylko wtedy, gdy użytkownik może zmienić element PropertyGrid.
Aby zapoznać się z omówieniem automatyzacji interfejsu użytkownika, zobacz [Omówienie automatyzacji interfejsu użytkownika](https://docs.microsoft.com/dotnet/framework/ui-automation/ui-automation-overview).</p>**Ulepszone nawigowanie po klawiaturze**

- <xref:System.Windows.Forms.ToolStripButton>teraz umożliwia fokus, gdy jest zawarty w elemencie <xref:System.Windows.Forms.ToolStripPanel> , który ma <xref:System.Windows.Forms.ToolStripPanel.TabStop> Właściwość ustawioną na `true` .

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Duży       |
| Wersja | 4.7.2       |
| Typ    | Przekierowanie |
