---
title: "Przesłanianie tożsamości usługi na potrzeby uwierzytelniania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d613a22b-07d7-41a4-bada-1adc653b9b5d
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6a3125504326f2cb129fef6f1f3e01dba577f599
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="overriding-the-identity-of-a-service-for-authentication"></a>Przesłanianie tożsamości usługi na potrzeby uwierzytelniania
Zazwyczaj nie trzeba ustawić tożsamość w usłudze, ponieważ typ tożsamości w metadanych usługi nakazują wybór typu poświadczeń klienta. Na przykład w poniższym kodzie konfiguracji użyto [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element i zestawy `clientCredentialType` atrybutu do systemu Windows.  
  
  
  
 Poniższy fragment Web Services Description Language (WSDL) zawiera tożsamość punktu końcowego wcześniej zdefiniowany. W tym przykładzie usługa jest uruchomiona jako usługa samodzielnie hostowana w obszarze konta określonego użytkownika (username@contoso.com), dlatego tożsamości użytkownika (UPN) Nazwa główna zawiera nazwę konta. Nazwa UPN nosi również nazwę logowania użytkownika w domenie systemu Windows.  
  
  
  
 Przykładową aplikację prezentującą ustawienie tożsamości, zobacz [tożsamość usług — przykład](../../../../docs/framework/wcf/samples/service-identity-sample.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Usługa tożsamości, zobacz [uwierzytelnianie i tożsamość usługi](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
## <a name="kerberos-authentication-and-identity"></a>Uwierzytelnianie Kerberos i tożsamość  
 Domyślnie, gdy usługa jest skonfigurowana do używania poświadczeń systemu Windows [ \<tożsamości >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) element, który zawiera [ \<userPrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/userprincipalname.md) lub [ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) element jest generowany w formacie WSDL. Jeśli usługa jest uruchomiona w obszarze `LocalSystem`, `LocalService`, lub `NetworkService` konto, usługi głównej nazwy (usługi SPN) jest generowany domyślnie w formie `host/` \< *hostname*> ponieważ te konta mają dostęp do danych SPN komputera. Jeśli usługa jest uruchomiona przy użyciu innego konta [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] generuje nazwy UPN w formie \< *username*>@<*domainName*`>`. Dzieje się tak, ponieważ wymaga uwierzytelniania Kerberos, należy podać nazwy UPN lub nazwy SPN do klienta do uwierzytelniania usługi.  
  
 Można także użyć narzędzia Setspn.exe rejestrowania nazwy SPN dodatkowych z kontem usługi w domenie. Można następnie użyć nazwy SPN jako tożsamość usługi. Aby pobrać to narzędzie, zobacz [systemu Windows 2000 Resource Kit narzędzie: Setspn.exe](http://go.microsoft.com/fwlink/?LinkId=91752). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Narzędzie, zobacz [Omówienie narzędzia Setspn](http://go.microsoft.com/fwlink/?LinkId=61374).  
  
> [!NOTE]
>  Aby użyć typu poświadczeń systemu Windows bez negocjowania, konto użytkownika usługi musi mieć dostęp do głównej nazwy usługi, które jest zarejestrowane w domenie usługi Active Directory. Można to zrobić w następujący sposób:  
  
-   Użyj konta NetworkService lub LocalSystem uruchamiania usługi. Ponieważ te konta ma dostęp do komputera, nazwę SPN, który zostanie nawiązane, gdy komputer jest dołączany domeny usługi Active Directory [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] automatycznie generuje prawidłowego elementu SPN w punkt końcowy usługi w metadanych usługi (WSDL).  
  
-   Użyj dowolnego konta domeny usługi Active Directory do uruchomienia usługi. W takim przypadku ustanowić nazwę SPN dla tego konta domeny, co można zrobić za pomocą narzędzia Narzędzie Setspn.exe. Po utworzeniu nazwy SPN konta usługi, należy skonfigurować [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] do opublikowania tej nazwy SPN do obsługi klientów za pośrednictwem jego metadanych (WSDL). Jest to realizowane przez ustawienie tożsamość punktu końcowego dla dostępnego punktu końcowego, albo za pomocą pliku konfiguracji aplikacji lub kodu.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Nazwy SPN, protokołu Kerberos i usługi Active Directory, zobacz [Kerberos techniczne dodatku dla systemu Windows](http://go.microsoft.com/fwlink/?LinkId=88330).  
  
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
 Usługi nie trzeba jawnie określać tożsamości, ponieważ [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] automatycznie określa go. Jednak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] służy do określania tożsamości dla punktu końcowego, jeśli jest to wymagane. Poniższy kod dodaje nowy punkt końcowy usługi o określonej tożsamości DNS.  
  
 [!code-csharp[C_Identity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#5)]
 [!code-vb[C_Identity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#5)]  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: tworzenie weryfikatora tożsamości niestandardowego klienta](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)  
 [Uwierzytelnianie i tożsamość usług](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
