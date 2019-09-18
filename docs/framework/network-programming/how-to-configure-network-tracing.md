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
# <a name="how-to-configure-network-tracing"></a><span data-ttu-id="46d61-102">Instrukcje: konfigurowanie funkcji śledzenia sieci</span><span class="sxs-lookup"><span data-stu-id="46d61-102">How to: Configure Network Tracing</span></span>
<span data-ttu-id="46d61-103">Plik konfiguracyjny aplikacji lub komputera zawiera ustawienia, które określają format i zawartość danych ze śledzenia sieci.</span><span class="sxs-lookup"><span data-stu-id="46d61-103">The application or computer configuration file holds the settings that determine the format and content of network traces.</span></span> <span data-ttu-id="46d61-104">Przed rozpoczęciem procedury należy się upewnić, że śledzenie jest włączone.</span><span class="sxs-lookup"><span data-stu-id="46d61-104">Before performing this procedure, be sure tracing is enabled.</span></span> <span data-ttu-id="46d61-105">Aby uzyskać informacje na temat włączania śledzenia, zobacz [Włączanie śledzenia sieci](enabling-network-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="46d61-105">For information about enabling tracing, see [Enabling Network Tracing](enabling-network-tracing.md).</span></span>  
  
 <span data-ttu-id="46d61-106">Plik konfiguracji komputera — machine.config — znajduje się w folderze %Windir%\Microsoft.NET\Framework w katalogu, w którym zainstalowano system Windows.</span><span class="sxs-lookup"><span data-stu-id="46d61-106">The computer configuration file, machine.config, is stored in the %Windir%\Microsoft.NET\Framework folder in the directory where Windows was installed.</span></span> <span data-ttu-id="46d61-107">W folderach w obszarze%Windir%\Microsoft.NET\Framework istnieje osobny plik Machine. config dla każdej wersji .NET Framework zainstalowanej na komputerze (na przykład C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config lub C:\Windows\ Microsoft. NET\Framework64\v4.0.30319\Config\machine.config.).</span><span class="sxs-lookup"><span data-stu-id="46d61-107">There is a separate machine.config file in the folders under %Windir%\Microsoft.NET\Framework for each version of the .NET Framework installed on the computer (for example, C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config or C:\Windows\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config.).</span></span>  
  
 <span data-ttu-id="46d61-108">Ustawienia te można również wprowadzić w pliku konfiguracyjnym aplikacji. Ma on priorytet nad plikiem konfiguracyjnym komputera.</span><span class="sxs-lookup"><span data-stu-id="46d61-108">These settings can also be made in the configuration file for the application, which has precedence over the computer configuration file.</span></span>  
  
### <a name="to-configure-network-tracing"></a><span data-ttu-id="46d61-109">Aby skonfigurować funkcję śledzenia sieci</span><span class="sxs-lookup"><span data-stu-id="46d61-109">To configure network tracing</span></span>  
  
- <span data-ttu-id="46d61-110">Dodaj następujące wiersze do odpowiedniego pliku konfiguracyjnego.</span><span class="sxs-lookup"><span data-stu-id="46d61-110">Add the following lines to the appropriate configuration file.</span></span> <span data-ttu-id="46d61-111">Wartości i opcje ustawień opisano w tabelach poniżej.</span><span class="sxs-lookup"><span data-stu-id="46d61-111">The values and options for these settings are described in the tables below.</span></span>  
  
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
  
 <span data-ttu-id="46d61-112">Po dodaniu nazwy do `<switches>` bloku dane wyjściowe śledzenia zawierają informacje z niektórych metod związanych z nazwą.</span><span class="sxs-lookup"><span data-stu-id="46d61-112">When you add a name to the `<switches>` block, the trace output includes information from some methods related to the name.</span></span> <span data-ttu-id="46d61-113">W tabeli poniżej opisano dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="46d61-113">The following table describes the output.</span></span>  
  
|<span data-ttu-id="46d61-114">Nazwa</span><span class="sxs-lookup"><span data-stu-id="46d61-114">Name</span></span>|<span data-ttu-id="46d61-115">Skąd dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="46d61-115">Output from</span></span>|  
|----------|-----------------|  
|`System.Net.Sockets`|<span data-ttu-id="46d61-116">Niektóre metody <xref:System.Net.Sockets.Socket>publiczne klasy, <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient>, i <xref:System.Net.Dns></span><span class="sxs-lookup"><span data-stu-id="46d61-116">Some public methods of the <xref:System.Net.Sockets.Socket>, <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient>, and <xref:System.Net.Dns> classes</span></span>|  
|`System.Net`|<span data-ttu-id="46d61-117">Niektóre publiczne metody <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>, i <xref:System.Net.FtpWebResponse> informacje debugowania protokołu SSL (Nieprawidłowe certyfikaty, Lista brakujących wystawców i błędy certyfikatów klienta).</span><span class="sxs-lookup"><span data-stu-id="46d61-117">Some public methods of the <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>, and <xref:System.Net.FtpWebResponse> classes, and SSL debug information (invalid certificates, missing issuers list, and client certificate errors.)</span></span>|  
|`System.Net.HttpListener`|<span data-ttu-id="46d61-118">Niektóre publiczne metody <xref:System.Net.HttpListener>klasy, <xref:System.Net.HttpListenerRequest>, i <xref:System.Net.HttpListenerResponse> .</span><span class="sxs-lookup"><span data-stu-id="46d61-118">Some public methods of the <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest>, and <xref:System.Net.HttpListenerResponse> classes.</span></span>|  
|`System.Net.Cache`|<span data-ttu-id="46d61-119">Niektóre metody prywatne i wewnętrzne w `System.Net.Cache`.</span><span class="sxs-lookup"><span data-stu-id="46d61-119">Some private and internal methods in `System.Net.Cache`.</span></span>|  
|`System.Net.Http`|<span data-ttu-id="46d61-120">Niektóre <xref:System.Net.Http.HttpClient>publiczne metody klasy, <xref:System.Net.Http.DelegatingHandler>, <xref:System.Net.Http.HttpClientHandler> <xref:System.Net.Http.HttpMessageHandler>,, i<xref:System.Net.Http.WebRequestHandler> . <xref:System.Net.Http.MessageProcessingHandler></span><span class="sxs-lookup"><span data-stu-id="46d61-120">Some public methods of the  <xref:System.Net.Http.HttpClient>,  <xref:System.Net.Http.DelegatingHandler>,  <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>,  <xref:System.Net.Http.MessageProcessingHandler>, and  <xref:System.Net.Http.WebRequestHandler> classes.</span></span>|  
|`System.Net.WebSockets.WebSocket`|<span data-ttu-id="46d61-121">Niektóre metody <xref:System.Net.WebSockets.ClientWebSocket> publiczne klas i <xref:System.Net.WebSockets.WebSocket> .</span><span class="sxs-lookup"><span data-stu-id="46d61-121">Some public methods of the <xref:System.Net.WebSockets.ClientWebSocket> and <xref:System.Net.WebSockets.WebSocket> classes.</span></span>|  
  
 <span data-ttu-id="46d61-122">W tabeli poniżej wymieniono atrybuty konfiguracyjne danych wyjściowych śledzenia.</span><span class="sxs-lookup"><span data-stu-id="46d61-122">The attributes listed in the following table configure trace output.</span></span>  
  
|<span data-ttu-id="46d61-123">Nazwa atrybutu</span><span class="sxs-lookup"><span data-stu-id="46d61-123">Attribute name</span></span>|<span data-ttu-id="46d61-124">Wartość atrybutu</span><span class="sxs-lookup"><span data-stu-id="46d61-124">Attribute value</span></span>|  
|--------------------|---------------------|  
|`Value`|<span data-ttu-id="46d61-125">Wymagany <xref:System.String> atrybut.</span><span class="sxs-lookup"><span data-stu-id="46d61-125">Required <xref:System.String> attribute.</span></span> <span data-ttu-id="46d61-126">Ustawia poziom szczegółowości danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="46d61-126">Sets the verbosity of the output.</span></span> <span data-ttu-id="46d61-127">Wiarygodne wartości to `Critical`, `Error`, `Verbose` ,`Warning`i .`Information`</span><span class="sxs-lookup"><span data-stu-id="46d61-127">Legitimate values are `Critical`, `Error`, `Verbose`, `Warning`, and `Information`.</span></span><br /><br /> <span data-ttu-id="46d61-128">Ten atrybut musi być ustawiony w \<elemencie \<Dodaj nazwę > elementu > przełączników, jak pokazano w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="46d61-128">This attribute must be set on the \<add name> element of the \<switches> element as shown in the example.</span></span> <span data-ttu-id="46d61-129">Wyjątek jest generowany, \<Jeśli ten atrybut jest ustawiony w źródłowym elemencie >.</span><span class="sxs-lookup"><span data-stu-id="46d61-129">An exception is thrown if this attribute is set on the \<source> element.</span></span>|  
|`maxdatasize`|<span data-ttu-id="46d61-130">Opcjonalny <xref:System.Int32> atrybut.</span><span class="sxs-lookup"><span data-stu-id="46d61-130">Optional <xref:System.Int32> attribute.</span></span> <span data-ttu-id="46d61-131">Ustawia maksymalną liczbę bajtów danych sieciowych w każdym zapisie ze śledzenia linii.</span><span class="sxs-lookup"><span data-stu-id="46d61-131">Sets the maximum number of bytes of network data included in each line trace.</span></span> <span data-ttu-id="46d61-132">Wartość domyślna to 1024.</span><span class="sxs-lookup"><span data-stu-id="46d61-132">The default value is 1024.</span></span><br /><br /> <span data-ttu-id="46d61-133">Ten atrybut musi być ustawiony dla \<elementu źródłowego >, jak pokazano w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="46d61-133">This attribute must be set on the \<source> element as shown in the example.</span></span> <span data-ttu-id="46d61-134">Wyjątek jest generowany, jeśli ten atrybut jest ustawiony dla elementu w obszarze \<przełączniki > elementu.</span><span class="sxs-lookup"><span data-stu-id="46d61-134">An exception is thrown if this attribute is set on an element under the \<switches> element.</span></span>|  
|`Tracemode`|<span data-ttu-id="46d61-135">Opcjonalny <xref:System.String> atrybut.</span><span class="sxs-lookup"><span data-stu-id="46d61-135">Optional <xref:System.String> attribute.</span></span> <span data-ttu-id="46d61-136">Ustaw, `includehex` aby wyświetlać ślady protokołu w formacie szesnastkowym i tekstowym.</span><span class="sxs-lookup"><span data-stu-id="46d61-136">Set to `includehex` to show protocol traces in hexadecimal and text format.</span></span> <span data-ttu-id="46d61-137">Ustaw, `protocolonly` aby pokazywać tylko tekst.</span><span class="sxs-lookup"><span data-stu-id="46d61-137">Set to `protocolonly` to show only text.</span></span> <span data-ttu-id="46d61-138">Wartość domyślna to `includehex`.</span><span class="sxs-lookup"><span data-stu-id="46d61-138">The default value is `includehex`.</span></span><br /><br /> <span data-ttu-id="46d61-139">Ten atrybut musi być ustawiony dla \<przełączników > elementu, jak pokazano w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="46d61-139">This attribute must be set on the \<switches> element as shown in the example.</span></span> <span data-ttu-id="46d61-140">Wyjątek jest zgłaszany, jeśli ten atrybut jest ustawiony dla elementu pod \<elementem źródłowym >.</span><span class="sxs-lookup"><span data-stu-id="46d61-140">An exception is thrown if this attribute is set on an element under the \<source> element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="46d61-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="46d61-141">See also</span></span>

- [<span data-ttu-id="46d61-142">Interpretowanie śledzenia sieci</span><span class="sxs-lookup"><span data-stu-id="46d61-142">Interpreting Network Tracing</span></span>](interpreting-network-tracing.md)
- [<span data-ttu-id="46d61-143">Śledzenie sieci w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="46d61-143">Network Tracing in the .NET Framework</span></span>](network-tracing.md)
- [<span data-ttu-id="46d61-144">Włączanie śledzenia sieci</span><span class="sxs-lookup"><span data-stu-id="46d61-144">Enabling Network Tracing</span></span>](enabling-network-tracing.md)
- [<span data-ttu-id="46d61-145">Śledzenie i instrumentacja aplikacji</span><span class="sxs-lookup"><span data-stu-id="46d61-145">Tracing and Instrumenting Applications</span></span>](../debug-trace-profile/tracing-and-instrumenting-applications.md)
