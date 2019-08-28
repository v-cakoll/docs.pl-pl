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
ms.openlocfilehash: 2ab0a41e87a9b14d1beac9fb0c39586f0ea16a4a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040193"
---
# <a name="data-contract-known-types"></a>Znane typy kontraktów danych
<xref:System.Runtime.Serialization.KnownTypeAttribute> Klasa pozwala określić z wyprzedzeniem typy, które powinny być brane pod uwagę podczas deserializacji. Aby zapoznać się z przykładem roboczym, zobacz przykład [znanych typów](../../../../docs/framework/wcf/samples/known-types.md) .  
  
 Zwykle podczas przekazywania parametrów i zwracanych wartości między klientem a usługą oba punkty końcowe współdzielą wszystkie Kontrakty danych do przesłania. Nie dotyczy to jednak następujących sytuacji:  
  
- Kontrakt wysłanych danych pochodzi od oczekiwanego kontraktu danych. Aby uzyskać więcej informacji, zapoznaj się z sekcją dotyczącej dziedziczenia w obszarze [równoważności kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md). W takim przypadku przesyłane dane nie mają tego samego kontraktu danych zgodnie z oczekiwaniami w punkcie końcowym odbioru.  
  
- Zadeklarowany typ dla przekazywanych informacji jest interfejsem, a nie z klasą, strukturą lub wyliczeniem. W związku z tym nie może być znany z wyprzedzeniem, który typ implementujący interfejs jest faktycznie wysyłany i dlatego punkt końcowy odbiorcy nie może określić z wyprzedzeniem kontraktu danych dla przesyłanych danych.  
  
- Zadeklarowany typ dla przekazywanych informacji to <xref:System.Object>. Ponieważ każdy typ dziedziczy z <xref:System.Object>i nie może być znany z wyprzedzeniem, który jest faktycznie wysyłany, punkt końcowy odbiorcy nie może określić z wyprzedzeniem kontraktu danych dla przesyłanych danych. Jest to specjalny przypadek pierwszego elementu: Wszystkie Kontrakty danych pochodzą z domyślnego, pustego kontraktu danych wygenerowanego dla <xref:System.Object>.  
  
- Niektóre typy, które obejmują .NET Framework typy, mają składowe, które znajdują się w jednej z powyższych trzech kategorii. Na przykład program <xref:System.Collections.Hashtable> używa <xref:System.Object> do przechowywania rzeczywistych obiektów w tabeli skrótów. Podczas serializacji tych typów Strona otrzymująca nie może określić z wyprzedzeniem kontraktu danych dla tych członków.  
  
## <a name="the-knowntypeattribute-class"></a>Klasa KnownTypeattribute  
 Gdy dane docierają do odbiorczego punktu końcowego, środowisko uruchomieniowe WCF próbuje zdeserializować dane do wystąpienia aparatu plików wykonywalnych języka wspólnego (CLR). Typ, który jest skonkretyzowany dla deserializacji jest wybierany przez pierwsze Inspekcja komunikatu przychodzącego, aby określić kontrakt danych, do którego zawartość wiadomości jest zgodna. Aparat deserializacji próbuje znaleźć typ CLR, który implementuje kontrakt danych zgodny z zawartością wiadomości. Zestaw typów kandydujących, które mogą być używane przez aparat deserializacji w trakcie tego procesu, jest nazywany zestawem "znanych typów".  
  
 Jednym ze sposobów na umożliwienie aparatowi deserializacji informacji o typie jest użycie <xref:System.Runtime.Serialization.KnownTypeAttribute>. Nie można zastosować atrybutu do poszczególnych składowych danych, tylko do typów kontraktu danych całych. Ten atrybut jest stosowany do *typu zewnętrznego* , który może być klasą lub strukturą. W najbardziej podstawowym użyciu, zastosowanie atrybutu określa typ jako "znany typ". Powoduje to, że znany typ jest częścią zestawu znanych typów za każdym razem, gdy obiekt typu zewnętrznego lub dowolnego obiektu, do którego odwołuje się jego składowe, jest deserializowany. Do tego samego <xref:System.Runtime.Serialization.KnownTypeAttribute> typu można zastosować więcej niż jeden atrybut.  
  
## <a name="known-types-and-primitives"></a>Znane typy i elementy podstawowe  
 Typy pierwotne, a także niektóre typy traktowane jako elementy pierwotne (na przykład <xref:System.DateTime> i <xref:System.Xml.XmlElement>) są zawsze "znane" i nigdy nie muszą być dodawane przez ten mechanizm. Jednakże tablice typów pierwotnych muszą być dodawane jawnie. Większość kolekcji jest traktowana jako odpowiednik tablic. (Kolekcje inne niż ogólne są uważane za równoważne tablicom <xref:System.Object>). Aby zapoznać się z przykładem typów pierwotnych, tablic podstawowych i kolekcji pierwotnych, zobacz przykład 4.  
  
> [!NOTE]
> W <xref:System.DateTimeOffset> przeciwieństwie do innych typów pierwotnych, struktura nie jest typem znanym domyślnie, więc należy ją dodać ręcznie do listy znanych typów.  
  
## <a name="examples"></a>Przykłady  
 W poniższych przykładach <xref:System.Runtime.Serialization.KnownTypeAttribute> przedstawiono klasę używaną.  
  
#### <a name="example-1"></a>Przykład 1  
 Istnieją trzy klasy z relacją dziedziczenia.  
  
 [!code-csharp[C_KnownTypeAttribute#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#1)]
 [!code-vb[C_KnownTypeAttribute#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#1)]  
  
 Następująca `CompanyLogo` Klasa może być serializowana, ale nie można jej zdeserializować, `ShapeOfLogo` Jeśli element członkowski `CircleType` jest ustawiony `TriangleType` na albo obiekt, ponieważ aparat deserializacji nie rozpoznaje żadnych typów z nazwami kontraktu danych " Okrąg "lub" trójkąta ".  
  
 [!code-csharp[C_KnownTypeAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#2)]
 [!code-vb[C_KnownTypeAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#2)]  
  
 Poprawna Metoda pisania `CompanyLogo` typu jest pokazana w poniższym kodzie.  
  
 [!code-csharp[C_KnownTypeAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#3)]
 [!code-vb[C_KnownTypeAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#3)]  
  
 Za każdym razem, `CompanyLogo2` gdy typ zewnętrzny jest deserializowany, aparat deserializacji wie `CircleType` o `TriangleType` i i, w związku z tym, może znaleźć pasujące typy kontraktów danych "Circle" i "Trójkąty".  
  
#### <a name="example-2"></a>Przykład 2  
 W poniższym przykładzie, pomimo tego, że `CustomerTypeA` oba `CustomerTypeB` i mają `Customer` umowę danych `PurchaseOrder` , wystąpienie `CustomerTypeB` jest tworzone za każdym razem, gdy jest deserializowany, ponieważ `CustomerTypeB` jest znane tylko dla aparat deserializacji.  
  
 [!code-csharp[C_KnownTypeAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#4)]
 [!code-vb[C_KnownTypeAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#4)]  
  
#### <a name="example-3"></a>Przykład 3  
 W poniższym przykładzie zawartość jest <xref:System.Collections.Hashtable> przechowywana wewnętrznie jako. <xref:System.Object> Aby pomyślnie deserializować tablicę skrótów, aparat deserializacji musi znać zestaw możliwych typów, które mogą wystąpić w tym miejscu. W takim przypadku `Book` wiemy, że tylko `Magazine` `Catalog`obiekty są przechowywane w, dlatego są one dodawane przy użyciu <xref:System.Runtime.Serialization.KnownTypeAttribute> atrybutu.  
  
 [!code-csharp[C_KnownTypeAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#5)]
 [!code-vb[C_KnownTypeAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#5)]  
  
#### <a name="example-4"></a>Przykład 4  
 W poniższym przykładzie kontrakt danych przechowuje liczbę i operację do wykonania na numerze. Składowa danych może być liczbą całkowitą, tablicą liczb całkowitych <xref:System.Collections.Generic.List%601> lub zawierającą liczby całkowite. `Numbers`  
  
> [!CAUTION]
> Ta wartość będzie działała tylko po stronie klienta, jeśli SVCUTIL. Plik EXE jest używany do generowania serwera proxy WCF. Svcutil. EXE pobiera metadane z usługi, w tym wszystkie znane typy. Bez tych informacji klient nie będzie mógł deserializować typów.  
  
 [!code-csharp[C_KnownTypeAttribute#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#6)]
 [!code-vb[C_KnownTypeAttribute#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#6)]  
  
 Jest to kod aplikacji.  
  
 [!code-csharp[C_KnownTypeAttribute#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#7)]
 [!code-vb[C_KnownTypeAttribute#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#7)]  
  
## <a name="known-types-inheritance-and-interfaces"></a>Znane typy, dziedziczenie i interfejsy  
 Gdy znany typ jest skojarzony z określonym typem przy użyciu `KnownTypeAttribute` atrybutu, znany typ jest również skojarzony ze wszystkimi typami pochodnymi tego typu. Na przykład zapoznaj się z poniższym kodem.  
  
 [!code-csharp[C_KnownTypeAttribute#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#8)]
 [!code-vb[C_KnownTypeAttribute#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#8)]  
  
 `Circle` Klasanie`Drawing`wymaga, `Square` aby atrybut był używany i w polu,ponieważklasabazowa()majużzastosowaneteatrybuty.`AdditionalShape` `KnownTypeAttribute` `DoubleDrawing`  
  
 Znane typy można kojarzyć tylko z klasami i strukturami, a nie interfejsami.  
  
## <a name="known-types-using-open-generic-methods"></a>Znane typy używające otwartych metod ogólnych  
 Może być konieczne dodanie typu ogólnego jako znanego typu. Jednak otwarty typ generyczny nie może być przekazywać jako parametr do `KnownTypeAttribute` atrybutu.  
  
 Ten problem można rozwiązać przy użyciu alternatywnego mechanizmu: Napisz metodę, która zwraca listę typów, które mają zostać dodane do kolekcji znanych typów. Nazwa metody jest następnie określona jako argument ciągu dla `KnownTypeAttribute` atrybutu z powodu pewnych ograniczeń.  
  
 Metoda musi istnieć w typie, do którego `KnownTypeAttribute` zastosowano atrybut, musi być statyczna, nie może akceptować parametrów i musi zwracać obiekt, <xref:System.Type>do <xref:System.Collections.IEnumerable> którego można przypisać.  
  
 Nie można połączyć `KnownTypeAttribute` atrybutu z nazwą metody i `KnownTypeAttribute` atrybutami o rzeczywistych typach tego samego typu. Ponadto nie można zastosować więcej niż jednego `KnownTypeAttribute` z nazwą metody do tego samego typu.  
  
 Zapoznaj się z następującą klasą.  
  
 [!code-csharp[C_KnownTypeAttribute#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#9)]
 [!code-vb[C_KnownTypeAttribute#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#9)]  
  
 Pole zawiera wystąpienia klasy `ColorDrawing` generycznej i klasy `BlackAndWhiteDrawing`generycznej, które dziedziczą z klasy `Drawing`generycznej. `theDrawing` Zwykle obydwie muszą być dodawane do znanych typów, ale Poniższa składnia nie jest prawidłową składnią dla atrybutów.  
  
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
  
 W tym celu należy utworzyć metodę, aby zwracała te typy. Prawidłowy sposób zapisu tego typu, a następnie pokazano w poniższym kodzie.  
  
 [!code-csharp[C_KnownTypeAttribute#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#10)]
 [!code-vb[C_KnownTypeAttribute#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#10)]  
  
## <a name="additional-ways-to-add-known-types"></a>Dodatkowe sposoby dodawania znanych typów  
 Ponadto znane typy można dodawać za pomocą pliku konfiguracji. Jest to przydatne, gdy nie kontrolujesz typu wymagającego znanych typów do właściwej deserializacji, na przykład w przypadku używania bibliotek typów innych firm z Windows Communication Foundation (WCF).  
  
 Poniższy plik konfiguracji przedstawia sposób określenia znanego typu w pliku konfiguracji.  
  
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
  
 W poprzednim pliku konfiguracji typ kontraktu danych o nazwie `MyCompany.Library.Shape` jest zadeklarowany `MyCompany.Library.Circle` jako znany typ.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Serialization.KnownTypeAttribute>
- <xref:System.Collections.Hashtable>
- <xref:System.Object>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A>
- [Znane typy](../../../../docs/framework/wcf/samples/known-types.md)
- [Równoważność kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [Projektowanie kontraktów usług](../../../../docs/framework/wcf/designing-service-contracts.md)
