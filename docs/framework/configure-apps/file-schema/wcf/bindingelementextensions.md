---
title: <bindingElementExtensions>
ms.date: 03/30/2017
ms.assetid: bb597fc0-c947-451c-afda-bf23d42f4f4d
ms.openlocfilehash: c323a65ace332d2ecd1e03330dddbe7ca17ff5bd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926367"
---
# <a name="bindingelementextensions"></a>\<bindingElementExtensions >
Ta sekcja umożliwia korzystanie z niestandardowego elementu powiązania z pliku konfiguracji komputera lub aplikacji. Można dodać niestandardowy element powiązania do tej kolekcji przy użyciu `add` słowa kluczowego i `type` ustawić atrybut elementu na rozszerzenie elementu powiązania `name` , a także atrybut elementu niestandardowego powiązania.  
  
 Rozszerzenia powiązań umożliwiają użytkownikowi tworzenie elementów powiązania zdefiniowanych przez użytkownika do użycia w ramach powiązań niestandardowych. Programowe rozszerzenie powiązania jest typem, który implementuje klasę <xref:System.ServiceModel.Channels.BindingElement>abstrakcyjną. W pliku `bindingElementExtensions` konfiguracji sekcja służy do definiowania elementu rozszerzenia.  
  
 Poniższy przykład używa `add` elementu, a także `name` atrybutu, aby dodać rozszerzenie powiązania do `bindingElementExtensions` sekcji pliku konfiguracji.  
  
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
  
 Aby dodać możliwości konfiguracji do elementu, użytkownik musi napisać i zarejestrować `bindingElementExtensionSection` element. Aby uzyskać więcej informacji na ten temat, <xref:System.Configuration> zapoznaj się z dokumentacją.  
  
 Po zdefiniowaniu elementu i jego typu konfiguracji rozszerzenie może być używane jako część niestandardowego powiązania, jak pokazano w poniższym przykładzie.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>
- [Rozszerzanie powiązań](../../../wcf/extending/extending-bindings.md)
