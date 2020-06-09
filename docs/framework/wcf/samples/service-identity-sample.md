---
title: Tożsamość usług — przykład
ms.date: 03/30/2017
ms.assetid: 79fa8c1c-85bb-4b67-bc67-bfaf721303f8
ms.openlocfilehash: e4b5e739db04fbb3270c9870468433aec7787061
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599909"
---
# <a name="service-identity-sample"></a>Tożsamość usług — przykład
Ta przykładowa tożsamość usługi pokazuje, jak ustawić tożsamość dla usługi. W czasie projektowania klient może pobrać tożsamość przy użyciu metadanych usługi, a następnie w czasie wykonywania klient może uwierzytelnić tożsamość usługi. Pojęcie tożsamości usługi polega na umożliwieniu klientowi uwierzytelnienia usługi przed wywołaniem jakiejkolwiek z jej operacji, co chroni klienta przed nieuwierzytelnionymi wywołaniami. W przypadku bezpiecznego połączenia usługa uwierzytelnia także poświadczenia klienta przed zezwoleniem na dostęp do niego, ale nie jest to fokus tego przykładu. Zapoznaj się z przykładami w [kliencie](client.md) , który pokazuje uwierzytelnianie serwera.

> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.

 Ten przykład ilustruje następujące funkcje:

- Jak ustawić różne typy tożsamości w różnych punktach końcowych dla usługi. Każdy typ tożsamości ma różne możliwości. Typ tożsamości do użycia zależy od typu poświadczeń zabezpieczeń używanych w powiązaniu punktu końcowego.

- Tożsamość można skonfigurować w sposób deklaratywny w konfiguracji lub za pomocą kodu. Zwykle dla klienta i usługi należy użyć konfiguracji, aby ustawić tożsamość.

- Jak ustawić niestandardową tożsamość na kliencie. Niestandardowa tożsamość jest zwykle dostosowywana do istniejącego typu tożsamości, która umożliwia klientowi badanie innych informacji o zadaniu w poświadczeniach usługi w celu podejmowania decyzji dotyczących autoryzacji przed wywołaniem usługi.

    > [!NOTE]
    > Ten przykład umożliwia sprawdzenie tożsamości określonego certyfikatu o nazwie identity.com i klucza RSA zawartego w tym certyfikacie. W przypadku korzystania z certyfikatów i typów tożsamości RSA w konfiguracji na kliencie, prostym sposobem na uzyskanie tych wartości jest sprawdzenie WSDL dla usługi, w której te wartości są serializowane.

 Poniższy przykładowy kod pokazuje, jak skonfigurować tożsamość punktu końcowego usługi za pomocą serwera nazw domen (DNS) certyfikatu przy użyciu WSHttpBinding.

```csharp
//Create a service endpoint and set its identity to the certificate's DNS
WSHttpBinding wsAnonbinding = new WSHttpBinding (SecurityMode.Message);
// Client are Anonymous to the service
wsAnonbinding.Security.Message.ClientCredentialType = MessageCredentialType.None;
WServiceEndpoint ep = serviceHost.AddServiceEndpoint(typeof(ICalculator),wsAnonbinding, String.Empty);
EndpointAddress epa = new EndpointAddress(dnsrelativeAddress,EndpointIdentity.CreateDnsIdentity("identity.com"));
ep.Address = epa;
```

 Tożsamość można także określić w konfiguracji w pliku App. config. Poniższy przykład pokazuje, jak ustawić tożsamość UPN (główna nazwa użytkownika) dla punktu końcowego usługi.

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

 Tożsamość niestandardową można ustawić na kliencie, pobierając ją z <xref:System.ServiceModel.EndpointIdentity> <xref:System.ServiceModel.Security.IdentityVerifier> klas i. Koncepcyjnie <xref:System.ServiceModel.Security.IdentityVerifier> Klasa może być traktowana jako odpowiednik klienta `AuthorizationManager` klasy usługi. Poniższy przykład kodu pokazuje implementację `OrgEndpointIdentity` , która przechowuje nazwę organizacji do dopasowania w nazwie podmiotu certyfikatu serwera. Sprawdzanie autoryzacji nazwy organizacji występuje w `CheckAccess` metodzie `CustomIdentityVerifier` klasy.

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

 Ten przykład używa certyfikatu o nazwie identity.com, który znajduje się w folderze rozwiązania tożsamości specyficznej dla języka.

### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład

1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).

3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).

### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić przykład na tym samym komputerze

1. W systemie Windows XP lub Windows Vista Zaimportuj plik certyfikatu Identity. pfx w folderze rozwiązania tożsamości do magazynu certyfikatów LocalMachine/my (Personal) za pomocą narzędzia przystawek programu MMC. Ten plik jest chroniony hasłem. Podczas importowania zostanie wyświetlony monit o podanie hasła. Wpisz `xyz` w polu hasło. Aby uzyskać więcej informacji, zobacz temat [How to: View Certificates with MMC przystawka](../feature-details/how-to-view-certificates-with-the-mmc-snap-in.md) . Po wykonaniu tej czynności uruchom setup. bat w wiersz polecenia dla deweloperów dla programu Visual Studio z uprawnieniami administratora, które kopiuje ten certyfikat do magazynu CurrentUser/zaufane osoby do użytku na kliencie.

2. W systemie Windows Server 2003 uruchom setup. bat z przykładowego folderu instalacyjnego w wierszu polecenia programu Visual Studio 2012 z uprawnieniami administratora. Spowoduje to zainstalowanie wszystkich certyfikatów wymaganych do uruchomienia przykładu.

    > [!NOTE]
    > Plik wsadowy Setup. bat został zaprojektowany do uruchamiania z wiersza polecenia programu Visual Studio 2012. Zmienna środowiskowa PATH ustawiona w wierszu polecenia programu Visual Studio 2012 wskazuje katalog zawierający pliki wykonywalne wymagane przez skrypt Setup. bat. Upewnij się, że certyfikaty są usuwane przez uruchomienie Oczyść. bat po zakończeniu z przykładem. Inne przykłady zabezpieczeń używają tych samych certyfikatów.  
  
3. Uruchom plik Service. exe z katalogu \service\bin. Upewnij się, że usługa wskazuje, że jest gotowa i wyświetla monit, aby \<Enter> zakończyć działanie usługi.  
  
4. Uruchom program Client. exe z katalogu \client\bin lub naciskając klawisz F5 w programie Visual Studio, aby skompilować i uruchomić. Aktywność klienta jest wyświetlana w aplikacji konsoli klienta.  
  
5. Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Aby uruchomić przykład na wielu komputerach  
  
1. Przed utworzeniem części klienta przykładu należy zmienić wartość adresu punktu końcowego usługi w pliku Client.cs w `CallServiceCustomClientIdentity` metodzie. Następnie Skompiluj przykład.  
  
2. Utwórz katalog na komputerze usługi.  
  
3. Skopiuj pliki programu Service z usługi service\bin do katalogu na komputerze usługi. Skopiuj także pliki Setup. bat i Oczyść. bat do komputera usługi.  
  
4. Utwórz katalog na komputerze klienckim dla plików binarnych klienta.  
  
5. Skopiuj pliki programu klienckiego do katalogu klienta na komputerze klienckim. Skopiuj również do klienta pliki Setup. bat, Oczyść. bat i ImportServiceCert. bat.  
  
6. W usłudze Uruchom polecenie `setup.bat service` w wiersz polecenia dla deweloperów dla programu Visual Studio otwartego z uprawnieniami administratora. Uruchomienie `setup.bat` z `service` argumentem tworzy certyfikat usługi z w pełni kwalifikowaną nazwą domeny komputera i eksportuje certyfikat usługi do pliku o nazwie Service. cer.  
  
7. Skopiuj plik. cer usługi z katalogu usługi do katalogu klienta na komputerze klienckim.  
  
8. W pliku Client. exe. config na komputerze klienckim Zmień wartość adresu punktu końcowego, aby odpowiadała nowemu adresowi usługi. Istnieje wiele wystąpień, które należy zmienić.  
  
9. Na kliencie Uruchom program ImportServiceCert. bat w wiersz polecenia dla deweloperów dla programu Visual Studio otwartego z uprawnieniami administratora. Spowoduje to zaimportowanie certyfikatu usługi z pliku CER usługi do magazynu CurrentUser-TrustedPeople.  
  
10. Na komputerze usługi Uruchom program Service. exe z wiersza polecenia.  
  
11. Na komputerze klienckim uruchom program Client. exe z wiersza polecenia. Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić po przykładzie  
  
- Uruchom Oczyść. bat w folderze Samples po zakończeniu uruchamiania przykładu.  
  
    > [!NOTE]
    > Ten skrypt nie powoduje usunięcia certyfikatów usługi na kliencie podczas uruchamiania tego przykładu między komputerami. W przypadku uruchamiania przykładów programu Windows Communication Foundation (WCF), które używają certyfikatów między komputerami, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w magazynie CurrentUser-TrustedPeople. Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com` .
