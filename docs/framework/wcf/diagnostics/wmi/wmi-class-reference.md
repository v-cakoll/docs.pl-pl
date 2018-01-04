---
title: Informacje o klasach WMI
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b95a51f5-8251-4619-ae05-7de88cb90f9a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0e221c8197b9713dd5f4e35114ada3c63f4978ef
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="wmi-class-reference"></a><span data-ttu-id="c91c3-102">Informacje o klasach WMI</span><span class="sxs-lookup"><span data-stu-id="c91c3-102">WMI Class Reference</span></span>
<span data-ttu-id="c91c3-103">Ta sekcja zawiera listę klas usługi WMI udostępnianych przez [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] dostawcy WMI.</span><span class="sxs-lookup"><span data-stu-id="c91c3-103">This section lists all the WMI classes exposed by the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] WMI provider.</span></span>  
  
## <a name="accessing-wmi-instances"></a><span data-ttu-id="c91c3-104">Uzyskiwanie dostępu do wystąpienia usługi WMI</span><span class="sxs-lookup"><span data-stu-id="c91c3-104">Accessing WMI Instances</span></span>  
 <span data-ttu-id="c91c3-105">Wszystkie klasy odwołanie do obiektu WMI na liście nie można bezpośrednio utworzyć wystąpienia, z wyjątkiem usługi, elementu AppDomain, kontrakt, ServiceAppDomain, ServiceToEndpointAssociation i punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="c91c3-105">All the classes listed in the WMI Object Reference cannot be directly instantiated, except for Service, AppDomain, Contract, ServiceAppDomain, ServiceToEndpointAssociation and Endpoint.</span></span> <span data-ttu-id="c91c3-106">Aby uzyskać dostęp do innych wystąpień, można uzyskać dostęp do właściwości klasy opisane powyżej najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="c91c3-106">To access other instances, you can access the properties of the previously mentioned top level classes.</span></span> <span data-ttu-id="c91c3-107">Można na przykład dostęp do wystąpienia klasy TransportBindingElement z punktu końcowego wystąpienia -> -> BindingElements powiązania.</span><span class="sxs-lookup"><span data-stu-id="c91c3-107">For example, you can access the TransportBindingElement instance from the Endpoint instance -> Binding -> BindingElements.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c91c3-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="c91c3-108">In This Section</span></span>  
 [<span data-ttu-id="c91c3-109">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="c91c3-109">ActivityTransfer</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/activitytransfer.md)  
  
 [<span data-ttu-id="c91c3-110">AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="c91c3-110">AppDomainInfo</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md)  
  
 [<span data-ttu-id="c91c3-111">AspNetCompatibilityRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="c91c3-111">AspNetCompatibilityRequirementsAttribute</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/aspnetcompatibilityrequirementsattribute.md)  
  
 [<span data-ttu-id="c91c3-112">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="c91c3-112">AsymmetricSecurityBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/asymmetricsecuritybindingelement.md)  
  
 <span data-ttu-id="c91c3-113">"Zachowanie class"</span><span class="sxs-lookup"><span data-stu-id="c91c3-113">"Behavior class"</span></span>  
  
 [<span data-ttu-id="c91c3-114">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="c91c3-114">BinaryMessageEncodingBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/binarymessageencodingbindingelement.md)  
  
 [<span data-ttu-id="c91c3-115">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="c91c3-115">Binding</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/binding.md)  
  
 [<span data-ttu-id="c91c3-116">BindingElement</span><span class="sxs-lookup"><span data-stu-id="c91c3-116">BindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/bindingelement.md)  
  
 [<span data-ttu-id="c91c3-117">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="c91c3-117">CallbackBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/callbackbehavior.md)  
  
 [<span data-ttu-id="c91c3-118">Klasa Channel</span><span class="sxs-lookup"><span data-stu-id="c91c3-118">Channel class</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/channel-class.md)  
  
 [<span data-ttu-id="c91c3-119">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="c91c3-119">ChannelPoolSettings</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/channelpoolsettings.md)  
  
 [<span data-ttu-id="c91c3-120">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="c91c3-120">ClientCredentials</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/clientcredentials.md)  
  
 [<span data-ttu-id="c91c3-121">ClientViaBehavior</span><span class="sxs-lookup"><span data-stu-id="c91c3-121">ClientViaBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md)  
  
 [<span data-ttu-id="c91c3-122">CompositeDuplexBindingElement</span><span class="sxs-lookup"><span data-stu-id="c91c3-122">CompositeDuplexBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/compositeduplexbindingelement.md)  
  
 [<span data-ttu-id="c91c3-123">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="c91c3-123">ConnectionOrientedTransportBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/connectionorientedtransportbindingelement.md)  
  
 [<span data-ttu-id="c91c3-124">Kontrakt</span><span class="sxs-lookup"><span data-stu-id="c91c3-124">Contract</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/contract.md)  
  
 [<span data-ttu-id="c91c3-125">CustomBindingElement</span><span class="sxs-lookup"><span data-stu-id="c91c3-125">CustomBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/custombindingelement.md)  
  
 [<span data-ttu-id="c91c3-126">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="c91c3-126">DeliveryRequirementsAttribute</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/deliveryrequirementsattribute.md)  
  
 [<span data-ttu-id="c91c3-127">Punkt końcowy</span><span class="sxs-lookup"><span data-stu-id="c91c3-127">Endpoint</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md)  
  
 [<span data-ttu-id="c91c3-128">HttpsTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="c91c3-128">HttpsTransportBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/httpstransportbindingelement.md)  
  
 [<span data-ttu-id="c91c3-129">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="c91c3-129">HttpTransportBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/httptransportbindingelement.md)  
  
 [<span data-ttu-id="c91c3-130">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="c91c3-130">LocalServiceSecuritySettings</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/localservicesecuritysettings.md)  
  
 [<span data-ttu-id="c91c3-131">MatchAllEndpointBehavior</span><span class="sxs-lookup"><span data-stu-id="c91c3-131">MatchAllEndpointBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/matchallendpointbehavior.md)  
  
 [<span data-ttu-id="c91c3-132">MessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="c91c3-132">MessageEncodingBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/messageencodingbindingelement.md)  
  
 [<span data-ttu-id="c91c3-133">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="c91c3-133">MsmqBindingElementBase</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/msmqbindingelementbase.md)  
  
 [<span data-ttu-id="c91c3-134">MsmqIntegrationBindingElement</span><span class="sxs-lookup"><span data-stu-id="c91c3-134">MsmqIntegrationBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/msmqintegrationbindingelement.md)  
  
 [<span data-ttu-id="c91c3-135">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="c91c3-135">MsmqTransportBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/msmqtransportbindingelement.md)  
  
 [<span data-ttu-id="c91c3-136">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="c91c3-136">MtomMessageEncodingBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/mtommessageencodingbindingelement.md)  
  
 [<span data-ttu-id="c91c3-137">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="c91c3-137">MustUnderstandBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/mustunderstandbehavior.md)  
  
 [<span data-ttu-id="c91c3-138">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="c91c3-138">NamedPipeConnectionPoolSettings</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/namedpipeconnectionpoolsettings.md)  
  
 [<span data-ttu-id="c91c3-139">NamedPipeTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="c91c3-139">NamedPipeTransportBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/namedpipetransportbindingelement.md)  
  
 [<span data-ttu-id="c91c3-140">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="c91c3-140">OneWayBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/onewaybindingelement.md)  
  
 <span data-ttu-id="c91c3-141">"Operacji class"</span><span class="sxs-lookup"><span data-stu-id="c91c3-141">"Operation class"</span></span>  
  
 [<span data-ttu-id="c91c3-142">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="c91c3-142">OperationBehaviorAttribute</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/operationbehaviorattribute.md)  
  
 [<span data-ttu-id="c91c3-143">PeerCustomResolverBindingElement</span><span class="sxs-lookup"><span data-stu-id="c91c3-143">PeerCustomResolverBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/peercustomresolverbindingelement.md)  
  
 [<span data-ttu-id="c91c3-144">PeerResolverBindingElement</span><span class="sxs-lookup"><span data-stu-id="c91c3-144">PeerResolverBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/peerresolverbindingelement.md)  
  
 [<span data-ttu-id="c91c3-145">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="c91c3-145">PeerSecuritySettings</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/peersecuritysettings.md)  
  
 [<span data-ttu-id="c91c3-146">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="c91c3-146">PeerTransportBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/peertransportbindingelement.md)  
  
 [<span data-ttu-id="c91c3-147">PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="c91c3-147">PeerTransportSecuritySettings</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/peertransportsecuritysettings.md)  
  
 [<span data-ttu-id="c91c3-148">PnrpPeerResolverBindingElement</span><span class="sxs-lookup"><span data-stu-id="c91c3-148">PnrpPeerResolverBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/pnrppeerresolverbindingelement.md)  
  
 [<span data-ttu-id="c91c3-149">PrivacyNoticeBindingElement</span><span class="sxs-lookup"><span data-stu-id="c91c3-149">PrivacyNoticeBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/privacynoticebindingelement.md)  
  
 [<span data-ttu-id="c91c3-150">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="c91c3-150">ReliableSessionBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/reliablesessionbindingelement.md)  
  
 [<span data-ttu-id="c91c3-151">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="c91c3-151">SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/securitybindingelement.md)  
  
 [<span data-ttu-id="c91c3-152">Usługa</span><span class="sxs-lookup"><span data-stu-id="c91c3-152">Service</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/service.md)  
  
 [<span data-ttu-id="c91c3-153">ServiceAppDomain</span><span class="sxs-lookup"><span data-stu-id="c91c3-153">ServiceAppDomain</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/serviceappdomain.md)  
  
 [<span data-ttu-id="c91c3-154">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="c91c3-154">ServiceAuthorizationBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/serviceauthorizationbehavior.md)  
  
 [<span data-ttu-id="c91c3-155">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="c91c3-155">ServiceBehaviorAttribute</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/servicebehaviorattribute.md)  
  
 [<span data-ttu-id="c91c3-156">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="c91c3-156">ServiceCredentials</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/servicecredentials.md)  
  
 [<span data-ttu-id="c91c3-157">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="c91c3-157">ServiceDebugBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/servicedebugbehavior.md)  
  
 [<span data-ttu-id="c91c3-158">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="c91c3-158">ServiceMetadataBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/servicemetadatabehavior.md)  
  
 [<span data-ttu-id="c91c3-159">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="c91c3-159">ServiceSecurityAuditBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/servicesecurityauditbehavior.md)  
  
 [<span data-ttu-id="c91c3-160">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="c91c3-160">ServiceThrottlingBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/servicethrottlingbehavior.md)  
  
 [<span data-ttu-id="c91c3-161">ServiceTimeoutsBehavior</span><span class="sxs-lookup"><span data-stu-id="c91c3-161">ServiceTimeoutsBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/servicetimeoutsbehavior.md)  
  
 [<span data-ttu-id="c91c3-162">ServiceToEndpointAssociation</span><span class="sxs-lookup"><span data-stu-id="c91c3-162">ServiceToEndpointAssociation</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/servicetoendpointassociation.md)  
  
 [<span data-ttu-id="c91c3-163">SslStreamSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="c91c3-163">SslStreamSecurityBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/sslstreamsecuritybindingelement.md)  
  
 [<span data-ttu-id="c91c3-164">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="c91c3-164">SymmetricSecurityBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/symmetricsecuritybindingelement.md)  
  
 [<span data-ttu-id="c91c3-165">SynchronousReceiveBehavior</span><span class="sxs-lookup"><span data-stu-id="c91c3-165">SynchronousReceiveBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/synchronousreceivebehavior.md)  
  
 [<span data-ttu-id="c91c3-166">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="c91c3-166">TcpConnectionPoolSettings</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/tcpconnectionpoolsettings.md)  
  
 [<span data-ttu-id="c91c3-167">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="c91c3-167">TcpTransportBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/tcptransportbindingelement.md)  
  
 [<span data-ttu-id="c91c3-168">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="c91c3-168">TextMessageEncodingBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/textmessageencodingbindingelement.md)  
  
 [<span data-ttu-id="c91c3-169">TraceListener</span><span class="sxs-lookup"><span data-stu-id="c91c3-169">TraceListener</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/tracelistener.md)  
  
 [<span data-ttu-id="c91c3-170">TraceListenerArgument</span><span class="sxs-lookup"><span data-stu-id="c91c3-170">TraceListenerArgument</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/tracelistenerargument.md)  
  
 [<span data-ttu-id="c91c3-171">TransactedBatchingBehavior</span><span class="sxs-lookup"><span data-stu-id="c91c3-171">TransactedBatchingBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/transactedbatchingbehavior.md)  
  
 [<span data-ttu-id="c91c3-172">TransactionFlowAttribute</span><span class="sxs-lookup"><span data-stu-id="c91c3-172">TransactionFlowAttribute</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/transactionflowattribute.md)  
  
 [<span data-ttu-id="c91c3-173">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="c91c3-173">TransactionFlowBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/transactionflowbindingelement.md)  
  
 [<span data-ttu-id="c91c3-174">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="c91c3-174">TransportBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/transportbindingelement.md)  
  
 [<span data-ttu-id="c91c3-175">TransportSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="c91c3-175">TransportSecurityBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/transportsecuritybindingelement.md)  
  
 [<span data-ttu-id="c91c3-176">UseManagedPresentationBindingElement</span><span class="sxs-lookup"><span data-stu-id="c91c3-176">UseManagedPresentationBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/usemanagedpresentationbindingelement.md)  
  
 [<span data-ttu-id="c91c3-177">WindowsStreamSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="c91c3-177">WindowsStreamSecurityBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/windowsstreamsecuritybindingelement.md)  
  
 [<span data-ttu-id="c91c3-178">WSAT_TraceEvent</span><span class="sxs-lookup"><span data-stu-id="c91c3-178">WSAT_TraceEvent</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/wsat-traceevent.md)  
  
 [<span data-ttu-id="c91c3-179">WSAT_TraceProvider</span><span class="sxs-lookup"><span data-stu-id="c91c3-179">WSAT_TraceProvider</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/wsat-traceprovider.md)  
  
 [<span data-ttu-id="c91c3-180">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="c91c3-180">WSAT_TraceRecord</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/wsat-tracerecord.md)  
  
 [<span data-ttu-id="c91c3-181">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="c91c3-181">XmlDictionaryReaderQuotas</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/xmldictionaryreaderquotas.md)  
  
 [<span data-ttu-id="c91c3-182">XmlSerializerOperationBehavior</span><span class="sxs-lookup"><span data-stu-id="c91c3-182">XmlSerializerOperationBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/xmlserializeroperationbehavior.md)
