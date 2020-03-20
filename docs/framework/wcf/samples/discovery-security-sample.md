---
title: Zabezpieczenia odnajdywania — przykład
ms.date: 03/30/2017
ms.assetid: b8db01f4-b4a1-43fe-8e31-26d4e9304a65
ms.openlocfilehash: 00f81d1879d9157a7ecdfa0db8d2ea0d505ad5b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183743"
---
# <a name="discovery-security-sample"></a>Zabezpieczenia odnajdywania — przykład

Specyfikacja odnajdywania nie wymaga, aby punkty końcowe, które uczestniczą w procesie odnajdywania, były bezpieczne. Ulepszanie komunikatów odnajdywania za pomocą zabezpieczeń ogranicza różne typy ataków (zmiana wiadomości, odmowa usługi, powtarzanie, fałszowanie). W tym przykładzie implementuje kanały niestandardowe, które obliczają i weryfikują podpisy wiadomości przy użyciu formatu sygnatur kompaktowych (opisanego w sekcji 8.2 specyfikacji WS-Discovery). Próbka obsługuje zarówno [specyfikację discovery z 2005 r.,](http://specs.xmlsoap.org/ws/2005/04/discovery/ws-discovery.pdf) jak i [wersję 1.1.](http://docs.oasis-open.org/ws-dd/discovery/1.1/cs-01/wsdd-discovery-1.1-spec-cs-01.pdf)  
  
 Kanał niestandardowy jest stosowany na górze istniejącego stosu kanałów dla punktów końcowych odnajdywania i anonsu. W ten sposób nagłówek podpisu jest stosowany dla każdej wysłanej wiadomości. Podpis jest weryfikowany na odebranych wiadomości i gdy nie jest zgodny lub gdy wiadomości nie mają podpisu, wiadomości są usuwane. Aby podpisać i zweryfikować wiadomości, w przykładzie użyto certyfikatów.  
  
## <a name="discussion"></a>Dyskusji  
 WCF jest bardzo rozszerzalny i pozwala użytkownikom na dostosowanie kanałów zgodnie z potrzebami. Przykład implementuje odnajdowanie bezpiecznego elementu wiązania, który tworzy bezpieczne kanały. Bezpieczne kanały stosują i weryfikują podpisy wiadomości i są stosowane na bieżącym stosie.  
  
 Element bezpiecznego wiązania tworzy fabryki bezpiecznego kanału i odbiorników kanałów.  
  
## <a name="secure-channel-factory"></a>Bezpieczna fabryka kanałów  
 Fabryka bezpiecznego kanału tworzy kanały wyjściowe lub dupleksowe, które dodają kompaktowy podpis do nagłówków wiadomości. Aby wiadomości były jak najmniejsze, używany jest kompaktowy format podpisu. Struktura podpisu kompaktowego jest pokazana w poniższym przykładzie.  
  
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
> Został `PrefixList` dodany w 2008 Discovery protokół wersji.  
  
 Aby obliczyć podpis, przykład określa rozwinięte elementy podpisu. Podpis XML`SignedInfo`( ) jest `ds` tworzony przy użyciu prefiksu obszaru nazw, zgodnie ze specyfikacją WS-Discovery. Treść i wszystkie nagłówki w odnajdywaniu i adresowaniu obszarów nazw są odwoływane w podpisie, więc nie można ich manipulować. Każdy element, do którego istnieje odwołanie,http://www.w3.org/2001/10/xml-exc-c14n# jest przekształcany przy użyciu funkcji Kanonizacjahttp://www.w3.org/2000/09/xmldsig#sha1 wyłączności ( ), a następnie oblicza się wartość skrótu SHA-1 ( ). Na podstawie wszystkich elementów, do których istnieje odwołanie i ich wartościhttp://www.w3.org/2000/09/xmldsig#rsa-sha1 skrótu, wartość podpisu jest obliczana przy użyciu algorytmu RSA ( ).  
  
 Wiadomości są podpisane za pomocą certyfikatu określonego przez klienta. Lokalizacja magazynu, nazwa i nazwa podmiotu certyfikatu muszą być określone podczas tworzenia elementu wiązania. W `KeyId` podpisie kompaktowym reprezentuje identyfikator klucza tokenu podpisywania i jest identyfikatorem klucza podmiotu (SKI) tokenu podpisywania lub (jeśli ski nie istnieje) skrót SHA-1 klucza publicznego tokenu podpisywania.  
  
## <a name="secure-channel-listener"></a>Odbiornik bezpiecznego kanału  
 Odbiornik bezpiecznego kanału tworzy kanały wejściowe lub dupleksowe, które weryfikują kompaktowy podpis w odebranych wiadomościach. Aby zweryfikować podpis, `KeyId` określony w podpisie kompaktowym dołączonym do wiadomości jest używany do wybierania certyfikatu z określonego magazynu. Jeśli wiadomość nie ma podpisu lub sprawdzanie podpisu kończy się niepowodzeniem, wiadomości są usuwane. Aby użyć bezpiecznego powiązania, przykład definiuje fabrykę, która tworzy niestandardowe <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> i <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> z dodanym elementem wiązania bezpiecznego odnajdywania. Te bezpieczne punkty końcowe mogą być używane w detektorach anonsów odnajdywania i odnajdowalnych usługach.  
  
## <a name="sample-details"></a>Przykładowe szczegóły  
 Przykład zawiera bibliotekę i 4 aplikacje konsoli:  
  
- **DiscoverySecurityChannels:** Biblioteka, która udostępnia bezpieczne powiązanie. Biblioteka oblicza i weryfikuje kompaktowy podpis dla wiadomości wychodzących/przychodzących.  
  
- **Usługa**: Usługa odsłaniająca umowę ICalculatorService, hostowana samodzielnie. Usługa jest oznaczona jako wykrywalna. Użytkownik określa szczegóły certyfikatu używanego do podpisywania wiadomości, określając lokalizację i nazwę sklepu oraz nazwę podmiotu lub inny unikatowy identyfikator certyfikatu oraz magazyn, w którym znajdują się certyfikaty klienta (certyfikaty używane do sprawdzić podpis dla wiadomości przychodzących). Na podstawie tych szczegółów UdpDiscoveryEndpoint z dodatkowymi zabezpieczeniami jest zbudowany i używany.  
  
- **Klient:** Ta klasa próbuje odnajdować ICalculatorService i wywołać metody w usłudze. <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> Ponownie, a z dodatkowymi zabezpieczeniami jest zbudowany i używany do podpisywania i weryfikowania wiadomości.  
  
- **AnnouncementListener**: usługa hostowana samodzielnie, która nasłuchuje anonsów online i offline i używa bezpiecznego punktu końcowego anonsu.  
  
> [!NOTE]
> Jeśli plik Setup.bat jest uruchamiany wiele razy, menedżer certyfikatów monituje o wybranie certyfikatu do dodania, ponieważ istnieją zduplikowane certyfikaty. W takim przypadku setup.bat powinien zostać przerwany i Cleanup.bat powinien zostać wywołany, ponieważ duplikaty zostały już utworzone. Cleanup.bat monituje również o wybranie certyfikatu do usunięcia. Wybierz certyfikat z listy i kontynuuj wykonywanie cleanup.bat, dopóki nie pozostaną żadne certyfikaty.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tej próbki  
  
1. Wykonaj skrypt Setup.bat z wiersza polecenia dewelopera dla programu Visual Studio. Przykład używa certyfikatów do podpisywania i weryfikowania wiadomości. Skrypt tworzy certyfikaty przy użyciu pliku Makecert.exe, a następnie instaluje je za pomocą programu Certmgr.exe. Skrypt musi być uruchomiony z uprawnieniami administratora.  
  
2. Aby skompilować i uruchomić przykład, otwórz plik Security.sln w programie Visual Studio i wybierz pozycję **Odbuduj wszystko**. Zaktualizuj właściwości rozwiązania, aby uruchomić wiele projektów: wybierz **Start** dla wszystkich projektów z wyjątkiem DiscoverySecureChannels. Uruchom rozwiązanie normalnie.  
  
3. Po zakończeniu pracy z próbki, wykonać Cleanup.bat skrypt, który usuwa certyfikaty utworzone dla tego przykładu.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DiscoveryScenario`  
