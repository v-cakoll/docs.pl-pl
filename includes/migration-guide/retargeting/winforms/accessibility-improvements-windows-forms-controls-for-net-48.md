---
ms.openlocfilehash: e528a41748d9353c96d443f68e15e7a98ee7f4ae
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616305"
---
### <a name="accessibility-improvements-in-windows-forms-controls-for-net-48"></a>Ulepszenia ułatwień dostępu w kontrolkach Windows Forms dla programu .NET 4,8

#### <a name="details"></a>Szczegóły

Windows Forms Framework kontynuuje ulepszanie sposobu działania z technologiami ułatwień dostępu w celu lepszego wsparcia Windows Forms klientów. Należą do nich następujące zmiany:

- Zmiany w celu usprawnienia wyświetlania w trybie duży kontrast.
- Zmiany interakcji z narratorem.
- Zmiany w dostępnej hierarchii (ulepszenie nawigacji przez drzewo automatyzacji interfejsu użytkownika).

#### <a name="suggestion"></a>Sugestia

**Jak wybrać lub wycofać te zmiany** Aby aplikacja mogła korzystać z tych zmian, należy ją uruchomić na .NET Framework 4,8. Aplikacja może wyrazić zgodę na te zmiany w jeden z następujących sposobów:

- Zostanie ponownie skompilowana w celu przekierowania .NET Framework 4,8. Te zmiany ułatwień dostępu są domyślnie włączone w Windows Forms aplikacjach przeznaczonych dla .NET Framework 4,8.
- Jest ona przeznaczona dla .NET Framework 4.7.2 lub starszej wersji, a także [wyłączają](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) się ze starszych zachowań ułatwień dostępu, dodając następujący `<runtime>` przykład do sekcji w pliku konfiguracji aplikacji i ustawiając go na `false` , jak pokazano w poniższym przykładzie.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <startup>
    <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7"/>
  </startup>
  <runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false" />
  </runtime>
</configuration>
```

Należy pamiętać, że aby skorzystać z funkcji ułatwień dostępu dodanych w .NET Framework 4,8, należy również zrezygnować z funkcji ułatwień dostępu .NET Framework 4.7.1 i 4.7.2. Aplikacje, które są przeznaczone dla .NET Framework 4,8 i chcą zachować starsze zachowanie ułatwień dostępu, mogą zrezygnować z używania starszych funkcji ułatwień dostępu przez jawne ustawienie tego przełącznika AppContext na `true` . Włączenie obsługi wywołania etykietki narzędzia klawiatury wymaga dodania `Switch.System.Windows.Forms.UseLegacyToolTipDisplay=false` linii do wartości AppContextSwitchOverrides:

```xml
<AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false;Switch.System.Windows.Forms.UseLegacyToolTipDisplay=false" />
```

Należy pamiętać, że włączenie tej funkcji wymaga skorzystania z powyższych funkcji ułatwień dostępu .NET Framework 4.7.1-4,8. Ponadto jeśli jakakolwiek z funkcji ułatwień dostępu nie zostanie włączona, ale funkcja wyświetlania etykietki narzędzi zostanie włączona, środowisko uruchomieniowe <xref:System.NotSupportedException> zostanie zgłoszone przy pierwszym dostępie do tych funkcji. Komunikat o wyjątku wskazuje, że etykietki narzędzi klawiatury wymagają usprawnienia ułatwienia dostępu w celu włączenia poziomu 3.

**Używanie kolorów zdefiniowanych w systemie operacyjnym w duży kontrast motywach**

- Ulepszone motywy o wysokim kontraście.

**Ulepszona obsługa Narratora**

- Narrator ogłasza teraz kierunek sortowania w <xref:System.Windows.Forms.DataGridViewColumn> przypadku ogłaszania dostępnej nazwy <xref:System.Windows.Forms.DataGridViewCell> .

**Ulepszona obsługa ułatwień dostępu CheckedListBox**

- Ulepszona obsługa programu Narrator dla <xref:System.Windows.Forms.CheckedListBox> kontrolki. Podczas przechodzenia do <xref:System.Windows.Forms.CheckedListBox> formantu przy użyciu klawiatury, narrator koncentruje się na <xref:System.Windows.Forms.CheckedListBox> elemencie i ogłasza.
- Pusta kontrolka CheckedListBox ma teraz prostokąt fokusu rysowany dla wirtualnego pierwszego elementu, gdy formant zmieni się na fokus.

**Ulepszona obsługa ułatwień dostępu ComboBox**

- Obsługa automatyzacji interfejsu użytkownika dla <xref:System.Windows.Forms.ComboBox> kontrolek z możliwością korzystania z powiadomień automatyzacji interfejsu użytkownika i innych funkcji automatyzacji interfejsu użytkownika.
**Ulepszona obsługa ułatwień dostępu DataGridView**

- Włączono obsługę automatyzacji interfejsu użytkownika dla <xref:System.Windows.Forms.DataGridView> kontrolek z możliwością używania powiadomień automatyzacji interfejsu użytkownika i innych funkcji automatyzacji interfejsu użytkownika.
- Element automatyzacji interfejsu użytkownika, który odnosi się do <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl> lub <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl> jest teraz elementem podrzędnym odpowiedniej komórki edycji.

**Ulepszona obsługa ułatwień dostępu LinkLabel**

- Ulepszona <xref:System.Windows.Forms.LinkLabel> dostępność kontroli: program Narrator ogłasza stan wyłączenia dla łącza, Jeśli odpowiednia <xref:System.Windows.Forms.LinkLabel> kontrolka jest wyłączona.

**Ulepszona obsługa ułatwień dostępu ProgressBar**

- Włączono obsługę automatyzacji interfejsu użytkownika dla <xref:System.Windows.Forms.ProgressBar> kontrolki z możliwością używania powiadomień automatyzacji interfejsu użytkownika i innych funkcji automatyzacji interfejsu użytkownika. Deweloperzy mogą teraz używać powiadomień automatyzacji interfejsu użytkownika, które narrator może ogłosić, aby wskazać postęp.
Omówienie zdarzeń automatyzacji interfejsu użytkownika, w tym zdarzenia powiadomień automatyzacji interfejsu użytkownika, można znaleźć w temacie [Omówienie zdarzeń automatyzacji interfejsu użytkownika](https://docs.microsoft.com/windows/desktop/WinAuto/uiauto-eventsoverview).

**Ulepszona obsługa ułatwień dostępu do elementu PropertyGrid**

- Obsługa automatyzacji interfejsu użytkownika dla <xref:System.Windows.Forms.PropertyGrid> kontrolek z możliwością korzystania z powiadomień automatyzacji interfejsu użytkownika i innych funkcji automatyzacji interfejsu użytkownika.
- Element automatyzacji interfejsu użytkownika, który odnosi się do obecnie edytowanej właściwości, jest teraz elementem podrzędnym odpowiadającego elementu automatyzacji interfejsu użytkownika elementu właściwości.
- Element elementu właściwości Automatyzacja interfejsu użytkownika jest teraz elementem podrzędnym odpowiadającego elementu kategorii, jeśli <xref:System.Windows.Forms.PropertyGrid> formant nadrzędny jest ustawiony na widok kategorii.

**Ulepszona obsługa ToolStrip**

- Obsługa automatyzacji interfejsu użytkownika dla <xref:System.Windows.Forms.ToolStrip> kontrolek z możliwością korzystania z powiadomień automatyzacji interfejsu użytkownika i innych funkcji automatyzacji interfejsu użytkownika.
- Ulepszona nawigacja przez <xref:System.Windows.Forms.ToolStrip> elementy.
- W trybie elementów fokus Narratora nie znika i nie przechodzi do elementów ukrytych.

**Ulepszone podpowiedzi wizualne**

- Pusta <xref:System.Windows.Forms.CheckedListBox> kontrolka wyświetla teraz wskaźnik fokusu po odebraniu fokusu.
Uwaga: Obsługa automatyzacji interfejsu użytkownika jest włączona dla formantów w środowisku uruchomieniowym, ale nie jest używana w czasie projektowania. Aby zapoznać się z omówieniem automatyzacji interfejsu użytkownika, zobacz [Omówienie automatyzacji interfejsu użytkownika](https://docs.microsoft.com/dotnet/framework/ui-automation/ui-automation-overview).

**Wywoływanie etykietek narzędzi formantów przy użyciu klawiatury**

- Etykietka narzędzia kontrolki może teraz być wywoływana przez skoncentrowanie kontrolki z klawiaturą. Ta funkcja musi zostać włączona jawnie dla aplikacji (zobacz sekcję ** &quot; Jak zrezygnować z tych &quot; zmian lub z nich**)

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Duży       |
| Wersja | 4,8         |
| Typ    | Przekierowanie |
