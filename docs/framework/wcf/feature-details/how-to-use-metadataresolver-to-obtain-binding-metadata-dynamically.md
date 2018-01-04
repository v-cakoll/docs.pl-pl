---
title: "Instrukcje: Dynamiczne uzyskiwanie metadanych powiązania przy użyciu klasy MetadataResolver"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56ffcb99-fff0-4479-aca0-e3909009f605
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 640d053e0186766e5acdbef692f4e7fae59337b0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically"></a><span data-ttu-id="2389b-102">Instrukcje: Dynamiczne uzyskiwanie metadanych powiązania przy użyciu klasy MetadataResolver</span><span class="sxs-lookup"><span data-stu-id="2389b-102">How to: Use MetadataResolver to Obtain Binding Metadata Dynamically</span></span>
<span data-ttu-id="2389b-103">W tym temacie przedstawiono sposób użycia <xref:System.ServiceModel.Description.MetadataResolver> klasy dynamiczne uzyskiwanie metadanych powiązania.</span><span class="sxs-lookup"><span data-stu-id="2389b-103">This topic shows you how to use the <xref:System.ServiceModel.Description.MetadataResolver> class to dynamically obtain binding metadata.</span></span>  
  
### <a name="to-dynamically-obtain-binding-metadata"></a><span data-ttu-id="2389b-104">Aby dynamiczne uzyskiwanie metadanych powiązania</span><span class="sxs-lookup"><span data-stu-id="2389b-104">To dynamically obtain binding metadata</span></span>  
  
1.  <span data-ttu-id="2389b-105">Utwórz <xref:System.ServiceModel.EndpointAddress> obiektu adres punktu końcowego metadanych.</span><span class="sxs-lookup"><span data-stu-id="2389b-105">Create an <xref:System.ServiceModel.EndpointAddress> object with the address of the metadata endpoint.</span></span>  
  
    ```  
    EndpointAddress metaAddress  
      = new EndpointAddress(new   Uri("http://localhost:8080/SampleService/mex"));  
    ```  
  
2.  <span data-ttu-id="2389b-106">Wywołanie <xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29>, która przechodzi w typu usługi i adres punktu końcowego metadanych.</span><span class="sxs-lookup"><span data-stu-id="2389b-106">Call <xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29>, which passes in the service type and the metadata endpoint address.</span></span> <span data-ttu-id="2389b-107">To zwraca kolekcję punktów końcowych, które implementuje kontrakt określony.</span><span class="sxs-lookup"><span data-stu-id="2389b-107">This returns a collection of endpoints that implement the specified contract.</span></span> <span data-ttu-id="2389b-108">Tylko informacje o powiązaniu została zaimportowana z metadanymi; kontrakt informacji nie zostanie zaimportowany.</span><span class="sxs-lookup"><span data-stu-id="2389b-108">Only binding information is imported from the metadata; contract information is not imported.</span></span> <span data-ttu-id="2389b-109">Zamiast niego jest używana dostarczony kontraktu.</span><span class="sxs-lookup"><span data-stu-id="2389b-109">The supplied contract is used instead.</span></span>  
  
    ```  
    ServiceEndpointCollection endpoints = MetadataResolver.Resolve(typeof(SampleServiceClient),metaAddress);  
    ```  
  
3.  <span data-ttu-id="2389b-110">Następnie można wykonać iterację kolekcji punktów końcowych usługi, aby wyodrębnić informacje o powiązaniu, które są potrzebne.</span><span class="sxs-lookup"><span data-stu-id="2389b-110">You can then iterate through the collection of service endpoints to extract the binding information you need.</span></span> <span data-ttu-id="2389b-111">Poniższy kod iteruje punkty końcowe, tworzy obiekt klienta usługi, który przekazuje powiązanie i adres skojarzony z bieżącym punktem końcowym i następnie wywołuje metodę dla usługi.</span><span class="sxs-lookup"><span data-stu-id="2389b-111">The following code iterates through the endpoints, creates a service client object that passes in the binding and address associated with the current endpoint, and then calls a method on the service.</span></span>  
  
    ```  
    foreach (ServiceEndpoint point in endpoints)  
    {  
       if (point != null)  
       {  
          // Create a new wcfClient using retrieved endpoints.  
          using (wcfClient = new SampleServiceClient(point.Binding, point.Address))  
          {  
             Console.WriteLine(  
               wcfClient.SampleMethod("Client used the "  
               + point.Address.ToString() + " address."));  
          }  
      }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2389b-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2389b-112">See Also</span></span>  
 [<span data-ttu-id="2389b-113">Metadane</span><span class="sxs-lookup"><span data-stu-id="2389b-113">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)
