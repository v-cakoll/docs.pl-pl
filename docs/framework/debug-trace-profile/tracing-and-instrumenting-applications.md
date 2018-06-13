---
title: Śledzenie i instrumentacja aplikacji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tracing [.NET Framework]
- debugging [.NET Framework], instrumentation
- performance monitoring, instrumentation
- instrumentation, about instrumentation
- tracing [.NET Framework], about tracing
- performance monitoring, tracing code
- Trace class, instrumentation for .NET applications
ms.assetid: 773b6fc4-9013-4322-b728-5dec7a72e743
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 33d940a051c3185d8a3a04e77ea5899de0475ffc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33392960"
---
# <a name="tracing-and-instrumenting-applications"></a>Śledzenie i instrumentacja aplikacji
Śledzenie jest sposobem monitorowania wykonanie aplikacji jest uruchomiona. Możesz dodać Instrumentacji śledzenia i debugowania aplikacji .NET Framework podczas jej opracowywania i zarówno podczas tworzenia aplikacji, jak i po jej wdrożeniu, można użyć tego instrumentacji. Można użyć <xref:System.Diagnostics.Trace?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug?displayProperty=nameWithType>, i <xref:System.Diagnostics.TraceSource?displayProperty=nameWithType> klasy do rejestrowania informacji o błędach i wykonanie aplikacji w dzienniki, pliki tekstowe lub innych urządzeń w celu późniejszej analizy.  
  
 Termin *Instrumentacji* odwołuje się do możliwości monitorowania lub miary, poziom wydajności produktu i diagnozowanie błędów. W programowaniu oznacza to możliwość aplikację do uwzględnienia:  
  
-   **Kod śledzenia** — odbieranie to informacje dotyczące wykonywania aplikacji w czasie wykonywania.  
  
-   **Debugowanie** — śledzenie i rozwiązywanie problemów programowania w tworzonej aplikacji. Aby uzyskać więcej informacji, zobacz [debugowanie](/visualstudio/debugger/debugging-in-visual-studio).  
  
-   **Liczniki wydajności** -składników, które pozwalają śledzić wydajność aplikacji. Aby uzyskać więcej informacji, zobacz [liczniki wydajności](../../../docs/framework/debug-trace-profile/performance-counters.md).  
  
-   **Dzienniki zdarzeń** -składników, które należy spełnić, odbierania i śledzenie zdarzeń głównych w wykonywanie aplikacji. Aby uzyskać więcej informacji, zobacz <xref:System.Diagnostics.EventLog> klasy.  
  
 Instrumentacji aplikacji, umieszczając instrukcji śledzenia strategicznych lokalizacji w kodzie jest szczególnie przydatna w przypadku aplikacji rozproszonych. Za pomocą instrukcji śledzenia mogą dodawać aplikacji nie tylko do wyświetlania informacji w przypadku wystąpienia problemów, ale do monitorowania, jak działa aplikacja.  
  
 <xref:System.Diagnostics.TraceSource> Klasy zawiera ulepszone funkcje śledzenia i można użyć zamiast metod statycznych starszej <xref:System.Diagnostics.Trace> i <xref:System.Diagnostics.Debug> klasy śledzenia. Znanych <xref:System.Diagnostics.Trace> i <xref:System.Diagnostics.Debug> klas są nadal powszechnie używane, ale <xref:System.Diagnostics.TraceSource> klasy jest zalecane w przypadku nowych śledzenia poleceń, takich jak <xref:System.Diagnostics.TraceSource.TraceEvent%2A> i <xref:System.Diagnostics.TraceSource.TraceData%2A>.  
  
 <xref:System.Diagnostics.Trace> i <xref:System.Diagnostics.Debug> klas są identyczne, z wyjątkiem tej procedury i funkcje <xref:System.Diagnostics.Trace> klasy są skompilowane domyślnie w kompilacjach wydania, ale tych <xref:System.Diagnostics.Debug> klasy nie są.  
  
 <xref:System.Diagnostics.Trace> i <xref:System.Diagnostics.Debug> klasy pozwalają monitorować i sprawdź, czy wydajność aplikacji, podczas tworzenia lub po wdrożeniu. Na przykład można użyć <xref:System.Diagnostics.Trace> klasy do śledzenia poszczególnych typów akcji we wdrożonej aplikacji jako wystąpić (na przykład tworzenie nowych połączeń z bazą danych), a więc można monitorować wydajność aplikacji.  
  
## <a name="code-tracing-and-debugging"></a>Kod śledzenia i debugowania  
 Podczas tworzenia, można użyć danych wyjściowych metody <xref:System.Diagnostics.Debug> klasy do wyświetlenia w oknie danych wyjściowych programu Visual Studio zintegrowane środowisko programistyczne (IDE) wiadomości. Na przykład:  
  
```vb  
Trace.WriteLine("Hello World!")  
Debug.WriteLine("Hello World!")  
```  
  
```csharp  
System.Diagnostics.Trace.WriteLine("Hello World!");  
System.Diagnostics.Debug.WriteLine("Hello World!");  
```  
  
 Każdy z tych przykładów wyświetli "Witaj świecie!" w oknie dane wyjściowe po uruchomieniu aplikacji w debugerze.  
  
 Dzięki temu można debugowania aplikacji i optymalizacji ich wydajności na podstawie ich zachowania w środowisku testowym. Można debugować aplikacji w kompilacji debugowania z <xref:System.Diagnostics.Debug> atrybut conditional włączona, aby odbierać wszystkie dane wyjściowe debugowania. Gdy aplikacja jest gotowa do wydania, będzie można kompilować kompilację wersji bez włączania <xref:System.Diagnostics.Debug> warunkowego atrybutu, tak aby kompilator nie będzie zawierać debugowania kodu w końcowym pliku wykonywalnego. Aby uzyskać więcej informacji, zobacz [porady: kompilowanie warunkowe ze śledzeniem i debugowaniem](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md). Aby uzyskać więcej informacji o konfiguracjach kompilacji w innej aplikacji, zobacz [kompilowania i tworzenia](/visualstudio/ide/compiling-and-building-in-visual-studio).  
  
 Można także śledzić wykonywanie kodu w zainstalowanej aplikacji, za pomocą metody <xref:System.Diagnostics.Trace> klasy. Przez umieszczenie [przełączniki śledzenia](../../../docs/framework/debug-trace-profile/trace-switches.md) w kodzie, można kontrolować czy występuje śledzenia i jest ich zakresu. Dzięki temu można monitorować stan aplikacji w środowisku produkcyjnym. Jest to szczególnie ważne w aplikacji biznesowych, która używa wielu składniki działające na wielu komputerach. Można kontrolować, jak przełączniki są używane po wdrożeniu za pomocą pliku konfiguracji. Aby uzyskać więcej informacji, zobacz [porady: tworzenie, inicjowanie i konfigurowanie przełączników śledzenia](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md).  
  
 Gdy tworzysz aplikację, dla którego mają być używane do śledzenia, należy zwykle zawiera zarówno śledzenie i debugowanie wiadomości w kodzie aplikacji. Gdy wszystko będzie gotowe do wdrożenia aplikacji można kompilować kompilację wersji bez włączania **debugowania** atrybut conditional. Jednak można włączyć **śledzenia** warunkowego atrybutu, aby kompilator zawiera kod śledzenia w pliku wykonywalnego. Aby uzyskać więcej informacji, zobacz [porady: kompilowanie warunkowe ze śledzeniem i debugowaniem](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md).  
  
### <a name="phases-of-code-tracing"></a>Fazy kod śledzenia  
 Istnieją trzy etapy kod śledzenia:  
  
1.  **Instrumentacja** — Dodaj kod śledzenia do aplikacji.  
  
2.  **Śledzenie** — kod śledzenia zapisuje informacje w określonym obiekcie docelowym.  
  
3.  **Analiza** — ocenić informacje śledzenia do identyfikowania i zrozumienia problemów w aplikacji.  
  
 Podczas tworzenia wszystkie debugowania i śledzenia danych wyjściowych metody zapisywać informacje w oknie danych wyjściowych w programie Visual Studio domyślnie. We wdrożonej aplikacji do obiektów docelowych, które można określić metody zapisu informacji o śledzeniu. Aby uzyskać więcej informacji na temat określania obiektu docelowego dane wyjściowe do śledzenia i debugowania, zobacz [obiektów nasłuchujących śledzenia](../../../docs/framework/debug-trace-profile/trace-listeners.md).  
  
 Oto ogólny widok główne etapy zwykle za pomocą śledzenia do analizowania i rozwiązać potencjalne problemy we wdrożonej aplikacji. Aby uzyskać więcej informacji na temat sposobu wykonywania tych kroków, zobacz odpowiednie łącze.  
  
##### <a name="to-use-tracing-in-an-application"></a>Aby użyć śledzenia w aplikacji  
  
1.  Należy rozważyć, które śledzenie danych wyjściowych będzie chcesz otrzymywać u klienta po wdrożeniu aplikacji.  
  
2.  Utwórz zestaw parametrów. Aby uzyskać więcej informacji, zobacz [porady: Konfigurowanie przełączników śledzenia](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md).  
  
3.  Dodawanie instrukcji śledzenia do kodu aplikacji.  
  
4.  Określ, w którym dane wyjściowe śledzenia są wyświetlane, a następnie dodaj odpowiednie odbiorników. Aby uzyskać więcej informacji, zobacz [tworzenie i Inicjowanie obiektów nasłuchujących śledzenia](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-listeners.md).  
  
5.  Testowanie i debugowanie aplikacji i kod śledzenia, które zawiera.  
  
6.  Kompilowanie aplikacji na kod wykonywalny przy użyciu jednej z następujących procedur:  
  
    -   Użyj **kompilacji** menu wraz z **debugowania** strony **strony właściwości** okno dialogowe w **Eksploratora rozwiązań**. Użyj tego podczas kompilowania w programie Visual Studio.  
  
         \- lub -  
  
    -   Użyj **śledzenia** i **debugowania** dyrektywy kompilatora wiersza polecenia metody kompilacji. Aby uzyskać więcej informacji, zobacz [kompilowanie warunkowe ze śledzeniem i debugowaniem](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md). Użyj tego podczas kompilowania z wiersza polecenia.  
  
7.  Jeśli wystąpi problem w czasie wykonywania, włącz przełącznik odpowiednie śledzenia. Aby uzyskać więcej informacji, zobacz [Konfigurowanie przełączników śledzenia](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md).  
  
     Kod śledzenia zapisuje komunikaty śledzenia do określonego obiektu docelowego, na przykład ekranu plik tekstowy i dziennik zdarzeń. Typ odbiornika uwzględnione w **Trace.Listeners** kolekcji określa obiekt docelowy.  
  
8.  Przeanalizuj komunikaty śledzenia do identyfikowania i zrozumienia problem w aplikacji.  
  
## <a name="trace-instrumentation-and-distributed-applications"></a>Instrumentacja śledzenia i aplikacji rozproszonych  
 Podczas tworzenia aplikacji rozproszonej może być bardzo trudne do testowania aplikacji w taki sposób, w którym będzie on używany. Kilka zespołów deweloperów wykorzystuje funkcję do testowania wszystkie możliwe kombinacje systemów operacyjnych lub przeglądarki sieci Web (w tym wszystkie opcje zlokalizowanego języka) lub aby symulować dużą liczbę użytkowników, którzy uzyskują dostęp do aplikacji w tym samym czasie. W tej sytuacji nie można sprawdzić, jak aplikacji rozproszonej będzie odpowiadać dużej ilości różnych konfiguracji i zachowania unikatowy przez użytkownika końcowego. Ponadto wielu części aplikacji rozproszonej jest bez interfejsu użytkownika bezpośredniej interakcji lub wyświetlać informacje dotyczące aktywności części.  
  
 Jednak można zniwelować to przez aplikacje rozproszone do opisywania określone zdarzenia przydatne dla administratorów systemu, szczególnie rzeczy, które udaje przez włączenie *Instrumentacji* aplikacji — to znaczy przez umieszczenie instrukcje śledzenia strategicznych lokalizacji w kodzie. Następnie, jeśli nieoczekiwane występuje w czasie wykonywania (na przykład bardzo długi czas odpowiedzi), można określić, prawdopodobną przyczyną.  
  
 Z instrukcji śledzenia można uniknąć trudne badanie oryginalny kod źródłowy, modyfikowanie, ponowną kompilację i podjęto próbę utworzenia błędów czasu wykonywania w środowisku debugowania. Należy pamiętać, że mogą dodawać nie tylko do wyświetlania błędów, ale do monitorowania wydajności aplikacji.  
  
## <a name="strategic-placement-of-trace-statements"></a>Strategiczne umieszczania instrukcje śledzenia  
 Szczególną musi wykonywać podczas umieszczania Twojej instrukcji śledzenia do użytku w czasie wykonywania. Należy rozważyć informacjach śledzenia jest potrzebny we wdrożonej aplikacji tak, aby wszystkie scenariusze prawdopodobnie śledzenie odpowiednio zostały uwzględnione. Ponieważ aplikacje używające śledzenia różnią się znacznie istnieją nie ogólne wskazówki dotyczące umieszczania strategicznych śledzenia. Aby uzyskać więcej informacji na umieszczenie instrukcji śledzenia, zobacz [porady: Dodawanie instrukcji śledzenia do kodu aplikacji](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md).  
  
## <a name="output-from-tracing"></a>Dane wyjściowe śledzenia  
 Dane wyjściowe śledzenia są zbierane przez obiekty o nazwie *odbiorników*. Odbiornik jest obiekt, który odbiera dane wyjściowe śledzenia i zapisuje go na urządzeniach (zwykle plik okna, dziennika lub tekst). Po utworzeniu odbiornika śledzenia zwykle jest dodawany do <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> kolekcji, umożliwiając odbiornika do odbierania wszystkich danych wyjściowych śledzenia.  
  
 Śledzenie informacji są zawsze zapisywane co najmniej domyślne <xref:System.Diagnostics.Trace> docelowego dane wyjściowe <xref:System.Diagnostics.DefaultTraceListener>. Jeśli z jakiegoś powodu zostały usunięte <xref:System.Diagnostics.DefaultTraceListener> bez dodawania innych odbiorników do <xref:System.Diagnostics.Trace.Listeners%2A> kolekcji, nie będziesz otrzymywać komunikaty śledzenia. Aby uzyskać więcej informacji, zobacz [obiektów nasłuchujących śledzenia](../../../docs/framework/debug-trace-profile/trace-listeners.md).  
  
 Sześciu <xref:System.Diagnostics.Debug> elementy członkowskie i <xref:System.Diagnostics.Trace> metody, które zapisują informacje śledzenia są wymienione w poniższej tabeli.  
  
|Metoda|Dane wyjściowe|  
|------------|------------|  
|**Assert**|Określony tekst; lub, jeśli nie zostanie określona, wywołanie stosu. Dane wyjściowe są zapisywane tylko jeśli warunek określony jako argument w **Assert** instrukcja jest **false**.|  
|**Niepowodzenie**|Określony tekst; lub, jeśli nie zostanie określona, wywołanie stosu.|  
|**zapisu**|Określony tekst.|  
|**WriteIf**|Określony tekst, jeśli warunek określony jako argument w **WriteIf** instrukcji jest spełniony.|  
|**WriteLine**|Określony tekst i powrotu karetki.|  
|**WriteLineIf**|Określony tekst i karetki zwracany, jeśli warunek określony jako argument w **WriteLineIf** instrukcji jest spełniony.|  
  
 Wszystkie obiekty nasłuchujące w <xref:System.Diagnostics.Trace.Listeners%2A> kolekcji odbierać komunikaty opisane w powyższej tabeli, ale akcje wykonywane może się różnić w zależności od tego, jakiego rodzaju odbiornika odbiera wiadomości. Na przykład <xref:System.Diagnostics.DefaultTraceListener> Wyświetla okno dialogowe potwierdzenia, gdy odbierze **się nie powieść** lub nie powiodło się **Assert** powiadomień, ale <xref:System.Diagnostics.TextWriterTraceListener> po prostu zapisuje dane wyjściowe do jego strumienia.  
  
 Zaimplementowanie własne odbiornika służy do tworzenia niestandardowych wyników. Odbiornik śledzenia niestandardowych mogą, na przykład wyświetlić wiadomości do okna komunikatu lub połączenia z bazą danych, aby dodać komunikaty do tabeli. Wszystkie niestandardowe odbiorniki powinien obsługiwać sześciu metod wymienionych powyżej. Aby uzyskać więcej informacji o tworzeniu odbiorników zdefiniowane przez deweloperów, zobacz <xref:System.Diagnostics.TraceListener> w odwołania programu .NET Framework.  
  
> [!NOTE]
>  W [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], **Debug.Write —**, **Debug.WriteIf**, **Debug.WriteLine**, i **Debug.WriteLineIf** zastąpienia metody **Debug.Print** metody, które były dostępne w starszych wersjach programu Visual Basic.  
  
 **Zapisu** i **WriteLine** metody zawsze wpisać tekst można określić. **Assert**, **WriteIf**, i **WriteLineIf** wymagają argument logiczna, która kontroluje, czy zapisują określony tekst; zapisują określony tekst tylko jeśli wyrażenie jest **true** (dla **WriteIf** i **WriteLineIf**), lub **false** (dla **Assert**). **Niepowodzenie** metody zawsze zapisuje określony tekst. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie instrukcji śledzenia do kodu aplikacji](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md) i odwołania programu .NET Framework.  
  
## <a name="security-concerns"></a>Zagadnienia dotyczące zabezpieczeń  
 Jeśli nie można wyłączyć śledzenie i debugowanie przed wdrożeniem aplikacji ASP.NET, aplikacja może ujawnić informacje o sobie, który może zostać wykorzystana przez złośliwych programów. Aby uzyskać więcej informacji, zobacz [porady: kompilowanie warunkowe ze śledzeniem i debugowaniem](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md), [kompilowania i tworzenia](/visualstudio/ide/compiling-and-building-in-visual-studio), i [porady: tworzenie, inicjowanie i konfigurowanie przełączników śledzenia](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md) . Debugowanie jest także można skonfigurować za pomocą programu Internet Information Services (IIS).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.TraceSource>  
 [Kontrakty kodu](../../../docs/framework/debug-trace-profile/code-contracts.md)  
 [C#, F # i typy projektów Visual Basic](/visualstudio/debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types)  
 [Instrukcje: Dodawanie instrukcji śledzenia do kodu aplikacji](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)  
 [Instrukcje: Kompilowanie warunkowe ze śledzeniem i debugowaniem](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)  
 [Instrukcje: tworzenie, inicjowanie i konfigurowanie przełączników śledzenia](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)  
 [Instrukcje: Tworzenie i inicjowanie źródeł śledzenia](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md)  
 [Instrukcje: Użycie TraceSource i filtrów z obiektami nasłuchującymi śledzenie](../../../docs/framework/debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md)  
 [Obiekty nasłuchujące śledzenie](../../../docs/framework/debug-trace-profile/trace-listeners.md)  
 [Przełączniki śledzenia](../../../docs/framework/debug-trace-profile/trace-switches.md)
