---
title: 'Instrukcje: konfigurowanie funkcji śledzenia sieci'
ms.date: 03/30/2017
helpviewer_keywords:
- formatting [.NET Framework], network tracing
- network tracing, configuring
- level attribute
- app.config files, network tracing
- configuration files [.NET Framework], network tracing
- protocol-level trace output
- application configuration files, network tracing
- sockets, trace output
ms.assetid: 5ef9fe4b-8d3d-490e-9259-1d014b2181af
ms.openlocfilehash: dc9b6b5399063026c0bbe5735964ed42a21168fa
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048369"
---
# <a name="how-to-configure-network-tracing"></a>Instrukcje: konfigurowanie funkcji śledzenia sieci
Plik konfiguracyjny aplikacji lub komputera zawiera ustawienia, które określają format i zawartość danych ze śledzenia sieci. Przed rozpoczęciem procedury należy się upewnić, że śledzenie jest włączone. Aby uzyskać informacje na temat włączania śledzenia, zobacz [Włączanie śledzenia sieci](enabling-network-tracing.md).  
  
 Plik konfiguracji komputera — machine.config — znajduje się w folderze %Windir%\Microsoft.NET\Framework w katalogu, w którym zainstalowano system Windows. W folderach w obszarze%Windir%\Microsoft.NET\Framework istnieje osobny plik Machine. config dla każdej wersji .NET Framework zainstalowanej na komputerze (na przykład C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config lub C:\Windows\ Microsoft. NET\Framework64\v4.0.30319\Config\machine.config.).  
  
 Ustawienia te można również wprowadzić w pliku konfiguracyjnym aplikacji. Ma on priorytet nad plikiem konfiguracyjnym komputera.  
  
### <a name="to-configure-network-tracing"></a>Aby skonfigurować funkcję śledzenia sieci  
  
- Dodaj następujące wiersze do odpowiedniego pliku konfiguracyjnego. Wartości i opcje ustawień opisano w tabelach poniżej.  
  
    ```xml  
    <configuration>  
      <system.diagnostics>  
        <sources>  
          <source name="System.Net" tracemode="includehex" maxdatasize="1024">  
            <listeners>  
              <add name="System.Net"/>  
            </listeners>  
          </source>  
          <source name="System.Net.Cache">  
            <listeners>  
              <add name="System.Net"/>  
            </listeners>  
          </source>  
          <source name="System.Net.Http">  
            <listeners>  
              <add name="System.Net"/>  
            </listeners>  
          </source>  
          <source name="System.Net.Sockets">  
            <listeners>  
              <add name="System.Net"/>  
            </listeners>  
          </source>  
          <source name="System.Net.WebSockets">  
            <listeners>  
              <add name="System.Net"/>  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="System.Net" value="Verbose"/>  
          <add name="System.Net.Cache" value="Verbose"/>  
          <add name="System.Net.Http" value="Verbose"/>  
          <add name="System.Net.Sockets" value="Verbose"/>  
          <add name="System.Net.WebSockets" value="Verbose"/>  
        </switches>  
        <sharedListeners>  
          <add name="System.Net"  
            type="System.Diagnostics.TextWriterTraceListener"  
            initializeData="network.log"
            traceOutputOptions="ProcessId, DateTime" 
          />  
        </sharedListeners>  
        <trace autoflush="true"/>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
 Po dodaniu nazwy do `<switches>` bloku dane wyjściowe śledzenia zawierają informacje z niektórych metod związanych z nazwą. W tabeli poniżej opisano dane wyjściowe.  
  
|Nazwa|Skąd dane wyjściowe|  
|----------|-----------------|  
|`System.Net.Sockets`|Niektóre metody <xref:System.Net.Sockets.Socket>publiczne klasy, <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient>, i <xref:System.Net.Dns>|  
|`System.Net`|Niektóre publiczne metody <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>, i <xref:System.Net.FtpWebResponse> informacje debugowania protokołu SSL (Nieprawidłowe certyfikaty, Lista brakujących wystawców i błędy certyfikatów klienta).|  
|`System.Net.HttpListener`|Niektóre publiczne metody <xref:System.Net.HttpListener>klasy, <xref:System.Net.HttpListenerRequest>, i <xref:System.Net.HttpListenerResponse> .|  
|`System.Net.Cache`|Niektóre metody prywatne i wewnętrzne w `System.Net.Cache`.|  
|`System.Net.Http`|Niektóre <xref:System.Net.Http.HttpClient>publiczne metody klasy, <xref:System.Net.Http.DelegatingHandler>, <xref:System.Net.Http.HttpClientHandler> <xref:System.Net.Http.HttpMessageHandler>,, i<xref:System.Net.Http.WebRequestHandler> . <xref:System.Net.Http.MessageProcessingHandler>|  
|`System.Net.WebSockets.WebSocket`|Niektóre metody <xref:System.Net.WebSockets.ClientWebSocket> publiczne klas i <xref:System.Net.WebSockets.WebSocket> .|  
  
 W tabeli poniżej wymieniono atrybuty konfiguracyjne danych wyjściowych śledzenia.  
  
|Nazwa atrybutu|Wartość atrybutu|  
|--------------------|---------------------|  
|`Value`|Wymagany <xref:System.String> atrybut. Ustawia poziom szczegółowości danych wyjściowych. Wiarygodne wartości to `Critical`, `Error`, `Verbose` ,`Warning`i .`Information`<br /><br /> Ten atrybut musi być ustawiony w \<elemencie \<Dodaj nazwę > elementu > przełączników, jak pokazano w przykładzie. Wyjątek jest generowany, \<Jeśli ten atrybut jest ustawiony w źródłowym elemencie >.|  
|`maxdatasize`|Opcjonalny <xref:System.Int32> atrybut. Ustawia maksymalną liczbę bajtów danych sieciowych w każdym zapisie ze śledzenia linii. Wartość domyślna to 1024.<br /><br /> Ten atrybut musi być ustawiony dla \<elementu źródłowego >, jak pokazano w przykładzie. Wyjątek jest generowany, jeśli ten atrybut jest ustawiony dla elementu w obszarze \<przełączniki > elementu.|  
|`Tracemode`|Opcjonalny <xref:System.String> atrybut. Ustaw, `includehex` aby wyświetlać ślady protokołu w formacie szesnastkowym i tekstowym. Ustaw, `protocolonly` aby pokazywać tylko tekst. Wartość domyślna to `includehex`.<br /><br /> Ten atrybut musi być ustawiony dla \<przełączników > elementu, jak pokazano w przykładzie. Wyjątek jest zgłaszany, jeśli ten atrybut jest ustawiony dla elementu pod \<elementem źródłowym >.|  
  
## <a name="see-also"></a>Zobacz także

- [Interpretowanie śledzenia sieci](interpreting-network-tracing.md)
- [Śledzenie sieci w programie .NET Framework](network-tracing.md)
- [Włączanie śledzenia sieci](enabling-network-tracing.md)
- [Śledzenie i instrumentacja aplikacji](../debug-trace-profile/tracing-and-instrumenting-applications.md)
