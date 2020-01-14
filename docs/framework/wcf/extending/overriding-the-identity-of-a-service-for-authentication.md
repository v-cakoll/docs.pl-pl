---
title: Przesłanianie tożsamości usługi na potrzeby uwierzytelniania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d613a22b-07d7-41a4-bada-1adc653b9b5d
ms.openlocfilehash: d1c0cc487d8deea7045ee9653d1eae9b73ec864f
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75938015"
---
# <a name="overriding-the-identity-of-a-service-for-authentication"></a>Przesłanianie tożsamości usługi na potrzeby uwierzytelniania
Zazwyczaj nie trzeba ustawiać tożsamości w usłudze, ponieważ wybór typu poświadczeń klienta określa typ tożsamości uwidocznionej w metadanych usługi. Na przykład poniższy kod konfiguracyjny używa elementu [\<wsHttpBinding >](../../configure-apps/file-schema/wcf/wshttpbinding.md) i ustawia atrybut `clientCredentialType` dla systemu Windows.  

 Poniższy fragment Web Services Description Language (WSDL) przedstawia tożsamość punktu końcowego zdefiniowanego wcześniej. W tym przykładzie usługa działa jako usługa samodzielna w ramach określonego konta użytkownika (username@contoso.com), w związku z czym tożsamość głównej nazwy użytkownika (UPN) zawiera nazwę konta. Nazwa UPN jest również nazywana nazwą logowania użytkownika w domenie systemu Windows.  

 Aby zapoznać się z przykładową aplikacją, która demonstruje ustawienie tożsamości, zobacz [przykład Identity Service](../samples/service-identity-sample.md). Aby uzyskać więcej informacji na temat tożsamości usługi, zobacz [tożsamość usługi i uwierzytelnianie](../feature-details/service-identity-and-authentication.md).  
  
## <a name="kerberos-authentication-and-identity"></a>Uwierzytelnianie i tożsamość Kerberos  
 Domyślnie, gdy usługa jest skonfigurowana do korzystania z poświadczeń systemu Windows, element [\<identity >](../../configure-apps/file-schema/wcf/identity.md) zawierający [\<userPrincipalName >](../../configure-apps/file-schema/wcf/userprincipalname.md) lub [\<elementu ServicePrincipalName >](../../configure-apps/file-schema/wcf/serviceprincipalname.md) jest generowany w języku WSDL. Jeśli usługa jest uruchomiona w ramach konta `LocalSystem`, `LocalService`lub `NetworkService`, nazwa główna usługi (SPN) jest generowana domyślnie w postaci `host/`\<*hostname*>, ponieważ te konta mają dostęp do danych SPN komputera. Jeśli usługa jest uruchomiona przy użyciu innego konta, Windows Communication Foundation (WCF) generuje nazwę UPN w postaci \<*username*>@<*nazwa_domeny*`>`. Dzieje się tak, ponieważ uwierzytelnianie Kerberos wymaga, aby nazwa UPN lub nazwa SPN była dostarczana do klienta w celu uwierzytelnienia usługi.  
  
 Można również użyć narzędzia Setspn. exe do zarejestrowania dodatkowej nazwy SPN z kontem usługi w domenie. Następnie można użyć nazwy SPN jako tożsamości usługi. Aby pobrać narzędzie, zobacz [Windows 2000 Resource Kit Tool: Setspn. exe](https://go.microsoft.com/fwlink/?LinkId=91752). Więcej informacji o narzędziu można znaleźć w temacie [Setspn Overview](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc773257(v=ws.10)).  
  
> [!NOTE]
> Aby użyć typu poświadczeń systemu Windows bez negocjowania, konto użytkownika usługi musi mieć dostęp do nazwy SPN, która jest zarejestrowana w domenie Active Directory. Można to zrobić w następujący sposób:  
  
- Użyj konta NetworkService lub LocalSystem do uruchomienia usługi. Ponieważ te konta mają dostęp do nazwy SPN maszyny, która została ustanowiona, gdy komputer jest przyłączony do domeny Active Directory, funkcja WCF automatycznie generuje prawidłowy element SPN w ramach punktu końcowego usługi w metadanych usługi (WSDL).  
  
- Użyj dowolnego konta domeny Active Directory, aby uruchomić usługę. W takim przypadku należy ustanowić nazwę SPN dla tego konta domeny, którą można wykonać za pomocą narzędzia narzędzia Setspn. exe. Po utworzeniu nazwy SPN dla konta usługi Skonfiguruj program WCF do publikowania tej nazwy SPN na klientach usługi za pomocą metadanych (WSDL). W tym celu należy ustawić tożsamość punktu końcowego dla uwidocznionego punktu końcowego za pomocą pliku lub kodu konfiguracji aplikacji.  
  
 Aby uzyskać więcej informacji na temat nazw SPN, protokołu Kerberos i Active Directory, zobacz [dodatek dotyczący protokołu Kerberos dla systemu Windows](https://docs.microsoft.com/previous-versions/msp-n-p/ff649429(v=pandp.10)).  
  
### <a name="when-spn-or-upn-equals-the-empty-string"></a>Gdy nazwa SPN lub nazwa UPN jest równa pustemu ciągowi  
 Jeśli ustawisz nazwę SPN lub nazwę UPN równą pustemu ciągowi, następuje wiele różnych rzeczy, w zależności od poziomu zabezpieczeń i używanego trybu uwierzytelniania:  
  
- W przypadku korzystania z zabezpieczeń na poziomie transportu jest wybierane uwierzytelnianie NT LanMan (NTLM).  
  
- W przypadku korzystania z zabezpieczeń na poziomie komunikatów uwierzytelnianie może zakończyć się niepowodzeniem, w zależności od trybu uwierzytelniania:  
  
- Jeśli używasz trybu `spnego`, a atrybut `AllowNtlm` jest ustawiony na `false`, uwierzytelnianie nie powiedzie się.  
  
- Jeśli używasz trybu `spnego`, a atrybut `AllowNtlm` jest ustawiony na `true`, uwierzytelnianie kończy się niepowodzeniem, jeśli nazwa UPN jest pusta, ale zostanie zakończona, gdy nazwa SPN jest pusta.  
  
- W przypadku korzystania z protokołu Kerberos Direct (znanego również jako "z pojedynczym zrzutem") uwierzytelnianie kończy się niepowodzeniem.  
  
### <a name="using-the-identity-element-in-configuration"></a>Używanie elementu \<Identity > w konfiguracji  
 Jeśli zmienisz typ poświadczeń klienta w powiązaniu wcześniej pokazanym na certyfikacie`,`, wygenerowany kod WSDL zawiera certyfikat X. 509 z serializowanym algorytmem Base64 dla wartości tożsamości, jak pokazano w poniższym kodzie. Jest to wartość domyślna dla wszystkich typów poświadczeń klienta innych niż Windows.  

 Można zmienić wartość domyślnej tożsamości usługi lub zmienić typ tożsamości za pomocą <`identity`> elementu w konfiguracji lub przez ustawienie tożsamości w kodzie. Poniższy kod konfiguracji ustawia tożsamość systemu nazw domen (DNS) z wartością `contoso.com`.  

### <a name="setting-identity-programmatically"></a>Programowo Ustawianie tożsamości  
 Usługa nie musi jawnie określać tożsamości, ponieważ funkcja WCF automatycznie ją określa. Jednak funkcja WCF umożliwia określenie tożsamości w punkcie końcowym, jeśli jest to wymagane. Poniższy kod dodaje nowy punkt końcowy usługi z określoną tożsamością DNS.  
  
 [!code-csharp[C_Identity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#5)]
 [!code-vb[C_Identity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#5)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: tworzenie niestandardowego weryfikatora tożsamości klienta](how-to-create-a-custom-client-identity-verifier.md)
- [Uwierzytelnianie i tożsamość usług](../feature-details/service-identity-and-authentication.md)
