---
title: Tożsamość usług — przykład
ms.date: 03/30/2017
ms.assetid: 79fa8c1c-85bb-4b67-bc67-bfaf721303f8
ms.openlocfilehash: 341e4922089634c3e46929d6cdb474b2dfbd0666
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152735"
---
# <a name="service-identity-sample"></a>Tożsamość usług — przykład
Ta tożsamość usług — przykład pokazuje, jak ustawić tożsamość usługi. W czasie projektowania klient może pobrać tożsamości przy użyciu metadanych usługi, a następnie w czasie wykonywania klienta można uwierzytelnić tożsamości usługi. Pojęcie tożsamości usługi jest umożliwienie klienta do uwierzytelniania usługi przed wywołaniem dowolnej swojego działania, w tym samym ochrony klienta przed nieuwierzytelnione wywołania. Dla bezpiecznego połączenia usługi jest również uwierzytelniany poświadczeń klienta przed zezwoleniem na jego dostęp, ale nie jest celem tego przykładu. Zobacz przykłady w [klienta](../../../../docs/framework/wcf/samples/client.md) ukazują uwierzytelniania serwera.

> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.

 Ten przykład ilustruje następujące funkcje:

-   Jak ustawić różne rodzaje tożsamości w różnych punktach końcowych usługi. Każdy typ tożsamości ma różne możliwości. Typ tożsamości do użycia zależy od typu poświadczeń zabezpieczeń używane na powiązanie punktu końcowego.

-   Tożsamość albo można ustawić deklaratywnie w konfiguracji lub obowiązkowo w kodzie. Zazwyczaj zarówno klient, jak i usługi należy użyć konfiguracji do ustawiania tożsamości.

-   Jak ustawić tożsamość niestandardowa na komputerze klienckim. Tożsamość niestandardowa jest zazwyczaj dostosowanie istniejącego typu tożsamości, która umożliwia klientowi zbadać inne oświadczenia informacjami poświadczenia do podejmowania decyzji dotyczących autoryzacji przed wywołaniem usługi.

    > [!NOTE]
    >  W tym przykładzie sprawdza, czy tożsamość określonego certyfikatu o nazwie identity.com i klucz RSA zawartych w tym certyfikacie. Korzystając z typów tożsamości certyfikatu i RSA w konfiguracji na komputerze klienckim, prosty sposób uzyskania tych wartości jest sprawdzanie WSDL usługi gdy te wartości są serializowane.

 Następujący przykładowy kod pokazuje, jak skonfigurować tożsamość punktu końcowego usługi za pomocą serwera nazw domen (DNS) przy użyciu WSHttpBinding certyfikatu.

```csharp
//Create a service endpoint and set its identity to the certificate's DNS
WSHttpBinding wsAnonbinding = new WSHttpBinding (SecurityMode.Message);
// Client are Anonymous to the service
wsAnonbinding.Security.Message.ClientCredentialType = MessageCredentialType.None;
WServiceEndpoint ep = serviceHost.AddServiceEndpoint(typeof(ICalculator),wsAnonbinding, String.Empty);
EndpointAddress epa = new EndpointAddress(dnsrelativeAddress,EndpointIdentity.CreateDnsIdentity("identity.com"));
ep.Address = epa;
```

 Tożsamość można również określić w konfiguracji w pliku App.config. Poniższy przykład pokazuje, jak ustawić tożsamością UPN (główna nazwa użytkownika) dla punktu końcowego usługi.

```xml
<endpoint address="upnidentity"
        behaviorConfiguration=""
        binding="wsHttpBinding"
        bindingConfiguration="WSHttpBinding_Windows"
        name="WSHttpBinding_ICalculator_Windows"
        contract="Microsoft.ServiceModel.Samples.ICalculator">
  <!-- Set the UPN identity for this endpoint -->
  <identity>
      <userPrincipalName value="host\myservice.com" />
  </identity >
</endpoint>
```

 Tożsamość niestandardowa można ustawić na komputerze klienckim, wynikające z <xref:System.ServiceModel.EndpointIdentity> i <xref:System.ServiceModel.Security.IdentityVerifier> klasy. Koncepcyjnie <xref:System.ServiceModel.Security.IdentityVerifier> klasy jest uznawana za klienta odpowiada usługi `AuthorizationManager` klasy. Poniższy przykład kodu przedstawia implementację `OrgEndpointIdentity`, która przechowuje nazwę organizacji, aby dopasować nazwę podmiotu certyfikatu serwera. Sprawdzanie autoryzacji, nazwę organizacji jest wykonywane w `CheckAccess` metody `CustomIdentityVerifier` klasy.

```csharp
// This custom EndpointIdentity stores an organization name
public class OrgEndpointIdentity : EndpointIdentity
{
    private string orgClaim;
    public OrgEndpointIdentity(string orgName)
    {
        orgClaim = orgName;
    }
    public string OrganizationClaim
    {
        get { return orgClaim; }
        set { orgClaim = value; }
    }
}

//This custom IdentityVerifier uses the supplied OrgEndpointIdentity to
//check that X.509 certificate's distinguished name claim contains
//the organization name e.g. the string value "O=Contoso"
class CustomIdentityVerifier : IdentityVerifier
{
    public override bool CheckAccess(EndpointIdentity identity, AuthorizationContext authContext)
    {
        bool returnvalue = false;
        foreach (ClaimSet claimset in authContext.ClaimSets)
        {
            foreach (Claim claim in claimset)
            {
                if (claim.ClaimType == "http://schemas.microsoft.com/ws/2005/05/identity/claims/x500distinguishedname")
                {
                    X500DistinguishedName name = (X500DistinguishedName)claim.Resource;
                    if (name.Name.Contains(((OrgEndpointIdentity)identity).OrganizationClaim))
                    {
                        Console.WriteLine("Claim Type: {0}",claim.ClaimType);
                        Console.WriteLine("Right: {0}", claim.Right);
                        Console.WriteLine("Resource: {0}",claim.Resource);
                        Console.WriteLine();
                        returnvalue = true;
                    }
                }
            }
        }
        return returnvalue;
    }
}
```

 W tym przykładzie używa certyfikatu o nazwie identity.com, który znajduje się w folderze rozwiązania tożsamości specyficzny dla języka.

### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej

1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

3.  Do uruchomienia przykładu w konfiguracji o jednym lub między komputerami, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić przykład na tym samym komputerze

1.  Na [!INCLUDE[wxp](../../../../includes/wxp-md.md)] lub [!INCLUDE[wv](../../../../includes/wv-md.md)], zaimportuj plik certyfikatu Identity.pfx w folderze rozwiązania tożsamości do magazynu LocalMachine/My certyfikatów (osobistych), za pomocą narzędzia przystawki programu MMC. Ten plik jest chroniony hasłem. Podczas importowania zostanie wyświetlona prośba o podanie hasła. Typ `xyz` w polu hasła. Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie certyfikatów za pomocą przystawki programu MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md) tematu. Po zakończeniu tej operacji Uruchom Setup.bat w programie Visual Studio wiersz polecenia z uprawnieniami administratora, który kopiuje ten certyfikat do magazynu osób zaufanych/CurrentUser do użytku na komputerze klienckim.

2.  Na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], uruchom Setup.bat jest z poziomu folderu instalacji przykładowej wewnątrz programu Visual Studio 2012 wiersz polecenia z uprawnieniami administratora. Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.

    > [!NOTE]
    >  Plik wsadowy Setup.bat jest przeznaczony do uruchamiania z programu Visual Studio 2012 wiersz polecenia. Ustaw w Visual Studio 2012 Command Prompt punkty do katalogu, który zawiera pliki wykonywalne wymagane przez skrypt Setup.bat jest zmiennej środowiskowej PATH. Upewnij się, usunąć certyfikaty, uruchamiając Cleanup.bat po zakończeniu dla próbki. Inne przykłady zabezpieczeń za pomocą tych samych certyfikatów.  
  
3.  Uruchom Service.exe z katalogu \service\bin. Upewnij się, że usługa wskazuje, że jest gotowy i wyświetla monit o naciśnięcie klawisza \<Enter > do zakończenia usługi.  
  
4.  Uruchom Client.exe z katalogu \client\bin lub naciskając klawisz F5 w programie Visual Studio, aby skompilować i uruchomić. Aktywność klienta jest wyświetlany w aplikacji konsolowej klienta.  
  
5.  Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-run-the-sample-across-computers"></a>Do uruchomienia przykładu na komputerach  
  
1.  Przed zbudowaniem klienta części przykładu, należy zmienić wartość adresu punktu końcowego usługi w pliku Client.cs w `CallServiceCustomClientIdentity` metody. Następnie skompiluj przykład.  
  
2.  Utwórz katalog na komputerze usługi.  
  
3.  Skopiuj pliki programu usługi z service\bin do katalogu na komputerze usługi. Także skopiować pliki Setup.bat i Cleanup.bat na komputerze usługi.  
  
4.  Utwórz katalog na komputerze klienckim, aby pliki binarne klienta.  
  
5.  Skopiuj pliki programu klienta do katalogu klienta na komputerze klienckim. Także skopiować pliki Setup.bat, Cleanup.bat i ImportServiceCert.bat do klienta.  
  
6.  W usłudze Uruchom `setup.bat service` w wierszu polecenia programu Visual Studio otwartych z uprawnieniami administratora. Uruchamianie `setup.bat` z `service` argument tworzy certyfikat usługi z w pełni kwalifikowana nazwa domeny komputera i eksportuje certyfikat usługi do pliku o nazwie Service.cer.  
  
7.  Skopiuj plik Service.cer z katalogu usług w katalogu klienta na komputerze klienckim.  
  
8.  W pliku Client.exe.config na komputerze klienckim należy zmienić wartość adresu punktu końcowego, aby dopasować nowy adres usługi. Istnieje wiele wystąpień, które musi zostać zmienione.  
  
9. Na komputerze klienckim należy uruchomić ImportServiceCert.bat w wierszu polecenia programu Visual Studio otwartych z uprawnieniami administratora. To importuje certyfikatu usługi z pliku Service.cer, do CurrentUser - TrustedPeople magazynu.  
  
10. Na komputerze, usługi uruchom Service.exe w wierszu polecenia.  
  
11. Na komputerze klienckim należy uruchomić Client.exe z poziomu wiersza polecenia. Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić zasoby po próbki  
  
-   Uruchom Cleanup.bat w folderze samples, po zakończeniu działa aplikacja przykładowa.  
  
    > [!NOTE]
    >  Ten skrypt nie powoduje usunięcia usług certyfikatów na komputerze klienckim, podczas uruchamiania tego przykładu na komputerach. Po uruchomieniu przykładów Windows Communication Foundation (WCF), które używają certyfikatów na komputerach, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w CurrentUser - TrustedPeople magazynu. Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.

## <a name="see-also"></a>Zobacz też
