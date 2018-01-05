---
title: "Przechowywanie wersji usługi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37575ead-d820-4a67-8059-da11a2ab48e2
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 791e201907f72f9d590f6d835fd6ec1bfc25633f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="service-versioning"></a>Przechowywanie wersji usługi
Po początkowym wdrożeniu i potencjalnie kilka razy w okresie ich istnienia usług (i punktów końcowych, które udostępniają) może być konieczne zostanie zmieniony z różnych powodów, takich jak zmieniające się potrzeby biznesowe, wymagania dotyczące technologii informacji, lub do innych adresów problemy. Każda zmiana wprowadziła nową wersję usługi. W tym temacie wyjaśniono, jak należy wziąć pod uwagę przechowywania wersji [!INCLUDE[indigo1](../../../includes/indigo1-md.md)].  
  
## <a name="four-categories-of-service-changes"></a>Cztery kategorie o zmianach usługi  
 Zmiany usług, które mogą być wymagane, można podzielić na cztery kategorie:  
  
-   Zwiń zmiany: na przykład operacji mogą być dodane lub element danych w komunikacie może być dodane lub zmienione.  
  
-   Zmiany adresów: na przykład usługi przechodzi do innej lokalizacji, w której punkty końcowe mają nowe adresy.  
  
-   Powiązanie zmiany: na przykład zmiany mechanizm zabezpieczeń lub zmień jej ustawienia.  
  
-   Zmiany implementacji: na przykład implementacji metody wewnętrznej zmiany.  
  
 Niektóre z tych zmian są nazywane "podziału", a inne są "nierozdzielający". Zmiana jest *nierozdzielający* Jeśli wszystkie komunikaty, które mogłyby zostać przetworzone pomyślnie w poprzedniej wersji pomyślnie przetworzonych w nowej wersji. Wszelkie zmiany, które nie spełnia tego kryterium jest *fundamentalne* zmienić.  
  
## <a name="service-orientation-and-versioning"></a>Orientacja usługi i kontroli wersji  
 Jeden z zasady orientacji usługi to usług i klientów autonomicznego (lub niezależny). Między innymi oznacza to, że deweloperzy usług nie założono, kontrolowania lub nawet wiedzieć o wszystkich klientów usługi. Eliminuje to opcja odbudowywania ani ponownego wdrażania wszystkich klientów, gdy wersje zmian usługi. W tym temacie założono usługa działa zgodnie z tym cechą i dlatego musi być zmieniony lub "kontrolą wersji" niezależnie od klientów.  
  
 W przypadku, gdy na istotne zmiany jest nieoczekiwany i nie można uniknąć aplikacji może wybrać opcję Ignoruj ten cechą i wymagają, aby klienci należy odbudować i wdrożone za pomocą nowej wersji usługi.  
  
## <a name="contract-versioning"></a>Przechowywanie wersji kontraktów  
 Kontrakty używany przez klienta musi być taka sama jak kontraktu używanego przez usługę; tylko muszą być zgodne.  
  
 Dla kontraktów usług zgodności można dodać nowych operacji oznacza udostępnianych przez usługę, ale istniejące operacje nie można usunąć ani zmienić semantycznie.  
  
 Dla kontraktów danych zgodności oznacza, że nowy typ schematu, definicje mogą zostać dodane, ale istniejącej definicji typu schematu nie można zmienić dzielenie sposobów. Fundamentalne zmiany może obejmować usunięcie danych elementów członkowskich lub niezgodny sposób zmiany ich typu danych. Ta funkcja umożliwia usłudze niektórych szerokości geograficznej w zmiana wersji jego kontraktów bez przerywania klientów. W dwóch następnych sekcjach opisano nierozdzielających i fundamentalne zmiany, które mogą być dla [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] kontraktów danych i usługi.  
  
## <a name="data-contract-versioning"></a>Przechowywanie wersji kontraktów danych  
 W tej sekcji omówiono zarządzanie wersjami danych, korzystając z <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Runtime.Serialization.DataContractAttribute> klasy.  
  
### <a name="strict-versioning"></a>Przechowywanie wersji ograniczeniami  
 W wielu scenariuszach podczas zmiany wersji jest problem dewelopera usługi nie mają kontrolę nad klientów i w związku z tym nie można wprowadzić założenia dotyczące jak będzie reagować na zmiany w komunikacie lub schemat XML. W takich przypadkach musi zagwarantować, że nowych wiadomości będzie sprawdzania poprawności schematu starego dwóch powodów:  
  
-   Stary klientów opracowano przy założeniu, że nie spowoduje zmiany schematu. Nie może przetwarzać komunikatów, które nigdy nie są one przeznaczone do.  
  
-   Stary klienci mogą wykonywać rzeczywiste weryfikacji względem starego schematu przed próbą nawet do przetwarzania komunikatów.  
  
 Zalecane podejście w takich scenariuszach jest można traktować jako niezmienialny istniejących kontraktów danych i tworzenie nowych unikatowy XML kwalifikowanej nazwy. Dewelopera usługi będą następnie Dodaj nowych metod do istniejący kontrakt usługi lub utworzenia nowego kontraktu usługi z metody, które używają nowego kontraktu danych.  
  
 Często będzie przypadku dewelopera usługi nie musi zapisywać niektórych logiki biznesowej, które powinno być ono uruchomione w ramach wszystkich wersji kontraktu danych oraz specyficzne dla wersji business kodu dla każdej wersji kontraktu danych. Dodatek na końcu tego tematu opisano, jak interfejsy mogą służyć do spełnia te wymagania.  
  
### <a name="lax-versioning"></a>Swobodny kontroli wersji  
 W wielu innych scenariuszach dewelopera usługi wprowadzić założeniu, że dodawanie nowych, opcjonalne członka do kontraktu danych nie będę powodować utraty istniejących klientów. Wymaga to deweloperom usługi Sprawdź, czy istniejący klienci nie są wykonywane sprawdzanie poprawności schematu i czy Ignoruj ich elementy członkowskie danych nieznany. W tych scenariuszach jest to możliwe, należy korzystać z funkcji kontraktu danych do dodawania nowych elementów członkowskich w sposób nierozdzielający. Dewelopera usługi można wprowadzać tego założeń bez obaw, jeśli już użyto funkcji kontraktu danych do przechowywania wersji dla pierwszej wersji usługi.  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], Usług sieci Web ASP.NET i wiele innych Obsługa usługi sieci Web stosy *swobodny versioning*: oznacza to, że ich nie zgłaszają wyjątki dla nowych członków: nieznane dane w odebranych danych.  
  
 To proste przez pomyłkę podejrzeń, że dodawanie nowego elementu członkowskiego nie będę powodować utraty istniejących klientów. Jeśli nie wiesz, że wszyscy klienci mogą obsługiwać swobodny przechowywania wersji, zalecane jest wytycznymi wersjonowania ograniczeniami i traktować danych umów jako niezmienialny.  
  
 Aby uzyskać szczegółowe wskazówki dotyczące zarówno swobodny i ograniczeniami przechowywanie wersji kontraktów danych, zobacz [najlepsze rozwiązania: przechowywanie wersji kontraktów danych](../../../docs/framework/wcf/best-practices-data-contract-versioning.md).  
  
### <a name="distinguishing-between-data-contract-and-net-types"></a>Kontrakt danych i typów .NET  
 .NET klasy lub struktury może zostać przedstawione jako kontraktu danych poprzez zastosowanie <xref:System.Runtime.Serialization.DataContractAttribute> do klasy atrybutu. Typ architektury .NET i jego projekcje kontraktu danych są dwa różne kwestie. Użytkownik może mieć wiele typów .NET z tym samym projekcji kontraktu danych. Ta różnica jest szczególnie przydatna w umożliwia zmianę typ architektury .NET, przy zachowaniu kontraktu prognozowanych danych, co utrzymania zgodności z istniejących klientów nawet w tym sensie strict, Word. Istnieją dwie czynności, które należy zawsze zachować tej różnicy między .NET, a typ danych kontraktu:  
  
-   Określ <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> i <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>. Należy zawsze podać nazwę i przestrzeń nazw umowy danych, aby zapobiec nazwę danego typu .NET i przestrzeń nazw z ujawniany w umowie. Dzięki temu, jeśli później zdecydujesz się zmienić obszaru nazw .NET lub wpisz nazwę, dany kontrakt danych jest taka sama.  
  
-   Określ <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A>. Należy zawsze podać nazwę użytkownika elementy członkowskie danych, aby zapobiec przypadkowym w kontrakcie nazwę użytkownika platformy .NET. Dzięki temu, jeśli później zdecydujesz się zmienić nazwę .NET elementu członkowskiego, dany kontrakt danych jest taka sama.  
  
### <a name="changing-or-removing-members"></a>Zmienić lub usunąć elementy członkowskie  
 Zmiana nazwy lub dane typu elementu członkowskiego lub usunąć elementy członkowskie danych jest istotne zmiany nawet wtedy, gdy swobodny versioning jest dozwolone. Jeśli jest to konieczne, Utwórz nowe kontraktu danych.  
  
 W przypadku zgodności o wysokim znaczeniu, może wziąć pod uwagę ignorowanie elementy członkowskie danych nieużywane w kodzie i pozostawić bez zmian. Jeśli są podzielić elementu członkowskiego danych do wielu członków, można rozważyć pozostawienie istniejącego elementu członkowskiego w miejscu jako właściwość można wykonywać wymagane rozdzielenie i ponowne agregacji w przypadku klientów niskiego poziomu (klientów, które nie zostały uaktualnione do najnowszej wersji).  
  
 Podobnie zmiany nazwę lub przestrzeń nazw kontraktu danych są istotne zmiany.  
  
### <a name="round-trips-of-unknown-data"></a>Przechodzenia nieznane dane  
 W niektórych scenariuszach istnieje potrzeba "obustronne" nieznane dane pochodzące z elementy członkowskie dodane w nowej wersji. Na przykład usługi "versionNew" wysyła dane z niektórymi nowo dodanych elementów członkowskich do klienta "versionOld". Klient ignoruje nowo dodanych elementów podczas przetwarzania komunikatu, ale jego przesłania tego tych samych danych, w tym nowo dodanych elementów członkowskich, wróć do usługi versionNew. Typowy scenariusz, w tym jest aktualizacje danych gdzie zwrócił, zmienić i pobierane z usługi danych.  
  
 Aby włączyć dwustronną komunikację dla określonego typu, typ musi implementować <xref:System.Runtime.Serialization.IExtensibleDataObject> interfejsu. Interfejs zawiera jedną właściwość <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> zwracającą <xref:System.Runtime.Serialization.ExtensionDataObject> typu. Właściwość jest używana do przechowywania wszelkich danych z przyszłych wersji kontraktu danych, który jest nieznany w bieżącej wersji. Dane te są nieprzezroczyste do klienta, ale, gdy wystąpienie jest serializowany, zawartość <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> właściwości są zapisywane z resztą danych członków kontraktu danych.  
  
 Zaleca się, że swój typ implementuje ten interfejs, aby pomieścić nowy i nieznany przyszłych członków.  
  
### <a name="data-contract-libraries"></a>Biblioteki kontraktu danych  
 Może to być bibliotek kontraktów danych, gdy kontrakt jest publikowana w centralnym repozytorium, i implementacji usługi i typu wdrożenia i ujawnia kontraktów danych z tego repozytorium. W takim przypadku podczas publikowania kontraktu danych do repozytorium, możesz nie kontrolują który tworzy typy, które implementuje go. W związku z tym nie można zmodyfikować umowy po opublikowaniu go renderowaniem go skutecznie niezmienialny.  
  
### <a name="when-using-the-xmlserializer"></a>Przy użyciu elementu XmlSerializer  
 Zastosuj te same zasady przechowywania wersji, gdy przy użyciu <xref:System.Xml.Serialization.XmlSerializer> klasy. Jeśli wymagane jest przechowywanie wersji strict, traktować jako niezmienialny kontraktów danych i Utwórz nowe kontraktów danych z nazwy kwalifikowanej, unikatową nowych wersji. Jeśli masz pewność, że swobodny wersji może być używany, można dodawać nowych członków do serializacji w nowej wersji, ale nie zmienić lub usunąć istniejące elementy członkowskie.  
  
> [!NOTE]
>  <xref:System.Xml.Serialization.XmlSerializer> Używa <xref:System.Xml.Serialization.XmlAnyElementAttribute> i <xref:System.Xml.Serialization.XmlAnyAttributeAttribute> atrybuty do obsługi dwustronną komunikację nieznane dane.  
  
## <a name="message-contract-versioning"></a>Przechowywanie wersji kontraktów komunikatu  
 Wytyczne dotyczące przechowywanie wersji kontraktów komunikatu są bardzo podobne do przechowywanie wersji kontraktów danych. Jeśli wymagana jest strict przechowywania wersji, należy nie zmienić treść komunikatu, ale zamiast tego utworzyć nowe kontraktu komunikatu o unikatowej nazwie kwalifikowanej. Jeśli znasz służy swobodny przechowywania wersji, można dodać nowe części treści wiadomości, ale nie zmienić lub usunąć istniejące. W tych wskazówkach zastosowanie zarówno do bez systemu operacyjnego i opakować kontraktów komunikatu.  
  
 Zawsze można dodać nagłówków komunikatów, nawet jeśli strict versioning jest w użyciu. Flaga atrybutu MustUnderstand może mieć wpływ na przechowywanie wersji. Ogólnie rzecz biorąc, przechowywania wersji modelu dla nagłówków w [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] jest zgodnie z opisem w specyfikacji protokołu SOAP.  
  
## <a name="service-contract-versioning"></a>Przechowywanie wersji kontraktów usług  
 Podobnie jak przechowywanie wersji kontraktów danych, przechowywanie wersji kontraktów usługi obejmuje również dodawanie, zmienianie i usuwanie operacji.  
  
### <a name="specifying-name-namespace-and-action"></a>Określanie nazwy i Namespace, akcja  
 Domyślnie nazwa kontraktu usługi jest nazwą interfejsu. Jego domyślnej przestrzeni nazw jest "http://tempuri.org" i "http://tempuri.org/contractname/methodname" jest akcja każdej operacji. Zaleca się, że użytkownik jawnie określić nazwę i przestrzeń nazw kontraktu usługi i akcji dla każdej operacji należy unikać "http://tempuri.org" i nazwy interfejsu i metoda zapobiec przypadkowym w kontrakcie usługi.  
  
### <a name="adding-parameters-and-operations"></a>Dodawanie parametrów i operacje  
 Dodawanie operacji usługi udostępniane przez usługi jest nierozdzielający zmiany, ponieważ istniejący klienci nie muszą być zajmującym się tych nowych operacji.  
  
> [!NOTE]
>  Dodawanie działań do kontraktu dwustronnego wywołania zwrotnego jest istotne zmiany.  
  
### <a name="changing-operation-parameter-or-return-types"></a>Zmiana parametru operacji lub typy zwracane  
 Zmiana parametr lub zwracane typy zazwyczaj jest istotne zmiany, chyba że nowy typ implementuje ten sam kontrakt danych implementowane przez stary typ. Aby wprowadzić zmiany, dodać nową operację do umowy serwisowej lub zdefiniowanie nowego kontraktu usługi.  
  
### <a name="removing-operations"></a>Usuwanie operacji  
 Usuwanie operacji jest również istotne zmiany. Aby wprowadzić zmiany, zdefiniowanie nowego kontraktu usługi i pozostawić ją na nowy punkt końcowy.  
  
### <a name="fault-contracts"></a>Kontrakty błędów  
 <xref:System.ServiceModel.FaultContractAttribute> Atrybut umożliwia deweloperowi kontraktu usługi, określ informacje o błędach, które mogą być zwracane z operacji kontraktu.  
  
 Lista błędów, które opisano w kontrakcie usługi nie jest uważana za wyczerpujący. W dowolnym momencie operacja może zwrócić błędów, które nie zostały opisane w jego kontraktu. W związku z tym zmiana zestawu błędów opisanego w kontrakcie nie jest uznawane za krytyczne. Na przykład dodać do umowy przy użyciu nowych usterek <xref:System.ServiceModel.FaultContractAttribute> lub usunięcie istniejącej usterki z umowy.  
  
### <a name="service-contract-libraries"></a>Biblioteki kontraktu usługi  
 Organizacje mogą stosować bibliotek kontraktów, gdy kontrakt jest publikowana w centralnym repozytorium i implementacji usługi Implementowanie kontraktów z tego repozytorium. W takim przypadku podczas publikowania kontraktu usługi do repozytorium można nie kontrolują stwarza usług, które implementuje go. W związku z tym nie można modyfikować po opublikowaniu kontrakt usługi renderowaniem go skutecznie niezmienialny. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]obsługuje kontraktu dziedziczenia, która może służyć do tworzenia nowego kontraktu, rozszerzający istniejących umów. Aby użyć tej funkcji, zdefiniuj nowy interfejs kontraktu usługi, która dziedziczy po interfejsie starego kontraktu usługi, a następnie dodaj metody nowego interfejsu. Następnie zmienić usługa, która implementuje starego kontraktu do wdrożenia nowego kontraktu i zmień definicję punktu końcowego "versionOld", aby użyć nowego kontraktu. Do klientów "versionOld" punktu końcowego będą nadal wyświetlane jako uwidaczniającą kontraktu "versionOld"; do klientów "versionNew" punktu końcowego pojawi się do udostępnienia kontraktu "versionNew".  
  
## <a name="address-and-binding-versioning"></a>Adres i powiązanie kontroli wersji  
 Zmiany adres punktu końcowego i powiązania są fundamentalne zmiany, chyba że klienci są w stanie powiązania lub dynamicznie odnajdywania nowy adres punktu końcowego. Jeden mechanizm stosowania tej funkcji jest za pomocą rejestru Universal Description odnajdywania i usług UDDI i wzorzec wywołania UDDI, gdzie klient próbuje nawiązać połączenia z punktem końcowym i, w przypadku awarii zapytanie UDDI dobrze znane rejestr dla bieżących metadanych punktu końcowego. Klient używa następnie adres i powiązanie z tym metadanych do komunikowania się z punktem końcowym. Jeśli ta komunikacja zakończy się powodzeniem, klient buforuje informacje adres i powiązanie do użytku w przyszłości.  
  
## <a name="routing-service-and-versioning"></a>Usługa routingu i kontroli wersji  
 Jeśli zmiany wprowadzone do usługi są fundamentalne zmiany, a muszą mieć co najmniej dwa różne wersje usługi uruchomionej jednocześnie służy usługa routingu WCF do przesyłania wiadomości do wystąpienia odpowiedniej usługi. Usługa routingu WCF używa routingu opartego na zawartość, innymi słowy, używa informacji w komunikacie do określenia miejsca kierowania komunikatu. [!INCLUDE[crabout](../../../includes/crabout-md.md)]Zobacz Usługa routingu WCF [usługa routingu](../../../docs/framework/wcf/feature-details/routing-service.md). Przykład sposobu użycia usługi routingu WCF do wersji usługi zobacz [jak: przechowywanie wersji usługi](../../../docs/framework/wcf/feature-details/how-to-service-versioning.md).  
  
## <a name="appendix"></a>Dodatek  
 Wskazówki przechowywanie wersji kontraktu ogólne dane gdy wymagany jest strict versioning jest traktować jako niezmienialny kontraktów danych i utworzyć nowe, jeśli są wymagane zmiany. Nową klasę musi zostać utworzona dla każdego nowego kontraktu danych, więc mechanizm jest potrzebny, aby uniknąć konieczności podjęcia istniejący kod, który został zapisany w postaci liczby stare dane kontraktu klasy i ponowne zapisywanie adresów pod względem nowej klasy kontraktu danych.  
  
 Jeden taki mechanizm jest za pomocą interfejsów można zdefiniować elementów członkowskich każdego kontraktu danych oraz pisania kodu wewnętrznej implementacji pod względem interfejsy zamiast klasy kontraktu danych, które implementują interfejsy. Poniższy kod dla wersji 1 usługi przedstawia `IPurchaseOrderV1` interfejsu i `PurchaseOrderV1`:  
  
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
  
 Podczas operacji kontraktu usługi powinny być zapisane w postaci liczby `PurchaseOrderV1`, logika biznesowa rzeczywiste byłoby w `IPurchaseOrderV1`. Następnie, w wersji 2 byłoby nowy `IPurchaseOrderV2` interfejsu i nowy `PurchaseOrderV2` klasy, jak pokazano w poniższym kodzie:  
  
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
  
 Kontrakt usługi będzie można zaktualizowano w celu uwzględnienia nowych operacji, które są zapisywane w postaci liczby `PurchaseOrderV2`. Istniejące logiki biznesowej zapisywane w postaci liczby `IPurchaseOrderV1` będzie nadal działać w przypadku `PurchaseOrderV2` i nowych logiki biznesowej, które należy `OrderDate` właściwości powinny być zapisane w postaci liczby `IPurchaseOrderV2`.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A>  
 <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>  
 <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A>  
 <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>  
 <xref:System.Runtime.Serialization.IExtensibleDataObject>  
 <xref:System.Runtime.Serialization.ExtensionDataObject>  
 <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A>  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [Równoważność kontraktów danych](../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)  
 [Wywołania zwrotne serializacji z tolerancją dla wersji](../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md)
