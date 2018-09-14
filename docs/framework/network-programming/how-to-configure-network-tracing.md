---
title: 'Porady: Konfigurowanie śledzenia sieci'
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 3c9550bf9d3483a8d2961e6137138bfb11f71bca
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45527593"
---
# <a name="how-to-configure-network-tracing"></a>Porady: Konfigurowanie śledzenia sieci
Plik konfiguracyjny aplikacji lub komputera zawiera ustawienia, które określają format i zawartość danych ze śledzenia sieci. Przed rozpoczęciem procedury należy się upewnić, że śledzenie jest włączone. Aby uzyskać informacje na temat włączania śledzenia, zobacz [Enabling Network Tracing](../../../docs/framework/network-programming/enabling-network-tracing.md).  
  
 Plik konfiguracji komputera — machine.config — znajduje się w folderze %Windir%\Microsoft.NET\Framework w katalogu, w którym zainstalowano system Windows. Istnieje osobny plik machine.config w folderach w ramach %Windir%\Microsoft.NET\Framework dla każdej wersji programu .NET Framework zainstalowanej na komputerze (na przykład C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config lub C:\Windows\ Microsoft.NET\Framework64\v4.0.30319\Config\machine.config.).  
  
 Ustawienia te można również wprowadzić w pliku konfiguracyjnym aplikacji. Ma on priorytet nad plikiem konfiguracyjnym komputera.  
  
### <a name="to-configure-network-tracing"></a>Aby skonfigurować funkcję śledzenia sieci  
  
-   Dodaj następujące wiersze do odpowiedniego pliku konfiguracyjnego. Wartości i opcje ustawień opisano w tabelach poniżej.  
  
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
          />  
        </sharedListeners>  
        <trace autoflush="true"/>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
 Po dodaniu nazwy do `<switches>` bloku, dane wyjściowe śledzenia zawierały informacje z niektórych metod związanych z nazwą. W tabeli poniżej opisano dane wyjściowe.  
  
|Nazwa|Skąd dane wyjściowe|  
|----------|-----------------|  
|`System.Net.Sockets`|Niektóre metody publiczne <xref:System.Net.Sockets.Socket>, <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient>, i <xref:System.Net.Dns> klas|  
|`System.Net`|Niektóre metody publiczne <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>, i <xref:System.Net.FtpWebResponse> klasy i protokołu SSL, debugowanie informacji (nieważne certyfikaty, brakujące listy wystawców i błędy certyfikatów klientów.)|  
|`System.Net.HttpListener`|Niektóre metody publiczne <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest>, i <xref:System.Net.HttpListenerResponse> klasy.|  
|`System.Net.Cache`|Niektóre metody prywatne i wewnętrzne w `System.Net.Cache`.|  
|`System.Net.Http`|Niektóre metody publiczne <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.DelegatingHandler>, <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>, <xref:System.Net.Http.MessageProcessingHandler>, i <xref:System.Net.Http.WebRequestHandler> klasy.|  
|`System.Net.WebSockets.WebSocket`|Niektóre metody publiczne <xref:System.Net.WebSockets.ClientWebSocket> i <xref:System.Net.WebSockets.WebSocket> klasy.|  
  
 W tabeli poniżej wymieniono atrybuty konfiguracyjne danych wyjściowych śledzenia.  
  
|Nazwa atrybutu|Wartość atrybutu|  
|--------------------|---------------------|  
|`Value`|Wymagane <xref:System.String> atrybutu. Ustawia poziom szczegółowości danych wyjściowych. Dozwolone wartości to `Critical`, `Error`, `Verbose`, `Warning`, i `Information`.<br /><br /> Ten atrybut musi być ustawiony na \<Dodaj nazwę > element \<przełączników > elementu, jak pokazano w przykładzie. Wyjątek jest generowany, jeśli ten atrybut jest ustawiony na \<źródło > element.|  
|`maxdatasize`|Opcjonalnie <xref:System.Int32> atrybutu. Ustawia maksymalną liczbę bajtów danych sieciowych w każdym zapisie ze śledzenia linii. Wartość domyślna to 1024.<br /><br /> Ten atrybut musi być ustawiony na \<źródło > elementu, jak pokazano w przykładzie. Wyjątek jest generowany, jeśli ten atrybut jest ustawiony na elemencie należącym do elementu \<przełączników > element.|  
|`Tracemode`|Opcjonalnie <xref:System.String> atrybutu. Ustaw `includehex` Aby wyświetlić ślady protokołu w formacie szesnastkowym i tekstowym. Ustaw `protocolonly` wyświetlanie tylko tekstu. Wartość domyślna to `includehex`.<br /><br /> Ten atrybut musi być ustawiony na \<przełączników > elementu, jak pokazano w przykładzie. Wyjątek jest generowany, jeśli ten atrybut jest ustawiony na elemencie należącym do elementu \<źródło > element.|  
  
## <a name="see-also"></a>Zobacz też  
 [Interpretowanie śledzenia sieci](../../../docs/framework/network-programming/interpreting-network-tracing.md)  
 [Śledzenie sieci w programie .NET Framework](../../../docs/framework/network-programming/network-tracing.md)  
 [Włączanie śledzenia sieci](../../../docs/framework/network-programming/enabling-network-tracing.md)  
 [Wprowadzenie do Instrumentacji i śledzenia](https://msdn.microsoft.com/library/e924e57c-33cf-4b0e-9e7f-a45d13e38f2c)
