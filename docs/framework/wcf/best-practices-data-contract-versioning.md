---
title: 'Najlepsze rozwiązania: Przechowywanie wersji kontraktów danych'
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- service contracts
- best practices [WCF], data contract versioning
- Windows Communication Foundation, data contracts
ms.assetid: bf0ab338-4d36-4e12-8002-8ebfdeb346cb
ms.openlocfilehash: cf3ae6f47f63c545edf3d65804daa049d4541788
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59334929"
---
# <a name="best-practices-data-contract-versioning"></a>Najlepsze rozwiązania: Przechowywanie wersji kontraktów danych
Ten temat zawiera najlepsze rozwiązania dotyczące tworzenia kontraktów danych, które można łatwo ewoluować wraz z upływem czasu. Aby uzyskać więcej informacji na temat kontraktów danych, zobacz Tematy w [za pomocą kontraktów danych](../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
## <a name="note-on-schema-validation"></a>Uwaga dotycząca sprawdzania poprawności schematu  
 W Omawiając przechowywanie wersji kontraktów danych, jest należy pamiętać, że schematu kontraktu danych, które są eksportowane przez Windows Communication Foundation (WCF) nie ma żadnych obsługą wersjonowania, poza tym, że elementy są oznaczone jako opcjonalną domyślnie.  
  
 Oznacza to, że nawet najbardziej typowe wersji scenariusza, takie jak dodanie nowy element członkowski danych nie mogą zostać zaimplementowane w sposób, który jest bezproblemowe w odniesieniu do danego schematu. Nowsze wersje kontraktu danych (za pomocą nowej składowej danych, na przykład) nie weryfikują przy użyciu starego schematu.  
  
 Istnieją jednak wiele scenariuszy, w których zgodność ścisłego schematu nie jest wymagane. Wiele platform usług sieci Web, w tym usług WCF i sieci Web XML utworzone za pomocą programu ASP.NET, nie wykonać sprawdzanie poprawności schematu domyślnie i w związku z tym tolerować dodatkowe elementy, które nie zostały opisane w schemacie. Podczas pracy z takich platform, wiele scenariuszy, w wersji są łatwiejsze do wdrożenia.  
  
 W związku z tym, są dwa zestawy danych kontraktu wskazówki wersji: on ustawiony dla scenariuszy, w którym ważność ścisłego schematu jest ważna, a innego zestawu dla scenariuszy, gdy nie jest.  
  
## <a name="versioning-when-schema-validation-is-required"></a>Przechowywanie wersji, gdy wymagana jest Weryfikacja schematu  
 Jeśli ważność ścisłego schematu jest wymagany we wszystkich kierunkach (nowy w starym i starego do nowego), kontraktów danych należy rozważyć niezmienne. Jeśli wymagane jest przechowywanie wersji, nowe kontraktu danych należy utworzyć inną nazwę lub przestrzeń nazw, i kontrakt usługi przy użyciu typu danych powinien być poddany kontroli wersji w związku z tym.  
  
 Na przykład zamówienie zakupu przetwarzania kontraktu usługi o nazwie `PoProcessing` z `PostPurchaseOrder` operacji przyjmuje parametr, który jest zgodny z `PurchaseOrder` kontraktu danych. Jeśli `PurchaseOrder` kontraktu musi zmienić, należy utworzyć nowe kontraktu danych, oznacza to, `PurchaseOrder2`, który zawiera zmiany. Następnie musi obsługiwać wersji na poziomie kontraktu usługi. Na przykład, tworząc `PostPurchaseOrder2` operacji, która przyjmuje `PurchaseOrder2` parametru lub tworząc `PoProcessing2` kontraktu usługi gdzie `PostPurchaseOrder` Trwa operacja `PurchaseOrder2` kontraktu danych.  
  
 Należy pamiętać, że zmiany w kontraktach danych, które są przywoływane przez inne kontraktów danych także rozszerzyć warstwy modelu usług. Na przykład w poprzednim scenariuszu `PurchaseOrder` kontraktu danych nie trzeba zmieniać. Jednak zawiera element członkowski danych z `Customer` kontraktu danych, który z kolei zawarty składowa danych klasy `Address` kontraktu danych, które muszą zostać zmienione. W takim przypadku należy utworzyć `Address2` kontraktu danych za pomocą wymagane zmiany `Customer2` kontraktu danych, który zawiera `Address2` element członkowski danych, a `PurchaseOrder2` kontraktu danych, który zawiera `Customer2` element członkowski danych. Tak jak w przypadku poprzedniego Umowa serwisowa musi również być poddany kontroli wersji.  
  
 Mimo że w tych przykładach zmiany nazw (na przykład przez dołączenie "2"), zaleca się zmiany obszarów nazw, zamiast nazwy, dodając nowe przestrzenie nazw za pomocą numeru wersji lub wartość typu date. Na przykład `http://schemas.contoso.com/2005/05/21/PurchaseOrder` kontraktu danych zmienią się `http://schemas.contoso.com/2005/10/14/PurchaseOrder` kontraktu danych.  
  
 Aby uzyskać więcej informacji zobacz najważniejsze wskazówki: [Przechowywanie wersji usługi](../../../docs/framework/wcf/service-versioning.md).  
  
 Od czasu do czasu należy zagwarantować zgodność ścisłego schematu dla komunikatów wysyłanych przez aplikację, ale nie można polegać na komunikaty przychodzące być ściśle zgodny ze schematem. W tym przypadku istnieje zagrożenie, że wiadomości przychodzące mogą zawierać nadmiarowe dane. Nadmiarowe wartości są przechowywane i zwrócony przez architekturę WCF, czyli z wiadomości nieprawidłowy schemat. Aby uniknąć tego problemu, funkcja Pełna zgodnooć wersji powinna być wyłączona. Istnieją dwa sposoby, aby to zrobić.  
  
-   Nie należy implementować <xref:System.Runtime.Serialization.IExtensibleDataObject> interfejsu na wszystkich typów.  
  
-   Zastosuj <xref:System.ServiceModel.ServiceBehaviorAttribute> atrybutu do Twojej umowy serwisowej z <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> właściwością `true`.  
  
 Aby uzyskać więcej informacji na temat Pełna zgodnooć wersji, zobacz [kontrakty danych zgodne](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
## <a name="versioning-when-schema-validation-is-not-required"></a>Przechowywanie wersji, gdy sprawdzanie poprawności schematu nie jest wymagane  
 Rzadko wymagana jest zgodność ścisłego schematu. Wiele platform tolerować dodatkowe elementy, które nie są opisane przez schemat. Tak długo, jak to jest tolerowane, pełny zestaw funkcji opisanych w [przechowywanie wersji kontraktów danych](../../../docs/framework/wcf/feature-details/data-contract-versioning.md) i [kontrakty danych zgodne](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md) mogą być używane. Zaleca się następujące wskazówki.  
  
 Niektóre wytyczne musi występować dokładnie wysyłanie nowej wersji typu gdzie stary oczekuje lub wysyłania stare hasło, których oczekuje się nowego. Innych wytycznych, nie są ściśle wymagane, ale są wymienione w tym miejscu, ponieważ one mogą mieć wpływ na przyszłość schematu przechowywania wersji.  
  
1. Nie należy próbować wersji kontraktów danych poprzez dziedziczenie typu. Aby utworzyć nowsze wersje, zmień kontraktu danych na istniejący typ lub utworzenia nowego typu niepowiązanego.  
  
2. Dziedziczenie wraz z kontraktów danych jest dozwolone, pod warunkiem, że dziedziczenie nie jest używana jako mechanizm obsługi wersji, a niektóre zasady zostaną wykonane prawidłowo. Jeśli typ pochodzi z określonego typu podstawowego, nie dokonuj on pochodzić z innym typem bazowym w przyszłych wersjach (chyba że ma te same dane umowy). Istnieje jeden wyjątek to: typ można wstawić do hierarchii między typu kontraktu danych i jego typ podstawowy, ale tylko wtedy, gdy nie zawiera elementów członkowskich danych za pomocą te same nazwy jak inne elementy wszystkie możliwe wersje innych typów w hierarchii. Ogólnie rzecz biorąc elementy członkowskie danych przy użyciu tych samych nazw na różnych poziomach w tej samej hierarchii dziedziczenia może prowadzić do problemów poważnych versioning i należy ich unikać.  
  
3. Począwszy od pierwszej wersji kontraktu danych, zawsze wdrożenia <xref:System.Runtime.Serialization.IExtensibleDataObject> umożliwia Pełna zgodnooć wersji. Aby uzyskać więcej informacji, zobacz [kontrakty danych zgodne](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md). Jeśli zostały wydane co najmniej wersji typu bez implementacji interfejsu, należy ją wykonać w następnej wersji typu.  
  
4. W nowszych wersjach nie zmieniaj nazwy kontraktu danych lub obszaru nazw. Jeśli zmiana nazwy lub przestrzeń nazw typu kontraktu danych bazowych upewnij się zachować nazwie kontraktu danych i przestrzeni nazw przy użyciu odpowiednich mechanizmów, takich jak <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> właściwość <xref:System.Runtime.Serialization.DataContractAttribute>. Aby uzyskać więcej informacji na temat nazewnictwa, zobacz [nazwy kontraktów danych](../../../docs/framework/wcf/feature-details/data-contract-names.md).  
  
5. W nowszych wersjach nie należy zmieniać nazw żadnych składowych danych. Jeśli zmiana nazwy pola, właściwości lub zdarzenia bazowego elementu członkowskiego danych, użyj `Name` właściwość <xref:System.Runtime.Serialization.DataMemberAttribute> zachować istniejącą nazwę elementu członkowskiego danych.  
  
6. W nowszych wersjach nie należy zmieniać typu pola, właściwości lub zdarzenia podstawowy element członkowski danych w taki sposób, że dane wynikowe kontrakt dla tej zmiany element członkowski danych. Należy pamiętać, że typy interfejsów są równoważne <xref:System.Object> na potrzeby określania kontraktu oczekiwanych danych.  
  
7. W nowszych wersjach, nie należy zmieniać kolejność istniejących elementów członkowskich danych przez dostosowanie <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> właściwość <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutu.  
  
8. W nowszych wersjach można dodać nowe elementy członkowskie danych. Powinny one zawsze wykonać następujące czynności:  
  
    1.  <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> Właściwość zawsze należy pozostawić wartość domyślną `false`.  
  
    2.  Jeśli wartość domyślną `null` lub zero dla elementu członkowskiego jest nieodpowiednia, można określić metodę wywołania zwrotnego za pomocą <xref:System.Runtime.Serialization.OnDeserializingAttribute> do zapewniania domyślnego uzasadnione, w przypadku, gdy element członkowski nie jest obecny w strumienia przychodzącego. Aby uzyskać więcej informacji na temat wywołania zwrotnego, zobacz [wywołania zwrotne serializacji z tolerancją dla wersji](../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md).  
  
    3.  <xref:System.Runtime.Serialization.DataMemberAttribute.Order?displayProperty=nameWithType> Właściwość powinna być używana, aby upewnić się, czy wszystkie elementy członkowskie nowo dodane dane są wyświetlane po istniejące elementy członkowskie danych. Zalecanym sposobem w ten sposób jest następująca: Żaden z elementów członkowskich danych w pierwszej wersji kontraktu danych powinny mieć ich `Order` zestawu właściwości. Wszystkie elementy członkowskie danych dodane w wersji 2 kontraktu danych powinny mieć ich `Order` właściwość ustawioną na 2. Wszystkie elementy członkowskie danych dodane w wersji 3 kontraktu danych powinny mieć ich `Order` ustawiony na wartość 3 i tak dalej. Dopuszcza się mieć więcej niż jeden element członkowski danych takie same `Order` numer.  
  
9. Nie usuwaj elementy członkowskie danych w nowszych wersjach, nawet wtedy, gdy <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> właściwość pozostawało na jego domyślna właściwość `false` w poprzednich wersjach.  
  
10. Nie zmieniaj `IsRequired` właściwość wszelkie istniejące elementy członkowskie danych z wersji do wersji.  
  
11. Dla wymaganych elementów członkowskich danych (gdzie `IsRequired` jest `true`), nie należy zmieniać `EmitDefaultValue` właściwości z wersji do wersji.  
  
12. Nie należy próbować tworzyć hierarchie rozgałęziony przechowywania wersji. Oznacza to, że zawsze należy ścieżki co najmniej w jednym kierunku z dowolnej wersji do innej wersji przy użyciu tylko zmiany dozwolone stosowanie tych wytycznych.  
  
     Na przykład, jeśli wersja 1 kontraktu danych osoby zawiera tylko nazwę składowej danych, nie należy tworzyć 2a wersja kontraktu, dodawanie tylko wiek elementu członkowskiego i wersji 2b dodawanie tylko członek adresu. Zamierzasz 2b z 2a obejmowałaby usunięcie wiek, a dodanie adresu; Możesz to zrobić w innym kierunku będzie pociąga za sobą usunięcie adresu i dodawanie wieku. Usuwanie członków nie jest dozwolona stosowanie tych wytycznych.  
  
13. Zazwyczaj nie należy tworzyć nowych podtypów istniejące typy kontraktu danych w nowej wersji aplikacji. Podobnie nie należy tworzyć nowych kontraktów danych, które są używane zamiast dane, które są zadeklarowane elementy członkowskie jako obiekt lub typów interfejsów. Tworzenie tych nowych klas jest dozwolone tylko wtedy, gdy wiesz, dodawać nowych typów do listy znanych typów wszystkich wystąpień starych aplikacji. Na przykład w wersji 1 aplikacji może mieć LibraryItem dane typu z książką kontraktu i gazet podtypy kontraktu. LibraryItem będzie miała listę znanych typów, która zawiera książki i gazet. Załóżmy, że teraz dodać typ magazynu w wersji 2, która jest podtypem LibraryItem. Jeśli wyślesz wystąpienia magazyn w wersji 2 do wersji 1 kontraktu danych magazyn nie znajduje się na liście znanych typów, i zgłaszany jest wyjątek.  
  
14. Należy nie dodawać lub usuwać elementy członkowskie wyliczenia między wersjami. Należy również nie zmienić nazwy elementów członkowskich wyliczenia, chyba że używana jest właściwość nazwa na `EnumMemberAttribute` atrybutu, aby zapewnić ich nazwy w modelu kontraktu danych, takie same.  
  
15. Kolekcje są wymienne w modelu kontraktu danych, zgodnie z opisem w [typy kolekcji w kontraktach danych](../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md). Umożliwia to doskonałe stopień elastyczności. Jednak należy się upewnić, że nie przypadkowo zmienisz typ kolekcji, w innych niż wymienne sposób od poprzedniej wersji. Na przykład nie należy zmieniać z kolekcji, które nie zostały dostosowane (to znaczy bez `CollectionDataContractAttribute` atrybutu) do dostosowanego co najmniej kolekcję dostosowane do jednego z innych dostosowanego przez producenta. Ponadto nie należy zmieniać właściwości na `CollectionDataContractAttribute` od wersji. Jedyna zmiana dozwolone jest dodawanie właściwości nazwy lub Namespace, jeśli zmieniono nazwę lub przestrzeń nazw podstawowy typ kolekcji, a następnie musisz wprowadzić swoje dane umowy, nazwę i przestrzeń nazw taki sam jak w poprzedniej wersji.  
  
 Niektóre z wymienionych w tym miejscu można bezpiecznie zignorować kiedy szczególne okoliczności. Upewnij się, że w pełni zrozumieć serializacji, deserializacji i mechanizmy schematu przed odejście od wytycznych.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>
- <xref:System.Runtime.Serialization.IExtensibleDataObject>
- <xref:System.ServiceModel.ServiceBehaviorAttribute>
- <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A>
- <xref:System.Runtime.Serialization.ExtensionDataObject>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- [Używanie kontraktów danych](../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Przechowywanie wersji kontraktów danych](../../../docs/framework/wcf/feature-details/data-contract-versioning.md)
- [Nazwy kontraktów danych](../../../docs/framework/wcf/feature-details/data-contract-names.md)
- [Kontrakty danych zgodne z nowszymi wersjami](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)
- [Wywołania zwrotne serializacji z tolerancją dla wersji](../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md)
