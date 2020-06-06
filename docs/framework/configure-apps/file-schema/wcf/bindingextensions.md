---
title: <bindingExtensions>
ms.date: 03/30/2017
ms.assetid: 8373f94d-d095-486f-8f1e-4ac2f72b58c7
ms.openlocfilehash: bd6aeb32e0994bceb9e56bcb1c6267f4cb64a5a4
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73039142"
---
# \<bindingExtensions>

Ta sekcja umożliwia użycie zdefiniowanego przez użytkownika powiązania z pliku konfiguracji komputera lub aplikacji. Można dodać powiązanie zdefiniowane przez użytkownika do tej kolekcji przy użyciu `add` słowa kluczowego i ustawić `type` atrybut elementu na powiązanie zdefiniowane przez użytkownika, a także `name` atrybut nazwy wiązania zdefiniowanej przez użytkownika.

Rozszerzenia powiązań umożliwiają użytkownikowi tworzenie powiązań zdefiniowanych przez użytkownika do użycia jako część konfiguracji punktu końcowego. Programowe rozszerzenie powiązania jest typem, który implementuje klasę abstrakcyjną <xref:System.ServiceModel.Channels.Binding> .

Poniższy przykład używa `add` elementu, a także `name` atrybutu, aby dodać rozszerzenie powiązania do `bindingExtensions` sekcji pliku konfiguracji:

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

Aby dodać możliwości konfiguracji do elementu, użytkownik musi napisać i zarejestrować `bindingSection` element. Aby uzyskać więcej informacji na ten temat, zapoznaj się z <xref:System.Configuration> dokumentacją.

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
