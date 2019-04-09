---
title: Niestandardowe uaktualnienia strumienia
ms.date: 03/30/2017
ms.assetid: e3da85c8-57f3-4e32-a4cb-50123f30fea6
ms.openlocfilehash: cd8385194e1f24d246e6fc398462b45bacbe15d6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127364"
---
# <a name="custom-stream-upgrades"></a>Niestandardowe uaktualnienia strumienia
Zorientowane na Stream transportu, takich jak TCP i nazwane potoki działają na ciągłego strumienia bajtów między klientem i serwerem. Ten strumień jest wykonywane przez <xref:System.IO.Stream> obiektu. W przypadku uaktualniania strumienia klient chce Dodawanie warstwy protokołu opcjonalne stosu kanału i prosi drugiej stronie kanał komunikacyjny, aby to zrobić. Uaktualnienie strumienia polega na zastąpienie oryginalnego <xref:System.IO.Stream> obiektu z uaktualnionym.  
  
 Na przykład można skompilować skompresowanego strumienia bezpośrednio na strumień transportowy. W takim przypadku oryginalnego transportu <xref:System.IO.Stream> jest zastępowany przy użyciu jednego, który otacza kompresja <xref:System.IO.Stream> wokół oryginalnego.  
  
 Można zastosować wiele uaktualnienia strumienia, każdy zawijania mieszanego.  
  
## <a name="how-stream-upgrades-work"></a>Sposób działania uaktualnień Stream  
 Dostępne są cztery składniki podczas procesu uaktualniania strumienia.  
  
1.  Strumień uaktualnienia *inicjatora* rozpoczyna proces: w czasie wykonywania można zainicjować żądanie drugiej stronie połączenia uaktualnić z warstwy transportowej kanału.  
  
2.  Strumień uaktualnienia *wykonawca* przeprowadza uaktualnienie: w czasie wykonywania odbierze żądanie uaktualnienia z innej maszyny i jeśli to możliwe, akceptuje uaktualnienia.  
  
3.  Uaktualnienie *dostawcy* tworzy *inicjatora* na komputerze klienckim i *wykonawca* na serwerze.  
  
4.  Uaktualnienie strumienia *Element powiązania* jest dodawany do powiązania usługi i klienta i tworzy dostawcę w czasie wykonywania.  
  
 Należy pamiętać, że w przypadku kilku uaktualnień inicjatora i wykonawca hermetyzacji maszyny stanu do wymuszania które uaktualnienia przejścia są prawidłowe dla każdego inicjacji.  
  
## <a name="how-to-implement-a-stream-upgrade"></a>Jak wdrożyć uaktualnienie Stream  
 Windows Communication Foundation (WCF) zawiera cztery `abstract` klas, które można zaimplementować:  
  
-   <xref:System.ServiceModel.Channels.StreamUpgradeInitiator?displayProperty=nameWithType>  
  
-   <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor?displayProperty=nameWithType>  
  
-   <xref:System.ServiceModel.Channels.StreamUpgradeProvider?displayProperty=nameWithType>  
  
-   <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement?displayProperty=nameWithType>  
  
 Aby zaimplementować uaktualnienia strumienia niestandardowe, należy wykonać następujące czynności. Ta procedura implementuje minimalny strumienia proces uaktualniania na komputerach klienta i serwera.  
  
1.  Utwórz klasę, która implementuje <xref:System.ServiceModel.Channels.StreamUpgradeInitiator>.  
  
    1.  Zastąp <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.InitiateUpgrade%2A> metody do wykonania w usłudze stream, można uaktualnić, a następnie wróć uaktualnionego strumienia. Ta metoda działa synchronicznie; dostępne są analogiczne metody, aby zainicjować uaktualnienie asynchronicznie.  
  
    2.  Zastąp <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> metodę sprawdzania, czy są dostępne dodatkowe uaktualnienia.  
  
2.  Utwórz klasę, która implementuje <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor>.  
  
    1.  Zastąp <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.AcceptUpgrade%2A> metody do wykonania w usłudze stream, można uaktualnić, a następnie wróć uaktualnionego strumienia. Ta metoda działa synchronicznie; istnieją podobne metody o zgodę na uaktualnienie asynchronicznie.  
  
    2.  Zastąp <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A> metodę pozwala ustalić, czy uaktualnienie wymagane jest obsługiwana przez tego uaktualnienia wykonawca na tym etapie w procesie uaktualniania.  
  
3.  Utwórz klasę implementuje <xref:System.ServiceModel.Channels.StreamUpgradeProvider>. Zastąp <xref:System.ServiceModel.Channels.StreamUpgradeProvider.CreateUpgradeAcceptor%2A> i <xref:System.ServiceModel.Channels.StreamUpgradeProvider.CreateUpgradeInitiator%2A> metody do zwrócenia wystąpienia wykonawca i inicjatora zdefiniowane w kroku 2 i 1.  
  
4.  Utwórz klasę, która implementuje <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement>.  
  
    1.  Zastąp <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement.BuildClientStreamUpgradeProvider%2A> metody na kliencie i <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement.BuildServerStreamUpgradeProvider%2A> metody dla usługi.  
  
    2.  Zastąp <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> metody na kliencie i <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> metody dla usługi, aby dodać uaktualnienia elementu powiązania do <xref:System.ServiceModel.Channels.BindingContext.BindingParameters%2A>.  
  
5.  Dodaj nowy element strumienia w uaktualnienia powiązania do powiązania na komputerach serwera i klienta.  
  
## <a name="security-upgrades"></a>Aktualizacje zabezpieczeń  
 Dodawanie uaktualnienie zabezpieczeń jest specjalizowanej wersji strumienia ogólne procesu uaktualniania.  
  
 Usługi WCF już zawiera dwa elementy wiązania dla uaktualnienie zabezpieczenia strumienia. Konfiguracja zabezpieczeń na poziomie transportu jest hermetyzowany przez <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement> i <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement> którego można konfigurować i dodane do niestandardowego powiązania. Rozszerzenia te elementy powiązania <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement> klasę, która tworzy strumień klienta i serwera dostawców uaktualnienia. Te elementy powiązania ma metody tworzące strumienia wyspecjalizowanych zabezpieczeń klasy dostawcy uaktualnienia, które nie są `public`, dlatego w tych dwóch przypadkach wszystko, czego potrzebujesz, aby zrobić to dodanie elementu powiązania do powiązania.  
  
 Dla scenariuszy zabezpieczeń, które nie zostały spełnione przez powyższe elementy powiązania dwóch, trzech związanych z zabezpieczeniami `abstract` klasy pochodzą z powyższych inicjatora, wykonawca i dostawcy klas bazowych:  
  
1.  <xref:System.ServiceModel.Channels.StreamSecurityUpgradeInitiator?displayProperty=nameWithType>  
  
2.  <xref:System.ServiceModel.Channels.StreamSecurityUpgradeAcceptor?displayProperty=nameWithType>  
  
3.  <xref:System.ServiceModel.Channels.StreamSecurityUpgradeProvider?displayProperty=nameWithType>  
  
 Proces wdrażania uaktualnienia strumienia zabezpieczeń jest taka sama jak wcześniej, z tą różnicą, że będą pochodzić z tych trzech klas. Musi zostać zastąpiona dodatkowe właściwości tych klas, aby podać informacje o zabezpieczeniach do środowiska uruchomieniowego.  
  
## <a name="multiple-upgrades"></a>Kilku uaktualnień  
 Do utworzenia dodatkowych żądań uaktualnienia należy powtórzyć powyżej: Utwórz dodatkowe rozszerzenia <xref:System.ServiceModel.Channels.StreamUpgradeProvider> i elementów wiązania. Dodaj elementy powiązania do powiązania. Dodatkowe elementy są przetwarzane sekwencyjnie, rozpoczynając od pierwszego elementu powiązania dodane do powiązania. W <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> i <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> każdy dostawca uaktualnienia można określić sposób samej warstwy w dowolnym istniejącym uaktualnieniu wiązania parametrów. Należy zastąpić go uaktualniania istniejących wiązanie parametru za pomocą nowego parametru złożone powiązanie uaktualnienia.  
  
 Alternatywnie jednego dostawcę uaktualnienia mogą obsługiwać kilku uaktualnień. Na przykład można zaimplementować dostawcę uaktualnienia niestandardowe strumienia, który obsługuje aktualizacje zabezpieczeń, jak i kompresji. Wykonaj następujące czynności:  
  
1.  Podklasy <xref:System.ServiceModel.Channels.StreamSecurityUpgradeProvider> do zapisywania klasy dostawcy, która tworzy inicjatora i wykonawca.  
  
2.  Podklasy <xref:System.ServiceModel.Channels.StreamSecurityUpgradeInitiator> upewniając się zastąpić <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> metodę, aby zwrócić typy zawartości dla strumienia kompresji i bezpieczne dane ze strumienia, w kolejności.  
  
3.  Podklasy <xref:System.ServiceModel.Channels.StreamSecurityUpgradeAcceptor> rozumie, że niestandardowe typy zawartości w jego <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A> metody.  
  
4.  Strumień zostanie uaktualniony po każdym wywołaniu <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> i <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Channels.StreamUpgradeInitiator>
- <xref:System.ServiceModel.Channels.StreamSecurityUpgradeInitiator>
- <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor>
- <xref:System.ServiceModel.Channels.StreamSecurityUpgradeAcceptor>
- <xref:System.ServiceModel.Channels.StreamUpgradeProvider>
- <xref:System.ServiceModel.Channels.StreamSecurityUpgradeProvider>
- <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
