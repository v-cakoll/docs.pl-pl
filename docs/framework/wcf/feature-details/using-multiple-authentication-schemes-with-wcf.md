---
title: "Używanie wielu schematów uwierzytelniania z programem WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f32a56a0-e2b2-46bf-a302-29e1275917f9
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e570185b7df06a47e8c7fb3319328e760079415d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="using-multiple-authentication-schemes-with-wcf"></a>Używanie wielu schematów uwierzytelniania z programem WCF
WCF można teraz określić wielu schematów uwierzytelniania w jednym punkcie końcowym. Ponadto usługi sieci web hostowanej może dziedziczyć ustawień uwierzytelniania bezpośrednio za pomocą programu IIS. Hostowanie Samoobsługowe usługi można określić rodzaju uwierzytelniania schematy może służyć. Aby uzyskać więcej informacji na temat ustawiania ustawienia uwierzytelniania w usługach IIS, zobacz [uwierzytelniania usług IIS](http://go.microsoft.com/fwlink/?LinkId=232458)  
  
## <a name="iis-hosted-services"></a>Usług hostowanych przez usługi IIS  
 W przypadku usług hostowanych przez usługi IIS należy ustawić schematy uwierzytelniania, który ma zostać użyty w usługach IIS. Następnie w pliku web.config z usługą, w konfiguracji powiązania Określ typu poświadczeń klienta jako "InheritedFromHost" jak pokazano w następujący fragment kodu XML:  
  
```xml  
<bindings>  
      <basicHttpBinding>  
        <binding name="secureBinding">  
          <security mode="Transport">  
            <transport clientCredentialType="InheritedFromHost" />  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
```  
  
 Można określić, że mają podzbiór schematy uwierzytelniania do użycia z usługą przy użyciu ServiceAuthenticationBehavior lub \<serviceAuthenticationManager > elementu. Podczas konfigurowania to w kodzie Użyj ServiceAuthenticationBehavior, jak pokazano w poniższy fragment kodu.  
  
```csharp  
// ...  
ServiceAuthenticationBehavior sab = null;  
sab = serviceHost.Description.Behaviors.Find<ServiceAuthenticationBehavior>();  
  
if (sab == null)  
{  
    sab = new ServiceAuthenticationBehavior();  
    sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
    serviceHost.Description.Behaviors.Add(sab);  
}  
else  
{  
     sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
}  
// ...  
```  
  
 Podczas konfigurowania w pliku konfiguracji, użyj \<serviceAuthenticationManager > element, jak pokazano w następujący fragment kodu XML.  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior name="limitedAuthBehavior">  
          <serviceAuthenticationManager authenticationSchemes="Negotiate, Digest, Basic"/>  
          <!-- ... -->  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
 Daje to pewność, że tylko podzestaw schematy uwierzytelniania przedstawione w tym miejscu będą uznawane za stosowania dla punktu końcowego usługi, w zależności od wybranej usług IIS. Oznacza to, które można wykluczyć dewelopera powiedzieć uwierzytelnianie podstawowe z listy, pomijając go z listy serviceAuthenticationManager i nawet, jeśli jest włączone w usługach IIS, nie zostanie zastosowana na punkt końcowy usługi  
  
## <a name="self-hosted-services"></a>Hostowanie Samoobsługowe usług  
 Samodzielnie hostowane usługi są skonfigurowane nieco inaczej, ponieważ nie istnieje żadne usług IIS, aby odziedziczyć ustawienia z. W tym miejscu użyć \<serviceAuthenticationManager > elementu lub ServiceAuthenticationBehavior, aby określić ustawienia uwierzytelniania, które będą dziedziczone. W kodzie wygląda następująco:  
  
```csharp  
// ...  
ServiceAuthenticationBehavior sab = null;  
sab = serviceHost.Description.Behaviors.Find<ServiceAuthenticationBehavior>();  
  
if (sab == null)  
{  
    sab = new ServiceAuthenticationBehavior();  
    sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
    serviceHost.Description.Behaviors.Add(sab);  
}  
else  
{  
     sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
}  
// ...  
```  
  
 W konfiguracji wygląda następująco:  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior name="limitedAuthBehavior">  
          <serviceAuthenticationManager authenticationSchemes="Negotiate, Digest, Basic"/>  
          <!-- ... -->  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
 A następnie można określić InheritFromHost w ustawieniach powiązanie, jak pokazano w następujący fragment kodu XML.  
  
```xml  
<bindings>  
      <basicHttpBinding>  
        <binding name="secureBinding">  
          <security mode="Transport">  
            <transport clientCredentialType="InheritedFromHost" />  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
```  
  
 Alternatywnie możesz określić schematy uwierzytelniania niestandardowego powiązania, ustawiając schematy uwierzytelniania HTTP transportu element powiązania, jak pokazano w poniższy fragment konfiguracji.  
  
```xml  
<binding name="multipleBinding">  
      <textMessageEncoding/>  
      <httpTransport authenticationScheme="Negotiate, Ntlm, Digest, Basic" />  
    </binding>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Powiązania i zabezpieczenia](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 [Punkty końcowe: adresy, powiązania i kontrakty](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 [Konfigurowanie powiązań dostarczanych przez system](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Możliwości zabezpieczeń powiązań niestandardowych](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [Powiązania](../../../../docs/framework/wcf/feature-details/bindings.md)  
 [Powiązania](../../../../docs/framework/wcf/feature-details/bindings.md)  
 [Powiązania niestandardowe](../../../../docs/framework/wcf/extending/custom-bindings.md)
