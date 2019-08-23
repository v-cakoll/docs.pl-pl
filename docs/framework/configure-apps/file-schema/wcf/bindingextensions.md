---
title: <bindingExtensions>
ms.date: 03/30/2017
ms.assetid: 8373f94d-d095-486f-8f1e-4ac2f72b58c7
ms.openlocfilehash: 34ba198de33ae4aa1882d13f74bd2d538999a0c9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919786"
---
# <a name="bindingextensions"></a><span data-ttu-id="bd0cc-101">\<bindingExtensions ></span><span class="sxs-lookup"><span data-stu-id="bd0cc-101">\<bindingExtensions></span></span>
<span data-ttu-id="bd0cc-102">Ta sekcja umożliwia użycie zdefiniowanego przez użytkownika powiązania z pliku konfiguracji komputera lub aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bd0cc-102">This section enables the use of a user defined binding from a machine or application configuration file.</span></span> <span data-ttu-id="bd0cc-103">Można dodać powiązanie zdefiniowane przez użytkownika do tej kolekcji przy użyciu `add` słowa kluczowego i `type` ustawić atrybut elementu na powiązanie zdefiniowane przez użytkownika `name` , a także atrybut nazwy wiązania zdefiniowanej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bd0cc-103">You can add a user defined binding to this collection by using the `add` keyword, and setting the `type` attribute of the element to a user defined binding, as well as the `name` attribute to the name of the user defined binding.</span></span>  
  
 <span data-ttu-id="bd0cc-104">Rozszerzenia powiązań umożliwiają użytkownikowi tworzenie powiązań zdefiniowanych przez użytkownika do użycia jako część konfiguracji punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="bd0cc-104">Binding extensions enable the user to create user-defined bindings for use as part an endpoint configuration.</span></span> <span data-ttu-id="bd0cc-105">Programowe rozszerzenie powiązania jest typem, który implementuje klasę <xref:System.ServiceModel.Channels.Binding>abstrakcyjną.</span><span class="sxs-lookup"><span data-stu-id="bd0cc-105">Programmatically, a binding extension is a type that implements the abstract class <xref:System.ServiceModel.Channels.Binding>.</span></span>  
  
 <span data-ttu-id="bd0cc-106">Poniższy przykład używa `add` elementu, a także `name` atrybutu, aby dodać rozszerzenie powiązania do `bindingElementExtensions` sekcji pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="bd0cc-106">The following example uses the `add` element, as well as the `name` attribute to add a binding extension to the `bindingElementExtensions` section of the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="bd0cc-107">Aby dodać możliwości konfiguracji do elementu, użytkownik musi napisać i zarejestrować `bindingSection` element.</span><span class="sxs-lookup"><span data-stu-id="bd0cc-107">To add configuration abilities to the element, the user needs to write and register a `bindingSection` element.</span></span> <span data-ttu-id="bd0cc-108">Aby uzyskać więcej informacji na ten temat, <xref:System.Configuration> zapoznaj się z dokumentacją.</span><span class="sxs-lookup"><span data-stu-id="bd0cc-108">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="bd0cc-109">Po zdefiniowaniu elementu i jego typu konfiguracji rozszerzenie może być używane jako część punktu końcowego, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="bd0cc-109">After the element and its configuration type are defined, the extension can be used as part of an endpoint as shown in the following example.</span></span>  
  
```xml  
<services>
  <service name="MyService">
    <endpoint address="myAddress"
              binding="MyBinding" />
  </service>
</services>
```  
  
## <a name="see-also"></a><span data-ttu-id="bd0cc-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bd0cc-110">See also</span></span>

- [<span data-ttu-id="bd0cc-111">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="bd0cc-111">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
