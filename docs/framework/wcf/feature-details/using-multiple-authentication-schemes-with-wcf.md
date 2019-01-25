---
title: Używanie wielu schematów uwierzytelniania z programem WCF
ms.date: 03/30/2017
ms.assetid: f32a56a0-e2b2-46bf-a302-29e1275917f9
ms.openlocfilehash: 8aa593803354628354e5ed3bf02cbcea44505e5e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54593813"
---
# <a name="using-multiple-authentication-schemes-with-wcf"></a>Używanie wielu schematów uwierzytelniania z programem WCF
Usługi WCF umożliwia teraz określenie wielu schematów uwierzytelniania w jednym punkcie końcowym. Ponadto usługi sieci web hostowanych może dziedziczyć ustawień uwierzytelniania bezpośrednio za pomocą programu IIS. Samodzielnie hostowanej usługi można określić rodzaju uwierzytelniania może służyć schematów. Aby uzyskać więcej informacji na temat ustawiania ustawienia uwierzytelniania w usługach IIS, zobacz [uwierzytelnianie usług IIS](https://go.microsoft.com/fwlink/?LinkId=232458)  
  
## <a name="iis-hosted-services"></a>IIS-Hosted Services  
 W przypadku usług hostowanych przez usługi IIS należy ustawić schematy uwierzytelniania, które mają być używane w usługach IIS. Następnie w pliku web.config usługi w konfiguracji powiązania Określ typ clientCredential jako "InheritedFromHost" jak pokazano w poniższym fragmencie kodu XML:  
  
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
  
 Można określić tylko mają podzbiór schematów uwierzytelniania do użycia z usługą za pomocą ServiceAuthenticationBehavior lub \<serviceAuthenticationManager > element. Podczas konfigurowania to w kodzie należy użyć ServiceAuthenticationBehavior, jak pokazano w poniższym fragmencie kodu.  
  
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
  
 Podczas konfigurowania to w pliku konfiguracji, użyj \<serviceAuthenticationManager > elementu, jak pokazano w poniższym fragmencie kodu XML.  
  
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
  
 Pozwoli to zagwarantować, że tylko podzbiór schematy uwierzytelniania, wymienione w tym miejscu będą uznawane za do stosowania w punkcie końcowym usługi, w zależności od tego, co jest wybrane w usługach IIS. Oznacza to, że deweloper można wykluczyć powiedz uwierzytelnianie podstawowe z listy, pomijając go z listy serviceAuthenticationManager, a nawet, jeśli jest włączone w usługach IIS, nie zostanie zastosowana na punkt końcowy usługi  
  
## <a name="self-hosted-services"></a>Usługi samodzielnie hostowane  
 Samodzielnie hostowanej usługi są konfigurowane nieco inaczej, ponieważ nie istnieje żadne usługi IIS mają dziedziczyć ustawienia z. W tym miejscu możesz użyć \<serviceAuthenticationManager > element lub ServiceAuthenticationBehavior do określania ustawień uwierzytelniania, które będą dziedziczone. W kodzie wygląda następująco:  
  
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
  
 W pliku konfiguracyjnym wygląda następująco:  
  
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
  
 A następnie można określić InheritFromHost w ustawieniach powiązania, jak pokazano w poniższym fragmencie kodu XML.  
  
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
  
 Alternatywnie można określić schematów uwierzytelniania w niestandardowym powiązaniu, ustawiając schematów uwierzytelniania na HTTP transportu elementu powiązania, jak pokazano w poniższym fragmencie kodu konfiguracji.  
  
```xml  
<binding name="multipleBinding">  
      <textMessageEncoding/>  
      <httpTransport authenticationScheme="Negotiate, Ntlm, Digest, Basic" />  
    </binding>  
```  
  
## <a name="see-also"></a>Zobacz także
- [Powiązania i zabezpieczenia](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
- [Punkty końcowe: Adresy, powiązania i kontrakty](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Możliwości zabezpieczeń powiązań niestandardowych](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [Powiązania](../../../../docs/framework/wcf/feature-details/bindings.md)
- [Powiązania](../../../../docs/framework/wcf/feature-details/bindings.md)
- [Powiązania niestandardowe](../../../../docs/framework/wcf/extending/custom-bindings.md)
