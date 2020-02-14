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
ms.openlocfilehash: c164e26c6757094b9820af14a098229ab11eb137
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217208"
---
# <a name="trace-switches"></a>Przełączniki śledzenia
Przełączniki śledzenia umożliwiają włączenie, wyłączenie i filtrowanie danych wyjściowych śledzenia. Są to obiekty istniejące w kodzie i można je skonfigurować zewnętrznie za pomocą pliku. config. Istnieją trzy typy przełączników śledzenia podane w .NET Framework: Klasa <xref:System.Diagnostics.BooleanSwitch>, Klasa <xref:System.Diagnostics.TraceSwitch> i Klasa <xref:System.Diagnostics.SourceSwitch>. Klasa <xref:System.Diagnostics.BooleanSwitch> działa jako przełącznik przełącznika, włączając lub wyłączając różne instrukcje śledzenia. Klasy <xref:System.Diagnostics.TraceSwitch> i <xref:System.Diagnostics.SourceSwitch> umożliwiają włączenie przełącznika śledzenia dla określonego poziomu śledzenia, tak aby komunikaty <xref:System.Diagnostics.Trace> lub <xref:System.Diagnostics.TraceSource> określone dla tego poziomu i wszystkie poziomy widoczne poniżej. Jeśli wyłączysz przełącznik, komunikaty śledzenia nie będą wyświetlane. Wszystkie te klasy pochodzą od abstrakcyjnej (**MustInherit**) **przełącznika**klasy, tak jak w przypadku wszystkich przełączników opracowanych przez użytkownika.  
  
 Przełączniki śledzenia mogą być przydatne do filtrowania informacji. Na przykład możesz chcieć zobaczyć każdy komunikat śledzenia w module dostępu do danych, ale tylko komunikaty o błędach w pozostałej części aplikacji. W takim przypadku należy użyć jednego przełącznika śledzenia dla modułu dostępu do danych i jednego przełącznika dla pozostałej części aplikacji. Przy użyciu pliku. config aby skonfigurować przełączniki do odpowiednich ustawień, można kontrolować, jakie typy komunikatów śledzenia zostały odebrane. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie, inicjowanie i konfigurowanie przełączników śledzenia](how-to-create-initialize-and-configure-trace-switches.md).  
  
 Zwykle wdrożona aplikacja jest wykonywana z wyłączonymi przełącznikami, dzięki czemu użytkownicy nie muszą obserwować wielu nieistotnych komunikatów śledzenia pojawiających się na ekranie lub wypełniania pliku dziennika w trakcie uruchamiania aplikacji. Jeśli wystąpi problem podczas wykonywania aplikacji, możesz zatrzymać aplikację, włączyć przełączniki i ponownie uruchomić aplikację. Następnie zostaną wyświetlone komunikaty śledzenia.  
  
 Aby użyć przełącznika, należy najpierw utworzyć obiekt Switch z klasy **BooleanSwitch** , klasy **TraceSwitch** lub klasy Switch zdefiniowanej przez dewelopera. Aby uzyskać więcej informacji na temat tworzenia przełączników zdefiniowanych przez dewelopera, zobacz klasę <xref:System.Diagnostics.Switch> w odwołaniu .NET Framework. Następnie należy ustawić wartość konfiguracji określającą, kiedy ma być używany obiekt przełącznika. Następnie przetestuj ustawienia obiektu Switch w różnych metodach śledzenia **śledzenia** (lub **debugowania**).  
  
## <a name="trace-levels"></a>Poziomy śledzenia  
 Jeśli używasz **TraceSwitch**, istnieją dodatkowe zagadnienia. Obiekt **TraceSwitch** ma cztery właściwości, które zwracają wartości **logiczne** wskazujące, czy przełącznik jest ustawiony na co najmniej na określonym poziomie:  
  
- <xref:System.Diagnostics.TraceSwitch.TraceError%2A?displayProperty=nameWithType>  
  
- <xref:System.Diagnostics.TraceSwitch.TraceWarning%2A?displayProperty=nameWithType>  
  
- <xref:System.Diagnostics.TraceSwitch.TraceInfo%2A?displayProperty=nameWithType>  
  
- <xref:System.Diagnostics.TraceSwitch.TraceVerbose%2A?displayProperty=nameWithType>  
  
 Poziomy umożliwiają ograniczenie ilości informacji śledzenia otrzymywanych tylko do tych informacji, które są potrzebne do rozwiązania problemu. Aby określić żądany poziom szczegółowości w danych wyjściowych śledzenia, należy ustawić i skonfigurować przełączniki śledzenia do odpowiedniego poziomu śledzenia. Można odbierać komunikaty o błędach, komunikaty ostrzegawcze, komunikaty informacyjne, pełne komunikaty śledzenia lub Brak komunikatów.  
  
 W całości można zdecydować, jakiego rodzaju komunikat ma być skojarzony z każdym poziomem. Zwykle zawartość śledzenia komunikatów zależy od tego, co jest skojarzone z każdym poziomem, ale można określić różnice między poziomami. Warto podać szczegółowe opisy problemu na poziomie 3 (**informacje**), na przykład, ale podać tylko numer odwołania błędu na poziomie 1 (**błąd**). W całości można zdecydować, który schemat działa najlepiej w aplikacji.  
  
 Te właściwości odpowiadają wartościom od 1 do 4 wyliczenia **TraceLevel** . Poniższa tabela zawiera listę poziomów wyliczania elementu **TraceLevel** i ich wartości.  
  
|Wartość wyliczana|Wartość całkowita|Typ komunikatu wyświetlanego (lub zapisywana w określonym wyjściowym miejscu docelowym)|  
|----------------------|-------------------|---------------------------------------------------------------------------|  
|Wyłączone|0|None|  
|Błąd|1|Tylko komunikaty o błędach|  
|Ostrzeżenie|2|Komunikaty ostrzegawcze i komunikaty o błędach|  
|Informacje|3|Komunikaty informacyjne, komunikaty ostrzegawcze i komunikaty o błędach|  
|Pełny|4|Komunikaty pełne, komunikaty informacyjne, komunikaty ostrzegawcze i komunikaty o błędach|  
  
 Właściwości **TraceSwitch** wskazują maksymalny poziom śledzenia dla przełącznika. Oznacza to, że informacje o śledzeniu są zapisywane dla określonego poziomu, a także dla wszystkich niższych poziomów. Na przykład jeśli **TraceInfo** ma **wartość true**, wówczas **zarejestrowano element TraceError** i **zarejestrowano element TraceWarning** są również **prawdziwe** , ale **TraceVerbose** może być również **fałszywa**.  
  
 Te właściwości są tylko do odczytu. Obiekt **TraceSwitch** automatycznie ustawia je, gdy właściwość **TraceLevel** jest ustawiona. Na przykład:  
  
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
 Oprócz zapewniania **BooleanSwitch** i **TraceSwitch**, można definiować własne przełączniki, dziedzicząc klasę **Switch** i zastępując metody klasy bazowej przy użyciu dostosowanych metod. Aby uzyskać więcej informacji na temat tworzenia przełączników zdefiniowanych przez dewelopera, zobacz klasę <xref:System.Diagnostics.Switch> w odwołaniu .NET Framework.  
  
## <a name="see-also"></a>Zobacz też

- [Obiekty nasłuchujące śledzenie](trace-listeners.md)
- [Instrukcje: Dodawanie instrukcji śledzenia do kodu aplikacji](how-to-add-trace-statements-to-application-code.md)
- [Śledzenie i instrumentacja aplikacji](tracing-and-instrumenting-applications.md)
