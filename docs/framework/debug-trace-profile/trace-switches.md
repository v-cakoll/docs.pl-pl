---
title: "Przełączniki śledzenia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 082d84fe0ac4193f3da5ac9be52789432bde76aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="trace-switches"></a>Przełączniki śledzenia
Przełączniki śledzenia umożliwiają włączać, wyłączać i Filtruj dane wyjściowe śledzenia. Są one obiekty, które istnieją w kodzie i zewnętrznie można skonfigurować za pomocą pliku .config. Istnieją trzy typy przełączników śledzenia w programie .NET Framework: <xref:System.Diagnostics.BooleanSwitch> klasy <xref:System.Diagnostics.TraceSwitch> klasy, a <xref:System.Diagnostics.SourceSwitch> klasy. <xref:System.Diagnostics.BooleanSwitch> Klasa działa jako przełącznika przełączania, albo Włączanie lub wyłączanie szereg instrukcji śledzenia. <xref:System.Diagnostics.TraceSwitch> i <xref:System.Diagnostics.SourceSwitch> klasy umożliwiają włączenie przełącznika śledzenia, poziom śledzenia w szczególności, aby <xref:System.Diagnostics.Trace> lub <xref:System.Diagnostics.TraceSource> wiadomości określona dla tego poziomu i na wszystkich poziomach poniżej są wyświetlane. Jeśli wyłączysz przełącznika nie będą wyświetlane komunikaty śledzenia. Te klasy pochodzi z klasy abstrakcyjnej (**MustInherit**) klasy **przełącznika**, jak powinna przełącznikami opracowane przez użytkownika.  
  
 Przełączniki śledzenia może być przydatna do filtrowania informacji. Na przykład możesz chcieć Zobacz każdej wiadomości śledzenia w modułu dostępu do danych, ale tylko komunikaty w pozostałej części aplikacji. W takim przypadku można skorzystać przełącznika śledzenia jednego modułu dostępu do danych i jeden w pozostałej części aplikacji. Przy użyciu pliku .config skonfigurowanie przełączników, aby odpowiednie ustawienia, można kontrolować, jakie typy śledzenia komunikatów odebranych. Aby uzyskać więcej informacji, zobacz [porady: tworzenie, inicjowanie i konfigurowanie przełączników śledzenia](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md).  
  
 Zazwyczaj wdrożonej aplikacji została wykonana z jego przełącznikami wyłączone, tak, aby użytkownicy nie muszą przestrzegać partii nie ma znaczenia śledzenia komunikatów wyświetlanych na ekranie lub zapełnia się w pliku dziennika jako jest uruchamiana aplikacja. Jeśli wystąpi problem podczas wykonywania aplikacji, Zatrzymaj aplikację, Włącz przełączniki i ponownie uruchom aplikację. Następnie zostanie wyświetlony komunikaty śledzenia.  
  
 Aby użyć przełącznika należy najpierw utworzyć obiekt przełącznika z **BooleanSwitch** klasy, **TraceSwitch** klasy lub klas zdefiniowanych przez dewelopera przełącznika. Aby uzyskać więcej informacji o tworzeniu zdefiniowane przez dewelopera przełączników, zobacz <xref:System.Diagnostics.Switch> klasy w odwołania programu .NET Framework. Następnie należy ustawić wartość konfiguracji, która określa, kiedy ma być używany obiekt przełącznika. Następnie przetestuj ustawienia obiektu przełącznika w różnych **śledzenia** (lub **debugowania**) metody śledzenia.  
  
## <a name="trace-levels"></a>Poziomy śledzenia  
 Jeśli używasz **TraceSwitch**, istnieją dodatkowe zagadnienia. A **TraceSwitch** obiekt ma cztery właściwości, które zwracają **logiczna** wartość wskazującą, czy przełącznik jest równa co najmniej określonym poziomie:  
  
-   <xref:System.Diagnostics.TraceSwitch.TraceError%2A?displayProperty=nameWithType>  
  
-   <xref:System.Diagnostics.TraceSwitch.TraceWarning%2A?displayProperty=nameWithType>  
  
-   <xref:System.Diagnostics.TraceSwitch.TraceInfo%2A?displayProperty=nameWithType>  
  
-   <xref:System.Diagnostics.TraceSwitch.TraceVerbose%2A?displayProperty=nameWithType>  
  
 Poziomy umożliwiają ograniczenie ilości informacji śledzenia, otrzymany tylko te informacje, które są potrzebne do rozwiązania problemu. Możesz określić poziom szczegółowości interesujące dane wyjściowe śledzenia przez i konfigurowanie przełączników śledzenia do poziomu śledzenia odpowiednie. Na wszystkich może odbierać komunikaty o błędach, komunikaty ostrzegawcze, komunikaty informacyjne, komunikaty pełne śledzenia lub żaden komunikat.  
  
 Jest całkowicie można zdecydować, jakiego rodzaju wiadomości do skojarzenia z każdym poziomie. Zazwyczaj zawartość komunikaty śledzenia zależy od tego, skojarzony z każdym poziomie, ale określić różnice między poziomami. Należy podać szczegółowe opisy problemów na poziomie 3 (**informacji**), na przykład, jednak tylko błąd numer odwołania na poziomie 1 (**błąd**). Jest całkowicie można zdecydować, jakiego schemat działa najlepiej w aplikacji.  
  
 Te właściwości odpowiada wartości 1 do 4 **TraceLevel** wyliczenia. W poniższej tabeli wymieniono poziomy **TraceLevel** wyliczenie i ich wartości.  
  
|Wartość wyliczenia|Wartość całkowita|Typ komunikatu wyświetlane (lub zapisywane w docelowym określonym produktem wyjściowym)|  
|----------------------|-------------------|---------------------------------------------------------------------------|  
|Off|0|Brak|  
|Błąd|1|Tylko komunikaty o błędach|  
|Ostrzeżenie|2|Ostrzeżenia i komunikaty o błędach|  
|Informacje o|3|Komunikaty informacyjne, ostrzeżenia i komunikaty o błędach|  
|Pełny|4|Pełne komunikaty, komunikaty informacyjne, ostrzeżenia i komunikaty o błędach|  
  
 **TraceSwitch** właściwości wskazuje poziom śledzenia maksymalną dla tego przełącznika. Oznacza to informacje śledzenia są zapisywane dla poziomu określonego również, jak w przypadku wszystkich niższych poziomach. Na przykład jeśli **TraceInfo** jest **true**, następnie **Błąd śledzenia** i **zarejestrowano element TraceWarning** są również **true** ale **TraceVerbose** może również być **false**.  
  
 Te właściwości są tylko do odczytu. **TraceSwitch** obiektu są automatycznie ustawiane w ich przypadku **TraceLevel** właściwość jest ustawiona. Na przykład:  
  
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
  
## <a name="developer-defined-switches"></a>Zdefiniowane przez dewelopera przełączników  
 Oprócz zapewnienia **BooleanSwitch** i **TraceSwitch**, możesz definiować własne przełączniki za dziedziczących **przełącznika** klasy i zastępowanie metod klasy podstawowej za pomocą metod niestandardowych. Aby uzyskać więcej informacji o tworzeniu zdefiniowane przez dewelopera przełączników, zobacz <xref:System.Diagnostics.Switch> klasy w odwołania programu .NET Framework.  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekty nasłuchujące śledzenia](../../../docs/framework/debug-trace-profile/trace-listeners.md)  
 [Porady: Dodawanie instrukcji śledzenia do kodu aplikacji](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)  
 [Śledzenie i Instrumentacja aplikacji](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
