---
title: Podstawowe pojęcia programu Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], concepts
- concepts [WCF]
- fundamentals [WCF]
- Windows Communication Foundation [WCF], concepts
ms.assetid: 3e7e0afd-7913-499d-bafb-eac7caacbc7a
ms.openlocfilehash: 44b36fc917ceb30141d7d2235b8bb364d3b998c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="fundamental-windows-communication-foundation-concepts"></a>Podstawowe pojęcia programu Windows Communication Foundation
Ten dokument zawiera ogólny widok architektury usług Windows Communication Foundation (WCF). Jest on przeznaczony do podstawowych pojęć i sposób ich dopasowania. Samouczek dotyczący tworzenia najprostszym wersji [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi i klienta, zobacz [Wprowadzenie — samouczek](../../../docs/framework/wcf/getting-started-tutorial.md). Aby dowiedzieć się [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] programowania, zobacz [podstawowe programowania WCF](../../../docs/framework/wcf/basic-wcf-programming.md).  
  
## <a name="wcf-fundamentals"></a>Podstawowe informacje na temat usługi WCF  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] to środowisko uruchomieniowe i zestaw interfejsów API do tworzenia systemów, które wysyłać wiadomości między usług i klientów. Te same infrastruktura i interfejsy API są używane do tworzenia aplikacji, które komunikują się z innymi aplikacjami na tym samym komputerze lub w systemie znajduje się w innej firmy, który jest dostępny za pośrednictwem Internetu.  
  
### <a name="messaging-and-endpoints"></a>Obsługa komunikatów i punkty końcowe  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] opiera się na koncepcji komunikacji wiadomości i niczego, które mogą być modelowane zgodnie z komunikatu (na przykład żądania HTTP lub wiadomości MSMQ (MSMQ)) może być reprezentowany w jednolity sposób w modelu programowania. Dzięki temu ujednolicony interfejs API przez różne mechanizmy transportu.  
  
 Model rozróżnia *klientów*, które są aplikacje, które inicjują komunikację, i *usług*, które są aplikacje, które poczekaj, aż klienci komunikują się z nimi i reagowanie na który komunikacji. Pojedynczej aplikacji może działać jako klient i usługa. Aby uzyskać przykłady, zobacz [usługi dwukierunkowe](../../../docs/framework/wcf/feature-details/duplex-services.md) i [sieci Peer-to-Peer](../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
 Komunikaty są wysyłane między punktami końcowymi. *Punkty końcowe* miejsc, w której wysyłane lub odbierane wiadomości (lub obie) i określają one wszystkie informacje wymagane do wymiany komunikatów. Udostępnia usługi punktów końcowych aplikacji (a także zero lub więcej punktów końcowych infrastruktury), a klient generuje punktu końcowego, który jest zgodny z jednym z punktów końcowych usługi.  
  
 *Punktu końcowego* opisano w sposób oparta na standardach, wysyłania wiadomości, jak mają być wysyłane i jak powinna wyglądać wiadomości. Usługi można ujawnić te informacje jako metadane przetwarzające przez klientów do generowania odpowiednich [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klientów i komunikacja *stosy*.  
  
### <a name="communication-protocols"></a>Protokoły komunikacji  
 Jeden wymagany jest element stosu komunikacji *protokołu transportu*. Wiadomości mogą być wysyłane za pośrednictwem sieci intranet i Internet za pomocą transportu wspólne, takie jak HTTP i TCP. Uwzględniono innych transportów obsługujące komunikacji z aplikacjami usługi kolejkowania komunikatów i węzły w sieci równorzędnej siatki. Można dodać więcej mechanizmów transportu za pomocą wbudowanych rozszerzenia punkty [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  
  
 Innego wymaganego elementu stosu komunikacji jest kodowanie, które określa sposób formatowania żadnych podanym komunikatem. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] udostępnia następujące rodzaje kodowania:  
  
-   Kodowanie, interoperacyjne kodowania tekstu.  
  
-   Komunikat transmisji optymalizacji mechanizmu (MTOM) kodowania, czyli sposób interoperacyjne wydajnie wysyłania niestrukturalnych dane binarne do i z usługi.  
  
-   Binarny kodowanie transferu wydajne.  
  
 Można dodać więcej kodowania mechanizmów (na przykład kompresji kodowanie) przy użyciu wbudowanych rozszerzenia punkty [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  
  
### <a name="message-patterns"></a>Wzorce wiadomości  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] obsługuje kilka wzorce obsługi komunikatów, w tym żądanie odpowiedź, jednokierunkowe i komunikację dupleksową. Różnych transportów obsługuje różne wzorce obsługi komunikatów, a w związku z tym wpływają na typy interakcji, które obsługują. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Interfejsów API i środowiska uruchomieniowego też pomóc Ci do wysyłania wiadomości w sposób bezpieczny i niezawodny.  
  
## <a name="wcf-terms"></a>Warunki WCF  
 Inne pojęć i terminów używanych w [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] dokumentacji to m.in.  
  
 — komunikat  
 Samodzielna jednostka danych, które może składać się z kilku części, łącznie z treści i nagłówków.  
  
 usługa  
 Strukturą ujawniającą jeden lub więcej punktów końcowych z każdego punktu końcowego udostępnianie co najmniej jedną operację usługi.  
  
 endpoint  
 Konstrukcja w wiadomości, które są wysyłane lub odbierane (lub obie). W tym zawiera lokalizację (adresu), która określa, gdzie mogą być wysyłane wiadomości, specyfikacja mechanizm komunikacji (powiązanie), który opisano, jak można wysłać wiadomości, i definicji zestaw komunikatów, które mogą być wysyłane lub odbierane (lub obie) Lokalizacja (kontrakt usługi) w tym artykule opisano, jakie komunikaty mogą być wysyłane.  
  
 A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi jest narażony na świecie jako kolekcja punktów końcowych.  
  
 punkt końcowy aplikacji  
 Punkt końcowy udostępniany przez aplikację i że odpowiada kontrakt usługi zaimplementowana przez aplikację.  
  
 punkt końcowy infrastruktury  
 Punkt końcowy, który jest udostępniany przez infrastruktury w celu ułatwienia funkcji, które jest wymagane lub udostępniony przez usługę, która odnosi się do kontraktu usługi. Na przykład usługa może być infrastruktury punktu końcowego, który zawiera informacje o metadanych.  
  
 adres  
 Określa lokalizację, w którym są odbierane wiadomości. Został określony jako zasób identyfikator URI (Uniform). Części schematu identyfikatora URI nazwy mechanizm transportu do adresu, na przykład HTTP i TCP. Hierarchiczna część identyfikatora URI zawiera unikatową lokalizację, w których format jest zależny od mechanizm transportu.  
  
 Adres punktu końcowego można tworzyć adresy unikatowy punktów końcowych dla każdego punktu końcowego w usłudze lub, w niektórych warunkach udostępnianie adresu w obrębie punktów końcowych. W poniższym przykładzie przedstawiono adresu przy użyciu protokołu HTTPS przez port inny niż domyślny:  
  
```  
HTTPS://cohowinery:8005/ServiceModelSamples/CalculatorService  
```  
  
 powiązanie  
 Określa, jak punkt końcowy komunikuje się do środowiska. Jest zbudowane zestawu o nazwie elementy wiązania, które "stosu" jeden nad drugim do utworzenia infrastruktury komunikacji składników. Co najmniej powiązanie definiuje transportu (np. HTTP lub TCP) i kodowanie używane (np. tekst lub binarny). Powiązania mogą zawierać elementy powiązania, które Określ szczegóły, takie jak te mechanizmy zabezpieczeń używany do zabezpieczania komunikatów lub komunikatów używane przez punkt końcowy. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usług](../../../docs/framework/wcf/configuring-services.md).  
  
 element powiązania  
 Reprezentuje powiązanie, takich jak transport, kodowania, implementacja protokołu poziomie infrastruktury (na przykład WS-ReliableMessaging) lub innych składników stosu komunikacji z określonym wystąpieniem.  
  
 zachowania  
 Składnik, który określa różne aspekty środowiska wykonawczego usługi, punkt końcowy, określonej operacji lub klienta. Zachowania są pogrupowane według zakresu: zachowań wspólnych globalnie wpływają na wszystkie punkty końcowe, zachowania usługi wpływania na aspekty tylko związane z usługą tylko właściwości powiązanych z punktu końcowego wpłynąć na zachowania punktu końcowego i zachowania poziomu operacji wpływają na konkretnym operacje. Na przykład jeden zachowanie usługi jest ograniczanie, który określa, w jaki sposób usługa reaguje, gdy część wiadomości grozi przeciąży możliwości obsługi. Zachowanie punktu końcowego z drugiej strony, określa tylko aspektów, które mają zastosowanie do punktów końcowych, jak i gdzie można znaleźć poświadczeń zabezpieczeń.  
  
 powiązania dostarczane przez system  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] zawiera liczbę powiązania dostarczane przez system. Te są kolekcjami elementów, które są zoptymalizowane pod kątem konkretnych scenariuszy wiązania. Na przykład <xref:System.ServiceModel.WSHttpBinding> zaprojektowano pod kątem współdziałania z usługami, które implementują różnych WS-* specyfikacji. Te wstępnie zdefiniowanych powiązań zaoszczędzić czas, z uwzględnieniem tylko te opcje, które można poprawnie zastosować do danego scenariusza. Jeśli wstępnie zdefiniowane powiązania nie spełnia wymagań, można tworzyć własnego niestandardowego powiązania.  
  
 Konfiguracja i kodowania  
 Formant aplikacji można przeprowadzić albo za pomocą kodowania, za pośrednictwem konfiguracji, lub obie te grupy. Konfiguracja ma możliwość kogoś innego niż developer (na przykład administrator sieci), aby ustawić parametry klienta i usługi, po zapisaniu kodu i bez konieczności ponownego kompilowania. Konfiguracja nie tylko służy do ustawiania wartości podobnie jak adresy punktów końcowych, ale również umożliwia dalsze kontrolę umożliwiając dodać punkty końcowe, powiązania i zachowania. Kodowanie umożliwia deweloperowi zachować ścisłą kontrolę nad wszystkimi składnikami usługi lub klienta i wszelkich ustawień za pomocą konfiguracji mogą być kontrolowane i w razie potrzeby zastąpione przez kod.  
  
 Operacja usługi  
 Procedura zdefiniowane w kodzie usługi, która implementuje funkcje dla operacji. Ta operacja jest widoczne dla klientów jako metody na [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klienta. Metoda może zwracać wartości, można podjąć opcjonalne liczba argumentów, lub nie przyjmują argumentów i zwraca odpowiedź nie. Na przykład operacja, która działa jako prosty tekst "Hello" mogą być używane jako powiadomienie obecności klienta i rozpocząć czynności.  
  
 kontrakt usługi  
 Wiąże ze sobą wielu powiązanych operacji w pojedynczą jednostkę funkcjonalności. Kontrakt można zdefiniować ustawienia poziomu usług, takie jak przestrzeń nazw usługi, kontrakt wywołania zwrotnego odpowiedniego i inne takie ustawienia. W większości przypadków kontrakt jest definiowana za tworzenie interfejsu w języku programowania i stosowanie <xref:System.ServiceModel.ServiceContractAttribute> do interfejsu. Wyniki kodu usługi rzeczywiste zaimplementowanie interfejsu.  
  
 Kontrakt operacji  
 Kontrakt operacji określa parametry oraz zwracany typ operacji. Podczas tworzenia interfejs, który definiuje kontrakt usługi, oznaczającego kontrakt operacji stosując <xref:System.ServiceModel.OperationContractAttribute> atrybutu do każdej definicji metody, która jest częścią kontraktu. Operacje mogą być modelowane jako pobieranie pojedynczej wiadomości i zwracanie pojedynczej wiadomości lub biorąc zestaw typów i zwracanie typu. W drugim przypadku system będzie określić format wiadomości, które muszą być wymieniane dla tej operacji.  
  
 kontrakt komunikatów  
 Opisuje format komunikatu. Na przykład deklaruje, czy elementy wiadomości powinny przejść w nagłówkach i treści, jaki poziom zabezpieczeń powinny być stosowane do elementy wiadomości i tak dalej.  
  
 kontrakt błędu  
 Może być skojarzony z operacji usługi do oznaczania błędów, które może być zwracany do obiektu wywołującego. Operacja może mieć zero lub więcej błędów skojarzonych z nim. Te błędy są błędach SOAP, modelowane jako wyjątki w modelu programowania.  
  
 kontrakt danych  
 Opisy w metadanych typów danych, które są używane przez usługę. Dzięki temu inne osoby do współpracy z usługą. Typy danych można używać w każdej części komunikatu, na przykład jako parametry lub typy zwracane. Jeśli usługa używa tylko proste typy, jest niepotrzebna jawnie używać kontraktów danych.  
  
 hosting  
 Usługa musi być obsługiwana przez procesu. A *hosta* jest aplikacja, która określa okres istnienia usługi. Usługi można samodzielnie hostowana lub zarządza istniejącego procesu hostingu.  
  
 hostowanie samoobsługowe  
 Usługa, która jest uruchamiany w ramach aplikacji utworzony przez dewelopera. Deweloper steruje jego okres istnienia, ustawia właściwości usługi, otwiera usługi, (która ustawia ją w trybie nasłuchiwania) i zamknięcie usługi.  
  
 proces hostingu  
 Aplikacja jest przeznaczona do usługi hosta. Obejmują one Internet Information Services (IIS), usługi aktywacji systemu Windows (WAS) i usług systemu Windows. W tych scenariuszach hostowanej hosta kontroluje cykl życia usługi. Na przykład za pomocą usług IIS można ustawić wirtualny katalog zawierający plik zestawu i konfiguracji usługi. Po odebraniu wiadomości usług IIS umożliwia uruchomienie usługi i kontroluje jego okres istnienia.  
  
 tworzenie instancji  
 Usługa ma wystąpień modelu. Istnieją trzy modele wystąpień: "jednym", w którym pojedynczego obiektu CLR usług wszystkich klientów; " na wywołanie,"w którym jest tworzony nowy obiekt CLR do obsługi każdego wywołania klienta; i "na"sesji, w które obiekty Zestaw CLR, jest tworzony, jeden dla każdej sesji oddzielne. Wybór wystąpień modelu zależy od wymagań aplikacji i wzorzec oczekiwane wykorzystanie usługi.  
  
 Aplikacja kliencka  
 Program, który wymienia wiadomości z jedną lub więcej punktów końcowych. Aplikacja kliencka rozpoczyna się od utworzenia wystąpienia [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klienta i wywołanie metody [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klienta. Należy do pojedynczej aplikacji może zawierać zarówno klient, jak i usługi.  
  
 Kanał  
 Konkretną implementację elementu powiązania. Powiązanie reprezentuje konfigurację i kanał jest skojarzony z tym konfiguracji wdrożenia. W związku z tym jest skojarzone z każdym elementem powiązania kanału. Kanały stosu na siebie, aby utworzyć konkretną implementację powiązania: stosu kanału.  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Klienta  
 Aplikacja kliencka strukturą ujawniającą operacji usługi jako metody (w [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] programowania w języku, takich jak Visual Basic lub Visual C#). Każdej aplikacji może obsługiwać [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klienta, w tym aplikacji, która obsługuje usługę. W związku z tym istnieje możliwość utworzyć usługę, która obejmuje [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klientów z innymi usługami.  
  
 A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klienta mogą być generowane automatycznie za pomocą [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) i wskazując uruchomioną usługę, która publikuje metadane.  
  
 metadane  
 W usłudze opisano charakterystyki usługę jednostki zewnętrznej trzeba poznać, aby komunikować się z usługą. Metadane mogą być używane przez [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do generowania [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klienta i towarzyszące konfiguracji, który aplikacja kliencka służy do interakcji z usługą.  
  
 Metadane udostępnianych przez usługę obejmuje dokumentach schematów XML, których definiowanie kontraktu danych usługi, i dokumentów WSDL, których opisano metody usługi.  
  
 Po włączeniu metadanych dla usługi jest generowana automatycznie przez [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] sprawdzając usługę i jej punkty końcowe. Publikowanie metadanych z usługą, musisz jawnie włączyć zachowanie metadanych.  
  
 zabezpieczenia  
 W [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], obejmuje poufność (szyfrowanie wiadomości, aby zapobiec podsłuchiwaniu), integralność (oznacza wykrywania naruszeniu wiadomości), uwierzytelniania (oznacza do sprawdzania poprawności serwerów i klientów) i autoryzacji ( Kontrola dostępu do zasobów). Funkcje te są udostępniane przez albo korzystanie z usług istniejące mechanizmy zabezpieczeń, takich jak TLS za pośrednictwem protokołu HTTP (znanej także jako HTTPS) lub wdrażanie jednego lub kilku różnych WS-* specyfikacji zabezpieczenia.  
  
 Tryb zabezpieczeń Transport  
 Określa, że poufności, integralności i uwierzytelniania są udostępniane przez mechanizmy warstwy transportu (na przykład HTTPS). Korzystając z transportu, takich jak HTTPS, w tym trybie ma zaletą jest efektywne pod względem wydajności, a także rozpoznawanych ze względu na jego występowanie w Internecie. Wadą jest to, że tego rodzaju zabezpieczeń jest stosowane osobno każdego przeskoku w ścieżce komunikacji wprowadzania komunikacji narażony na atak typu "man w środku".  
  
 Tryb zabezpieczeń komunikatów  
 Określa, że zabezpieczenia dzięki implementacji co najmniej jednego wymagania zabezpieczeń, takich jak specyfikacje o nazwie [zabezpieczenia usługi sieci Web: zabezpieczenia komunikatów SOAP](http://go.microsoft.com/fwlink/?LinkId=94684). Każdy komunikat zawiera mechanizmy niezbędne do zapewnienia bezpieczeństwa podczas jego przesyłania i umożliwienie odbiorcy przed naruszeniem i do odszyfrowywania wiadomości. W tym sensie zabezpieczeń jest hermetyzowany w każdej wiadomości, zapewniając zabezpieczeń na trasie między wieloma przeskokami. Ponieważ informacje o zabezpieczeniach staje się częścią komunikatu, jest również może zawierać wiele rodzajów poświadczeń z komunikatu (te są nazywane *oświadczeń*). Takie podejście charakteryzuje się również korzystać z włączeniem komunikat, aby bezpiecznie są przesyłane za pośrednictwem żadnych transportu, w tym wiele transportów między jego źródło i miejsce docelowe. Wadą tego podejścia jest złożoność mechanizmów kryptograficznych zatrudnionych, co powoduje wpływ na wydajność.  
  
 transportu z trybu zabezpieczenia wiadomości poświadczeń  
 Określa użycie warstwy transportu, aby zagwarantować poufność, uwierzytelniania i integralności wiadomości, podczas każdej wiadomości może zawierać wiele poświadczeń (oświadczeń) wymagany przez odbiorców w wiadomości.  
  
 WS-*  
 Skrócona forma rosnącej gamy parametry usługi sieci Web (WS), na przykład WS-Security, WS-ReliableMessaging i tak dalej, które zostały wdrożone w [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  
  
## <a name="see-also"></a>Zobacz też  
 [Co to jest program Windows Communication Foundation](../../../docs/framework/wcf/whats-wcf.md)  
 [Architektura WCF (Windows Communication Foundation)](../../../docs/framework/wcf/architecture.md)  
 [Architektura zabezpieczeń](http://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)
