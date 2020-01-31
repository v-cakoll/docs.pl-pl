---
title: '@ServiceHost'
ms.date: 03/30/2017
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
ms.openlocfilehash: fdd6d83836c4ef31a4d7c8e68cb0cc050ac6bea4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
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

## <a name="attributes"></a>{1&gt;{2&gt;Atrybuty&lt;2}&lt;1}

### <a name="service"></a>NDES

Nazwa typu CLR hostowanej usługi. Powinna to być kwalifikowana nazwa typu, który implementuje co najmniej jeden kontakt usługi.

### <a name="factory"></a>indywidual

Nazwa typu CLR fabryki hosta usługi użyta do utworzenia wystąpienia hosta usługi. Ten atrybut jest opcjonalny. Jeśli nie zostanie określony, zostanie użyta domyślna <xref:System.ServiceModel.Activation.ServiceHostFactory>, która zwraca wystąpienie <xref:System.ServiceModel.ServiceHost>.

### <a name="debug"></a>Debugowanie

Wskazuje, czy usługa Windows Communication Foundation (WCF) powinna być skompilowana przy użyciu symboli debugowania. `true`, jeśli usługa WCF powinna być skompilowana przy użyciu symboli debugowania; w przeciwnym razie `false`.

### <a name="language"></a>Język

Określa język używany podczas kompilowania całego kodu śródwierszowego w pliku (. svc). Wartości mogą reprezentować dowolne. Język obsługiwany w sieci, w tym `C#`, `VB`i `JS`, który odwołuje C#się odpowiednio do, Visual Basic i JScript .NET. Ten atrybut jest opcjonalny.

### <a name="codebehind"></a>Plik CodeBehind

Określa plik źródłowy, który implementuje usługę sieci Web XML, gdy Klasa implementująca usługę XML sieci Web nie znajduje się w tym samym pliku i nie została skompilowana do zestawu i umieszczona w katalogu *\Bin* .

## <a name="remarks"></a>Uwagi

<xref:System.ServiceModel.ServiceHost> używany do hostowania usługi jest punktem rozszerzalności w modelu programowania Windows Communication Foundation (WCF). Wzorzec fabryki służy do tworzenia wystąpienia <xref:System.ServiceModel.ServiceHost>, ponieważ jest to, potencjalnie, typ polimorficzny, że środowisko hostingu nie powinno bezpośrednio tworzyć wystąpienia.

Domyślna implementacja używa <xref:System.ServiceModel.Activation.ServiceHostFactory> do utworzenia wystąpienia <xref:System.ServiceModel.ServiceHost>. Można jednak zapewnić własną fabrykę (taką, która zwraca hosta pochodnego), określając nazwę typu CLR implementacji fabryki w dyrektywie `@ServiceHost`.

Aby korzystać z własnej fabryki hosta usługi niestandardowej zamiast fabryki domyślnej, wystarczy podać nazwę typu w dyrektywie `@ServiceHost` w następujący sposób.

```xml
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>
```

W miarę możliwości Zachowaj implementacje fabryk. Jeśli masz wiele logiki niestandardowej, kod jest większy do wielokrotnego użytku, jeśli zostanie umieszczony w obrębie hosta zamiast fabryki.

Na przykład aby włączyć punkt końcowy z obsługą technologii AJAX dla `MyService`, należy określić <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> dla wartości atrybutu `Factory` zamiast domyślnego <xref:System.ServiceModel.Activation.ServiceHostFactory>, w dyrektywie `@ServiceHost`, jak pokazano w następującym przykładzie:

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
