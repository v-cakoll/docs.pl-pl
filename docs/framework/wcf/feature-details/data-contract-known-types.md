---
title: "Znane typy kontraktów danych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], known types
- KnownTypeAttribute [WCF]
- KnownTypes [WCF]
ms.assetid: 1a0baea1-27b7-470d-9136-5bbad86c4337
caps.latest.revision: "42"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7420b2c47356eee526c46e97d35e6d3cc474797e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="data-contract-known-types"></a>Znane typy kontraktów danych
<xref:System.Runtime.Serialization.KnownTypeAttribute> Klasa pozwala na określenie z wyprzedzeniem, typów, które powinny zostać uwzględnione w brany pod uwagę podczas deserializacji. Na przykład pracy, zobacz [znane typy](../../../../docs/framework/wcf/samples/known-types.md) przykład.  
  
 Zwykle podczas przekazywania parametrów i zwracanych wartości między klientem a usługą, oba punkty końcowe udostępnianie wszystkie kontrakty danych z danych przekazywanych. Jednak to nie jest to w następujących okolicznościach:  
  
-   Kontrakt danych wysłanych jest pochodną kontraktu oczekiwane dane. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]sekcja o dziedziczenia w [równoważność kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)). W takim przypadku przesyłanych danych nie ma tych samych danych kontraktu, zgodnie z oczekiwaniami odbierania punktu końcowego.  
  
-   Deklarowany typ informacji przekazywanych jest interfejsem, w przeciwieństwie do klasy, struktury lub wyliczenia. W związku z tym ona nie być znane z wyprzedzeniem typ implementuje interfejs faktycznie jest wysyłany, a w związku z tym odbierania punktu końcowego nie może wcześniej określić kontraktu danych przesyłanych danych.  
  
-   Deklarowany typ informacji przekazywanych jest <xref:System.Object>. Ponieważ każdy typ dziedziczy z <xref:System.Object>i go nie może być znane z wyprzedzeniem typu faktycznie jest wysyłane, odbierania punktu końcowego nie może określić wcześniej kontraktu danych dla przekazywanych danych. Jest to szczególnych przypadkach pierwszego elementu: co kontraktu danych pochodzi od domyślnej, generowany dla kontraktu danych puste <xref:System.Object>.  
  
-   Niektóre typy, które obejmują [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy, mieć elementów członkowskich, które znajdują się w jednej z poprzednich trzech kategorii. Na przykład <xref:System.Collections.Hashtable> używa <xref:System.Object> do przechowywania rzeczywistych obiektów w tablicy skrótów. Podczas serializowania te typy, po stronie odbierającej nie można ustalić wcześniej kontraktu danych dla tych elementów członkowskich.  
  
## <a name="the-knowntypeattribute-class"></a>Klasa KnownTypeAttribute  
 Po odebraniu danych odbierania punktu końcowego, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] środowiska uruchomieniowego podejmuje próbę deserializacji danych do wystąpienia typu wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR). Typ, który zostanie uruchomiony do deserializacji jest wybierany przez pierwsze badanie kontraktu komunikatu przychodzącego określenie danych, do którego zawartość komunikatu jest zgodna z. Aparat deserializacji następnie próbuje odnaleźć typu CLR, który implementuje kontrakt danych zgodne z treść komunikatu. Zestaw typów kandydujących, które umożliwia aparat deserializacji w trakcie tego procesu jest określana jako zestaw Deserializator "znanych typów."  
  
 Jednym ze sposobów let aparat deserializacji wiedzieć o typie polega na użyciu <xref:System.Runtime.Serialization.KnownTypeAttribute>. Ten atrybut nie można zastosować do poszczególnych danych elementów członkowskich, tylko na typy kontraktu danych całego. Ten atrybut jest stosowany do *typu zewnętrznego* które może być klasą lub strukturą. W jego najbardziej podstawowa użycia stosowania ten atrybut określa typ jako "znanego typu". Powoduje to znanego typu jako część zestawu znanych typów, gdy obiekt typu zewnętrznego lub deserializacji dowolny obiekt określony przez jego elementów członkowskich. Więcej niż jeden <xref:System.Runtime.Serialization.KnownTypeAttribute> atrybut można stosować do tego samego typu.  
  
## <a name="known-types-and-primitives"></a>Znane typy i elementy podstawowe  
 Typy pierwotne, jak również niektórych typów traktowane jako typów podstawowych (na przykład <xref:System.DateTime> i <xref:System.Xml.XmlElement>) są zawsze "Nieznany" i nigdy nie muszą być dodane przez ten mechanizm. Jednak tablice typów pierwotnych muszą być jawnie dodane. Większość kolekcji są traktowane jako równoważne tablic. (Inne niż ogólne kolekcje są traktowane jako równoważne tablice <xref:System.Object>). Na przykład za pomocą podstawowych, tablice pierwotne i pierwotny kolekcji, zobacz przykład 4.  
  
> [!NOTE]
>  W odróżnieniu od innych typów pierwotnych <xref:System.DateTimeOffset> struktury nie jest znanym typem domyślnie, dlatego należy ręcznie dodać do listy znanych typów.  
  
## <a name="examples"></a>Przykłady  
 W poniższych przykładach pokazano <xref:System.Runtime.Serialization.KnownTypeAttribute> klasy w użyciu.  
  
#### <a name="example-1"></a>Przykład 1  
 Istnieją trzy klasy z relacji dziedziczenia.  
  
 [!code-csharp[C_KnownTypeAttribute#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#1)]
 [!code-vb[C_KnownTypeAttribute#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#1)]  
  
 Następujące `CompanyLogo` klasy może być Zserializowany, ale nie można przeprowadzić deserializacji Jeśli `ShapeOfLogo` elementu członkowskiego jest ustawiona jako `CircleType` lub `TriangleType` obiektu, ponieważ aparat deserializacji nie rozpoznaje wszystkie typy z nazw kontraktu danych " Koło"lub"Trójkąt."  
  
 [!code-csharp[C_KnownTypeAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#2)]
 [!code-vb[C_KnownTypeAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#2)]  
  
 Prawidłowy sposób zapisu `CompanyLogo` typu przedstawiono w poniższym kodzie.  
  
 [!code-csharp[C_KnownTypeAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#3)]
 [!code-vb[C_KnownTypeAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#3)]  
  
 Zawsze, gdy typu zewnętrznego `CompanyLogo2` jest poddawany deserializacji aparat deserializacji wie o `CircleType` i `TriangleType` i dlatego jest w stanie znaleźć pasujące typy kontraktów danych "Okrąg" i "Trójkąt".  
  
#### <a name="example-2"></a>Przykład 2  
 W poniższym przykładzie nawet jeśli zarówno `CustomerTypeA` i `CustomerTypeB` ma `Customer` kontraktu danych, wystąpienia `CustomerTypeB` jest tworzony po każdej zmianie `PurchaseOrder` jest deserializacji, ponieważ tylko `CustomerTypeB` jest znana Aparat wykonywania deserializacji.  
  
 [!code-csharp[C_KnownTypeAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#4)]
 [!code-vb[C_KnownTypeAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#4)]  
  
#### <a name="example-3"></a>Przykład 3  
 W poniższym przykładzie <xref:System.Collections.Hashtable> przechowuje zawartością wewnętrznie jako <xref:System.Object>. Aby pomyślnie zdeserializowanie tablicy skrótów, aparat deserializacji trzeba znać zestaw możliwych typów, które mogą wystąpić istnieje. W takim przypadku wiemy z wyprzedzeniem jedynie `Book` i `Magazine` obiekty są przechowywane w `Catalog`, więc te są dodawane przy użyciu <xref:System.Runtime.Serialization.KnownTypeAttribute> atrybutu.  
  
 [!code-csharp[C_KnownTypeAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#5)]
 [!code-vb[C_KnownTypeAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#5)]  
  
#### <a name="example-4"></a>Przykład 4  
 W poniższym przykładzie kontraktu danych przechowuje numer i operacji do wykonania na liczbę. `Numbers` Elementu członkowskiego danych może być liczbą całkowitą, tablica liczb całkowitych, lub <xref:System.Collections.Generic.List%601> zawierający liczb całkowitych.  
  
> [!CAUTION]
>  Działa tylko po stronie klienta jeśli SVCUTIL. EXE służy do generowania serwer proxy usługi WCF. NARZĘDZIA SVCUTIL. EXE pobiera metadane z usługi, w tym wszystkie znane typy. Bez tych informacji klient nie będzie mógł zdeserializować typów.  
  
 [!code-csharp[C_KnownTypeAttribute#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#6)]
 [!code-vb[C_KnownTypeAttribute#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#6)]  
  
 To jest kod aplikacji.  
  
 [!code-csharp[C_KnownTypeAttribute#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#7)]
 [!code-vb[C_KnownTypeAttribute#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#7)]  
  
## <a name="known-types-inheritance-and-interfaces"></a>Znane typy, dziedziczenia i interfejsy  
 Gdy jest skojarzony z określonego typu za pomocą znanego typu `KnownTypeAttribute` atrybutu, znany typ jest także powiązany z wszystkich typów pochodnych danego typu. Na przykład zobacz następujący kod.  
  
 [!code-csharp[C_KnownTypeAttribute#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#8)]
 [!code-vb[C_KnownTypeAttribute#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#8)]  
  
 `DoubleDrawing` Nie wymaga klasy `KnownTypeAttribute` atrybutu `Square` i `Circle` w `AdditionalShape` pola, ponieważ klasa podstawowa (`Drawing`) ma już te atrybuty stosowane.  
  
 Znanych typów może być skojarzony tylko z klas i struktur, nie interfejsy.  
  
## <a name="known-types-using-open-generic-methods"></a>Znane typy przy użyciu Otwórz metody ogólne  
 Może być konieczne dodanie typem ogólnym jako znanego typu. Jednak to otwarty typ ogólny nie mogą być przekazywane jako parametr `KnownTypeAttribute` atrybutu.  
  
 Ten problem można rozwiązać przy użyciu alternatywny mechanizm: napisanie metody, która zwraca listę typów do dodania do kolekcji znanych typów. Nazwa metody jest następnie określony jako argument będący ciągiem `KnownTypeAttribute` atrybutu z powodu pewne ograniczenia.  
  
 Metoda musi istnieć w typie, do którego `KnownTypeAttribute` atrybut jest stosowany, musi być statyczna, musisz zaakceptować bez parametrów i musi zwracać obiekt, który można przypisać do <xref:System.Collections.IEnumerable> z <xref:System.Type>.  
  
 Nie można łączyć `KnownTypeAttribute` atrybutu z nazwą metody i `KnownTypeAttribute` atrybuty z typami rzeczywistymi do tego samego typu. Ponadto nie można zastosować więcej niż jeden `KnownTypeAttribute` nazwą metody do tego samego typu.  
  
 Zobacz następujące klasy.  
  
 [!code-csharp[C_KnownTypeAttribute#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#9)]
 [!code-vb[C_KnownTypeAttribute#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#9)]  
  
 `theDrawing` Pole zawiera wystąpień klasy generycznej `ColorDrawing` i klasy ogólnej `BlackAndWhiteDrawing`, które dziedziczą z klasy ogólnej `Drawing`. Zwykle oba muszą zostać dodane do znanych typów, ale następujący ciąg nie jest prawidłową składnię dla atrybutów.  
  
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
  
 W związku z tym należy utworzyć metody w celu te typy zwracane. Prawidłowy sposób można zapisać tego typu, następnie jest wyświetlany w poniższym kodzie.  
  
 [!code-csharp[C_KnownTypeAttribute#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#10)]
 [!code-vb[C_KnownTypeAttribute#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#10)]  
  
## <a name="additional-ways-to-add-known-types"></a>Dodatkowe sposoby dodawania znanych typów  
 Ponadto można dodać za pomocą pliku konfiguracji znanych typów. Jest to przydatne, gdy nie kontroli typ, który wymaga znanych typów dla odpowiednich deserializacji, takich jak przy użyciu innej firmy podczas wpisywania bibliotek z [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
 Następujący plik konfiguracji pokazano, jak określić znanego typu w pliku konfiguracji.  
  
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
  
 W tej konfiguracji pliku typu kontraktu danych o nazwie `MyCompany.Library.Shape` jest zadeklarowana, aby mieć `MyCompany.Library.Circle` jako znanego typu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.Serialization.KnownTypeAttribute>  
 <xref:System.Collections.Hashtable>  
 <xref:System.Object>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A>  
 [Znane typy](../../../../docs/framework/wcf/samples/known-types.md)  
 [Równoważność kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)  
 [Projektowanie kontraktów usług](../../../../docs/framework/wcf/designing-service-contracts.md)
