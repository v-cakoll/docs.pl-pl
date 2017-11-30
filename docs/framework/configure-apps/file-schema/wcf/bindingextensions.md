---
title: '&lt;bindingExtensions&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8373f94d-d095-486f-8f1e-4ac2f72b58c7
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c02af972ad52119af07da404a61fd3afc0facbeb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltbindingextensionsgt"></a>&lt;bindingExtensions&gt;
Ta sekcja umożliwia korzystanie z powiązania z maszyny zdefiniowanego przez użytkownika lub pliku konfiguracji aplikacji. Można dodać powiązania do tej kolekcji przy użyciu zdefiniowanego przez użytkownika `add` — słowo kluczowe i ustawienie `type` atrybutu elementu powiązania, zdefiniowanego przez użytkownika, jak również `name` powiązania zdefiniowanych dla atrybutu nazwy użytkownika.  
  
 Powiązanie rozszerzeniom użytkownikowi utworzenie powiązań zdefiniowanych przez użytkownika jako część konfiguracji punktu końcowego. Programowo, rozszerzenia powiązania jest typu, który implementuje klasy abstrakcyjnej <xref:System.ServiceModel.Channels.Binding>.  
  
 W poniższym przykładzie użyto `add` elementu, jak również `name` atrybutu, aby dodać rozszerzenie powiązania do `bindingElementExtensions` sekcji pliku konfiguracji.  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <bindingExtensions>  
           <add name="MyBinding" type="Microsoft.ServiceModel.Samples.MyBinding, MyBinding,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </bindingExtensions>  
    </extensions>  
</system.serviceModel>  
```  
  
 Aby dodać możliwości konfiguracji do elementu, użytkownik musi zapisać i Zarejestruj `bindingSection` elementu. Aby uzyskać więcej informacji o tym, zobacz <xref:System.Configuration> dokumentacji.  
  
 Po zdefiniowaniu elementu i jego typ Konfiguracja rozszerzenia może służyć jako część punktu końcowego jak pokazano w poniższym przykładzie.  
  
```xml  
<services>  
    <service name="MyService">  
        <endpoint address="myAddress" binding="MyBinding" />  
    </service>  
</services>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)
