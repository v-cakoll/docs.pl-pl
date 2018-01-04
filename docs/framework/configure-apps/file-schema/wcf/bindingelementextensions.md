---
title: '&lt;bindingElementExtensions&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb597fc0-c947-451c-afda-bf23d42f4f4d
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bc5245be9b008f4bd8021c501860d789c60c73a4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltbindingelementextensionsgt"></a><span data-ttu-id="34e8e-102">&lt;bindingElementExtensions&gt;</span><span class="sxs-lookup"><span data-stu-id="34e8e-102">&lt;bindingElementExtensions&gt;</span></span>
<span data-ttu-id="34e8e-103">Ta sekcja umożliwia zastosowanie elementu niestandardowego powiązania z maszyny lub pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="34e8e-103">This section enables the use of a custom binding element from a machine or application configuration file.</span></span> <span data-ttu-id="34e8e-104">Można dodać element niestandardowego powiązania do tej kolekcji przy użyciu `add` — słowo kluczowe i ustawienie `type` atrybut element, aby element rozszerzenia powiązania, jak również `name` atrybutu element niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="34e8e-104">You can add a custom binding element to this collection by using the `add` keyword, and setting the `type` attribute of the element to a binding element extension, as well as the `name` attribute to the custom binding element.</span></span>  
  
 <span data-ttu-id="34e8e-105">Powiązanie rozszerzeniom użytkownikowi utworzenie powiązań zdefiniowanych przez użytkownika elementy do użycia jako część niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="34e8e-105">Binding extensions enable the user to create user-defined binding elements for use as part of custom bindings.</span></span> <span data-ttu-id="34e8e-106">Programowo, rozszerzenia powiązania jest typu, który implementuje klasy abstrakcyjnej <xref:System.ServiceModel.Channels.BindingElement>.</span><span class="sxs-lookup"><span data-stu-id="34e8e-106">Programmatically, a binding extension is a type that implements the abstract class <xref:System.ServiceModel.Channels.BindingElement>.</span></span> <span data-ttu-id="34e8e-107">W pliku konfiguracyjnym `bindingElementExtensions` sekcji służy do definiowania elementu rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="34e8e-107">In the configuration file, the `bindingElementExtensions` section is used to define an extension element.</span></span>  
  
 <span data-ttu-id="34e8e-108">W poniższym przykładzie użyto `add` elementu, jak również `name` atrybutu, aby dodać rozszerzenie powiązania do `bindingElementExtensions` sekcji pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="34e8e-108">The following example uses the `add` element, as well as the `name` attribute to add a binding extension to the `bindingElementExtensions` section of the configuration file.</span></span>  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <bindingElementExtensions>  
           <add name="udpTransport" type="Microsoft.ServiceModel.Samples.UdpTransportSection, UdpTransport,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </bindingElementExtensions>  
    </extensions>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="34e8e-109">Aby dodać możliwości konfiguracji do elementu, użytkownik musi zapisać i Zarejestruj `bindingElementExtensionSection` elementu.</span><span class="sxs-lookup"><span data-stu-id="34e8e-109">To add configuration abilities to the element, the user needs to write and register a `bindingElementExtensionSection` element.</span></span> <span data-ttu-id="34e8e-110">Aby uzyskać więcej informacji o tym, zobacz <xref:System.Configuration> dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="34e8e-110">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="34e8e-111">Po zdefiniowaniu elementu i jego typ Konfiguracja rozszerzenia może służyć jako część niestandardowego powiązania jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="34e8e-111">After the element and its configuration type are defined, the extension can be used as part of a custom binding as shown in the following example.</span></span>  
  
```xml  
<customBinding>  
     <binding name="test2">  
         <udpTransport />  
         <binaryMessageEncoding maxReadPoolSize="211" maxWritePoolSize="2132"  
             maxSessionSize="3141" />  
         </binding>  
</customBinding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="34e8e-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="34e8e-112">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>  
 [<span data-ttu-id="34e8e-113">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="34e8e-113">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
