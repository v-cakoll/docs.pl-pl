---
title: <bindingElementExtensions>
ms.date: 03/30/2017
ms.assetid: bb597fc0-c947-451c-afda-bf23d42f4f4d
ms.openlocfilehash: 775f93f319c136a29a32ffaa1dfabc12ee081b29
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59227512"
---
# <a name="bindingelementextensions"></a><span data-ttu-id="09afb-101">\<bindingElementExtensions ></span><span class="sxs-lookup"><span data-stu-id="09afb-101">\<bindingElementExtensions></span></span>
<span data-ttu-id="09afb-102">Ta sekcja umożliwia zastosowanie elementu niestandardowego powiązania z maszyny lub pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="09afb-102">This section enables the use of a custom binding element from a machine or application configuration file.</span></span> <span data-ttu-id="09afb-103">Można dodać element niestandardowego powiązania z tą kolekcją, za pomocą `add` — słowo kluczowe i ustawienie `type` atrybutu elementu, który ma rozszerzenie elementu powiązania, jak również `name` atrybutu do elementu niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="09afb-103">You can add a custom binding element to this collection by using the `add` keyword, and setting the `type` attribute of the element to a binding element extension, as well as the `name` attribute to the custom binding element.</span></span>  
  
 <span data-ttu-id="09afb-104">Powiązanie rozszerzenia umożliwiają użytkownikowi utworzenie powiązań zdefiniowanych przez użytkownika elementy do użycia jako część niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="09afb-104">Binding extensions enable the user to create user-defined binding elements for use as part of custom bindings.</span></span> <span data-ttu-id="09afb-105">Programowe rozszerzenie powiązania jest typu, który implementuje klasa abstrakcyjna <xref:System.ServiceModel.Channels.BindingElement>.</span><span class="sxs-lookup"><span data-stu-id="09afb-105">Programmatically, a binding extension is a type that implements the abstract class <xref:System.ServiceModel.Channels.BindingElement>.</span></span> <span data-ttu-id="09afb-106">W pliku konfiguracyjnym `bindingElementExtensions` sekcji jest używana do definiowania elementu rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="09afb-106">In the configuration file, the `bindingElementExtensions` section is used to define an extension element.</span></span>  
  
 <span data-ttu-id="09afb-107">W poniższym przykładzie użyto `add` elementu, jak również `name` atrybutu, aby dodać rozszerzenie powiązania `bindingElementExtensions` sekcję pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="09afb-107">The following example uses the `add` element, as well as the `name` attribute to add a binding extension to the `bindingElementExtensions` section of the configuration file.</span></span>  
  
```xml  
<system.serviceModel>
  <extensions>
    <bindingElementExtensions>
      <add name="udpTransport"
           type="Microsoft.ServiceModel.Samples.UdpTransportSection, UdpTransport,
                 Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
    </bindingElementExtensions>
  </extensions>
</system.serviceModel>
```  
  
 <span data-ttu-id="09afb-108">Aby dodać możliwości konfiguracji do elementu, użytkownik musi napisać i Zarejestruj `bindingElementExtensionSection` elementu.</span><span class="sxs-lookup"><span data-stu-id="09afb-108">To add configuration abilities to the element, the user needs to write and register a `bindingElementExtensionSection` element.</span></span> <span data-ttu-id="09afb-109">Aby uzyskać więcej informacji na temat tego, zobacz <xref:System.Configuration> dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="09afb-109">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="09afb-110">Po zdefiniowaniu elementu i jego typ Konfiguracja rozszerzenia może służyć jako część niestandardowego powiązania jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="09afb-110">After the element and its configuration type are defined, the extension can be used as part of a custom binding as shown in the following example.</span></span>  
  
```xml  
<customBinding>
  <binding name="test2">
    <udpTransport />
    <binaryMessageEncoding maxReadPoolSize="211"
                           maxWritePoolSize="2132"
                           maxSessionSize="3141" />
  </binding>
</customBinding>
```  
  
## <a name="see-also"></a><span data-ttu-id="09afb-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="09afb-111">See also</span></span>

- <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>
- [<span data-ttu-id="09afb-112">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="09afb-112">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
