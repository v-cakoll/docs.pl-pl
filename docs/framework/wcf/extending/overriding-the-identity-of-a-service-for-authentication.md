---
title: Przesłanianie tożsamości usługi na potrzeby uwierzytelniania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d613a22b-07d7-41a4-bada-1adc653b9b5d
ms.openlocfilehash: ec1acc009e58408fc41c60134538340486f19f75
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949676"
---
# <a name="overriding-the-identity-of-a-service-for-authentication"></a>Przesłanianie tożsamości usługi na potrzeby uwierzytelniania
Zazwyczaj nie trzeba ustawiać tożsamości w usłudze, ponieważ wybór typu poświadczeń klienta określa typ tożsamości uwidocznionej w metadanych usługi. Na przykład poniższy kod konfiguracyjny używa `clientCredentialType` [ \<elementu WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) i ustawia atrybut na Windows.  

 Poniższy fragment Web Services Description Language (WSDL) przedstawia tożsamość punktu końcowego zdefiniowanego wcześniej. W tym przykładzie usługa działa jako usługa samodzielna w ramach określonego konta użytkownika (username@contoso.com), w związku z czym tożsamość głównej nazwy użytkownika (UPN) zawiera nazwę konta. Nazwa UPN jest również nazywana nazwą logowania użytkownika w domenie systemu Windows.  

 Aby zapoznać się z przykładową aplikacją, która demonstruje ustawienie tożsamości, zobacz [przykład Identity Service](../../../../docs/framework/wcf/samples/service-identity-sample.md). Aby uzyskać więcej informacji na temat tożsamości usługi, zobacz [tożsamość usługi i uwierzytelnianie](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
## <a name="kerberos-authentication-and-identity"></a>Uwierzytelnianie i tożsamość Kerberos  
 Domyślnie, gdy usługa jest skonfigurowana do korzystania z poświadczeń systemu Windows, [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/userprincipalname.md) [ \<element > Identity](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) , który zawiera element userPrincipalName > lub ServicePrincipalName > jest generowane w języku WSDL. Jeśli usługa `LocalSystem`jest uruchomiona w ramach `NetworkService` `LocalService`konta, lub, nazwa główna usługi (SPN) `host/` \<jest generowana domyślnie w postaci nazwy *hosta*> ponieważ te konta mają dostęp do dane SPN komputera. Jeśli usługa jest uruchomiona przy użyciu innego konta, Windows Communication Foundation (WCF) \<generuje nazwę UPN w postaci>@<`>` *nazwy użytkownika* *nazwa_domeny*. Dzieje się tak, ponieważ uwierzytelnianie Kerberos wymaga, aby nazwa UPN lub nazwa SPN była dostarczana do klienta w celu uwierzytelnienia usługi.  
  
 Można również użyć narzędzia Setspn. exe do zarejestrowania dodatkowej nazwy SPN z kontem usługi w domenie. Następnie można użyć nazwy SPN jako tożsamości usługi. Aby pobrać narzędzie, zobacz [Windows 2000 Resource Kit Tool: Setspn.exe](https://go.microsoft.com/fwlink/?LinkId=91752). Więcej informacji o narzędziu można znaleźć w temacie [Setspn Overview](https://go.microsoft.com/fwlink/?LinkId=61374).  
  
> [!NOTE]
> Aby użyć typu poświadczeń systemu Windows bez negocjowania, konto użytkownika usługi musi mieć dostęp do nazwy SPN, która jest zarejestrowana w domenie Active Directory. Można to zrobić w następujący sposób:  
  
- Użyj konta NetworkService lub LocalSystem do uruchomienia usługi. Ponieważ te konta mają dostęp do nazwy SPN maszyny, która została ustanowiona, gdy komputer jest przyłączony do domeny Active Directory, funkcja WCF automatycznie generuje prawidłowy element SPN w ramach punktu końcowego usługi w metadanych usługi (WSDL).  
  
- Użyj dowolnego konta domeny Active Directory, aby uruchomić usługę. W takim przypadku należy ustanowić nazwę SPN dla tego konta domeny, którą można wykonać za pomocą narzędzia narzędzia Setspn. exe. Po utworzeniu nazwy SPN dla konta usługi Skonfiguruj program WCF do publikowania tej nazwy SPN na klientach usługi za pomocą metadanych (WSDL). W tym celu należy ustawić tożsamość punktu końcowego dla uwidocznionego punktu końcowego za pomocą pliku lub kodu konfiguracji aplikacji.  
  
 Aby uzyskać więcej informacji na temat nazw SPN, protokołu Kerberos i Active Directory, zobacz [dodatek dotyczący protokołu Kerberos dla systemu Windows](https://go.microsoft.com/fwlink/?LinkId=88330).  
  
### <a name="when-spn-or-upn-equals-the-empty-string"></a>Gdy nazwa SPN lub nazwa UPN jest równa pustemu ciągowi  
 Jeśli ustawisz nazwę SPN lub nazwę UPN równą pustemu ciągowi, następuje wiele różnych rzeczy, w zależności od poziomu zabezpieczeń i używanego trybu uwierzytelniania:  
  
- W przypadku korzystania z zabezpieczeń na poziomie transportu jest wybierane uwierzytelnianie NT LanMan (NTLM).  
  
- W przypadku korzystania z zabezpieczeń na poziomie komunikatów uwierzytelnianie może zakończyć się niepowodzeniem, w zależności od trybu uwierzytelniania:  
  
- Jeśli używasz `spnego` trybu, `AllowNtlm` a atrybut jest ustawiony na `false`, uwierzytelnianie kończy się niepowodzeniem.  
  
- Jeśli używasz `AllowNtlm`trybu, a atrybut jest ustawiony na `true`, uwierzytelnianie kończy się niepowodzeniem, jeśli główna nazwa użytkownika jest pusta, ale zostanie ukończona, jeśli nazwa SPN jest pusta. `spnego`  
  
- W przypadku korzystania z protokołu Kerberos Direct (znanego również jako "z pojedynczym zrzutem") uwierzytelnianie kończy się niepowodzeniem.  
  
### <a name="using-the-identity-element-in-configuration"></a>Używanie elementu \<Identity > w konfiguracji  
 Jeśli zmienisz typ poświadczeń klienta w powiązaniu wcześniej pokazanym na`,` certyfikacie, wygenerowany kod WSDL zawiera certyfikat X. 509 z serializowanym algorytmem Base64 dla wartości tożsamości, jak pokazano w poniższym kodzie. Jest to wartość domyślna dla wszystkich typów poświadczeń klienta innych niż Windows.  

 Można zmienić wartość domyślnej tożsamości usługi lub zmienić typ tożsamości przy użyciu <`identity`elementu > w konfiguracji lub przez ustawienie tożsamości w kodzie. Poniższy kod konfiguracji ustawia tożsamość systemu nazw domen (DNS) z wartością `contoso.com`.  

### <a name="setting-identity-programmatically"></a>Programowo Ustawianie tożsamości  
 Usługa nie musi jawnie określać tożsamości, ponieważ funkcja WCF automatycznie ją określa. Jednak funkcja WCF umożliwia określenie tożsamości w punkcie końcowym, jeśli jest to wymagane. Poniższy kod dodaje nowy punkt końcowy usługi z określoną tożsamością DNS.  
  
 [!code-csharp[C_Identity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#5)]
 [!code-vb[C_Identity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#5)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Tworzenie niestandardowego weryfikatora tożsamości klienta](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)
- [Uwierzytelnianie i tożsamość usług](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
