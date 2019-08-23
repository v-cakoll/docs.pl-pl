---
title: '@ServiceHost'
ms.date: 03/30/2017
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
ms.openlocfilehash: a56fb1bb9395425222347914fe3f4c17f1a451b7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920338"
---
# <a name="servicehost"></a>\@ServiceHost
Kojarzy fabrykę używaną do tworzenia hosta usługi z usługą, która ma być hostowana, i innych aspektów programistycznych wymaganych do uzyskania dostępu lub skompilowania kodu hostingu podanego w pliku SVC.  
  
## <a name="syntax"></a>Składnia  
  
```  
<% @ServiceHost   
Service = "Service, ServiceNamespace"   
Factory = "Factory, FactoryNamespace"  
Debug = "Debug"  
Language = "Language"   
CodeBehind = "CodeBehind"%>  
```  
  
## <a name="attributes"></a>Atrybuty  
  
#### <a name="service"></a>Usługa  
 Nazwa typu CLR hostowanej usługi. Powinna to być kwalifikowana nazwa typu, który implementuje co najmniej jeden kontakt usługi.  
  
#### <a name="factory"></a>Indywidual  
 Nazwa typu CLR fabryki hosta usługi użyta do utworzenia wystąpienia hosta usługi. Ten atrybut jest opcjonalny. Jeśli nie zostanie określony, zostanie <xref:System.ServiceModel.Activation.ServiceHostFactory> użyta wartość domyślna, która zwraca <xref:System.ServiceModel.ServiceHost>wystąpienie.  
  
#### <a name="debug"></a>Debugowanie  
 Wskazuje, czy usługa Windows Communication Foundation (WCF) powinna być skompilowana przy użyciu symboli debugowania. `true`Jeśli usługa WCF powinna być skompilowana przy użyciu symboli debugowania; w przeciwnym razie. `false`  
  
#### <a name="language"></a>Język  
 Określa język używany podczas kompilowania całego kodu śródwierszowego w pliku (. svc). Wartości mogą reprezentować dowolne. Język obsługiwany w sieci, w C#tym VB i JS, który odnosi się C#odpowiednio do, Visual Basic .NET i JScript .NET. Ten atrybut jest opcjonalny.  
  
#### <a name="codebehind"></a>Plik CodeBehind  
 Określa plik źródłowy, który implementuje usługę sieci Web XML, gdy Klasa implementująca usługę XML sieci Web nie znajduje się w tym samym pliku i nie została skompilowana do zestawu i umieszczona w katalogu \Bin.  
  
## <a name="remarks"></a>Uwagi  
 <xref:System.ServiceModel.ServiceHost> Używany do hostowania usługi jest punktem rozszerzalności w modelu programowania Windows Communication Foundation (WCF). Wzorzec fabryki służy do tworzenia wystąpienia <xref:System.ServiceModel.ServiceHost> elementu, ponieważ jest to, potencjalnie, typ polimorficzny, że środowisko hostingu nie powinno bezpośrednio tworzyć wystąpienia.  
  
 Domyślna implementacja używa <xref:System.ServiceModel.Activation.ServiceHostFactory> do tworzenia <xref:System.ServiceModel.ServiceHost>wystąpienia. Można jednak zapewnić własną fabrykę (taką, która zwraca hosta pochodnego), określając nazwę typu CLR implementacji fabryki w [ \@](servicehost.md) dyrektywie ServiceHost.  
  
 Aby korzystać z własnej fabryki hosta usługi niestandardowej zamiast fabryki domyślnej, wystarczy podać nazwę typu w [@ServiceHost](servicehost.md) dyrektywie w następujący sposób:  
  
```xml  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 W miarę możliwości Zachowaj implementacje fabryk. Jeśli masz wiele logiki niestandardowej, kod jest większy do wielokrotnego użytku, jeśli zostanie umieszczony w obrębie hosta zamiast fabryki.  
  
 Na przykład, aby włączyć punkt końcowy z obsługą technologii `MyService`AJAX dla programu <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> , należy określić jako wartość `Factory` atrybutu zamiast domyślnego <xref:System.ServiceModel.Activation.ServiceHostFactory>, w [@ServiceHost](servicehost.md) dyrektywie, jak pokazano w poniższym przykładzie.  
  
## <a name="example"></a>Przykład  
  
```  
<% @ServiceHost   
Service="MyService"  
Language="C#"  
Debug="true"  
Factory="WebScriptServiceHostFactory"  
%>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Niestandardowy host usługi](../../../wcf/samples/custom-service-host.md)
