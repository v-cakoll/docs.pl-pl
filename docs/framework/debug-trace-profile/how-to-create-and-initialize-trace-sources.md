---
title: 'Porady: tworzenie i inicjowanie źródeł śledzenia'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- trace sources
- initializing trace sources
- configuration files [.NET Framework], trace sources
ms.assetid: f88dda6f-5fda-45be-9b3c-745a9b708c4d
ms.openlocfilehash: cc2987499aa094960c08d220940fe1aed5440b2d
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449962"
---
# <a name="how-to-create-and-initialize-trace-sources"></a>Porady: tworzenie i inicjowanie źródeł śledzenia
Klasa <xref:System.Diagnostics.TraceSource> jest używana przez aplikacje do tworzenia śladów, które mogą być skojarzone z aplikacją. <xref:System.Diagnostics.TraceSource> udostępnia metody śledzenia, które umożliwiają łatwe śledzenie zdarzeń, danych śledzenia i wystawianie śladów informacyjnych. Dane wyjściowe śledzenia z <xref:System.Diagnostics.TraceSource> mogą być tworzone i inicjowane przy użyciu plików konfiguracyjnych lub bez nich. Ten temat zawiera instrukcje dotyczące obu tych opcji. Zaleca się jednak używanie plików konfiguracji w celu ułatwienia ponownej konfiguracji śladów generowanych przez źródła śledzenia w czasie wykonywania.  
  
### <a name="to-create-and-initialize-a-trace-source-using-a-configuration-file"></a>Aby utworzyć i zainicjować Źródło śledzenia przy użyciu pliku konfiguracji  
  
1. Utwórz projekt aplikacji konsolowej programu Visual Studio (.NET Framework) i Zastąp podany kod następującym kodem. Ten kod rejestruje błędy i ostrzeżenia i wyprowadza niektóre z nich do konsoli programu, a niektóre z nich do pliku, który jest tworzony przez wpisy w pliku konfiguracji.  
  
     [!code-csharp[TraceSourceExample1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample1/cs/program.cs#1)]
     [!code-vb[TraceSourceExample1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample1/vb/program.vb#1)]  
  
2. Dodaj do projektu plik konfiguracji aplikacji, jeśli nie istnieje, w celu zainicjowania źródła śledzenia o nazwie `TraceSourceApp` w przykładzie kodu w kroku 1.  
  
3. Zastąp domyślną zawartość pliku konfiguracji następującymi ustawieniami, aby zainicjować odbiornik śledzenia konsoli i odbiornik śledzenia tekstu składnika zapisywania dla źródła śledzenia, które zostało utworzone w kroku 1.  
  
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
  
     Oprócz konfigurowania detektorów śledzenia, plik konfiguracji tworzy filtry dla obu odbiorników i tworzy przełącznik źródła dla źródła śledzenia. Dwie techniki są pokazane w przypadku dodawania detektorów śledzenia: dodanie odbiornika bezpośrednio do źródła śledzenia i dodanie odbiornika do kolekcji udostępnionych odbiorników, a następnie dodanie go według nazwy do źródła śledzenia. Filtry zidentyfikowane dla dwóch odbiorników są inicjowane z różnymi poziomami źródła. Powoduje to, że niektóre komunikaty są zapisywane tylko przez jeden z dwóch odbiorników.  
  
     Plik konfiguracji inicjuje ustawienia dla źródła śledzenia w momencie zainicjowania aplikacji. Aplikacja może dynamicznie zmieniać właściwości ustawiane przez plik konfiguracji w celu zastąpienia wszelkich ustawień określonych przez użytkownika. Można na przykład upewnić się, że komunikaty krytyczne są zawsze wysyłane do pliku tekstowego, niezależnie od bieżących ustawień konfiguracji. Przykładowy kod demonstruje sposób przesłania ustawień pliku konfiguracji, aby zapewnić, że krytyczne komunikaty są wyprowadzane do odbiorników śledzenia.  
  
     Zmiana ustawień pliku konfiguracji w trakcie wykonywania aplikacji nie powoduje zmiany ustawień początkowych. Aby zmienić ustawienia, należy ponownie uruchomić aplikację lub programowo odświeżyć aplikację przy użyciu metody <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType>.  
  
### <a name="to-initialize-trace-sources-listeners-and-filters-without-a-configuration-file"></a>Aby zainicjować źródła śledzenia, detektory i filtry bez pliku konfiguracji  
  
- Użyj następującego przykładowego kodu, aby włączyć śledzenie za pośrednictwem źródła śledzenia bez użycia pliku konfiguracji. Nie jest to zalecane rozwiązanie, ale mogą wystąpić sytuacje, w których nie należy zależeć od plików konfiguracji w celu zapewnienia śledzenia.  
  
     [!code-csharp[TraceSourceExample2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample2/cs/program.cs#1)]
     [!code-vb[TraceSourceExample2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample2/vb/program.vb#1)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventTypeFilter>
- [Śledzenie i instrumentacja aplikacji](tracing-and-instrumenting-applications.md)
