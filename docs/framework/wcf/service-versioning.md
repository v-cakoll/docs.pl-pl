---
title: Przechowywanie wersji usługi
ms.date: 03/30/2017
ms.assetid: 37575ead-d820-4a67-8059-da11a2ab48e2
ms.openlocfilehash: ea5e80e33d1b29e01e6d1867c50bb3bb973b01c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183120"
---
# <a name="service-versioning"></a>Przechowywanie wersji usługi
Po pierwszym wdrożeniu i potencjalnie kilka razy w okresie ich istnienia usługi (i punkty końcowe, które ujawniają) mogą wymagać zmiany z różnych powodów, takich jak zmieniające się potrzeby biznesowe, wymagania dotyczące technologii informatycznych lub w celu rozwiązania innych Problemy. Każda zmiana wprowadza nową wersję usługi. W tym temacie wyjaśniono, jak rozważyć przechowywanie wersji w programie Windows Communication Foundation (WCF).  
  
## <a name="four-categories-of-service-changes"></a>Cztery kategorie zmian w usłudze  
 Zmiany w usługach, które mogą być wymagane, można podzielić na cztery kategorie:  
  
- Zmiany umowy: Na przykład operacja może zostać dodana lub element danych w wiadomości może zostać dodany lub zmieniony.  
  
- Zmiany adresów: Na przykład usługa przenosi się do innej lokalizacji, w której punkty końcowe mają nowe adresy.  
  
- Zmiany wiązania: Na przykład zmiany mechanizmu zabezpieczeń lub jego zmiany ustawień.  
  
- Zmiany implementacji: Na przykład, gdy zmienia się implementacja metody wewnętrznej.  
  
 Niektóre z tych zmian są nazywane "łamaniem", a inne są "nieprzełamające". Zmiana jest *nierozdzielająca,* jeśli wszystkie wiadomości, które zostały pomyślnie przetworzone w poprzedniej wersji, są przetwarzane pomyślnie w nowej wersji. Każda zmiana, która nie spełnia tego kryterium, jest *przełomową* zmianą.  
  
## <a name="service-orientation-and-versioning"></a>Orientacja i przechowywanie wersji usług  
 Jednym z założeń orientacji usług jest to, że usługi i klienci są autonomiczne (lub niezależne). Między innymi oznacza to, że deweloperzy usług nie mogą zakładać, że kontrolują lub nawet wiedzą o wszystkich klientach usług. Eliminuje to możliwość przebudowywania i ponownego rozmieszczania wszystkich klientów, gdy usługa zmienia wersje. W tym temacie przyjęto założenie, że usługa jest zgodna z tym tenetem i dlatego musi zostać zmieniona lub "wersjona" niezależnie od swoich klientów.  
  
 W przypadkach, gdy zmiana podziału jest nieoczekiwane i nie można uniknąć, aplikacja może zignorować tenet i wymagają, aby klienci zostać przebudowany i ponownie wdrożyć z nową wersją usługi.  
  
## <a name="contract-versioning"></a>Przechowywanie wersji kontraktu  
 Umowy używane przez klienta nie muszą być takie same jak umowa używana przez usługę; muszą być kompatybilne.  
  
 W przypadku umów serwisowych zgodność oznacza, że można dodać nowe operacje udostępniane przez usługę, ale nie można usunąć ani zmienić istniejących operacji semantycznie.  
  
 W przypadku kontraktów na dane zgodność oznacza, że można dodać nowe definicje typów schematów, ale istniejących definicji typów schematów nie można zmienić w sposób przerywany. Wprowadzanie zmian może obejmować usunięcie elementów członkowskich danych lub nieprzeszkadnie zmieniając ich typ danych. Ta funkcja umożliwia usługi pewną swobodę w zmianie wersji swoich umów bez przerywania klientów. Następne dwie sekcje wyjaśniają zmiany nierozdzielające i przerywające, które można ww przypadku danych WCF i umów serwisowych.  
  
## <a name="data-contract-versioning"></a>Przechowywanie wersji kontraktów danych  
 Ta sekcja dotyczy przechowywania wersji <xref:System.Runtime.Serialization.DataContractSerializer> danych <xref:System.Runtime.Serialization.DataContractAttribute> podczas korzystania z i klas.  
  
### <a name="strict-versioning"></a>Ścisłe przechowywanie wersji  
 W wielu scenariuszach, gdy zmiana wersji jest problemem, deweloper usługi nie ma kontroli nad klientami i dlatego nie może wprowadzać założeń dotyczących sposobu reagowania na zmiany w wiadomości XML lub schemacie. W takich przypadkach należy zagwarantować, że nowe komunikaty będą sprawdzać poprawność względem starego schematu, z dwóch powodów:  
  
- Stare klienty zostały opracowane przy założeniu, że schemat nie ulegnie zmianie. Mogą nie przetwarzać wiadomości, dla których nigdy nie zostały zaprojektowane.  
  
- Starzy klienci mogą wykonywać sprawdzanie poprawności rzeczywistego schematu względem starego schematu, zanim jeszcze spróbują przetworzyć wiadomości.  
  
 Zalecane podejście w takich scenariuszach jest traktowanie istniejących kontraktów danych jako niezmienne i tworzenie nowych z unikatowymi nazwami kwalifikowanymi XML. Deweloper usługi następnie dodać nowe metody do istniejącego umowy serwisowej lub utworzyć nowy kontrakt serwisowy z metod, które używają nowego kontraktu danych.  
  
 Często będzie tak, że deweloper usługi musi napisać logikę biznesową, która powinna być uruchamiana we wszystkich wersjach umowy danych oraz kodu biznesowego specyficznego dla wersji dla każdej wersji kontraktu danych. Dodatek na końcu tego tematu wyjaśnia, jak interfejsy mogą być używane do zaspokojenia tej potrzeby.  
  
### <a name="lax-versioning"></a>Lax Versioning  
 W wielu innych scenariuszach deweloper usługi można przyjąć założenie, że dodanie nowego, opcjonalnego elementu członkowskiego do umowy danych nie spowoduje przerwania istniejących klientów. Wymaga to od dewelopera usługi zbadania, czy istniejący klienci nie wykonują sprawdzania poprawności schematu i że ignorują nieznanych elementów członkowskich danych. W tych scenariuszach jest możliwe, aby skorzystać z funkcji kontraktu danych do dodawania nowych członków w sposób nierozdzielający. Deweloper usługi można dokonać tego założenia z ufnością, jeśli funkcje umowy danych dla przechowywania wersji były już używane dla pierwszej wersji usługi.  
  
 WCF, ASP.NET Web Services i wiele innych stosów usług sieci Web obsługuje *lax versioning:* oznacza to, że nie zgłaszają wyjątków dla nowych nieznanych elementów członkowskich danych w odebranych danych.  
  
 Łatwo jest błędnie uwierzyć, że dodanie nowego członka nie spowoduje złamania istniejących klientów. Jeśli nie masz pewności, że wszyscy klienci mogą obsługiwać luźne przechowywanie wersji, zaleca się użycie ścisłych wytycznych dotyczących przechowywania wersji i traktowanie kontraktów danych jako niezmiennych.  
  
 Aby uzyskać szczegółowe wskazówki dotyczące zarówno luźnego, jak i ścisłego przechowywania wersji kontraktów danych, zobacz [Najważniejsze rozwiązania: Przechowywanie wersji kontraktu danych.](best-practices-data-contract-versioning.md)  
  
### <a name="distinguishing-between-data-contract-and-net-types"></a>Rozróżnianie między typami data i .NET  
 Klasa lub struktura .NET mogą być rzutowane jako <xref:System.Runtime.Serialization.DataContractAttribute> kontrakt danych, stosując atrybut do klasy. Typ .NET i jego prognozy kontraktu danych są dwie różne sprawy. Istnieje możliwość wielu typów .NET z tej samej projekcji kontraktu danych. To rozróżnienie jest szczególnie przydatne w umożliwia zmianę typu .NET przy zachowaniu przewidywanej umowy danych, utrzymując w ten sposób zgodność z istniejącymi klientami, nawet w ścisłym znaczeniu tego słowa. Istnieją dwie rzeczy, które należy zawsze zrobić, aby zachować to rozróżnienie między typem .NET a kontraktem na dane:  
  
- Określ <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>a i . Zawsze należy określić nazwę i obszar nazw umowy danych, aby zapobiec narazić nazwę typu .NET i obszar nazw w umowie. W ten sposób, jeśli zdecydujesz się później zmienić obszar nazw .NET lub nazwę typu, umowa danych pozostaje taka sama.  
  
- Podaj wartość <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A>. Zawsze należy określić nazwę elementów członkowskich danych, aby zapobiec ujawnieniu nazwy elementu członkowskiego platformy .NET w umowie. W ten sposób, jeśli zdecydujesz się później zmienić nazwę .NET elementu członkowskiego, umowa danych pozostaje taka sama.  
  
### <a name="changing-or-removing-members"></a>Zmiana lub usunięcie członków  
 Zmiana nazwy lub typu danych członka lub usunięcie elementów członkowskich danych jest przełomową zmianą, nawet jeśli dozwolone jest przechowywanie wersji lax. Jeśli jest to konieczne, należy utworzyć nową umowę danych.  
  
 Jeśli zgodność usługi ma duże znaczenie, można rozważyć ignorowanie nieużywanych elementów członkowskich danych w kodzie i pozostawić je na swoim miejscu. Jeśli dzielisz element członkowski danych na wielu członków, można rozważyć pozostawienie istniejącego elementu członkowskiego w miejscu jako właściwość, która może wykonać wymagane dzielenie i ponowne agregowanie dla klientów poziomu w dół (klientów, które nie są uaktualniane do najnowszej wersji).  
  
 Podobnie zmiany nazwy kontraktu danych lub obszaru nazw są przełomowe zmiany.  
  
### <a name="round-trips-of-unknown-data"></a>Podróże w obie strony nieznanych danych  
 W niektórych scenariuszach istnieje potrzeba "round-trip" nieznane dane, które pochodzą od członków dodanych w nowej wersji. Na przykład usługa "versionNew" wysyła dane z niektórymi nowo dodanymi członkami do klienta "versionOld". Klient ignoruje nowo dodanych elementów członkowskich podczas przetwarzania wiadomości, ale ponownie wysyła te same dane, w tym nowo dodanych członków, z powrotem do versionNew usługi. Typowym scenariuszem jest aktualizacje danych, gdzie dane są pobierane z usługi, zmienione i zwrócone.  
  
 Aby włączyć potknięcia zaokrąglone dla <xref:System.Runtime.Serialization.IExtensibleDataObject> określonego typu, typ musi implementować interfejs. Interfejs zawiera jedną <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> właściwość, <xref:System.Runtime.Serialization.ExtensionDataObject> która zwraca typ. Właściwość jest używana do przechowywania wszelkich danych z przyszłych wersji kontraktu danych, który jest nieznany do bieżącej wersji. Te dane są nieprzezroczyste dla klienta, ale gdy <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> wystąpienie jest serializowane, zawartość właściwości jest zapisywana z pozostałymi danymi członków umowy danych.  
  
 Zaleca się, że wszystkie typy implementują ten interfejs, aby pomieścić nowych i nieznanych przyszłych członków.  
  
### <a name="data-contract-libraries"></a>Biblioteki kontraktów danych  
 Mogą istnieć biblioteki kontraktów danych, w których umowa jest publikowana w centralnym repozytorium, a realizatorzy usług i typów implementują i udostępniają kontrakty danych z tego repozytorium. W takim przypadku podczas publikowania umowy danych do repozytorium, nie masz kontroli nad tym, kto tworzy typy, które go implementują. W związku z tym nie można zmodyfikować umowy po jego opublikowaniu, czyniąc go skutecznie niezmienne.  
  
### <a name="when-using-the-xmlserializer"></a>Podczas korzystania z XmlSerializer  
 Te same zasady przechowywania wersji <xref:System.Xml.Serialization.XmlSerializer> mają zastosowanie podczas korzystania z klasy. Gdy wymagane jest ścisłe przechowywanie wersji, traktuj kontrakty danych jako niezmienne i twórz nowe kontrakty danych z unikatowymi, kwalifikowanymi nazwami dla nowych wersji. Jeśli masz pewność, że lax versioning mogą być używane, można dodać nowe elementy członkowskie serializable w nowych wersjach, ale nie zmieniać lub usuwać istniejących elementów członkowskich.  
  
> [!NOTE]
> Używa <xref:System.Xml.Serialization.XmlSerializer> <xref:System.Xml.Serialization.XmlAnyElementAttribute> i <xref:System.Xml.Serialization.XmlAnyAttributeAttribute> atrybuty do obsługi zaokrąglania potknięcia nieznanych danych.  
  
## <a name="message-contract-versioning"></a>Przechowywanie wersji kontraktu z wiadomościami  
 Wskazówki dotyczące przechowywania wersji kontraktu wiadomości są bardzo podobne do kontraktów danych przechowywania wersji. Jeśli wymagane jest ścisłe przechowywanie wersji, nie należy zmieniać treści wiadomości, ale zamiast tego utworzyć nowy kontrakt wiadomości o unikatowej nazwie kwalifikowanej. Jeśli wiesz, że możesz użyć wersji lax, możesz dodać nowe części treści wiadomości, ale nie zmieniać ani usuwać istniejących. Niniejsze wskazówki dotyczą zarówno kontraktów na gołe, jak i opakowane wiadomości.  
  
 Nagłówki wiadomości zawsze można dodać, nawet jeśli jest używana ścisła wersja. MustUnderstand flaga może mieć wpływ na przechowywanie wersji. Ogólnie rzecz biorąc model przechowywania wersji dla nagłówków w WCF jest opisany w specyfikacji PROTOKOŁU SOAP.  
  
## <a name="service-contract-versioning"></a>Przechowywanie wersji umowy serwisowej  
 Podobnie jak w wersji umowy danych, przechowywanie wersji umowy serwisowej obejmuje również dodawanie, zmienianie i usuwanie operacji.  
  
### <a name="specifying-name-namespace-and-action"></a>Określanie nazwy, obszaru nazw i akcji  
 Domyślnie nazwa umowy serwisowej jest nazwą interfejsu. Jego domyślna przestrzeńhttp://tempuri.orgnazw to " ",http://tempuri.org/contractname/methodnamea akcja każdej operacji to " ". Zaleca się jawnie określić nazwę i obszar nazw dla umowy serwisowej ihttp://tempuri.orgakcji dla każdej operacji, aby uniknąć używania " " i zapobiec nazwy interfejsu i metody są widoczne w umowie usługi.  
  
### <a name="adding-parameters-and-operations"></a>Dodawanie parametrów i operacji  
 Dodawanie operacji usługi udostępniane przez usługę jest zmiana nierozdzielająca, ponieważ istniejących klientów nie muszą być zaniepokojeni tych nowych operacji.  
  
> [!NOTE]
> Dodawanie operacji do umowy wywołania zwrotnego dupleksu jest przełomową zmianą.  
  
### <a name="changing-operation-parameter-or-return-types"></a>Zmiana parametru operacji lub typów zwracania  
 Zmiana parametru lub zwraca typy zazwyczaj jest zmiana podziału, chyba że nowy typ implementuje ten sam kontrakt danych zaimplementowane przez starego typu. Aby wprowadzić taką zmianę, należy dodać nową operację do umowy serwisowej lub zdefiniować nową umowę serwisową.  
  
### <a name="removing-operations"></a>Usuwanie operacji  
 Usuwanie operacji jest również przełomową zmianą. Aby wprowadzić taką zmianę, należy zdefiniować nowy kontrakt serwisowy i udostępnić go w nowym punkcie końcowym.  
  
### <a name="fault-contracts"></a>Kontrakty na usterki  
 Atrybut <xref:System.ServiceModel.FaultContractAttribute> umożliwia deweloperowi umowy serwisowej określić informacje o błędach, które mogą być zwracane z operacji kontraktu.  
  
 Lista usterek opisanych w umowie o świadczenie usług nie jest uważana za wyczerpującą. W dowolnym momencie operacja może zwrócić usterki, które nie są opisane w umowie. W związku z tym zmiana zestawu usterek opisanych w umowie nie jest uważana za złamanie. Na przykład dodanie nowego błędu do <xref:System.ServiceModel.FaultContractAttribute> umowy przy użyciu lub usunięcie istniejącego błędu z umowy.  
  
### <a name="service-contract-libraries"></a>Biblioteki umów serwisowych  
 Organizacje mogą mieć biblioteki umów, w których umowa jest publikowana w centralnym repozytorium i realizatorów usług implementacji umów z tego repozytorium. W takim przypadku podczas publikowania umowy serwisowej do repozytorium nie masz kontroli nad tym, kto tworzy usługi, które go implementują. W związku z tym nie można zmodyfikować umowy serwisowej raz opublikowane, czyniąc go skutecznie niezmienne. WCF obsługuje dziedziczenie umowy, które mogą służyć do tworzenia nowego kontraktu, który rozszerza istniejące kontrakty. Aby użyć tej funkcji, należy zdefiniować nowy interfejs umowy serwisowej, który dziedziczy ze starego interfejsu umowy serwisowej, a następnie dodaj metody do nowego interfejsu. Następnie należy zmienić usługę, która implementuje stary kontrakt do zaimplementowania nowego kontraktu i zmienić "versionOld" definicji punktu końcowego, aby użyć nowego kontraktu. Do "versionOld" klientów, punkt końcowy będzie nadal pojawiać się jako uwidacznianie "versionOld" umowy; do "versionNew" klientów, punkt końcowy pojawi się uwidaczniać "versionNew" umowy.  
  
## <a name="address-and-binding-versioning"></a>Przechowywanie wersji adresów i wiązań  
 Zmiany adresu punktu końcowego i powiązania są przerywanie zmian, chyba że klienci są w stanie dynamicznie odnajdywania nowego adresu punktu końcowego lub powiązania. Jednym z mechanizmów implementowania tej funkcji jest użycie rejestru universal discovery description and integration (UDDI) i wzorca wywołania UDDI, w którym klient próbuje komunikować się z punktem końcowym i po niepowodzeniu wysyła kwerendy do dobrze znanego UDDI rejestru dla bieżących metadanych punktu końcowego. Klient następnie używa adresu i powiązania z tych metadanych do komunikowania się z punktem końcowym. Jeśli ta komunikacja powiedzie się, klient buforuje adres i informacje o powiązaniach do wykorzystania w przyszłości.  
  
## <a name="routing-service-and-versioning"></a>Usługa routingu i przechowywanie wersji  
 Jeśli zmiany wprowadzone w usłudze są przerywane zmiany i trzeba mieć dwie lub więcej różnych wersji usługi uruchomionej jednocześnie można użyć WCF routingu usługi do kierowania wiadomości do wystąpienia usługi odpowiednie. Usługa routingu WCF używa routingu opartego na zawartości, innymi słowy używa informacji w wiadomości, aby określić, gdzie chcesz rozsyłać wiadomość. Aby uzyskać więcej informacji na temat usługi routingu WCF, zobacz [Usługa routingu](./feature-details/routing-service.md). Na przykład, jak używać usługi routingu WCF do przechowywania wersji usługi, zobacz [Jak: Przechowywanie wersji usługi](./feature-details/how-to-service-versioning.md).  
  
## <a name="appendix"></a>Dodatek  
 Ogólne wskazówki dotyczące przechowywania wersji umowy danych, gdy wymagane jest ścisłe przechowywanie wersji, jest traktowanie kontraktów danych jako niezmiennych i tworzenie nowych, gdy wymagane są zmiany. Nowa klasa musi zostać utworzona dla każdej nowej umowy danych, więc mechanizm jest potrzebny, aby uniknąć konieczności podjęcia istniejącego kodu, który został napisany w kategoriach starej klasy kontraktu danych i przepisać go pod względem nowej klasy kontraktu danych.  
  
 Jednym z takich mechanizmów jest użycie interfejsów do definiowania elementów członkowskich każdej umowy danych i pisania wewnętrznego kodu implementacji pod względem interfejsów, a nie klas kontraktów danych, które implementują interfejsy. Poniższy kod dla wersji 1 `IPurchaseOrderV1` usługi pokazuje `PurchaseOrderV1`interfejs i:  
  
```csharp  
public interface IPurchaseOrderV1  
{  
    string OrderId { get; set; }  
    string CustomerId { get; set; }  
}  
  
[DataContract(  
Name = "PurchaseOrder",  
Namespace = "http://examples.microsoft.com/WCF/2005/10/PurchaseOrder")]  
public class PurchaseOrderV1 : IPurchaseOrderV1  
{  
    [DataMember(...)]  
    public string OrderId {...}  
    [DataMember(...)]  
    public string CustomerId {...}  
}  
```  
  
 Podczas gdy działalność umowy o świadczenie usług `PurchaseOrderV1`byłaby napisana w kategoriach, rzeczywista logika biznesowa byłaby pod względem `IPurchaseOrderV1`. Następnie w wersji 2 będzie nowy `IPurchaseOrderV2` interfejs i `PurchaseOrderV2` nowa klasa, jak pokazano w poniższym kodzie:  
  
```csharp
public interface IPurchaseOrderV2  
{  
    DateTime OrderDate { get; set; }  
}

[DataContract(
Name = "PurchaseOrder",  
Namespace = "http://examples.microsoft.com/WCF/2006/02/PurchaseOrder")]  
public class PurchaseOrderV2 : IPurchaseOrderV1, IPurchaseOrderV2  
{  
    [DataMember(...)]  
    public string OrderId {...}  
    [DataMember(...)]  
    public string CustomerId {...}  
    [DataMember(...)]  
    public DateTime OrderDate { ... }  
}  
```  
  
 Umowa serwisowa zostanie zaktualizowana w celu uwzględnienia nowych `PurchaseOrderV2`operacji, które są napisane w kategoriach . Istniejąca logika biznesowa `IPurchaseOrderV1` napisana w `PurchaseOrderV2` kategoriach będzie nadal `OrderDate` działać i nowa logika biznesowa, która potrzebuje nieruchomości, zostanie napisana w kategoriach `IPurchaseOrderV2`.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A>
- <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>
- <xref:System.Runtime.Serialization.IExtensibleDataObject>
- <xref:System.Runtime.Serialization.ExtensionDataObject>
- <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A>
- <xref:System.Xml.Serialization.XmlSerializer>
- [Równoważność kontraktów danych](./feature-details/data-contract-equivalence.md)
- [Wywołania zwrotne serializacji z tolerancją dla wersji](./feature-details/version-tolerant-serialization-callbacks.md)
