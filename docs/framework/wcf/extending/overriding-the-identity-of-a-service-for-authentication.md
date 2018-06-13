---
title: Przesłanianie tożsamości usługi na potrzeby uwierzytelniania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d613a22b-07d7-41a4-bada-1adc653b9b5d
ms.openlocfilehash: 3df1f2490f8636d52ac75fad2469adadec2a57da
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806945"
---
# <a name="overriding-the-identity-of-a-service-for-authentication"></a>Przesłanianie tożsamości usługi na potrzeby uwierzytelniania
Zazwyczaj nie trzeba ustawić tożsamość w usłudze, ponieważ typ tożsamości w metadanych usługi nakazują wybór typu poświadczeń klienta. Na przykład w poniższym kodzie konfiguracji użyto [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element i zestawy `clientCredentialType` atrybutu do systemu Windows.  
  
  
  
 Poniższy fragment Web Services Description Language (WSDL) zawiera tożsamość punktu końcowego wcześniej zdefiniowany. W tym przykładzie usługa jest uruchomiona jako usługa samodzielnie hostowana w obszarze konta określonego użytkownika (username@contoso.com), dlatego tożsamości użytkownika (UPN) Nazwa główna zawiera nazwę konta. Nazwa UPN nosi również nazwę logowania użytkownika w domenie systemu Windows.  
  
  
  
 Przykładową aplikację prezentującą ustawienie tożsamości, zobacz [tożsamość usług — przykład](../../../../docs/framework/wcf/samples/service-identity-sample.md). Aby uzyskać więcej informacji o tożsamości usługi, zobacz [uwierzytelnianie i tożsamość usługi](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
## <a name="kerberos-authentication-and-identity"></a>Uwierzytelnianie Kerberos i tożsamość  
 Domyślnie, gdy usługa jest skonfigurowana do używania poświadczeń systemu Windows [ \<tożsamości >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) element, który zawiera [ \<userPrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/userprincipalname.md) lub [ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) element jest generowany w formacie WSDL. Jeśli usługa jest uruchomiona w obszarze `LocalSystem`, `LocalService`, lub `NetworkService` konto, usługi głównej nazwy (usługi SPN) jest generowany domyślnie w formie `host/` \< *hostname*> ponieważ te konta mają dostęp do danych SPN komputera. Jeśli usługa jest uruchomiona przy użyciu innego konta, Windows Communication Foundation (WCF) generuje nazwy UPN w formie \< *username*>@<*domainName* `>` . Dzieje się tak, ponieważ wymaga uwierzytelniania Kerberos, należy podać nazwy UPN lub nazwy SPN do klienta do uwierzytelniania usługi.  
  
 Można także użyć narzędzia Setspn.exe rejestrowania nazwy SPN dodatkowych z kontem usługi w domenie. Można następnie użyć nazwy SPN jako tożsamość usługi. Aby pobrać to narzędzie, zobacz [systemu Windows 2000 Resource Kit narzędzie: Setspn.exe](http://go.microsoft.com/fwlink/?LinkId=91752). Aby uzyskać więcej informacji o tym narzędziu, zobacz [Omówienie narzędzia Setspn](http://go.microsoft.com/fwlink/?LinkId=61374).  
  
> [!NOTE]
>  Aby użyć typu poświadczeń systemu Windows bez negocjowania, konto użytkownika usługi musi mieć dostęp do głównej nazwy usługi, które jest zarejestrowane w domenie usługi Active Directory. Można to zrobić w następujący sposób:  
  
-   Użyj konta NetworkService lub LocalSystem uruchamiania usługi. Ponieważ te konta dostępu do komputera, nazwę SPN, który zostanie nawiązane, gdy komputer jest dołączany do domeny usługi Active Directory, usługi WCF automatycznie generuje prawidłowego elementu SPN w punkt końcowy usługi w metadanych usługi (WSDL).  
  
-   Użyj dowolnego konta domeny usługi Active Directory do uruchomienia usługi. W takim przypadku ustanowić nazwę SPN dla tego konta domeny, co można zrobić za pomocą narzędzia Narzędzie Setspn.exe. Po utworzeniu nazwy SPN konta usługi, należy skonfigurować usług WCF do opublikowania tej nazwy SPN do obsługi klientów za pośrednictwem jego metadanych (WSDL). Jest to realizowane przez ustawienie tożsamość punktu końcowego dla dostępnego punktu końcowego, albo za pomocą pliku konfiguracji aplikacji lub kodu.  
  
 Aby uzyskać więcej informacji na temat nazw SPN, protokołu Kerberos i usługi Active Directory, zobacz [Kerberos techniczne dodatku dla systemu Windows](http://go.microsoft.com/fwlink/?LinkId=88330).  
  
### <a name="when-spn-or-upn-equals-the-empty-string"></a>Kiedy nazwa SPN i UPN jest równa pusty ciąg  
 Jeśli jest ustawiony SPN i UPN na pusty ciąg, liczbę różnych rzeczy wystąpi, w zależności od poziomu i uwierzytelnianie trybu zabezpieczeń używany:  
  
-   Jeśli używane są zabezpieczenia na poziomie transportu, jest wybierany uwierzytelniania LanMan NT (NTLM).  
  
-   Jeśli korzystasz z zabezpieczeniami na poziomie wiadomości, uwierzytelnianie może zakończyć się niepowodzeniem, w zależności od trybu uwierzytelniania:  
  
-   Jeśli używasz `spnego` tryb i `AllowNtlm` atrybut ma ustawioną `false`, niepowodzenie uwierzytelniania.  
  
-   Jeśli używasz `spnego` tryb i `AllowNtlm` atrybut ma ustawioną `true`, uwierzytelnianie nie powiedzie się, jeśli nazwa UPN jest pusty, ale zakończy się pomyślnie, jeśli nazwa SPN jest pusta.  
  
-   Jeśli używasz protokołu Kerberos bezpośrednio (znanej także jako "jednorazowej"), uwierzytelnianie nie powiedzie się.  
  
### <a name="using-the-identity-element-in-configuration"></a>Przy użyciu \<tożsamości > Element w konfiguracji  
 Jeśli zmienisz typ poświadczeń klienta w powiązaniu pokazano wcześniej certyfikatem`,` wygenerowanego WSDL zawiera seryjnych Base64 certyfikatu X.509 do wartości tożsamości, jak pokazano w poniższym kodzie. Jest to wartość domyślna dla wszystkich typów poświadczeń klienta innych niż Windows.  
  
  
  
 Możesz zmienić wartość domyślną tożsamość usługi lub zmień typ tożsamości za pomocą <`identity`> element w konfiguracji lub ustawiając tożsamość w kodzie. Poniższy kod konfiguracji ustawia tożsamość systemu (nazw domen DNS) nazwy domeny, z wartością `contoso.com`.  
  
  
  
### <a name="setting-identity-programmatically"></a>Ustawienie programowo tożsamości  
 Usługi nie trzeba jawnie określić tożsamości, ponieważ automatycznie określa WCF. Jednak WCF można określić tożsamości dla punktu końcowego, jeśli jest to wymagane. Poniższy kod dodaje nowy punkt końcowy usługi o określonej tożsamości DNS.  
  
 [!code-csharp[C_Identity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#5)]
 [!code-vb[C_Identity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#5)]  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: tworzenie niestandardowego weryfikatora tożsamości klienta](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)  
 [Uwierzytelnianie i tożsamość usług](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
