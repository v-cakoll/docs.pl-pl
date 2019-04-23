---
title: Znane typy kontraktów danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], known types
- KnownTypeAttribute [WCF]
- KnownTypes [WCF]
ms.assetid: 1a0baea1-27b7-470d-9136-5bbad86c4337
ms.openlocfilehash: bedf35544454a32ff13856a072779cd70723e989
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59129626"
---
# <a name="data-contract-known-types"></a>Znane typy kontraktów danych
<xref:System.Runtime.Serialization.KnownTypeAttribute> Klasy pozwala na określenie z wyprzedzeniem, typy, które należy wziąć pod uwagę podczas deserializacji. Aby uzyskać przykład pracy, zobacz [znane typy](../../../../docs/framework/wcf/samples/known-types.md) przykład.  
  
 Zwykle podczas przekazywania parametrów i zwracanych wartości między klientem a usługą, oba punkty końcowe współdziel kontraktów danych danych przekazywanych. Jednak to nie jest wymagane w następujących okolicznościach:  
  
-   Kontrakt przesłanych danych jest tworzony na podstawie umowy oczekiwanych danych. Aby uzyskać więcej informacji, zobacz sekcję dotyczącą dziedziczenie w [równoważność kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)). W takim przypadku przesyłanych danych ma te same dane Umowę zgodnie z oczekiwaniami, odbieranie punktu końcowego.  
  
-   Deklarowany typ informacji przekazywanych jest interfejs, w przeciwieństwie do klasy, struktury lub wyliczenia. W związku z tym go nie może być znane z wyprzedzeniem typu czy implementuje interfejs są faktycznie przesyłane i w związku z tym, odbieranie punktu końcowego ustalić wcześniej kontraktu danych dla przesyłanych danych.  
  
-   Deklarowany typ informacji przekazywanych jest <xref:System.Object>. Ponieważ każdy typ dziedziczy z <xref:System.Object>i go nie może być znane z wyprzedzeniem typy są faktycznie przesyłane, odbieranie punkt końcowy nie może ustalić z wyprzedzeniem kontraktu danych dla przesyłanych danych. To jest szczególnym przypadkiem pierwszego elementu: Co kontraktu danych pochodzi z domyślnej umowy puste dane, który jest generowany dla <xref:System.Object>.  
  
-   Niektóre typy, które obejmują [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy, mieć elementy członkowskie, które należą do jednej z trzech powyższych kategorii. Na przykład <xref:System.Collections.Hashtable> używa <xref:System.Object> przechowywanie rzeczywistych obiektów w tablicy skrótów. Podczas serializacji tych typów, po stronie odbierającej nie może ustalić z wyprzedzeniem kontraktu danych dla tych członków.  
  
## <a name="the-knowntypeattribute-class"></a>Klasa KnownTypeAttribute  
 Dane odebrane na odbieranie punktu końcowego, środowisko wykonawcze programu WCF próbuje zdeserializowanie danych do wystąpienia typu wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR). Typ, który zostanie uruchomiony do deserializacji jest wybierany sprawdzając pierwszego komunikatu przychodzącego do ustalenia danych umowę które treści wiadomości są zgodne. Następnie aparat deserializacji próbuje odnaleźć typu CLR, który implementuje kontraktu danych, zgodny z treści wiadomości. Zestaw typów Release candidate, które umożliwiają aparatu deserializacji w trakcie tego procesu jest określany jako zestaw Deserializator "znanych typów."  
  
 Jednym ze sposobów, aby umożliwić aparatu deserializacji wiedzieć o typie jest przy użyciu <xref:System.Runtime.Serialization.KnownTypeAttribute>. Nie można zastosować atrybut do poszczególnych elementów członkowskich danych, tylko typy kontraktu danych całego. Atrybut jest stosowany do *typu zewnętrznego* , może być klasą lub strukturą. W jej najprostsze użycie stosowanie atrybutu określa typ jako "znanych type". Powoduje to, że znany typ jako część zestawu znanych typów, zawsze wtedy, gdy obiekt typu zewnętrznego lub wykonać deserializacji dowolny obiekt określony przez jego członków. Więcej niż jeden <xref:System.Runtime.Serialization.KnownTypeAttribute> atrybut można stosować do tego samego typu.  
  
## <a name="known-types-and-primitives"></a>Znane typy i elementy podstawowe  
 Typy pierwotne, a także niektórych typów traktowane jako elementy podstawowe (na przykład <xref:System.DateTime> i <xref:System.Xml.XmlElement>) są zawsze "Nieznany" i nigdy nie muszą być dodane za pomocą tego mechanizmu. Jednak tablic prymitywnych typów muszą być dodane jawnie. Większość kolekcji są uważane za równoważne do tablic. (Inne niż ogólne kolekcje są uważane za równoważne do tablic <xref:System.Object>). Na przykład przy użyciu podstawowych, pierwotnych tablice i kolekcje pierwotnych, zobacz przykład 4.  
  
> [!NOTE]
>  W przeciwieństwie do innych typów pierwotnych <xref:System.DateTimeOffset> struktura nie jest znany typ domyślnie, dlatego należy ręcznie dodać do listy znanych typów.  
  
## <a name="examples"></a>Przykłady  
 W poniższych przykładach pokazano <xref:System.Runtime.Serialization.KnownTypeAttribute> klasy w użyciu.  
  
#### <a name="example-1"></a>Przykład 1  
 Istnieją trzy klasy przy użyciu relacji dziedziczenia.  
  
 [!code-csharp[C_KnownTypeAttribute#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#1)]
 [!code-vb[C_KnownTypeAttribute#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#1)]  
  
 Następujące `CompanyLogo` klasy może być Zserializowany, ale nie można zdeserializować, jeśli `ShapeOfLogo` element członkowski jest ustawiany na `CircleType` lub `TriangleType` obiektu, ponieważ aparat deserializacji nie rozpoznaje wszystkie typy z nazw kontraktu danych " Koło"lub"Trójkąt".  
  
 [!code-csharp[C_KnownTypeAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#2)]
 [!code-vb[C_KnownTypeAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#2)]  
  
 Poprawny sposób zapisu `CompanyLogo` typu jest wyświetlana w poniższym kodzie.  
  
 [!code-csharp[C_KnownTypeAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#3)]
 [!code-vb[C_KnownTypeAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#3)]  
  
 Zawsze, gdy typu zewnętrznego `CompanyLogo2` jest przeprowadzona, aparat deserializacji wie o `CircleType` i `TriangleType` i dlatego jest w stanie znaleźć pasujące typy kontraktów danych "Koło" i "Trójkąt".  
  
#### <a name="example-2"></a>Przykład 2  
 W poniższym przykładzie mimo że zarówno `CustomerTypeA` i `CustomerTypeB` mają `Customer` kontraktu danych, wystąpienie `CustomerTypeB` jest tworzony w każdym przypadku, gdy `PurchaseOrder` jest przeprowadzona, ponieważ tylko `CustomerTypeB` znanego Aparat deserializacji.  
  
 [!code-csharp[C_KnownTypeAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#4)]
 [!code-vb[C_KnownTypeAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#4)]  
  
#### <a name="example-3"></a>Przykład 3  
 W poniższym przykładzie <xref:System.Collections.Hashtable> jej zawartość są przechowywane wewnętrznie jako <xref:System.Object>. Aby pomyślnie zdeserializowanie tablicy skrótów, aparat deserializacji trzeba znać zestaw możliwych typów, które mogą wystąpić, istnieje. W tym przypadku wiemy z wyprzedzeniem tylko `Book` i `Magazine` obiekty są przechowywane w `Catalog`, więc te są dodawane przy użyciu <xref:System.Runtime.Serialization.KnownTypeAttribute> atrybutu.  
  
 [!code-csharp[C_KnownTypeAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#5)]
 [!code-vb[C_KnownTypeAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#5)]  
  
#### <a name="example-4"></a>Przykład 4  
 W poniższym przykładzie kontraktu danych przechowuje liczbę i operacji do wykonania na liczbę. `Numbers` Element członkowski danych może być liczbą całkowitą, tablicy liczb całkowitych, lub <xref:System.Collections.Generic.List%601> zawierający liczb całkowitych.  
  
> [!CAUTION]
>  Ta opcja zadziała tylko po stronie klienta Jeśli narzędzia SVCUTIL. Plik EXE jest używany do generowania serwera proxy usługi WCF. NARZĘDZIA SVCUTIL. Plik EXE pobiera metadane z usługi, w tym wszystkie znane typy. Bez tych informacji klienta nie będzie można wykonać deserializacji typów.  
  
 [!code-csharp[C_KnownTypeAttribute#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#6)]
 [!code-vb[C_KnownTypeAttribute#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#6)]  
  
 Jest to kod aplikacji.  
  
 [!code-csharp[C_KnownTypeAttribute#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#7)]
 [!code-vb[C_KnownTypeAttribute#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#7)]  
  
## <a name="known-types-inheritance-and-interfaces"></a>Znanych typów, dziedziczenie i interfejsy  
 Jeśli znany typ jest skojarzony z określonego typu, w którym używana jest `KnownTypeAttribute` , znany typ jest również skojarzony z wszystkich typów pochodnych tego typu. Zobacz na przykład, poniższy kod.  
  
 [!code-csharp[C_KnownTypeAttribute#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#8)]
 [!code-vb[C_KnownTypeAttribute#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#8)]  
  
 `DoubleDrawing` Klasy nie wymaga `KnownTypeAttribute` atrybutu `Square` i `Circle` w `AdditionalShape` pola, ponieważ klasa bazowa (`Drawing`) ma już te atrybuty zastosowane.  
  
 Znane typy mogą zostać skojarzone tylko z klas i struktur, interfejsów nie.  
  
## <a name="known-types-using-open-generic-methods"></a>Znane typy, za pomocą otwartych metod ogólnych  
 Może być konieczne dodanie typem ogólnym jako znanego typu. Jednak to otwarty typ ogólny nie można przekazać jako parametru `KnownTypeAttribute` atrybutu.  
  
 Ten problem można rozwiązać za pomocą alternatywny mechanizm: Napisanie metody, która zwraca listę typów, aby dodać do kolekcji znanych typów. Nazwa metody jest następnie określony jako argument ciągu `KnownTypeAttribute` atrybut ze względu na pewne ograniczenia.  
  
 Metoda musi istnieć na typ, do którego `KnownTypeAttribute` atrybut jest stosowany, muszą być statyczne, należy zaakceptować żadnych parametrów i musi zwracać obiekt, który można przypisać do <xref:System.Collections.IEnumerable> z <xref:System.Type>.  
  
 Nie można łączyć `KnownTypeAttribute` atrybutu o nazwie metody i `KnownTypeAttribute` atrybuty z typami rzeczywistymi do tego samego typu. Ponadto nie można zastosować więcej niż jedną `KnownTypeAttribute` nazwą metody do tego samego typu.  
  
 Zobacz następujące klasy.  
  
 [!code-csharp[C_KnownTypeAttribute#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#9)]
 [!code-vb[C_KnownTypeAttribute#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#9)]  
  
 `theDrawing` Pole zawiera wystąpienia klasy generycznej `ColorDrawing` i klasę ogólną `BlackAndWhiteDrawing`, które dziedziczą z klasy rodzajowej `Drawing`. Normalnie oba muszą zostać dodane do znanych typów, ale poniżej nie jest prawidłową składnię dla atrybutów.  
  
```csharp  
// Invalid syntax for attributes:  
// [KnownType(typeof(ColorDrawing<T>))]  
// [KnownType(typeof(BlackAndWhiteDrawing<T>))]  
```  
  
```vb  
' Invalid syntax for attributes:  
' <KnownType(GetType(ColorDrawing(Of T))), _  
' KnownType(GetType(BlackAndWhiteDrawing(Of T)))>  
```  
  
 W związku z tym metoda musi zostać utworzona do tych typów zwracanych. Poprawny sposób pisania tego typu, następnie jest wyświetlany w poniższym kodzie.  
  
 [!code-csharp[C_KnownTypeAttribute#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#10)]
 [!code-vb[C_KnownTypeAttribute#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#10)]  
  
## <a name="additional-ways-to-add-known-types"></a>Dodatkowe sposoby dodawania znane typy  
 Ponadto można dodać znanych typów za pomocą pliku konfiguracji. Jest to przydatne, gdy nie mają kontroli nad typ, który wymaga znanych typów do odpowiednich deserializacji, np. gdy przy użyciu innych firm wpisz biblioteki za pomocą programu Windows Communication Foundation (WCF).  
  
 Następujący plik konfiguracji pokazuje sposób określania znanego typu w pliku konfiguracji.  
  
 `<configuration>`  
  
 `<system.runtime.serialization>`  
  
 `<dataContractSerializer>`  
  
 `<declaredTypes>`  
  
 `<add type="MyCompany.Library.Shape,`  
  
 `MyAssembly, Version=2.0.0.0, Culture=neutral,`  
  
 `PublicKeyToken=XXXXXX, processorArchitecture=MSIL">`  
  
 `<knownType type="MyCompany.Library.Circle,`  
  
 `MyAssembly, Version=2.0.0.0, Culture=neutral,`  
  
 `PublicKeyToken=XXXXXX, processorArchitecture=MSIL"/>`  
  
 `</add>`  
  
 `</declaredTypes>`  
  
 `</dataContractSerializer>`  
  
 `</system.runtime.serialization>`  
  
 `</configuration>`  
  
 W tej konfiguracji pliku typu kontraktu danych, nazywane `MyCompany.Library.Shape` jest zadeklarowany ma `MyCompany.Library.Circle` jako znanego typu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Serialization.KnownTypeAttribute>
- <xref:System.Collections.Hashtable>
- <xref:System.Object>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A>
- [Znane typy](../../../../docs/framework/wcf/samples/known-types.md)
- [Równoważność kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [Projektowanie kontraktów usług](../../../../docs/framework/wcf/designing-service-contracts.md)
