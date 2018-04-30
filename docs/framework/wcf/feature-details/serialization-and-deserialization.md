---
title: Serializacja i deserializacja
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 3d71814c-bda7-424b-85b7-15084ff9377a
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2343ebe5a2a029ddb40da98d28f5c442aa7b6962
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="serialization-and-deserialization"></a>Serializacja i deserializacja
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] obejmuje nowy aparat serializacji <xref:System.Runtime.Serialization.DataContractSerializer>. <xref:System.Runtime.Serialization.DataContractSerializer> Tłumaczy [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] obiektów i XML w obu kierunkach. W tym temacie wyjaśniono, jak działa serializatora.  
  
 Podczas serializowania [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] obiektów, serializator zrozumienie różnych serializacji programowania modeli, w tym nowe *kontraktu danych* modelu. Aby uzyskać pełną listę obsługiwanych typów, zobacz [typy obsługiwane przez serializator kontraktu danych](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md). Aby obejrzeć wprowadzenie do kontraktów danych, zobacz [za pomocą kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 Podczas deserializacji XML, używa serializator <xref:System.Xml.XmlReader> i <xref:System.Xml.XmlWriter> klasy. Obsługuje ona również <xref:System.Xml.XmlDictionaryReader> i <xref:System.Xml.XmlDictionaryWriter> klasy, aby włączyć go do produkcji zoptymalizowanych pod kątem XML w niektórych przypadkach, takich jak przy użyciu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] binarny format XML.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zawiera również element serializujący Pomocnika <xref:System.Runtime.Serialization.NetDataContractSerializer>. <xref:System.Runtime.Serialization.NetDataContractSerializer> Jest podobny do <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> i <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> serializatorów ponieważ również emituje [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] wpisz nazwy w ramach danych serializacji. Jest używany, gdy te same typy są udostępniane na serializacja i deserializacja zakończenia. Zarówno <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Runtime.Serialization.NetDataContractSerializer> pochodzi od wspólna klasa podstawowa <xref:System.Runtime.Serialization.XmlObjectSerializer>.  
  
> [!WARNING]
>  <xref:System.Runtime.Serialization.DataContractSerializer> Serializuje ciągi zawierające znaki kontrolne o wartości szesnastkowej poniżej 20 jako jednostki XML. Może to spowodować problem z klienta z systemem innym niż WCF podczas wysyłania tych danych do usługi WCF.  
  
## <a name="creating-a-datacontractserializer-instance"></a>Tworzenie wystąpienia elementu DataContractSerializer  
 Utworzenie wystąpienia <xref:System.Runtime.Serialization.DataContractSerializer> to ważny krok. Po wykonaniu konstrukcji nie można zmienić dowolne z ustawień.  
  
### <a name="specifying-the-root-type"></a>Określanie typu głównego  
 *Typ główny* jest to typ, którego serializowany lub deserializowany wystąpień. <xref:System.Runtime.Serialization.DataContractSerializer> Ma wiele przeciążeń konstruktora, ale co najmniej, należy podać typ główny przy użyciu `type` parametru.  
  
 Element serializujący utworzone dla określonego typu głównego nie można użyć do serializacji (lub deserializacji) innego typu, chyba że typ pochodzi od typu głównego. W poniższym przykładzie przedstawiono dwie klasy.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#1)]
 [!code-vb[c_StandaloneDataContractSerializer#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#1)]  
  
 Ten kod tworzy wystąpienie klasy `DataContractSerializer` który może służyć tylko do serializacji lub deserializacji wystąpienia `Person` klasy.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#2)]
 [!code-vb[c_StandaloneDataContractSerializer#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#2)]  
  
### <a name="specifying-known-types"></a>Określanie znanych typów  
 Jeśli polimorfizm uczestniczy w typach serializowana, które nie jest już obsługiwana za pomocą <xref:System.Runtime.Serialization.KnownTypeAttribute> atrybutu lub innych mechanizmu listę możliwych znane typy muszą być przekazywane do konstruktora serializatora za pomocą `knownTypes` parametru. Aby uzyskać więcej informacji na temat znanych typów, zobacz [znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
 W poniższym przykładzie przedstawiono klasę, `LibraryPatron`, który zawiera kolekcję określonego typu `LibraryItem`. Definiuje klasę sekundę `LibraryItem` typu. Trzeci i cztery klasy (`Book` i `Newspaper`) dziedziczyć `LibraryItem` klasy.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#3)]  
 [!code-vb[c_StandaloneDataContractSerializer#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#3)]  
  
 Poniższy kod tworzy wystąpienie klasy przy użyciu serializatora `knownTypes` parametru.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#4)]
 [!code-vb[c_StandaloneDataContractSerializer#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#4)]  
  
### <a name="specifying-the-default-root-name-and-namespace"></a>Określanie domyślną nazwę katalogu głównego i Namespace  
 Zwykle podczas serializowany jest obiekt, domyślną nazwę i przestrzeń nazw elementu XML najbardziej zewnętrznego są określane zgodnie z nazwą kontraktu danych i przestrzeni nazw. Nazwy wszystkich elementów wewnętrzny zależą od nazw elementów członkowskich danych i ich przestrzeń nazw jest przestrzeń nazw kontraktu danych. W poniższym przykładzie `Name` i `Namespace` wartości konstruktorów <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> klasy.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#5)]
 [!code-vb[c_StandaloneDataContractSerializer#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#5)]  
  
 Serializacji wystąpienia `Person` klasę XML podobny do następującego.  
  
```xml  
<PersonContract xmlns="http://schemas.contoso.com">  
  <AddressMember>  
    <StreetMember>123 Main Street</StreetMember>  
   </AddressMember>  
</PersonContract>  
```  
  
 Jednak można dostosować domyślną nazwę i przestrzeń nazw głównego elementu przez przekazanie wartości `rootName` i `rootNamespace` parametry <xref:System.Runtime.Serialization.DataContractSerializer> konstruktora. Należy pamiętać, że `rootNamespace` nie ma wpływu na przestrzeń nazw zawartych w niej elementów, które odnoszą się do elementów członkowskich danych. Wpływa on tylko przestrzeń nazw elementu najbardziej zewnętrznego.  
  
 Te wartości mogą być przekazywane jako parametry lub wystąpień <xref:System.Xml.XmlDictionaryString> klasy, aby umożliwić ich Optymalizacja za pomocą binarny format XML.  
  
### <a name="setting-the-maximum-objects-quota"></a>Ustawienie limitu przydziału maksymalnej obiektów  
 Niektóre `DataContractSerializer` mają przeciążenia konstruktora `maxItemsInObjectGraph` parametru. Ten parametr określa maksymalną liczbę obiektów serializator serializuje i deserializuje w jednej <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> wywołania metody. (Metoda odczytuje zawsze jednego obiektu głównego, ale ten obiekt może mieć inne obiekty w jej elementów członkowskich danych. Te obiekty mogą mieć inne obiekty itd.) Wartość domyślna to 65536. Należy pamiętać, że podczas serializacji lub deserializacji tablic, każdy wpis tablicy jest traktowana jako oddzielny obiekt. Należy również zauważyć, że niektóre obiekty mogą ma reprezentacji w postaci dużej ilości pamięci, a więc tego samego przydziału nie może być wystarczające, aby zapobiec typu "odmowa usługi". Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące zabezpieczeń dla danych](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md). Jeśli potrzebujesz zwiększyć ten przydział ponad wartość domyślną, należy to zrobić zarówno na wysyłanie (serializację) i odbieranie strony (deserializacji), ponieważ dotyczy zarówno podczas odczytywania i zapisywania danych.  
  
### <a name="round-trips"></a>Rund  
 A *Rundy* występuje, gdy obiekt jest zdeserializować i ponownie zserializowane w jednej operacji. W związku z tym z pliku XML do wystąpienia obiektu i z powrotem ponownie umieszczanej w kodzie to strumień XML.  
  
 Niektóre `DataContractSerializer` mają przeciążenia konstruktora `ignoreExtensionDataObject` parametr, który ma ustawioną wartość `false` domyślnie. W tym trybie domyślne można wysyłać dane na podróż z nowszej wersji kontraktu danych za pomocą starszej wersji i z powrotem do nowszej wersji bez utraty, jak długo implementuje kontraktu danych <xref:System.Runtime.Serialization.IExtensibleDataObject> interfejsu. Na przykład, załóżmy, że wersja 1 `Person` zawiera kontrakt danych `Name` i `PhoneNumber` elementów członkowskich danych i w wersji 2 dodaje `Nickname` elementu członkowskiego. Jeśli `IExtensibleDataObject` zaimplementowano podczas wysyłania informacji z wersji 2 do wersji 1, `Nickname` dane są przechowywane i następnie ponownie wysyłanego, gdy dane są serializowane ponownie; w związku z tym nie dane zostaną utracone w obiegu. Aby uzyskać więcej informacji, zobacz [kontrakty danych zgodne z nowszymi](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md) i [przechowywanie wersji kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md).  
  
#### <a name="security-and-schema-validity-concerns-with-round-trips"></a>Zabezpieczenia i problemy ważności schematu z wystąpień komunikacji dwustronnej  
 Rund może mieć wpływ na bezpieczeństwo. Na przykład podczas deserializacji i przechowywania dużych ilości danych nadmiarowe może stanowić zagrożenie bezpieczeństwa. Może być ponownie emitowanie te dane, że nie istnieje sposób, aby sprawdzić, zwłaszcza jeśli podpisy cyfrowe są związane z punktu widzenia bezpieczeństwa. Na przykład w poprzednim scenariuszu punkt końcowy w wersji 1 można podpisać `Nickname` wartość, która zawiera dane złośliwe. Ponadto może być zastrzeżenia co do poprawności schematu: punkt końcowy może być zawsze Emituj danych zgodną ściśle jej podane kontrakt i nie wszystkie dodatkowe wartości. W poprzednim przykładzie kontraktu punktu końcowego w wersji 1 mówi tylko emituje `Name` i `PhoneNumber`i jeśli sprawdzanie poprawności schematu jest używana, emitowanie nadmiarowe `Nickname` wartość powoduje niepowodzenie sprawdzania poprawności.  
  
#### <a name="enabling-and-disabling-round-trips"></a>Włączanie i wyłączanie rund  
 Aby wyłączyć rund, nie należy implementować <xref:System.Runtime.Serialization.IExtensibleDataObject> interfejsu. Jeśli użytkownik nie kontrolują typy, ustaw `ignoreExtensionDataObject` parametr `true` osiągnąć ten sam efekt.  
  
### <a name="object-graph-preservation"></a>Obiekt wykresu konserwacji  
 Zwykle Serializator nie interesujących tożsamości obiektu, zgodnie z poniższym kodem.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#6)]
 [!code-vb[c_StandaloneDataContractSerializer#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#6)]  
  
 Poniższy kod tworzy zamówienia zakupu.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#7)]
 [!code-vb[c_StandaloneDataContractSerializer#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#7)]  
  
 Zwróć uwagę, że `billTo` i `shipTo` pola są ustawione w tym samym wystąpieniu obiektu. Jednak XML wygenerowanych duplikaty zduplikowane informacje i wygląda podobnie do następującego pliku XML.  
  
```xml  
<PurchaseOrder>  
  <billTo><street>123 Main St.</street></billTo>  
  <shipTo><street>123 Main St.</street></shipTo>  
</PurchaseOrder>  
```  
  
 Jednak takie podejście ma następujące właściwości, które mogą być niepożądane:  
  
-   Wydajność. Replikowanie danych jest nieefektywne.  
  
-   Odwołania cykliczne. Jeśli obiekty odwołują się do siebie, nawet za pośrednictwem innych obiektów serializacji za pomocą replikacji powoduje nieskończoną pętlę. (Serializator zgłasza <xref:System.Runtime.Serialization.SerializationException> w takim przypadku.)  
  
-   Semantyki. Czasami jest ważne zachować fakt, że są dwa odwołania do tego samego obiektu, a nie dwa obiekty identyczne.  
  
 Te powodów, niektóre `DataContractSerializer` mają przeciążenia konstruktora `preserveObjectReferences` parametr (wartość domyślna to `false`). Jeśli ten parametr jest równa `true`, odwołuje się specjalnej metody obiekt kodowania, które tylko [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] rozumie, jest używany. Jeśli wartość `true`, przykładowy kod XML jest teraz podobny do następującego.  
  
```xml  
<PurchaseOrder ser:id="1">  
  <billTo ser:id="2"><street ser:id="3">123 Main St.</street></billTo>  
  <shipTo ser:ref="2"/>  
</PurchaseOrder>  
```  
  
 Przestrzeń nazw "ser" odwołuje się do przestrzeni nazw standardowe serializacji, http://schemas.microsoft.com/2003/10/Serialization/. Każdy element danych jest serializować tylko raz i podany identyfikator i kolejne używa wynik odwołanie do danych już serializacji.  
  
> [!IMPORTANT]
>  Jeśli atrybuty zarówno "id" i "ref" są obecne w kontraktu danych `XMLElement`, jest honorowane atrybutu "ref" i "id" atrybut jest ignorowany.  
  
 Należy pamiętać o ograniczeniach ten tryb:  
  
-   Kod XML `DataContractSerializer` tworzy z `preserveObjectReferences` ustawioną `true` nie jest współpraca z innymi technologiami i jest możliwy tylko przez inną `DataContractSerializer` wystąpienia, także z `preserveObjectReferences` ustawioną `true`.  
  
-   Brak obsługi metadanych (schemat) dla tej funkcji. Schemat, który jest tworzony jest prawidłowe tylko w przypadku gdy `preserveObjectReferences` ma ustawioną wartość `false`.  
  
-   Ta funkcja może spowodować serializacji i deserializacji procesu działać wolniej. Mimo że dane muszą zostać zreplikowane, należy wykonać dodatkowy obiekt porównania w tym trybie.  
  
> [!CAUTION]
>  Gdy `preserveObjectReferences` jest włączony tryb, jest szczególnie ważne, aby ustawić `maxItemsInObjectGraph` wartość przydziału poprawne. Ze względu na sposób tablice są obsługiwane w tym trybie jest łatwe osobie atakującej do skonstruowania małych niebezpieczną wiadomość, która powoduje zużycie pamięci dużych ograniczone tylko przez `maxItemsInObjectGraph` przydziału.  
  
### <a name="specifying-a-data-contract-surrogate"></a>Określanie Surogat kontraktu danych  
 Niektóre `DataContractSerializer` mają przeciążenia konstruktora `dataContractSurrogate` parametr, który może być ustawiony na `null`. W przeciwnym razie go użyć do określenia *Surogat kontraktu danych*, który jest typem, który implementuje <xref:System.Runtime.Serialization.IDataContractSurrogate> interfejsu. Interfejs umożliwia następnie dostosować serializacji i deserializacji procesu. Aby uzyskać więcej informacji, zobacz [surogaty kontraktu danych](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).  
  
## <a name="serialization"></a>Serializacja  
 Poniższe informacje dotyczą dowolnej klasy, która dziedziczy <xref:System.Runtime.Serialization.XmlObjectSerializer>, takie jak <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Runtime.Serialization.NetDataContractSerializer> klasy.  
  
### <a name="simple-serialization"></a>Proste serializacji  
 Najprostszym sposobem szeregowania obiektu jest przekazywany do <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObject%2A> metody. Istnieją trzy przeciążenia, jeden dla zapisywania <xref:System.IO.Stream>, <xref:System.Xml.XmlWriter>, lub <xref:System.Xml.XmlDictionaryWriter>. Z <xref:System.IO.Stream> przeciążenia, dane wyjściowe jest XML przy użyciu kodowania UTF-8. Z <xref:System.Xml.XmlDictionaryWriter> przeciążenia, serializator optymalizuje dane wyjściowe dla Binarny XML.  
  
 Korzystając z <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObject%2A> metoda, serializator domyślną nazwę i przestrzeń nazw dla elementu otoki i zapisuje go wraz z zawartością (zobacz poprzednią sekcję "Określenie domyślnego głównego Name i Namespace").  
  
 W poniższym przykładzie pokazano zapisu z <xref:System.Xml.XmlDictionaryWriter>.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#8)]
 [!code-vb[c_StandaloneDataContractSerializer#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#8)]  
  
 Daje to XML podobny do następującego.  
  
```xml  
<Person>  
  <Name>Jay Hamlin</Name>  
  <Address>123 Main St.</Address>  
</Person>  
```  
  
### <a name="step-by-step-serialization"></a>Serializacja krok po kroku  
 Użyj <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A>, <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObjectContent%2A>, i <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> metod można zapisać elementu końcowego zapis zawartości obiektu i odpowiednio Zamknij element otoki.  
  
> [!NOTE]
>  Istnieją nie <xref:System.IO.Stream> przeciążenia tych metod.  
  
 Ten krok serializacji ma dwa typowych zastosowań. Jedna jest do wstawiania zawartości, takich jak atrybuty lub komentarzy między `WriteStartObject` i `WriteObjectContent`, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#9)]
 [!code-vb[c_StandaloneDataContractSerializer#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#9)]  
  
 Daje to XML podobny do następującego.  
  
```xml  
<Person serializedBy="myCode">  
  <Name>Jay Hamlin</Name>  
  <Address>123 Main St.</Address>  
</Person>  
```  
  
 Inny zazwyczaj jest używane, aby uniknąć używania <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A> i <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> całkowicie, napisać własny element otoki niestandardowe (lub nawet Pomiń zapisywanie otoka całkowicie), jak pokazano w poniższym kodzie.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#10)]
 [!code-vb[c_StandaloneDataContractSerializer#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#10)]  
  
 Daje to XML podobny do następującego.  
  
```xml  
<MyCustomWrapper>  
  <Name>Jay Hamlin</Name>  
  <Address>123 Main St.</Address>  
</MyCustomWrapper>  
```  
  
> [!NOTE]
>  Za pomocą serializacji krok może spowodować nieprawidłowe schematu XML.  
  
## <a name="deserialization"></a>Deserializacja  
 Poniższe informacje dotyczą dowolnej klasy, która dziedziczy <xref:System.Runtime.Serialization.XmlObjectSerializer>, takie jak <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Runtime.Serialization.NetDataContractSerializer> klasy.  
  
 Najprostszym sposobem deserializacji obiektu jest wywoływanie jednego z <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> przeciążenia metody. Istnieją trzy przeciążenia, jeden dla odczytu z <xref:System.Xml.XmlDictionaryReader>, `XmlReader`, lub `Stream`. Należy pamiętać, że `Stream` przeciążenia tworzy tekstową <xref:System.Xml.XmlDictionaryReader> nie jest chroniony przez dowolnego przydziałów i powinien być używany tylko do odczytu danych zaufanych.  
  
 Należy również zauważyć, że obiekt `ReadObject` metoda zwróci wartość musi być rzutowane na odpowiedniego typu.  
  
 Poniższy kod tworzy wystąpienie klasy <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Xml.XmlDictionaryReader>, następnie deserializuje `Person` wystąpienia.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#11)]
 [!code-vb[c_StandaloneDataContractSerializer#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#11)]  
  
 Przed wywołaniem <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> metodę, umieść modułu odczytującego XML na element otoki lub węzłem z systemem innym niż zawartości, który poprzedza element otoki. Można to zrobić przez wywołanie metody <xref:System.Xml.XmlReader.Read%2A> metody <xref:System.Xml.XmlReader> ani jego pochodnym i testowania <xref:System.Xml.XmlReader.NodeType%2A>, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#12)]
 [!code-vb[c_StandaloneDataContractSerializer#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#12)]  
  
 Należy pamiętać, że mogą odczytywać atrybuty w tym elemencie otoki, przed przekazaniem czytelnika `ReadObject`.  
  
 Korzystając z jednego miejsca proste `ReadObject` przeciążenia, Deserializator szuka domyślną nazwę i przestrzeń nazw dla elementu otoki (zobacz poprzednią sekcję "Określenie domyślnego głównego Name i Namespace") i zgłasza wyjątek, jeśli znajdzie nieznany element. W powyższym przykładzie `<Person>` oczekuje elementu otoki. <xref:System.Runtime.Serialization.XmlObjectSerializer.IsStartObject%2A> Metoda jest wywoływana, aby sprawdzić, czy czytnik jest umieszczony w elemencie o nazwie zgodnie z oczekiwaniami.  
  
 Nie istnieje sposób, aby wyłączyć to sprawdzenie nazwa elementu otoki; Niektóre przeciążeń `ReadObject` metoda przyjmować parametrów typu Boolean `verifyObjectName`, która ma wartość `true` domyślnie. Jeśli wartość `false`, nazwę i przestrzeń nazw elementu otoki jest ignorowana. Jest to przydatne podczas odczytywania pliku XML, napisane przy użyciu mechanizmu serializacji krok po kroku opisanych powyżej.  
  
## <a name="using-the-netdatacontractserializer"></a>Przy użyciu NetDataContractSerializer  
 Główną różnicą między `DataContractSerializer` i <xref:System.Runtime.Serialization.NetDataContractSerializer> jest to, że `DataContractSerializer` używa nazwy kontraktu danych, podczas gdy `NetDataContractSerializer` generuje pełny [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] nazwy zestawu i typu serializacji XML. Oznacza to, że dokładnie takie same typy muszą być udostępniane między punktami końcowymi serializacji i deserializacji. Oznacza to mechanizm znanych typów nie jest wymagane w przypadku `NetDataContractSerializer` ponieważ znane są zawsze dokładnie typów do zdeserializowania.  
  
 Jednak może wystąpić pewne problemy:  
  
-   Zabezpieczenia. Załadowano dowolnego typu w pliku XML deserializacji. Można to wykorzystać, aby wymusić ładowania typów złośliwego. Przy użyciu `NetDataContractSerializer` z niezaufanych danych należy przypisywać tylko wtedy, gdy *wiążącego serializacji* jest używana (przy użyciu <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder%2A> parametrów właściwości lub konstruktora). Obiekt wiążący zezwala na tylko bezpiecznych typów do załadowania. Mechanizm integratora jest taki sam jak ten, który typy w <xref:System.Runtime.Serialization> Użyj przestrzeni nazw.  
  
-   Przechowywanie wersji. Przy użyciu pełnej nazwy typ i zestaw w pliku XML znacznie ogranicza jak typy mogą być numerów wersji. Nie można zmienić następujących: wpisz nazwy przestrzeni nazw, nazw zestawów i wersji zestawu. Ustawienie <xref:System.Runtime.Serialization.NetDataContractSerializer.AssemblyFormat%2A> właściwości lub konstruktora parametr <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle.Simple> zamiast wartość domyślną <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle.Full> umożliwia zmiany wersji zestawu, ale nie dla typów parametrów ogólnych.  
  
-   Współdziałanie. Ponieważ [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] nazwy typ i zestaw są dołączane do pliku XML, platform innych niż [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] nie może uzyskać dostępu do danych.  
  
-   Wydajność. Wypisywanie typ i zestaw nazwy znacznie zwiększa rozmiar wynikowy kod XML.  
  
 Mechanizm ten jest podobny do pliku binarnego lub serializacji SOAP używane przez [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zdalnych (w szczególności <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> i <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>).  
  
 Przy użyciu `NetDataContractSerializer` jest podobny do sposobu używania `DataContractSerializer`, z następującymi różnicami:  
  
-   Konstruktory nie wymagają określenia typu głównego. Może wykonywać serializację dowolnego typu tego samego wystąpienia `NetDataContractSerializer`.  
  
-   Konstruktory nie akceptują listy znanych typów. Mechanizm znanych typów nie jest konieczne, jeśli nazwy typów są serializowane w pliku XML.  
  
-   Konstruktory nie akceptują Surogat kontraktu danych. Zamiast tego należy zaakceptować <xref:System.Runtime.Serialization.ISurrogateSelector> parametr o nazwie `surrogateSelector` (który mapuje <xref:System.Runtime.Serialization.NetDataContractSerializer.SurrogateSelector%2A> właściwości). Jest to mechanizm Surogat starszej wersji.  
  
-   Konstruktory akceptuje parametr o nazwie `assemblyFormat` z <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle> mapujący do <xref:System.Runtime.Serialization.NetDataContractSerializer.AssemblyFormat%2A> właściwości. Jak wspomniano wcześniej, może być używany w celu zwiększenia możliwości przechowywania wersji serializator. Jest to identyczne <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle> mechanizm w pliku binarnego lub serializacji SOAP.  
  
-   Zaakceptuj konstruktorów <xref:System.Runtime.Serialization.StreamingContext> parametr o nazwie `context` mapujący do <xref:System.Runtime.Serialization.NetDataContractSerializer.Context%2A> właściwości. Służy to do przekazywania informacji do serializacji typów. Użycie tego jest identyczna ze <xref:System.Runtime.Serialization.StreamingContext> mechanizmem używanym w innych <xref:System.Runtime.Serialization> klasy.  
  
-   <xref:System.Runtime.Serialization.NetDataContractSerializer.Serialize%2A> i <xref:System.Runtime.Serialization.NetDataContractSerializer.Deserialize%2A> metody są aliasami <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObject%2A> i <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> metody. Istnieją one w celu zapewnienia bardziej spójny model programowania z pliku binarnego lub serializacji SOAP.  
  
 Aby uzyskać więcej informacji o tych funkcjach, zobacz [szeregowanie binarne](../../../../docs/standard/serialization/binary-serialization.md).  
  
 Formatów XML, który `NetDataContractSerializer` i `DataContractSerializer` użycia zazwyczaj nie są zgodne. Oznacza to, że próby serializacji jednego z tych serializatorów i deserializacji z innym nie jest obsługiwanym scenariuszem.  
  
 Ponadto należy pamiętać, że `NetDataContractSerializer` Wyprowadza pełny [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typ i nazwa zestawu dla każdego węzła na wykresie obiektu. Generuje on te informacje, tylko gdy jest niejednoznaczna. Oznacza to generuje na poziomie obiektu głównego i dla innych przypadków polimorficznym.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Runtime.Serialization.NetDataContractSerializer>  
 <xref:System.Runtime.Serialization.XmlObjectSerializer>  
 [Serializacja binarna](../../../../docs/standard/serialization/binary-serialization.md)  
 [Typy obsługiwane przez serializator kontraktu danych](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)
