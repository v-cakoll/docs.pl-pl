---
title: Wskazówki dotyczące serializacji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serialization, guidelines
- binary serialization, guidelines
ms.assetid: ebbeddff-179d-443f-bf08-9c373199a73a
ms.openlocfilehash: b47be45f00ee03d400383dd45dc6776cff3f816d
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44060336"
---
# <a name="serialization-guidelines"></a>Wskazówki dotyczące serializacji
Ten dokument zawiera listę wskazówek, które należy wziąć pod uwagę podczas projektowania interfejs API serializacji.  

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
 .NET oferuje trzy technologii serializacji głównym, które są zoptymalizowane pod kątem różnych scenariuszy serializacji. W poniższej tabeli wymieniono te technologie i typy .NET związane z tych technologii.  
  
|Technologia|Odpowiednich klas|Uwagi|  
|----------------|----------------------|-----------|  
|Serializacja kontrakt danych|<xref:System.Runtime.Serialization.DataContractAttribute><br /><br /> <xref:System.Runtime.Serialization.DataMemberAttribute><br /><br /> <xref:System.Runtime.Serialization.DataContractSerializer><br /><br /> <xref:System.Runtime.Serialization.NetDataContractSerializer><br /><br /> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer><br /><br /> <xref:System.Runtime.Serialization.ISerializable>|Trwałość ogólne<br /><br /> Usługi sieci Web<br /><br /> JSON|  
|Serializacji XML|<xref:System.Xml.Serialization.XmlSerializer>|XML format <br />z pełną kontrolę|  
|Środowisko wykonawcze-serializacji (binarnych i protokołu SOAP)|<xref:System.SerializableAttribute><br /><br /> <xref:System.Runtime.Serialization.ISerializable><br /><br /> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter><br /><br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>|Wywołaniem funkcji zdalnych .NET|  
  
 Podczas projektowania nowych typów, należy zdecydować, które ewentualnie technologii te typy muszą obsługiwać. Poniższe wskazówki opisano sposób, aby wybrać i jak zapewnić obsługę takich. Te wytyczne nie jest przeznaczona do pomagają w określeniu należy używać technologii serializacji w implementacji aplikacji lub biblioteki. Takie wytyczne nie są bezpośrednio związane z interfejsu API projektowania i w związku z tym nie są w zakresie tego tematu.  
  
## <a name="guidelines"></a>Wytyczne dotyczące  
  
-   Zastanowić serializacji podczas projektowania nowych typów.  
  
     Serializacji jest ważna projektowania dla dowolnego typu, ponieważ programy może być wymagane do utrwalenia lub przesłania wystąpienie typu.  
  
### <a name="choosing-the-right-serialization-technology-to-support"></a>Wybór technologii serializacji prawo do pomocy technicznej  
 Dla dowolnego typu może obsługiwać none, co najmniej jedną z technologii serializacji.  
  
-   Obsługa ROZWAŻ *kontraktu danych serializacji* w przypadku wystąpienia tego typu może być konieczne może być utrwalone lub używany w usługach sieci Web.  
  
-   Obsługa ROZWAŻ *serializacji XML* zamiast lub oprócz danych serializacji umowy, jeśli potrzebujesz większej kontroli nad formatem XML, który jest generowany, gdy typ jest serializowana.  
  
     Może to być konieczne w niektórych scenariuszach współpracy, w którym należy użyć konstrukcji XML, który nie jest obsługiwany przez danych serializacji umowy, na przykład do tworzenia atrybutów XML.  
  
-   Obsługa ROZWAŻ *czasu wykonywania serializacji* w przypadku wystąpienia tego typu muszą przechodzić granic wywołaniem funkcji zdalnych .NET.  
  
-   UNIKAJ obsługi czasu wykonywania serializacji lub serializacji XML tylko dla trwałości głównej przyczyny. Zamiast tego użyć serializacji kontrakt danych  
  
#### <a name="supporting-data-contract-serialization"></a>Pomocniczych serializacji kontrakt danych  
 Typy może obsługiwać serializacji kontrakt danych przez zastosowanie <xref:System.Runtime.Serialization.DataContractAttribute> do typu i <xref:System.Runtime.Serialization.DataMemberAttribute> do elementów członkowskich (pola i właściwości) tego typu.  
  
 [!code-csharp[SerializationGuidelines#1](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#1)]
 [!code-vb[SerializationGuidelines#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#1)]  
  
1.  Należy rozważyć oznaczanie elementów członkowskich danych tego typu publiczne, jeśli typ może być używany w częściowej relacji zaufania. W pełnej relacji zaufania serializatory umowy danych mogą serializacji i deserializacji niepublicznych typy i elementy członkowskie, ale tylko publiczne elementy Członkowskie mogą być serializacji i deserializacji w częściowej relacji zaufania.  
  
2.  Implementuje metodę getter i setter na wszystkie właściwości, które mają MemberAttribute danych. Serializatory umowy danych wymagają zarówno getter i setter dla typu, który ma być brany pod uwagę serializacji. Jeśli typ nie można używać w częściowej relacji zaufania, co najmniej jeden z metody dostępu właściwości można niepublicznych.  
  
     [!code-csharp[SerializationGuidelines#2](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#2)]
     [!code-vb[SerializationGuidelines#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#2)]  
  
3.  Należy rozważyć użycie wywołania zwrotne serializacji dla inicjowania wystąpień zdeserializowany.  
  
     Konstruktorów nie są wywoływane, gdy obiekty są deserializacji. W związku z tym, wszelka logika, która wykonuje podczas konstruowania normalnych musi zostać wdrożone jako jeden z *wywołania zwrotne serializacji*.  
  
     [!code-csharp[SerializationGuidelines#3](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#3)]
     [!code-vb[SerializationGuidelines#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#3)]  
  
     <xref:System.Runtime.Serialization.OnDeserializedAttribute> Atrybutu jest atrybutem najczęściej używane wywołania zwrotnego. Inne atrybuty z rodziny są <xref:System.Runtime.Serialization.OnDeserializingAttribute>,    
    <xref:System.Runtime.Serialization.OnSerializingAttribute>, a <xref:System.Runtime.Serialization.OnSerializedAttribute>. One służy do oznaczania wywołania zwrotne, które są wykonywane przed deserializacji, przed serializacji, a na końcu po serializacji, odpowiednio.  
  
4.  ROZWAŻ użycie <xref:System.Runtime.Serialization.KnownTypeAttribute> do wskazania konkretnych typów, które powinny być używane podczas deserializacji obiektu złożonego wykresu.  
  
     Na przykład, jeśli typ składowej danych zdeserializowany jest reprezentowany przez klasę abstrakcyjną, serializator, konieczne będzie *znany typ* informacje, aby wybrać konkretny typ do tworzenia instancji i przypisać do elementu członkowskiego. Jeśli znany typ nie jest określony za pomocą atrybutu, trzeba będzie ją można przekazać do serializator jawnie (można go zrobić przez przekazanie znanych typów do konstruktora serializator) lub trzeba będzie ją można określić w pliku konfiguracji.  
  
     [!code-csharp[SerializationGuidelines#4](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#4)]
     [!code-vb[SerializationGuidelines#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#4)]  
  
     W przypadkach, gdy listę znanych typów nie jest znany statycznie (gdy **osoby** jest skompilowana klasa), **KnownTypeAttribute** może też wskazywać na metodę, która zwraca listę znanych typów w czasie wykonywania.  
  
5.  Należy wziąć pod uwagę zgodność z poprzednimi wersjami i do przodu, podczas tworzenia lub zmiany typów możliwych do serializacji.  
  
     Należy pamiętać, który serializowany strumieni przyszłych wersjach tego typu mogą zostać przeprowadzona deserializacja bieżącą wersję tego typu i na odwrót. Upewnij się, że rozumiesz, że danych elementów członkowskich, nawet prywatne i wewnętrzne, nie można zmienić ich nazwy, typy lub nawet ich kolejność w przyszłych wersjach tego typu, chyba że specjalne jest uwagę, aby zachować zamówienia przy użyciu jawne parametry, atrybuty kontraktu danych . Testowanie zgodności serializacji podczas wprowadzania zmian do typów możliwych do serializacji. Spróbuj wykonać deserializacji nowej wersji w starszej wersji i na odwrót.  
  
6.  ROZWAŻ wykonania <xref:System.Runtime.Serialization.IExtensibleDataObject> interfejs umożliwia Pełna zgodnooć wersji między różnymi wersjami tego typu.  
  
     Interfejs umożliwia serializator upewnić się, że nie są żadne dane utracone podczas Pełna zgodnooć wersji. <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> Właściwość przechowuje wszystkie dane z przyszłej wersji typu, który jest nieznany do bieżącej wersji. Gdy bieżącej wersji jest następnie serializacji i deserializacji w przyszłej wersji, dodatkowe dane będą dostępne w strumieniu Zserializowany za pośrednictwem **extensiondata —** wartości właściwości.  
  
     [!code-csharp[SerializationGuidelines#5](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#5)]
     [!code-vb[SerializationGuidelines#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#5)]  
  
     Aby uzyskać więcej informacji, zobacz [kontrakty danych zgodne](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
#### <a name="supporting-xml-serialization"></a>Obsługa serializacji XML  
 Serializacja kontrakt danych jest głównym (domyślnie) technologii serializacji w programie .NET Framework, ale istnieją scenariusze serializacji umowy serializacji w danych nie obsługuje. Na przykład jego zapewnia pełną kontrolę nad kształt XML utworzone lub używane przez program. Jeśli takie precyzyjnego jest wymagany, *serializacji XML* ma być używany, a trzeba utworzyć swój typ do obsługi tej technologii serializacji.  
  
1.  Należy UNIKAĆ projektowanie swój typ specjalnie dla serializacji XML, chyba że użytkownik ma bardzo duży Przyczyna do określenia kształtu XML utworzone. Ta technologia serializacji została zastąpiona przez serializacji kontrakt danych opisanych w poprzedniej sekcji.  
  
     Innymi słowy, nie można stosować atrybutów z <xref:System.Runtime.Serialization> przestrzeni nazw do nowych typów, jeśli nie masz pewności, czy zostanie użyty typ serializacji XML. W poniższym przykładzie przedstawiono sposób **System.Xml.Serialization** może służyć do określenia kształtu XML-utworzone.  
  
     [!code-csharp[SerializationGuidelines#6](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#6)]
     [!code-vb[SerializationGuidelines#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#6)]  
  
2.  ROZWAŻ wykonania <xref:System.Xml.Serialization.IXmlSerializable> interfejsu, jeśli chcesz, aby jeszcze bardziej kontrolować kształt serializacji XML niż treści oferowanych przez zastosowanie atrybutów serializacji XML. Dwie metody interfejsu, <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> i <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>, pozwalają na w pełni kontrolować Zserializowany strumień XML. Możesz również kontrolować schematu XML, który pobiera wygenerowany dla typu przez zastosowanie <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> atrybutu.  
  
#### <a name="supporting-runtime-serialization"></a>Obsługa czasu wykonywania serializacji  
 *Środowisko wykonawcze serializacji* to technologia używana przez wywołaniem funkcji zdalnych .NET. Jeśli uważasz, że Twoje typy będzie transportowane przy użyciu wywołaniem funkcji zdalnych .NET, należy upewnić się, że obsługują serializacji w czasie wykonywania.  
  
 Podstawowa pomoc techniczna dla *czasu wykonywania serializacji* można uwzględnić stosując <xref:System.SerializableAttribute> atrybut i bardziej zaawansowanych scenariuszy wymagają wykonania prosty *czasu wykonywania serializacji wzorzec* () Implementowanie -<xref:System.Runtime.Serialization.ISerializable> i dostarczyć konstruktora serializacji).  
  
1.  Należy rozważyć obsługę serializacji w czasie wykonywania, jeśli Twój typy będzie używany z wywołaniem funkcji zdalnych .NET. Na przykład <xref:System.AddIn> nazw korzysta z wywołaniem funkcji zdalnych .NET, a więc wszystkie typy wymieniane między **System.AddIn** dodatków musi obsługiwać serializacji w czasie wykonywania.  
  
     [!code-csharp[SerializationGuidelines#7](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#7)]
     [!code-vb[SerializationGuidelines#7](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#7)]  
  
2.  ROZWAŻ wykonania *czasu wykonywania serializacji wzorzec* jeśli mają pełną kontrolę nad procesem serializacji. Na przykład jeśli chcesz przekształcania danych jako jej pobiera serializowany lub deserializowany.  
  
     Wzorzec jest bardzo proste. Wszystko, czego potrzebujesz, aby zrobić to zaimplementować <xref:System.Runtime.Serialization.ISerializable> interfejs i dostarczyć konstruktora specjalne, który jest używany, gdy deserializowany jest.  
  
     [!code-csharp[SerializationGuidelines#8](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#8)]
     [!code-vb[SerializationGuidelines#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#8)]  
  
3.  Wybierz konstruktora serializacji chronione i podaj dwa parametry wpisany i o nazwie dokładnie tak jak pokazano w przykładzie poniżej.  
  
     [!code-csharp[SerializationGuidelines#9](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#9)]
     [!code-vb[SerializationGuidelines#9](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#9)]  
  
4.  Implementuje jawnie ISerializable elementów członkowskich.  
  
     [!code-csharp[SerializationGuidelines#10](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#10)]
     [!code-vb[SerializationGuidelines#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#10)]  
  
5.  Zastosuj żądanie łącza do **ISerializable.GetObjectData** implementacji. Dzięki temu który tylko w pełni zaufanego podstawowych oraz serializator środowiska wykonawczego ma dostęp do elementu członkowskiego.  
  
     [!code-csharp[SerializationGuidelines#11](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#11)]
     [!code-vb[SerializationGuidelines#11](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#11)]  
  
## <a name="see-also"></a>Zobacz także

- [Używanie kontraktów danych](../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
- [Serializator kontraktów danych](../../../docs/framework/wcf/feature-details/data-contract-serializer.md)  
- [Typy obsługiwane przez serializator kontraktu danych](../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)  
- [Serializacja binarna](binary-serialization.md)  
- [Obiekty zdalne](https://msdn.microsoft.com/library/515686e6-0a8d-42f7-8188-73abede57c58)  
- [Serializacja XML i SOAP](xml-and-soap-serialization.md)  
- [Zabezpieczenia i serializacja](../../../docs/framework/misc/security-and-serialization.md)
