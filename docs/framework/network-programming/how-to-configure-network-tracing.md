---
title: 'Instrukcje: konfigurowanie śledzenia sieci'
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
ms.openlocfilehash: 06132509860b16d1e22cfdf7e3226c968d16b7cf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73040643"
---
# <a name="how-to-configure-network-tracing"></a>Jak: Konfigurowanie śledzenia sieci

Plik konfiguracyjny aplikacji lub komputera zawiera ustawienia, które określają format i zawartość danych ze śledzenia sieci. Przed rozpoczęciem procedury należy się upewnić, że śledzenie jest włączone. Aby uzyskać więcej informacji, zobacz [Włączanie śledzenia sieci](enabling-network-tracing.md).

Plik konfiguracyjny komputera, *machine.config,* jest przechowywany w folderze *%windir%\Microsoft.NET\Framework.* W folderach w obszarze *%windir%\Microsoft.NET\Framework* znajduje się oddzielny plik *machine.config* dla każdej wersji programu .NET Framework zainstalowanej na komputerze, na przykład:

- *C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\Config\machine.config*
- *C:\WINDOWS\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config*

Ustawienia te można również wprowadzić w pliku konfiguracyjnym aplikacji. Ma on priorytet nad plikiem konfiguracyjnym komputera.

## <a name="configure-network-tracing"></a>Konfigurowanie śledzenia sieci

Aby skonfigurować śledzenie sieci, dodaj następujące wiersze do odpowiedniego pliku konfiguracyjnego. Wartości i opcje ustawień opisano w tabelach poniżej.

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

### <a name="trace-output-from-methods"></a>Śledzenie danych wyjściowych z metod

Po dodaniu nazwy `<switches>` do bloku dane wyjściowe śledzenia zawiera informacje z niektórych metod związanych z nazwą. W poniższej tabeli opisano dane wyjściowe:

|Nazwa|Skąd dane wyjściowe|
|----------|-----------------|
|`System.Net.Sockets`|Niektóre publiczne metody <xref:System.Net.Sockets.Socket> <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Dns> i klasy.|
|`System.Net`|Niektóre publiczne metody <xref:System.Net.HttpWebRequest> <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.FtpWebResponse> i klas oraz informacje debugowania SSL (nieprawidłowe certyfikaty, lista brakujących wystawców i błędy certyfikatów klienta).|
|`System.Net.HttpListener`|Niektóre publiczne metody <xref:System.Net.HttpListener> <xref:System.Net.HttpListenerRequest>, <xref:System.Net.HttpListenerResponse> i klasy.|
|`System.Net.Cache`|Niektóre metody prywatne `System.Net.Cache`i wewnętrzne w .|
|`System.Net.Http`|Niektóre publiczne metody <xref:System.Net.Http.HttpClient> <xref:System.Net.Http.DelegatingHandler>, <xref:System.Net.Http.HttpClientHandler> <xref:System.Net.Http.HttpMessageHandler>, <xref:System.Net.Http.MessageProcessingHandler>, <xref:System.Net.Http.WebRequestHandler> , i klas.|
|`System.Net.WebSockets.WebSocket`|Niektóre publiczne metody <xref:System.Net.WebSockets.ClientWebSocket> <xref:System.Net.WebSockets.WebSocket> i klasy.|

### <a name="trace-output-attributes"></a>Śledzenie atrybutów danych wyjściowych

Atrybuty wymienione w poniższej tabeli konfigurują dane wyjściowe śledzenia:

|Nazwa atrybutu|Wartość atrybutu|
|--------------------|---------------------|
|`value`|Wymagany <xref:System.String> atrybut. Ustawia poziom szczegółowości danych wyjściowych. Wartości zgodne `Critical` `Error`z `Verbose` `Warning`prawem `Information`to , , , i .<br /><br />Ten atrybut musi być ustawiony na **add** element elementu **przełączniki.** Wyjątek jest zgłaszany, jeśli ten atrybut jest ustawiony na element **źródłowy.**<br/><br/>Przykład: `<add name="System.Net" value="Verbose"/>`|
|`maxdatasize`|Opcjonalny <xref:System.Int32> atrybut. Ustawia maksymalną liczbę bajtów danych sieciowych w każdym zapisie ze śledzenia linii. Wartość domyślna to 1024.<br /><br />Ten atrybut musi być ustawiony na elemencie **źródłowym.** Wyjątek jest zgłaszany, jeśli ten atrybut jest ustawiony na element pod **elementem przełączników.**<br/><br/>Przykład: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`|
|`tracemode`|Opcjonalny <xref:System.String> atrybut. Ustaw, `includehex` aby wyświetlić ślady protokołu w formacie szesnastkowym i tekstowym. Ustaw, `protocolonly` aby wyświetlić tylko tekst. Wartością domyślną jest `includehex`.<br /><br />Ten atrybut musi być ustawiony na elemencie **źródłowym.** Wyjątek jest zgłaszany, jeśli ten atrybut jest ustawiony na element pod **elementem przełączników.**<br/><br/>Przykład: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`|

## <a name="see-also"></a>Zobacz też

- [Interpretowanie śledzenia sieci](interpreting-network-tracing.md)
- [Śledzenie sieci w .NET Framework](network-tracing.md)
- [Włączanie śledzenia sieci](enabling-network-tracing.md)
- [Śledzenie i instrumentacja aplikacji](../debug-trace-profile/tracing-and-instrumenting-applications.md)
