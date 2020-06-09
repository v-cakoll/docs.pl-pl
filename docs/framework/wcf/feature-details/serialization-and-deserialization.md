---
title: Serializacja i deserializacja
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3d71814c-bda7-424b-85b7-15084ff9377a
ms.openlocfilehash: 8d62fe1cb646bfa00f3fd2e694f08d9fed297bc2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600428"
---
# <a name="serialization-and-deserialization"></a>Serializacja i deserializacja
Windows Communication Foundation (WCF) zawiera nowy aparat serializacji, <xref:System.Runtime.Serialization.DataContractSerializer> . <xref:System.Runtime.Serialization.DataContractSerializer>Tłumaczy między obiektami .NET Framework i XML, w obu kierunkach. W tym temacie wyjaśniono, jak działa serializator.  
  
 Podczas serializacji obiektów .NET Framework, serializator zrozumie różne modele programowania serializacji, łącznie z nowym modelem *kontraktu danych* . Aby uzyskać pełną listę obsługiwanych typów, zobacz [Typy obsługiwane przez serializator kontraktu danych](types-supported-by-the-data-contract-serializer.md). Aby zapoznać się z wprowadzeniem do kontraktów danych, zobacz [Korzystanie z kontraktów danych](using-data-contracts.md).  
  
 Podczas deserializacji XML, serializator używa <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> klas i. Obsługuje ona również <xref:System.Xml.XmlDictionaryReader> klasy i, <xref:System.Xml.XmlDictionaryWriter> Aby umożliwić jej tworzenie ZOPTYMALIZOWANEGO kodu XML w niektórych przypadkach, na przykład przy użyciu binarnego formatu XML WCF.  
  
 WCF zawiera również serializator pomocnika, <xref:System.Runtime.Serialization.NetDataContractSerializer> . <xref:System.Runtime.Serialization.NetDataContractSerializer>Jest podobna do <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> i <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> serializatorów, ponieważ również emituje .NET Framework nazw typów w ramach serializowanych danych. Jest on używany, gdy te same typy są udostępniane na serializacji i zakończenia deserializacji. Zarówno, <xref:System.Runtime.Serialization.DataContractSerializer> jak i <xref:System.Runtime.Serialization.NetDataContractSerializer> pochodna z wspólnej klasy bazowej, <xref:System.Runtime.Serialization.XmlObjectSerializer> .  
  
> [!WARNING]
> <xref:System.Runtime.Serialization.DataContractSerializer>Serializacji ciągów zawierających znaki kontrolne o wartości szesnastkowej poniżej 20 jako jednostki XML. Może to spowodować problem z klientem innym niż WCF podczas wysyłania takich danych do usługi WCF.  
  
## <a name="creating-a-datacontractserializer-instance"></a>Tworzenie wystąpienia DataContractSerializer  
 Konstruowanie wystąpienia <xref:System.Runtime.Serialization.DataContractSerializer> jest ważnym krokiem. Po przygotowaniu nie można zmienić żadnych ustawień.  
  
### <a name="specifying-the-root-type"></a>Określanie typu głównego  
 *Typ główny* to typ, z którego wystąpienia są serializowane lub deserializowane. <xref:System.Runtime.Serialization.DataContractSerializer>Ma wiele przeciążeń konstruktora, ale co najmniej musi być dostarczony typ główny przy użyciu `type` parametru.  
  
 Serializator utworzony dla określonego typu głównego nie może zostać użyty do serializacji (lub deserializacji) innego typu, chyba że typ pochodzi od typu głównego. Poniższy przykład przedstawia dwie klasy.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#1)]
 [!code-vb[c_StandaloneDataContractSerializer#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#1)]  
  
 Ten kod tworzy wystąpienie `DataContractSerializer` , które może być używane tylko do serializacji lub deserializacji wystąpień `Person` klasy.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#2)]
 [!code-vb[c_StandaloneDataContractSerializer#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#2)]  
  
### <a name="specifying-known-types"></a>Określanie znanych typów  
 Jeśli polimorfizm jest uwzględniany w serializowanych typach, które nie zostały jeszcze obsłużone przy użyciu <xref:System.Runtime.Serialization.KnownTypeAttribute> atrybutu lub innego mechanizmu, lista możliwych znanych typów musi zostać przeniesiona do konstruktora serializatora przy użyciu `knownTypes` parametru. Aby uzyskać więcej informacji na temat znanych typów, zobacz [znane typy kontraktu danych](data-contract-known-types.md).  
  
 Poniższy przykład pokazuje klasę, `LibraryPatron` , która zawiera kolekcję określonego typu, `LibraryItem` . Druga klasa definiuje `LibraryItem` Typ. Trzecia i cztery klasy ( `Book` i `Newspaper` ) dziedziczą z `LibraryItem` klasy.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#3)]  
 [!code-vb[c_StandaloneDataContractSerializer#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#3)]  
  
 Poniższy kod tworzy wystąpienie serializatora przy użyciu `knownTypes` parametru.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#4)]
 [!code-vb[c_StandaloneDataContractSerializer#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#4)]  
  
### <a name="specifying-the-default-root-name-and-namespace"></a>Określanie domyślnej nazwy głównej i przestrzeni nazw  
 Zwykle gdy obiekt jest serializowany, domyślna nazwa i przestrzeń nazw zewnętrznego elementu XML są określane zgodnie z nazwą kontraktu danych i przestrzenią nazw. Nazwy wszystkich elementów wewnętrznych są określane na podstawie nazw składowych danych, a ich przestrzeń nazw jest przestrzenią nazw kontraktu danych. Poniższe przykładowe zestawy `Name` i `Namespace` wartości w konstruktorach <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute> klas i.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#5)]
 [!code-vb[c_StandaloneDataContractSerializer#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#5)]  
  
 Serializacja wystąpienia `Person` klasy powoduje, że kod XML jest podobny do poniższego.  
  
```xml  
<PersonContract xmlns="http://schemas.contoso.com">  
  <AddressMember>  
    <StreetMember>123 Main Street</StreetMember>  
   </AddressMember>  
</PersonContract>  
```  
  
 Można jednak dostosować domyślną nazwę i przestrzeń nazw elementu głównego, przekazując wartości `rootName` i `rootNamespace` parametrów do <xref:System.Runtime.Serialization.DataContractSerializer> konstruktora. Należy zauważyć, że nie `rootNamespace` ma to wpływu na przestrzeń nazw zawartych elementów, które odpowiadają elementom członkowskim danych. Dotyczy tylko przestrzeni nazw zewnętrznego elementu.  
  
 Te wartości mogą być przesyłane jako ciągi lub wystąpienia <xref:System.Xml.XmlDictionaryString> klasy w celu umożliwienia optymalizacji przy użyciu binarnego formatu XML.  
  
### <a name="setting-the-maximum-objects-quota"></a>Ustawianie maksymalnego limitu przydziału obiektów  
 Niektóre `DataContractSerializer` przeciążenia konstruktora mają `maxItemsInObjectGraph` parametr. Ten parametr określa maksymalną liczbę obiektów serializowanych lub deserializacji serializatora w jednym <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> wywołaniu metody. (Metoda zawsze odczytuje jeden obiekt główny, ale ten obiekt może mieć inne obiekty w jego składowych danych. Obiekty te mogą mieć inne obiekty itd.) Wartość domyślna to 65536. Należy pamiętać, że podczas serializacji lub deserializacji tablic każda pozycja tablicy jest traktowana jako oddzielny obiekt. Należy również pamiętać, że niektóre obiekty mogą mieć znaczną reprezentację pamięci, więc ten limit przydziału może być niewystarczający, aby zapobiec atakom typu "odmowa usługi". Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące zabezpieczeń danych](security-considerations-for-data.md). Jeśli trzeba zwiększyć ten limit przydziału poza wartością domyślną, należy to zrobić zarówno w przypadku wysyłania (serializacji), jak i otrzymywania (deserializacji) stron, ponieważ odnosi się zarówno do odczytu i zapisu danych.  
  
### <a name="round-trips"></a>Okrągłe podróże  
 Gdy obiekt jest deserializowany i ponownie serializowany w jednej operacji, występuje *runda* . W tym celu pochodzi z pliku XML do wystąpienia obiektu i ponownie w strumieniu XML.  
  
 Niektóre `DataContractSerializer` przeciążenia konstruktora mają `ignoreExtensionDataObject` parametr, który jest domyślnie ustawiony na wartość `false` . W tym trybie domyślnym dane mogą być wysyłane w formie rundy z nowszej wersji kontraktu danych za pośrednictwem starszej wersji i z powrotem do nowszej wersji bez utraty, o ile kontrakt danych implementuje <xref:System.Runtime.Serialization.IExtensibleDataObject> interfejs. Na przykład załóżmy, że wersja 1 `Person` kontraktu danych zawiera `Name` elementy członkowskie danych i `PhoneNumber` , a wersja 2 dodaje `Nickname` element członkowski. Jeśli `IExtensibleDataObject` jest zaimplementowany, podczas wysyłania informacji z wersji 2 do wersji 1 `Nickname` dane są przechowywane, a następnie ponownie emitowane po ponownym serializacji danych; w związku z tym żadne dane nie zostaną utracone podczas rundy. Aby uzyskać więcej informacji, zobacz [Kontrakty danych zgodne z przekazaniem](forward-compatible-data-contracts.md) i [przechowywanie wersji kontraktu danych](data-contract-versioning.md).  
  
#### <a name="security-and-schema-validity-concerns-with-round-trips"></a>Zagadnienia dotyczące zabezpieczeń i schematów w przypadku rundy  
 Obie podróże mogą mieć wpływ na bezpieczeństwo. Na przykład deserializacja i przechowywanie dużych ilości danych obcych może stanowić zagrożenie bezpieczeństwa. Mogą wystąpić problemy z bezpieczeństwem dotyczące ponownego emitowania tych danych, które nie mają możliwości sprawdzenia, szczególnie jeśli są używane podpisy cyfrowe. Na przykład w poprzednim scenariuszu punkt końcowy w wersji 1 może podpisywać `Nickname` wartość, która zawiera złośliwe dane. Na koniec mogą wystąpić problemy z ważnością schematu: punkt końcowy może chcieć, aby zawsze emitować dane, które są ściśle zgodne z podaną umową, a nie z żadnymi dodatkowymi wartościami. W poprzednim przykładzie kontrakt punktu końcowego w wersji 1 wydaje się, że emituje tylko `Name` i `PhoneNumber` i jeśli jest używana Walidacja schematu, emitowanie dodatkowej `Nickname` wartości powoduje niepowodzenie walidacji.  
  
#### <a name="enabling-and-disabling-round-trips"></a>Włączanie i wyłączanie rundy  
 Aby wyłączyć funkcję błądzenia, nie należy implementować <xref:System.Runtime.Serialization.IExtensibleDataObject> interfejsu. Jeśli nie masz kontroli nad typami, ustaw parametr tak, aby `ignoreExtensionDataObject` `true` osiągnąć ten sam efekt.  
  
### <a name="object-graph-preservation"></a>Zachowywanie wykresu obiektów  
 Zwykle serializator nie dba o tożsamość obiektu, jak w poniższym kodzie.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#6)]
 [!code-vb[c_StandaloneDataContractSerializer#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#6)]  
  
 Poniższy kod tworzy zamówienie zakupu.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#7)]
 [!code-vb[c_StandaloneDataContractSerializer#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#7)]  
  
 Należy zauważyć, że `billTo` i `shipTo` pola są ustawione na to samo wystąpienie obiektu. Jednak wygenerowany kod XML duplikuje informacje zduplikowane i wygląda podobnie do poniższego kodu XML.  
  
```xml  
<PurchaseOrder>  
  <billTo><street>123 Main St.</street></billTo>  
  <shipTo><street>123 Main St.</street></shipTo>  
</PurchaseOrder>  
```  
  
 Jednak takie podejście ma następujące cechy, które mogą być niepożądane:  
  
- Wydajność. Replikowanie danych jest niewydajne.  
  
- Odwołania cykliczne. Jeśli obiekty odnoszą się do siebie, nawet za pomocą innych obiektów, serializacja przez replikację powoduje nieskończoną pętlę. (Serializator zgłasza, <xref:System.Runtime.Serialization.SerializationException> Jeśli taka sytuacja występuje).  
  
- Semantyki. Czasami ważne jest, aby zachować fakt, że dwa odwołania są do tego samego obiektu, a nie do dwóch identycznych obiektów.  
  
 Z tego względu niektóre `DataContractSerializer` przeciążenia konstruktora mają `preserveObjectReferences` parametr (wartość domyślna to `false` ). Gdy ten parametr jest ustawiony na `true` , jest to specjalna metoda kodowania odwołań do obiektów, która jest używana tylko przez program WCF. Po ustawieniu na `true` , przykładowy kod XML jest teraz podobny do poniższego.  
  
```xml  
<PurchaseOrder ser:id="1">  
  <billTo ser:id="2"><street ser:id="3">123 Main St.</street></billTo>  
  <shipTo ser:ref="2"/>  
</PurchaseOrder>  
```  
  
 Przestrzeń nazw "ser" odwołuje się do przestrzeni nazw serializacji standardowej, `http://schemas.microsoft.com/2003/10/Serialization/` . Każdy element danych jest serializowany tylko raz i ma określony numer IDENTYFIKACYJNy, a kolejne użycie powoduje odwołanie do już zserializowanych danych.  
  
> [!IMPORTANT]
> Jeśli w kontrakcie danych są obecne atrybuty "ID" i "ref" `XMLElement` , atrybut "ref" jest uznawany, a atrybut "ID" jest ignorowany.  
  
 Ważne jest zrozumienie ograniczeń tego trybu:  
  
- KOD XML `DataContractSerializer` tworzony z `preserveObjectReferences` ustawioną na `true` nie jest współdziałany z innymi technologiami i można uzyskać do niego dostęp tylko przy użyciu innego `DataContractSerializer` wystąpienia, a także `preserveObjectReferences` ustawić wartość `true` .  
  
- Brak obsługi metadanych (schematu) dla tej funkcji. Tworzony schemat jest prawidłowy tylko dla przypadku, gdy `preserveObjectReferences` jest ustawiony na `false` .  
  
- Ta funkcja może spowodować wolniejsze działanie serializacji i deserializacji. Chociaż dane nie muszą być replikowane, w tym trybie należy wykonać dodatkowe porównania obiektów.  
  
> [!CAUTION]
> Gdy `preserveObjectReferences` tryb jest włączony, jest szczególnie ważne, aby ustawić wartość w `maxItemsInObjectGraph` prawidłowym limicie przydziału. Ze względu na sposób obsługi tablic w tym trybie, osoba atakująca może łatwo utworzyć małą złośliwą wiadomość, która powoduje, że duże użycie pamięci jest ograniczone tylko przez `maxItemsInObjectGraph` przydział.  
  
### <a name="specifying-a-data-contract-surrogate"></a>Określanie surogatu kontraktu danych  
 Niektóre `DataContractSerializer` przeciążenia konstruktora mają `dataContractSurrogate` parametr, który może być ustawiony na `null` . W przeciwnym razie można użyć jej do określenia *surogatu kontraktu danych*, który jest typem, który implementuje <xref:System.Runtime.Serialization.IDataContractSurrogate> interfejs. Następnie można użyć interfejsu do dostosowania procesu serializacji i deserializacji. Aby uzyskać więcej informacji, zobacz [surogaty kontraktu danych](../extending/data-contract-surrogates.md).  
  
## <a name="serialization"></a>Serializacja  
 Poniższe informacje dotyczą każdej klasy, która dziedziczy z <xref:System.Runtime.Serialization.XmlObjectSerializer> , łącznie z <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.NetDataContractSerializer> klasami i.  
  
### <a name="simple-serialization"></a>Prosta Serializacja  
 Najbardziej podstawowym sposobem serializacji obiektu jest przekazanie go do <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObject%2A> metody. Istnieją trzy przeciążenia, jeden z nich do zapisu w <xref:System.IO.Stream> , a <xref:System.Xml.XmlWriter> lub <xref:System.Xml.XmlDictionaryWriter> . W przypadku <xref:System.IO.Stream> przeciążenia dane wyjściowe są XML w kodowaniu UTF-8. W przypadku <xref:System.Xml.XmlDictionaryWriter> przeciążenia, serializator optymalizuje dane wyjściowe dla binarnego kodu XML.  
  
 W przypadku korzystania z <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObject%2A> metody serializator używa domyślnej nazwy i przestrzeni nazw dla elementu otoki i zapisuje go wraz z zawartością (zobacz poprzednią sekcję "Określanie domyślnej nazwy głównej i przestrzeni nazw").  
  
 Poniższy przykład ilustruje pisanie przy użyciu <xref:System.Xml.XmlDictionaryWriter> .  
  
 [!code-csharp[c_StandaloneDataContractSerializer#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#8)]
 [!code-vb[c_StandaloneDataContractSerializer#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#8)]  
  
 Spowoduje to utworzenie kodu XML podobnego do poniższego.  
  
```xml  
<Person>  
  <Name>Jay Hamlin</Name>  
  <Address>123 Main St.</Address>  
</Person>  
```  
  
### <a name="step-by-step-serialization"></a>Serializacja krok po kroku  
 Użyj <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A> metod, <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObjectContent%2A> , i, <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> Aby zapisać element końcowy, zapisać zawartość obiektu i zamknąć odpowiednio element otoki.  
  
> [!NOTE]
> Nie ma żadnych <xref:System.IO.Stream> przeciążeń tych metod.  
  
 Ta Serializacja krok po kroku ma dwa typowe zastosowania. Jednym z nich jest wstawianie zawartości, takiej jak atrybuty lub komentarze między `WriteStartObject` i `WriteObjectContent` , jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#9)]
 [!code-vb[c_StandaloneDataContractSerializer#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#9)]  
  
 Spowoduje to utworzenie kodu XML podobnego do poniższego.  
  
```xml  
<Person serializedBy="myCode">  
  <Name>Jay Hamlin</Name>  
  <Address>123 Main St.</Address>  
</Person>  
```  
  
 Innym typowym zastosowaniem jest unikanie używania <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A> i <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> całości, a także tworzenie własnego elementu otoki niestandardowej (lub nawet pomijanie tworzenia otoki), jak pokazano w poniższym kodzie.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#10)]
 [!code-vb[c_StandaloneDataContractSerializer#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#10)]  
  
 Spowoduje to utworzenie kodu XML podobnego do poniższego.  
  
```xml  
<MyCustomWrapper>  
  <Name>Jay Hamlin</Name>  
  <Address>123 Main St.</Address>  
</MyCustomWrapper>  
```  
  
> [!NOTE]
> Użycie serializacji krok po kroku może spowodować, że w schemacie nieprawidłowy kod XML.  
  
## <a name="deserialization"></a>Deserializacji  
 Poniższe informacje dotyczą każdej klasy, która dziedziczy z <xref:System.Runtime.Serialization.XmlObjectSerializer> , łącznie z <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.NetDataContractSerializer> klasami i.  
  
 Najbardziej podstawowym sposobem deserializacji obiektu jest wywołanie jednego z <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> przeciążeń metody. Istnieją trzy przeciążenia, jeden z nich do odczytu z <xref:System.Xml.XmlDictionaryReader> , a `XmlReader` lub `Stream` . Należy zauważyć, że `Stream` Przeciążenie tworzy tekst <xref:System.Xml.XmlDictionaryReader> , który nie jest chroniony przez żadne przydziały i powinien być używany tylko do odczytywania zaufanych danych.  
  
 Należy również zauważyć, że obiekt `ReadObject` zwracany przez metodę musi być rzutowany na odpowiedni typ.  
  
 Poniższy kod tworzy wystąpienie <xref:System.Runtime.Serialization.DataContractSerializer> i a <xref:System.Xml.XmlDictionaryReader> , a następnie deserializacji `Person` wystąpienia.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#11)]
 [!code-vb[c_StandaloneDataContractSerializer#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#11)]  
  
 Przed wywołaniem <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> metody należy umieścić obiekt odczytujący XML na elemencie otoki lub w węźle nienależącym do zawartości, który poprzedza element otoki. Można to zrobić przez wywołanie <xref:System.Xml.XmlReader.Read%2A> metody <xref:System.Xml.XmlReader> lub jej pochodne i przetestowanie <xref:System.Xml.XmlReader.NodeType%2A> , jak pokazano w poniższym kodzie.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#12)]
 [!code-vb[c_StandaloneDataContractSerializer#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#12)]  
  
 Należy pamiętać, że atrybuty tego elementu otoki można odczytać przed przekazaniem czytnika do programu `ReadObject` .  
  
 W przypadku użycia jednego z prostych `ReadObject` przeciążeń, Deserializator szuka domyślnej nazwy i przestrzeni nazw w elemencie otoki (zobacz poprzednią sekcję "Określanie domyślnej nazwy głównej i przestrzeni nazw") i zgłasza wyjątek, jeśli odnajdzie nieznany element. W poprzednim przykładzie `<Person>` oczekiwany jest element otoki. <xref:System.Runtime.Serialization.XmlObjectSerializer.IsStartObject%2A>Metoda jest wywoływana w celu sprawdzenia, czy czytnik jest umieszczony na elemencie o nazwie zgodnie z oczekiwaniami.  
  
 Istnieje możliwość wyłączenia tego sprawdzania nazwy elementu otoki; Niektóre przeciążenia `ReadObject` metody przyjmują parametr logiczny `verifyObjectName` , który jest domyślnie ustawiony na wartość `true` . Gdy jest ustawiona na `false` , nazwa i przestrzeń nazw elementu otoki jest ignorowana. Jest to przydatne w przypadku odczytywania kodu XML, który został zapisany przy użyciu opisanego wcześniej mechanizmu serializacji krok po kroku.  
  
## <a name="using-the-netdatacontractserializer"></a>Korzystanie z NetDataContractSerializer  
 Główną różnicą między `DataContractSerializer` i <xref:System.Runtime.Serialization.NetDataContractSerializer> jest to, że program `DataContractSerializer` używa nazw kontraktów danych, podczas gdy dane `NetDataContractSerializer` wyjściowe pełnią .NET Framework zestawu i typów nazw w serializowanym kodzie XML. Oznacza to, że dokładnie te same typy muszą być współdzielone między punktami końcowymi serializacji i deserializacji. Oznacza to, że mechanizm znanych typów nie jest wymagany w przypadku, gdy `NetDataContractSerializer` dokładne typy do deserializacji są zawsze znane.  
  
 Może jednak wystąpić kilka problemów:  
  
- Zabezpieczenia. Zostanie załadowany dowolny typ znaleziony w deserializowanym kodzie XML. Może to być wykorzystane w celu wymuszenia załadowania złośliwych typów. Za pomocą `NetDataContractSerializer` niezaufanych danych należy wykonać tylko wtedy, gdy jest używany *spinacz serializacji* (przy użyciu <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder%2A> właściwości lub konstruktora). Spinacz zezwala na ładowanie tylko bezpiecznych typów. Mechanizm segregatora jest identyczny z typem, który jest <xref:System.Runtime.Serialization> używany w przestrzeni nazw.  
  
- Przechowywanie wersji. Używanie typów pełnych i nazw zestawów w kodzie XML poważnie ogranicza sposób obsługi wersji. Nie można zmienić następujących danych: nazwy typów, przestrzenie nazw, nazwy zestawów i wersje zestawu. Ustawienie <xref:System.Runtime.Serialization.NetDataContractSerializer.AssemblyFormat%2A> właściwości lub konstruktora <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle.Simple> zamiast wartości domyślnej <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle.Full> zezwala na zmiany wersji zestawu, ale nie dla typów parametrów ogólnych.  
  
- Współdziałanie. Ponieważ typ .NET Framework i nazwy zestawów są zawarte w pliku XML, platformy inne niż .NET Framework nie mogą uzyskać dostępu do danych wyjściowych.  
  
- Wydajność. Wpisywanie nazw typów i zestawów znacząco zwiększa rozmiar wynikowego kodu XML.  
  
 Ten mechanizm jest podobny do serializacji binarnej lub SOAP używanej przez .NET Framework komunikacji zdalnej (w tym, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> a <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> ).  
  
 Korzystanie z programu `NetDataContractSerializer` jest podobne do użycia `DataContractSerializer` , z następującymi różnicami:  
  
- Konstruktory nie wymagają określenia typu głównego. Można serializować dowolnego typu z tym samym wystąpieniem `NetDataContractSerializer` .  
  
- Konstruktory nie akceptują listy znanych typów. Mechanizm znanych typów jest zbędny, jeśli nazwy typów są serializowane do kodu XML.  
  
- Konstruktory nie akceptują surogatu kontraktu danych. Zamiast tego akceptują <xref:System.Runtime.Serialization.ISurrogateSelector> parametr o nazwie `surrogateSelector` (który mapuje do <xref:System.Runtime.Serialization.NetDataContractSerializer.SurrogateSelector%2A> Właściwości). Jest to starszy mechanizm zastępczy.  
  
- Konstruktory akceptują parametr wywoływany przez `assemblyFormat` <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle> Mapowanie do <xref:System.Runtime.Serialization.NetDataContractSerializer.AssemblyFormat%2A> właściwości. Jak wspomniano wcześniej, może to służyć do ulepszania możliwości obsługi wersji programu szeregującego. Jest to taka sama jak <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle> w przypadku serializacji binarnej lub SOAP.  
  
- Konstruktory akceptują <xref:System.Runtime.Serialization.StreamingContext> parametr o nazwie `context` , który jest mapowany na <xref:System.Runtime.Serialization.NetDataContractSerializer.Context%2A> Właściwość. Możesz użyć tego do przekazania informacji do typów, które są serializowane. To użycie jest takie samo jak w przypadku <xref:System.Runtime.Serialization.StreamingContext> mechanizmu używanego w innych <xref:System.Runtime.Serialization> klasach.  
  
- <xref:System.Runtime.Serialization.NetDataContractSerializer.Serialize%2A>Metody i <xref:System.Runtime.Serialization.NetDataContractSerializer.Deserialize%2A> są aliasami dla <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObject%2A> metod i <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> . Istnieją one, aby zapewnić bardziej spójny model programowania z binarną lub serializacji SOAP.  
  
 Aby uzyskać więcej informacji o tych funkcjach, zobacz [Serializacja binarna](../../../standard/serialization/binary-serialization.md).  
  
 Formaty XML, których `NetDataContractSerializer` `DataContractSerializer` użycie i nie są zwykle zgodne. Oznacza to, że próba serializacji z jednym z tych serializacji i deserializacji z drugim nie jest obsługiwanym scenariuszem.  
  
 Należy również pamiętać, że program `NetDataContractSerializer` nie wyprowadza pełnego typu .NET Framework i nazwy zestawu dla każdego węzła na grafie obiektów. Dane te są wyprowadzane tylko wtedy, gdy są niejednoznaczne. Oznacza to, że jest ona wyprowadzana na poziomie obiektu głównego i dla każdego polimorficznego przypadku.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.NetDataContractSerializer>
- <xref:System.Runtime.Serialization.XmlObjectSerializer>
- [Serializacja binarna](../../../standard/serialization/binary-serialization.md)
- [Typy obsługiwane przez serializator kontraktu danych](types-supported-by-the-data-contract-serializer.md)
