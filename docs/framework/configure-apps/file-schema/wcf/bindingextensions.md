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
# <a name="bindingextensions"></a>\<bindingExtensions >
Ta sekcja umożliwia użycie zdefiniowanego przez użytkownika powiązania z pliku konfiguracji komputera lub aplikacji. Można dodać powiązanie zdefiniowane przez użytkownika do tej kolekcji przy użyciu `add` słowa kluczowego i `type` ustawić atrybut elementu na powiązanie zdefiniowane przez użytkownika `name` , a także atrybut nazwy wiązania zdefiniowanej przez użytkownika.  
  
 Rozszerzenia powiązań umożliwiają użytkownikowi tworzenie powiązań zdefiniowanych przez użytkownika do użycia jako część konfiguracji punktu końcowego. Programowe rozszerzenie powiązania jest typem, który implementuje klasę <xref:System.ServiceModel.Channels.Binding>abstrakcyjną.  
  
 Poniższy przykład używa `add` elementu, a także `name` atrybutu, aby dodać rozszerzenie powiązania do `bindingElementExtensions` sekcji pliku konfiguracji.  
  
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
  
 Aby dodać możliwości konfiguracji do elementu, użytkownik musi napisać i zarejestrować `bindingSection` element. Aby uzyskać więcej informacji na ten temat, <xref:System.Configuration> zapoznaj się z dokumentacją.  
  
 Po zdefiniowaniu elementu i jego typu konfiguracji rozszerzenie może być używane jako część punktu końcowego, jak pokazano w poniższym przykładzie.  
  
```xml  
<services>
  <service name="MyService">
    <endpoint address="myAddress"
              binding="MyBinding" />
  </service>
</services>
```  
  
## <a name="see-also"></a>Zobacz także

- [Rozszerzanie powiązań](../../../wcf/extending/extending-bindings.md)
