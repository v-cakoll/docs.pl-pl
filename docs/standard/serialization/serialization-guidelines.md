---
title: Wskazówki dotyczące serializacji
description: Ten dokument zawiera wskazówki, które należy wziąć pod uwagę podczas projektowania interfejsu API do serializacji, oraz podsumowanie trzech głównych oferowanych przez platformę .NET technologii serializacji.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serialization, guidelines
- binary serialization, guidelines
ms.assetid: ebbeddff-179d-443f-bf08-9c373199a73a
ms.openlocfilehash: eb11f0b8ddd34df7c6970c275d4b83cb95f59a53
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "84287496"
---
# <a name="serialization-guidelines"></a>Wskazówki dotyczące serializacji
Ten dokument zawiera listę wskazówek, które należy wziąć pod uwagę podczas projektowania interfejs API serializacji.  

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
 Platforma .NET oferuje trzy główne technologie serializacji, które są zoptymalizowane pod kątem różnych scenariuszy serializacji. W poniższej tabeli wymieniono technologie i główne typy .NET związane z tymi technologiami.  
  
|Technologia|Odpowiednich klas|Uwagi|  
|----------------|----------------------|-----------|  
|Serializacja kontrakt danych|<xref:System.Runtime.Serialization.DataContractAttribute><br /><br /> <xref:System.Runtime.Serialization.DataMemberAttribute><br /><br /> <xref:System.Runtime.Serialization.DataContractSerializer><br /><br /> <xref:System.Runtime.Serialization.NetDataContractSerializer><br /><br /> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer><br /><br /> <xref:System.Runtime.Serialization.ISerializable>|Trwałość ogólne<br /><br /> Usługi sieci Web<br /><br /> JSON|  
|Serializacji XML|<xref:System.Xml.Serialization.XmlSerializer>|XML format <br />z pełną kontrolę|  
|Środowisko wykonawcze-serializacji (binarnych i protokołu SOAP)|<xref:System.SerializableAttribute><br /><br /> <xref:System.Runtime.Serialization.ISerializable><br /><br /> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter><br /><br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>|Wywołaniem funkcji zdalnych .NET|  
  
 Podczas projektowania nowych typów, należy zdecydować, które ewentualnie technologii te typy muszą obsługiwać. Poniższe wskazówki opisano sposób, aby wybrać i jak zapewnić obsługę takich. Te wytyczne nie mają na celu ułatwienie wyboru technologii serializacji, która ma być używana w implementacji aplikacji lub biblioteki. Takie wytyczne nie są bezpośrednio związane z interfejsu API projektowania i w związku z tym nie są w zakresie tego tematu.  
  
## <a name="guidelines"></a>Wytyczne  
  
- Zastanowić serializacji podczas projektowania nowych typów.  
  
     Serializacji jest ważna projektowania dla dowolnego typu, ponieważ programy może być wymagane do utrwalenia lub przesłania wystąpienie typu.  
  
### <a name="choosing-the-right-serialization-technology-to-support"></a>Wybieranie odpowiedniej technologii serializacji do obsługi  
 Dla dowolnego typu może obsługiwać none, co najmniej jedną z technologii serializacji.  
  
- NALEŻY rozważyć obsługę *serializacji kontraktu danych* , jeśli wystąpienia typu mogą wymagać utrwalenia lub użycia w usługach sieci Web.  
  
- Rozważ obsługę *serializacji XML* zamiast lub oprócz serializacji kontraktu danych, jeśli potrzebna jest większa kontrola nad formatem XML, który jest generowany, gdy typ jest serializowany.  
  
     Może to być konieczne w niektórych scenariuszach współdziałania, w których należy użyć konstrukcji XML, która nie jest obsługiwana przez serializacji kontraktu danych, na przykład w celu utworzenia atrybutów XML.  
  
- Rozważ obsługę *serializacji środowiska uruchomieniowego* , jeśli wystąpienia typu muszą poruszać się w granicach komunikacji zdalnej platformy .NET.  
  
- UNIKAJ obsługi czasu wykonywania serializacji lub serializacji XML tylko dla trwałości głównej przyczyny. Zamiast tego użyć serializacji kontrakt danych  
  
#### <a name="supporting-data-contract-serialization"></a>Obsługa serializacji kontraktu danych  
 Typy mogą obsługiwać serializacji kontraktu danych przez zastosowanie <xref:System.Runtime.Serialization.DataContractAttribute> do typu i <xref:System.Runtime.Serialization.DataMemberAttribute> do elementów członkowskich (pól i właściwości) typu.  
  
 [!code-csharp[SerializationGuidelines#1](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#1)]
 [!code-vb[SerializationGuidelines#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#1)]  
  
1. Należy rozważyć oznaczanie elementów członkowskich danych tego typu publiczne, jeśli typ może być używany w częściowej relacji zaufania. W pełnej relacji zaufania serializatory umowy danych mogą serializacji i deserializacji niepublicznych typy i elementy członkowskie, ale tylko publiczne elementy Członkowskie mogą być serializacji i deserializacji w częściowej relacji zaufania.  
  
2. NALEŻY zaimplementować metody pobierającej i ustawiającej we wszystkich właściwościach, które mają element Memberattribute. Serializatory umowy danych wymagają zarówno getter i setter dla typu, który ma być brany pod uwagę serializacji. Jeśli typ nie można używać w częściowej relacji zaufania, co najmniej jeden z metody dostępu właściwości można niepublicznych.  
  
     [!code-csharp[SerializationGuidelines#2](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#2)]
     [!code-vb[SerializationGuidelines#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#2)]  
  
3. Należy rozważyć użycie wywołania zwrotne serializacji dla inicjowania wystąpień zdeserializowany.  
  
     Konstruktorów nie są wywoływane, gdy obiekty są deserializacji. W związku z tym każda logika, która jest wykonywana podczas normalnej konstrukcji, musi być zaimplementowana jako jedno z *wywołań zwrotnych serializacji*.  
  
     [!code-csharp[SerializationGuidelines#3](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#3)]
     [!code-vb[SerializationGuidelines#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#3)]  
  
     <xref:System.Runtime.Serialization.OnDeserializedAttribute> Atrybutu jest atrybutem najczęściej używane wywołania zwrotnego. Inne atrybuty w rodzinie to <xref:System.Runtime.Serialization.OnDeserializingAttribute> , <xref:System.Runtime.Serialization.OnSerializingAttribute> , i <xref:System.Runtime.Serialization.OnSerializedAttribute> . One służy do oznaczania wywołania zwrotne, które są wykonywane przed deserializacji, przed serializacji, a na końcu po serializacji, odpowiednio.  
  
4. Rozważ użycie elementu <xref:System.Runtime.Serialization.KnownTypeAttribute> do wskazania konkretnych typów, które powinny być używane podczas deserializacji grafu złożonego obiektu.  
  
     Na przykład, jeśli typ deserializowanego elementu członkowskiego danych jest reprezentowany przez klasę abstrakcyjną, serializator będzie potrzebował informacji o *znanym typie* , aby określić konkretny typ do wystąpienia i przypisać do elementu członkowskiego. Jeśli znany typ nie jest określony przy użyciu atrybutu, należy przekazać go do serializatora jawnie (można to zrobić, przekazując znane typy do konstruktora serializatora) lub trzeba go określić w pliku konfiguracji.  
  
     [!code-csharp[SerializationGuidelines#4](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#4)]
     [!code-vb[SerializationGuidelines#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#4)]  
  
     W przypadkach, gdy lista znanych typów nie jest znana statycznie (podczas kompilowania klasy **osoba** ), element **KnownTypeAttribute** może również wskazywać na metodę, która zwraca listę znanych typów w czasie wykonywania.  
  
5. Należy wziąć pod uwagę zgodność z poprzednimi wersjami i do przodu, podczas tworzenia lub zmiany typów możliwych do serializacji.  
  
     Należy pamiętać, który serializowany strumieni przyszłych wersjach tego typu mogą zostać przeprowadzona deserializacja bieżącą wersję tego typu i na odwrót. Upewnij się, że rozumiesz, że członkowie danych, nawet prywatna i wewnętrzna, nie mogą zmienić swoich nazw, typów, a nawet ich kolejności w przyszłych wersjach typu, chyba że szczególna ostrożność zachowuje umowę przy użyciu jawnych parametrów do atrybutów kontraktu danych. Przetestuj zgodność serializacji podczas wprowadzania zmian w możliwych do serializacji typach. Spróbuj wykonać deserializacji nowej wersji w starszej wersji i na odwrót.  
  
6. Rozważ zaimplementowanie <xref:System.Runtime.Serialization.IExtensibleDataObject> interfejsu, aby umożliwić wykonywanie rundy między różnymi wersjami tego typu.  
  
     Interfejs umożliwia serializator upewnić się, że nie są żadne dane utracone podczas Pełna zgodnooć wersji. <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> Właściwość przechowuje wszystkie dane z przyszłej wersji typu, który jest nieznany do bieżącej wersji. Gdy bieżąca wersja jest następnie serializowana i deserializowana w przyszłej wersji, dodatkowe dane będą dostępne w serializowanym strumieniu za pomocą wartości właściwości **ExtensionData —** .  
  
     [!code-csharp[SerializationGuidelines#5](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#5)]
     [!code-vb[SerializationGuidelines#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#5)]  
  
     Aby uzyskać więcej informacji, zobacz [Kontrakty danych zgodne z przekazywaniem dalej](../../framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
#### <a name="supporting-xml-serialization"></a>Obsługa serializacji XML  
 Serializacja kontrakt danych jest głównym (domyślnie) technologii serializacji w programie .NET Framework, ale istnieją scenariusze serializacji umowy serializacji w danych nie obsługuje. Na przykład nie zapewnia pełnej kontroli nad kształtem XML produkowanym lub zużywanym przez serializator. Jeśli wymagana jest taka kontrola, *Serializacja XML* musi być używana i musisz zaprojektować typy do obsługi tej technologii serializacji.  
  
1. Należy UNIKAĆ projektowanie swój typ specjalnie dla serializacji XML, chyba że użytkownik ma bardzo duży Przyczyna do określenia kształtu XML utworzone. Ta technologia serializacji została zastąpiona przez serializacji kontrakt danych opisanych w poprzedniej sekcji.  
  
     Innymi słowy, nie stosuj atrybutów z <xref:System.Xml.Serialization> przestrzeni nazw do nowych typów, chyba że wiadomo, że typ będzie używany z serializacji XML. Poniższy przykład pokazuje, jak **System. XML. Serialization** może służyć do kontrolowania kształtu utworzonego XML.  
  
     [!code-csharp[SerializationGuidelines#6](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#6)]
     [!code-vb[SerializationGuidelines#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#6)]  
  
2. Rozważ zaimplementowanie <xref:System.Xml.Serialization.IXmlSerializable> interfejsu, jeśli chcesz jeszcze bardziej kontrolować kształt serializowanego kodu XML niż to, co jest oferowane przez zastosowanie atrybutów serializacji XML. Dwie metody interfejsu <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> i <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> umożliwiają pełną kontrolę serializowanego strumienia XML. Można również kontrolować schemat XML, który jest generowany dla typu przez zastosowanie <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> atrybutu.  
  
#### <a name="supporting-runtime-serialization"></a>Obsługa serializacji środowiska uruchomieniowego  
 *Serializacja środowiska uruchomieniowego* jest technologią używaną przez funkcję komunikacji zdalnej platformy .NET. Jeśli uważasz, że Twoje typy będzie transportowane przy użyciu wywołaniem funkcji zdalnych .NET, należy upewnić się, że obsługują serializacji w czasie wykonywania.  
  
 Podstawowe wsparcie dla *serializacji środowiska uruchomieniowego* może być zapewnione przez zastosowanie <xref:System.SerializableAttribute> atrybutu, a bardziej zaawansowane scenariusze obejmują implementację prostego, *serializowanego wzorca środowiska uruchomieniowego* (implementacja <xref:System.Runtime.Serialization.ISerializable> i dostarczenie konstruktora serializacji).  
  
1. Należy rozważyć obsługę serializacji w czasie wykonywania, jeśli Twój typy będzie używany z wywołaniem funkcji zdalnych .NET. Na przykład <xref:System.AddIn> przestrzeń nazw używa komunikacji zdalnej .NET, a więc wszystkie typy wymieniane między dodatkiem **System. addin** muszą obsługiwać serializację w czasie wykonywania.  
  
     [!code-csharp[SerializationGuidelines#7](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#7)]
     [!code-vb[SerializationGuidelines#7](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#7)]  
  
2. Rozważ zaimplementowanie *wzorca serializacji środowiska uruchomieniowego* , jeśli chcesz uzyskać pełną kontrolę nad procesem serializacji. Na przykład, jeśli chcesz przekształcić dane w sposób, w jaki są one serializowane lub deserializowane.  
  
     Wzorzec jest bardzo prosty. Wszystko, co musisz zrobić, implementuje <xref:System.Runtime.Serialization.ISerializable> interfejs i udostępnia specjalny Konstruktor, który jest używany podczas deserializacji obiektu.  
  
     [!code-csharp[SerializationGuidelines#8](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#8)]
     [!code-vb[SerializationGuidelines#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#8)]  
  
3. Uczyń Konstruktor serializacji ochroną i podaj dwa parametry, jak pokazano w przykładzie w tym miejscu.  
  
     [!code-csharp[SerializationGuidelines#9](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#9)]
     [!code-vb[SerializationGuidelines#9](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#9)]  
  
4. NALEŻY zaimplementować jawnie elementy członkowskie ISerializable.  
  
     [!code-csharp[SerializationGuidelines#10](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#10)]
     [!code-vb[SerializationGuidelines#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#10)]  
  
5. Zastosuj żądanie link do implementacji **ISerializable. GetObjectData** . Dzięki temu który tylko w pełni zaufanego podstawowych oraz serializator środowiska wykonawczego ma dostęp do elementu członkowskiego.  
  
     [!code-csharp[SerializationGuidelines#11](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#11)]
     [!code-vb[SerializationGuidelines#11](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#11)]  
  
## <a name="see-also"></a>Zobacz także

- [Używanie kontraktów danych](../../framework/wcf/feature-details/using-data-contracts.md)
- [Serializator kontraktów danych](../../framework/wcf/feature-details/data-contract-serializer.md)
- [Typy obsługiwane przez serializator kontraktu danych](../../framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)
- [Serializacja binarna](binary-serialization.md)
- [Wywołaniem funkcji zdalnych .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))
- [Serializacja XML i SOAP](xml-and-soap-serialization.md)
- [Zabezpieczenia i serializacja](../../framework/misc/security-and-serialization.md)
