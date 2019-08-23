---
title: Uwierzytelnianie i tożsamość usług
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- authentication [WCF], specifying the identity of a service
ms.assetid: a4c8f52c-5b30-45c4-a545-63244aba82be
ms.openlocfilehash: f9ed2a7c284588a0fb481d41dca61e663fd090b1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969232"
---
# <a name="service-identity-and-authentication"></a>Uwierzytelnianie i tożsamość usług
*Tożsamość punktu końcowego* usługi jest wartością wygenerowaną na podstawie Web Services Description Language usługi (WSDL). Ta wartość propagowana do dowolnego klienta jest używana do uwierzytelniania usługi. Po zainicjowaniu przez klienta komunikacji z punktem końcowym, gdy usługa uwierzytelnia się na kliencie, klient porównuje wartość tożsamości punktu końcowego z rzeczywistą wartością zwróconą przez proces uwierzytelniania punktu końcowego. Jeśli są one zgodne, klient ma pewność, że skontaktował się z oczekiwanym punktem końcowym usługi. Ta funkcja działa jako ochrona przed *phishingiem* , uniemożliwiając przekierowywanie klienta do punktu końcowego hostowanego przez złośliwą usługę.  
  
 Aby zapoznać się z przykładową aplikacją, która demonstruje ustawienie tożsamości, zobacz [przykład Identity Service](../../../../docs/framework/wcf/samples/service-identity-sample.md). Aby uzyskać więcej informacji o punktach końcowych i [](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)adresach punktów końcowych, zobacz temat addresss.  
  
> [!NOTE]
> Podczas uwierzytelniania przy użyciu programu NT LanMan (NTLM) tożsamość usługi nie jest sprawdzana, ponieważ w obszarze NTLM klient nie może uwierzytelnić serwera. Protokół NTLM jest używany, gdy komputery są częścią grupy roboczej systemu Windows lub w przypadku korzystania ze starszej wersji systemu Windows, która nie obsługuje uwierzytelniania Kerberos.  
  
 Gdy klient inicjuje bezpieczny kanał w celu wysłania wiadomości do usługi za pośrednictwem niej, infrastruktura Windows Communication Foundation (WCF) uwierzytelnia usługę i wysyła komunikat tylko wtedy, gdy tożsamość usługi jest zgodna z tożsamością określoną w punkcie końcowym. adres jest wykorzystywany przez klienta.  
  
 Przetwarzanie tożsamości składa się z następujących etapów:  
  
- W czasie projektowania deweloper klienta Określa tożsamość usługi z metadanych punktu końcowego (uwidacznianych za pośrednictwem WSDL).  
  
- W czasie wykonywania aplikacja kliencka sprawdza oświadczenia dotyczące poświadczeń zabezpieczeń usługi przed wysłaniem jakichkolwiek komunikatów do usługi.  
  
 Przetwarzanie tożsamości na kliencie jest analogiczne do uwierzytelniania klienta w usłudze. Usługa zabezpieczona nie wykonuje kodu do momentu uwierzytelnienia poświadczeń klienta. Podobnie klient nie wysyła komunikatów do usługi, dopóki poświadczenia usługi nie zostały uwierzytelnione na podstawie tego, co jest znane z góry metadanych usługi.  
  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A> Właściwość<xref:System.ServiceModel.EndpointAddress> klasy reprezentuje tożsamość usługi wywołana przez klienta. Usługa publikuje <xref:System.ServiceModel.EndpointAddress.Identity%2A> w metadanych. Gdy deweloper klienta uruchamia [Narzędzie metadanych ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) względem punktu końcowego usługi, wygenerowana konfiguracja zawiera wartość <xref:System.ServiceModel.EndpointAddress.Identity%2A> właściwości usługi. Infrastruktura WCF (jeśli została skonfigurowana z zabezpieczeniami) sprawdza, czy usługa posiada określoną tożsamość.  
  
> [!IMPORTANT]
> Metadane zawierają oczekiwaną tożsamość usługi, dlatego zaleca się uwidocznienie metadanych usługi za pośrednictwem bezpiecznych metod, na przykład przez utworzenie punktu końcowego HTTPS dla usługi. Aby uzyskać więcej informacji, zobacz [jak: Bezpieczne punkty końcowe](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md)metadanych.  
  
## <a name="identity-types"></a>Typy tożsamości  
 Usługa może udostępnić sześć typów tożsamości. Każdy typ tożsamości odpowiada elementowi, który może znajdować się wewnątrz `<identity>` elementu w konfiguracji. Używany typ zależy od scenariusza i wymagań dotyczących zabezpieczeń usługi. W poniższej tabeli opisano każdy typ tożsamości.  
  
|Typ tożsamości|Opis|Typowy scenariusz|  
|-------------------|-----------------|----------------------|  
|System nazw domen (DNS)|Tego elementu należy używać z certyfikatami X. 509 lub kontami systemu Windows. Porównuje nazwę DNS określoną w poświadczeniu z wartością określoną w tym elemencie.|Sprawdzanie DNS umożliwia korzystanie z certyfikatów z nazwami DNS lub podmiotami. Jeśli certyfikat zostanie ponownie wystawiony z tą samą nazwą DNS lub podmiotem, sprawdzanie tożsamości jest nadal ważne. Gdy certyfikat zostanie ponownie wystawiony, pobiera nowy klucz RSA, ale zachowuje tę samą nazwę DNS lub podmiotu. Oznacza to, że klienci nie muszą aktualizować informacji o tożsamości dotyczącej usługi.|  
|Certyfikatu. Wartość domyślna, `ClientCredentialType` gdy jest ustawiona na wartość Certificate.|Ten element określa zakodowaną w formacie base64 wartość certyfikatu X. 509 do porównania z klientem.<br /><br /> Użyj tego elementu również w przypadku korzystania z programu CardSpace jako poświadczenia do uwierzytelniania usługi.|Ten element ogranicza uwierzytelnianie do pojedynczego certyfikatu na podstawie jego wartości odcisku palca. Umożliwia to bardziej rygorystyczne uwierzytelnianie, ponieważ wartości odcisków palca są unikatowe. Jest to jedno z Zastrzeżenie: Jeśli certyfikat zostanie ponownie wystawiony z tą samą nazwą podmiotu, ma również nowy odcisk palca. W związku z tym klienci nie mogą sprawdzić poprawności usługi, chyba że jest znany nowy odcisk palca. Aby uzyskać więcej informacji na temat znajdowania odcisku palca certyfikatu, zobacz [How to: Pobieranie odcisku palca certyfikatu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).|  
|Odwołanie do certyfikatu|Taka sama jak w przypadku opcji certyfikatu opisanej wcześniej. Jednak ten element pozwala określić nazwę certyfikatu i lokalizację magazynu, z którego ma zostać pobrany certyfikat.|Analogicznie jak scenariusz certyfikatu opisany wcześniej.<br /><br /> Korzyścią jest możliwość zmiany lokalizacji magazynu certyfikatów.|  
|RSA|Ten element określa wartość klucza RSA do porównania z klientem. Jest to podobne do opcji certyfikatu, ale nie przy użyciu odcisku palca certyfikatu, zamiast tego jest używany klucz RSA certyfikatu.|Sprawdzanie RSA umożliwia ograniczenie uwierzytelniania do pojedynczego certyfikatu na podstawie jego klucza RSA. Umożliwia to bardziej rygorystyczne uwierzytelnianie określonego klucza RSA kosztem usługi, która nie działa już z istniejącymi klientami, jeśli wartość klucza RSA ulegnie zmianie.|  
|Główna nazwa użytkownika (UPN). Wartość domyślna, gdy `ClientCredentialType` jest ustawiona na system Windows, a proces usługi nie jest uruchomiony na jednym z kont systemu.|Ten element określa nazwę UPN, w ramach której działa usługa. Zapoznaj się z sekcją protokołu i tożsamości protokołu Kerberos w celu [przesłaniania tożsamości usługi na potrzeby uwierzytelniania](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md).|Dzięki temu usługa jest uruchomiona w ramach określonego konta użytkownika systemu Windows. Konto użytkownika może być kontem bieżącego zalogowanego użytkownika lub usługi działającej w ramach określonego konta użytkownika.<br /><br /> To ustawienie wykorzystuje zabezpieczenia protokołu Kerberos systemu Windows, jeśli usługa jest uruchomiona w ramach konta domeny w środowisku Active Directoryu.|  
|Główna nazwa usługi (SPN). Wartość domyślna, gdy `ClientCredentialType` jest ustawiona na system Windows, a proces usługi jest uruchomiony w ramach jednego z kont systemu — LocalService, LocalSystem lub NetworkService.|Ten element określa nazwę SPN skojarzoną z kontem usługi. Zapoznaj się z sekcją protokołu i tożsamości protokołu Kerberos w celu [przesłaniania tożsamości usługi na potrzeby uwierzytelniania](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md).|Gwarantuje to, że nazwa SPN i określone konto systemu Windows skojarzone z nazwą SPN zidentyfikuje usługę.<br /><br /> Za pomocą narzędzia Setspn. exe można skojarzyć konto komputera z kontem użytkownika usługi.<br /><br /> To ustawienie wykorzystuje zabezpieczenia protokołu Kerberos systemu Windows, jeśli usługa jest uruchomiona w ramach jednego z kont systemu lub konta domeny, które ma skojarzoną z nim nazwę SPN, a komputer jest członkiem domeny w środowisku Active Directoryowym.|  
  
## <a name="specifying-identity-at-the-service"></a>Określanie tożsamości w usłudze  
 Zazwyczaj nie trzeba ustawiać tożsamości w usłudze, ponieważ wybór typu poświadczeń klienta określa typ tożsamości uwidocznionej w metadanych usługi. Aby uzyskać więcej informacji na temat przesłonięcia lub określenia tożsamości usługi, zobacz [Przesłanianie tożsamości usługi na potrzeby uwierzytelniania](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md).  
  
## <a name="using-the-identity-element-in-configuration"></a>Używanie elementu \<Identity > w konfiguracji  
 Jeśli zmienisz typ poświadczeń klienta w powiązaniu poprzednio pokazanym `Certificate,` do, wygenerowany kod WSDL zawiera certyfikat X. 509 z serializowanym algorytmem Base64 dla wartości tożsamości, jak pokazano w poniższym kodzie. Jest to wartość domyślna dla wszystkich typów poświadczeń klienta innych niż Windows.  

 Można zmienić wartość domyślnej tożsamości usługi lub zmienić typ tożsamości za pomocą `<identity>` elementu w konfiguracji lub przez ustawienie tożsamości w kodzie. Poniższy kod konfiguracji ustawia tożsamość systemu nazw domen (DNS) z wartością `contoso.com`.  

## <a name="setting-identity-programmatically"></a>Programowo Ustawianie tożsamości  
 Usługa nie musi jawnie określać tożsamości, ponieważ funkcja WCF automatycznie ją określa. Jednak funkcja WCF umożliwia określenie tożsamości w punkcie końcowym, jeśli jest to wymagane. Poniższy kod dodaje nowy punkt końcowy usługi z określoną tożsamością DNS.  
  
 [!code-csharp[C_Identity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#5)]
 [!code-vb[C_Identity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#5)]  
  
## <a name="specifying-identity-at-the-client"></a>Określanie tożsamości na kliencie  
 W czasie projektowania deweloper klienta zwykle używa [Narzędzia do przesyłania metadanych programu ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) w celu wygenerowania konfiguracji klienta. Wygenerowany plik konfiguracji (przeznaczony do użycia przez klienta) zawiera tożsamość serwera. Na przykład poniższy kod jest generowany na podstawie usługi, która określa tożsamość DNS, jak pokazano w powyższym przykładzie. Zwróć uwagę, że wartość tożsamości punktu końcowego klienta jest zgodna z wartością usługi. W takim przypadku, gdy klient otrzymuje poświadczenia systemu Windows (Kerberos) dla usługi, oczekuje wartości `contoso.com`.  

 Jeśli zamiast systemu Windows, usługa określa certyfikat jako typ poświadczeń klienta, oczekiwana jest wartość `contoso.com`właściwości DNS certyfikatu. (Lub jeśli właściwość DNS ma `null`wartość, nazwa podmiotu certyfikatu musi być `contoso.com`.)  
  
#### <a name="using-a-specific-value-for-identity"></a>Używanie określonej wartości tożsamości  
 Następujący plik konfiguracji klienta pokazuje, w jaki sposób tożsamość usługi powinna być określoną wartością. W poniższym przykładzie klient może komunikować się z dwoma punktami końcowymi. Pierwszy jest identyfikowany za pomocą odcisku palca certyfikatu, a drugi z kluczem RSA certyfikatu. Oznacza to, że certyfikat zawierający tylko parę klucz publiczny/prywatny, ale nie został wystawiony przez zaufany urząd.  

## <a name="identity-checking-at-run-time"></a>Sprawdzanie tożsamości w czasie wykonywania  
 W czasie projektowania deweloper klienta Określa tożsamość serwera za pomocą metadanych. W czasie wykonywania Sprawdzanie tożsamości jest przeprowadzane przed wywołaniem punktów końcowych w usłudze.  
  
 Wartość tożsamości jest powiązana z typem uwierzytelniania określonym przez metadane; Innymi słowy, typ poświadczeń używanych przez usługę.  
  
 Jeśli kanał jest skonfigurowany do uwierzytelniania przy użyciu protokołu SSL (Message-lub Transport Level SSL) z certyfikatami X. 509 w celu uwierzytelnienia, następujące wartości tożsamości są prawidłowe:  
  
- DNS. Funkcja WCF gwarantuje, że certyfikat podany podczas uzgadniania SSL zawiera atrybut DNS lub `CommonName` (CN) równy wartości określonej w tożsamości DNS na kliencie. Należy zauważyć, że te testy są wykonywane Oprócz określenia okresu ważności certyfikatu serwera. Domyślnie WCF sprawdza, czy certyfikat serwera jest wystawiony przez zaufany główny urząd certyfikacji.  
  
- Certyfikatu. Podczas uzgadniania protokołu SSL usługa WCF zapewnia, że zdalny punkt końcowy zapewnia dokładną wartość certyfikatu określoną w tożsamości.  
  
- Odwołanie do certyfikatu. Analogicznie jak certyfikat.  
  
- RSA. Podczas uzgadniania protokołu SSL usługa WCF zapewnia, że zdalny punkt końcowy zapewnia dokładny klucz RSA określony w tożsamości.  
  
 Jeśli usługa uwierzytelnia przy użyciu protokołu SSL lub certyfikatu na poziomie transportu z poświadczenia systemu Windows na potrzeby uwierzytelniania, a następnie negocjuje poświadczenie, następujące wartości tożsamości są prawidłowe:  
  
- DNS. Negocjowanie przekazuje nazwę SPN usługi, aby można było sprawdzić, czy nazwa DNS. Nazwa SPN ma postać `host/<dns name>`.  
  
- SPN. Zwracana jest jawna Nazwa SPN usługi, na przykład `host/myservice`.  
  
- UPN. Nazwa UPN konta usługi. Nazwa UPN ma postać `username`. @ `domain` Na przykład, gdy usługa jest uruchomiona w ramach konta użytkownika, może to być `username@contoso.com`.  
  
 Określanie tożsamości programowo (przy użyciu <xref:System.ServiceModel.EndpointAddress.Identity%2A> właściwości) jest opcjonalne. Jeśli tożsamość nie zostanie określona, a typ poświadczeń klienta to Windows, wartość domyślna to SPN z wartością ustawioną na część nazwy hosta adresu punktu końcowego usługi poprzedzoną prefiksem "host/". Jeśli tożsamość nie zostanie określona, a typ poświadczeń klienta to certyfikat, wartość domyślna to `Certificate`. Dotyczy to zarówno zabezpieczeń komunikatów, jak i na poziomie transportu.  
  
## <a name="identity-and-custom-bindings"></a>Tożsamość i powiązania niestandardowe  
 Ponieważ tożsamość usługi zależy od używanego typu powiązania, upewnij się, że podczas tworzenia niestandardowego powiązania jest dostępna odpowiednia tożsamość. Na przykład, w poniższym przykładzie kodu, uwidoczniona tożsamość nie jest zgodna z typem zabezpieczeń, ponieważ tożsamość powiązania Bootstrap bezpiecznego konwersacji nie jest zgodna z tożsamością dla powiązania w punkcie końcowym. Powiązanie bezpiecznej konwersacji ustawia tożsamość DNS, podczas gdy <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement> ustawia tożsamość UPN lub SPN.  
  
 [!code-csharp[C_Identity#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#8)]
 [!code-vb[C_Identity#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#8)]  
  
 Aby uzyskać więcej informacji o tym, jak prawidłowo układać elementy powiązań dla niestandardowego powiązania, zobacz [Tworzenie powiązań zdefiniowanych przez użytkownika](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md). Aby uzyskać więcej informacji o tworzeniu niestandardowego powiązania z <xref:System.ServiceModel.Channels.SecurityBindingElement>, zobacz [How to: Utwórz elementu SecurityBindingElement dla określonego trybu](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)uwierzytelniania.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Tworzenie niestandardowego powiązania przy użyciu elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Instrukcje: Utwórz elementu SecurityBindingElement dla określonego trybu uwierzytelniania](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
- [Instrukcje: Tworzenie niestandardowego weryfikatora tożsamości klienta](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)
- [Wybieranie typu poświadczeń](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Tworzenie powiązań zdefiniowanych przez użytkownika](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)
- [Instrukcje: Pobieranie odcisku palca certyfikatu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
