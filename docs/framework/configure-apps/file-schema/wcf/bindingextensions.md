---
title: <bindingExtensions>
ms.date: 03/30/2017
ms.assetid: 8373f94d-d095-486f-8f1e-4ac2f72b58c7
ms.openlocfilehash: 6eed4e8c549bccb06d8d425b084554a2ec7a1183
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55272764"
---
# <a name="bindingextensions"></a><span data-ttu-id="3bc38-101">\<bindingExtensions ></span><span class="sxs-lookup"><span data-stu-id="3bc38-101">\<bindingExtensions></span></span>
<span data-ttu-id="3bc38-102">Ta sekcja umożliwia korzystanie z powiązania zdefiniowanego przez użytkownika z maszyny lub pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3bc38-102">This section enables the use of a user defined binding from a machine or application configuration file.</span></span> <span data-ttu-id="3bc38-103">Można dodać powiązania zdefiniowanego przez użytkownika do tej kolekcji przy użyciu `add` — słowo kluczowe i ustawienie `type` atrybut elementu do powiązania zdefiniowanego przez użytkownika, także `name` atrybutu nazwy użytkownika zdefiniowanych powiązań.</span><span class="sxs-lookup"><span data-stu-id="3bc38-103">You can add a user defined binding to this collection by using the `add` keyword, and setting the `type` attribute of the element to a user defined binding, as well as the `name` attribute to the name of the user defined binding.</span></span>  
  
 <span data-ttu-id="3bc38-104">Powiązanie rozszerzenia umożliwiają użytkownikowi utworzenie powiązań zdefiniowanych przez użytkownika jako część konfiguracji punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="3bc38-104">Binding extensions enable the user to create user-defined bindings for use as part an endpoint configuration.</span></span> <span data-ttu-id="3bc38-105">Programowe rozszerzenie powiązania jest typu, który implementuje klasa abstrakcyjna <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="3bc38-105">Programmatically, a binding extension is a type that implements the abstract class <xref:System.ServiceModel.Channels.Binding>.</span></span>  
  
 <span data-ttu-id="3bc38-106">W poniższym przykładzie użyto `add` elementu, jak również `name` atrybutu, aby dodać rozszerzenie powiązania `bindingElementExtensions` sekcję pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3bc38-106">The following example uses the `add` element, as well as the `name` attribute to add a binding extension to the `bindingElementExtensions` section of the configuration file.</span></span>  
  
```xml  
<system.serviceModel>
  <extensions>
    <bindingExtensions>
      <add name="MyBinding"
           type="Microsoft.ServiceModel.Samples.MyBinding, MyBinding,
                 Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
    </bindingExtensions>
  </extensions>
</system.serviceModel>
```  
  
 <span data-ttu-id="3bc38-107">Aby dodać możliwości konfiguracji do elementu, użytkownik musi napisać i Zarejestruj `bindingSection` elementu.</span><span class="sxs-lookup"><span data-stu-id="3bc38-107">To add configuration abilities to the element, the user needs to write and register a `bindingSection` element.</span></span> <span data-ttu-id="3bc38-108">Aby uzyskać więcej informacji na temat tego, zobacz <xref:System.Configuration> dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="3bc38-108">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="3bc38-109">Po zdefiniowaniu elementu i jego typ Konfiguracja rozszerzenia może służyć jako część punktu końcowego jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="3bc38-109">After the element and its configuration type are defined, the extension can be used as part of an endpoint as shown in the following example.</span></span>  
  
```xml  
<services>
  <service name="MyService">
    <endpoint address="myAddress"
              binding="MyBinding" />
  </service>
</services>
```  
  
## <a name="see-also"></a><span data-ttu-id="3bc38-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3bc38-110">See also</span></span>
- [<span data-ttu-id="3bc38-111">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="3bc38-111">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
