---
title: Używanie wielu schematów uwierzytelniania z programem WCF
ms.date: 03/30/2017
ms.assetid: f32a56a0-e2b2-46bf-a302-29e1275917f9
ms.openlocfilehash: 1874963573a6ec12939bd12b79574f1e2c889bfd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600221"
---
# <a name="using-multiple-authentication-schemes-with-wcf"></a>Używanie wielu schematów uwierzytelniania z programem WCF
Funkcja WCF umożliwia teraz określenie wielu schematów uwierzytelniania w jednym punkcie końcowym. Ponadto usługi hostowane w sieci Web mogą dziedziczyć ustawienia uwierzytelniania bezpośrednio z usług IIS. Usługi samoobsługowe mogą określać, które schematy uwierzytelniania mogą być używane. Aby uzyskać więcej informacji na temat ustawiania ustawień uwierzytelniania w usługach IIS, zobacz [uwierzytelnianie usług IIS](https://go.microsoft.com/fwlink/?LinkId=232458) .  
  
## <a name="iis-hosted-services"></a>Usługi hostowane przez usługi IIS  
 W przypadku usług hostowanych przez usługi IIS Ustaw schematy uwierzytelniania, które mają być używane w usługach IIS. Następnie w pliku Web. config usługi w konfiguracji powiązania Określ obiekt clientCredential Type jako "InheritedFromHost", jak pokazano w poniższym fragmencie kodu XML:  
  
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
  
 Można określić, że tylko podzbiór schematów uwierzytelniania ma być używany z usługą przy użyciu ServiceAuthenticationBehavior lub \<serviceAuthenticationManager> elementu. Podczas konfigurowania tego programu w kodzie Użyj ServiceAuthenticationBehavior, jak pokazano w poniższym fragmencie kodu.  
  
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
  
 W przypadku konfigurowania tego elementu w pliku konfiguracji, należy użyć \<serviceAuthenticationManager> element, jak pokazano w poniższym fragmencie kodu XML.  
  
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
  
 Zapewni to, że tylko podzestaw schematów uwierzytelniania wymienionych w tym miejscu zostanie uwzględniony w punkcie końcowym usługi, w zależności od tego, co jest wybrane w usługach IIS. Oznacza to, że deweloper może wykluczyć uwierzytelnianie podstawowe na liście, pomijając je z listy ServiceAuthenticationManager, a nawet jeśli jest włączona w usługach IIS, nie zostanie zastosowana w punkcie końcowym usługi.  
  
## <a name="self-hosted-services"></a>Usługi samoobsługowe  
 Usługi samoobsługowe są skonfigurowane nieco inaczej, ponieważ nie ma żadnych usług IIS do dziedziczenia ustawień. W tym miejscu Użyj \<serviceAuthenticationManager> elementu lub ServiceAuthenticationBehavior, aby określić ustawienia uwierzytelniania, które będą dziedziczone. W kodzie wygląda to następująco:  
  
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
  
 W konfiguracji wygląda to następująco:  
  
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
  
 Alternatywnie możesz określić schematy uwierzytelniania w niestandardowym powiązaniu, ustawiając schematy uwierzytelniania w elemencie powiązania transportu HTTP, jak pokazano w poniższym fragmencie kodu.  
  
```xml  
<binding name="multipleBinding">  
      <textMessageEncoding/>  
      <httpTransport authenticationScheme="Negotiate, Ntlm, Digest, Basic" />  
    </binding>  
```  
  
## <a name="see-also"></a>Zobacz też

- [Wiązania i zabezpieczenia](bindings-and-security.md)
- [Punkty końcowe: Adresy, powiązania i kontrakty](endpoints-addresses-bindings-and-contracts.md)
- [Konfigurowanie powiązań dostarczanych przez system](configuring-system-provided-bindings.md)
- [Możliwości zabezpieczeń powiązań niestandardowych](security-capabilities-with-custom-bindings.md)
- [Powiązania](bindings.md)
- [Powiązania niestandardowe](../extending/custom-bindings.md)
