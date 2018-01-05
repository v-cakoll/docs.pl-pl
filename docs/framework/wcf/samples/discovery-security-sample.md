---
title: "Zabezpieczenia odnajdywania — przykład"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8db01f4-b4a1-43fe-8e31-26d4e9304a65
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: f50334c8477b8823ef1dfb6abcae640e439d5ddd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="discovery-security-sample"></a>Zabezpieczenia odnajdywania — przykład
Specyfikacja odnajdywania nie wymaga czy punkty końcowe, które uczestniczą w procesie odnajdywania należy zabezpieczyć. Udoskonalanie komunikaty odnajdywania z zabezpieczeniami zmniejsza różnych rodzajów ataków (komunikatu zmiany, odmowę usługi, powtarzania, fałszowania). W tym przykładzie implementuje kanałów niestandardowych, które obliczeniowe i weryfikowania podpisów wiadomości w formacie kompaktowym podpisu (opisanej w sekcji 8.2 specyfikacji WS-Discovery). Przykład obsługuje zarówno [specyfikacji odnajdywania 2005](http://go.microsoft.com/fwlink/?LinkId=177912) i [wersji 1.1](http://go.microsoft.com/fwlink/?LinkId=179677).  
  
 Niestandardowy kanał jest stosowany na szczycie stosu istniejącego kanału dla punktów końcowych odnajdywania i anonsu. W ten sposób nagłówka podpis jest stosowana dla każdej wiadomości wysyłane. Podpis jest weryfikowany na odebrane wiadomości, a jeśli nie są zgodne lub komunikaty nie ma podpisu, komunikaty są usuwane. Aby zarejestrować i Sprawdź komunikaty, próbki korzysta z certyfikatów.  
  
## <a name="discussion"></a>Omówienie  
 Usługi WCF jest bardzo extensible i umożliwia użytkownikom możliwość dostosowywania kanałów zgodnie z potrzebami. Przykład implementuje element bezpiecznego powiązania odnajdywania, która tworzy bezpiecznych kanałów. Bezpieczne kanały zastosować i weryfikowania podpisów wiadomości i są stosowane na szczycie stosu bieżącej.  
  
 Element powiązania bezpiecznej kompilacje fabryk bezpiecznego kanału i odbiorniki kanałów.  
  
## <a name="secure-channel-factory"></a>Fabryka bezpiecznego kanału  
 Fabryka bezpiecznego kanału tworzy dane wyjściowe lub kanałach dupleksowych, które Dodawanie podpisu compact do nagłówków komunikatów. Aby zachować wiadomości możliwie najmniejsze format compact podpisu jest używana. W poniższym przykładzie przedstawiono struktury podpisu compact.  
  
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
>  `PrefixList` Został dodany w protokole 2008 w wersji odnajdywania.  
  
 Można obliczyć podpisu, próbki określa elementy rozszerzonej podpisu. Podpis XML (`SignedInfo`) jest tworzony przy użyciu `ds` prefiks przestrzeni nazw, co jest wymagane przez specyfikację WS-Discovery. Treść i wszystkich nagłówków odnajdywania i przestrzeni nazw adresowania odwołuje się podpisu, więc nie może być naruszona z. Każdy element do którego istnieje odwołanie jest przekształcana przy użyciu wyłącznego zapewniania kanoniczności (http://www.w3.org/2001/10/xml-exc-c14n#), a następnie wartość skrótu SHA-1 jest obliczana (http://www.w3.org/2000/09/xmldsig#sha1). Na podstawie wszystkich elementów i ich wartości, wartość podpisu jest obliczana, przy użyciu algorytmu RSA (http://www.w3.org/2000/09/xmldsig#rsa-sha1).  
  
 Komunikaty są podpisane za pomocą certyfikatu określonego przez klienta. Lokalizacja magazynu, nazwę i nazwa podmiotu certyfikatu należy określić podczas tworzenia elementu powiązania. `KeyId` w podpisie compact reprezentuje identyfikator klucza podpisywania tokenu i identyfikator klucza podmiotu (SKI) podpisywania tokenu jest lub (Jeśli nie ma SKI) wartości skrótu SHA-1 podpisywania tokenu klucza publicznego.  
  
## <a name="secure-channel-listener"></a>Bezpieczny kanał odbiornika  
 Bezpieczny kanał odbiornika tworzy danych wejściowych lub dupleks kanałów, które Sprawdź compact podpis odebranej wiadomości. Można zweryfikować podpisu, `KeyId` określone w kompaktowania podpisu w załączniku do wiadomości jest używany do wybierania certyfikatu w sklepie. Jeśli komunikat nie ma podpisu lub sprawdzenie podpisu nie powiedzie się, komunikaty są usuwane. Aby używać bezpiecznego powiązania, próbki określa fabrykę, która tworzy niestandardowe <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> i <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> z elementem bezpiecznego powiązania odnajdywania dodany. Te bezpieczne punkty końcowe można używać w odbiorników anonsu odnajdywania i wykrywalny usług.  
  
## <a name="sample-details"></a>Szczegóły próbki  
 Przykład obejmuje biblioteki i 4 aplikacje konsoli:  
  
-   **DiscoverySecurityChannels**: Biblioteka, która uwidacznia bezpiecznego powiązania. Biblioteka oblicza i weryfikuje podpis compact dla komunikatów wychodzących/przychodzących.  
  
-   **Usługa**: udostępnianie ICalculatorService kontraktu usługi, hostowana samodzielnie. Usługa jest oznaczona jako wykrywalny. Użytkownik określa szczegóły certyfikatu używanego do podpisywania wiadomości, określając lokalizację magazynu i nazwę i nazwa podmiotu lub inny unikatowy identyfikator certyfikatu i Magazyn, których certyfikaty klienta są znajduje (certyfikaty używane do sprawdzenie, czy podpis dla komunikatów przychodzących). W oparciu o te informacje, UdpDiscoveryEndpoint z zwiększyć bezpieczeństwo jest utworzony i używany.  
  
-   **Klient**: Ta klasa próbuje ICalculatorService i wywoływać metod w usłudze. Ponownie <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> z dodane zabezpieczeń jest utworzony i używany do podpisywania i Sprawdź komunikaty.  
  
-   **AnnouncementListener**: hostowanie Samoobsługowe usługa nasłuchuje anonsów online i offline i korzysta z punktu końcowego bezpiecznego anonsu.  
  
> [!NOTE]
>  Jeśli pliku Setup.bat jest uruchamiana wielokrotnie, Menedżer certyfikatów wyświetla monit o wybranie certyfikat, aby dodać, ponieważ istnieją zduplikowane certyfikatów. W takim przypadku powinien być przerwane pliku Setup.bat i powinna być wywoływana Cleanup.bat, ponieważ duplikaty zostały już utworzone. CleanUp.bat także wyświetli monit o wybranie certyfikatu do usunięcia. Wybierz certyfikat z listy i kontynuuje wykonywanie Cleanup.bat, dopóki pozostają nie ma żadnych certyfikatów.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Wykonanie skryptu pliku Setup.bat z wiersza polecenia programu Visual Studio. Przykład używa certyfikatów do podpisywania i Sprawdź komunikaty. Skrypt tworzy certyfikaty przy użyciu Makecert.exe, a następnie instaluje je przy użyciu Certmgr.exe. Skrypt musi zostać uruchomione z uprawnieniami administratora.  
  
2.  Aby skompilować i uruchomić przykład, otwórz plik Security.sln w programie Visual Studio i wybierz polecenie **rekompilacji wszystkiego**. Aktualizowanie właściwości rozwiązania, aby uruchomić wiele projektów: Wybierz **Start** dla wszystkich projektów z wyjątkiem DiscoverySecureChannels. Rozwiązanie, będą działać normalnie.  
  
3.  Po wykonaniu próbki, należy wykonać skrypt Cleanup.bat, który usuwa certyfikaty utworzone dla tego przykładu.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DiscoveryScenario`  
  
## <a name="see-also"></a>Zobacz też
