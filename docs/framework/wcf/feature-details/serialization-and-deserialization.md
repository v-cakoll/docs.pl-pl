---
title: Serializacja i deserializacja
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3d71814c-bda7-424b-85b7-15084ff9377a
ms.openlocfilehash: 7ddad36c05d9972b9fc613403b68b7c793b6701d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54707580"
---
# <a name="serialization-and-deserialization"></a>Serializacja i deserializacja
Windows Communication Foundation (WCF) obejmuje nowy mechanizm serializacji, <xref:System.Runtime.Serialization.DataContractSerializer>. <xref:System.Runtime.Serialization.DataContractSerializer> Tłumaczy [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] obiektów i XML w obu kierunkach. W tym temacie wyjaśniono, jak serializator działa.  
  
 Podczas serializacji [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] obiektów, serializator zrozumienie różnych serializacji programowania modeli, w tym nowym *kontraktu danych* modelu. Aby uzyskać pełną listę obsługiwanych typów, zobacz [typy obsługiwane przez serializator kontraktu danych](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md). Aby zapoznać się z wprowadzeniem do kontraktów danych, zobacz [za pomocą kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 Podczas deserializacji XML, używa serializatora <xref:System.Xml.XmlReader> i <xref:System.Xml.XmlWriter> klasy. Obsługuje ona również <xref:System.Xml.XmlDictionaryReader> i <xref:System.Xml.XmlDictionaryWriter> klasy do wygenerowania zoptymalizowane pod kątem XML w niektórych przypadkach, takich jak podczas formatowania przy użyciu programu WCF binarny kod XML.  
  
 Usługi WCF zawiera również element serializujący Pomocnika <xref:System.Runtime.Serialization.NetDataContractSerializer>. <xref:System.Runtime.Serialization.NetDataContractSerializer> Przypomina <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> i <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> serializatory ponieważ również emituje [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] wpisz nazwy użytkowników w ramach serializowanych danych. Jest używany podczas takich samych typach są udostępniane na serializacji i deserializacji kończy się. Zarówno <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Runtime.Serialization.NetDataContractSerializer> dziedziczyć wspólna klasa bazowa <xref:System.Runtime.Serialization.XmlObjectSerializer>.  
  
> [!WARNING]
>  <xref:System.Runtime.Serialization.DataContractSerializer> Serializuje ciągi zawierające znaki kontrolne o wartości szesnastkowej poniżej 20 jako jednostki XML. Może to spowodować problem z klienta programu WCF niż podczas wysyłania tych danych do usługi WCF.  
  
## <a name="creating-a-datacontractserializer-instance"></a>Tworzenie wystąpienia elementu DataContractSerializer  
 Tworzenia wystąpienia <xref:System.Runtime.Serialization.DataContractSerializer> jest ważnym krokiem. Po konstrukcji nie można zmienić dowolne ustawienia.  
  
### <a name="specifying-the-root-type"></a>Określanie typu głównego  
 *Główny typ* to typ, którego wystąpienia są serializowany lub deserializowany. <xref:System.Runtime.Serialization.DataContractSerializer> Ma wiele przeciążeń konstruktora, ale co najmniej głównych wymagane jest podanie typu przy użyciu `type` parametru.  
  
 Element serializujący utworzone dla określonego typu głównego nie może służyć do serializacji (lub deserializacji) innego typu, chyba że typ pochodzi od typu głównego. Poniższy przykład pokazuje dwóch klas.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#1)]
 [!code-vb[c_StandaloneDataContractSerializer#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#1)]  
  
 Ten kod tworzy wystąpienie klasy `DataContractSerializer` który może służyć tylko do serializacji lub deserializacji wystąpienia `Person` klasy.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#2)]
 [!code-vb[c_StandaloneDataContractSerializer#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#2)]  
  
### <a name="specifying-known-types"></a>Określanie znane typy  
 Jeśli polimorfizm uczestniczy w typach serializacji, które nie są już obsługiwane za pomocą <xref:System.Runtime.Serialization.KnownTypeAttribute> atrybutu lub innego mechanizmu listę możliwych znane typy muszą być przekazywane do konstruktora serializator przy użyciu `knownTypes` parametru. Aby uzyskać więcej informacji na temat znanych typów, zobacz [znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
 W poniższym przykładzie pokazano klasę, `LibraryPatron`, która zawiera kolekcję określonego typu `LibraryItem`. Druga klasa definiuje `LibraryItem` typu. Trzecia i cztery klasy (`Book` i `Newspaper`) dziedziczyć `LibraryItem` klasy.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#3)]  
 [!code-vb[c_StandaloneDataContractSerializer#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#3)]  
  
 Poniższy kod tworzy wystąpienie klasy serializatora przy użyciu `knownTypes` parametru.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#4)]
 [!code-vb[c_StandaloneDataContractSerializer#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#4)]  
  
### <a name="specifying-the-default-root-name-and-namespace"></a>Określanie domyślnej nazwy katalogu głównego i Namespace  
 Zwykle gdy obiekt jest serializowany, domyślną nazwę i przestrzeń nazw najbardziej zewnętrznego element XML są określane zgodnie z nazwą kontraktu danych i przestrzeni nazw. Nazwy wszystkich elementów wewnętrzny są ustalane na podstawie nazwy elementów członkowskich danych i ich przestrzeń nazw jest przestrzeń nazw kontraktu danych. Poniższy przykład ustawia `Name` i `Namespace` wartości w konstruktorach z <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> klasy.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#5)]
 [!code-vb[c_StandaloneDataContractSerializer#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#5)]  
  
 Serializacji wystąpienia `Person` klasę XML, podobny do następującego.  
  
```xml  
<PersonContract xmlns="http://schemas.contoso.com">  
  <AddressMember>  
    <StreetMember>123 Main Street</StreetMember>  
   </AddressMember>  
</PersonContract>  
```  
  
 Jednakże, można dostosować domyślną nazwę i przestrzeń nazw głównego elementu przez przekazanie wartości `rootName` i `rootNamespace` parametry <xref:System.Runtime.Serialization.DataContractSerializer> konstruktora. Należy pamiętać, że `rootNamespace` nie ma wpływu na przestrzeń nazw zawartych elementów, które odnoszą się do elementów członkowskich danych. Ma to wpływ tylko przestrzeń nazw elementu najbardziej zewnętrznej.  
  
 Te wartości mogą być przekazywane jako parametry lub wystąpień <xref:System.Xml.XmlDictionaryString> klasy w celu umożliwienia ich optymalizacji, za pomocą binarny format XML.  
  
### <a name="setting-the-maximum-objects-quota"></a>Ustawienie limitu przydziału obiektów maksymalna  
 Niektóre `DataContractSerializer` mają przeciążenia konstruktora `maxItemsInObjectGraph` parametru. Ten parametr określa maksymalną liczbę obiektów serializator serializuje lub deserializuje w jednym <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> wywołania metody. (Metoda ma zawsze wartość jeden główny obiekt, ale ten obiekt może mieć inne obiekty w składowych danych. Te obiekty mogą mieć inne obiekty itd.) Wartość domyślna to 65536. Należy pamiętać, że podczas serializacji lub deserializacji tablic, każdy wpis tablicy jest liczona jako oddzielny obiekt. Należy również zauważyć, że niektóre obiekty mogą mieć reprezentację dużej ilości pamięci, a więc tego samego przydziału nie może być wystarczające, aby zapobiec "odmowa usługi". Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące zabezpieczeń dla danych](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md). Jeśli chcesz zwiększyć ten limit przydziału ponad wartość domyślną, należy to zrobić na wysyłanie (serializację) i odbieranie stronach (deserializacji), ponieważ dotyczy zarówno podczas odczytywania i zapisywania danych.  
  
### <a name="round-trips"></a>Dwustronne  
 A *obiegu* występuje, gdy obiekt jest przeprowadzona ponownie serializacji w ramach jednej operacji. W związku z tym go przechodzi z pliku XML na wystąpienie obiektu i ponownie do strumienia XML.  
  
 Niektóre `DataContractSerializer` mają przeciążenia konstruktora `ignoreExtensionDataObject` parametr, który jest ustawiona na `false` domyślnie. W tym trybie domyślne można wysyłać dane na komunikację dwustronną z nowszej wersji kontraktu danych za pomocą starszej wersji i z powrotem do nowszej wersji bez utraty, tak długo, jak implementuje kontraktu danych <xref:System.Runtime.Serialization.IExtensibleDataObject> interfejsu. Na przykład, załóżmy, że wersja 1 `Person` kontraktu danych zawiera `Name` i `PhoneNumber` elementy członkowskie danych i w wersji 2 dodaje `Nickname` elementu członkowskiego. Jeśli `IExtensibleDataObject` zaimplementowano podczas wysyłania informacji z wersji 2 do wersji 1, `Nickname` dane są przechowywane i następnie ponownie emitowane w przypadku danych jest serializowana ponownie; w związku z tym, nie dane zostaną utracone w przypadku komunikacji dwustronnej. Aby uzyskać więcej informacji, zobacz [kontrakty danych zgodne](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md) i [przechowywanie wersji kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md).  
  
#### <a name="security-and-schema-validity-concerns-with-round-trips"></a>Zabezpieczenia i schematu ważności problemów z dwustronne  
 Dwustronne mogą mieć wpływ na zabezpieczenia. Na przykład podczas deserializacji i przechowywania dużych ilości danych, nadmiarowe może stanowić zagrożenie bezpieczeństwa. Może to być obawy związane z bezpieczeństwem dotyczące ponownie emitowania te dane, że nie istnieje żaden sposób, aby sprawdzić, zwłaszcza, jeśli podpisy cyfrowe są zaangażowane. Na przykład w poprzednim scenariuszu punkt końcowy w wersji 1 może być podpisywania `Nickname` wartość, która zawiera dane złośliwe. Ponadto może być schematu ważności problemów: punkt końcowy, może być zawsze Emituj dane, które ściśle działa zgodnie z jego podane kontraktu i żadne dodatkowe wartości. W poprzednim przykładzie kontraktu punktu końcowego w wersji 1 mówi, że emituje tylko `Name` i `PhoneNumber`i jeśli jest on używany podczas sprawdzania poprawności schematu, wysyłających nadmiarowe `Nickname` wartość powoduje, że weryfikacja nie powiedzie się.  
  
#### <a name="enabling-and-disabling-round-trips"></a>Włączanie i wyłączanie dwustronne  
 Aby wyłączyć rund, nie należy implementować <xref:System.Runtime.Serialization.IExtensibleDataObject> interfejsu. Jeśli masz nie kontroluje typów, ustaw `ignoreExtensionDataObject` parametr `true` aby osiągnąć ten sam efekt.  
  
### <a name="object-graph-preservation"></a>Obiekt wykresu konserwacji  
 Zwykle Serializator nie interesują tożsamość obiektu, tak jak w poniższym kodzie.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#6)]
 [!code-vb[c_StandaloneDataContractSerializer#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#6)]  
  
 Poniższy kod tworzy zamówienie zakupu.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#7)]
 [!code-vb[c_StandaloneDataContractSerializer#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#7)]  
  
 Należy zauważyć, że `billTo` i `shipTo` pola są ustawione na tym samym wystąpieniu obiektu. Jednak wygenerowany kod XML duplikuje informacje zduplikowane i wygląda podobnie do następujących XML.  
  
```xml  
<PurchaseOrder>  
  <billTo><street>123 Main St.</street></billTo>  
  <shipTo><street>123 Main St.</street></shipTo>  
</PurchaseOrder>  
```  
  
 Jednak to podejście ma następujące cechy, które mogą być niepożądane:  
  
-   Wydajność. Replikowanie danych jest nieefektywne.  
  
-   Odwołania cykliczne. Jeśli obiekty odnoszą się do siebie, nawet za pośrednictwem innych obiektów serializacji za pomocą replikacji powoduje nieskończoną pętlę. (Element serializujący zgłasza <xref:System.Runtime.Serialization.SerializationException> w takiej sytuacji.)  
  
-   Semantyka. Czasami jest ważne, aby zachować fakt, że dwa odwołania są tego samego obiektu, a nie dwa obiekty identyczne.  
  
 Dla tych powodów niektóre `DataContractSerializer` mają przeciążenia konstruktora `preserveObjectReferences` parametru (wartość domyślna to `false`). Jeśli ten parametr jest równa `true`, specjalne metody kodowania odwołania do obiektów, które obsługuje tylko WCF, jest używany. Po ustawieniu `true`, przykładowy kod XML jest teraz podobny do następującego.  
  
```xml  
<PurchaseOrder ser:id="1">  
  <billTo ser:id="2"><street ser:id="3">123 Main St.</street></billTo>  
  <shipTo ser:ref="2"/>  
</PurchaseOrder>  
```  
  
 Przestrzeń nazw "użytkownika" odnosi się do przestrzeni nazw standardowych serializacji `http://schemas.microsoft.com/2003/10/Serialization/`. Każdy element danych jest serializowana tylko raz, a podany identyfikator, a kolejne używa wyników w odwołaniu do już serializowane dane.  
  
> [!IMPORTANT]
>  Jeśli atrybuty "id" i "ref" znajdują się w kontraktu danych `XMLElement`, a następnie zostanie uznane atrybutu "ref" i atrybut "id" jest ignorowany.  
  
 Warto zapoznać się z ograniczeniami w tym trybie:  
  
-   Plik XML `DataContractSerializer` tworzy się za pomocą `preserveObjectReferences` równa `true` nie współdziała z innymi technologiami, a są dostępne tylko dla innego `DataContractSerializer` wystąpienia, również przy użyciu `preserveObjectReferences` równa `true`.  
  
-   Brak obsługi metadanych (schemat) dla tej funkcji. Schemat, który jest generowany jest prawidłowy tylko w przypadku gdy `preserveObjectReferences` ustawiono `false`.  
  
-   Ta funkcja może spowodować procesu serializacji i deserializacji wolniejsze działanie. Mimo, że dane nie muszą być replikowane, dodatkowy obiekt porównania muszą być wykonywane w tym trybie.  
  
> [!CAUTION]
>  Gdy `preserveObjectReferences` jest włączony tryb, jest szczególnie ważne, aby ustawić `maxItemsInObjectGraph` wartość prawidłowy limit przydziału. Ze względu na sposób tablice są obsługiwane w tym trybie, to proste osobie atakującej do konstruowania małych niebezpieczną wiadomość, która powoduje zużycie pamięci tylko przez ograniczony `maxItemsInObjectGraph` limitu przydziału.  
  
### <a name="specifying-a-data-contract-surrogate"></a>Określanie zastępczy kontraktu danych  
 Niektóre `DataContractSerializer` mają przeciążenia konstruktora `dataContractSurrogate` parametr, który może być ustawiona na `null`. W przeciwnym razie służy do określania *zastępczy kontraktu danych*, który jest typem, który implementuje <xref:System.Runtime.Serialization.IDataContractSurrogate> interfejsu. Można następnie użyć interfejsu dostosować serializacji i deserializacji procesu. Aby uzyskać więcej informacji, zobacz [surogaty kontraktu danych](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).  
  
## <a name="serialization"></a>Serializacja  
 Poniższe informacje dotyczą do każdej klasy, która dziedziczy <xref:System.Runtime.Serialization.XmlObjectSerializer>, w tym <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Runtime.Serialization.NetDataContractSerializer> klasy.  
  
### <a name="simple-serialization"></a>Serializacja prostą  
 Najbardziej podstawową metodą do serializacji obiektu jest przekazywany do <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObject%2A> metody. Istnieją trzy przeciążenia, jeden dla zapisywania <xref:System.IO.Stream>, <xref:System.Xml.XmlWriter>, lub <xref:System.Xml.XmlDictionaryWriter>. Za pomocą <xref:System.IO.Stream> przeciążenia, danych wyjściowych jest XML przy użyciu kodowania UTF-8. Za pomocą <xref:System.Xml.XmlDictionaryWriter> przeciążenia, serializator optymalizuje dane wyjściowe dla binarny kod XML.  
  
 Korzystając z <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObject%2A> metoda, serializator domyślną nazwę i przestrzeń nazw dla elementu otoki i zapisuje go wraz z treści (zobacz poprzednią sekcję "Określanie domyślnej głównej nazwy i Namespace").  
  
 W poniższym przykładzie pokazano zapisu z <xref:System.Xml.XmlDictionaryWriter>.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#8)]
 [!code-vb[c_StandaloneDataContractSerializer#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#8)]  
  
 To daje XML, podobny do następującego.  
  
```xml  
<Person>  
  <Name>Jay Hamlin</Name>  
  <Address>123 Main St.</Address>  
</Person>  
```  
  
### <a name="step-by-step-serialization"></a>Instrukcje krok po kroku serializacji  
 Użyj <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A>, <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObjectContent%2A>, i <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> metody do zapisu elementu końcowego zapis zawartości obiektu i Zamknij element otoki odpowiednio.  
  
> [!NOTE]
>  Istnieją nie <xref:System.IO.Stream> przeciążenia tych metod.  
  
 Ten krok po kroku serializacji ma dwie typowe zastosowania. Jeden jest wstawienie zawartości, takich jak atrybuty lub komentarze między `WriteStartObject` i `WriteObjectContent`, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#9)]
 [!code-vb[c_StandaloneDataContractSerializer#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#9)]  
  
 To daje XML, podobny do następującego.  
  
```xml  
<Person serializedBy="myCode">  
  <Name>Jay Hamlin</Name>  
  <Address>123 Main St.</Address>  
</Person>  
```  
  
 Innym typowym zastosowaniem jest aby unikać <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A> i <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> całości, a także napisać własny element otoki niestandardowe (lub nawet pominąć pisania otokę całkowicie), jak pokazano w poniższym kodzie.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#10)]
 [!code-vb[c_StandaloneDataContractSerializer#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#10)]  
  
 To daje XML, podobny do następującego.  
  
```xml  
<MyCustomWrapper>  
  <Name>Jay Hamlin</Name>  
  <Address>123 Main St.</Address>  
</MyCustomWrapper>  
```  
  
> [!NOTE]
>  Za pomocą serializacji krok po kroku może spowodować nieprawidłowe schematu XML.  
  
## <a name="deserialization"></a>Deserializacja  
 Poniższe informacje dotyczą do każdej klasy, która dziedziczy <xref:System.Runtime.Serialization.XmlObjectSerializer>, w tym <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Runtime.Serialization.NetDataContractSerializer> klasy.  
  
 To najprostszy sposób deserializacji obiektu jest wywoływanie jednego z <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> przeciążenia metody. Istnieją trzy przeciążenia, jeden dla odczytu z <xref:System.Xml.XmlDictionaryReader>, `XmlReader`, lub `Stream`. Należy pamiętać, że `Stream` przeciążenia tworzy tekstową <xref:System.Xml.XmlDictionaryReader> nie jest chroniony przez wykorzystani limitów przydziałów i powinna służyć tylko do odczytu danych zaufanych.  
  
 Należy również zauważyć, że obiekt `ReadObject` metoda zwraca wartość, należy zrzutować do odpowiedniego typu.  
  
 Poniższy kod tworzy wystąpienie klasy <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Xml.XmlDictionaryReader>, następnie deserializuje `Person` wystąpienia.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#11)]
 [!code-vb[c_StandaloneDataContractSerializer#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#11)]  
  
 Przed wywołaniem <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> metodę, umieść odczytującego XML na element otoki lub węzeł-content, który poprzedza element otoki. Można to zrobić, wywołując <xref:System.Xml.XmlReader.Read%2A> metody <xref:System.Xml.XmlReader> ani jego pochodnym i testowania <xref:System.Xml.XmlReader.NodeType%2A>, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#12)]
 [!code-vb[c_StandaloneDataContractSerializer#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#12)]  
  
 Należy pamiętać, że mogą odczytywać atrybuty, w tym elemencie otoki, przed przekazaniem czytelnika `ReadObject`.  
  
 Gdy używany jest jeden prostą `ReadObject` przeciążeń, Deserializator szuka domyślną nazwę i przestrzeni nazw na element otoki (zobacz poprzednią sekcję "Określanie domyślnej głównej nazwy i Namespace") i zgłasza wyjątek, jeśli znajdzie nieznany element. W powyższym przykładzie `<Person>` element otoki jest oczekiwany. <xref:System.Runtime.Serialization.XmlObjectSerializer.IsStartObject%2A> Metoda jest wywoływana, aby sprawdzić, czy czytnik jest umieszczony w elemencie, który nosi nazwę zgodnie z oczekiwaniami.  
  
 Istnieje sposób, aby wyłączyć ten test nazwa element otoki; Niektóre przeciążenia `ReadObject` metoda przyjmować parametr logiczny `verifyObjectName`, która jest równa `true` domyślnie. Po ustawieniu `false`, nazwa i nazw element otoki jest ignorowana. Jest to przydatne w przypadku odczytywania pliku XML, która została opracowana za pomocą mechanizmu serializacji krok po kroku opisanych powyżej.  
  
## <a name="using-the-netdatacontractserializer"></a>Za pomocą NetDataContractSerializer  
 Główną różnicą między `DataContractSerializer` i <xref:System.Runtime.Serialization.NetDataContractSerializer> jest fakt, że `DataContractSerializer` używa nazwy kontraktów danych, natomiast `NetDataContractSerializer` generuje pełną [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] nazwy zestawu i typu w serializacji XML. Oznacza to, że dokładnie te same typy muszą być udostępniane między punktami końcowymi serializacji i deserializacji. To oznacza, że mechanizm znanych typów nie jest wymagane w przypadku `NetDataContractSerializer` ponieważ znane są zawsze dokładnie typów do zdeserializowania.  
  
 Jednak może wystąpić kilka problemów:  
  
-   Zabezpieczenia. Dowolny typ, znaleziono w pliku XML deserializowany jest ładowany. To może być wykorzystywana w celu wymuszenia ładowania typów złośliwego. Za pomocą `NetDataContractSerializer` z niezaufanych danych ma być przeprowadzane tylko wtedy, gdy *wiążącego serializacji* służy (przy użyciu <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder%2A> Konstruktor lub właściwości parametru). Obiekt wiążący zezwala na tylko bezpiecznych typy do załadowania. Mechanizm integratorów modeli jest taka sama jak ten, który wpisuje <xref:System.Runtime.Serialization> Użyj przestrzeni nazw.  
  
-   Przechowywanie wersji. Przy użyciu pełnej nazwy typu i zestawu w pliku XML znacznie ogranicza, jak typy mogą być poddany kontroli wersji. Nie można zmienić następujących: typ nazwy przestrzeni nazw, nazw zestawów i wersji zestawu. Ustawienie <xref:System.Runtime.Serialization.NetDataContractSerializer.AssemblyFormat%2A> Konstruktor lub właściwości parametru, aby <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle.Simple> zamiast wartość domyślną <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle.Full> umożliwia zmiany wersji zestawu, ale nie typy parametrów ogólnych.  
  
-   Współdziałanie. Ponieważ [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typ i zestaw nazw znajdują się w pliku XML, platform innych niż [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] nie może uzyskać dostęp do danych wynikowych.  
  
-   Wydajność. Wypisywanie typ i zestaw nazw znacznie zwiększa rozmiar wynikowy kod XML.  
  
 Mechanizm ten jest podobny do pliku binarnego lub protokołu SOAP serializacji używany przez [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Komunikacja zdalna (w szczególności <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> i <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>).  
  
 Za pomocą `NetDataContractSerializer` jest podobne do `DataContractSerializer`, z następującymi różnicami:  
  
-   Konstruktory nie wymagają określenia typu głównego. Może wykonywać serializację dowolnego typu za pomocą tego samego wystąpienia `NetDataContractSerializer`.  
  
-   Konstruktory nie akceptuje listę znanych typów. Mechanizm znanych typów nie jest konieczne, jeśli nazwy typów są serializowane w kodzie XML.  
  
-   Konstruktory nie akceptują zastępczy kontraktu danych. Zamiast tego przyjmują <xref:System.Runtime.Serialization.ISurrogateSelector> parametr o nazwie `surrogateSelector` (która mapuje do <xref:System.Runtime.Serialization.NetDataContractSerializer.SurrogateSelector%2A> właściwości). Jest to mechanizm zastępczy starszej wersji.  
  
-   Konstruktory akceptuje parametr o nazwie `assemblyFormat` z <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle> mapujący do <xref:System.Runtime.Serialization.NetDataContractSerializer.AssemblyFormat%2A> właściwości. Jak wspomniano wcześniej, to może służyć do zwiększenia możliwości przechowywania wersji wybrania serializatora. To jest taka sama jak <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle> mechanizm w pliku binarnego lub serializacji protokołu SOAP.  
  
-   Zaakceptuj konstruktory <xref:System.Runtime.Serialization.StreamingContext> parametr o nazwie `context` mapujący do <xref:System.Runtime.Serialization.NetDataContractSerializer.Context%2A> właściwości. Służy to do przekazywania informacji do serializacji typów. To obciążenie jest taka sama jak w przypadku <xref:System.Runtime.Serialization.StreamingContext> mechanizm używany w innych <xref:System.Runtime.Serialization> klasy.  
  
-   <xref:System.Runtime.Serialization.NetDataContractSerializer.Serialize%2A> i <xref:System.Runtime.Serialization.NetDataContractSerializer.Deserialize%2A> metody są aliasami <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObject%2A> i <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> metody. Istnieją one w celu zapewnienia bardziej spójny model programowania przy użyciu pliku binarnego lub serializacji protokołu SOAP.  
  
 Aby uzyskać więcej informacji o tych funkcjach, zobacz [serializacji binarnej](../../../../docs/standard/serialization/binary-serialization.md).  
  
 Formatów XML, który `NetDataContractSerializer` i `DataContractSerializer` Użyj zwykle nie są zgodne. Oznacza to, że próby serializacji przy użyciu jednego z tych serializatory i deserializacji razem z innymi nie jest obsługiwanym scenariuszem.  
  
 Ponadto należy pamiętać, że `NetDataContractSerializer` nie wyświetla pełną [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typ i nazwa zestawu dla każdego węzła na grafie obiektu. Wyświetla te informacje tylko gdzie jest niejednoznaczny. Oznacza to generuje na poziomie obiektu głównego i polimorficznych przypadki.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.NetDataContractSerializer>
- <xref:System.Runtime.Serialization.XmlObjectSerializer>
- [Serializacja binarna](../../../../docs/standard/serialization/binary-serialization.md)
- [Typy obsługiwane przez serializator kontraktu danych](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)
