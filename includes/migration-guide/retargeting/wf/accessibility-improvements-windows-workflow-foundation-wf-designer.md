---
ms.openlocfilehash: d420be76645fc71ac922542fa49f799a473e9a83
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614852"
---
### <a name="accessibility-improvements-in-windows-workflow-foundation-wf-workflow-designer"></a>Ulepszenia ułatwień dostępu w Projektancie przepływu pracy w programie Windows Workflow Foundation (WF)

#### <a name="details"></a>Szczegóły

Projektant przepływów pracy Windows Workflow Foundation (WF) ulepsza sposób działania z technologiami ułatwień dostępu. Te ulepszenia obejmują następujące zmiany:

- Kolejność tabulacji jest zmieniana na od lewej do prawej i od góry do dołu w niektórych kontrolkach:
- Okno inicjowania korelacji do ustawiania danych korelacji dla <xref:System.ServiceModel.Activities.InitializeCorrelation> działania
- Okno definicji zawartości dla <xref:System.ServiceModel.Activities.Receive> działań,, <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.SendReply> i <xref:System.ServiceModel.Activities.ReceiveReply>
- Więcej funkcji jest dostępnych za pośrednictwem klawiatury:
- Podczas edytowania właściwości działania grupy właściwości mogą być zwijane przez klawiaturę po raz pierwszy.
- Ikony ostrzeżeń są teraz dostępne na klawiaturze.
- Przycisk więcej właściwości w okno Właściwości jest teraz dostępny na klawiaturze.
- Użytkownicy klawiatury mogą teraz uzyskiwać dostęp do elementów nagłówka w okienkach argumenty i zmienne Projektant przepływu pracy.
- Ulepszona widoczność elementów z fokusem, takich jak:
- Dodawanie wierszy do siatek danych używanych przez Projektant przepływu pracy i projektantów działań.
- Używanie tabulacji w polach w <xref:System.ServiceModel.Activities.ReceiveReply> <xref:System.ServiceModel.Activities.SendReply> działaniach i.
- Ustawianie wartości domyślnych dla zmiennych lub argumentów
- Czytniki zawartości ekranu mogą teraz prawidłowo rozpoznać:
- Punkty przerwania ustawione w Projektancie przepływu pracy.
- <xref:System.Activities.Statements.FlowSwitch%601>Działania, <xref:System.Activities.Statements.FlowDecision> i <xref:System.ServiceModel.Activities.CorrelationScope> .
- Zawartość <xref:System.ServiceModel.Activities.Receive> działania.
- Typ docelowy dla <xref:System.Activities.Statements.InvokeMethod> działania.
- Pole kombi wyjątku oraz sekcja finally w <xref:System.Activities.Statements.TryCatch> działaniu.
- Pole kombi typ komunikatu, rozdzielacz w oknie Dodaj inicjatory korelacji, okno definicji zawartości i okno CorrelatesOn definicji w działaniach związanych z wiadomościami ( <xref:System.ServiceModel.Activities.Receive> , <xref:System.ServiceModel.Activities.Send> , <xref:System.ServiceModel.Activities.SendReply> i <xref:System.ServiceModel.Activities.ReceiveReply> ).
- Przejścia komputera stanu i miejsca docelowe przejść.
- Adnotacje i łączniki na <xref:System.Activities.Statements.FlowDecision> działaniach.
- Menu kontekstowe (kliknij prawym przyciskiem myszy) dla działań.
- Edytor wartości właściwości, przycisk Wyczyść wyszukiwanie, Kategoria według oraz alfabetyczne przyciski sortowania i okno dialogowe Edytor wyrażeń w siatce właściwości.
- Procent powiększenia w Projektant przepływu pracy.
- Separator w <xref:System.Activities.Statements.Parallel> <xref:System.Activities.Statements.Pick> działaniach i.
- <xref:System.Activities.Statements.InvokeDelegate>Działanie.
- Okno wybór typów dla działań słownika ( `Microsoft.Activities.AddToDictionary&lt;TKey,TValue>` , `Microsoft.Activities.RemoveFromDictionary&lt;TKey,TValue>` itp.).
- Okno Przeglądaj i wybierz typ platformy .NET.
- Struktura nawigacyjna w Projektant przepływu pracy.
- Użytkownicy, którzy wybierają duży kontrast motywy zobaczą wiele ulepszeń w widoczności Projektant przepływu pracy i jej kontrolki, takie jak lepsze współczynniki kontrastu między elementami i bardziej zauważalne pola wyboru używane na potrzeby elementów fokusu.

#### <a name="suggestion"></a>Sugestia

Jeśli masz aplikację z nieobsługiwanym projektantem przepływu pracy, Twoja aplikacja może korzystać z tych zmian, wykonując jedną z następujących czynności:

- Skompiluj ponownie aplikację pod kątem .NET Framework 4.7.1. Te zmiany ułatwień dostępu są domyślnie włączone.
- Jeśli aplikacja jest przeznaczona dla .NET Framework 4,7 lub wcześniejszych, ale jest uruchomiona na .NET Framework 4.7.1, można zrezygnować z tych starszych zachowań dostępności, dodając następujący [przełącznik AppContext](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do `<runtime>` sekcji pliku app.config i ustawiając go na `false` , tak jak pokazano w poniższym przykładzie.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <startup>
    <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7"/>
  </startup>
  <runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
  </runtime>
</configuration>
```

Aplikacje, które są przeznaczone dla .NET Framework 4.7.1 lub nowszych i chcą zachować starsze zachowanie ułatwień dostępu, mogą zrezygnować z używania starszych funkcji ułatwień dostępu przez jawne ustawienie tego przełącznika AppContext na `true` .

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Mały       |
| Wersja | 4.7.1       |
| Typ    | Przekierowanie |
