---
title: 'Wskazówki: Przechowywanie wersji kontraktów danych'
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- service contracts
- best practices [WCF], data contract versioning
- Windows Communication Foundation, data contracts
ms.assetid: bf0ab338-4d36-4e12-8002-8ebfdeb346cb
ms.openlocfilehash: 33db8749656a8bb001f0a1797c77451476a126f2
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33808539"
---
# <a name="best-practices-data-contract-versioning"></a>Wskazówki: Przechowywanie wersji kontraktów danych
Ten temat zawiera najlepsze rozwiązania w zakresie tworzenia kontraktów danych, które można łatwo rozwijać, wraz z upływem czasu. Aby uzyskać więcej informacji na temat kontraktów danych, zobacz Tematy w [za pomocą kontraktów danych](../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
## <a name="note-on-schema-validation"></a>Uwagi dotyczące sprawdzania poprawności schematu  
 W dyskutować przechowywanie wersji kontraktów danych, to należy pamiętać, że schematu kontraktu danych wyeksportowane przez Windows Communication Foundation (WCF) nie ma żadnych obsługi przechowywania wersji, innego niż fakt, że elementy nie została oznaczona jako opcjonalna domyślnie.  
  
 Oznacza to, że nawet najbardziej typowych versioning scenariusz, takie jak dodawanie nowego elementu członkowskiego danych nie można zaimplementować w sposób zapewniający szybkie rozwiązanie w zakresie danego schematu. Nowsze wersje kontraktu danych (z nowego członka danych, na przykład) nie weryfikują przy użyciu starego schematu.  
  
 Istnieje jednak wiele scenariuszy, w których zgodność strict schematu nie jest wymagane. Wiele platform usług sieci Web, w tym usług WCF i XML sieci Web utworzony za pomocą programu ASP.NET, nie sprawdzania poprawności schematu domyślnie i w związku z tym tolerować dodatkowe elementy, które nie zostały opisane w schemacie. Podczas pracy z takich platform, wiele scenariuszy, w kontroli wersji są łatwiejsze do wdrożenia.  
  
 W związku z tym są dwa zestawy danych kontraktu wytycznymi wersjonowania: jeden ustawiony w scenariuszach, w których ważność strict schematu jest ważne, a inną wartość dla scenariuszy nie jest.  
  
## <a name="versioning-when-schema-validation-is-required"></a>Przechowywanie wersji, gdy jest wymagana Weryfikacja schematu  
 Jeśli schemat strict ważności jest wymagane we wszystkich kierunkach (nowe stary i starego do nowego), kontraktów danych należy traktować jako niezmienialny. Jeśli wymagane jest przechowywanie wersji, nowe kontraktu danych należy utworzyć inną nazwę lub przestrzeń nazw, i kontraktu usługi przy użyciu typu danych powinien być numerów wersji odpowiednio.  
  
 Na przykład zamówienia zakupu przetwarzania kontraktu usługi o nazwie `PoProcessing` z `PostPurchaseOrder` operacji przyjmuje parametr, który odpowiada `PurchaseOrder` kontraktu danych. Jeśli `PurchaseOrder` kontraktu musi zmienić, należy utworzyć nowego kontraktu danych, czyli `PurchaseOrder2`, która obejmuje zmiany. Następnie musi obsługiwać versioning na poziomie kontraktu usługi. Na przykład, tworząc `PostPurchaseOrder2` operacja, która przyjmuje `PurchaseOrder2` parametr, lub przez tworzenie `PoProcessing2` kontraktu usługi gdzie `PostPurchaseOrder` Trwa operacja `PurchaseOrder2` kontraktu danych.  
  
 Należy pamiętać, że zmiany w kontraktach danych, do których odwołuje się inne kontraktów danych rozszerzać do warstwy modelu usług. Na przykład w poprzednim scenariuszu `PurchaseOrder` kontraktu danych nie trzeba zmieniać. Jednak zawiera element członkowski danych klasy `Customer` kontraktu danych, który z kolei zawiera element członkowski danych klasy `Address` kontraktu danych, które muszą zostać zmienione. W takim przypadku należy utworzyć `Address2` kontrakt danych o wymagane zmiany, `Customer2` kontraktu danych, który zawiera `Address2` element członkowski danych, a `PurchaseOrder2` kontraktu danych, który zawiera `Customer2` element członkowski danych. Tak jak w przypadku poprzednich kontrakt usługi musi również być wersjonowany.  
  
 Mimo że w tych przykładach zmiany nazw (przez dodanie "2"), zaleca się zmienić przestrzeni nazw zamiast nazw przez dodanie nowych przestrzeni nazw datę lub numer wersji. Na przykład `http://schemas.contoso.com/2005/05/21/PurchaseOrder` zmienić kontraktu danych `http://schemas.contoso.com/2005/10/14/PurchaseOrder` kontraktu danych.  
  
 Aby uzyskać więcej informacji, zobacz zalecenia: [przechowywanie wersji usługi](../../../docs/framework/wcf/service-versioning.md).  
  
 Czasami musi zapewniać zgodność strict schematu dla wiadomości wysyłanych przez aplikację, ale nie może polegać na wiadomości przychodzących, które należy ściśle schematu zgodne. W takim przypadku to zagrożenie, że komunikat przychodzący może zawierać nadmiarowe dane. Nadmiarowe wartości są przechowywane i zwrócony przez usługę WCF i w związku z tym wynikiem wiadomości nieprawidłowy schemat. Aby uniknąć tego problemu, funkcja dwustronną komunikację powinna być wyłączona. Istnieją dwa sposoby, w tym celu.  
  
-   Nie należy implementować <xref:System.Runtime.Serialization.IExtensibleDataObject> interfejsu na żadnym z typów.  
  
-   Zastosuj <xref:System.ServiceModel.ServiceBehaviorAttribute> do umowy serwisowej z atrybut <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> ustawioną właściwość `true`.  
  
 Aby uzyskać więcej informacji na temat dwustronną komunikację, zobacz [kontrakty danych zgodne z nowszymi](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
## <a name="versioning-when-schema-validation-is-not-required"></a>Przechowywanie wersji podczas sprawdzania poprawności schematu nie jest wymagana  
 Rzadko wymagany jest schemat Strict zgodności. Wiele platform tolerować dodatkowe elementy, które nie dotyczą schematu. Tak długo, jak jest to dopuszczalne, pełny zestaw funkcji opisanych w [przechowywanie wersji kontraktów danych](../../../docs/framework/wcf/feature-details/data-contract-versioning.md) i [kontrakty danych zgodne z nowszymi](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md) mogą być używane. Zaleca się następujące wskazówki.  
  
 Niektóre wytycznych musi występować dokładnie tak, aby wysłać nowe wersje typu, których można oczekiwać stary lub wysyłania stare hasło, których można oczekiwać nowego. Pozostałych wskazówek nie są ściśle wymagane, ale są wymienione w tym miejscu, ponieważ mogą one mieć wpływ przyszłych wersji schematu.  
  
1.  Nie należy próbować wersji kontraktów danych przez typ dziedziczenia. Aby utworzyć nowsze wersje, Zmień na istniejący typ kontraktu danych lub utworzenia nowego typu niepowiązanego.  
  
2.  Dziedziczenie wraz z kontraktów danych jest dozwolone, pod warunkiem że dziedziczenia nie jest używana jako mechanizm kontroli wersji, a niektóre zasady zostaną wykonane. Jeśli typ pochodzi z określonego typu podstawowego, nie należy wprowadzać on pochodzić z innym typem bazowym w przyszłych wersjach (o ile nie ma tych samych danych kontraktu). Istnieje jeden wyjątek to: typ można wstawiać do hierarchii między typu kontraktu danych, a jego typ podstawowy, ale tylko wtedy, gdy nie zawiera elementów członkowskich danych z nazwy taki sam jak inne elementy członkowskie w wszystkie możliwe wersje inne typy w hierarchii. Ogólnie rzecz biorąc, przy użyciu elementy członkowskie danych pod tą samą nazwą na różnych poziomach o tej samej hierarchii dziedziczenia może prowadzić do problemów poważne przechowywanie wersji i należy unikać.  
  
3.  Począwszy od pierwszej wersji kontraktu danych, zawsze zaimplementować <xref:System.Runtime.Serialization.IExtensibleDataObject> umożliwiające dwustronną komunikację. Aby uzyskać więcej informacji, zobacz [kontrakty danych zgodne z nowszymi](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md). Bez stosowania tego interfejsu wydaniu wersji co najmniej jednego typu należy wdrożyć go w następnej wersji tego typu.  
  
4.  W nowszych wersjach nie należy zmieniać nazwy kontraktu danych lub przestrzeni nazw. Jeśli zmiana nazwy lub przestrzeni nazw typu podstawowego kontraktu danych, upewnij się zachować nazwie kontraktu danych i przestrzeni nazw przy użyciu odpowiednich mechanizmów, takich jak <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> właściwość <xref:System.Runtime.Serialization.DataContractAttribute>. Aby uzyskać więcej informacji o nazwach, zobacz [nazwy kontraktów danych](../../../docs/framework/wcf/feature-details/data-contract-names.md).  
  
5.  W nowszych wersjach nie należy zmieniać nazwy żadnych elementów członkowskich danych. Jeśli zmiana nazwy pola, właściwości lub zdarzenia podstawowy element członkowski danych, użyj `Name` właściwość <xref:System.Runtime.Serialization.DataMemberAttribute> zachować nazwę istniejącego elementu członkowskiego danych.  
  
6.  W nowszych wersjach nie należy zmieniać typu pola, właściwości lub zdarzenia podstawowy element członkowski danych w taki sposób, że dane wynikowe kontraktu tego zmian elementów członkowskich danych. Należy pamiętać, że typy interfejsów są równoważne <xref:System.Object> na potrzeby określania kontraktu oczekiwane dane.  
  
7.  W nowszych wersjach, nie należy zmieniać kolejność istniejące elementy członkowskie danych przez dostosowanie wartości właściwości <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> właściwość <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutu.  
  
8.  W nowszych wersjach można dodać nowe elementy członkowskie danych. One zawsze należy wykonać następujące czynności:  
  
    1.  <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> Właściwość zawsze należy pozostawić wartość domyślną `false`.  
  
    2.  Jeśli wartość domyślną równą `null` lub zero dla elementu członkowskiego jest nie do przyjęcia, metody wywołania zwrotnego należy podawać przy użyciu <xref:System.Runtime.Serialization.OnDeserializingAttribute> do zapewniania domyślnego uzasadnione, w przypadku, gdy element członkowski nie jest obecny w strumienia przychodzącego. Aby uzyskać więcej informacji na temat wywołania zwrotnego, zobacz [wywołania zwrotne serializacji z tolerancją dla wersji](../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md).  
  
    3.  `Order` Właściwość `DataMemberAttribute` powinien być używany do upewnij się, że wszystkie elementy członkowskie nowo dodanych danych zostaną wyświetlone po istniejące elementy członkowskie danych. Zalecaną metodą zrobić to wygląda następująco: żaden z elementów członkowskich danych w pierwszej wersji kontraktu danych powinien nie ma ich `Order` zestawu właściwości. Wszystkie elementy członkowskie danych dodany w wersji 2 kontraktu danych powinny mieć swoje `Order` właściwością o wartości 2. Wszystkie elementy członkowskie danych dodany w wersji 3 kontraktu danych powinny mieć ich `Order` na 3 i tak dalej. Dopuszcza się ma więcej niż jeden element członkowski danych takie same `Order` numer.  
  
9. Nie usuwaj elementy członkowskie danych w nowszych wersjach, nawet wtedy, gdy <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> właściwości pozostawało na jego domyślna właściwość `false` w poprzednich wersjach.  
  
10. Nie zmieniaj `IsRequired` właściwość żadnych istniejących elementów członkowskich danych z wersji do wersji.  
  
11. Dla wymaganych elementów członkowskich danych (jeżeli `IsRequired` jest `true`), nie należy zmieniać `EmitDefaultValue` właściwości z wersji do wersji.  
  
12. Nie należy próbować tworzyć hierarchie rozgałęzione przechowywania wersji. Oznacza to, że zawsze należy ścieżką w co najmniej jeden kierunek z dowolnej wersji do innych wersji przy użyciu tylko zmiany dozwolone przez te wytyczne.  
  
     Na przykład, jeśli wersja 1 kontraktu danych osoby zawiera tylko nazwa członka danych, nie należy tworzyć 2a wersja kontraktu dodanie tylko wieku element członkowski i wersji 2b dodanie tylko z elementem członkowskim adresu. Będzie 2a 2b wymagałoby usunąć wieku i dodać adres; Przechodzenie w innym kierunku pociąga adres usuwania i dodawania wieku. Usunięcie elementów członkowskich nie jest dozwolone przez te wytyczne.  
  
13. Zwykle nie należy tworzyć nowych podtypów istniejące typy kontraktu danych w nowej wersji aplikacji. Ponadto nie należy tworzyć nowych kontraktów danych, które są używane zamiast dane, które elementy członkowskie zadeklarowany jako obiekt lub typów interfejsów. Tworzenie tych nowych klas jest dozwolone tylko wtedy, gdy wiesz, że można dodać nowych typów do listy znanych typów wszystkich wystąpień aplikacji stary. Na przykład w aplikacji w wersji 1, konieczne może być typu z książką kontraktu danych LibraryItem i danych gazecie kontraktu podtypów. LibraryItem będzie zmuszony listę znanych typów, która zawiera książki i gazecie. Załóżmy, że teraz dodać typ magazynu w wersji 2, która jest podtypem LibraryItem. Po wysłaniu wystąpienia magazynu w wersji 2 do wersji 1 kontraktu danych magazynu nie odnaleziono listy znanych typów i jest zgłaszany wyjątek.  
  
14. Nie należy dodawać lub usuwać elementy członkowskie wyliczenia między wersjami. Należy również nie zmienisz elementy członkowskie wyliczenia, chyba że używana jest właściwość Name na `EnumMemberAttribute` atrybutu, aby zapewnić ich nazwy w modelu kontraktu danych, takie same.  
  
15. Kolekcje są wymienne w modelu kontraktu danych, zgodnie z opisem w [typy kolekcji w kontraktach danych](../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md). Dzięki temu precyzyjną elastyczność. Jednak należy się upewnić, że nie mogą przypadkowo zmienisz typ kolekcji w innych niż wymienne sposób od poprzedniej wersji. Na przykład nie należy zmieniać z kolekcji bez dostosowania (czyli bez `CollectionDataContractAttribute` atrybut) dostosowane jedno lub dostosowany zbiór aby stworzyć plik bez dostosowania. Ponadto nie należy zmieniać właściwości na `CollectionDataContractAttribute` od wersji. Dozwolonych jedyna różnica polega na dodaniu właściwości Name i Namespace Jeśli nazwę lub przestrzeń nazw podstawowy typ kolekcji został zmieniony, należy udostępnić jego dane umowy, nazwę i przestrzeń nazw takie same jak w poprzedniej wersji.  
  
 Niektóre z wymienionych w tym miejscu można bezpiecznie zignorować podczas specjalne okoliczności. Upewnij się, że w pełni zrozumieć serializacji, deserializacji i mechanizmach schematu przed odejście od wytyczne.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A>  
 <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>  
 <xref:System.Runtime.Serialization.IExtensibleDataObject>  
 <xref:System.ServiceModel.ServiceBehaviorAttribute>  
 <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A>  
 <xref:System.Runtime.Serialization.ExtensionDataObject>  
 <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
 [Używanie kontraktów danych](../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [Przechowywanie wersji kontraktów danych](../../../docs/framework/wcf/feature-details/data-contract-versioning.md)  
 [Nazwy kontraktów danych](../../../docs/framework/wcf/feature-details/data-contract-names.md)  
 [Kontrakty danych zgodne z nowszymi wersjami](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)  
 [Wywołania zwrotne serializacji z tolerancją dla wersji](../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md)
