---
title: <basicHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- basicHttpBinding Element
ms.assetid: 85cf1a4f-26c2-48c7-bda6-6c960d5d3fb3
ms.openlocfilehash: f1be0997fc7b2b884c7ec90ea6a02ea0af96ab4c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431025"
---
# <a name="basichttpbinding"></a><span data-ttu-id="0329c-101">\<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="0329c-101">\<basicHttpBinding></span></span>
<span data-ttu-id="0329c-102">Represents a binding that a Windows Communication Foundation (WCF) service can use to configure and expose endpoints that are able to communicate with ASMX-based Web services and clients and other services that conform to the WS-I Basic Profile 1.1.</span><span class="sxs-lookup"><span data-stu-id="0329c-102">Represents a binding that a Windows Communication Foundation (WCF) service can use to configure and expose endpoints that are able to communicate with ASMX-based Web services and clients and other services that conform to the WS-I Basic Profile 1.1.</span></span>  
  
<span data-ttu-id="0329c-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0329c-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0329c-104">&nbsp;&nbsp;[ **\<system.serviceModel>** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="0329c-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="0329c-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bindings>** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="0329c-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="0329c-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<basicHttpBinding>**</span><span class="sxs-lookup"><span data-stu-id="0329c-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<basicHttpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0329c-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="0329c-107">Syntax</span></span>  
  
```xml  
<basicHttpBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxReceivedMessageSize="Integer"
           messageEncoding="Text/Mtom"
           name="String"
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
                 realm="String" />
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="UserName/Certificate" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</basicHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0329c-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0329c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0329c-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0329c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0329c-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0329c-110">Attributes</span></span>  
  
|<span data-ttu-id="0329c-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0329c-111">Attribute</span></span>|<span data-ttu-id="0329c-112">Opis</span><span class="sxs-lookup"><span data-stu-id="0329c-112">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="0329c-113">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span><span class="sxs-lookup"><span data-stu-id="0329c-113">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="0329c-114">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="0329c-114">The default is `false`.</span></span><br /><br /> <span data-ttu-id="0329c-115">You can use this property when you interact with ASMX Web services that use cookies.</span><span class="sxs-lookup"><span data-stu-id="0329c-115">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="0329c-116">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span><span class="sxs-lookup"><span data-stu-id="0329c-116">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="0329c-117">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span><span class="sxs-lookup"><span data-stu-id="0329c-117">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="0329c-118">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="0329c-118">The default is `false`.</span></span><br /><br /> <span data-ttu-id="0329c-119">An Internet resource is local if it has a local address.</span><span class="sxs-lookup"><span data-stu-id="0329c-119">An Internet resource is local if it has a local address.</span></span> <span data-ttu-id="0329c-120">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs "http://webserver/" and "http://localhost/".</span><span class="sxs-lookup"><span data-stu-id="0329c-120">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs "http://webserver/" and "http://localhost/".</span></span><br /><br /> <span data-ttu-id="0329c-121">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span><span class="sxs-lookup"><span data-stu-id="0329c-121">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span></span> <span data-ttu-id="0329c-122">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span><span class="sxs-lookup"><span data-stu-id="0329c-122">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span></span> <span data-ttu-id="0329c-123">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span><span class="sxs-lookup"><span data-stu-id="0329c-123">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span></span><br /><br /> <span data-ttu-id="0329c-124">When this attribute is `false`, all Internet requests are made through the proxy server.</span><span class="sxs-lookup"><span data-stu-id="0329c-124">When this attribute is `false`, all Internet requests are made through the proxy server.</span></span>|  
|`closeTimeout`|<span data-ttu-id="0329c-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span><span class="sxs-lookup"><span data-stu-id="0329c-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="0329c-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="0329c-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0329c-127">The default is 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="0329c-127">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="0329c-128">Specifies the HTTP hostname comparison mode used to parse URIs.</span><span class="sxs-lookup"><span data-stu-id="0329c-128">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="0329c-129">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span><span class="sxs-lookup"><span data-stu-id="0329c-129">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="0329c-130">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span><span class="sxs-lookup"><span data-stu-id="0329c-130">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="0329c-131">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span><span class="sxs-lookup"><span data-stu-id="0329c-131">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="0329c-132">The default value is 524288 (0x80000) bytes.</span><span class="sxs-lookup"><span data-stu-id="0329c-132">The default value is 524288 (0x80000) bytes.</span></span><br /><br /> <span data-ttu-id="0329c-133">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span><span class="sxs-lookup"><span data-stu-id="0329c-133">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span></span> <span data-ttu-id="0329c-134">Buffers are required to process messages by the service when they come out of the channel.</span><span class="sxs-lookup"><span data-stu-id="0329c-134">Buffers are required to process messages by the service when they come out of the channel.</span></span> <span data-ttu-id="0329c-135">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span><span class="sxs-lookup"><span data-stu-id="0329c-135">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span></span> <span data-ttu-id="0329c-136">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span><span class="sxs-lookup"><span data-stu-id="0329c-136">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="0329c-137">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span><span class="sxs-lookup"><span data-stu-id="0329c-137">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="0329c-138">The default value is 65,536 bytes.</span><span class="sxs-lookup"><span data-stu-id="0329c-138">The default value is 65,536 bytes.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="0329c-139">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span><span class="sxs-lookup"><span data-stu-id="0329c-139">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="0329c-140">The sender receives a SOAP fault if the message is too large for the receiver.</span><span class="sxs-lookup"><span data-stu-id="0329c-140">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="0329c-141">The receiver drops the message and creates an entry of the event in the trace log.</span><span class="sxs-lookup"><span data-stu-id="0329c-141">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="0329c-142">The default is 65,536 bytes.</span><span class="sxs-lookup"><span data-stu-id="0329c-142">The default is 65,536 bytes.</span></span>|  
|`messageEncoding`|<span data-ttu-id="0329c-143">Defines the encoder used to encode the SOAP message.</span><span class="sxs-lookup"><span data-stu-id="0329c-143">Defines the encoder used to encode the SOAP message.</span></span> <span data-ttu-id="0329c-144">Valid values include the following:</span><span class="sxs-lookup"><span data-stu-id="0329c-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="0329c-145">-   Text: Use a text message encoder.</span><span class="sxs-lookup"><span data-stu-id="0329c-145">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="0329c-146">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span><span class="sxs-lookup"><span data-stu-id="0329c-146">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="0329c-147">The default is Text.</span><span class="sxs-lookup"><span data-stu-id="0329c-147">The default is Text.</span></span> <span data-ttu-id="0329c-148">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="0329c-148">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="0329c-149">A string that contains the configuration name of the binding.</span><span class="sxs-lookup"><span data-stu-id="0329c-149">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="0329c-150">This value should be unique among bindings of the same type.</span><span class="sxs-lookup"><span data-stu-id="0329c-150">This value should be unique among bindings of the same type.</span></span> <span data-ttu-id="0329c-151">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span><span class="sxs-lookup"><span data-stu-id="0329c-151">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="0329c-152">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="0329c-152">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="0329c-153">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span><span class="sxs-lookup"><span data-stu-id="0329c-153">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="0329c-154">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="0329c-154">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0329c-155">The default is 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="0329c-155">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="0329c-156">A URI that contains the address of the HTTP proxy.</span><span class="sxs-lookup"><span data-stu-id="0329c-156">A URI that contains the address of the HTTP proxy.</span></span> <span data-ttu-id="0329c-157">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span><span class="sxs-lookup"><span data-stu-id="0329c-157">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span></span> <span data-ttu-id="0329c-158">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="0329c-158">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="0329c-159">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span><span class="sxs-lookup"><span data-stu-id="0329c-159">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="0329c-160">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="0329c-160">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0329c-161">The default is 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="0329c-161">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="0329c-162">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span><span class="sxs-lookup"><span data-stu-id="0329c-162">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="0329c-163">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="0329c-163">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0329c-164">The default is 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="0329c-164">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="0329c-165">Sets the character set encoding to be used for emitting messages on the binding.</span><span class="sxs-lookup"><span data-stu-id="0329c-165">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="0329c-166">Valid values include the following:</span><span class="sxs-lookup"><span data-stu-id="0329c-166">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="0329c-167">-   BigEndianUnicode: Unicode BigEndian encoding.</span><span class="sxs-lookup"><span data-stu-id="0329c-167">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="0329c-168">-   Unicode: 16-bit encoding.</span><span class="sxs-lookup"><span data-stu-id="0329c-168">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="0329c-169">-   UTF8: 8-bit encoding</span><span class="sxs-lookup"><span data-stu-id="0329c-169">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="0329c-170">The default is UTF8.</span><span class="sxs-lookup"><span data-stu-id="0329c-170">The default is UTF8.</span></span> <span data-ttu-id="0329c-171">This attribute is of type <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="0329c-171">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transferMode`|<span data-ttu-id="0329c-172">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span><span class="sxs-lookup"><span data-stu-id="0329c-172">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="0329c-173">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span><span class="sxs-lookup"><span data-stu-id="0329c-173">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span></span> <span data-ttu-id="0329c-174">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="0329c-174">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0329c-175">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0329c-175">Child Elements</span></span>  
  
|<span data-ttu-id="0329c-176">Element</span><span class="sxs-lookup"><span data-stu-id="0329c-176">Element</span></span>|<span data-ttu-id="0329c-177">Opis</span><span class="sxs-lookup"><span data-stu-id="0329c-177">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0329c-178">\<security></span><span class="sxs-lookup"><span data-stu-id="0329c-178">\<security></span></span>](security-of-basichttpbinding.md)|<span data-ttu-id="0329c-179">Defines the security settings for the binding.</span><span class="sxs-lookup"><span data-stu-id="0329c-179">Defines the security settings for the binding.</span></span> <span data-ttu-id="0329c-180">This element is of type <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="0329c-180">This element is of type <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.</span></span>|  
|<span data-ttu-id="0329c-181">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="0329c-181">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="0329c-182">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span><span class="sxs-lookup"><span data-stu-id="0329c-182">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="0329c-183">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="0329c-183">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0329c-184">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0329c-184">Parent Elements</span></span>  
  
|<span data-ttu-id="0329c-185">Element</span><span class="sxs-lookup"><span data-stu-id="0329c-185">Element</span></span>|<span data-ttu-id="0329c-186">Opis</span><span class="sxs-lookup"><span data-stu-id="0329c-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0329c-187">\<bindings></span><span class="sxs-lookup"><span data-stu-id="0329c-187">\<bindings></span></span>](bindings.md)|<span data-ttu-id="0329c-188">This element holds a collection of standard and custom bindings.</span><span class="sxs-lookup"><span data-stu-id="0329c-188">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0329c-189">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0329c-189">Remarks</span></span>  
 <span data-ttu-id="0329c-190">The BasicHttpBinding uses HTTP as the transport for sending SOAP 1.1 messages.</span><span class="sxs-lookup"><span data-stu-id="0329c-190">The BasicHttpBinding uses HTTP as the transport for sending SOAP 1.1 messages.</span></span> <span data-ttu-id="0329c-191">A service can use this binding to expose endpoints that conform to WS-I BP 1.1, such as those that ASMX clients consume.</span><span class="sxs-lookup"><span data-stu-id="0329c-191">A service can use this binding to expose endpoints that conform to WS-I BP 1.1, such as those that ASMX clients consume.</span></span> <span data-ttu-id="0329c-192">Similarly, a client can use the BasicHttpBinding to communicate with services exposing endpoints that conform to WS-I BP 1.1, such as ASMX Web services or services configured with the BasicHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="0329c-192">Similarly, a client can use the BasicHttpBinding to communicate with services exposing endpoints that conform to WS-I BP 1.1, such as ASMX Web services or services configured with the BasicHttpBinding.</span></span>  
  
 <span data-ttu-id="0329c-193">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](security-of-basichttpbinding.md) child element to a value other than `None`.</span><span class="sxs-lookup"><span data-stu-id="0329c-193">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](security-of-basichttpbinding.md) child element to a value other than `None`.</span></span> <span data-ttu-id="0329c-194">It uses a "Text" message encoding and UTF-8 text encoding by default.</span><span class="sxs-lookup"><span data-stu-id="0329c-194">It uses a "Text" message encoding and UTF-8 text encoding by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0329c-195">Przykład</span><span class="sxs-lookup"><span data-stu-id="0329c-195">Example</span></span>  
 <span data-ttu-id="0329c-196">The following example demonstrates the use of <xref:System.ServiceModel.BasicHttpBinding> that provides HTTP communication and maximum interoperability with first- and second-generation Web services.</span><span class="sxs-lookup"><span data-stu-id="0329c-196">The following example demonstrates the use of <xref:System.ServiceModel.BasicHttpBinding> that provides HTTP communication and maximum interoperability with first- and second-generation Web services.</span></span> <span data-ttu-id="0329c-197">The binding is specified in the configuration files for the client and service.</span><span class="sxs-lookup"><span data-stu-id="0329c-197">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="0329c-198">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span><span class="sxs-lookup"><span data-stu-id="0329c-198">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="0329c-199">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span><span class="sxs-lookup"><span data-stu-id="0329c-199">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="0329c-200">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span><span class="sxs-lookup"><span data-stu-id="0329c-200">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="basicHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
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
               messageEncoding="Text"
               textEncoding="utf-8"
               bypassProxyOnLocal="false"
               useDefaultWebProxy="true">
        <security mode="None" />
      </binding>
    </basicHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="example"></a><span data-ttu-id="0329c-201">Przykład</span><span class="sxs-lookup"><span data-stu-id="0329c-201">Example</span></span>  
 <span data-ttu-id="0329c-202">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span><span class="sxs-lookup"><span data-stu-id="0329c-202">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="0329c-203">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name from the binding.</span><span class="sxs-lookup"><span data-stu-id="0329c-203">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name from the binding.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="basicHttpBinding"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
      <binding hostNameComparisonMode="StrongWildcard"
               receiveTimeout="00:10:00"
               sendTimeout="00:10:00"
               openTimeout="00:10:00"
               closeTimeout="00:10:00"
               maxReceivedMessageSize="65536"
               maxBufferSize="65536"
               maxBufferPoolSize="524288"
               transferMode="Buffered"
               messageEncoding="Text"
               textEncoding="utf-8"
               bypassProxyOnLocal="false"
               useDefaultWebProxy="true">
        <security mode="None" />
      </binding>
    </basicHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
 <span data-ttu-id="0329c-204">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="0329c-204">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0329c-205">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0329c-205">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="0329c-206">Powiązania</span><span class="sxs-lookup"><span data-stu-id="0329c-206">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="0329c-207">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="0329c-207">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="0329c-208">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="0329c-208">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="0329c-209">\<binding></span><span class="sxs-lookup"><span data-stu-id="0329c-209">\<binding></span></span>](bindings.md)
