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
# <a name="how-to-configure-network-tracing"></a><span data-ttu-id="fa062-104">Instrukcje: Konfigurowanie śledzenia sieci</span><span class="sxs-lookup"><span data-stu-id="fa062-104">How to: Configure network tracing</span></span>

<span data-ttu-id="fa062-105">Plik konfiguracyjny aplikacji lub komputera zawiera ustawienia, które określają format i zawartość danych ze śledzenia sieci.</span><span class="sxs-lookup"><span data-stu-id="fa062-105">The application or computer configuration file holds the settings that determine the format and content of network traces.</span></span> <span data-ttu-id="fa062-106">Przed rozpoczęciem procedury należy się upewnić, że śledzenie jest włączone.</span><span class="sxs-lookup"><span data-stu-id="fa062-106">Before performing this procedure, be sure tracing is enabled.</span></span> <span data-ttu-id="fa062-107">Aby uzyskać więcej informacji, zobacz [Włączanie śledzenia sieci](enabling-network-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="fa062-107">For more information, see [Enable network tracing](enabling-network-tracing.md).</span></span>

<span data-ttu-id="fa062-108">Plik konfiguracji komputera, *Machine. config*, jest przechowywany w folderze *%windir%\Microsoft.NET\Framework* .</span><span class="sxs-lookup"><span data-stu-id="fa062-108">The computer configuration file, *machine.config*, is stored in the *%windir%\Microsoft.NET\Framework* folder.</span></span> <span data-ttu-id="fa062-109">W folderach w obszarze *%windir%\Microsoft.NET\Framework* istnieje osobny plik *Machine. config* dla każdej wersji .NET Framework zainstalowanej na komputerze, na przykład:</span><span class="sxs-lookup"><span data-stu-id="fa062-109">There is a separate *machine.config* file in the folders under *%windir%\Microsoft.NET\Framework* for each version of the .NET Framework installed on the computer, for example:</span></span>

- <span data-ttu-id="fa062-110">*C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\Config\machine.config*</span><span class="sxs-lookup"><span data-stu-id="fa062-110">*C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\Config\machine.config*</span></span>
- <span data-ttu-id="fa062-111">*C:\WINDOWS\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config*</span><span class="sxs-lookup"><span data-stu-id="fa062-111">*C:\WINDOWS\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config*</span></span>

<span data-ttu-id="fa062-112">Ustawienia te można również wprowadzić w pliku konfiguracyjnym aplikacji. Ma on priorytet nad plikiem konfiguracyjnym komputera.</span><span class="sxs-lookup"><span data-stu-id="fa062-112">These settings can also be made in the configuration file for the application, which has precedence over the computer configuration file.</span></span>

## <a name="configure-network-tracing"></a><span data-ttu-id="fa062-113">Konfigurowanie śledzenia sieci</span><span class="sxs-lookup"><span data-stu-id="fa062-113">Configure network tracing</span></span>

<span data-ttu-id="fa062-114">Aby skonfigurować śledzenie sieci, Dodaj następujące wiersze do odpowiedniego pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="fa062-114">To configure network tracing, add the following lines to the appropriate configuration file.</span></span> <span data-ttu-id="fa062-115">Wartości i opcje ustawień opisano w tabelach poniżej.</span><span class="sxs-lookup"><span data-stu-id="fa062-115">The values and options for these settings are described in the tables below.</span></span>

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

### <a name="trace-output-from-methods"></a><span data-ttu-id="fa062-116">Śledzenie danych wyjściowych z metod</span><span class="sxs-lookup"><span data-stu-id="fa062-116">Trace output from methods</span></span>

<span data-ttu-id="fa062-117">Po dodaniu nazwy do `<switches>` bloku dane wyjściowe śledzenia zawierają informacje z niektórych metod związanych z nazwą.</span><span class="sxs-lookup"><span data-stu-id="fa062-117">When you add a name to the `<switches>` block, the trace output includes information from some methods related to the name.</span></span> <span data-ttu-id="fa062-118">W poniższej tabeli opisano dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="fa062-118">The following table describes the output:</span></span>

|<span data-ttu-id="fa062-119">Nazwa</span><span class="sxs-lookup"><span data-stu-id="fa062-119">Name</span></span>|<span data-ttu-id="fa062-120">Skąd dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="fa062-120">Output from</span></span>|
|----------|-----------------|
|`System.Net.Sockets`|<span data-ttu-id="fa062-121">Niektóre metody publiczne <xref:System.Net.Sockets.Socket> <xref:System.Net.Sockets.TcpListener> klasy,, <xref:System.Net.Sockets.TcpClient> , i <xref:System.Net.Dns> .</span><span class="sxs-lookup"><span data-stu-id="fa062-121">Some public methods of the <xref:System.Net.Sockets.Socket>, <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient>, and <xref:System.Net.Dns> classes.</span></span>|
|`System.Net`|<span data-ttu-id="fa062-122">Niektóre publiczne metody <xref:System.Net.HttpWebRequest> , <xref:System.Net.HttpWebResponse> , <xref:System.Net.FtpWebRequest> , i <xref:System.Net.FtpWebResponse> informacje debugowania protokołu SSL (Nieprawidłowe certyfikaty, Lista brakujących wystawców i błędy certyfikatów klienta).</span><span class="sxs-lookup"><span data-stu-id="fa062-122">Some public methods of the <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>, and <xref:System.Net.FtpWebResponse> classes, and SSL debug information (invalid certificates, missing issuers list, and client certificate errors).</span></span>|
|`System.Net.HttpListener`|<span data-ttu-id="fa062-123">Niektóre publiczne metody <xref:System.Net.HttpListener> <xref:System.Net.HttpListenerRequest> klasy,, i <xref:System.Net.HttpListenerResponse> .</span><span class="sxs-lookup"><span data-stu-id="fa062-123">Some public methods of the <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest>, and <xref:System.Net.HttpListenerResponse> classes.</span></span>|
|`System.Net.Cache`|<span data-ttu-id="fa062-124">Niektóre metody prywatne i wewnętrzne w `System.Net.Cache` .</span><span class="sxs-lookup"><span data-stu-id="fa062-124">Some private and internal methods in `System.Net.Cache`.</span></span>|
|`System.Net.Http`|<span data-ttu-id="fa062-125">Niektóre publiczne metody <xref:System.Net.Http.HttpClient> klasy,,,, <xref:System.Net.Http.DelegatingHandler> <xref:System.Net.Http.HttpClientHandler> <xref:System.Net.Http.HttpMessageHandler> <xref:System.Net.Http.MessageProcessingHandler> i <xref:System.Net.Http.WebRequestHandler> .</span><span class="sxs-lookup"><span data-stu-id="fa062-125">Some public methods of the  <xref:System.Net.Http.HttpClient>,  <xref:System.Net.Http.DelegatingHandler>,  <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>,  <xref:System.Net.Http.MessageProcessingHandler>, and  <xref:System.Net.Http.WebRequestHandler> classes.</span></span>|
|`System.Net.WebSockets.WebSocket`|<span data-ttu-id="fa062-126">Niektóre metody publiczne <xref:System.Net.WebSockets.ClientWebSocket> <xref:System.Net.WebSockets.WebSocket> klas i.</span><span class="sxs-lookup"><span data-stu-id="fa062-126">Some public methods of the <xref:System.Net.WebSockets.ClientWebSocket> and <xref:System.Net.WebSockets.WebSocket> classes.</span></span>|

### <a name="trace-output-attributes"></a><span data-ttu-id="fa062-127">Atrybuty wyjściowe śledzenia</span><span class="sxs-lookup"><span data-stu-id="fa062-127">Trace output attributes</span></span>

<span data-ttu-id="fa062-128">Atrybuty wymienione w poniższej tabeli konfigurują dane wyjściowe śledzenia:</span><span class="sxs-lookup"><span data-stu-id="fa062-128">The attributes listed in the following table configure trace output:</span></span>

|<span data-ttu-id="fa062-129">Nazwa atrybutu</span><span class="sxs-lookup"><span data-stu-id="fa062-129">Attribute name</span></span>|<span data-ttu-id="fa062-130">Wartość atrybutu</span><span class="sxs-lookup"><span data-stu-id="fa062-130">Attribute value</span></span>|
|--------------------|---------------------|
|`value`|<span data-ttu-id="fa062-131">Wymagany <xref:System.String> atrybut.</span><span class="sxs-lookup"><span data-stu-id="fa062-131">Required <xref:System.String> attribute.</span></span> <span data-ttu-id="fa062-132">Ustawia poziom szczegółowości danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="fa062-132">Sets the verbosity of the output.</span></span> <span data-ttu-id="fa062-133">Wiarygodne wartości to `Critical` , `Error` , `Verbose` , `Warning` i `Information` .</span><span class="sxs-lookup"><span data-stu-id="fa062-133">Legitimate values are `Critical`, `Error`, `Verbose`, `Warning`, and `Information`.</span></span><br /><br /><span data-ttu-id="fa062-134">Ten atrybut musi być ustawiony w elemencie **Add** elementu **switchs** .</span><span class="sxs-lookup"><span data-stu-id="fa062-134">This attribute must be set on the **add** element of the **switches** element.</span></span> <span data-ttu-id="fa062-135">Wyjątek jest generowany, jeśli ten atrybut jest ustawiony dla elementu **źródłowego** .</span><span class="sxs-lookup"><span data-stu-id="fa062-135">An exception is thrown if this attribute is set on the **source** element.</span></span><br/><br/><span data-ttu-id="fa062-136">Przykład: `<add name="System.Net" value="Verbose"/>`</span><span class="sxs-lookup"><span data-stu-id="fa062-136">Example: `<add name="System.Net" value="Verbose"/>`</span></span>|
|`maxdatasize`|<span data-ttu-id="fa062-137">Opcjonalny <xref:System.Int32> atrybut.</span><span class="sxs-lookup"><span data-stu-id="fa062-137">Optional <xref:System.Int32> attribute.</span></span> <span data-ttu-id="fa062-138">Ustawia maksymalną liczbę bajtów danych sieciowych w każdym zapisie ze śledzenia linii.</span><span class="sxs-lookup"><span data-stu-id="fa062-138">Sets the maximum number of bytes of network data included in each line trace.</span></span> <span data-ttu-id="fa062-139">Wartość domyślna to 1024.</span><span class="sxs-lookup"><span data-stu-id="fa062-139">The default value is 1024.</span></span><br /><br /><span data-ttu-id="fa062-140">Ten atrybut musi być ustawiony dla elementu **Source** .</span><span class="sxs-lookup"><span data-stu-id="fa062-140">This attribute must be set on the **source** element.</span></span> <span data-ttu-id="fa062-141">Wyjątek jest generowany, jeśli ten atrybut jest ustawiony dla elementu w elemencie **switchs** .</span><span class="sxs-lookup"><span data-stu-id="fa062-141">An exception is thrown if this attribute is set on an element under the **switches** element.</span></span><br/><br/><span data-ttu-id="fa062-142">Przykład: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span><span class="sxs-lookup"><span data-stu-id="fa062-142">Example: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span></span>|
|`tracemode`|<span data-ttu-id="fa062-143">Opcjonalny <xref:System.String> atrybut.</span><span class="sxs-lookup"><span data-stu-id="fa062-143">Optional <xref:System.String> attribute.</span></span> <span data-ttu-id="fa062-144">Ustaw, aby `includehex` wyświetlać ślady protokołu w formacie szesnastkowym i tekstowym.</span><span class="sxs-lookup"><span data-stu-id="fa062-144">Set to `includehex` to show protocol traces in hexadecimal and text format.</span></span> <span data-ttu-id="fa062-145">Ustaw, aby `protocolonly` pokazywać tylko tekst.</span><span class="sxs-lookup"><span data-stu-id="fa062-145">Set to `protocolonly` to show only text.</span></span> <span data-ttu-id="fa062-146">Wartość domyślna to `includehex`.</span><span class="sxs-lookup"><span data-stu-id="fa062-146">The default value is `includehex`.</span></span><br /><br /><span data-ttu-id="fa062-147">Ten atrybut musi być ustawiony dla elementu **Source** .</span><span class="sxs-lookup"><span data-stu-id="fa062-147">This attribute must be set on the **source** element.</span></span> <span data-ttu-id="fa062-148">Wyjątek jest generowany, jeśli ten atrybut jest ustawiony dla elementu w elemencie **switchs** .</span><span class="sxs-lookup"><span data-stu-id="fa062-148">An exception is thrown if this attribute is set on an element under the **switches** element.</span></span><br/><br/><span data-ttu-id="fa062-149">Przykład: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span><span class="sxs-lookup"><span data-stu-id="fa062-149">Example: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span></span>|

## <a name="see-also"></a><span data-ttu-id="fa062-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fa062-150">See also</span></span>

- [<span data-ttu-id="fa062-151">Interpretowanie śledzenia sieci</span><span class="sxs-lookup"><span data-stu-id="fa062-151">Interpreting Network Tracing</span></span>](interpreting-network-tracing.md)
- [<span data-ttu-id="fa062-152">Śledzenie sieci w .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fa062-152">Network Tracing in the .NET Framework</span></span>](network-tracing.md)
- [<span data-ttu-id="fa062-153">Włączanie śledzenia sieci</span><span class="sxs-lookup"><span data-stu-id="fa062-153">Enabling Network Tracing</span></span>](enabling-network-tracing.md)
- [<span data-ttu-id="fa062-154">Śledzenie i instrumentacja aplikacji</span><span class="sxs-lookup"><span data-stu-id="fa062-154">Tracing and Instrumenting Applications</span></span>](../debug-trace-profile/tracing-and-instrumenting-applications.md)
