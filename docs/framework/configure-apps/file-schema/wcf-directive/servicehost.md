---
title: '@ServiceHost'
ms.date: 03/30/2017
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
ms.openlocfilehash: 3d59fac08ee59ab5ede943de5109805ff1633d48
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54623940"
---
# <a name="servicehost"></a>\@ServiceHost
Kojarzy fabryka użyta do wyprodukowania hosta usługi przy użyciu usługi hostowane i innych aspektów programowania wymagane w celu uzyskania dostępu lub skompilować kod hostingu z pliku .svc.  
  
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
 Nazwa typu CLR usługi hostowanej. Powinna to być kwalifikowana nazwa typu, który implementuje jedną lub więcej kontaktów usługi.  
  
#### <a name="factory"></a>Fabryka  
 Nazwa typu CLR fabryki hostów usług, które są używane do utworzenia wystąpienia hosta usługi. Ten atrybut jest opcjonalny. Jeśli nie zostanie podany, domyślna <xref:System.ServiceModel.Activation.ServiceHostFactory> jest używany, która zwraca wystąpienie <xref:System.ServiceModel.ServiceHost>.  
  
#### <a name="debug"></a>Debugowanie  
 Wskazuje, czy usługa Windows Communication Foundation (WCF) powinna być skompilowana przy użyciu symboli debugowania. `true` Jeśli usługa WCF powinna być skompilowana przy użyciu symboli debugowania; w przeciwnym razie `false`.  
  
#### <a name="language"></a>Język  
 Określa język używany podczas kompilowania kodu wbudowanego w pliku (SVC). Wartość może reprezentować dowolny. Obsługiwane NET języka, w tym C#, VB i JS, które odwołują się odpowiednio do języka C#, Visual Basic .NET i JScript .NET. Ten atrybut jest opcjonalny.  
  
#### <a name="codebehind"></a>Plik CodeBehind  
 Określa plik źródłowy, który implementuje usługi XML sieci Web, gdy klasa, która implementuje usługi XML sieci Web nie znajduje się w tym samym pliku i nie został skompilowany w zestawie i umieszczane w katalogu \Bin.  
  
## <a name="remarks"></a>Uwagi  
 <xref:System.ServiceModel.ServiceHost> Używane do hostowania usługi jest punktem rozszerzalność w modelu programowania Windows Communication Foundation (WCF). Wzorzec fabryki jest używany do utworzenia wystąpienia <xref:System.ServiceModel.ServiceHost> ponieważ, potencjalnie, typem polimorficznym, środowisko hostingu nie należy bezpośrednio wystąpienia.  
  
 Domyślna implementacja używa <xref:System.ServiceModel.Activation.ServiceHostFactory> do utworzenia wystąpienia <xref:System.ServiceModel.ServiceHost>. Ale możesz podać własne fabryki (taki, który zwraca pochodnej hosta), określając nazwę typu CLR fabryki implementacji w [ \@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dyrektywy.  
  
 Aby użyć własnych niestandardowych usługi fabryka hostów zamiast domyślną fabrykę, wystarczy podać nazwę typu w [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dyrektywy w następujący sposób:  
  
```xml  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 Zachowaj jak implementacje fabryki. Jeśli masz wiele logikę niestandardową, Twój kod jest bardziej wielokrotnego użytku, jeżeli umieścisz tej logiki wewnątrz hosta zamiast w fabryce.  
  
 Na przykład, aby włączyć punkt końcowy interfejsu AJAX w celu `MyService`, określ <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> dla wartości `Factory` atrybutu zamiast domyślnego <xref:System.ServiceModel.Activation.ServiceHostFactory>w [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dyrektywy jako pokazano w poniższym przykładzie.  
  
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
- [Niestandardowy host usługi](../../../../../docs/framework/wcf/samples/custom-service-host.md)
