---
title: 'Instrukcje: Tworzenie i inicjowanie źródeł śledzenia'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- trace sources
- initializing trace sources
- configuration files [.NET Framework], trace sources
ms.assetid: f88dda6f-5fda-45be-9b3c-745a9b708c4d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2d96de43d258e4a7ff925e0c5b1702727e67d737
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61754521"
---
# <a name="how-to-create-and-initialize-trace-sources"></a>Instrukcje: Tworzenie i inicjowanie źródeł śledzenia
<xref:System.Diagnostics.TraceSource> Klasa jest używana przez aplikacje do tworzenia śladów, które mogą być skojarzone z aplikacją. <xref:System.Diagnostics.TraceSource> udostępnia metody śledzenia, które pozwalają na łatwe śledzenie zdarzeń, dane śledzenia i ślady informacyjne problemu. Dane wyjściowe śledzenia z <xref:System.Diagnostics.TraceSource> mogą być tworzone i inicjowane z użyciem lub bez korzystania z plików konfiguracji. Ten temat zawiera instrukcje dla obu opcji. Jednak zaleca się używać plików konfiguracyjnych ułatwiających rekonfigurację śladów produkowanych przez źródła śledzenia w czasie wykonywania.  
  
### <a name="to-create-and-initialize-a-trace-source-using-a-configuration-file"></a>Aby utworzyć i zainicjować źródło śledzenia przy użyciu pliku konfiguracji  
  
1. Utwórz projekt aplikacji konsoli Visual Studio i Zastąp dostarczony kod następującym kodem. Ten kod rejestruje błędy i ostrzeżenia i wysyła niektóre z nich do konsoli, a niektóre z nich do pliku myListener, który jest tworzony przez wpisy w pliku konfiguracji.  
  
     [!code-csharp[TraceSourceExample1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample1/cs/program.cs#1)]
     [!code-vb[TraceSourceExample1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample1/vb/program.vb#1)]  
  
2. Dodaj plik konfiguracji aplikacji, jeśli nie został jeszcze dołączony, do projektu, aby zainicjować źródła śledzenia o nazwie `TraceSourceApp` w przykładzie kodu w kroku 1.  
  
3. Zastąp domyślną treść pliku konfiguracji z następującymi ustawieniami, aby zainicjować detektor śledzenia konsoli i odbiornik śledzenia modułu zapisującego tekst dla źródła śledzenia, który został utworzony w kroku 1.  
  
    ```xml  
    <configuration>  
      <system.diagnostics>  
        <sources>  
          <source name="TraceSourceApp"   
            switchName="sourceSwitch"   
            switchType="System.Diagnostics.SourceSwitch">  
            <listeners>  
              <add name="console"   
                type="System.Diagnostics.ConsoleTraceListener">  
                <filter type="System.Diagnostics.EventTypeFilter"   
                  initializeData="Error"/>  
              </add>  
              <add name="myListener"/>  
              <remove name="Default"/>  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="sourceSwitch" value="Error"/>  
        </switches>  
        <sharedListeners>  
          <add name="myListener"   
            type="System.Diagnostics.TextWriterTraceListener"   
            initializeData="myListener.log">  
            <filter type="System.Diagnostics.EventTypeFilter"   
              initializeData="Error"/>  
          </add>  
        </sharedListeners>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
     Poza skonfigurowaniem detektorów śledzenia, plik konfiguracyjny tworzy filtry dla obu detektorów oraz tworzy przełącznik źródła dla źródła śledzenia. Do dodawania detektorów śledzenia pokazano dwie techniki: dodanie detektora bezpośrednio do źródła śledzenia i dodanie detektora do kolekcji współdzielonych detektorów, a następnie dodanie go według nazwy do źródła śledzenia. Filtry określone dla obu detektorów są inicjowane z różnymi poziomami źródła. Skutkuje to pewne komunikaty są zapisywane przez tylko jeden z dwóch detektorów.  
  
     Plik konfiguracyjny inicjuje ustawienia źródła śledzenia w czasie, w których aplikacja została zainicjowany. Aplikacja można dynamicznie zmieniać właściwości ustawione w pliku konfiguracyjnym, aby zastąpić wszelkie ustawienia określone przez użytkownika. Na przykład możesz chcieć upewnij się, że krytyczne wiadomości są zawsze wysyłane do pliku tekstowego, niezależnie od bieżących ustawień konfiguracji. Przykładowy kod ilustruje sposób zastąpienia ustawień pliku konfiguracji, aby upewnić się, że newralgiczne komunikaty są do odbiorników śledzenia.  
  
     Zmiana ustawień pliku konfiguracji, podczas wykonywania aplikacji nie powoduje zmiany ustawień początkowych. Aby zmienić ustawienia, należy ponownie uruchomić aplikację lub programowo odświeżyć aplikację za pomocą <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> metody.  
  
### <a name="to-initialize-trace-sources-listeners-and-filters-without-a-configuration-file"></a>Aby zainicjować źródła śledzenia, detektory i filtry bez pliku konfiguracji  
  
- Użyj poniższy przykład kodu umożliwia śledzenie za pośrednictwem źródła śledzenia bez użycia pliku konfiguracji. Nie jest to zalecana praktyka, ale mogą zaistnieć okoliczności, w których nie chcesz zależało od plików konfiguracyjnych, aby upewnić się, śledzenia.  
  
     [!code-csharp[TraceSourceExample2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample2/cs/program.cs#1)]
     [!code-vb[TraceSourceExample2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample2/vb/program.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventTypeFilter>
- [Śledzenie i instrumentacja aplikacji](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
