---
title: <bindingExtensions>
ms.date: 03/30/2017
ms.assetid: 8373f94d-d095-486f-8f1e-4ac2f72b58c7
ms.openlocfilehash: bd6aeb32e0994bceb9e56bcb1c6267f4cb64a5a4
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039142"
---
# <a name="bindingextensions"></a>\<bindingExtensions >

Ta sekcja umożliwia użycie zdefiniowanego przez użytkownika powiązania z pliku konfiguracji komputera lub aplikacji. Można dodać powiązanie zdefiniowane przez użytkownika do tej kolekcji przy użyciu słowa kluczowego `add` i ustawić atrybut `type` elementu na powiązanie zdefiniowane przez użytkownika, a także atrybut `name` na nazwę wiązania zdefiniowanego przez użytkownika.

Rozszerzenia powiązań umożliwiają użytkownikowi tworzenie powiązań zdefiniowanych przez użytkownika do użycia jako część konfiguracji punktu końcowego. Programowe rozszerzenie powiązania jest typem, który implementuje klasę abstrakcyjną <xref:System.ServiceModel.Channels.Binding>.

Poniższy przykład używa elementu `add`, a także atrybutu `name`, aby dodać rozszerzenie powiązania do sekcji `bindingExtensions` pliku konfiguracji:

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

Aby dodać możliwości konfiguracji do elementu, użytkownik musi napisać i zarejestrować element `bindingSection`. Aby uzyskać więcej informacji na ten temat, zobacz dokumentację <xref:System.Configuration>.

Po zdefiniowaniu elementu i jego typu konfiguracji rozszerzenie może być używane jako część punktu końcowego, jak pokazano w następującym przykładzie:

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
