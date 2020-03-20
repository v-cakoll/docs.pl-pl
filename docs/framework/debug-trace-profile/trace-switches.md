---
title: Przełączniki śledzenia
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tracing [.NET Framework], trace switches
- trace switches, about trace switches
- tracing [.NET Framework], level of detail
- switches, trace
- trace switches
- trace switches, creating custom
ms.assetid: 8ab913aa-f400-4406-9436-f45bc6e54fbe
ms.openlocfilehash: a8ce4ee5de4d330b88e98e85cce4b6547e969613
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181731"
---
# <a name="trace-switches"></a>Przełączniki śledzenia
Przełączniki śledzenia umożliwiają włączanie, wyłączanie i filtrowanie danych wyjściowych. Są to obiekty, które istnieją w kodzie i mogą być konfigurowane zewnętrznie za pośrednictwem pliku .config. Istnieją trzy typy przełączników śledzenia przewidziane w <xref:System.Diagnostics.BooleanSwitch> .NET <xref:System.Diagnostics.TraceSwitch> Framework: <xref:System.Diagnostics.SourceSwitch> klasa, klasa i klasa. Klasa <xref:System.Diagnostics.BooleanSwitch> działa jako przełącznik przełącznika, włączając lub wyłączając różne instrukcje śledzenia. Klasy <xref:System.Diagnostics.TraceSwitch> <xref:System.Diagnostics.SourceSwitch> i umożliwiają włączenie przełącznika śledzenia dla określonego poziomu <xref:System.Diagnostics.Trace> śledzenia, tak aby wyświetlane były komunikaty określone <xref:System.Diagnostics.TraceSource> dla tego poziomu i wszystkie poziomy poniżej. Jeśli wyłączysz przełącznik, komunikaty śledzenia nie będą wyświetlane. Wszystkie te klasy pochodzą z abstrakcyjnej **(MustInherit**) klasy **Switch**, podobnie jak wszystkie przełączniki opracowane przez użytkownika.  
  
 Przełączniki śledzenia mogą być przydatne do filtrowania informacji. Na przykład można wyświetlić każdy komunikat śledzenia w module dostępu do danych, ale tylko komunikaty o błędach w pozostałej części aplikacji. W takim przypadku należy użyć jednego przełącznika śledzenia dla modułu dostępu do danych i jednego przełącznika dla pozostałej części aplikacji. Korzystając z pliku .config, aby skonfigurować przełączniki do odpowiednich ustawień, można kontrolować, jakie typy wiadomości śledzenia zostały odebrane. Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie, Inicjowanie i konfigurowanie przełączników śledzenia](how-to-create-initialize-and-configure-trace-switches.md).  
  
 Zazwyczaj wdrożona aplikacja jest wykonywana z wyłączonymi przełącznikami, dzięki czemu użytkownicy nie muszą obserwować wielu nieistotnych komunikatów śledzenia pojawiających się na ekranie lub wypełniających plik dziennika podczas pracy aplikacji. Jeśli problem wystąpi podczas wykonywania aplikacji, można zatrzymać aplikację, włączyć przełączniki i ponownie uruchomić aplikację. Następnie zostaną wyświetlone komunikaty śledzenia.  
  
 Aby użyć przełącznika, należy najpierw utworzyć obiekt switch z klasy **BooleanSwitch,** **TraceSwitch** lub klasy switch zdefiniowanej przez dewelopera. Aby uzyskać więcej informacji na temat tworzenia <xref:System.Diagnostics.Switch> przełączników zdefiniowanych przez dewelopera, zobacz klasę w odwołaniu do programu .NET Framework. Następnie należy ustawić wartość konfiguracji, która określa, kiedy ma być używany obiekt switch. You then test the setting of the switch object in various **Trace** (or **Debug**) tracing methods.  
  
## <a name="trace-levels"></a>Poziomy śledzenia  
 Podczas korzystania **traceswitch**, istnieją dodatkowe uwagi. Obiekt **TraceSwitch** ma cztery właściwości zwracające wartości **logiczne** wskazujące, czy przełącznik jest ustawiony na co najmniej określony poziom:  
  
- <xref:System.Diagnostics.TraceSwitch.TraceError%2A?displayProperty=nameWithType>  
  
- <xref:System.Diagnostics.TraceSwitch.TraceWarning%2A?displayProperty=nameWithType>  
  
- <xref:System.Diagnostics.TraceSwitch.TraceInfo%2A?displayProperty=nameWithType>  
  
- <xref:System.Diagnostics.TraceSwitch.TraceVerbose%2A?displayProperty=nameWithType>  
  
 Poziomy umożliwiają ograniczenie ilości otrzymywanych informacji o śledzeniu tylko do tych informacji potrzebnych do rozwiązania problemu. Należy określić poziom szczegółowości, który ma być odtwarzany w danych wyjściowych śledzenia, ustawiając i konfigurując przełączniki śledzenia do odpowiedniego poziomu śledzenia. Możesz otrzymywać komunikaty o błędach, komunikaty ostrzegawcze, komunikaty informacyjne, pełne komunikaty śledzenia lub w ogóle nie.  
  
 To do Ciebie należy decyzja, jaki rodzaj wiadomości należy skojarzyć z każdym poziomem. Zazwyczaj zawartość wiadomości śledzenia zależy od tego, co można skojarzyć z każdym poziomem, ale można określić różnice między poziomami. Możesz podać szczegółowe opisy problemu na poziomie 3 (**Informacje**), na przykład, ale podać tylko numer referencyjny błędu na poziomie 1 (**Błąd**). To zależy wyłącznie od Ciebie, aby zdecydować, który schemat działa najlepiej w aplikacji.  
  
 Właściwości te odpowiadają wartości 1 do 4 **TraceLevel** wyliczenia. W poniższej tabeli wymieniono poziomy wyliczenia **TraceLevel** i ich wartości.  
  
|Wyliczona wartość|Wartość całkowita|Typ wyświetlanego komunikatu (lub zapisanego do określonego obiektu docelowego wyjściowego)|  
|----------------------|-------------------|---------------------------------------------------------------------------|  
|Wyłączone|0|Brak|  
|Błąd|1|Tylko komunikaty o błędach|  
|Ostrzeżenie|2|Komunikaty ostrzegawcze i komunikaty o błędach|  
|Info|3|Komunikaty informacyjne, komunikaty ostrzegawcze i komunikaty o błędach|  
|Pełny|4|Pełne komunikaty, komunikaty informacyjne, komunikaty ostrzegawcze i komunikaty o błędach|  
  
 **TraceSwitch** właściwości wskazują maksymalny poziom śledzenia dla przełącznika. Oznacza to, że informacje o śledzeniu są zapisywane dla określonego poziomu, a także dla wszystkich niższych poziomów. Na przykład jeśli **TraceInfo** jest **true**, a następnie **TraceError** i **TraceWarning** są również **prawdziwe,** ale **TraceVerbose** może również być **false**.  
  
 Te właściwości są tylko do odczytu. **TraceSwitch** Obiekt automatycznie ustawia je po **ustawieniu tracelevel** właściwości. Przykład:  
  
```vb  
Dim myTraceSwitch As New TraceSwitch("SwitchOne", "The first switch")  
myTraceSwitch.Level = TraceLevel.Info  
' This message box displays true, because setting the level to  
' TraceLevel.Info sets all lower levels to true as well.  
MessageBox.Show(myTraceSwitch.TraceWarning.ToString())  
' This messagebox displays false.  
MessageBox.Show(myTraceSwitch.TraceVerbose.ToString())  
```  
  
```csharp  
System.Diagnostics.TraceSwitch myTraceSwitch =
   new System.Diagnostics.TraceSwitch("SwitchOne", "The first switch");  
myTraceSwitch.Level = System.Diagnostics.TraceLevel.Info;  
// This message box displays true, because setting the level to
// TraceLevel.Info sets all lower levels to true as well.  
MessageBox.Show(myTraceSwitch.TraceWarning.ToString());  
// This message box displays false.  
MessageBox.Show(myTraceSwitch.TraceVerbose.ToString());  
```  
  
## <a name="developer-defined-switches"></a>Przełączniki zdefiniowane przez dewelopera  
 Oprócz dostarczania **booleanSwitch** i **TraceSwitch,** można zdefiniować własne przełączniki, dziedzicząc z **Switch** klasy i zastąpienie metody klasy podstawowej z niestandardowych metod. Aby uzyskać więcej informacji na temat tworzenia <xref:System.Diagnostics.Switch> przełączników zdefiniowanych przez dewelopera, zobacz klasę w odwołaniu do programu .NET Framework.  
  
## <a name="see-also"></a>Zobacz też

- [Obiekty nasłuchujące śledzenia](trace-listeners.md)
- [Porady: dodawanie instrukcji śledzenia do kodu aplikacji](how-to-add-trace-statements-to-application-code.md)
- [Śledzenie i instrumentacja aplikacji](tracing-and-instrumenting-applications.md)
