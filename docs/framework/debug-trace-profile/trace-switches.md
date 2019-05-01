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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 85a1a017197826717280f53995ed98f26f1d80bb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61873863"
---
# <a name="trace-switches"></a>Przełączniki śledzenia
Przełączniki śledzenia umożliwiają włączać, wyłączać i filtrować dane wyjściowe śledzenia. Są to obiekty, które istnieją w kodzie i zewnętrznie można skonfigurować za pomocą pliku Config. Istnieją trzy typy przełączników śledzenia w programie .NET Framework: <xref:System.Diagnostics.BooleanSwitch> klasy <xref:System.Diagnostics.TraceSwitch> klasy, a <xref:System.Diagnostics.SourceSwitch> klasy. <xref:System.Diagnostics.BooleanSwitch> Klasa działa jako przełącznik, włączenie lub wyłączenie szereg instrukcji śledzenia. <xref:System.Diagnostics.TraceSwitch> i <xref:System.Diagnostics.SourceSwitch> klasy umożliwiają włączenie przełącznikiem śledzenia dla poziomu śledzenia określonego tak, aby <xref:System.Diagnostics.Trace> lub <xref:System.Diagnostics.TraceSource> komunikaty określonego dla tego poziomu i na wszystkich poziomach poniżej są wyświetlane. Jeśli wyłączysz przełącznika, nie pojawią się komunikaty śledzenia. Te klasy dziedziczyć abstrakcyjnej (**MustInherit**) klasy **przełącznika**, jak powinna żadnych przełączników opracowane przez użytkownika.  
  
 Przełączniki śledzenia mogą być przydatne do filtrowania informacji. Na przykład możesz chcieć wyświetlić każdy komunikat śledzenia w module dostępu do danych, ale komunikaty o błędach tylko w pozostałej części aplikacji. W takim przypadku użyjesz przełącznika jeden śledzenia dla modułu dostępu do danych i jeden do pozostałej części aplikacji. Za pomocą pliku .config do skonfigurowania przełączników do odpowiednie ustawienia, można kontrolować, jakie typy śledzenia komunikatów odebranych. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie, inicjowanie i konfigurowanie przełączników śledzenia](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md).  
  
 Zazwyczaj wdrożonej aplikacji jest wykonywane przy użyciu jego przełączników wyłączone, tak, aby użytkownicy nie muszą obowiązują mnóstwo komunikaty śledzenia nie ma znaczenia, pojawiają się na ekranie lub zapełnia się w pliku dziennika w miarę działania aplikacji. W razie problemów podczas wykonywania aplikacji, można zatrzymać aplikację, Włącz przełączników i ponowne uruchomienie aplikacji. Komunikaty śledzenia zostanie wyświetlony.  
  
 Aby użyć przełącznika należy najpierw utworzyć obiekt przełącznika z **BooleanSwitch** klasy **TraceSwitch** klasy lub klasy przełącznika zdefiniowane dla deweloperów. Aby uzyskać więcej informacji o tworzeniu przełączników zdefiniowane dla deweloperów, zobacz <xref:System.Diagnostics.Switch> klas w dokumentacji .NET Framework. Następnie można ustawić wartości konfiguracji, który określa, kiedy obiekt przełącznika ma być używany. Następnie przetestować ustawienia obiektu przełącznika w różnych **śledzenia** (lub **debugowania**) metody śledzenia.  
  
## <a name="trace-levels"></a>Poziom śledzenia  
 Kiedy używasz **TraceSwitch**, istnieją dodatkowe zagadnienia. A **TraceSwitch** obiekt ma cztery właściwości, które zwracają **logiczna** wartość wskazującą, czy przełącznik jest równa co najmniej określonego poziomu:  
  
- <xref:System.Diagnostics.TraceSwitch.TraceError%2A?displayProperty=nameWithType>  
  
- <xref:System.Diagnostics.TraceSwitch.TraceWarning%2A?displayProperty=nameWithType>  
  
- <xref:System.Diagnostics.TraceSwitch.TraceInfo%2A?displayProperty=nameWithType>  
  
- <xref:System.Diagnostics.TraceSwitch.TraceVerbose%2A?displayProperty=nameWithType>  
  
 Poziomy umożliwiają ograniczenie ilości informacji śledzenia, otrzymany tylko te informacje, które są wymagane w celu rozwiązania problemu. Możesz określić poziom szczegółowości, żądane dane wyjściowe śledzenia przez i konfigurowanie przełączników śledzenia na poziomie śledzenia odpowiednie. Możesz otrzymywać komunikaty o błędach, komunikatów ostrzegawczych, komunikaty informacyjne, komunikaty pełne śledzenie lub żaden komunikat w ogóle.  
  
 To całkowicie decydujesz o tym, jakiego rodzaju wiadomości do skojarzenia z poszczególnych poziomów. Zazwyczaj zawartość komunikaty dotyczące śledzenia zależy od tego, należy skojarzyć z każdym poziomie, ale należy określić różnice między poziomami. Warto podać szczegółowy opis problemu na poziomie 3 (**informacje**), na przykład, ale zapewnia jedynie odwołanie numer błędu na poziomie 1 (**błąd**). To całkowicie decydujesz o tym, jakie system sprawdza się najlepiej w aplikacji.  
  
 Te właściwości odpowiadają wartości od 1 do 4 **TraceLevel** wyliczenia. W poniższej tabeli wymieniono poziomy **TraceLevel** wyliczenie i ich wartości.  
  
|Wartość wyliczeniowa|Wartość całkowita|Typ komunikatu wyświetlanego (lub zapisywane w docelowym określonym produktem wyjściowym)|  
|----------------------|-------------------|---------------------------------------------------------------------------|  
|Off|0|Brak|  
|Błąd|1|Tylko komunikaty o błędach|  
|Ostrzeżenie|2|Komunikaty ostrzegawcze i komunikaty o błędach|  
|Informacje o|3|Komunikaty informacyjne, komunikaty ostrzegawcze i komunikaty o błędach|  
|Pełny|4|Pełne komunikaty, komunikaty informacyjne, komunikaty ostrzegawcze i komunikaty o błędach|  
  
 **TraceSwitch** właściwości wskazują poziom śledzenia maksymalną dla przełącznika. Oznacza to, że informacje śledzenia są zapisywane na poziomie określono również, jak w przypadku wszystkich niższych poziomach. Na przykład jeśli **TraceInfo** jest **true**, następnie **Błąd śledzenia** i **Ostrzeżenie śledzenia** są również **true** ale **TraceVerbose** może okazać się **false**.  
  
 Właściwości te są tylko do odczytu. **TraceSwitch** obiektu automatycznie ustawia je po **TraceLevel** właściwość jest ustawiona. Na przykład:  
  
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
  
## <a name="developer-defined-switches"></a>Przełączniki zdefiniowane dla deweloperów  
 Oprócz zapewniania **BooleanSwitch** i **TraceSwitch**, można zdefiniować własne przełączniki przez dziedziczenie z **przełącznika** klasy i nadpisywania metod klasy bazowej przy użyciu niestandardowych metod. Aby uzyskać więcej informacji o tworzeniu przełączników zdefiniowane dla deweloperów, zobacz <xref:System.Diagnostics.Switch> klas w dokumentacji .NET Framework.  
  
## <a name="see-also"></a>Zobacz także

- [Obiekty nasłuchujące śledzenie](../../../docs/framework/debug-trace-profile/trace-listeners.md)
- [Instrukcje: Dodawanie instrukcji śledzenia do kodu aplikacji](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)
- [Śledzenie i instrumentacja aplikacji](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
