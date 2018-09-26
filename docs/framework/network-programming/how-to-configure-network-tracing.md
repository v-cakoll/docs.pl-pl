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
ms.openlocfilehash: 4b8fa55375de5057eca92591cbf4d9da628a3f85
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47082503"
---
# <a name="how-to-configure-network-tracing"></a><span data-ttu-id="48927-102">Porady: Konfigurowanie śledzenia sieci</span><span class="sxs-lookup"><span data-stu-id="48927-102">How to: Configure Network Tracing</span></span>
<span data-ttu-id="48927-103">Plik konfiguracyjny aplikacji lub komputera zawiera ustawienia, które określają format i zawartość danych ze śledzenia sieci.</span><span class="sxs-lookup"><span data-stu-id="48927-103">The application or computer configuration file holds the settings that determine the format and content of network traces.</span></span> <span data-ttu-id="48927-104">Przed rozpoczęciem procedury należy się upewnić, że śledzenie jest włączone.</span><span class="sxs-lookup"><span data-stu-id="48927-104">Before performing this procedure, be sure tracing is enabled.</span></span> <span data-ttu-id="48927-105">Aby uzyskać informacje na temat włączania śledzenia, zobacz [Enabling Network Tracing](../../../docs/framework/network-programming/enabling-network-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="48927-105">For information about enabling tracing, see [Enabling Network Tracing](../../../docs/framework/network-programming/enabling-network-tracing.md).</span></span>  
  
 <span data-ttu-id="48927-106">Plik konfiguracji komputera — machine.config — znajduje się w folderze %Windir%\Microsoft.NET\Framework w katalogu, w którym zainstalowano system Windows.</span><span class="sxs-lookup"><span data-stu-id="48927-106">The computer configuration file, machine.config, is stored in the %Windir%\Microsoft.NET\Framework folder in the directory where Windows was installed.</span></span> <span data-ttu-id="48927-107">Istnieje osobny plik machine.config w folderach w ramach %Windir%\Microsoft.NET\Framework dla każdej wersji programu .NET Framework zainstalowanej na komputerze (na przykład C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config lub C:\Windows\ Microsoft.NET\Framework64\v4.0.30319\Config\machine.config.).</span><span class="sxs-lookup"><span data-stu-id="48927-107">There is a separate machine.config file in the folders under %Windir%\Microsoft.NET\Framework for each version of the .NET Framework installed on the computer (for example, C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config or C:\Windows\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config.).</span></span>  
  
 <span data-ttu-id="48927-108">Ustawienia te można również wprowadzić w pliku konfiguracyjnym aplikacji. Ma on priorytet nad plikiem konfiguracyjnym komputera.</span><span class="sxs-lookup"><span data-stu-id="48927-108">These settings can also be made in the configuration file for the application, which has precedence over the computer configuration file.</span></span>  
  
### <a name="to-configure-network-tracing"></a><span data-ttu-id="48927-109">Aby skonfigurować funkcję śledzenia sieci</span><span class="sxs-lookup"><span data-stu-id="48927-109">To configure network tracing</span></span>  
  
-   <span data-ttu-id="48927-110">Dodaj następujące wiersze do odpowiedniego pliku konfiguracyjnego.</span><span class="sxs-lookup"><span data-stu-id="48927-110">Add the following lines to the appropriate configuration file.</span></span> <span data-ttu-id="48927-111">Wartości i opcje ustawień opisano w tabelach poniżej.</span><span class="sxs-lookup"><span data-stu-id="48927-111">The values and options for these settings are described in the tables below.</span></span>  
  
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
  
 <span data-ttu-id="48927-112">Po dodaniu nazwy do `<switches>` bloku, dane wyjściowe śledzenia zawierały informacje z niektórych metod związanych z nazwą.</span><span class="sxs-lookup"><span data-stu-id="48927-112">When you add a name to the `<switches>` block, the trace output includes information from some methods related to the name.</span></span> <span data-ttu-id="48927-113">W tabeli poniżej opisano dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="48927-113">The following table describes the output.</span></span>  
  
|<span data-ttu-id="48927-114">Nazwa</span><span class="sxs-lookup"><span data-stu-id="48927-114">Name</span></span>|<span data-ttu-id="48927-115">Skąd dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="48927-115">Output from</span></span>|  
|----------|-----------------|  
|`System.Net.Sockets`|<span data-ttu-id="48927-116">Niektóre metody publiczne <xref:System.Net.Sockets.Socket>, <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient>, i <xref:System.Net.Dns> klas</span><span class="sxs-lookup"><span data-stu-id="48927-116">Some public methods of the <xref:System.Net.Sockets.Socket>, <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient>, and <xref:System.Net.Dns> classes</span></span>|  
|`System.Net`|<span data-ttu-id="48927-117">Niektóre metody publiczne <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>, i <xref:System.Net.FtpWebResponse> klasy i protokołu SSL, debugowanie informacji (nieważne certyfikaty, brakujące listy wystawców i błędy certyfikatów klientów.)</span><span class="sxs-lookup"><span data-stu-id="48927-117">Some public methods of the <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>, and <xref:System.Net.FtpWebResponse> classes, and SSL debug information (invalid certificates, missing issuers list, and client certificate errors.)</span></span>|  
|`System.Net.HttpListener`|<span data-ttu-id="48927-118">Niektóre metody publiczne <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest>, i <xref:System.Net.HttpListenerResponse> klasy.</span><span class="sxs-lookup"><span data-stu-id="48927-118">Some public methods of the <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest>, and <xref:System.Net.HttpListenerResponse> classes.</span></span>|  
|`System.Net.Cache`|<span data-ttu-id="48927-119">Niektóre metody prywatne i wewnętrzne w `System.Net.Cache`.</span><span class="sxs-lookup"><span data-stu-id="48927-119">Some private and internal methods in `System.Net.Cache`.</span></span>|  
|`System.Net.Http`|<span data-ttu-id="48927-120">Niektóre metody publiczne <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.DelegatingHandler>, <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>, <xref:System.Net.Http.MessageProcessingHandler>, i <xref:System.Net.Http.WebRequestHandler> klasy.</span><span class="sxs-lookup"><span data-stu-id="48927-120">Some public methods of the  <xref:System.Net.Http.HttpClient>,  <xref:System.Net.Http.DelegatingHandler>,  <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>,  <xref:System.Net.Http.MessageProcessingHandler>, and  <xref:System.Net.Http.WebRequestHandler> classes.</span></span>|  
|`System.Net.WebSockets.WebSocket`|<span data-ttu-id="48927-121">Niektóre metody publiczne <xref:System.Net.WebSockets.ClientWebSocket> i <xref:System.Net.WebSockets.WebSocket> klasy.</span><span class="sxs-lookup"><span data-stu-id="48927-121">Some public methods of the <xref:System.Net.WebSockets.ClientWebSocket> and <xref:System.Net.WebSockets.WebSocket> classes.</span></span>|  
  
 <span data-ttu-id="48927-122">W tabeli poniżej wymieniono atrybuty konfiguracyjne danych wyjściowych śledzenia.</span><span class="sxs-lookup"><span data-stu-id="48927-122">The attributes listed in the following table configure trace output.</span></span>  
  
|<span data-ttu-id="48927-123">Nazwa atrybutu</span><span class="sxs-lookup"><span data-stu-id="48927-123">Attribute name</span></span>|<span data-ttu-id="48927-124">Wartość atrybutu</span><span class="sxs-lookup"><span data-stu-id="48927-124">Attribute value</span></span>|  
|--------------------|---------------------|  
|`Value`|<span data-ttu-id="48927-125">Wymagane <xref:System.String> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="48927-125">Required <xref:System.String> attribute.</span></span> <span data-ttu-id="48927-126">Ustawia poziom szczegółowości danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="48927-126">Sets the verbosity of the output.</span></span> <span data-ttu-id="48927-127">Dozwolone wartości to `Critical`, `Error`, `Verbose`, `Warning`, i `Information`.</span><span class="sxs-lookup"><span data-stu-id="48927-127">Legitimate values are `Critical`, `Error`, `Verbose`, `Warning`, and `Information`.</span></span><br /><br /> <span data-ttu-id="48927-128">Ten atrybut musi być ustawiony na \<Dodaj nazwę > element \<przełączników > elementu, jak pokazano w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="48927-128">This attribute must be set on the \<add name> element of the \<switches> element as shown in the example.</span></span> <span data-ttu-id="48927-129">Wyjątek jest generowany, jeśli ten atrybut jest ustawiony na \<źródło > element.</span><span class="sxs-lookup"><span data-stu-id="48927-129">An exception is thrown if this attribute is set on the \<source> element.</span></span>|  
|`maxdatasize`|<span data-ttu-id="48927-130">Opcjonalnie <xref:System.Int32> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="48927-130">Optional <xref:System.Int32> attribute.</span></span> <span data-ttu-id="48927-131">Ustawia maksymalną liczbę bajtów danych sieciowych w każdym zapisie ze śledzenia linii.</span><span class="sxs-lookup"><span data-stu-id="48927-131">Sets the maximum number of bytes of network data included in each line trace.</span></span> <span data-ttu-id="48927-132">Wartość domyślna to 1024.</span><span class="sxs-lookup"><span data-stu-id="48927-132">The default value is 1024.</span></span><br /><br /> <span data-ttu-id="48927-133">Ten atrybut musi być ustawiony na \<źródło > elementu, jak pokazano w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="48927-133">This attribute must be set on the \<source> element as shown in the example.</span></span> <span data-ttu-id="48927-134">Wyjątek jest generowany, jeśli ten atrybut jest ustawiony na elemencie należącym do elementu \<przełączników > element.</span><span class="sxs-lookup"><span data-stu-id="48927-134">An exception is thrown if this attribute is set on an element under the \<switches> element.</span></span>|  
|`Tracemode`|<span data-ttu-id="48927-135">Opcjonalnie <xref:System.String> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="48927-135">Optional <xref:System.String> attribute.</span></span> <span data-ttu-id="48927-136">Ustaw `includehex` Aby wyświetlić ślady protokołu w formacie szesnastkowym i tekstowym.</span><span class="sxs-lookup"><span data-stu-id="48927-136">Set to `includehex` to show protocol traces in hexadecimal and text format.</span></span> <span data-ttu-id="48927-137">Ustaw `protocolonly` wyświetlanie tylko tekstu.</span><span class="sxs-lookup"><span data-stu-id="48927-137">Set to `protocolonly` to show only text.</span></span> <span data-ttu-id="48927-138">Wartość domyślna to `includehex`.</span><span class="sxs-lookup"><span data-stu-id="48927-138">The default value is `includehex`.</span></span><br /><br /> <span data-ttu-id="48927-139">Ten atrybut musi być ustawiony na \<przełączników > elementu, jak pokazano w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="48927-139">This attribute must be set on the \<switches> element as shown in the example.</span></span> <span data-ttu-id="48927-140">Wyjątek jest generowany, jeśli ten atrybut jest ustawiony na elemencie należącym do elementu \<źródło > element.</span><span class="sxs-lookup"><span data-stu-id="48927-140">An exception is thrown if this attribute is set on an element under the \<source> element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="48927-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="48927-141">See Also</span></span>  
 [<span data-ttu-id="48927-142">Interpretowanie śledzenia sieci</span><span class="sxs-lookup"><span data-stu-id="48927-142">Interpreting Network Tracing</span></span>](../../../docs/framework/network-programming/interpreting-network-tracing.md)  
 [<span data-ttu-id="48927-143">Śledzenie sieci w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="48927-143">Network Tracing in the .NET Framework</span></span>](../../../docs/framework/network-programming/network-tracing.md)  
 [<span data-ttu-id="48927-144">Włączanie śledzenia sieci</span><span class="sxs-lookup"><span data-stu-id="48927-144">Enabling Network Tracing</span></span>](../../../docs/framework/network-programming/enabling-network-tracing.md)  
 [<span data-ttu-id="48927-145">Wprowadzenie do Instrumentacji i śledzenia</span><span class="sxs-lookup"><span data-stu-id="48927-145">Introduction to Instrumentation and Tracing</span></span>](https://msdn.microsoft.com/library/e924e57c-33cf-4b0e-9e7f-a45d13e38f2c)
