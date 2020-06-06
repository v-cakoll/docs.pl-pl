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

<span data-ttu-id="761ac-101">Ta sekcja umożliwia użycie zdefiniowanego przez użytkownika powiązania z pliku konfiguracji komputera lub aplikacji.</span><span class="sxs-lookup"><span data-stu-id="761ac-101">This section enables the use of a user defined binding from a machine or application configuration file.</span></span> <span data-ttu-id="761ac-102">Można dodać powiązanie zdefiniowane przez użytkownika do tej kolekcji przy użyciu `add` słowa kluczowego i ustawić `type` atrybut elementu na powiązanie zdefiniowane przez użytkownika, a także `name` atrybut nazwy wiązania zdefiniowanej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="761ac-102">You can add a user defined binding to this collection by using the `add` keyword, and setting the `type` attribute of the element to a user defined binding, as well as the `name` attribute to the name of the user defined binding.</span></span>

<span data-ttu-id="761ac-103">Rozszerzenia powiązań umożliwiają użytkownikowi tworzenie powiązań zdefiniowanych przez użytkownika do użycia jako część konfiguracji punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="761ac-103">Binding extensions enable the user to create user-defined bindings for use as part an endpoint configuration.</span></span> <span data-ttu-id="761ac-104">Programowe rozszerzenie powiązania jest typem, który implementuje klasę abstrakcyjną <xref:System.ServiceModel.Channels.Binding> .</span><span class="sxs-lookup"><span data-stu-id="761ac-104">Programmatically, a binding extension is a type that implements the abstract class <xref:System.ServiceModel.Channels.Binding>.</span></span>

<span data-ttu-id="761ac-105">Poniższy przykład używa `add` elementu, a także `name` atrybutu, aby dodać rozszerzenie powiązania do `bindingExtensions` sekcji pliku konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="761ac-105">The following example uses the `add` element, as well as the `name` attribute to add a binding extension to the `bindingExtensions` section of the configuration file:</span></span>

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

<span data-ttu-id="761ac-106">Aby dodać możliwości konfiguracji do elementu, użytkownik musi napisać i zarejestrować `bindingSection` element.</span><span class="sxs-lookup"><span data-stu-id="761ac-106">To add configuration abilities to the element, the user needs to write and register a `bindingSection` element.</span></span> <span data-ttu-id="761ac-107">Aby uzyskać więcej informacji na ten temat, zapoznaj się z <xref:System.Configuration> dokumentacją.</span><span class="sxs-lookup"><span data-stu-id="761ac-107">For more information on this, see the <xref:System.Configuration> documentation.</span></span>

<span data-ttu-id="761ac-108">Po zdefiniowaniu elementu i jego typu konfiguracji rozszerzenie może być używane jako część punktu końcowego, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="761ac-108">After the element and its configuration type are defined, the extension can be used as part of an endpoint as shown in the following example:</span></span>

```xml
<services>
  <service name="MyService">
    <endpoint address="myAddress"
              binding="MyBinding" />
  </service>
</services>
```

## <a name="see-also"></a><span data-ttu-id="761ac-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="761ac-109">See also</span></span>

- [<span data-ttu-id="761ac-110">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="761ac-110">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
