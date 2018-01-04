---
title: "WebContentTypeMapper — przykład"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4fe59e7-44d8-43c6-a1f8-40c45223adca
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 34adf191d3edbff33fe989cf036c32104a6754ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="webcontenttypemapper-sample"></a><span data-ttu-id="3bdb9-102">WebContentTypeMapper — przykład</span><span class="sxs-lookup"><span data-stu-id="3bdb9-102">WebContentTypeMapper Sample</span></span>
<span data-ttu-id="3bdb9-103">W tym przykładzie pokazano, jak nowe typy zawartości do mapowania [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] formatów treści komunikatu.</span><span class="sxs-lookup"><span data-stu-id="3bdb9-103">This sample demonstrates how to map new content types to [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] message body formats.</span></span>  
  
 <span data-ttu-id="3bdb9-104"><xref:System.ServiceModel.Description.WebHttpEndpoint> Element podłącza kodera wiadomości w sieci Web, dzięki czemu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] do odbierania JSON, XML lub raw komunikatów binarnych w tym samym punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="3bdb9-104">The <xref:System.ServiceModel.Description.WebHttpEndpoint> element plugs in the Web message encoder, which allows [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] to receive JSON, XML, or raw binary messages at the same endpoint.</span></span> <span data-ttu-id="3bdb9-105">Koder Określa format treści wiadomości, analizując typ zawartości HTTP żądania.</span><span class="sxs-lookup"><span data-stu-id="3bdb9-105">The encoder determines the body format of the message by looking at the HTTP content-type of the request.</span></span> <span data-ttu-id="3bdb9-106">W tym przykładzie przedstawiono <xref:System.ServiceModel.Channels.WebContentTypeMapper> klasy, która umożliwia użytkownikowi na kontrolowanie mapowanie między typu zawartości i formatu treści.</span><span class="sxs-lookup"><span data-stu-id="3bdb9-106">This sample introduces the <xref:System.ServiceModel.Channels.WebContentTypeMapper> class, which allows the user to control the mapping between content type and body format.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="3bdb9-107">zawiera zestaw domyślnych mapowań typów zawartości.</span><span class="sxs-lookup"><span data-stu-id="3bdb9-107"> provides a set of default mappings for content types.</span></span> <span data-ttu-id="3bdb9-108">Na przykład `application/json` mapy do formatu JSON i `text/xml` mapy do pliku XML.</span><span class="sxs-lookup"><span data-stu-id="3bdb9-108">For example, `application/json` maps to JSON and `text/xml` maps to XML.</span></span> <span data-ttu-id="3bdb9-109">Typ zawartości, który nie jest zamapowany na formacie JSON i XML jest zamapowany na format binarny raw.</span><span class="sxs-lookup"><span data-stu-id="3bdb9-109">Any content type that is not mapped to JSON or XML is mapped to raw binary format.</span></span>  
  
 <span data-ttu-id="3bdb9-110">W niektórych scenariuszach (na przykład stylu wypychania API) dewelopera usługi nie kontroluje zawartości typ zwracany przez klienta.</span><span class="sxs-lookup"><span data-stu-id="3bdb9-110">In some scenarios (for example, push-style APIs), the service developer does not control the content type returned by the client.</span></span> <span data-ttu-id="3bdb9-111">Na przykład klienci mogą zwracać dane JSON jako `text/javascript` zamiast `application/json`.</span><span class="sxs-lookup"><span data-stu-id="3bdb9-111">For example, clients might return JSON as `text/javascript` instead of `application/json`.</span></span> <span data-ttu-id="3bdb9-112">W takim przypadku podać typu pochodzącego od dewelopera usługi <xref:System.ServiceModel.Channels.WebContentTypeMapper> poprawnie, jak pokazano w poniższym kodzie próbki obsługi danego typu zawartości.</span><span class="sxs-lookup"><span data-stu-id="3bdb9-112">In this case, the service developer must provide a type that derives from <xref:System.ServiceModel.Channels.WebContentTypeMapper> to handle the given content type correctly, as shown in the following sample code.</span></span>  
  
```  
public class JsonContentTypeMapper : WebContentTypeMapper  
{  
    public override WebContentFormat  
               GetMessageFormatForContentType(string contentType)  
    {  
        if (contentType == "text/javascript")  
        {  
            return WebContentFormat.Json;  
        }  
        else  
        {  
            return WebContentFormat.Default;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="3bdb9-113">Typ musi zastąpić <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> metody.</span><span class="sxs-lookup"><span data-stu-id="3bdb9-113">The type must override the <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> method.</span></span> <span data-ttu-id="3bdb9-114">Należy ocenić metodę `contentType` argumentów i zwracane jednej z następujących wartości: <xref:System.ServiceModel.Channels.WebContentFormat.Json>, <xref:System.ServiceModel.Channels.WebContentFormat.Xml>, <xref:System.ServiceModel.Channels.WebContentFormat.Raw>, lub <xref:System.ServiceModel.Channels.WebContentFormat.Default>.</span><span class="sxs-lookup"><span data-stu-id="3bdb9-114">The method must evaluate the `contentType` argument and return one of the following values: <xref:System.ServiceModel.Channels.WebContentFormat.Json>, <xref:System.ServiceModel.Channels.WebContentFormat.Xml>, <xref:System.ServiceModel.Channels.WebContentFormat.Raw>, or <xref:System.ServiceModel.Channels.WebContentFormat.Default>.</span></span> <span data-ttu-id="3bdb9-115">Zwracanie <xref:System.ServiceModel.Channels.WebContentFormat.Default> różni się do domyślnych mapowań kodera wiadomości w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="3bdb9-115">Returning <xref:System.ServiceModel.Channels.WebContentFormat.Default> defers to the default Web message encoder mappings.</span></span> <span data-ttu-id="3bdb9-116">W poprzednim przykładowym kodzie `text/javascript` zawartości typu jest mapowana do formatu JSON, a wszystkie inne mapowania pozostają niezmienione.</span><span class="sxs-lookup"><span data-stu-id="3bdb9-116">In the previous sample code, the `text/javascript` content type is mapped to JSON, and all other mappings remain unchanged.</span></span>  
  
 <span data-ttu-id="3bdb9-117">Aby użyć `JsonContentTypeMapper` klasy, należy użyć następującego w pliku Web.config:</span><span class="sxs-lookup"><span data-stu-id="3bdb9-117">To use the `JsonContentTypeMapper` class, use the following in your Web.config:</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <standardEndpoint name="" contentTypeMapper="Microsoft.Samples.WebContentTypeMapper.JsonContentTypeMapper, JsonContentTypeMapper, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="3bdb9-118">Aby sprawdzić wymagania dotyczące korzystania z JsonContentTypeMapper, usuń atrybut zamapował z powyższych pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3bdb9-118">To verify the requirement for using the JsonContentTypeMapper, remove the contentTypeMapper attribute from the above configuration file.</span></span> <span data-ttu-id="3bdb9-119">Strona klienta nie udało się załadować podczas próby użycia `text/javascript` do wysyłania zawartości JSON.</span><span class="sxs-lookup"><span data-stu-id="3bdb9-119">The client page fails to load when attempting to use `text/javascript` to send JSON content.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3bdb9-120">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="3bdb9-120">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="3bdb9-121">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3bdb9-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="3bdb9-122">Skompiluj rozwiązanie WebContentTypeMapperSample.sln zgodnie z opisem w [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3bdb9-122">Build the solution WebContentTypeMapperSample.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="3bdb9-123">Przejdź do http://localhost/ServiceModelSamples/JCTMClientPage.htm (nie należy otwierać JCTMClientPage.htm w przeglądarce z katalogu projektu).</span><span class="sxs-lookup"><span data-stu-id="3bdb9-123">Navigate to http://localhost/ServiceModelSamples/JCTMClientPage.htm (do not open JCTMClientPage.htm in the browser from within the project directory).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3bdb9-124">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="3bdb9-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3bdb9-125">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="3bdb9-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3bdb9-126">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="3bdb9-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3bdb9-127">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="3bdb9-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Ajax\WebContentTypeMapper`  
  
## <a name="see-also"></a><span data-ttu-id="3bdb9-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3bdb9-128">See Also</span></span>
