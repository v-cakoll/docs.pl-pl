---
title: Przesłanianie tożsamości usługi na potrzeby uwierzytelniania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d613a22b-07d7-41a4-bada-1adc653b9b5d
ms.openlocfilehash: a5a32220ad1f638bf2e93051e9b436d8270aec2f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59082194"
---
# <a name="overriding-the-identity-of-a-service-for-authentication"></a>Przesłanianie tożsamości usługi na potrzeby uwierzytelniania
Zazwyczaj nie trzeba ustawić tożsamość usługi, ponieważ wybór typu poświadczeń klienta decyduje o rodzaju tożsamości widoczne w metadanych usługi. Na przykład, poniższy kod konfiguracji używa [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elementu i zestawy `clientCredentialType` atrybutu Windows.  

 Poniższy fragment Web Services Description Language (WSDL) zawiera tożsamości dla punkt końcowy wcześniej zdefiniowany. W tym przykładzie usługa jest uruchomiona jako usługa samodzielnie hostowanej w ramach określonego konta użytkownika (username@contoso.com), dlatego tożsamości użytkownika głównej nazwy (UPN) zawiera nazwę konta. Nazwa UPN jest również nazywany nazwy logowania użytkownika w domenie Windows.  

 Aby uzyskać przykładową aplikację prezentującą ustawienie tożsamości, zobacz [tożsamość usług — przykład](../../../../docs/framework/wcf/samples/service-identity-sample.md). Aby uzyskać więcej informacji na temat tożsamości usługi zobacz [uwierzytelnianie i tożsamość usług](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
## <a name="kerberos-authentication-and-identity"></a>Uwierzytelnianie Kerberos i tożsamości  
 Domyślnie, gdy usługa jest skonfigurowana do używania poświadczeń Windows [ \<tożsamości >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) element, który zawiera [ \<userPrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/userprincipalname.md) lub [ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) element jest generowany w pliku WSDL. Jeśli usługa jest uruchomiona w ramach `LocalSystem`, `LocalService`, lub `NetworkService` konta, usługi głównej nazwy (usługi SPN) została wygenerowana domyślnie w formie `host/` \< *hostname*> ponieważ te konta mają dostęp do danych nazwę SPN tego komputera. Jeśli usługa jest uruchomiona przy użyciu innego konta, Windows Communication Foundation (WCF) generuje nazwy UPN w postaci \< *username*>@<*nazwa_domeny* `>` . Dzieje się tak, ponieważ uwierzytelnianie Kerberos wymaga nazwy UPN lub nazwy SPN dostarczenia klienta do uwierzytelnienia usługi.  
  
 Można również użyć narzędzia Setspn.exe rejestrowania dodatkowe nazwy SPN przy użyciu konta usługi w domenie. Nazwy SPN można następnie użyć jako tożsamość usługi. Aby pobrać to narzędzie, zobacz [Windows 2000 Resource Kit narzędzie: Setspn.exe](https://go.microsoft.com/fwlink/?LinkId=91752). Aby uzyskać więcej informacji o tym narzędziu, zobacz [Setspn — omówienie](https://go.microsoft.com/fwlink/?LinkId=61374).  
  
> [!NOTE]
>  Aby użyć typu poświadczeń Windows bez negocjowania, konto użytkownika usługi musi mieć dostęp do nazwy SPN, który jest zarejestrowany w domenie usługi Active Directory. Można to zrobić w następujący sposób:  
  
-   Użyj konta NetworkService lub LocalSystem do uruchomienia usługi. Ponieważ te konta dostępu do komputera, nazwę SPN, który jest ustanawiane, jeśli komputer jest przyłączony do domeny usługi Active Directory, usługi WCF automatycznie generuje prawidłowego elementu SPN wewnątrz punktu końcowego usługi usługi metadanych (WSDL).  
  
-   Użyj dowolnego konta domeny usługi Active Directory do uruchomienia usługi. W takim przypadku należy ustanowić nazwę SPN dla tego konta domeny, co można zrobić za pomocą narzędzia narzędzia Setspn.exe. Po utworzeniu nazwy SPN dla konta usługi, należy skonfigurować usługi WCF do opublikowania tej nazwy SPN do obsługi klientów za pośrednictwem jego metadanych (WSDL). To zrobić, ustawiając tożsamość punktu końcowego narażonych punktu końcowego za pomocą pliku konfiguracji aplikacji lub kodu.  
  
 Aby uzyskać więcej informacji na temat nazw głównych usług, protokołu Kerberos i usługi Active Directory, zobacz [Kerberos technicznego dodatku dla Windows](https://go.microsoft.com/fwlink/?LinkId=88330).  
  
### <a name="when-spn-or-upn-equals-the-empty-string"></a>Jeśli nazwy SPN i UPN jest równe pusty ciąg  
 Jeśli jest ustawiony nazwy SPN i UPN na pusty ciąg, liczbę różnych rzeczy i tak się stanie w zależności od trybu poziom i uwierzytelniania zabezpieczeń używane:  
  
-   Jeśli używane są zabezpieczenia na poziomie transportu, jest wybierany uwierzytelniania NT LanMan (NTLM).  
  
-   Jeśli używane są zabezpieczenia na poziomie komunikatu, uwierzytelnianie może zakończyć się niepowodzeniem, w zależności od trybu uwierzytelniania:  
  
-   Jeśli używasz `spnego` tryb i `AllowNtlm` ma ustawioną wartość atrybutu `false`, niepowodzenie uwierzytelniania.  
  
-   Jeśli używasz `spnego` tryb i `AllowNtlm` ma ustawioną wartość atrybutu `true`, uwierzytelnianie nie powiedzie się, jeśli nazwa UPN jest pusta, ale zakończy się pomyślnie, jeśli nazwa SPN jest pusta.  
  
-   Jeśli używasz protokołu Kerberos bezpośrednio (znany także jako "jednorazowej"), uwierzytelnianie nie powiedzie się.  
  
### <a name="using-the-identity-element-in-configuration"></a>Za pomocą \<tożsamości > Element w konfiguracji  
 Jeśli zmienisz typ poświadczeń klienta w powiązaniu z wcześniejszymi certyfikatem`,` wygenerowanego pliku WSDL zawiera Base64 z serializacji, a następnie certyfikat X.509 dla wartości tożsamości, jak pokazano w poniższym kodzie. Jest to wartość domyślna dla wszystkich typów poświadczeń klienta inne niż Windows.  

 Można zmienić wartości domyślnej tożsamości usługi lub zmienić typ tożsamości za pomocą <`identity`> element konfiguracji lub przez ustawienie tożsamości w kodzie. Poniższy kod konfiguracji ustawia tożsamość system (DNS) nazwę domeny, z wartością `contoso.com`.  

### <a name="setting-identity-programmatically"></a>Programowe Ustawianie tożsamości  
 Usługa nie ma jawnie określić tożsamości, ponieważ automatycznie określa WCF. Jednak WCF można określić tożsamość w punkcie końcowym, jeśli jest to wymagane. Poniższy kod dodaje nowy punkt końcowy usługi w kontekście określonej tożsamości DNS.  
  
 [!code-csharp[C_Identity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#5)]
 [!code-vb[C_Identity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#5)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: tworzenie niestandardowego weryfikatora tożsamości klienta](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)
- [Uwierzytelnianie i tożsamość usług](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
