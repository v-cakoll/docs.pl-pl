---
title: 'Instrukcje: Dynamiczne uzyskiwanie metadanych powiązania przy użyciu klasy MetadataResolver'
ms.date: 03/30/2017
ms.assetid: 56ffcb99-fff0-4479-aca0-e3909009f605
ms.openlocfilehash: 98fe4977f270b008c51039af19261ca86b8d6642
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601130"
---
# <a name="how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically"></a><span data-ttu-id="69a96-102">Instrukcje: Dynamiczne uzyskiwanie metadanych powiązania przy użyciu klasy MetadataResolver</span><span class="sxs-lookup"><span data-stu-id="69a96-102">How to: Use MetadataResolver to Obtain Binding Metadata Dynamically</span></span>
<span data-ttu-id="69a96-103">W tym temacie pokazano, jak używać <xref:System.ServiceModel.Description.MetadataResolver> klasy do dynamicznego uzyskiwania metadanych powiązań.</span><span class="sxs-lookup"><span data-stu-id="69a96-103">This topic shows you how to use the <xref:System.ServiceModel.Description.MetadataResolver> class to dynamically obtain binding metadata.</span></span>  
  
### <a name="to-dynamically-obtain-binding-metadata"></a><span data-ttu-id="69a96-104">Aby dynamicznie uzyskać metadane powiązania</span><span class="sxs-lookup"><span data-stu-id="69a96-104">To dynamically obtain binding metadata</span></span>  
  
1. <span data-ttu-id="69a96-105">Utwórz <xref:System.ServiceModel.EndpointAddress> obiekt z adresem punktu końcowego metadanych.</span><span class="sxs-lookup"><span data-stu-id="69a96-105">Create an <xref:System.ServiceModel.EndpointAddress> object with the address of the metadata endpoint.</span></span>  
  
    ```csharp
    EndpointAddress metaAddress  
      = new EndpointAddress(new Uri("http://localhost:8080/SampleService/mex"));  
    ```  
  
2. <span data-ttu-id="69a96-106">Wywołanie <xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29> , które przekazuje typ usługi i adres punktu końcowego metadanych.</span><span class="sxs-lookup"><span data-stu-id="69a96-106">Call <xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29>, which passes in the service type and the metadata endpoint address.</span></span> <span data-ttu-id="69a96-107">Zwraca kolekcję punktów końcowych, które implementują określony kontrakt.</span><span class="sxs-lookup"><span data-stu-id="69a96-107">This returns a collection of endpoints that implement the specified contract.</span></span> <span data-ttu-id="69a96-108">Tylko informacje o powiązaniu są importowane z metadanych; Informacje o kontrakcie nie zostały zaimportowane.</span><span class="sxs-lookup"><span data-stu-id="69a96-108">Only binding information is imported from the metadata; contract information is not imported.</span></span> <span data-ttu-id="69a96-109">Zamiast tego użyto dostarczonej umowy.</span><span class="sxs-lookup"><span data-stu-id="69a96-109">The supplied contract is used instead.</span></span>  
  
    ```csharp  
    ServiceEndpointCollection endpoints = MetadataResolver.Resolve(typeof(SampleServiceClient),metaAddress);  
    ```  
  
3. <span data-ttu-id="69a96-110">Następnie można wykonać iterację kolekcji punktów końcowych usługi w celu wyodrębnienia potrzebnych informacji o powiązaniach.</span><span class="sxs-lookup"><span data-stu-id="69a96-110">You can then iterate through the collection of service endpoints to extract the binding information you need.</span></span> <span data-ttu-id="69a96-111">Poniższy kod wykonuje iterację punktów końcowych, tworzy obiekt klienta usługi, który przekazuje powiązanie i adres skojarzony z bieżącym punktem końcowym, a następnie wywołuje metodę w usłudze.</span><span class="sxs-lookup"><span data-stu-id="69a96-111">The following code iterates through the endpoints, creates a service client object that passes in the binding and address associated with the current endpoint, and then calls a method on the service.</span></span>  
  
    ```csharp  
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
  
## <a name="see-also"></a><span data-ttu-id="69a96-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69a96-112">See also</span></span>

- [<span data-ttu-id="69a96-113">Metadane</span><span class="sxs-lookup"><span data-stu-id="69a96-113">Metadata</span></span>](metadata.md)
