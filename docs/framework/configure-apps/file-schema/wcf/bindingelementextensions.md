---
title: <bindingElementExtensions>
ms.date: 03/30/2017
ms.assetid: bb597fc0-c947-451c-afda-bf23d42f4f4d
ms.openlocfilehash: 9a2a3af093949c1d724fdea13655bbb80fe71048
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55270474"
---
# <a name="bindingelementextensions"></a>\<bindingElementExtensions >
Ta sekcja umożliwia zastosowanie elementu niestandardowego powiązania z maszyny lub pliku konfiguracji aplikacji. Można dodać element niestandardowego powiązania z tą kolekcją, za pomocą `add` — słowo kluczowe i ustawienie `type` atrybutu elementu, który ma rozszerzenie elementu powiązania, jak również `name` atrybutu do elementu niestandardowego powiązania.  
  
 Powiązanie rozszerzenia umożliwiają użytkownikowi utworzenie powiązań zdefiniowanych przez użytkownika elementy do użycia jako część niestandardowego powiązania. Programowe rozszerzenie powiązania jest typu, który implementuje klasa abstrakcyjna <xref:System.ServiceModel.Channels.BindingElement>. W pliku konfiguracyjnym `bindingElementExtensions` sekcji jest używana do definiowania elementu rozszerzenia.  
  
 W poniższym przykładzie użyto `add` elementu, jak również `name` atrybutu, aby dodać rozszerzenie powiązania `bindingElementExtensions` sekcję pliku konfiguracji.  
  
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
  
 Aby dodać możliwości konfiguracji do elementu, użytkownik musi napisać i Zarejestruj `bindingElementExtensionSection` elementu. Aby uzyskać więcej informacji na temat tego, zobacz <xref:System.Configuration> dokumentacji.  
  
 Po zdefiniowaniu elementu i jego typ Konfiguracja rozszerzenia może służyć jako część niestandardowego powiązania jak pokazano w poniższym przykładzie.  
  
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
- [Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)
