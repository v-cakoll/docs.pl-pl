---
title: WebContentTypeMapper — przykład
ms.date: 03/30/2017
ms.assetid: a4fe59e7-44d8-43c6-a1f8-40c45223adca
ms.openlocfilehash: 540e5e775cf7b2a5a5b585d98772415653fa833a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143567"
---
# <a name="webcontenttypemapper-sample"></a><span data-ttu-id="981ae-102">WebContentTypeMapper — przykład</span><span class="sxs-lookup"><span data-stu-id="981ae-102">WebContentTypeMapper Sample</span></span>
<span data-ttu-id="981ae-103">W tym przykładzie pokazano, jak mapować nowe typy zawartości do formatów treści komunikatów programu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="981ae-103">This sample demonstrates how to map new content types to Windows Communication Foundation (WCF) message body formats.</span></span>  
  
 <span data-ttu-id="981ae-104">Element <xref:System.ServiceModel.Description.WebHttpEndpoint> podłącza koder wiadomości sieci Web, który umożliwia WCF odbierać JSON, XML lub nieprzetworzone wiadomości binarne w tym samym punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="981ae-104">The <xref:System.ServiceModel.Description.WebHttpEndpoint> element plugs in the Web message encoder, which allows WCF to receive JSON, XML, or raw binary messages at the same endpoint.</span></span> <span data-ttu-id="981ae-105">Koder określa format treści wiadomości, patrząc na typ zawartości HTTP żądania.</span><span class="sxs-lookup"><span data-stu-id="981ae-105">The encoder determines the body format of the message by looking at the HTTP content-type of the request.</span></span> <span data-ttu-id="981ae-106">W tym przykładzie wprowadza <xref:System.ServiceModel.Channels.WebContentTypeMapper> klasę, która umożliwia użytkownikowi kontrolowanie mapowania między typem zawartości a formatem treści.</span><span class="sxs-lookup"><span data-stu-id="981ae-106">This sample introduces the <xref:System.ServiceModel.Channels.WebContentTypeMapper> class, which allows the user to control the mapping between content type and body format.</span></span>  
  
 <span data-ttu-id="981ae-107">WCF udostępnia zestaw mapowań domyślnych dla typów zawartości.</span><span class="sxs-lookup"><span data-stu-id="981ae-107">WCF provides a set of default mappings for content types.</span></span> <span data-ttu-id="981ae-108">Na przykład `application/json` mapuje do `text/xml` JSON i mapuje do XML.</span><span class="sxs-lookup"><span data-stu-id="981ae-108">For example, `application/json` maps to JSON and `text/xml` maps to XML.</span></span> <span data-ttu-id="981ae-109">Każdy typ zawartości, który nie jest mapowany na JSON lub XML, jest mapowany na nieprzetworzony format binarny.</span><span class="sxs-lookup"><span data-stu-id="981ae-109">Any content type that is not mapped to JSON or XML is mapped to raw binary format.</span></span>  
  
 <span data-ttu-id="981ae-110">W niektórych scenariuszach (na przykład interfejsów API w stylu wypychania) deweloper usługi nie kontroluje typu zawartości zwracanego przez klienta.</span><span class="sxs-lookup"><span data-stu-id="981ae-110">In some scenarios (for example, push-style APIs), the service developer does not control the content type returned by the client.</span></span> <span data-ttu-id="981ae-111">Na przykład klienci mogą zwracać JSON jako `text/javascript` zamiast . `application/json`</span><span class="sxs-lookup"><span data-stu-id="981ae-111">For example, clients might return JSON as `text/javascript` instead of `application/json`.</span></span> <span data-ttu-id="981ae-112">W takim przypadku deweloper usługi musi podać typ, który pochodzi od <xref:System.ServiceModel.Channels.WebContentTypeMapper> do obsługi danego typu zawartości poprawnie, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="981ae-112">In this case, the service developer must provide a type that derives from <xref:System.ServiceModel.Channels.WebContentTypeMapper> to handle the given content type correctly, as shown in the following sample code.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="981ae-113">Typ musi zastąpić <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> metodę.</span><span class="sxs-lookup"><span data-stu-id="981ae-113">The type must override the <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> method.</span></span> <span data-ttu-id="981ae-114">Metoda musi ocenić `contentType` argument i zwrócić jedną <xref:System.ServiceModel.Channels.WebContentFormat.Json> <xref:System.ServiceModel.Channels.WebContentFormat.Xml>z <xref:System.ServiceModel.Channels.WebContentFormat.Raw>następujących <xref:System.ServiceModel.Channels.WebContentFormat.Default>wartości: , , , lub .</span><span class="sxs-lookup"><span data-stu-id="981ae-114">The method must evaluate the `contentType` argument and return one of the following values: <xref:System.ServiceModel.Channels.WebContentFormat.Json>, <xref:System.ServiceModel.Channels.WebContentFormat.Xml>, <xref:System.ServiceModel.Channels.WebContentFormat.Raw>, or <xref:System.ServiceModel.Channels.WebContentFormat.Default>.</span></span> <span data-ttu-id="981ae-115">Powrót <xref:System.ServiceModel.Channels.WebContentFormat.Default> defers do domyślnych mapowania kodera wiadomości sieci Web.</span><span class="sxs-lookup"><span data-stu-id="981ae-115">Returning <xref:System.ServiceModel.Channels.WebContentFormat.Default> defers to the default Web message encoder mappings.</span></span> <span data-ttu-id="981ae-116">W poprzednim przykładowym `text/javascript` kodzie typ zawartości jest mapowany na JSON, a wszystkie inne mapowania pozostają niezmienione.</span><span class="sxs-lookup"><span data-stu-id="981ae-116">In the previous sample code, the `text/javascript` content type is mapped to JSON, and all other mappings remain unchanged.</span></span>  
  
 <span data-ttu-id="981ae-117">Aby użyć `JsonContentTypeMapper` tej klasy, użyj następujących elementów w witrynie Web.config:</span><span class="sxs-lookup"><span data-stu-id="981ae-117">To use the `JsonContentTypeMapper` class, use the following in your Web.config:</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <standardEndpoint name="" contentTypeMapper="Microsoft.Samples.WebContentTypeMapper.JsonContentTypeMapper, JsonContentTypeMapper, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="981ae-118">Aby sprawdzić wymagania dotyczące korzystania z JsonContentTypeMapper, usuń atrybut contentTypeMapper z powyższego pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="981ae-118">To verify the requirement for using the JsonContentTypeMapper, remove the contentTypeMapper attribute from the above configuration file.</span></span> <span data-ttu-id="981ae-119">Strona klienta nie można załadować `text/javascript` podczas próby wysłania zawartości JSON.</span><span class="sxs-lookup"><span data-stu-id="981ae-119">The client page fails to load when attempting to use `text/javascript` to send JSON content.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="981ae-120">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="981ae-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="981ae-121">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="981ae-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="981ae-122">Tworzenie rozwiązania WebContentTypeMapperSample.sln zgodnie z opisem w [tworzenie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="981ae-122">Build the solution WebContentTypeMapperSample.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="981ae-123">Przejdź `http://localhost/ServiceModelSamples/JCTMClientPage.htm` do (nie otwieraj pliku JCTMClientPage.htm w przeglądarce z poziomu katalogu projektu).</span><span class="sxs-lookup"><span data-stu-id="981ae-123">Navigate to `http://localhost/ServiceModelSamples/JCTMClientPage.htm` (do not open JCTMClientPage.htm in the browser from within the project directory).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="981ae-124">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="981ae-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="981ae-125">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="981ae-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="981ae-126">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="981ae-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="981ae-127">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="981ae-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Ajax\WebContentTypeMapper`  
