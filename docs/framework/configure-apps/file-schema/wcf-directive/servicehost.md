---
title: '@ServiceHost'
ms.date: 03/30/2017
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
ms.openlocfilehash: fdd6d83836c4ef31a4d7c8e68cb0cc050ac6bea4
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "76787803"
---
# <a name="servicehost"></a>\@ServiceHost

Kojarzy fabrykę używaną do tworzenia hosta usługi z usługą, która ma być hostowana, i innych aspektów programistycznych wymaganych do uzyskania dostępu lub skompilowania kodu hostingu podanego w pliku SVC.

## <a name="syntax"></a>Składnia

```xml
<% @ServiceHost
Service = "Service, ServiceNamespace"
Factory = "Factory, FactoryNamespace"
Debug = "Debug"
Language = "Language"
CodeBehind = "CodeBehind"
%>
```

## <a name="attributes"></a>Atrybuty

### <a name="service"></a>Usługa

Nazwa typu CLR hostowanej usługi. Powinna to być kwalifikowana nazwa typu, który implementuje co najmniej jeden kontakt usługi.

### <a name="factory"></a>Fabryka

Nazwa typu CLR fabryki hosta usługi użyta do utworzenia wystąpienia hosta usługi. Ten atrybut jest opcjonalny. Jeśli <xref:System.ServiceModel.Activation.ServiceHostFactory> nie zostanie określony, zostanie użyta wartość domyślna, która zwraca wystąpienie <xref:System.ServiceModel.ServiceHost> .

### <a name="debug"></a>Debugowanie

Wskazuje, czy usługa Windows Communication Foundation (WCF) powinna być skompilowana przy użyciu symboli debugowania. `true`Jeśli usługa WCF powinna być skompilowana przy użyciu symboli debugowania; w przeciwnym razie `false` .

### <a name="language"></a>Język

Określa język używany podczas kompilowania całego kodu śródwierszowego w pliku (. svc). Wartości mogą reprezentować dowolne. Język obsługiwany w sieci, w tym, `C#` `VB` i, `JS` który odwołuje się odpowiednio do języka C#, Visual Basic i JScript .NET. Ten atrybut jest opcjonalny.

### <a name="codebehind"></a>CodeBehind

Określa plik źródłowy, który implementuje usługę sieci Web XML, gdy Klasa implementująca usługę XML sieci Web nie znajduje się w tym samym pliku i nie została skompilowana do zestawu i umieszczona w katalogu *\Bin* .

## <a name="remarks"></a>Uwagi

<xref:System.ServiceModel.ServiceHost>Używany do hostowania usługi jest punktem rozszerzalności w modelu programowania Windows Communication Foundation (WCF). Wzorzec fabryki służy do tworzenia wystąpienia elementu <xref:System.ServiceModel.ServiceHost> , ponieważ jest to, potencjalnie, typ polimorficzny, że środowisko hostingu nie powinno bezpośrednio tworzyć wystąpienia.

Domyślna implementacja używa <xref:System.ServiceModel.Activation.ServiceHostFactory> do tworzenia wystąpienia <xref:System.ServiceModel.ServiceHost> . Można jednak zapewnić własną fabrykę (taką, która zwraca hosta pochodnego), określając nazwę typu CLR implementacji fabryki w `@ServiceHost` dyrektywie.

Aby korzystać z własnej fabryki hosta usługi niestandardowej zamiast fabryki domyślnej, wystarczy podać nazwę typu w `@ServiceHost` dyrektywie w następujący sposób.

```xml
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>
```

W miarę możliwości Zachowaj implementacje fabryk. Jeśli masz wiele logiki niestandardowej, kod jest większy do wielokrotnego użytku, jeśli zostanie umieszczony w obrębie hosta zamiast fabryki.

Na przykład, aby włączyć punkt końcowy z obsługą technologii AJAX dla programu `MyService` , należy określić jako <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> wartość `Factory` atrybutu zamiast domyślnego <xref:System.ServiceModel.Activation.ServiceHostFactory> , w `@ServiceHost` dyrektywie, jak pokazano w następującym przykładzie:

```xml
<% @ServiceHost
Service="MyService"
Language="C#"
Debug="true"
Factory="WebScriptServiceHostFactory"
%>
```

## <a name="see-also"></a>Zobacz także

- [Niestandardowy host usługi](../../../wcf/samples/custom-service-host.md)
