---
title: "Tożsamość usług — przykład"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 79fa8c1c-85bb-4b67-bc67-bfaf721303f8
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5a89839294f74d733ec7f607a0afda53148fbd57
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="service-identity-sample"></a>Tożsamość usług — przykład
Usługi tożsamości przykładzie pokazano, jak ustawić tożsamości usługi. W czasie projektowania klient może pobrać tożsamość przy użyciu metadanych usługi, a następnie w czasie wykonywania klienta można uwierzytelnić tożsamości usługi. Pojęcie tożsamości usługi jest umożliwienie klientowi uwierzytelniania usługi przed wywołaniem dowolnej jego operacje, co chroni klienta z nieuwierzytelnione wywołania. Za pomocą bezpiecznego połączenia usługi również służy do uwierzytelniania poświadczeń klienta wcześniej, ale nie jest to fokus w tym przykładzie. Zobacz przykłady w [klienta](../../../../docs/framework/wcf/samples/client.md) który Pokaż uwierzytelniania serwera.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 W tym przykładzie przedstawiono następujące funkcje:  
  
-   Jak ustawić różne typy tożsamości dla różnych punktów końcowych dla usługi. Każdy typ tożsamości ma innej możliwości. Typ tożsamości do użycia zależy od typu poświadczeń zabezpieczeń używane w powiązaniu punktu końcowego.  
  
-   Tożsamość albo można ustawić deklaratywnie w konfiguracji lub imperatively w kodzie. Zazwyczaj zarówno klient, jak i usługi należy użyć konfiguracji, aby ustawić tożsamości.  
  
-   Jak ustawić tożsamość niestandardowa na kliencie. Tożsamość niestandardowa jest zwykle dostosowanie istniejącego typu tożsamości, która umożliwia klientowi Sprawdź inne informacje oświadczeń w poświadczenia do podejmowania decyzji dotyczących autoryzacji przed wywołaniem usługi.  
  
    > [!NOTE]
    >  W tym przykładzie sprawdza tożsamość identity.com i kluczy RSA zawartych w tym certyfikatu określonego certyfikatu. Podczas używania typów tożsamości certyfikatu i RSA w konfiguracji na kliencie, najłatwiejszym sposobem uzyskania tych wartości jest do zbadania WSDL usługi gdzie te wartości są serializowane.  
  
 Następujący przykładowy kod przedstawia sposób konfigurowania tożsamości punktu końcowego usługi z serwera nazw domen (DNS) przy użyciu WSHttpBinding certyfikatu.  
  
```  
//Create a service endpoint and set its identity to the certificate's DNS                 
WSHttpBinding wsAnonbinding = new WSHttpBinding (SecurityMode.Message);  
// Client are Anonymous to the service  
wsAnonbinding.Security.Message.ClientCredentialType = MessageCredentialType.None;  
WServiceEndpoint ep = serviceHost.AddServiceEndpoint(typeof(ICalculator),wsAnonbinding, String.Empty);  
EndpointAddress epa = new EndpointAddress(dnsrelativeAddress,EndpointIdentity.CreateDnsIdentity("identity.com"));  
ep.Address = epa;  
```  
  
 Można również określić tożsamość w konfiguracji w pliku App.config. Poniższy przykład przedstawia sposób ustawiania tożsamością UPN (główna nazwa użytkownika) dla punktu końcowego usługi.  
  
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
  
 Tożsamość niestandardowa można ustawić na kliencie przez pochodny <xref:System.ServiceModel.EndpointIdentity> i <xref:System.ServiceModel.Security.IdentityVerifier> klasy. Koncepcyjnie <xref:System.ServiceModel.Security.IdentityVerifier> klasy mogą być uważane klienta odpowiednik usługi `AuthorizationManager` klasy. Poniższy przykładowy kod przedstawia implementację `OrgEndpointIdentity`, która przechowuje nazwę organizacji w celu dopasowania do nazwy podmiotu certyfikatu serwera. Sprawdzanie autoryzacji, nazwę organizacji jest wykonywane w `CheckAccess` metoda `CustomIdentityVerifier` klasy.  
  
```  
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
  
 W przykładzie użyto certyfikatu o nazwie identity.com, który znajduje się w folderze rozwiązania tożsamości specyficzny dla języka.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić przykład na tym samym komputerze  
  
1.  Na [!INCLUDE[wxp](../../../../includes/wxp-md.md)] lub [!INCLUDE[wv](../../../../includes/wv-md.md)], zaimportuj plik certyfikatu Identity.pfx w folderze rozwiązania tożsamości w magazynie LocalMachine/My (osobistych) certyfikatu przy użyciu narzędzia przystawki programu MMC. Ten plik jest chroniony hasłem. Podczas importowania użytkownik zostanie poproszony o podanie hasła. Typ `xyz` w polu hasła. Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie certyfikatów w przystawce MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md) tematu. Po zakończeniu uruchom pliku Setup.bat w Visual Studio wiersz polecenia z uprawnieniami administratora, które kopiuje ten certyfikat w magazynie CurrentUser/zaufanych osób do użycia na kliencie.  
  
2.  Na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], uruchom z folderu instalacyjnego próbki wewnątrz pliku Setup.bat [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wiersz polecenia z uprawnieniami administratora. Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.  
  
    > [!NOTE]
    >  Plik wsadowy pliku Setup.bat jest przeznaczony do uruchamiania z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wiersza polecenia. Wartość zmiennej środowiskowej PATH w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wskazuje katalog zawierający pliki wykonywalne wymagane przez pliku Setup.bat skryptu wiersza polecenia. Upewnij się, Usuń certyfikaty, uruchamiając Cleanup.bat, po zakończeniu z próbką. Inne przykłady zabezpieczeń za pomocą tego samego certyfikatów.  
  
3.  Uruchom Service.exe z katalogu \service\bin. Upewnij się, że usługa wskazuje, że jest gotowy i wyświetla monit o naciśnięcie klawisza \<Enter > zakończenie usługi.  
  
4.  Uruchom Client.exe z katalogu \client\bin lub naciskając klawisz F5 w programie Visual Studio, aby skompilować i uruchomić. Aktywność klienta jest wyświetlany w aplikacji konsoli klienta.  
  
5.  Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-run-the-sample-across-computers"></a>Aby uruchomić przykład na komputerach  
  
1.  Przed zbudowaniem klienta część próbki, należy zmienić wartość adres punktu końcowego usługi w pliku Client.cs `CallServiceCustomClientIdentity` metody. Następnie tworzyć przykładowy kod.  
  
2.  Utwórz katalog na komputerze usługi.  
  
3.  Skopiuj pliki programu usługi z service\bin do katalogu na komputerze usługi. Także skopiować pliki pliku Setup.bat i Cleanup.bat na komputerze usługi.  
  
4.  Utwórz katalog na komputerze klienckim, aby pliki binarne klienta.  
  
5.  Skopiuj pliki programu klienta do katalogu klienta na komputerze klienckim. Także skopiować pliki pliku Setup.bat, Cleanup.bat i ImportServiceCert.bat do klienta.  
  
6.  W usłudze, uruchom `setup.bat service` w wierszu polecenia programu Visual Studio otwarty z uprawnieniami administratora. Uruchomiona `setup.bat` z `service` argument tworzy certyfikat usługi z domeny w pełni kwalifikowaną nazwę komputera i wyeksportuj certyfikat usługi do pliku o nazwie Service.cer.  
  
7.  Skopiuj plik Service.cer z katalogu usług do katalogu klienta na komputerze klienckim.  
  
8.  W pliku Client.exe.config na komputerze klienckim Zmień wartość adresu punktu końcowego, aby dopasować nowego adresu usługi. Istnieje wiele wystąpień, które musi zostać zmienione.  
  
9. Na komputerze klienckim należy uruchomić ImportServiceCert.bat w wierszu polecenia programu Visual Studio została otwarta z uprawnieniami administratora. Certyfikat usługi to importuje z pliku Service.cer do CurrentUser - TrustedPeople magazynu.  
  
10. Na komputerze, usługi uruchom Service.exe z wiersza polecenia.  
  
11. Na komputerze klienckim należy uruchomić Client.exe z wiersza polecenia. Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić po próbki  
  
-   Uruchamianie Cleanup.bat w folderze Przykłady po ukończeniu działania próbki.  
  
    > [!NOTE]
    >  Ten skrypt nie powoduje usunięcia usług certyfikatów na komputerze klienckim, podczas uruchamiania na komputerach w przykładzie. Jeśli uruchomiono [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] przykłady, które korzystają z certyfikatów na komputerach, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w CurrentUser - TrustedPeople magazynu. Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="see-also"></a>Zobacz też
