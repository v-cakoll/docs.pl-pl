---
title: Przechowywanie wersji usługi
ms.date: 03/30/2017
ms.assetid: 37575ead-d820-4a67-8059-da11a2ab48e2
ms.openlocfilehash: 3f9fd87eacf67a1b23568dcf87df086e935879ba
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423683"
---
# <a name="service-versioning"></a>Przechowywanie wersji usługi
Po wdrożeniu wstępnym i potencjalnie kilka razy w okresie istnienia usługi (i punkty końcowe, które ujawniają) mogą wymagać zmiany z różnych powodów, takich jak zmiana potrzeb firmy, wymagania dotyczące technologii informatycznych lub inne rozwiązanie luk. Każda zmiana wprowadza nową wersję usługi. W tym temacie wyjaśniono, jak rozważyć przechowywanie wersji w programie Windows Communication Foundation (WCF).  
  
## <a name="four-categories-of-service-changes"></a>Cztery kategorie zmian usługi  
 Zmiany w usługach, które mogą być wymagane, mogą być klasyfikowane do czterech kategorii:  
  
- Zmiany kontraktu: na przykład może zostać dodana operacja lub element danych w komunikacie może zostać dodany lub zmieniony.  
  
- Zmiany adresów: na przykład usługa przechodzi do innej lokalizacji, gdzie punkty końcowe mają nowe adresy.  
  
- Zmiany powiązań: na przykład zmiana mechanizmu zabezpieczeń lub zmiana jego ustawień.  
  
- Zmiany implementacji: na przykład podczas zmiany wewnętrznej implementacji metody.  
  
 Niektóre z tych zmian są nazywane "uszkodzeniem", a inne to "nieprzerywanie". Zmiana jest *nieprzerwana* , jeśli wszystkie komunikaty, które zostały pomyślnie przetworzone w poprzedniej wersji, zostały pomyślnie przetworzone w nowej wersji. Wszelkie zmiany, które nie spełniają tego kryterium, są istotną *zmianą* .  
  
## <a name="service-orientation-and-versioning"></a>Orientacja i przechowywanie wersji usługi  
 Jedną z założeniaych usług jest to, że usługi i klienci są autonomiczni (lub niezależnie). Oznacza to, że deweloperzy usług nie mogą założyć, że mogą oni kontrolować lub nawet wiedzieć o wszystkich klientach usługi. Eliminuje to możliwość odbudowy i ponownego wdrożenia wszystkich klientów w przypadku zmiany wersji usługi. W tym temacie przyjęto założenie, że usługa jest zgodna z tym cechą i dlatego należy ją zmienić lub "w wersji" niezależnie od jej klientów.  
  
 W przypadkach, gdy istotna zmiana jest nieoczekiwana i nie można jej uniknąć, aplikacja może zrezygnować z tej cechą i wymagać ponownego skompilowania i wdrożenia klientów przy użyciu nowej wersji usługi.  
  
## <a name="contract-versioning"></a>Przechowywanie wersji kontraktu  
 Kontrakty używane przez klienta nie muszą być takie same, jak kontrakt używany przez usługę; muszą one być zgodne.  
  
 W przypadku kontraktów dotyczących usług zgodność oznacza nowe operacje udostępniane przez usługę, ale nie można ich usunąć ani zmienić semantycznie.  
  
 W przypadku kontraktów dotyczących danych zgodność oznacza nowe definicje typów schematów, ale nie można zmienić istniejących definicji typów schematów na różne sposoby. Istotne zmiany mogą obejmować usunięcie elementów członkowskich danych lub zmianę ich typu danych incompatibly. Ta funkcja umożliwia korzystanie z usługi w niektórych systemach Latitude w przypadku zmiany wersji jej umów bez przerywania klientów. W następnych dwóch sekcjach objaśniono nieprzerwane i istotne zmiany, które można wprowadzać w ramach kontraktów dotyczących danych i usług WCF.  
  
## <a name="data-contract-versioning"></a>Przechowywanie wersji kontraktów danych  
 Ta sekcja zajmuje się przechowywaniem wersji danych przy użyciu klas <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Runtime.Serialization.DataContractAttribute>.  
  
### <a name="strict-versioning"></a>Dokładne przechowywanie wersji  
 W wielu scenariuszach, gdy zmiana wersji jest problemem, Deweloper usługi nie ma kontroli nad klientami i w związku z tym nie może tworzyć założeń dotyczących sposobu reagowania na zmiany w kodzie XML lub schemacie wiadomości. W takich przypadkach należy zagwarantować, że nowe wiadomości będą weryfikowane względem starego schematu, z dwóch powodów:  
  
- Stary klient został opracowany z założeniem, że schemat nie ulegnie zmianie. Mogą oni nie przetwarzać komunikatów, które nigdy nie zostały zaprojektowane.  
  
- Stary klient może przeprowadzić rzeczywistą weryfikację schematu względem starego schematu przed próbą przetworzenia komunikatów.  
  
 Zalecanym podejściem w takich scenariuszach jest traktowanie istniejących kontraktów danych jako niezmienne i tworzenie nowych przy użyciu unikatowych kwalifikowanych nazw XML. Deweloper usługi następnie doda nowe metody do istniejącego kontraktu usługi lub utworzy nowy kontrakt usługi z metodami korzystającymi z nowego kontraktu danych.  
  
 Często zdarza się, że deweloper usługi musi napisać pewną logikę biznesową, która powinna być uruchamiana w ramach wszystkich wersji kontraktu danych oraz kodu biznesowego specyficznego dla wersji dla każdej wersji kontraktu danych. Dodatek na końcu tego tematu wyjaśnia, jak interfejsy mogą być używane do zaspokajania tego zapotrzebowania.  
  
### <a name="lax-versioning"></a>Przechowywanie wersji swobodny  
 W wielu innych scenariuszach deweloperzy usług mogą wprowadzić założenie, że dodanie nowego, opcjonalnego elementu członkowskiego do kontraktu danych nie spowoduje przerwania istniejących klientów. Wymaga to, aby deweloper usług mógł zbadać, czy istniejący klienci nie wykonują walidacji schematu i ignorują nieznane elementy członkowskie danych. W tych scenariuszach można korzystać z funkcji kontraktu danych w celu dodawania nowych członków w sposób niepodzielony. Deweloper usługi może wprowadzić to założenie z pewnością, jeśli funkcje kontraktu danych dotyczące wersji zostały już użyte dla pierwszej wersji usługi.  
  
 Usługi WCF, ASP.NET Web Services i wiele innych stosów usługi sieci Web obsługują *przechowywanie wersji swobodny*: oznacza to, że nie generują one wyjątków dla nowych nieznanych elementów członkowskich danych w odebranych danych.  
  
 Jest to łatwe w użyciu, gdyż dodanie nowego elementu członkowskiego nie spowoduje przerwania istniejących klientów. Jeśli nie masz pewności, że wszyscy klienci mogą obsługiwać przechowywanie wersji swobodny, zalecenie polega na użyciu ścisłych wytycznych dotyczących wersji i traktuje Kontrakty danych jako niezmienne.  
  
 Aby uzyskać szczegółowe wytyczne dotyczące swobodny i ścisłej wersji umów dotyczących danych, zobacz [najlepsze rozwiązania: przechowywanie wersji kontraktu danych](best-practices-data-contract-versioning.md).  
  
### <a name="distinguishing-between-data-contract-and-net-types"></a>Rozróżnianie między kontraktem danych i typami .NET  
 Klasy lub struktury platformy .NET mogą być rzutowane jako kontrakt danych przez zastosowanie atrybutu <xref:System.Runtime.Serialization.DataContractAttribute> do klasy. Projekty typu .NET i jego Kontrakty danych są dwa odrębne zagadnienia. Istnieje możliwość, że istnieje wiele typów .NET z tą samą projekcją kontraktu danych. To rozróżnienie jest szczególnie przydatne w przypadku, gdy pozwala na zmianę typu .NET przy zachowaniu prognozowanych kontraktów danych, dzięki czemu zapewnia to zgodność z istniejącymi klientami nawet w ścisłym znaczeniu tego wyrazu. Istnieją dwie rzeczy, które zawsze należy wykonać, aby zachować rozróżnienie między typem .NET i umową dotyczącą danych:  
  
- Określ <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> i <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>. Należy zawsze określić nazwę i przestrzeń nazw kontraktu danych, aby zapobiec ujawnieniu nazwy i przestrzeni nazw typu .NET w kontrakcie. W ten sposób w przypadku późniejszej zmiany przestrzeni nazw lub nazwy typu platformy .NET kontrakt danych pozostaje taki sam.  
  
- Określ <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A>. Należy zawsze określić nazwę członków danych, aby zapobiec ujawnieniu nazwy członka platformy .NET w kontrakcie. W ten sposób w przypadku późniejszej zmiany nazwy platformy .NET elementu członkowskiego kontrakt danych pozostaje taki sam.  
  
### <a name="changing-or-removing-members"></a>Zmiana lub usuwanie członków  
 Zmiana nazwy lub typu danych elementu członkowskiego lub usunięcie elementów członkowskich danych jest istotną zmianą, nawet jeśli dozwolone jest przechowywanie wersji swobodny. Jeśli jest to konieczne, Utwórz nowy kontrakt danych.  
  
 Jeśli zgodność usługi ma wysoką ważność, można rozważyć zignorowanie nieużywanych elementów członkowskich danych w kodzie i pozostawienie ich na miejscu. W przypadku dzielenia elementu członkowskiego danych na wielu członków warto rozważyć opuszczenie istniejącego elementu członkowskiego w miejscu jako właściwość, która może wykonać wymagane dzielenie i ponowne agregowanie dla klientów niższego poziomu (klientów, którzy nie zostali uaktualnioni do najnowszej wersji).  
  
 Podobnie zmiany nazwy lub przestrzeni nazw kontraktu danych są istotne.  
  
### <a name="round-trips-of-unknown-data"></a>Rundy nieznanych danych  
 W niektórych scenariuszach istnieje potrzeba "rundy", które pochodzą z elementów członkowskich dodanych w nowej wersji. Na przykład usługa "versionNew" wysyła dane z nowo dodanych członków do klienta "versionOld". Klient ignoruje nowo dodane elementy członkowskie podczas przetwarzania komunikatu, ale ponownie wysyła te same dane, w tym nowo dodane elementy członkowskie, z powrotem do usługi versionNew. Typowym scenariuszem jest aktualizacja danych, w której dane są pobierane z usługi, zmienione i zwracane.  
  
 Aby włączyć funkcję okrężną dla określonego typu, typ musi implementować interfejs <xref:System.Runtime.Serialization.IExtensibleDataObject>. Interfejs zawiera jedną właściwość, <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> która zwraca typ <xref:System.Runtime.Serialization.ExtensionDataObject>. Właściwość służy do przechowywania danych z przyszłych wersji kontraktu danych, który jest nieznany dla bieżącej wersji. Te dane są nieprzezroczyste dla klienta, ale gdy wystąpienie jest serializowane, zawartość właściwości <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> jest zapisywana z pozostałymi danymi członków kontraktu danych.  
  
 Zaleca się, aby wszystkie typy implementują ten interfejs w celu uwzględnienia nowych i nieznanych przyszłych członków.  
  
### <a name="data-contract-libraries"></a>Biblioteki kontraktu danych  
 Mogą istnieć biblioteki kontraktów danych, w których kontrakt jest publikowany w centralnym repozytorium, a implementacje usług i typów implementują i uwidaczniają Kontrakty danych z tego repozytorium. W takim przypadku po opublikowaniu kontraktu danych w repozytorium nie ma kontroli nad tym, kto tworzy typy implementujące go. W tym celu nie można modyfikować kontraktu po jego opublikowaniu, dlatego renderowanie go efektywnie jest niezmienne.  
  
### <a name="when-using-the-xmlserializer"></a>Przy użyciu elementu XmlSerializer  
 Te same zasady przechowywania wersji są stosowane w przypadku używania klasy <xref:System.Xml.Serialization.XmlSerializer>. Gdy wymagane jest dokładne przechowywanie wersji, Traktuj Kontrakty danych jako niezmienne i Utwórz nowe kontrakty danych z unikatowymi, kwalifikowanymi nazwami dla nowych wersji. Jeśli masz pewność, że można użyć wersji swobodny, możesz dodać nowych możliwych do serializacji członków w nowych wersjach, ale nie zmieniać ani usuwać istniejących członków.  
  
> [!NOTE]
> <xref:System.Xml.Serialization.XmlSerializer> używa atrybutów <xref:System.Xml.Serialization.XmlAnyElementAttribute> i <xref:System.Xml.Serialization.XmlAnyAttributeAttribute> do obsługi rundy nieznanych danych.  
  
## <a name="message-contract-versioning"></a>Przechowywanie wersji kontraktu komunikatów  
 Wskazówki dotyczące przechowywania wersji kontraktu są bardzo podobne do wersji umów dotyczących danych. Jeśli jest wymagana ścisła wersja, nie należy zmieniać treści wiadomości, ale zamiast tego utworzyć nowy kontrakt wiadomości z unikatową kwalifikowaną nazwą. Jeśli wiesz, że możesz użyć wersji swobodny, możesz dodać nowe części treści wiadomości, ale nie zmieniać ani usuwać istniejących. Te wskazówki dotyczą umów dotyczących komunikatów zarówno od zera, jak i opakowanych.  
  
 Nagłówki wiadomości można zawsze dodawać nawet wtedy, gdy jest używana funkcja dokładnej wersji. Flaga MustUnderstand może wpłynąć na przechowywanie wersji. Ogólnie rzecz biorąc, model przechowywania wersji dla nagłówków w programie WCF jest opisany w specyfikacji protokołu SOAP.  
  
## <a name="service-contract-versioning"></a>Przechowywanie wersji kontraktu usług  
 Podobnie jak w przypadku wersji kontraktu danych, wersja kontraktu usług obejmuje także dodawanie, zmienianie i usuwanie operacji.  
  
### <a name="specifying-name-namespace-and-action"></a>Określanie nazwy, przestrzeni nazw i akcji  
 Domyślnie nazwą kontraktu usługi jest nazwa interfejsu. Jego domyślną przestrzenią nazw jest "http://tempuri.org", a każda akcja operacji to "http://tempuri.org/contractname/methodname". Zaleca się jawnie określić nazwę i obszar nazw dla kontraktu usługi oraz akcję dla każdej operacji, aby uniknąć używania "http://tempuri.org" i aby zapobiec ujawnieniu nazw interfejsów i metod w kontrakcie usługi.  
  
### <a name="adding-parameters-and-operations"></a>Dodawanie parametrów i operacji  
 Dodawanie operacji usługi ujawnionych przez usługę to zmiana nieprzerwana, ponieważ istniejący klienci nie muszą być zainteresowani tymi nowymi operacjami.  
  
> [!NOTE]
> Dodawanie operacji do wielostronnego kontraktu wywołania zwrotnego jest istotną zmianą.  
  
### <a name="changing-operation-parameter-or-return-types"></a>Zmienianie parametru operacji lub zwracanych typów  
 Zmienianie parametrów lub typów zwracanych zazwyczaj jest istotną zmianą, chyba że nowy typ implementuje ten sam kontrakt danych zaimplementowany przez stary typ. Aby wprowadzić taką zmianę, Dodaj nową operację do kontraktu usługi lub Zdefiniuj nowy kontrakt usługi.  
  
### <a name="removing-operations"></a>Usuwanie operacji  
 Usuwanie operacji jest również istotną zmianą. Aby wprowadzić taką zmianę, należy zdefiniować nowy kontrakt usługi i udostępnić go w nowym punkcie końcowym.  
  
### <a name="fault-contracts"></a>Kontrakty błędów  
 Atrybut <xref:System.ServiceModel.FaultContractAttribute> umożliwia deweloperowi kontraktu usługi Określanie informacji o błędach, które mogą być zwracane z operacji kontraktu.  
  
 Lista błędów opisanych w kontrakcie usługi nie jest uważana za wyczerpującą. W dowolnym momencie operacja może zwracać błędy, które nie zostały opisane w jego kontrakcie. W związku z tym zmiana zestawu błędów opisanych w kontrakcie nie jest uważana za przerywanie. Na przykład dodanie nowego błędu do kontraktu przy użyciu <xref:System.ServiceModel.FaultContractAttribute> lub usunięcie istniejącego błędu z kontraktu.  
  
### <a name="service-contract-libraries"></a>Biblioteki kontraktu usług  
 Organizacje mogą mieć biblioteki kontraktów, w których kontrakt jest publikowany w centralnym repozytorium i realizatorów usług implementujących umowy z tego repozytorium. W takim przypadku podczas publikowania kontraktu usługi do repozytorium nie ma kontroli nad tym, kto tworzy usługi implementujące ją. W związku z tym nie można modyfikować kontraktu usługi po opublikowaniu, ponieważ nie jest on efektywnie modyfikowany. Program WCF obsługuje dziedziczenie kontraktu, którego można użyć do utworzenia nowego kontraktu, który rozszerza istniejące kontrakty. Aby użyć tej funkcji, Zdefiniuj nowy interfejs kontraktu usługi, który dziedziczy po starym interfejsie kontraktu usługi, a następnie Dodaj metody do nowego interfejsu. Następnie należy zmienić usługę implementującą stary kontrakt w celu zaimplementowania nowego kontraktu i zmienić definicję punktu końcowego "versionOld" w taki sposób, aby korzystała z nowego kontraktu. Na klientach "versionOld" punkt końcowy będzie nadal wyświetlany jako Uwidacznianie kontraktu "versionOld"; na klientach "versionNew" zostanie wyświetlony punkt końcowy, który udostępni kontrakt "versionNew".  
  
## <a name="address-and-binding-versioning"></a>Przechowywanie wersji adresu i powiązania  
 Zmiany adresu i powiązania punktu końcowego są przerywane, chyba że klienci będą mogli dynamicznie odnajdywać nowy adres lub powiązanie punktu końcowego. Jednym z mechanizmów implementowania tej funkcji jest użycie rejestru Universal Discovery Description and Integration (UDDI) i wzorca wywołania usług UDDI, w którym klient próbuje komunikować się z punktem końcowym, a w przypadku niepowodzenia wysyła zapytania do dobrze znanych usług UDDI Rejestr dla bieżących metadanych punktu końcowego. Klient używa następnie adresu i powiązania z tych metadanych do komunikowania się z punktem końcowym. Jeśli ta komunikacja powiedzie się, Klient buforuje adres i informacje o powiązaniu do użytku w przyszłości.  
  
## <a name="routing-service-and-versioning"></a>Usługa routingu i przechowywanie wersji  
 Jeśli zmiany wprowadzone do usługi są istotne i należy mieć co najmniej dwie różne wersje usługi uruchomionej jednocześnie, można użyć usługi routingu WCF do kierowania komunikatów do odpowiedniego wystąpienia usługi. Usługa routingu WCF używa routingu opartego na zawartości, innymi słowy używa informacji w komunikacie, aby określić, gdzie należy skierować komunikat. Aby uzyskać więcej informacji na temat usługi routingu WCF, zobacz [Usługa routingu](./feature-details/routing-service.md). Przykład korzystania z usługi routingu WCF na potrzeby obsługi wersji usługi można znaleźć w temacie [How to: Versioning Service](./feature-details/how-to-service-versioning.md).  
  
## <a name="appendix"></a>Dodatek  
 Ogólne wskazówki dotyczące obsługi wersji kontraktu danych, gdy jest wymagana ścisła wersja, to traktowanie umów danych jako niezmienne i tworzenie nowych, gdy wymagane są zmiany. Należy utworzyć nową klasę dla każdego nowego kontraktu danych, więc mechanizm jest potrzebny, aby uniknąć konieczności podawania istniejącego kodu, który został napisany w rozumieniu starej klasy kontraktu danych i ponownie napisać go pod względem nowej klasy kontraktu danych.  
  
 Jednym z tych mechanizmów jest użycie interfejsów do definiowania elementów członkowskich każdego kontraktu danych i zapis wewnętrzny kod implementacji pod względem interfejsów, a nie klas kontraktów danych, które implementują interfejsy. Poniższy kod dla wersji 1 usługi zawiera interfejs `IPurchaseOrderV1` i `PurchaseOrderV1`:  
  
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
  
 Mimo że operacje kontraktu usługi są zapisywane w warunkach `PurchaseOrderV1`, rzeczywista logika biznesowa miałaby `IPurchaseOrderV1`. Następnie w wersji 2 można uzyskać nowy interfejs `IPurchaseOrderV2` i nową klasę `PurchaseOrderV2`, jak pokazano w poniższym kodzie:  
  
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
  
 Kontrakt usługi zostanie zaktualizowany w taki sposób, aby obejmował nowe operacje, które są zapisywane w odniesieniu do `PurchaseOrderV2`. Istniejąca logika biznesowa zapisywana w `IPurchaseOrderV1` będzie nadal działać dla `PurchaseOrderV2` i nowej logiki biznesowej, która wymaga, aby Właściwość `OrderDate` była zapisywana w zakresie `IPurchaseOrderV2`.  
  
## <a name="see-also"></a>Zobacz także

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
