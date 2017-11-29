---
title: "Porady: tworzenie i inicjowanie źródeł śledzenia"
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
- trace sources
- initializing trace sources
- configuration files [.NET Framework], trace sources
ms.assetid: f88dda6f-5fda-45be-9b3c-745a9b708c4d
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1fc1e843bb5841fcd5571bb1b57d6fb449336240
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-and-initialize-trace-sources"></a>Porady: tworzenie i inicjowanie źródeł śledzenia
<xref:System.Diagnostics.TraceSource> Klasa jest używana przez aplikacje do tworzenia śledzenia, które mogą być skojarzone z aplikacją. <xref:System.Diagnostics.TraceSource>udostępnia metody śledzenia, które pozwalają łatwo śledzić zdarzenia, dane śledzenia i zapisy informacyjne problem. Dane wyjściowe z śledzenia <xref:System.Diagnostics.TraceSource> można tworzyć i zainicjować z lub bez użycia plików konfiguracyjnych. Ten temat zawiera instrukcje dla obu opcji. Jednak zaleca się stosowania plików konfiguracji ułatwia ponowne konfigurowanie śledzenia utworzonego przez źródła śledzenia w czasie wykonywania.  
  
### <a name="to-create-and-initialize-a-trace-source-using-a-configuration-file"></a>Aby utworzyć i zainicjować źródła śledzenia, przy użyciu pliku konfiguracji  
  
1.  Utwórz projekt aplikacji konsoli programu Visual Studio i Zastąp podany kod następującym kodem. Ten kod rejestruje błędy i ostrzeżenia i wyprowadza niektóre z nich w konsoli, a niektóre z nich do pliku myListener, który jest tworzony na podstawie pozycji w pliku konfiguracji.  
  
     [!code-csharp[TraceSourceExample1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample1/cs/program.cs#1)]
     [!code-vb[TraceSourceExample1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample1/vb/program.vb#1)]  
  
2.  Dodaj plik konfiguracji aplikacji, jeśli nie został już dołączony do projektu, aby zainicjować źródła śledzenia o nazwie `TraceSourceApp` w przykładzie kodu w kroku 1.  
  
3.  Zastąp zawartość pliku konfiguracji domyślnej następujących ustawień, aby zainicjować odbiornika śledzenia konsoli i odbiornik śledzenia składnika zapisywania tekstu dla źródła śledzenia, który został utworzony w kroku 1.  
  
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
  
     Oprócz konfigurowania obiektów nasłuchujących śledzenia, plik konfiguracji tworzy filtry dla obu odbiorników oraz przełącznik źródła dla źródła śledzenia. Przedstawiono dwie metody dodawania obiektów nasłuchujących śledzenia: Dodawanie odbiornika bezpośrednio w źródle śledzenia i dodawanie odbiornik do kolekcji udostępnione obiekty nasłuchujące i dodanie go przez nazwę źródła. Filtry dla dwa odbiorniki są inicjowane z poziomu innego źródła. Powoduje to niektóre komunikaty zapisywana przez tylko jeden z dwóch odbiorników.  
  
     Plik konfiguracji inicjuje ustawienia źródła śledzenia w czasie aplikacji został zainicjowany. Aplikację można dynamicznie zmieniać właściwości ustawione przy użyciu pliku konfiguracji, aby zastąpić wszystkie ustawienia określone przez użytkownika. Na przykład możesz chcieć upewnij się, że krytycznych wiadomości zawsze są wysyłane do pliku tekstowego, niezależnie od bieżących ustawień konfiguracji. Przykładowy kod przedstawia sposób zastępują ustawienia pliku konfiguracji w celu zapewnienia krytycznych wiadomości o dane wyjściowe do obiektów nasłuchujących śledzenia.  
  
     Zmiana ustawień pliku konfiguracji, gdy aplikacja jest wykonywany nie zmienia ustawienia początkowe. Aby zmienić ustawienia, należy ponownie uruchomić aplikację lub programowo odświeżania aplikacji za pomocą <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> metody.  
  
### <a name="to-initialize-trace-sources-listeners-and-filters-without-a-configuration-file"></a>Aby zainicjować źródła śledzenia, odbiorników i filtry bez pliku konfiguracji  
  
-   Poniższy przykładowy kod umożliwia włączanie śledzenia przez źródło śladu bez użycia pliku konfiguracji. To nie jest zalecanym rozwiązaniem, ale może być okoliczności, w których nie chcesz zależą od pliki konfiguracji, aby upewnić się, śledzenie.  
  
     [!code-csharp[TraceSourceExample2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample2/cs/program.cs#1)]
     [!code-vb[TraceSourceExample2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample2/vb/program.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.ConsoleTraceListener>  
 <xref:System.Diagnostics.EventTypeFilter>  
 [Śledzenie i Instrumentacja aplikacji](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
