---
title: Przesłanianie tożsamości usługi na potrzeby uwierzytelniania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d613a22b-07d7-41a4-bada-1adc653b9b5d
ms.openlocfilehash: e7273c1e140e52eb37a30b6cabeb9e9a83a6fa2d
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121560"
---
# <a name="override-the-identity-of-a-service-for-authentication"></a>Zastępowanie tożsamości usługi do uwierzytelniania

Zazwyczaj nie trzeba ustawiać tożsamości w usłudze, ponieważ wybór typu poświadczeń klienta dyktuje typ tożsamości udostępniane w metadanych usługi. Na przykład poniższy kod konfiguracji używa elementu [ \<>wsHttpBinding](../../configure-apps/file-schema/wcf/wshttpbinding.md) `clientCredentialType` i ustawia atrybut dla systemu Windows.  

 Poniższy fragment języka opisu usług sieci Web (WSDL) pokazuje tożsamość punktu końcowego wcześniej zdefiniowanego. W tym przykładzie usługa jest uruchomiona jako usługa hostowana samodzielnieusername@contoso.comna określonym koncie użytkownika ( ) i dlatego tożsamość głównej nazwy użytkownika (UPN) zawiera nazwę konta. Nazwa UPN jest również znana jako nazwa logowania użytkownika w domenie systemu Windows.  

 Aby uzyskać przykładową aplikację, która demonstruje ustawienie tożsamości, zobacz [Przykład tożsamości usługi](../samples/service-identity-sample.md). Aby uzyskać więcej informacji na temat tożsamości usługi, zobacz [Tożsamość usługi i uwierzytelnianie](../feature-details/service-identity-and-authentication.md).  
  
## <a name="kerberos-authentication-and-identity"></a>Uwierzytelnianie i tożsamość protokołu Kerberos  
 Domyślnie, gdy usługa jest skonfigurowana do używania poświadczeń systemu Windows, [ \<element tożsamości>,](../../configure-apps/file-schema/wcf/identity.md) który zawiera [ \<element>>userPrincipalName](../../configure-apps/file-schema/wcf/userprincipalname.md) lub [ \<servicePrincipalName>jest](../../configure-apps/file-schema/wcf/serviceprincipalname.md) generowany w WSDL. Jeśli usługa jest uruchomiona `LocalSystem` `LocalService`w `NetworkService` obszarze , lub konto, nazwa główna usługi (SPN) jest generowany domyślnie w postaci `host/` \< *nazwy hosta*>, ponieważ te konta mają dostęp do danych SPN komputera. Jeśli usługa działa na innym koncie, Windows Communication Foundation (WCF) generuje \<nazwę UPN w postaci *nazwy użytkownika*>@<*domainName*`>`. Dzieje się tak, ponieważ uwierzytelnianie Kerberos wymaga dostarczenia do klienta nazwy UPN lub nazwy SPN w celu uwierzytelnienia usługi.  
  
 Można również użyć narzędzia [Setspn,](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731241(v=ws.10)?redirectedfrom=MSDN) aby zarejestrować dodatkową nazwę SPN z kontem usługi w domenie. Następnie można użyć nazwy SPN jako tożsamości usługi. Aby uzyskać więcej informacji na temat narzędzia, zobacz [Przegląd setspn](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc773257(v=ws.10)).  
  
> [!NOTE]
> Aby używać typu poświadczeń systemu Windows bez negocjacji, konto użytkownika usługi musi mieć dostęp do nazwy SPN zarejestrowanej w domenie usługi Active Directory. Można to zrobić w następujący sposób:  
  
- Użyj konta NetworkService lub LocalSystem, aby uruchomić usługę. Ponieważ te konta mają dostęp do nazwy SPN komputera, który jest ustanawiany, gdy maszyna dołącza do domeny usługi Active Directory, WCF automatycznie generuje odpowiedni element SPN wewnątrz punktu końcowego usługi w metadanych usługi (WSDL).  
  
- Użyj dowolnego konta domeny usługi Active Directory, aby uruchomić usługę. W takim przypadku należy ustanowić nazwę SPN dla tego konta domeny, co można zrobić za pomocą narzędzia Setspn.exe. Po utworzeniu nazwy SPN dla konta usługi, należy skonfigurować WCF, aby opublikować tej nazwy SPN do klientów usługi za pośrednictwem jego metadanych (WSDL). Odbywa się to przez ustawienie tożsamości punktu końcowego dla narażonego punktu końcowego, za pośrednictwem pliku konfiguracji aplikacji lub kodu.  
  
 Aby uzyskać więcej informacji na temat spn, protokołu Kerberos i usługi Active Directory, zobacz [Dodatek techniczny protokołu Kerberos dla systemu Windows](https://docs.microsoft.com/previous-versions/msp-n-p/ff649429(v=pandp.10)).  
  
### <a name="when-spn-or-upn-equals-the-empty-string"></a>Gdy nazwa SPN lub UPN jest równa pustemu ciągowi  
 Jeśli nazwa SPN lub UPN jest równa pustemu ciągowi, wydarzy się wiele różnych rzeczy, w zależności od używanego poziomu zabezpieczeń i trybu uwierzytelniania:  
  
- Jeśli używasz zabezpieczeń na poziomie transportu, wybierane jest uwierzytelnianie NT LanMan (NTLM).  
  
- Jeśli używasz zabezpieczeń na poziomie wiadomości, uwierzytelnianie może zakończyć się niepowodzeniem, w zależności od trybu uwierzytelniania:  
  
- Jeśli używasz `spnego` trybu `AllowNtlm` i atrybut jest `false`ustawiony na , uwierzytelnianie nie powiedzie się.  
  
- Jeśli używasz `spnego` trybu `AllowNtlm` i atrybut jest `true`ustawiony na , uwierzytelnianie kończy się niepowodzeniem, jeśli nazwa UPN jest pusta, ale powiedzie się, jeśli nazwa SPN jest pusta.  
  
- Jeśli używasz protokołu Kerberos direct (znanego również jako "one-shot"), uwierzytelnianie kończy się niepowodzeniem.  
  
### <a name="using-the-identity-element-in-configuration"></a>Korzystanie \<z elementu> tożsamości w konfiguracji  
 Jeśli zmienisz typ poświadczeń klienta`,` w powiązaniu wcześniej pokazanym certyfikatowi, wygenerowany WSDL zawiera szeregowany certyfikat X.509 base64 dla wartości tożsamości, jak pokazano w poniższym kodzie. Jest to wartość domyślna dla wszystkich typów poświadczeń klienta innych niż Windows.  

 Można zmienić wartość domyślnej tożsamości usługi lub zmienić typ tożsamości przy `identity` użyciu <> element w konfiguracji lub ustawiając tożsamość w kodzie. Poniższy kod konfiguracji ustawia tożsamość systemu nazw `contoso.com`domen (DNS) z wartością .  

### <a name="setting-identity-programmatically"></a>Programowo ustawianie tożsamości  
 Usługa nie musi jawnie określić tożsamość, ponieważ WCF automatycznie określa go. Jednak WCF umożliwia określenie tożsamości w punkcie końcowym, jeśli jest to wymagane. Poniższy kod dodaje nowy punkt końcowy usługi z określoną tożsamością DNS.  
  
 [!code-csharp[C_Identity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#5)]
 [!code-vb[C_Identity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#5)]  
  
## <a name="see-also"></a>Zobacz też

- [Instrukcje: tworzenie niestandardowego weryfikatora tożsamości klienta](how-to-create-a-custom-client-identity-verifier.md)
- [Uwierzytelnianie i tożsamość usług](../feature-details/service-identity-and-authentication.md)
