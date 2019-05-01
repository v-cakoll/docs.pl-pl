---
title: Przechowywanie wersji usługi
ms.date: 03/30/2017
ms.assetid: 37575ead-d820-4a67-8059-da11a2ab48e2
ms.openlocfilehash: 27d54cdf6f49bd9433f43290c97706af81d98b6b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949789"
---
# <a name="service-versioning"></a>Przechowywanie wersji usługi
Po początkowym wdrożeniu i potencjalnie kilka razy w okresie ich istnienia usługi (i punktów końcowych, które udostępniają) może być konieczne zostanie zmieniony z różnych powodów, takich jak zmieniających się potrzeb biznesowych, wymagań dotyczących technologii informacji, lub inne rozwiązania problemy. Każda zmiana wprowadza nową wersję usługi. W tym temacie wyjaśniono, jak należy wziąć pod uwagę przechowywanie wersji w Windows Communication Foundation (WCF).  
  
## <a name="four-categories-of-service-changes"></a>Cztery kategorie zmianami w usłudze  
 Zmiany usług, które mogą być wymagane, można podzielić na cztery kategorie:  
  
- Zmiany umowy: Na przykład operacji, które mogą być dodawane lub element danych w komunikacie może być dodane lub zmienione.  
  
- Zmian adresów: Na przykład usługa zostaje przeniesiony do innej lokalizacji, gdzie punkty końcowe mają nowe adresy.  
  
- Powiązanie zmiany: Na przykład zmienia mechanizmu zabezpieczeń lub zmienić jego ustawienia.  
  
- Zmiany w implementacji: Na przykład, gdy implementację metody wewnętrznego zmiany.  
  
 Niektóre z tych zmian są nazywane "złamanie", a inne są "nierozdzielające." Zmiana jest *nierozdzielający* Jeśli wszystkie komunikaty, które mogłyby zostały przetworzone pomyślnie w poprzedniej wersji pomyślnie przetworzonych w nowej wersji. Każda zmiana, który nie spełnia warunku jest *istotne* zmiany.  
  
## <a name="service-orientation-and-versioning"></a>Orientacja usługi i przechowywania wersji  
 Jedną z założenia orientacji usługi to usług i klientów autonomicznego (lub niezależnych). Między innymi oznacza to, że deweloperzy usług nie można zakładać, kontrolowania lub nawet wiedzieć o wszystkich klientów usługi. Pozwala to wyeliminować możliwość ponownego kompilowania lub wdrażania wszystkich klientów w przypadku wersji zmiany usługi. W tym temacie przyjęto założenie, usługa działa zgodnie z tym główną i dlatego musi być zmienione lub "kontrolą wersji", niezależnie od swoich klientów.  
  
 W przypadkach, gdy jest nieoczekiwany i nie można uniknąć istotnej zmiany mogą wybrać aplikację Ignoruj ten główną i wymagają, aby klienci można odbudować i ponownego wdrożenia nowej wersji usługi.  
  
## <a name="contract-versioning"></a>Przechowywanie wersji kontraktów  
 Kontrakty używany przez klienta musi być taka sama jak kontraktu używanego przez usługę; tylko muszą być zgodne.  
  
 Dla kontraktów usług zgodności można dodawać nowe operacje oznacza, że udostępniane przez usługę, ale istniejące operacje nie może być usunięte lub zmienione semantycznie.  
  
 W przypadku kontraktów danych zgodność oznacza nowego typu schematu, który można dodać definicji, ale w istotne sposoby nie można zmienić istniejące definicje typu schematu. Istotne zmiany może obejmować usunięcie elementów członkowskich danych lub incompatibly zmianie jego typu danych. Ta funkcja umożliwia usłudze niektóre latitude podczas zmieniania wersji swoich umów bez przerywania klientów. W dwóch następnych sekcjach opisano nieprzerywającymi działania aplikacji i istotne zmiany, które może przyjąć dane usług WCF i umowy o świadczenie usług.  
  
## <a name="data-contract-versioning"></a>Przechowywanie wersji kontraktów danych  
 W tej sekcji omówiono zarządzanie wersjami danych, korzystając z <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Runtime.Serialization.DataContractAttribute> klasy.  
  
### <a name="strict-versioning"></a>Przechowywanie wersji Strict  
 W wielu scenariuszach podczas zmiany wersji jest to problem dla deweloperów usługi ma kontrolę nad klientów i w związku z tym nie może wprowadzać założeń dotyczących jak będzie reagować na zmiany w komunikacie lub schemat XML. W takich przypadkach musisz gwarantować, że nowe wiadomości zostanie przeprowadzona Weryfikacja względem schematu stare dwóch powodów:  
  
- Starych klientów opracowano przy założeniu, że schemat nie ulegnie zmianie. One może zakończyć się niepowodzeniem do przetwarzania komunikatów, które nigdy nie zostały zaprojektowane dla.  
  
- Stary klientów mogą wykonać sprawdzanie poprawności schematu rzeczywiste względem schematu stare przed próbą nawet przetwarzania komunikatów.  
  
 W takich scenariuszach zaleca traktować istniejących kontraktów danych jako niezmienialny i tworzenie nowych, unikatowych XML kwalifikowane nazwy. Deweloper usługi będzie następnie dodać nowych metod do istniejącej umowy serwisowej lub tworzenie nowego kontraktu usługi przy użyciu metody, które używają nowego kontraktu danych.  
  
 Często będzie przypadek, który deweloper usługi musi zapisać niektóre logiki biznesowej, które należy uruchomić we wszystkich wersjach kontraktu danych oraz kod specyficzny dla wersji business dla każdej wersji kontraktu danych. Dodatku na końcu tego tematu opisano, jak interfejsów można spełnić te wymagania.  
  
### <a name="lax-versioning"></a>Przechowywanie wersji łagodnymi  
 W wielu inne scenariusze dla deweloperów usługi można zapewnić przy założeniu, że dodawanie elementu członkowskiego nowy, opcjonalny kontraktu danych nie spowoduje uszkodzenie istniejących klientów. Wymaga to deweloper usługi zbadać, czy istniejący klienci nie wykonuje sprawdzanie poprawności schematu i że Ignoruj ich elementy członkowskie danych nieznany. W tych scenariuszach jest to możliwe, należy korzystać z funkcji kontraktu danych do dodawania nowych elementów członkowskich w sposób nieprzerywającymi działania aplikacji. Dla deweloperów usługi ułatwia to założenie bez obaw, jeśli funkcje kontraktu danych pod kątem przechowywania wersji zostały już użyte w pierwszej wersji usługi.  
  
 Usługi WCF, usług sieci Web ASP.NET i wiele innych sieci Web usługi pomocy technicznej stosy *łagodnymi versioning*: oznacza to, mogą nie zgłaszać wyjątków dla nowych członków nieznany danych odebranych danych.  
  
 To proste przez pomyłkę podejrzewać, że dodawanie nowego elementu członkowskiego nie będę powodować istniejących klientów. Jeśli nie wiesz, że wszyscy klienci mogą obsługiwać łagodnymi przechowywania wersji, zaleca się użyć wskazówki wersji strict i traktować dane umów jako niezmienialny.  
  
 Aby uzyskać szczegółowe wskazówki dotyczące łagodnymi i ograniczeniami przechowywanie wersji kontraktów danych, zobacz [najlepsze rozwiązania: Przechowywanie wersji kontraktów danych](../../../docs/framework/wcf/best-practices-data-contract-versioning.md).  
  
### <a name="distinguishing-between-data-contract-and-net-types"></a>Rozróżniania kontraktu danych i typów .NET  
 .NET klasy lub struktury może być przekazywany jako kontraktu danych, stosując <xref:System.Runtime.Serialization.DataContractAttribute> do klasy atrybutu. Typ architektury .NET i jej prognozy kontraktu danych to dwa odrębne jest ważna. Istnieje możliwość mają różne typy .NET o tej samej projekcji kontraktu danych. Różnica ta jest szczególnie przydatna w umożliwia zmianę typu .NET, przy zachowaniu umowy prognozowanych danych, w tym samym zachowuje zgodność z istniejącymi klientami, nawet w sensie ograniczeniami Word. Istnieją dwie rzeczy, które należy zawsze zachować wykonywania tego rozróżnienia między kontraktu danych i typ .NET:  
  
- Określ <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> i <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>. Należy zawsze podać nazwę i przestrzeń nazw usługi kontraktu danych, aby zapobiec nazwę danego typu .NET i przestrzeni nazw przed przypadkowym w kontrakcie. Dzięki temu, jeśli później zdecydujesz się zmienić z obszaru nazw .NET lub wpisz nazwę, kontrakt usługi danych pozostaje taki sam.  
  
- Określ <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A>. Należy zawsze podać nazwę usługi składowych danych, aby uniemożliwić spowodują ujawnienie w kontrakcie nazwę użytkownika platformy .NET. Dzięki temu, jeśli później zdecydujesz się zmienić nazwę elementu członkowskiego .NET, usługi kontraktu danych pozostaje taki sam.  
  
### <a name="changing-or-removing-members"></a>Zmienianie lub usuwanie członków  
 Zmienianie nazwy lub typu danych elementu członkowskiego lub usuwanie elementów członkowskich danych jest istotną zmianę, nawet wtedy, gdy łagodnymi versioning jest dozwolone. Jeśli jest to konieczne, należy utworzyć nowego kontraktu danych.  
  
 W przypadku zgodności usługi o wysokiej ważności, może wziąć pod uwagę ignorowanie nieużywanych danych członków w kodzie i pozostawić bez zmian. Jeśli są dzielenie element członkowski danych do wielu członków, można rozważyć opuszczania istniejącego elementu członkowskiego w miejscu jako właściwość może wykonać wymagane rozdzielenie i ponowne agregacji w przypadku klientów niskiego poziomu (liczba klientów, które nie zostały uaktualnione do najnowszej wersji).  
  
 Podobnie zmiany nazwy lub przestrzeni nazw kontraktu danych są istotne zmiany.  
  
### <a name="round-trips-of-unknown-data"></a>Rund nieznane dane  
 W niektórych scenariuszach istnieje potrzeba "obustronne" Nieznany dane pochodzące z danych elementy członkowskie dodane w nowej wersji. Na przykład "versionNew" usługa wysyła dane za pomocą niektórych nowo dodane elementy członkowskie do klienta "versionOld". Klient ignoruje nowo dodanych elementów członkowskich, podczas przetwarzania komunikatu, ale umożliwia ponowne wysłanie tych samych danych, w tym nowo dodanych elementów członkowskich, wróć do usługi versionNew. Typowy scenariusz, w tym jest aktualizacji danych, gdzie dane są pobierane z usługi, zmienione i zwrócony.  
  
 Aby włączyć Pełna zgodnooć wersji dla określonego typu, musi implementować typ <xref:System.Runtime.Serialization.IExtensibleDataObject> interfejsu. Interfejs zawiera jedną właściwość <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> zwracającego <xref:System.Runtime.Serialization.ExtensionDataObject> typu. Właściwość jest używana do przechowywania wszelkich danych z przyszłych wersji kontraktu danych, który jest nieznany do bieżącej wersji. Dane te są nieprzezroczyste dla klienta, ale w przypadku wystąpienia jest serializowana, zawartość <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> właściwości są zapisywane z użyciem usług rest danych kontraktu składowych danych.  
  
 Zalecane jest, czy wszystkich typów implementować ten interfejs w celu uwzględnienia nowych i nieznany przyszłych członków.  
  
### <a name="data-contract-libraries"></a>Biblioteki kontraktu danych  
 Może to być bibliotek kontraktów danych, gdy kontrakt jest opublikowana w centralnym repozytorium i konsultantów usługi i typ wdrożenia i udostępnić kontraktów danych z tego repozytorium. W takim przypadku gdy opublikujesz umowy dotyczącej danych do repozytorium masz żadnej kontroli nad tym kto tworzy typy, które ją implementują. W związku z tym, nie można zmodyfikować umowy po opublikowaniu, renderowanie na efektywne niezmienne.  
  
### <a name="when-using-the-xmlserializer"></a>Przy użyciu elementu XmlSerializer  
 Te same zasady przechowywania wersji stosowane podczas korzystania z <xref:System.Xml.Serialization.XmlSerializer> klasy. Gdy wymagana jest ścisłym przechowywania wersji, Traktuj kontraktów danych jako niezmienialny i tworzenie nowych kontraktów danych przy użyciu nazwy kwalifikowanej, unikatową nowych wersji. Gdy masz pewność, że łagodnymi przechowywanie wersji może służyć, mogą dodawać nowych członków do serializacji w nowych wersji, ale nie zmieniać lub Usuń istniejących elementów członkowskich.  
  
> [!NOTE]
>  <xref:System.Xml.Serialization.XmlSerializer> Używa <xref:System.Xml.Serialization.XmlAnyElementAttribute> i <xref:System.Xml.Serialization.XmlAnyAttributeAttribute> atrybuty do obsługi Pełna zgodnooć wersji nieznany danych.  
  
## <a name="message-contract-versioning"></a>Przechowywanie wersji kontraktów komunikatu  
 Wytyczne dotyczące przechowywanie wersji kontraktów komunikatu są bardzo podobne do przechowywanie wersji kontraktów danych. Jeśli wymagana jest ścisłym przechowywania wersji, należy nie zmienić Twoje treści wiadomości, ale zamiast tego utworzyć nowego kontraktu komunikatu, unikatową nazwą kwalifikowaną. Jeśli znasz służy łagodnymi przechowywania wersji, możesz dodać nowe części treści wiadomości, ale nie zmienić lub usunąć istniejące. Te wskazówki dotyczą zarówno na komputerze i opakowane kontrakty komunikatów.  
  
 Zawsze można dodawać nagłówki wiadomości, nawet jeśli strict wersji jest używany. Flaga MustUnderstand może mieć wpływ na przechowywanie wersji. Ogólnie rzecz biorąc model przechowywania wersji dla nagłówków w programie WCF jest, jak opisano w specyfikacji protokołu SOAP.  
  
## <a name="service-contract-versioning"></a>Przechowywanie wersji kontraktów usług  
 Podobnie jak przechowywanie wersji kontraktów danych, przechowywanie wersji kontraktów usługi obejmuje również dodawanie, zmienianie i usuwanie operacji.  
  
### <a name="specifying-name-namespace-and-action"></a>Określanie nazwy, Namespace i akcji  
 Domyślnie nazwa kontraktu usługi jest nazwą interfejsu. Jego domyślnej przestrzeni nazw "http://tempuri.org", i akcji każdej operacji "http://tempuri.org/contractname/methodname". Zalecane jest, że jawnie określisz nazwę i przestrzeń nazw dla kontraktu usługi i akcję dla każdej operacji należy unikać "http://tempuri.org" i uniemożliwić nazwy interfejsu i metoda spowodują ujawnienie w kontrakcie usługi.  
  
### <a name="adding-parameters-and-operations"></a>Dodawanie parametrów i operacje  
 Dodawanie operacji usług udostępnianych przez usługę jest nierozdzielający zmiany, ponieważ istniejący klienci nie muszą być zajmującym się te nowe operacje.  
  
> [!NOTE]
>  Dodawanie operacji do kontraktu dwustronnego wywołania zwrotnego jest zmianą przerywającą.  
  
### <a name="changing-operation-parameter-or-return-types"></a>Zmiana parametru operacji lub typów zwracanych  
 Zmiana parametr lub zwracane typy ogólnie jest istotną zmianę, chyba, że nowy typ implementuje ten sam kontrakt danych implementowana przez typ stary. Aby wprowadzić zmiany, Dodaj nową operację do umowy serwisowej lub zdefiniowanie nowego kontraktu usługi.  
  
### <a name="removing-operations"></a>Operacje usuwania  
 Usuwanie operacji jest również istotną zmianę. Aby wprowadzić zmiany, zdefiniowanie nowego kontraktu usługi i ujawnisz go na nowy punkt końcowy.  
  
### <a name="fault-contracts"></a>Kontrakty błędów  
 <xref:System.ServiceModel.FaultContractAttribute> Atrybut umożliwia deweloperom kontraktu usługi, podaj informacje o błędach, które mogą być zwracane z operacji kontraktu.  
  
 Lista błędów, które opisano w kontrakcie usługi nie jest uważany za wyczerpujący. W dowolnym momencie operacja może zwrócić błędy, które nie zostały opisane w zmiana kontraktu. W związku z tym zmiana zestawu błędów opisanych w umowie nie jest uważany za istotne. Na przykład dodać do umowy przy użyciu nowych odporności <xref:System.ServiceModel.FaultContractAttribute> lub usunięcie istniejącej usterki z umowy.  
  
### <a name="service-contract-libraries"></a>Biblioteki kontraktu usługi  
 Organizacje mogą mieć bibliotek zamówień, gdy kontrakt jest opublikowana w centralnym repozytorium i konsultantów usługi wdrożenie umów z tego repozytorium. W tym przypadku gdy opublikujesz umowy serwisowej do repozytorium masz żadnej kontroli nad tym kto tworzy usług, które ją implementują. W związku z tym nie możesz modyfikować kontraktu usługi, po opublikowaniu renderowaniem go skutecznie niezmienne. Usługi WCF obsługuje dziedziczenie kontraktów, która może służyć do tworzenia nowego kontraktu, który rozszerza istniejących umów. Aby użyć tej funkcji, zdefiniuj nowy interfejs kontraktu usługi, która dziedziczy interfejs starego kontraktu usługi, a następnie dodaj metody nowego interfejsu. Następnie zmienić usługa, która implementuje ten kontrakt starego wdrożenia nowego kontraktu i zmieniać definicji punktu końcowego "versionOld", aby użyć nowego kontraktu. Dla klientów "versionOld" punktu końcowego będą nadal wyświetlane jako uwidaczniającą kontraktu "versionOld"; dla klientów "versionNew" punktu końcowego pojawi się do udostępnienia kontraktu "versionNew".  
  
## <a name="address-and-binding-versioning"></a>Adres i powiązanie przechowywania wersji  
 Zmiany adresu punktu końcowego i powiązania są istotne zmiany, chyba, że klienci są w stanie dynamicznie odnajdywania nowy adres punktu końcowego lub powiązania. Jeden mechanizm implementowania ta funkcja jest za pomocą rejestru Universal opis odnajdywania i integracja (UDDI) i wzorzec wywołania UDDI, gdzie klient próbuje nawiązać połączenia z punktem końcowym i, w przypadku awarii zapytanie UDDI dobrze znane Rejestr bieżący punkt końcowy metadanych. Klient używa następnie adres i powiązanie z tych metadanych do komunikowania się z punktem końcowym. Jeśli ta komunikacja zakończy się powodzeniem, klient buforuje informacje dotyczące adresów i powiązania do użycia w przyszłości.  
  
## <a name="routing-service-and-versioning"></a>Usługa routingu oraz zarządzanie ich wersjami  
 Jeśli zmiany wprowadzone do usługi są istotne zmiany i muszą mieć co najmniej dwóch różnych wersjach usługi uruchomionej jednocześnie służy usługa routingu WCF do przesyłania wiadomości do wystąpienia odpowiednią usługę. Usługa routingu WCF używa routingu opartego na zawartości, innymi słowy, używa informacji w wiadomości, aby określić miejsce do rozsyłania wiadomości. Aby uzyskać więcej informacji na temat usługi routingu WCF, zobacz [usługa routingu](../../../docs/framework/wcf/feature-details/routing-service.md). Aby uzyskać przykład sposobu użycia usługi routingu WCF pod kątem przechowywania wersji usługi, zobacz [How to: Przechowywanie wersji usługi](../../../docs/framework/wcf/feature-details/how-to-service-versioning.md).  
  
## <a name="appendix"></a>Dodatek  
 Wskazówki wersji kontraktu ogólne dane razie strict versioning jest traktować kontraktów danych jako niezmienialny i tworzenie nowych, gdy są wymagane zmiany. Nowa klasa musi zostać utworzona dla każdego nowego kontraktu danych, tak wymagany jest mechanizm pozwala uniknąć uruchomić istniejący kod, który został napisany pod względem stare dane kontraktu klasy i ponowne zapisywanie adresów pod względem nowej klasy kontraktu danych.  
  
 Jeden taki mechanizm jest zdefiniowanie członków każdej umowy danych oraz pisania kodu wewnętrznej implementacji pod względem interfejsów, a nie klasy kontraktu danych, które implementują interfejsy za pomocą interfejsów. W poniższym kodzie dla wersji 1 usługi pokazano `IPurchaseOrderV1` interfejsu i `PurchaseOrderV1`:  
  
```  
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
  
 Podczas operacji kontraktu usługi powinny być zapisane w `PurchaseOrderV1`, logiki biznesowej rzeczywiste byłaby w kategoriach `IPurchaseOrderV1`. Następnie, w wersji 2 będzie istnieć nową `IPurchaseOrderV2` interfejsu i nową `PurchaseOrderV2` klasy, jak pokazano w poniższym kodzie:  
  
```  
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
  
 Kontrakt usługi zostałaby zaktualizowana w celu uwzględnienia nowych operacji, które są zapisywane w `PurchaseOrderV2`. Istniejącej logiki biznesowej, zapisane pod względem `IPurchaseOrderV1` będzie w dalszym ciągu działać w przypadku `PurchaseOrderV2` i nowej logiki biznesowej, który wymaga `OrderDate` właściwości powinny być zapisane w `IPurchaseOrderV2`.  
  
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
- [Równoważność kontraktów danych](../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [Wywołania zwrotne serializacji z tolerancją dla wersji](../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md)
