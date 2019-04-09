---
title: 'Instrukcje: dynamiczne uzyskiwanie metadanych wiązania przy użyciu klasy MetadataResolver'
ms.date: 03/30/2017
ms.assetid: 56ffcb99-fff0-4479-aca0-e3909009f605
ms.openlocfilehash: d8efe2522d17829cc42d8ed1304983f6da46fb58
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111205"
---
# <a name="how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically"></a><span data-ttu-id="30a78-102">Instrukcje: dynamiczne uzyskiwanie metadanych wiązania przy użyciu klasy MetadataResolver</span><span class="sxs-lookup"><span data-stu-id="30a78-102">How to: Use MetadataResolver to Obtain Binding Metadata Dynamically</span></span>
<span data-ttu-id="30a78-103">W tym temacie dowiesz się, jak używać <xref:System.ServiceModel.Description.MetadataResolver> klasy dynamiczne uzyskiwanie metadanych powiązania.</span><span class="sxs-lookup"><span data-stu-id="30a78-103">This topic shows you how to use the <xref:System.ServiceModel.Description.MetadataResolver> class to dynamically obtain binding metadata.</span></span>  
  
### <a name="to-dynamically-obtain-binding-metadata"></a><span data-ttu-id="30a78-104">Aby dynamiczne uzyskiwanie metadanych powiązania</span><span class="sxs-lookup"><span data-stu-id="30a78-104">To dynamically obtain binding metadata</span></span>  
  
1.  <span data-ttu-id="30a78-105">Utwórz <xref:System.ServiceModel.EndpointAddress> obiektu przy użyciu adresu punktu końcowego metadanych.</span><span class="sxs-lookup"><span data-stu-id="30a78-105">Create an <xref:System.ServiceModel.EndpointAddress> object with the address of the metadata endpoint.</span></span>  
  
    ```  
    EndpointAddress metaAddress  
      = new EndpointAddress(new   Uri("http://localhost:8080/SampleService/mex"));  
    ```  
  
2.  <span data-ttu-id="30a78-106">Wywołaj <xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29>, która przekazuje typ usługi i adres punktu końcowego metadanych.</span><span class="sxs-lookup"><span data-stu-id="30a78-106">Call <xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29>, which passes in the service type and the metadata endpoint address.</span></span> <span data-ttu-id="30a78-107">Spowoduje to zwrócenie kolekcją punktów końcowych, które implementują określonej umowy.</span><span class="sxs-lookup"><span data-stu-id="30a78-107">This returns a collection of endpoints that implement the specified contract.</span></span> <span data-ttu-id="30a78-108">Tylko informacje o powiązaniu została zaimportowana z metadanych; informacje na temat Umowy nie zostanie zaimportowany.</span><span class="sxs-lookup"><span data-stu-id="30a78-108">Only binding information is imported from the metadata; contract information is not imported.</span></span> <span data-ttu-id="30a78-109">Podany kontraktu jest używana zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="30a78-109">The supplied contract is used instead.</span></span>  
  
    ```  
    ServiceEndpointCollection endpoints = MetadataResolver.Resolve(typeof(SampleServiceClient),metaAddress);  
    ```  
  
3.  <span data-ttu-id="30a78-110">Następnie można wykonać iterację kolekcji punktów końcowych usługi, aby wyodrębnić informacje o powiązaniu, które są potrzebne.</span><span class="sxs-lookup"><span data-stu-id="30a78-110">You can then iterate through the collection of service endpoints to extract the binding information you need.</span></span> <span data-ttu-id="30a78-111">Poniższy kod wykonuje iterację przez punkty końcowe, tworzy obiekt klienta usługi, który przekazuje powiązania oraz adres skojarzony z bieżącym punktem końcowym i następnie wywołuje metodę dla usługi.</span><span class="sxs-lookup"><span data-stu-id="30a78-111">The following code iterates through the endpoints, creates a service client object that passes in the binding and address associated with the current endpoint, and then calls a method on the service.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="30a78-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="30a78-112">See also</span></span>

- [<span data-ttu-id="30a78-113">Metadane</span><span class="sxs-lookup"><span data-stu-id="30a78-113">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)
