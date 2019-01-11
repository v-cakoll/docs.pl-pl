---
title: Zabezpieczenia odnajdywania — przykład
ms.date: 03/30/2017
ms.assetid: b8db01f4-b4a1-43fe-8e31-26d4e9304a65
ms.openlocfilehash: 9435afa7324ad9e0f2bf994b2f3ed5e54e5e2e7e
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2019
ms.locfileid: "54223107"
---
# <a name="discovery-security-sample"></a>Zabezpieczenia odnajdywania — przykład
Specyfikacja odnajdywania nie jest wymagane, czy punkty końcowe, które uczestniczą w procesie odnajdowania, można zabezpieczyć. Udoskonalanie komunikaty odnajdywania Dzięki zabezpieczeniom zmniejsza różne rodzaje ataków (komunikat zmiany, odmowa usługi, oparte na metodzie powtórzeń, fałszowanie adresów). W tym przykładzie implementuje niestandardowe kanały, które obliczeń i sprawdzanie podpisów komunikat w formacie compact podpisu (opisanej w sekcji 8.2 specyfikacji WS-Discovery). Przykład obsługuje zarówno [specyfikacji odnajdywania 2005](https://go.microsoft.com/fwlink/?LinkId=177912) i [wersji 1.1](https://go.microsoft.com/fwlink/?LinkId=179677).  
  
 Niestandardowy kanał jest stosowany na podstawie istniejącego stosu kanału punktów końcowych odnajdywania i anonsu. W ten sposób nagłówka podpisu jest stosowany dla każdej wiadomości wysłane. Podpis jest weryfikowany na odebrane komunikaty, a jeśli nie są zgodne lub komunikaty nie posiada podpisu, komunikaty są usuwane. Zaloguj się i Sprawdź komunikaty, w przykładzie użyto certyfikatów.  
  
## <a name="discussion"></a>Dyskusja  
 Usługi WCF jest bardzo rozszerzalny. Umożliwia ono użytkownikom możliwość dostosowywania kanały zgodnie z potrzebami. Przykład implementuje element bezpiecznego powiązania odnajdywania, który tworzy bezpiecznych kanałów. Bezpieczne kanały Zastosuj sprawdzanie podpisów wiadomości i są stosowane na podstawie bieżącego stosu.  
  
 Element bezpiecznego powiązania tworzy bezpieczny kanał fabryk i odbiorniki kanałów.  
  
## <a name="secure-channel-factory"></a>Fabryka bezpiecznego kanału  
 Fabryka bezpiecznego kanału tworzy dane wyjściowe lub dwukierunkowe kanały, które Dodawanie podpisu compact do nagłówków wiadomości. Aby zachować wiadomości możliwie najmniejsze format podpisu compact jest używany. Struktura compact podpisu przedstawiono w poniższym przykładzie.  
  
```xml  
<d:Security ... >   
  [<d:Sig Scheme="xs:anyURI"   
         [KeyId="xs:base64Binary"]?  
          Refs="..."  
         [PrefixList]="xs:NMTOKENS"   
          Sig="xs:base64Binary"   
          ... />]?  
  ...   
</d:Security>  
```  
  
> [!NOTE]
>  `PrefixList` Został dodany w protokole wersji 2008 odnajdywania.  
  
 Do obliczania podpisu, przykład określa elementy rozwiniętej podpisu. Podpis XML (`SignedInfo`) jest tworzony przy użyciu `ds` prefiks przestrzeni nazw, zgodnie z wymogami specyfikację protokołu WS Discovery. Treści i wszystkie nagłówki odnajdywania i adresowania przestrzenie nazw są przywoływane w podpisie, aby nie dało się. Każdy odnośny element jest przekształcana przy użyciu wyłączne Canonicalization (http://www.w3.org/2001/10/xml-exc-c14n# ), a następnie jest obliczana wartość skrótu SHA-1 (http://www.w3.org/2000/09/xmldsig#sha1 ). Na podstawie wszystkich elementów i ich wartości skrótu, podpis wartość jest obliczana przy użyciu algorytmu RSA (http://www.w3.org/2000/09/xmldsig#rsa-sha1 ).  
  
 Komunikaty są podpisywane przy użyciu określonych przez klienta certyfikatu. Lokalizacja magazynu, nazwę i nazwę podmiotu certyfikatu, należy określić po utworzeniu elementu powiązania. `KeyId` w podpisie compact reprezentuje identyfikator klucza podpisywania tokenu i jest podpisywania tokenu identyfikatora klucza podmiotu (NARCIARSKIE) lub (Jeśli nie istnieje NARCIARSKIE) Skrót SHA-1, publicznego klucza podpisywania tokenu.  
  
## <a name="secure-channel-listener"></a>Odbiornik bezpiecznego kanału  
 Odbiornik bezpiecznego kanału tworzy wejściowej lub dwukierunkowe kanały, które zweryfikować podpisu compact w odebranej wiadomości. Można zweryfikować podpisu, `KeyId` określone w kompaktowania podpisu, w załączniku do wiadomości jest używany do wybierania certyfikatu w sklepie. Jeśli komunikat nie ma podpisu lub sprawdzania podpisu kończy się niepowodzeniem, komunikaty są porzucane. Aby używać bezpiecznego powiązania, przykład określa fabrykę, która tworzy niestandardowy <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> i <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> z elementem bezpiecznego powiązania dodano odnajdywania. Te bezpieczne punkty końcowe może służyć w usługach wykrywalny i odbiorników ogłoszenie odnajdywania.  
  
## <a name="sample-details"></a>Przykład szczegółów  
 Przykład zawiera bibliotekę i 4 aplikacje konsoli:  
  
-   **DiscoverySecurityChannels**: Biblioteka, która udostępnia bezpiecznego powiązania. Biblioteka oblicza i weryfikuje podpis compact dla wiadomości wychodzących/przychodzących.  
  
-   **Usługa**: Udostępnianie ICalculatorService kontraktu, samodzielnie hostowanej usługi. Usługa jest oznaczona jako wykrywalny. Użytkownik określa szczegóły certyfikatu używanego do podpisywania wiadomości, określając lokalizację magazynu i nazw i nazwę podmiotu lub inny unikatowy identyfikator certyfikatu i magazynu, których certyfikaty klienta znajduje się (certyfikatów służących do Sprawdzanie podpisu dla komunikatów przychodzących). Oparte na te informacje, UdpDiscoveryEndpoint o bezpieczeństwo jest wbudowane i używać.  
  
-   **Klient**: Ta klasa próbuje odnaleźć ICalculatorService i wywoływać metody dla usługi. Ponownie <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> dodać bezpieczeństwo jest wbudowane i używany do podpisywania i Sprawdź komunikaty.  
  
-   **AnnouncementListener**: Samodzielnie hostowany usługa, która nasłuchuje zapowiedzi online i offline, a następnie używa ogłoszenie bezpiecznego punktu końcowego.  
  
> [!NOTE]
>  Jeśli Setup.bat jest wykonywany wielokrotnie, w Menedżer certyfikatów zostanie wyświetlony monit o wybranie certyfikatu, aby dodać, jak istnieją zduplikowane certyfikatów. W takim przypadku Setup.bat powinien przerwane i Cleanup.bat powinna być wywoływana, ponieważ duplikaty zostały już utworzone. CleanUp.bat również wyświetli monit o wybranie certyfikatu do usunięcia. Wybierz certyfikat z listy i kontynuowania wykonywania Cleanup.bat, dopóki pozostałych żadnych certyfikatów.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Wykonaj skrypt Setup.bat jest z wiersza polecenia dla deweloperów programu Visual Studio. W przykładzie użyto certyfikaty do podpisywania i Sprawdź komunikaty. Skrypt tworzy certyfikaty przy użyciu Makecert.exe, a następnie instaluje je przy użyciu Certmgr.exe. Skrypt musi być uruchamiane z uprawnieniami administratora.  
  
2.  Aby skompilować i uruchomić przykład, otwórz plik Security.sln w programie Visual Studio, a następnie wybierz **Kompiluj wszystko ponownie**. Aktualizowanie właściwości rozwiązania, aby uruchomić wiele projektów: Wybierz **Start** dla wszystkich projektów, z wyjątkiem DiscoverySecureChannels. Rozwiązania będą działać normalnie.  
  
3.  Po wykonaniu czynności przy użyciu przykładu należy wykonać skrypt Cleanup.bat, który usuwa certyfikaty utworzone dla tego przykładu.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DiscoveryScenario`  
  
## <a name="see-also"></a>Zobacz też
