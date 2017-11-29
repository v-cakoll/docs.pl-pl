---
title: '@ServiceHost'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ed64a90131fcd8f2d9f2120c03db4a21d8dc6efe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="servicehost"></a>@ServiceHost
Kojarzy fabryka użyta do wyprodukowania hosta usługi z usługą ma być obsługiwana i inne aspekty programowania wymagane do uzyskania dostępu lub skompilować hostingu kod zawarty w pliku svc.  
  
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
 Nazwa typu CLR usługi hostowanej. Powinna to być kwalifikowaną nazwę typu, który implementuje co najmniej jeden kontakty usługi.  
  
#### <a name="factory"></a>Fabryka  
 Nazwa typu CLR fabryki hostów usług służący do uruchamiania usługi hosta. Ten atrybut jest opcjonalne. Jeśli zostanie określona, domyślnie <xref:System.ServiceModel.Activation.ServiceHostFactory> jest używana, która zwraca wystąpienie klasy <xref:System.ServiceModel.ServiceHost>.  
  
#### <a name="debug"></a>Debugowanie  
 Wskazuje, czy [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] usługi ma być kompilowana przy użyciu symboli debugowania. `true`Jeśli [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] usługi powinny być skompilowanych przy użyciu symboli debugowania; w przeciwnym razie `false`.  
  
#### <a name="language"></a>Język  
 Określa język używany podczas kompilowania kodu wbudowanego w pliku (SVC). Wartości może reprezentować żadnego. Obsługiwane NET język, w tym C#, VB i JS, które dotyczą odpowiednio C#, Visual Basic .NET i JScript .NET. Ten atrybut jest opcjonalne.  
  
#### <a name="codebehind"></a>Plik CodeBehind  
 Określa plik źródłowy, który implementuje usługi XML sieci Web, gdy klasa, która implementuje usługi XML sieci Web nie znajduje się w tym samym pliku, a nie został skompilowany w zestawie i umieszczane w katalogu \Bin.  
  
## <a name="remarks"></a>Uwagi  
 <xref:System.ServiceModel.ServiceHost> Używane do obsługi usługi jest punktem rozszerzalności w [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] model programowania. Wzorzec fabryki służy do tworzenia wystąpienia <xref:System.ServiceModel.ServiceHost> , dlatego potencjalnie, typ polimorficzny środowisko macierzyste nie należy bezpośrednio wystąpienia.  
  
 Domyślna implementacja używa <xref:System.ServiceModel.Activation.ServiceHostFactory> można utworzyć wystąpienia <xref:System.ServiceModel.ServiceHost>. Ale możesz podać własne fabryki (taki, który zwraca pochodnej hosta), określając nazwę typu CLR fabryki implementacji w [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dyrektywy.  
  
 Aby użyć własnych niestandardowych usługi fabryka hostów zamiast domyślną fabrykę, wystarczy podać nazwę typu w [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dyrektywy w następujący sposób:  
  
```xml  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 Zachowaj jak implementacje fabryki. Jeśli masz wiele niestandardowej logiki kodu jest bardziej wielokrotnego użytku, jeśli umieść ten logikę w sieci hosta zamiast w fabryce.  
  
 Na przykład, aby włączyć punkt końcowy interfejsu AJAX dla `MyService`, określ <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> dla wartości `Factory` atrybutu, zamiast domyślnej <xref:System.ServiceModel.Activation.ServiceHostFactory>w [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dyrektywy jako pokazano w poniższym przykładzie.  
  
## <a name="example"></a>Przykład  
  
```  
<% @ServiceHost   
Service="MyService"  
Language="C#"  
Debug="true"  
Factory="WebScriptServiceHostFactory"  
%>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Niestandardowy Host usługi](../../../../../docs/framework/wcf/samples/custom-service-host.md)
