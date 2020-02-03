---
title: Zabezpieczenia odnajdywania — przykład
ms.date: 03/30/2017
ms.assetid: b8db01f4-b4a1-43fe-8e31-26d4e9304a65
ms.openlocfilehash: cfee226f52bc5f001b2952b76b40ce0eb8aebceb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728852"
---
# <a name="discovery-security-sample"></a>Zabezpieczenia odnajdywania — przykład

Specyfikacja odnajdywania nie wymaga, aby punkty końcowe, które uczestniczą w procesie odnajdywania, były bezpieczne. Udoskonalenie komunikatów odnajdowania z zabezpieczeniami zmniejszają różne rodzaje ataków (zmiana komunikatów, odmowa usługi, powtarzanie, fałszowanie). Ten przykład implementuje niestandardowe kanały, które obliczają i weryfikują sygnatury komunikatów przy użyciu formatu podpisu kompaktowego (opisanego w sekcji 8,2 specyfikacji WS-Discovery). Przykład obsługuje [specyfikację odnajdywania 2005](http://specs.xmlsoap.org/ws/2005/04/discovery/ws-discovery.pdf) i [wersję 1,1](http://docs.oasis-open.org/ws-dd/discovery/1.1/cs-01/wsdd-discovery-1.1-spec-cs-01.pdf).  
  
 Niestandardowy kanał jest stosowany na podstawie istniejącego stosu kanału w celu odnajdywania i punktów końcowych anonsów. W ten sposób nagłówek podpisu jest stosowany dla każdej wysyłanej wiadomości. Podpis jest weryfikowany dla odebranych komunikatów i niezgodnych lub gdy komunikaty nie mają podpisu, komunikaty są usuwane. Aby podpisać i zweryfikować komunikaty, przykład używa certyfikatów.  
  
## <a name="discussion"></a>Dyskusji  
 Funkcja WCF jest bardzo rozszerzalna i umożliwia użytkownikom dostosowanie kanałów zgodnie z potrzebami. Przykład implementuje element funkcji odnajdywania bezpiecznego powiązania, który kompiluje bezpieczne kanały. Bezpieczne kanały stosują i weryfikują podpisy komunikatów i są stosowane na podstawie bieżącego stosu.  
  
 Element bezpiecznego powiązania kompiluje bezpieczne fabryki kanałów i odbiorniki kanałów.  
  
## <a name="secure-channel-factory"></a>Fabryka kanałów Secure Channel  
 Fabryka bezpiecznych kanałów tworzy kanały wyjściowe lub dupleksowe, które dodają skrócony podpis do nagłówków komunikatów. Aby zapewnić, że komunikaty są możliwie małe, jest używany format podpisu kompaktowego. Struktura skróconej sygnatury jest pokazana w poniższym przykładzie.  
  
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
> `PrefixList` został dodany w protokole odnajdywania wersji 2008.  
  
 Aby obliczyć sygnaturę, przykład określa rozwinięte elementy podpisu. Podpis XML (`SignedInfo`) jest tworzony przy użyciu prefiksu przestrzeni nazw `ds`, zgodnie z wymaganiami specyfikacji WS-Discovery. Treść i wszystkie nagłówki w przestrzeni nazw odnajdowania i adresowania są przywoływane w podpisie, więc nie mogą zostać naruszone. Każdy element, do którego się odwoływano, jest przekształcany przy użyciu klucza kanonicznego (http://www.w3.org/2001/10/xml-exc-c14n#), a następnie obliczana jest wartość skrótu SHA-1 (http://www.w3.org/2000/09/xmldsig#sha1). W oparciu o wszystkie elementy, do których istnieją odwołania i ich wartości skrótu, wartość podpisu jest obliczana przy użyciu algorytmu RSA (http://www.w3.org/2000/09/xmldsig#rsa-sha1).  
  
 Komunikaty są podpisane przy użyciu certyfikatu określonego przez klienta. Podczas tworzenia elementu powiązania należy określić lokalizację magazynu, nazwę i nazwę podmiotu certyfikatu. `KeyId` w podpisie kompaktowym reprezentuje identyfikator klucza tokenu podpisywania i jest identyfikatorem klucza podmiotu (SKI) tokenu podpisywania lub (Jeśli ta nazwa nie istnieje) skrót SHA-1 klucza publicznego tokenu podpisywania.  
  
## <a name="secure-channel-listener"></a>Odbiornik bezpiecznego kanału  
 Odbiornik bezpiecznego kanału tworzy kanały wejściowe lub dupleksowe, które weryfikują skrócony podpis w odebranych komunikatach. Aby sprawdzić podpis, `KeyId` określony w podpisie kompaktowym dołączonym do wiadomości jest używany do wybierania certyfikatu z określonego magazynu. Jeśli wiadomość nie ma podpisu lub sprawdzanie podpisu nie powiedzie się, komunikaty są usuwane. Aby użyć bezpiecznego powiązania, przykład definiuje fabrykę tworzącą <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> niestandardowe i <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> z dodaniem elementu bezpieczne odnajdywania. Te bezpieczne punkty końcowe mogą być używane w detektorach anonsów odnajdowania i odnajdywanych usługach.  
  
## <a name="sample-details"></a>Przykładowe szczegóły  
 Przykład obejmuje bibliotekę i 4 aplikacje konsolowe:  
  
- **DiscoverySecurityChannels**: Biblioteka, która uwidacznia bezpieczne powiązanie. Biblioteka oblicza i weryfikuje skrócony podpis dla komunikatów wychodzących/przychodzących.  
  
- **Usługa**: usługa ujawniania kontraktu ICalculatorService, który jest obsługiwany przez siebie. Usługa jest oznaczona jako wykrywalna. Użytkownik określa szczegóły certyfikatu służącego do podpisywania wiadomości przez określenie lokalizacji i nazwy magazynu oraz nazwy podmiotu lub innego unikatowego identyfikatora certyfikatu oraz magazynu, w którym znajdują się certyfikaty klienta (certyfikaty używane do Sprawdź podpis dla wiadomości przychodzących). W oparciu o te szczegóły UdpDiscoveryEndpoint z dodatkowymi zabezpieczeniami jest zbudowany i używany.  
  
- **Klient**: Ta klasa próbuje odnaleźć ICalculatorService i wywołać metody w usłudze. Ponownie <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> z dodatkowymi zabezpieczeniami jest zbudowany i używany do podpisywania i weryfikowania komunikatów.  
  
- **AnnouncementListener**: usługa samoobsługowa, która nasłuchuje w trybie online i powiadomienia w trybie offline i korzysta z punktu końcowego bezpiecznego anonsu.  
  
> [!NOTE]
> Jeśli Setup. bat jest uruchamiany wiele razy, Menedżer certyfikatów monituje o wybranie certyfikatu do dodania, ponieważ istnieją zduplikowane certyfikaty. W takim przypadku należy przerwać działanie Setup. bat i oczyścić. bat, ponieważ duplikaty zostały już utworzone. Oczyść. bat jest również monitowany o wybranie certyfikatu do usunięcia. Wybierz certyfikat z listy i kontynuuj wykonywanie czyszczenia. bat do momentu pozostawania certyfikatów.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1. Wykonaj skrypt Setup. bat na podstawie wiersz polecenia dla deweloperów dla programu Visual Studio. Przykład używa certyfikatów do podpisywania i weryfikowania wiadomości. Skrypt tworzy certyfikaty przy użyciu programu Makecert. exe, a następnie instaluje je za pomocą certmgr. exe. Skrypt musi być uruchamiany z uprawnieniami administratora.  
  
2. Aby skompilować i uruchomić przykład, Otwórz plik Security. sln w programie Visual Studio i wybierz polecenie **Kompiluj ponownie wszystko**. Zaktualizuj właściwości rozwiązania, aby uruchomić wiele projektów: wybierz pozycję **Rozpocznij** dla wszystkich projektów z wyjątkiem DiscoverySecureChannels. Uruchom rozwiązanie normalnie.  
  
3. Po wykonaniu przykładu wykonaj skrypt Oczyść. bat, który usuwa certyfikaty utworzone dla tego przykładu.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DiscoveryScenario`  
