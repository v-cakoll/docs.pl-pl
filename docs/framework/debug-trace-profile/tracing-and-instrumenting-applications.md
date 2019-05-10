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
ms.openlocfilehash: 84af29aa169710f8de86c383429bf391fbc20bd3
ms.sourcegitcommit: 56ac30a336668124cb7d95d8ace16bd985875147
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/09/2019
ms.locfileid: "65469531"
---
# <a name="tracing-and-instrumenting-applications"></a>Śledzenie i instrumentacja aplikacji
Śledzenie jest sposobem monitorowania wykonywanie aplikacji, gdy jest on uruchomiony. Możesz dodać Instrumentacji śledzenia i debugowania aplikacji .NET Framework, Opracuj go, gdy zarówno podczas opracowywania aplikacji, jak i po jej wdrożeniu, można użyć tego instrumentacji. Możesz użyć <xref:System.Diagnostics.Trace?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug?displayProperty=nameWithType>, i <xref:System.Diagnostics.TraceSource?displayProperty=nameWithType> klasy do rejestrowania informacji o błędach oraz wykonywania aplikacji w dzienniki, pliki tekstowe lub innych urządzeń do późniejszej analizy.  
  
 Termin *Instrumentacji* odwołuje się do możliwości monitorowania lub mierzyć poziom wydajności produktu i diagnozowanie błędów. W programowaniu, oznacza to, możliwości aplikacji, aby dołączyć:  
  
- **Śledzenie kodu** -odbiera komunikaty informacyjne dotyczące wykonywania aplikacji w czasie wykonywania.  
  
- **Debugowanie** — śledzenie i naprawia błędy programowania aplikacji w fazie projektowania. Aby uzyskać więcej informacji, zobacz [debugowanie](/visualstudio/debugger/debugging-in-visual-studio).  
  
- **Liczniki wydajności** — składniki, które pozwalają śledzić wydajność aplikacji. Aby uzyskać więcej informacji, zobacz [liczniki wydajności](../../../docs/framework/debug-trace-profile/performance-counters.md).  
  
- **Dzienniki zdarzeń** — składniki, które pozwalają otrzymujesz i śledzisz istotnych zdarzeń podczas wykonywania aplikacji. Aby uzyskać więcej informacji, zobacz <xref:System.Diagnostics.EventLog> klasy.  
  
 Instrumentacji aplikacji, umieszczając instrukcji śledzenia w lokalizacjach strategicznych w kodzie jest szczególnie przydatne w przypadku aplikacji rozproszonych. Za pomocą instrukcji śledzenia możliwe jest instrumentowanie aplikacji nie tylko do wyświetlania informacji w przypadku, gdy coś pójdzie źle, ale także do monitorowania, jak działa aplikacja.  
  
 <xref:System.Diagnostics.TraceSource> Klasa udostępnia rozszerzone funkcje śledzenia i mogą być używane zamiast metod statycznych starszej wersji <xref:System.Diagnostics.Trace> i <xref:System.Diagnostics.Debug> klasy śledzenia. Znanej <xref:System.Diagnostics.Trace> i <xref:System.Diagnostics.Debug> są nadal powszechnie używane klasy, ale <xref:System.Diagnostics.TraceSource> klasy jest zalecane w przypadku nowych poleceń śledzenia, takie jak <xref:System.Diagnostics.TraceSource.TraceEvent%2A> i <xref:System.Diagnostics.TraceSource.TraceData%2A>.  
  
 <xref:System.Diagnostics.Trace> i <xref:System.Diagnostics.Debug> klasy są identyczne, z wyjątkiem sytuacji, w tym procedury składowane i funkcje z <xref:System.Diagnostics.Trace> klasy są kompilowane domyślnie do kompilacji wydania, ale w przypadku <xref:System.Diagnostics.Debug> klasy nie są.  
  
 <xref:System.Diagnostics.Trace> i <xref:System.Diagnostics.Debug> klasy zapewniają oznacza, że monitorowanie i badanie wydajności aplikacji podczas tworzenia lub po wdrożeniu. Na przykład, można użyć <xref:System.Diagnostics.Trace> klasy do śledzenia określonych rodzajów działań we wdrożonej aplikacji występują (np. tworzenia nowych połączeń z bazą danych) i w związku z tym można monitorować wydajność aplikacji.  
  
## <a name="code-tracing-and-debugging"></a>Śledzenie kodu i debugowania  
 Podczas tworzenia aplikacji, można użyć metod wyjścia metod klasy <xref:System.Diagnostics.Debug> klasy, aby wyświetlić komunikaty w oknie danych wyjściowych programu Visual Studio zintegrowane środowisko programistyczne (IDE). Na przykład:  
  
```vb  
Trace.WriteLine("Hello World!")  
Debug.WriteLine("Hello World!")  
```  
  
```csharp  
System.Diagnostics.Trace.WriteLine("Hello World!");  
System.Diagnostics.Debug.WriteLine("Hello World!");  
```  
  
 Każda z tych przykładów wyświetli "Hello World!" w oknie dane wyjściowe, gdy aplikacja jest uruchomiona w debugerze.  
  
 Dzięki temu można debugować aplikacje i optymalizowania wydajności na podstawie ich zachowania w środowisku testowym. Można debugować aplikację w kompilacji debugowania za pomocą <xref:System.Diagnostics.Debug> atrybut conditional włączona, aby otrzymywać wszystkie dane wyjściowe debugowania. Gdy aplikacja jest gotowa do wydania, można kompilować kompilacji wersji bez włączania <xref:System.Diagnostics.Debug> warunkowe atrybutu, aby kompilator nie będzie zawierać debugowania kodu w końcowego pliku wykonywalnego. Aby uzyskać więcej informacji, zobacz [jak: Kompilowanie warunkowe ze śledzeniem i debugowaniem](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md). Aby uzyskać więcej informacji na temat innych konfiguracji kompilacji dla aplikacji, zobacz [kompilowanie i tworzenie](/visualstudio/ide/compiling-and-building-in-visual-studio).  
  
 Można także śledzić wykonywanie kodu w zainstalowanej aplikacji przy użyciu metod <xref:System.Diagnostics.Trace> klasy. Umieszczając [przełączniki śledzenia](../../../docs/framework/debug-trace-profile/trace-switches.md) w kodzie, kontrolowania tego, czy występuje śledzenia i jest jak bardzo rozbudowane. Dzięki temu można monitorować stan aplikacji w środowisku produkcyjnym. Jest to szczególnie ważne w aplikacji biznesowej, która korzysta z wielu składników, działające na wielu komputerach. Można kontrolować, jak przełączniki są używane po wdrożeniu za pomocą pliku konfiguracji. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie, inicjowanie i konfigurowanie przełączników śledzenia](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md).  
  
 Opracowując aplikację, dla którego mają być używane do śledzenia, należy zazwyczaj obejmują zarówno śledzenie i debugowanie wiadomości w kodzie aplikacji. Gdy wszystko jest gotowe do wdrożenia aplikacji, można kompilować kompilacji wersji bez włączania **debugowania** atrybut conditional. Jednakże, możesz włączyć **śledzenia** warunkowe atrybutu, aby kompilator zawiera kod śledzenia w pliku wykonywalnym. Aby uzyskać więcej informacji, zobacz [jak: Kompilowanie warunkowe ze śledzeniem i debugowaniem](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md).  
  
### <a name="phases-of-code-tracing"></a>Fazy kod śledzenia  
 Dostępne są trzy etapy śledzenia kodu:  
  
1. **Instrumentacja** — możesz dodać kod śledzenia do aplikacji.  
  
2. **Śledzenie** — kod śledzenia zapisuje informacje w określonym obiekcie docelowym.  
  
3. **Analiza** — ocena informacje śledzenia do identyfikowania i lepsze poznanie problemów w aplikacji.  
  
 Podczas tworzenia aplikacji wszystkie debugowania i śledzenia danych wyjściowych metody zapisywać informacje w oknie danych wyjściowych w programie Visual Studio domyślnie. We wdrożonej aplikacji metody zapisać informacje śledzenia do obiektów docelowych, które określisz. Aby uzyskać więcej informacji na temat określania celu dane wyjściowe śledzenia i debugowania, zobacz [detektorów śledzenia](../../../docs/framework/debug-trace-profile/trace-listeners.md).  
  
 Poniżej przedstawiono ogólny widok główne etapy zazwyczaj przy użyciu śledzenia do analizowania i rozwiązać potencjalne problemy we wdrożonej aplikacji. Aby uzyskać więcej informacji na temat sposobu wykonywania tych kroków, zobacz odpowiednie łącze.  
  
##### <a name="to-use-tracing-in-an-application"></a>Aby użyć śledzenia w aplikacji  
  
1. Należy wziąć pod uwagę, które śledzenia danych wyjściowych, że chcesz otrzymywać u klienta po wdrożeniu aplikacji.  
  
2. Utwórz zestaw parametrów. Aby uzyskać więcej informacji, zobacz [jak: Konfigurowanie przełączników śledzenia](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md).  
  
3. Dodawanie instrukcji śledzenia do kodu aplikacji.  
  
4. Określ, gdzie dane wyjściowe śledzenia są wyświetlane, a następnie dodać odpowiednie odbiorników. Aby uzyskać więcej informacji, zobacz [tworzenie i Inicjowanie obiektów nasłuchujących śledzenia](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-listeners.md).  
  
5. Testowanie i debugowanie aplikacji i kod śledzenia, które zawiera.  
  
6. Kompilowanie aplikacji na kod wykonywalny przy użyciu jednej z następujących procedur:  
  
    - Użyj **kompilacji** menu wraz z **debugowania** strony **stron właściwości** okno dialogowe w **Eksploratora rozwiązań**. Użyj tego ustawienia podczas kompilowania w programie Visual Studio.  
  
         \- lub —  
  
    - Użyj **śledzenia** i **debugowania** dyrektywy kompilatora wiersza polecenia metody kompilowania. Aby uzyskać więcej informacji, zobacz [kompilowanie warunkowe ze śledzeniem i debugowaniem](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md). Użyj tego ustawienia podczas kompilowania z wiersza polecenia.  
  
7. Jeśli wystąpi problem w czasie wykonywania, włącz przełącznik odpowiednie śledzenia. Aby uzyskać więcej informacji, zobacz [Konfigurowanie przełączników śledzenia](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md).  
  
     Kod śledzenia zapisuje komunikaty dotyczące śledzenia w określonym miejscu docelowym, na przykład, ekran, plik tekstowy lub dziennik zdarzeń. Typ odbiornika zostało uwzględnione w **Trace.Listeners** Określa, kolekcji docelowej.  
  
8. Analizowanie komunikatów śledzenia do identyfikowania i zrozumienia problemu w aplikacji.  
  
## <a name="trace-instrumentation-and-distributed-applications"></a>Instrumentacji Śledź i aplikacji rozproszonych  
 Podczas tworzenia aplikacji rozproszonej może być trudno testowanie aplikacji w taki sposób, w którym będzie on używany. Kilka zespołów programistycznych wykorzystuje funkcję, aby przetestować wszystkie możliwe kombinacje systemów operacyjnych lub przeglądarek sieci Web (w tym wszystkie opcje zlokalizowane) lub do symulacji dużą liczbę użytkowników, którzy będą uzyskiwać dostęp do aplikacji, w tym samym czasie. W tych okolicznościach nie można przetestować, jak aplikacja rozproszona odpowie na dużej ilości danych, różne konfiguracje i zachowania unikatowy użytkownika końcowego. Ponadto wiele części aplikacji rozproszonej jest bez interfejsu użytkownika można wchodzić w interakcje bezpośrednio lub Wyświetl działania tych części.  
  
 Jednak można zniwelować to przez włączenie aplikacji rozproszonych do opisania określonych zdarzeń przydatne dla administratorów systemu, zwłaszcza te rzeczy, które pójdzie nie tak, przez *Instrumentacji* aplikacji — czyli przez umieszczenie instrukcji śledzenia w lokalizacjach strategicznych w kodzie. Następnie, jeśli coś nieoczekiwanego występuje w czasie wykonywania (na przykład zbyt długi czas odpowiedzi), można określić prawdopodobną przyczyną.  
  
 Za pomocą instrukcji śledzenia można uniknąć trudne badanie oryginalnego kodu źródłowego, modyfikowanie, ponownej kompilacji i podjęto próbę utworzenia błędów czasu wykonywania w środowisku debugowania. Należy pamiętać, że możliwe jest instrumentowanie aplikacji nie tylko do wyświetlania błędów, ale także do monitorowania wydajności.  
  
## <a name="strategic-placement-of-trace-statements"></a>Strategiczne rozmieszczenie instrukcji śledzenia  
 Szczególną muszą wykonywać, w przypadku umieszczenia Twojego instrukcji śledzenia do użycia w czasie wykonywania. Należy rozważyć informacjach śledzenia jest potrzebne byłyby we wdrożonej aplikacji, aby odpowiednio znajdują się wszystkie scenariusze prawdopodobnie śledzenia. Aplikacje, które używają śledzenia się nieznacznie różnić szeroko, jednak istnieją nie ogólne wskazówki dotyczące strategiczne rozmieszczenie śledzenia. Aby uzyskać więcej informacji na temat wprowadzania do instrukcji śledzenia, zobacz [jak: Dodawanie instrukcji śledzenia do kodu aplikacji](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md).  
  
## <a name="output-from-tracing"></a>Dane wyjściowe śledzenia  
 Dane wyjściowe śledzenia są zbierane przez obiekty o nazwie *odbiorników*. Odbiornik jest obiektem, który odbiera dane wyjściowe śledzenia i zapisuje go na urządzeniach (zwykle plik okna, dziennika lub tekst). Po utworzeniu odbiornika śledzenia, zwykle jest ona dodawana do <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> kolekcji, dzięki czemu odbiornika do odbierania wszystkich danych wyjściowych śledzenia.  
  
 Informacje śledzenia są zawsze zapisywane co najmniej wartość domyślna <xref:System.Diagnostics.Trace> celem danych wyjściowych <xref:System.Diagnostics.DefaultTraceListener>. Jeśli z jakiegoś powodu została usunięta <xref:System.Diagnostics.DefaultTraceListener> bez dodawania innych nasłuchujących, aby <xref:System.Diagnostics.Trace.Listeners%2A> kolekcji, nie otrzymasz żadnych komunikatów śledzenia. Aby uzyskać więcej informacji, zobacz [detektorów śledzenia](../../../docs/framework/debug-trace-profile/trace-listeners.md).  
  
 Sześciu <xref:System.Diagnostics.Debug> elementów członkowskich i <xref:System.Diagnostics.Trace> metody, które zapisują informacje śledzenia są wymienione w poniższej tabeli.  
  
|Metoda|Dane wyjściowe|  
|------------|------------|  
|**Assert**|Określony tekst. lub, jeśli nie określono wywołanie stosu. Dane wyjściowe są zapisywane tylko jeśli warunek określony jako argument w **Asercja** instrukcja jest **false**.|  
|**Niepowodzenie**|Określony tekst. lub, jeśli nie określono wywołanie stosu.|  
|**Zapis**|Określony tekst.|  
|**Writeif —**|Określony tekst, jeśli warunek określony jako argument w **writeif —** instrukcji jest spełniony.|  
|**WriteLine**|Określony tekst i znaku powrotu karetki.|  
|**WriteLineIf**|Określony tekst i karetki zwracają, jeśli warunek określony jako argument w **WriteLineIf** instrukcji jest spełniony.|  
  
 Wszystkie słuchaczy w <xref:System.Diagnostics.Trace.Listeners%2A> kolekcji odbierać komunikaty, opisano w powyższej tabeli, ale akcje wykonywane mogą się różnić w zależności od tego, jakiego rodzaju odbiornika odbiera komunikat. Na przykład <xref:System.Diagnostics.DefaultTraceListener> Wyświetla okno dialogowe potwierdzenia, po odebraniu **się nie powieść** lub nie powiodło się **Asercja** powiadomienia, ale <xref:System.Diagnostics.TextWriterTraceListener> po prostu zapisuje dane wyjściowe do strumienia jej.  
  
 Aby wygenerować wyniki niestandardowych, należy Implementowanie własnych odbiornika. Odbiornik śledzenia niestandardowe mogą, na przykład wyświetlanie wiadomości do okna komunikatu lub połączenie z bazą danych do dodawania komunikatów do tabeli. Wszystkie niestandardowe odbiorniki powinien obsługiwać sześciu metod wymienionych powyżej. Aby uzyskać więcej informacji na temat tworzenia odbiorników zdefiniowane dla deweloperów, zobacz <xref:System.Diagnostics.TraceListener> w dokumentacji .NET Framework.  
  
> [!NOTE]
>  W języku Visual Basic **Debug.Write —**, **Debug.WriteIf**, **Debug.WriteLine**, i **Debug.WriteLineIf** zastąpiono metody **Debug.Print** metody, które były dostępne we wcześniejszych wersjach programu Visual Basic.  
  
 **Zapisu** i **WriteLine** metody zawsze wpisać tekst należy określić. **Asercja**, **writeif —**, i **WriteLineIf** wymagają argument logiczny, który kontroluje, czy zapisują określony tekst; zapisują określony tekst tylko jeśli wyrażenie ma **true** (dla **writeif —** i **WriteLineIf**), lub **false** (dla **Asercja**). **Się nie powieść** metody są zawsze zapisywane określony tekst. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie instrukcji śledzenia do kodu aplikacji](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md) i odwołania programu .NET Framework.  
  
## <a name="security-concerns"></a>Zagadnienia dotyczące zabezpieczeń  
 Jeśli nie można wyłączyć śledzenie i debugowanie przed wdrożeniem aplikacji ASP.NET, aplikacja może ujawnić informacje o sobie, które mogą zostać wykorzystane przez złośliwych programów. Aby uzyskać więcej informacji, zobacz [jak: Kompiluj warunkowe ze śledzeniem i debugowaniem](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md), [kompilowanie i tworzenie](/visualstudio/ide/compiling-and-building-in-visual-studio), i [jak: Tworzenie, inicjowanie i konfigurowanie przełączników śledzenia](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md). Debugowanie jest także można skonfigurować za pomocą programu Internet Information Services (IIS).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceSource>
- [Kontrakty kodu](../../../docs/framework/debug-trace-profile/code-contracts.md)
- [Typy projektów C#, F# i Visual Basic](/visualstudio/debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types)
- [Instrukcje: Dodawanie instrukcji śledzenia do kodu aplikacji](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)
- [Instrukcje: Kompilowanie warunkowe ze śledzeniem i debugowaniem](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
- [Instrukcje: Tworzenie, inicjowanie i konfigurowanie przełączników śledzenia](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)
- [Instrukcje: Tworzenie i Inicjowanie źródeł śledzenia](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md)
- [Instrukcje: Użycie TraceSource i filtrów z obiektów nasłuchujących śledzenia](../../../docs/framework/debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md)
- [Obiekty nasłuchujące śledzenie](../../../docs/framework/debug-trace-profile/trace-listeners.md)
- [Przełączniki śledzenia](../../../docs/framework/debug-trace-profile/trace-switches.md)
