---
title: '&lt;message&gt; w &lt;netMsmqBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: 0e947667c414079f24398b401456efd56bf9922c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ltmessagegt-of-ltnetmsmqbindinggt"></a>&lt;message&gt; w &lt;netMsmqBinding&gt;
Definiuje ustawienia zabezpieczeń wiadomości SOAP na tym `netMsmqBinding` powiązania.  
  
 \<system.ServiceModel>  
\<powiązania >  
\<netMsmqBinding>  
\<Powiązanie >  
\<Zabezpieczenia >  
\<message>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<netMsmqBinding>  
    <binding>  
      <security>  
         <message   
                      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />  
    </security>  
</netMsmqBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|algorithmSuite|Ustawia komunikat algorytmów szyfrowania i zawijania klucza, które są używane do uzyskania zabezpieczenia oparte na komunikatu dla komunikatów wysyłanych za pośrednictwem transportu MSMQ.<br /><br /> Wartość domyślna to `Aes256`. Ten atrybut jest typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.|  
|clientCredentialType|Określa typ poświadczenia, które będą używane podczas uwierzytelniania klienta dla komunikatów wysyłanych za pomocą transportu MSMQ. Prawidłowe wartości są następujące:<br /><br /> -Brak: Dzięki usłudze na współdziałanie z anonimowego klientów. Usługa ani klient wymagane jest podanie poświadczeń.<br />-Windows: Umożliwia wymianę SOAP się pod uwierzytelnionego kontekstu poświadczenia systemu Windows. To jest zawsze przeprowadza uwierzytelnianie za pomocą protokołu Kerberos.<br />-UserName: Włącza usługę, aby wymagać który uwierzytelnienia klienta przy użyciu poświadczeń UserName. Poświadczenia w takim przypadku należy określić przy użyciu `clientCredentials` zachowanie **Przestroga:** Windows Communication Foundation (WCF) nie obsługuje wysyłanie hasła szyfrowane lub wyprowadzanie kluczy przy użyciu hasła i te klucze dla zabezpieczenia komunikatów. W związku z tym WCF wymusza, że programu exchange jest zabezpieczone przy użyciu poświadczeń UserName. Ten tryb wymaga określenia certyfikatu usługi przy użyciu po stronie klienta `clientCredential` zachowania i `serviceCertificate`. <br /><br /> -Certyfikat: Włącza usługę, aby wymagać który uwierzytelnienia klienta za pomocą certyfikatu. W takim przypadku poświadczeń klienta należy określić przy użyciu `clientCredentials` zachowanie. Poświadczenia usługi w takim przypadku należy określić przy użyciu `clientCredentials` zachowanie, określając `serviceCertificate`.<br />-CardSpace: Umożliwia usłudze wymagają który uwierzytelnienia klienta za pomocą programu CardSpace. `serviceCertiifcate` Należy udostępnić w `clientCredential` zachowanie.<br /><br /> Wartość domyślna to `Windows`. Ten atrybut jest typu <xref:System.ServiceModel.MessageCredentialType>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Zabezpieczenia >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|Definiuje ustawienia zabezpieczeń dla powiązania.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>  
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>  
 <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>  
 <xref:System.ServiceModel.MessageSecurityOverMsmq>  
 [Kolejki programu WCF](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurowanie powiązań dostarczanych przez system](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)
