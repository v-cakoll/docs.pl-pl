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
# <a name="how-to-configure-network-tracing"></a><span data-ttu-id="e0ea9-102">Jak: Konfigurowanie śledzenia sieci</span><span class="sxs-lookup"><span data-stu-id="e0ea9-102">How to: Configure network tracing</span></span>

<span data-ttu-id="e0ea9-103">Plik konfiguracyjny aplikacji lub komputera zawiera ustawienia, które określają format i zawartość danych ze śledzenia sieci.</span><span class="sxs-lookup"><span data-stu-id="e0ea9-103">The application or computer configuration file holds the settings that determine the format and content of network traces.</span></span> <span data-ttu-id="e0ea9-104">Przed rozpoczęciem procedury należy się upewnić, że śledzenie jest włączone.</span><span class="sxs-lookup"><span data-stu-id="e0ea9-104">Before performing this procedure, be sure tracing is enabled.</span></span> <span data-ttu-id="e0ea9-105">Aby uzyskać więcej informacji, zobacz [Włączanie śledzenia sieci](enabling-network-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="e0ea9-105">For more information, see [Enable network tracing](enabling-network-tracing.md).</span></span>

<span data-ttu-id="e0ea9-106">Plik konfiguracyjny komputera, *machine.config,* jest przechowywany w folderze *%windir%\Microsoft.NET\Framework.*</span><span class="sxs-lookup"><span data-stu-id="e0ea9-106">The computer configuration file, *machine.config*, is stored in the *%windir%\Microsoft.NET\Framework* folder.</span></span> <span data-ttu-id="e0ea9-107">W folderach w obszarze *%windir%\Microsoft.NET\Framework* znajduje się oddzielny plik *machine.config* dla każdej wersji programu .NET Framework zainstalowanej na komputerze, na przykład:</span><span class="sxs-lookup"><span data-stu-id="e0ea9-107">There is a separate *machine.config* file in the folders under *%windir%\Microsoft.NET\Framework* for each version of the .NET Framework installed on the computer, for example:</span></span>

- <span data-ttu-id="e0ea9-108">*C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\Config\machine.config*</span><span class="sxs-lookup"><span data-stu-id="e0ea9-108">*C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\Config\machine.config*</span></span>
- <span data-ttu-id="e0ea9-109">*C:\WINDOWS\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config*</span><span class="sxs-lookup"><span data-stu-id="e0ea9-109">*C:\WINDOWS\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config*</span></span>

<span data-ttu-id="e0ea9-110">Ustawienia te można również wprowadzić w pliku konfiguracyjnym aplikacji. Ma on priorytet nad plikiem konfiguracyjnym komputera.</span><span class="sxs-lookup"><span data-stu-id="e0ea9-110">These settings can also be made in the configuration file for the application, which has precedence over the computer configuration file.</span></span>

## <a name="configure-network-tracing"></a><span data-ttu-id="e0ea9-111">Konfigurowanie śledzenia sieci</span><span class="sxs-lookup"><span data-stu-id="e0ea9-111">Configure network tracing</span></span>

<span data-ttu-id="e0ea9-112">Aby skonfigurować śledzenie sieci, dodaj następujące wiersze do odpowiedniego pliku konfiguracyjnego.</span><span class="sxs-lookup"><span data-stu-id="e0ea9-112">To configure network tracing, add the following lines to the appropriate configuration file.</span></span> <span data-ttu-id="e0ea9-113">Wartości i opcje ustawień opisano w tabelach poniżej.</span><span class="sxs-lookup"><span data-stu-id="e0ea9-113">The values and options for these settings are described in the tables below.</span></span>

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

### <a name="trace-output-from-methods"></a><span data-ttu-id="e0ea9-114">Śledzenie danych wyjściowych z metod</span><span class="sxs-lookup"><span data-stu-id="e0ea9-114">Trace output from methods</span></span>

<span data-ttu-id="e0ea9-115">Po dodaniu nazwy `<switches>` do bloku dane wyjściowe śledzenia zawiera informacje z niektórych metod związanych z nazwą.</span><span class="sxs-lookup"><span data-stu-id="e0ea9-115">When you add a name to the `<switches>` block, the trace output includes information from some methods related to the name.</span></span> <span data-ttu-id="e0ea9-116">W poniższej tabeli opisano dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e0ea9-116">The following table describes the output:</span></span>

|<span data-ttu-id="e0ea9-117">Nazwa</span><span class="sxs-lookup"><span data-stu-id="e0ea9-117">Name</span></span>|<span data-ttu-id="e0ea9-118">Skąd dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="e0ea9-118">Output from</span></span>|
|----------|-----------------|
|`System.Net.Sockets`|<span data-ttu-id="e0ea9-119">Niektóre publiczne metody <xref:System.Net.Sockets.Socket> <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Dns> i klasy.</span><span class="sxs-lookup"><span data-stu-id="e0ea9-119">Some public methods of the <xref:System.Net.Sockets.Socket>, <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient>, and <xref:System.Net.Dns> classes.</span></span>|
|`System.Net`|<span data-ttu-id="e0ea9-120">Niektóre publiczne metody <xref:System.Net.HttpWebRequest> <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.FtpWebResponse> i klas oraz informacje debugowania SSL (nieprawidłowe certyfikaty, lista brakujących wystawców i błędy certyfikatów klienta).</span><span class="sxs-lookup"><span data-stu-id="e0ea9-120">Some public methods of the <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>, and <xref:System.Net.FtpWebResponse> classes, and SSL debug information (invalid certificates, missing issuers list, and client certificate errors).</span></span>|
|`System.Net.HttpListener`|<span data-ttu-id="e0ea9-121">Niektóre publiczne metody <xref:System.Net.HttpListener> <xref:System.Net.HttpListenerRequest>, <xref:System.Net.HttpListenerResponse> i klasy.</span><span class="sxs-lookup"><span data-stu-id="e0ea9-121">Some public methods of the <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest>, and <xref:System.Net.HttpListenerResponse> classes.</span></span>|
|`System.Net.Cache`|<span data-ttu-id="e0ea9-122">Niektóre metody prywatne `System.Net.Cache`i wewnętrzne w .</span><span class="sxs-lookup"><span data-stu-id="e0ea9-122">Some private and internal methods in `System.Net.Cache`.</span></span>|
|`System.Net.Http`|<span data-ttu-id="e0ea9-123">Niektóre publiczne metody <xref:System.Net.Http.HttpClient> <xref:System.Net.Http.DelegatingHandler>, <xref:System.Net.Http.HttpClientHandler> <xref:System.Net.Http.HttpMessageHandler>, <xref:System.Net.Http.MessageProcessingHandler>, <xref:System.Net.Http.WebRequestHandler> , i klas.</span><span class="sxs-lookup"><span data-stu-id="e0ea9-123">Some public methods of the  <xref:System.Net.Http.HttpClient>,  <xref:System.Net.Http.DelegatingHandler>,  <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>,  <xref:System.Net.Http.MessageProcessingHandler>, and  <xref:System.Net.Http.WebRequestHandler> classes.</span></span>|
|`System.Net.WebSockets.WebSocket`|<span data-ttu-id="e0ea9-124">Niektóre publiczne metody <xref:System.Net.WebSockets.ClientWebSocket> <xref:System.Net.WebSockets.WebSocket> i klasy.</span><span class="sxs-lookup"><span data-stu-id="e0ea9-124">Some public methods of the <xref:System.Net.WebSockets.ClientWebSocket> and <xref:System.Net.WebSockets.WebSocket> classes.</span></span>|

### <a name="trace-output-attributes"></a><span data-ttu-id="e0ea9-125">Śledzenie atrybutów danych wyjściowych</span><span class="sxs-lookup"><span data-stu-id="e0ea9-125">Trace output attributes</span></span>

<span data-ttu-id="e0ea9-126">Atrybuty wymienione w poniższej tabeli konfigurują dane wyjściowe śledzenia:</span><span class="sxs-lookup"><span data-stu-id="e0ea9-126">The attributes listed in the following table configure trace output:</span></span>

|<span data-ttu-id="e0ea9-127">Nazwa atrybutu</span><span class="sxs-lookup"><span data-stu-id="e0ea9-127">Attribute name</span></span>|<span data-ttu-id="e0ea9-128">Wartość atrybutu</span><span class="sxs-lookup"><span data-stu-id="e0ea9-128">Attribute value</span></span>|
|--------------------|---------------------|
|`value`|<span data-ttu-id="e0ea9-129">Wymagany <xref:System.String> atrybut.</span><span class="sxs-lookup"><span data-stu-id="e0ea9-129">Required <xref:System.String> attribute.</span></span> <span data-ttu-id="e0ea9-130">Ustawia poziom szczegółowości danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="e0ea9-130">Sets the verbosity of the output.</span></span> <span data-ttu-id="e0ea9-131">Wartości zgodne `Critical` `Error`z `Verbose` `Warning`prawem `Information`to , , , i .</span><span class="sxs-lookup"><span data-stu-id="e0ea9-131">Legitimate values are `Critical`, `Error`, `Verbose`, `Warning`, and `Information`.</span></span><br /><br /><span data-ttu-id="e0ea9-132">Ten atrybut musi być ustawiony na **add** element elementu **przełączniki.**</span><span class="sxs-lookup"><span data-stu-id="e0ea9-132">This attribute must be set on the **add** element of the **switches** element.</span></span> <span data-ttu-id="e0ea9-133">Wyjątek jest zgłaszany, jeśli ten atrybut jest ustawiony na element **źródłowy.**</span><span class="sxs-lookup"><span data-stu-id="e0ea9-133">An exception is thrown if this attribute is set on the **source** element.</span></span><br/><br/><span data-ttu-id="e0ea9-134">Przykład: `<add name="System.Net" value="Verbose"/>`</span><span class="sxs-lookup"><span data-stu-id="e0ea9-134">Example: `<add name="System.Net" value="Verbose"/>`</span></span>|
|`maxdatasize`|<span data-ttu-id="e0ea9-135">Opcjonalny <xref:System.Int32> atrybut.</span><span class="sxs-lookup"><span data-stu-id="e0ea9-135">Optional <xref:System.Int32> attribute.</span></span> <span data-ttu-id="e0ea9-136">Ustawia maksymalną liczbę bajtów danych sieciowych w każdym zapisie ze śledzenia linii.</span><span class="sxs-lookup"><span data-stu-id="e0ea9-136">Sets the maximum number of bytes of network data included in each line trace.</span></span> <span data-ttu-id="e0ea9-137">Wartość domyślna to 1024.</span><span class="sxs-lookup"><span data-stu-id="e0ea9-137">The default value is 1024.</span></span><br /><br /><span data-ttu-id="e0ea9-138">Ten atrybut musi być ustawiony na elemencie **źródłowym.**</span><span class="sxs-lookup"><span data-stu-id="e0ea9-138">This attribute must be set on the **source** element.</span></span> <span data-ttu-id="e0ea9-139">Wyjątek jest zgłaszany, jeśli ten atrybut jest ustawiony na element pod **elementem przełączników.**</span><span class="sxs-lookup"><span data-stu-id="e0ea9-139">An exception is thrown if this attribute is set on an element under the **switches** element.</span></span><br/><br/><span data-ttu-id="e0ea9-140">Przykład: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span><span class="sxs-lookup"><span data-stu-id="e0ea9-140">Example: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span></span>|
|`tracemode`|<span data-ttu-id="e0ea9-141">Opcjonalny <xref:System.String> atrybut.</span><span class="sxs-lookup"><span data-stu-id="e0ea9-141">Optional <xref:System.String> attribute.</span></span> <span data-ttu-id="e0ea9-142">Ustaw, `includehex` aby wyświetlić ślady protokołu w formacie szesnastkowym i tekstowym.</span><span class="sxs-lookup"><span data-stu-id="e0ea9-142">Set to `includehex` to show protocol traces in hexadecimal and text format.</span></span> <span data-ttu-id="e0ea9-143">Ustaw, `protocolonly` aby wyświetlić tylko tekst.</span><span class="sxs-lookup"><span data-stu-id="e0ea9-143">Set to `protocolonly` to show only text.</span></span> <span data-ttu-id="e0ea9-144">Wartością domyślną jest `includehex`.</span><span class="sxs-lookup"><span data-stu-id="e0ea9-144">The default value is `includehex`.</span></span><br /><br /><span data-ttu-id="e0ea9-145">Ten atrybut musi być ustawiony na elemencie **źródłowym.**</span><span class="sxs-lookup"><span data-stu-id="e0ea9-145">This attribute must be set on the **source** element.</span></span> <span data-ttu-id="e0ea9-146">Wyjątek jest zgłaszany, jeśli ten atrybut jest ustawiony na element pod **elementem przełączników.**</span><span class="sxs-lookup"><span data-stu-id="e0ea9-146">An exception is thrown if this attribute is set on an element under the **switches** element.</span></span><br/><br/><span data-ttu-id="e0ea9-147">Przykład: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span><span class="sxs-lookup"><span data-stu-id="e0ea9-147">Example: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span></span>|

## <a name="see-also"></a><span data-ttu-id="e0ea9-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e0ea9-148">See also</span></span>

- [<span data-ttu-id="e0ea9-149">Interpretowanie śledzenia sieci</span><span class="sxs-lookup"><span data-stu-id="e0ea9-149">Interpreting Network Tracing</span></span>](interpreting-network-tracing.md)
- [<span data-ttu-id="e0ea9-150">Śledzenie sieci w .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e0ea9-150">Network Tracing in the .NET Framework</span></span>](network-tracing.md)
- [<span data-ttu-id="e0ea9-151">Włączanie śledzenia sieci</span><span class="sxs-lookup"><span data-stu-id="e0ea9-151">Enabling Network Tracing</span></span>](enabling-network-tracing.md)
- [<span data-ttu-id="e0ea9-152">Śledzenie i instrumentacja aplikacji</span><span class="sxs-lookup"><span data-stu-id="e0ea9-152">Tracing and Instrumenting Applications</span></span>](../debug-trace-profile/tracing-and-instrumenting-applications.md)
