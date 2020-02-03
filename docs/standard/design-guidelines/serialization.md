---
title: Serializacja
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: bebb27ac-9712-4196-9931-de19fc04dbac
ms.openlocfilehash: d29a7bc9f304b8d19e8af593166b8d847117424f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743634"
---
# <a name="serialization"></a>Serializacja
Serializacja jest procesem konwersji obiektu do formatu, który może być łatwo utrwalany lub transportowany. Na przykład można serializować obiekt, transportować go za pośrednictwem Internetu przy użyciu protokołu HTTP i deserializacji go na maszynie docelowej.

 .NET Framework oferuje trzy podstawowe technologie serializacji zoptymalizowane pod kątem różnych scenariuszy serializacji. W poniższej tabeli przedstawiono te technologie i typy struktury związane z tych technologii.

|**Nazwa technologii**|**Typy główne**|**Scenariusze**|
|-------------------------|--------------------|-------------------|
|**Serializacja kontraktu danych**|<xref:System.Runtime.Serialization.DataContractAttribute> <br /> <xref:System.Runtime.Serialization.DataMemberAttribute> <br /> <xref:System.Runtime.Serialization.DataContractSerializer> <br /> <xref:System.Runtime.Serialization.NetDataContractSerializer> <br /> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> <br /> <xref:System.Runtime.Serialization.ISerializable>|Trwałość ogólne<br />Usługi sieci Web<br />JSON|
|**Serializacja XML**|<xref:System.Xml.Serialization.XmlSerializer>|Format XML z pełną kontrolą nad kształtem XML|
|**Serializacja czasu wykonywania (binarny i SOAP)**|<xref:System.SerializableAttribute> <br /> <xref:System.Runtime.Serialization.ISerializable> <br /> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> <br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>|Wywołaniem funkcji zdalnych .NET|

 ✔️ NALEŻY myśleć o serializacji podczas projektowania nowych typów.

## <a name="choosing-the-right-serialization-technology-to-support"></a>Wybranie opcji technologii serializacji prawo do pomocy technicznej
 ✔️ ROZWAŻYĆ obsługę serializacji kontraktu danych, jeśli wystąpienia typu mogą wymagać utrwalenia lub użycia w usługach sieci Web.

 ✔️ ROZWAŻYĆ obsługę serializacji XML zamiast lub oprócz serializacji kontraktu danych, jeśli potrzebna jest większa kontrola nad formatem XML, który jest generowany, gdy typ jest serializowany.

 Może to być konieczne w niektórych scenariuszach współdziałania, w których należy użyć konstrukcji XML, która nie jest obsługiwana przez serializacji kontraktu danych, na przykład w celu utworzenia atrybutów XML.

 ✔️ ROZWAŻYĆ obsługę serializacji środowiska uruchomieniowego, jeśli wystąpienia typu muszą poruszać się w granicach komunikacji zdalnej platformy .NET.

 ❌ uniknąć obsługi serializacji w czasie wykonywania lub serializacji XML tylko w przypadku ogólnych przyczyn trwałości. Zamiast tego Preferuj metodę serializacji kontraktu danych.

## <a name="supporting-data-contract-serialization"></a>Pomocniczych serializacji kontrakt danych
 Typy mogą obsługiwać serializacji kontraktu danych przez zastosowanie <xref:System.Runtime.Serialization.DataContractAttribute> do typu i <xref:System.Runtime.Serialization.DataMemberAttribute> do elementów członkowskich (pól i właściwości) typu.

 ✔️ NALEŻY rozważyć oznaczenie składowych danych typu Public, jeśli typ może być używany w częściowej relacji zaufania.

 W przypadku pełnego zaufania serializatory kontraktu danych mogą serializować i deserializować typy niepubliczne i składowe, ale tylko publiczne składowe mogą być serializowane i deserializowane w częściowej relacji zaufania.

 ✔️ implementuje metody pobierającej i ustawiającej dla wszystkich właściwości, które mają <xref:System.Runtime.Serialization.DataMemberAttribute>. Serializatory kontraktu danych wymagają zarówno metody pobierającej, jak i metody ustawiającej dla typu, który ma być uznawany za możliwy do serializacji. (W .NET Framework 3,5 z dodatkiem SP1 niektóre właściwości kolekcji mogą być tylko do odczytu.) Jeśli typ nie zostanie użyty w częściowej relacji zaufania, co najmniej jeden z metod dostępu do właściwości może być niepubliczny.

 ✔️ ROZWAŻYĆ użycie wywołania zwrotnego serializacji do inicjowania wystąpień deserializowanych.

 Konstruktorów nie są wywoływane, gdy obiekty są deserializacji. (Istnieją wyjątki od reguły. Konstruktory kolekcji oznaczone <xref:System.Runtime.Serialization.CollectionDataContractAttribute> są wywoływane podczas deserializacji.) W związku z tym każda logika, która jest wykonywana podczas normalnej konstrukcji, musi być zaimplementowana jako jedno z wywołań zwrotnych serializacji.

 `OnDeserializedAttribute` jest najczęściej używanym atrybutem wywołania zwrotnego. Inne atrybuty z rodziny są <xref:System.Runtime.Serialization.OnDeserializingAttribute>, <xref:System.Runtime.Serialization.OnSerializingAttribute>, i <xref:System.Runtime.Serialization.OnSerializedAttribute>. One służy do oznaczania wywołania zwrotne, które są wykonywane przed deserializacji, przed serializacji, a na końcu po serializacji, odpowiednio.

 ✔️ ROZWAŻYĆ użycie <xref:System.Runtime.Serialization.KnownTypeAttribute> do wskazania konkretnych typów, które powinny być używane podczas deserializacji grafu złożonego obiektu.

 ✔️ podczas tworzenia lub zmieniania typów możliwych do serializacji należy wziąć pod uwagę zgodność z poprzednimi i przekazaniem.

 Należy pamiętać, który serializowany strumieni przyszłych wersjach tego typu mogą zostać przeprowadzona deserializacja bieżącą wersję tego typu i na odwrót.

 Upewnij się, że rozumiesz, że członkowie danych, nawet prywatna i wewnętrzna, nie mogą zmienić swoich nazw, typów lub nawet ich kolejności w przyszłych wersjach typu, chyba że szczególna szczególna potrzeba zachowywać się w celu zachowania kontraktu przy użyciu jawnych parametrów do atrybutów kontraktu danych. .

 Przetestuj zgodność serializacji podczas wprowadzania zmian w możliwych do serializacji typach. Spróbuj wykonać deserializacji nowej wersji w starszej wersji i na odwrót.

 ✔️ ROZWAŻYĆ zaimplementowanie <xref:System.Runtime.Serialization.IExtensibleDataObject>, aby umożliwić wykonywanie rundy między różnymi wersjami tego typu.

 Interfejs umożliwia serializator upewnić się, że nie są żadne dane utracone podczas Pełna zgodnooć wersji. Właściwość <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A?displayProperty=nameWithType> służy do przechowywania wszelkich danych z przyszłej wersji typu, która jest nieznana w bieżącej wersji i dlatego nie może być przechowywana w jego elementach członkowskich danych. Gdy bieżąca wersja jest następnie serializowana i deserializowana w przyszłej wersji, dodatkowe dane będą dostępne w strumieniu serializowanym.

## <a name="supporting-xml-serialization"></a>Obsługa serializacji XML
 Serializacja kontraktu danych jest główną (domyślną) technologią serializacji w .NET Framework, ale istnieją scenariusze serializacji, które nie obsługują serializacji kontraktu danych. Na przykład nie zapewnia pełnej kontroli nad kształtem XML produkowanym lub zużywanym przez serializator. Jeśli wymagana jest taka kontrola, serializacja XML musi być używana i musisz zaprojektować typy do obsługi tej technologii serializacji.

 ❌ UNIKAj projektowania typów przeznaczonych do serializacji XML, chyba że masz bardzo silny powód, aby kontrolować kształt wygenerowanego kodu XML. Ta technologia serializacji została zastąpiona przez serializacji kontrakt danych opisanych w poprzedniej sekcji.

 ✔️ ROZWAŻYĆ zaimplementowanie interfejsu <xref:System.Xml.Serialization.IXmlSerializable>, jeśli chcesz jeszcze większą kontrolę nad kształtem serializowanego kodu XML niż proponowane przez zastosowanie atrybutów serializacji XML. Dwie metody interfejsu, <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> i <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>umożliwiają pełną kontrolę serializowanego strumienia XML. Można również kontrolować schemat XML, który jest generowany dla typu przez zastosowanie `XmlSchemaProviderAttribute`.

## <a name="supporting-runtime-serialization"></a>Obsługa czasu wykonywania serializacji
 Serializacja środowiska uruchomieniowego jest technologią używaną przez funkcję komunikacji zdalnej platformy .NET. Jeśli uważasz, że Twoje typy będą transportowane przy użyciu komunikacji zdalnej .NET, musisz upewnić się, że obsługują one serializacji środowiska uruchomieniowego.

 Podstawową obsługę serializacji środowiska uruchomieniowego można uzyskać, stosując <xref:System.SerializableAttribute>, a bardziej zaawansowane scenariusze obejmują implementację prostego, serializowanego wzorca środowiska uruchomieniowego (implementacja <xref:System.Runtime.Serialization.ISerializable> i dostarczenie konstruktora serializacji).

 ✔️ ROZWAŻYĆ obsługę serializacji środowiska uruchomieniowego, jeśli typy będą używane z usługami zdalnymi platformy .NET. Na przykład przestrzeń nazw <xref:System.AddIn?displayProperty=nameWithType> używa komunikacji zdalnej .NET, a więc wszystkie typy wymieniane między Dodatki `System.AddIn` muszą obsługiwać serializacji czasu wykonywania.

 ✔️ ROZWAŻYĆ zaimplementowanie wzorca serializacji środowiska uruchomieniowego, jeśli chcesz uzyskać pełną kontrolę nad procesem serializacji. Na przykład, jeśli chcesz przekształcić dane w sposób, w jaki są one serializowane lub deserializowane.

 Wzorzec jest bardzo prosty. Wszystko, co musisz zrobić, implementuje interfejs <xref:System.Runtime.Serialization.ISerializable> i udostępnia specjalny Konstruktor, który jest używany podczas deserializacji obiektu.

 ✔️ Uczyń Konstruktor serializacji ochroną i podaj dwa parametry i o nazwie dokładnie tak jak pokazano w przykładzie.

```csharp
[Serializable]
public class Person : ISerializable
{
    protected Person(SerializationInfo info, StreamingContext context)
    {
        // ...
    }
}
```

 ✔️ NALEŻY zaimplementować jawnie <xref:System.Runtime.Serialization.ISerializable> członków.

 ✔️ zastosować żądanie linku do <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> implementacji. Daje to pewność, że tylko w pełni zaufany rdzeń i Serializator środowiska uruchomieniowego mają dostęp do elementu członkowskiego.

 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
- [Zalecenia dotyczące użytkowania](../../../docs/standard/design-guidelines/usage-guidelines.md)
