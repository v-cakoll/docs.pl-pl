---
title: <netHttpsBinding>
ms.date: 03/30/2017
ms.assetid: ff122116-6042-4792-9f21-275b4f97a105
ms.openlocfilehash: 4e15a52603df12ea3e1332efcf707f7d0c389976
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430249"
---
# <a name="nethttpsbinding"></a><span data-ttu-id="03ed3-101">\<netHttpsBinding></span><span class="sxs-lookup"><span data-stu-id="03ed3-101">\<netHttpsBinding></span></span>
<span data-ttu-id="03ed3-102">Represents a binding that a Windows Communication Foundation (WCF) service can use to configure and expose endpoints that are able to communicate over HTTPS.</span><span class="sxs-lookup"><span data-stu-id="03ed3-102">Represents a binding that a Windows Communication Foundation (WCF) service can use to configure and expose endpoints that are able to communicate over HTTPS.</span></span> <span data-ttu-id="03ed3-103">When used with a duplex contract, Web Sockets will be used, otherwise HTTPS will be used.</span><span class="sxs-lookup"><span data-stu-id="03ed3-103">When used with a duplex contract, Web Sockets will be used, otherwise HTTPS will be used.</span></span>  
  
<span data-ttu-id="03ed3-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="03ed3-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="03ed3-105">&nbsp;&nbsp;[ **\<system.serviceModel>** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="03ed3-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="03ed3-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bindings>** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="03ed3-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="03ed3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<netHttpsBinding>**</span><span class="sxs-lookup"><span data-stu-id="03ed3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netHttpsBinding>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="03ed3-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="03ed3-108">Syntax</span></span>  
  
```xml  
<netHttpsBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxReceivedMessageSize="Integer"
           messageEncoding="Binary/Text/Mtom"
           name="string"
           openTimeout="TimeSpan"
           proxyAddress="URI"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"
           useDefaultWebProxy="Boolean">
    <security mode="None/Transport/Message/TransportWithMessageCredential/TransportCredentialOnly">
      <transport clientCredentialType="None/Basic/Digest/Ntlm/Windows/Certificate"
                 proxyCredentialType="None/Basic/Digest/Ntlm/Windows"
                 realm="string" />
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="UserName/Certificate" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netHttpsBinding>
```  
  
## <a name="type"></a><span data-ttu-id="03ed3-109">Typ</span><span class="sxs-lookup"><span data-stu-id="03ed3-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="03ed3-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="03ed3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="03ed3-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="03ed3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="03ed3-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="03ed3-112">Attributes</span></span>  
  
|<span data-ttu-id="03ed3-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="03ed3-113">Attribute</span></span>|<span data-ttu-id="03ed3-114">Opis</span><span class="sxs-lookup"><span data-stu-id="03ed3-114">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="03ed3-115">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span><span class="sxs-lookup"><span data-stu-id="03ed3-115">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="03ed3-116">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="03ed3-116">The default is `false`.</span></span><br /><br /> <span data-ttu-id="03ed3-117">You can use this property when you interact with ASMX Web services that use cookies.</span><span class="sxs-lookup"><span data-stu-id="03ed3-117">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="03ed3-118">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span><span class="sxs-lookup"><span data-stu-id="03ed3-118">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="03ed3-119">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span><span class="sxs-lookup"><span data-stu-id="03ed3-119">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="03ed3-120">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="03ed3-120">The default is `false`.</span></span><br /><br /> <span data-ttu-id="03ed3-121">An Internet resource is local if it has a local address.</span><span class="sxs-lookup"><span data-stu-id="03ed3-121">An Internet resource is local if it has a local address.</span></span> <span data-ttu-id="03ed3-122">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs "http://webserver/" and "http://localhost/".</span><span class="sxs-lookup"><span data-stu-id="03ed3-122">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs "http://webserver/" and "http://localhost/".</span></span><br /><br /> <span data-ttu-id="03ed3-123">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span><span class="sxs-lookup"><span data-stu-id="03ed3-123">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span></span> <span data-ttu-id="03ed3-124">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span><span class="sxs-lookup"><span data-stu-id="03ed3-124">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span></span> <span data-ttu-id="03ed3-125">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span><span class="sxs-lookup"><span data-stu-id="03ed3-125">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span></span><br /><br /> <span data-ttu-id="03ed3-126">When this attribute is `false`, all Internet requests are made through the proxy server.</span><span class="sxs-lookup"><span data-stu-id="03ed3-126">When this attribute is `false`, all Internet requests are made through the proxy server.</span></span>|  
|`closeTimeout`|<span data-ttu-id="03ed3-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span><span class="sxs-lookup"><span data-stu-id="03ed3-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="03ed3-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="03ed3-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="03ed3-129">The default is 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="03ed3-129">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="03ed3-130">Specifies the HTTP hostname comparison mode used to parse URIs.</span><span class="sxs-lookup"><span data-stu-id="03ed3-130">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="03ed3-131">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span><span class="sxs-lookup"><span data-stu-id="03ed3-131">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="03ed3-132">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span><span class="sxs-lookup"><span data-stu-id="03ed3-132">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="03ed3-133">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span><span class="sxs-lookup"><span data-stu-id="03ed3-133">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="03ed3-134">The default value is 524288 (0x80000) bytes.</span><span class="sxs-lookup"><span data-stu-id="03ed3-134">The default value is 524288 (0x80000) bytes.</span></span><br /><br /> <span data-ttu-id="03ed3-135">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span><span class="sxs-lookup"><span data-stu-id="03ed3-135">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span></span> <span data-ttu-id="03ed3-136">Buffers are required to process messages by the service when they come out of the channel.</span><span class="sxs-lookup"><span data-stu-id="03ed3-136">Buffers are required to process messages by the service when they come out of the channel.</span></span> <span data-ttu-id="03ed3-137">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span><span class="sxs-lookup"><span data-stu-id="03ed3-137">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span></span> <span data-ttu-id="03ed3-138">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span><span class="sxs-lookup"><span data-stu-id="03ed3-138">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="03ed3-139">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span><span class="sxs-lookup"><span data-stu-id="03ed3-139">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="03ed3-140">The default value is 65,536 bytes.</span><span class="sxs-lookup"><span data-stu-id="03ed3-140">The default value is 65,536 bytes.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="03ed3-141">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span><span class="sxs-lookup"><span data-stu-id="03ed3-141">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="03ed3-142">The sender receives a SOAP fault if the message is too large for the receiver.</span><span class="sxs-lookup"><span data-stu-id="03ed3-142">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="03ed3-143">The receiver drops the message and creates an entry of the event in the trace log.</span><span class="sxs-lookup"><span data-stu-id="03ed3-143">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="03ed3-144">The default is 65,536 bytes.</span><span class="sxs-lookup"><span data-stu-id="03ed3-144">The default is 65,536 bytes.</span></span>|  
|`messageEncoding`|<span data-ttu-id="03ed3-145">Defines the encoder used to encode the SOAP message.</span><span class="sxs-lookup"><span data-stu-id="03ed3-145">Defines the encoder used to encode the SOAP message.</span></span> <span data-ttu-id="03ed3-146">Valid values include the following:</span><span class="sxs-lookup"><span data-stu-id="03ed3-146">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="03ed3-147">-   Text: Use a text message encoder.</span><span class="sxs-lookup"><span data-stu-id="03ed3-147">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="03ed3-148">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span><span class="sxs-lookup"><span data-stu-id="03ed3-148">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="03ed3-149">The default is Text.</span><span class="sxs-lookup"><span data-stu-id="03ed3-149">The default is Text.</span></span> <span data-ttu-id="03ed3-150">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="03ed3-150">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="03ed3-151">A string that contains the configuration name of the binding.</span><span class="sxs-lookup"><span data-stu-id="03ed3-151">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="03ed3-152">This value should be unique because it is used as an identification for the binding.</span><span class="sxs-lookup"><span data-stu-id="03ed3-152">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="03ed3-153">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span><span class="sxs-lookup"><span data-stu-id="03ed3-153">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="03ed3-154">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="03ed3-154">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="03ed3-155">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span><span class="sxs-lookup"><span data-stu-id="03ed3-155">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="03ed3-156">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="03ed3-156">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="03ed3-157">The default is 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="03ed3-157">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="03ed3-158">A URI that contains the address of the HTTP proxy.</span><span class="sxs-lookup"><span data-stu-id="03ed3-158">A URI that contains the address of the HTTP proxy.</span></span> <span data-ttu-id="03ed3-159">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span><span class="sxs-lookup"><span data-stu-id="03ed3-159">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span></span> <span data-ttu-id="03ed3-160">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="03ed3-160">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="03ed3-161">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span><span class="sxs-lookup"><span data-stu-id="03ed3-161">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="03ed3-162">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="03ed3-162">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="03ed3-163">The default is 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="03ed3-163">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="03ed3-164">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span><span class="sxs-lookup"><span data-stu-id="03ed3-164">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="03ed3-165">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="03ed3-165">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="03ed3-166">The default is 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="03ed3-166">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="03ed3-167">Sets the character set encoding to be used for emitting messages on the binding.</span><span class="sxs-lookup"><span data-stu-id="03ed3-167">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="03ed3-168">Valid values include the following:</span><span class="sxs-lookup"><span data-stu-id="03ed3-168">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="03ed3-169">-   BigEndianUnicode: Unicode BigEndian encoding.</span><span class="sxs-lookup"><span data-stu-id="03ed3-169">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="03ed3-170">-   Unicode: 16-bit encoding.</span><span class="sxs-lookup"><span data-stu-id="03ed3-170">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="03ed3-171">-   UTF8: 8-bit encoding</span><span class="sxs-lookup"><span data-stu-id="03ed3-171">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="03ed3-172">The default is UTF8.</span><span class="sxs-lookup"><span data-stu-id="03ed3-172">The default is UTF8.</span></span> <span data-ttu-id="03ed3-173">This attribute is of type <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="03ed3-173">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transferMode`|<span data-ttu-id="03ed3-174">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span><span class="sxs-lookup"><span data-stu-id="03ed3-174">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="03ed3-175">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span><span class="sxs-lookup"><span data-stu-id="03ed3-175">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span></span> <span data-ttu-id="03ed3-176">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="03ed3-176">The default is `true`.</span></span>|  
|||  
  
### <a name="child-elements"></a><span data-ttu-id="03ed3-177">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="03ed3-177">Child Elements</span></span>  
  
|<span data-ttu-id="03ed3-178">Element</span><span class="sxs-lookup"><span data-stu-id="03ed3-178">Element</span></span>|<span data-ttu-id="03ed3-179">Opis</span><span class="sxs-lookup"><span data-stu-id="03ed3-179">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="03ed3-180">\<security></span><span class="sxs-lookup"><span data-stu-id="03ed3-180">\<security></span></span>](security-of-nethttpbinding.md)|<span data-ttu-id="03ed3-181">Defines the security settings for the binding.</span><span class="sxs-lookup"><span data-stu-id="03ed3-181">Defines the security settings for the binding.</span></span> <span data-ttu-id="03ed3-182">This element is of type <xref:System.ServiceModel.Configuration.BasicHttpsSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="03ed3-182">This element is of type <xref:System.ServiceModel.Configuration.BasicHttpsSecurityElement>.</span></span> |  
|<span data-ttu-id="03ed3-183">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="03ed3-183">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="03ed3-184">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span><span class="sxs-lookup"><span data-stu-id="03ed3-184">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="03ed3-185">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="03ed3-185">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="03ed3-186">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="03ed3-186">Parent Elements</span></span>  
  
|<span data-ttu-id="03ed3-187">Element</span><span class="sxs-lookup"><span data-stu-id="03ed3-187">Element</span></span>|<span data-ttu-id="03ed3-188">Opis</span><span class="sxs-lookup"><span data-stu-id="03ed3-188">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="03ed3-189">\<bindings></span><span class="sxs-lookup"><span data-stu-id="03ed3-189">\<bindings></span></span>](bindings.md)|<span data-ttu-id="03ed3-190">This element holds a collection of standard and custom bindings.</span><span class="sxs-lookup"><span data-stu-id="03ed3-190">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03ed3-191">Uwagi</span><span class="sxs-lookup"><span data-stu-id="03ed3-191">Remarks</span></span>  
 <span data-ttu-id="03ed3-192">The NetHttpsBinding uses HTTPS as the transport for sending messages.</span><span class="sxs-lookup"><span data-stu-id="03ed3-192">The NetHttpsBinding uses HTTPS as the transport for sending messages.</span></span> <span data-ttu-id="03ed3-193">When used with a duplex contract, Web Sockets will be used.</span><span class="sxs-lookup"><span data-stu-id="03ed3-193">When used with a duplex contract, Web Sockets will be used.</span></span>  <span data-ttu-id="03ed3-194">When used with a request-reply contract NetHttpsBinding will behave like a BasicHttpsBinding with a binary encoder.</span><span class="sxs-lookup"><span data-stu-id="03ed3-194">When used with a request-reply contract NetHttpsBinding will behave like a BasicHttpsBinding with a binary encoder.</span></span>  
  
 <span data-ttu-id="03ed3-195">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](security-of-basichttpbinding.md) child element to a value other than `None`.</span><span class="sxs-lookup"><span data-stu-id="03ed3-195">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](security-of-basichttpbinding.md) child element to a value other than `None`.</span></span> <span data-ttu-id="03ed3-196">It uses a "Text" message encoding and UTF-8 text encoding by default.</span><span class="sxs-lookup"><span data-stu-id="03ed3-196">It uses a "Text" message encoding and UTF-8 text encoding by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03ed3-197">Przykład</span><span class="sxs-lookup"><span data-stu-id="03ed3-197">Example</span></span>  
 <span data-ttu-id="03ed3-198">The following example demonstrates the use of <xref:System.ServiceModel.NetHttpBinding> that provides HTTPS communication and maximum interoperability with first- and second-generation Web services.</span><span class="sxs-lookup"><span data-stu-id="03ed3-198">The following example demonstrates the use of <xref:System.ServiceModel.NetHttpBinding> that provides HTTPS communication and maximum interoperability with first- and second-generation Web services.</span></span> <span data-ttu-id="03ed3-199">The binding is specified in the configuration files for the client and service.</span><span class="sxs-lookup"><span data-stu-id="03ed3-199">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="03ed3-200">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span><span class="sxs-lookup"><span data-stu-id="03ed3-200">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="03ed3-201">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span><span class="sxs-lookup"><span data-stu-id="03ed3-201">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="03ed3-202">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span><span class="sxs-lookup"><span data-stu-id="03ed3-202">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="netHttpsBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <netHttpsBinding>
      <binding name="Binding1"
               hostNameComparisonMode="StrongWildcard"
               receiveTimeout="00:10:00"
               sendTimeout="00:10:00"
               openTimeout="00:10:00"
               closeTimeout="00:10:00"
               maxReceivedMessageSize="65536"
               maxBufferSize="65536"
               maxBufferPoolSize="524288"
               transferMode="Buffered"
               messageEncoding="Binary"
               textEncoding="utf-8"
               bypassProxyOnLocal="false"
               useDefaultWebProxy="true">
        <security mode="None" />
      </binding>
    </netHttpsBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="example"></a><span data-ttu-id="03ed3-203">Przykład</span><span class="sxs-lookup"><span data-stu-id="03ed3-203">Example</span></span>  
 <span data-ttu-id="03ed3-204">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span><span class="sxs-lookup"><span data-stu-id="03ed3-204">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="03ed3-205">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name from the binding.</span><span class="sxs-lookup"><span data-stu-id="03ed3-205">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name from the binding.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="netHttpsBinding"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <netHttpsBinding>
      <binding hostNameComparisonMode="StrongWildcard"
               receiveTimeout="00:10:00"
               sendTimeout="00:10:00"
               openTimeout="00:10:00"
               closeTimeout="00:10:00"
               maxReceivedMessageSize="65536"
               maxBufferSize="65536"
               maxBufferPoolSize="524288"
               transferMode="Buffered"
               messageEncoding="Binary"
               textEncoding="utf-8"
               bypassProxyOnLocal="false"
               useDefaultWebProxy="true">
        <security mode="None" />
      </binding>
    </netHttpsBinding>
  </bindings>
</system.serviceModel>
```  
  
 <span data-ttu-id="03ed3-206">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="03ed3-206">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03ed3-207">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="03ed3-207">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="03ed3-208">Powiązania</span><span class="sxs-lookup"><span data-stu-id="03ed3-208">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="03ed3-209">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="03ed3-209">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="03ed3-210">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="03ed3-210">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="03ed3-211">\<binding></span><span class="sxs-lookup"><span data-stu-id="03ed3-211">\<binding></span></span>](bindings.md)
