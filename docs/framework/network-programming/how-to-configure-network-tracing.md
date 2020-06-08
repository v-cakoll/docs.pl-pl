---
title: 'Instrukcje: konfigurowanie śledzenia sieci'
description: Dowiedz się, jak skonfigurować śledzenie sieci w pliku konfiguracji komputera lub pliku konfiguracyjnym aplikacji. Ma pierwszeństwo plik konfiguracyjny aplikacji.
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
ms.openlocfilehash: b089746e9838c591ed5ccc9ac9aaeedb217de9a9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502564"
---
# <a name="how-to-configure-network-tracing"></a>Instrukcje: Konfigurowanie śledzenia sieci

Plik konfiguracyjny aplikacji lub komputera zawiera ustawienia, które określają format i zawartość danych ze śledzenia sieci. Przed rozpoczęciem procedury należy się upewnić, że śledzenie jest włączone. Aby uzyskać więcej informacji, zobacz [Włączanie śledzenia sieci](enabling-network-tracing.md).

Plik konfiguracji komputera, *Machine. config*, jest przechowywany w folderze *%windir%\Microsoft.NET\Framework* . W folderach w obszarze *%windir%\Microsoft.NET\Framework* istnieje osobny plik *Machine. config* dla każdej wersji .NET Framework zainstalowanej na komputerze, na przykład:

- *C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\Config\machine.config*
- *C:\WINDOWS\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config*

Ustawienia te można również wprowadzić w pliku konfiguracyjnym aplikacji. Ma on priorytet nad plikiem konfiguracyjnym komputera.

## <a name="configure-network-tracing"></a>Konfigurowanie śledzenia sieci

Aby skonfigurować śledzenie sieci, Dodaj następujące wiersze do odpowiedniego pliku konfiguracji. Wartości i opcje ustawień opisano w tabelach poniżej.

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

Po dodaniu nazwy do `<switches>` bloku dane wyjściowe śledzenia zawierają informacje z niektórych metod związanych z nazwą. W poniższej tabeli opisano dane wyjściowe:

|Nazwa|Skąd dane wyjściowe|
|----------|-----------------|
|`System.Net.Sockets`|Niektóre metody publiczne <xref:System.Net.Sockets.Socket> <xref:System.Net.Sockets.TcpListener> klasy,, <xref:System.Net.Sockets.TcpClient> , i <xref:System.Net.Dns> .|
|`System.Net`|Niektóre publiczne metody <xref:System.Net.HttpWebRequest> , <xref:System.Net.HttpWebResponse> , <xref:System.Net.FtpWebRequest> , i <xref:System.Net.FtpWebResponse> informacje debugowania protokołu SSL (Nieprawidłowe certyfikaty, Lista brakujących wystawców i błędy certyfikatów klienta).|
|`System.Net.HttpListener`|Niektóre publiczne metody <xref:System.Net.HttpListener> <xref:System.Net.HttpListenerRequest> klasy,, i <xref:System.Net.HttpListenerResponse> .|
|`System.Net.Cache`|Niektóre metody prywatne i wewnętrzne w `System.Net.Cache` .|
|`System.Net.Http`|Niektóre publiczne metody <xref:System.Net.Http.HttpClient> klasy,,,, <xref:System.Net.Http.DelegatingHandler> <xref:System.Net.Http.HttpClientHandler> <xref:System.Net.Http.HttpMessageHandler> <xref:System.Net.Http.MessageProcessingHandler> i <xref:System.Net.Http.WebRequestHandler> .|
|`System.Net.WebSockets.WebSocket`|Niektóre metody publiczne <xref:System.Net.WebSockets.ClientWebSocket> <xref:System.Net.WebSockets.WebSocket> klas i.|

### <a name="trace-output-attributes"></a>Atrybuty wyjściowe śledzenia

Atrybuty wymienione w poniższej tabeli konfigurują dane wyjściowe śledzenia:

|Nazwa atrybutu|Wartość atrybutu|
|--------------------|---------------------|
|`value`|Wymagany <xref:System.String> atrybut. Ustawia poziom szczegółowości danych wyjściowych. Wiarygodne wartości to `Critical` , `Error` , `Verbose` , `Warning` i `Information` .<br /><br />Ten atrybut musi być ustawiony w elemencie **Add** elementu **switchs** . Wyjątek jest generowany, jeśli ten atrybut jest ustawiony dla elementu **źródłowego** .<br/><br/>Przykład: `<add name="System.Net" value="Verbose"/>`|
|`maxdatasize`|Opcjonalny <xref:System.Int32> atrybut. Ustawia maksymalną liczbę bajtów danych sieciowych w każdym zapisie ze śledzenia linii. Wartość domyślna to 1024.<br /><br />Ten atrybut musi być ustawiony dla elementu **Source** . Wyjątek jest generowany, jeśli ten atrybut jest ustawiony dla elementu w elemencie **switchs** .<br/><br/>Przykład: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`|
|`tracemode`|Opcjonalny <xref:System.String> atrybut. Ustaw, aby `includehex` wyświetlać ślady protokołu w formacie szesnastkowym i tekstowym. Ustaw, aby `protocolonly` pokazywać tylko tekst. Wartość domyślna to `includehex`.<br /><br />Ten atrybut musi być ustawiony dla elementu **Source** . Wyjątek jest generowany, jeśli ten atrybut jest ustawiony dla elementu w elemencie **switchs** .<br/><br/>Przykład: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`|

## <a name="see-also"></a>Zobacz także

- [Interpretowanie śledzenia sieci](interpreting-network-tracing.md)
- [Śledzenie sieci w .NET Framework](network-tracing.md)
- [Włączanie śledzenia sieci](enabling-network-tracing.md)
- [Śledzenie i instrumentacja aplikacji](../debug-trace-profile/tracing-and-instrumenting-applications.md)
