---
title: <bindingExtensions>
ms.date: 03/30/2017
ms.assetid: 8373f94d-d095-486f-8f1e-4ac2f72b58c7
ms.openlocfilehash: ed55701e45d8580e37cf4776de6b9c5241e0548c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59113038"
---
# <a name="bindingextensions"></a>\<bindingExtensions >
Ta sekcja umożliwia korzystanie z powiązania zdefiniowanego przez użytkownika z maszyny lub pliku konfiguracji aplikacji. Można dodać powiązania zdefiniowanego przez użytkownika do tej kolekcji przy użyciu `add` — słowo kluczowe i ustawienie `type` atrybut elementu do powiązania zdefiniowanego przez użytkownika, także `name` atrybutu nazwy użytkownika zdefiniowanych powiązań.  
  
 Powiązanie rozszerzenia umożliwiają użytkownikowi utworzenie powiązań zdefiniowanych przez użytkownika jako część konfiguracji punktu końcowego. Programowe rozszerzenie powiązania jest typu, który implementuje klasa abstrakcyjna <xref:System.ServiceModel.Channels.Binding>.  
  
 W poniższym przykładzie użyto `add` elementu, jak również `name` atrybutu, aby dodać rozszerzenie powiązania `bindingElementExtensions` sekcję pliku konfiguracji.  
  
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
  
 Aby dodać możliwości konfiguracji do elementu, użytkownik musi napisać i Zarejestruj `bindingSection` elementu. Aby uzyskać więcej informacji na temat tego, zobacz <xref:System.Configuration> dokumentacji.  
  
 Po zdefiniowaniu elementu i jego typ Konfiguracja rozszerzenia może służyć jako część punktu końcowego jak pokazano w poniższym przykładzie.  
  
```xml  
<services>
  <service name="MyService">
    <endpoint address="myAddress"
              binding="MyBinding" />
  </service>
</services>
```  
  
## <a name="see-also"></a>Zobacz także

- [Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)
