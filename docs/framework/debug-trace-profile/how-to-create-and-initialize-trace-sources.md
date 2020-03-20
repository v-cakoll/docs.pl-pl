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
ms.openlocfilehash: eeccad44bd2719a3cb2a721ba4e32a7bf477636f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174735"
---
# <a name="how-to-create-and-initialize-trace-sources"></a>Porady: tworzenie i inicjowanie źródeł śledzenia
Klasa <xref:System.Diagnostics.TraceSource> jest używana przez aplikacje do tworzenia śladów, które mogą być skojarzone z aplikacją. <xref:System.Diagnostics.TraceSource>zawiera metody śledzenia, które umożliwiają łatwe śledzenie zdarzeń, śledzenie danych i wykrywanie śladów informacyjnych. Dane wyjściowe śledzenia z <xref:System.Diagnostics.TraceSource> mogą być tworzone i inicjowane z lub bez użycia plików konfiguracyjnych. Ten temat zawiera instrukcje dla obu opcji. Jednak zaleca się użycie plików konfiguracyjnych w celu ułatwienia ponownej konfiguracji śladów wytwarzanych przez źródła śledzenia w czasie wykonywania.  
  
### <a name="to-create-and-initialize-a-trace-source-using-a-configuration-file"></a>Aby utworzyć i zainicjować źródło śledzenia przy użyciu pliku konfiguracyjnego  
  
1. Utwórz projekt aplikacji konsoli programu Visual Studio (.NET Framework) i zastąp dostarczony kod następującym kodem. Ten kod rejestruje błędy i ostrzeżenia i wyprowadza niektóre z nich do konsoli, a niektóre z nich do pliku myListener, który jest tworzony przez wpisy w pliku konfiguracyjnym.  
  
     [!code-csharp[TraceSourceExample1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample1/cs/program.cs#1)]
     [!code-vb[TraceSourceExample1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample1/vb/program.vb#1)]  
  
2. Dodaj plik konfiguracji aplikacji, jeśli nie ma, do projektu, aby `TraceSourceApp` zainicjować źródło śledzenia o nazwie w przykładzie kodu w kroku 1.  
  
3. Zastąp domyślną zawartość pliku konfiguracji następującymi ustawieniami, aby zainicjować odbiornik śledzenia konsoli i odbiornik śledzenia modułu zapisującego tekst dla źródła śledzenia utworzonego w kroku 1.  
  
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
  
     Oprócz konfigurowania odbiorników śledzenia plik konfiguracyjny tworzy filtry dla detektorów i tworzy przełącznik źródłowy dla źródła śledzenia. Dwie techniki są wyświetlane do dodawania detektorów śledzenia: dodawanie odbiornika bezpośrednio do źródła śledzenia i dodawanie odbiornika do kolekcji odbiorników udostępnionych, a następnie dodanie go według nazwy do źródła śledzenia. Filtry zidentyfikowane dla dwóch odbiorników są inicjowane z różnych poziomów źródła. Powoduje to, że niektóre wiadomości są zapisywane przez tylko jednego z dwóch odbiorników.  
  
     Plik konfiguracyjny inicjuje ustawienia źródła śledzenia w momencie zainicjowania aplikacji. Aplikacja może dynamicznie zmieniać właściwości ustawione przez plik konfiguracyjny, aby zastąpić wszystkie ustawienia określone przez użytkownika. Na przykład można upewnić się, że wiadomości krytyczne są zawsze wysyłane do pliku tekstowego, niezależnie od bieżących ustawień konfiguracji. Przykładowy kod pokazuje, jak zastąpić ustawienia pliku konfiguracji, aby upewnić się, że wiadomości krytyczne są dane wyjściowe do detektorów śledzenia.  
  
     Zmiana ustawień pliku konfiguracyjnego podczas wykonywania aplikacji nie powoduje zmiany ustawień początkowych. Aby zmienić ustawienia, należy ponownie uruchomić aplikację lub programowo odświeżyć aplikację przy użyciu <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> metody.  
  
### <a name="to-initialize-trace-sources-listeners-and-filters-without-a-configuration-file"></a>Aby zainicjować źródła śledzenia, detektory i filtry bez pliku konfiguracyjnego  
  
- Użyj poniższego przykładu kodu, aby włączyć śledzenie za pośrednictwem źródła śledzenia bez użycia pliku konfiguracyjnego. Nie jest to zalecana praktyka, ale mogą wystąpić okoliczności, w których nie chcesz polegać na plikach konfiguracyjnych w celu zapewnienia śledzenia.  
  
     [!code-csharp[TraceSourceExample2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample2/cs/program.cs#1)]
     [!code-vb[TraceSourceExample2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample2/vb/program.vb#1)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventTypeFilter>
- [Śledzenie i instrumentacja aplikacji](tracing-and-instrumenting-applications.md)
