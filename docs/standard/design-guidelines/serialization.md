---
title: Serializacja
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: bebb27ac-9712-4196-9931-de19fc04dbac
author: KrzysztofCwalina
ms.openlocfilehash: 0259bf82e74cbca7df8da246ca2e6ba7ef4542b3
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68868522"
---
# <a name="serialization"></a>Serializacja
Serializacja jest procesem konwersji obiektu do formatu, który może być łatwo utrwalany lub transportowany. Na przykład można serializować obiekt, transportować go za pośrednictwem Internetu przy użyciu protokołu HTTP i deserializacji go na maszynie docelowej.  
  
 .NET Framework oferuje trzy podstawowe technologie serializacji zoptymalizowane pod kątem różnych scenariuszy serializacji. W poniższej tabeli przedstawiono te technologie i typy struktury związane z tych technologii.  
  
|**Nazwa technologii**|**Typy główne**|**Sytuacji**|  
|-------------------------|--------------------|-------------------|  
|**Serializacja kontraktu danych**|<xref:System.Runtime.Serialization.DataContractAttribute> <br /> <xref:System.Runtime.Serialization.DataMemberAttribute> <br /> <xref:System.Runtime.Serialization.DataContractSerializer> <br /> <xref:System.Runtime.Serialization.NetDataContractSerializer> <br /> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> <br /> <xref:System.Runtime.Serialization.ISerializable>|Trwałość ogólne<br />Usługi sieci Web<br />JSON|  
|**Serializacja XML**|<xref:System.Xml.Serialization.XmlSerializer>|Format XML z pełną kontrolą nad kształtem XML|  
|**Serializacja czasu wykonywania (binarny i SOAP)**|<xref:System.SerializableAttribute> <br /> <xref:System.Runtime.Serialization.ISerializable> <br /> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> <br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>|Wywołaniem funkcji zdalnych .NET|  
  
 **✓ DO** Pomyśl o serializacji podczas projektowania nowych typów.  
  
## <a name="choosing-the-right-serialization-technology-to-support"></a>Wybranie opcji technologii serializacji prawo do pomocy technicznej  
 **✓ CONSIDER** obsługę serializacji kontraktu danych, jeśli wystąpień tego typu może być konieczne może być utrwalona lub używany w usługach sieci Web.  
  
 **✓ CONSIDER** obsługę serializacji XML zamiast lub oprócz serializacji kontraktu danych, jeśli potrzebujesz większej kontroli nad formacie XML, który jest generowany, gdy typ jest serializowany.  
  
 Może to być konieczne w niektórych scenariuszach współdziałania, w których należy użyć konstrukcji XML, która nie jest obsługiwana przez serializacji kontraktu danych, na przykład w celu utworzenia atrybutów XML.  
  
 **✓ CONSIDER** obsługę serializacji środowiska uruchomieniowego, jeśli konieczne są przesyłane między granicami .NET Remoting wystąpień tego typu.  
  
 **X AVOID** Obsługa środowiska uruchomieniowego serializacji lub serializacji XML tylko ze względów ogólne trwałości. Zamiast tego Preferuj metodę serializacji kontraktu danych.  
  
## <a name="supporting-data-contract-serialization"></a>Pomocniczych serializacji kontrakt danych  
 Typy mogą obsługiwać serializacji kontraktu danych przez zastosowanie <xref:System.Runtime.Serialization.DataContractAttribute> do typu <xref:System.Runtime.Serialization.DataMemberAttribute> i do elementów członkowskich (pól i właściwości) typu.  
  
 **✓ CONSIDER** oznaczenie elementy członkowskie danych z typu publiczne, jeśli typ może być używany w częściowej relacji zaufania.  
  
 W przypadku pełnego zaufania serializatory kontraktu danych mogą serializować i deserializować typy niepubliczne i składowe, ale tylko publiczne składowe mogą być serializowane i deserializowane w częściowej relacji zaufania.  
  
 **✓ DO** implementuje metody pobierającej i ustawiającej dla wszystkich właściwości, które mają <xref:System.Runtime.Serialization.DataMemberAttribute>. Serializatory kontraktu danych wymagają zarówno metody pobierającej, jak i metody ustawiającej dla typu, który ma być uznawany za możliwy do serializacji. (W .NET Framework 3,5 z dodatkiem SP1 niektóre właściwości kolekcji mogą być tylko do odczytu.) Jeśli typ nie można używać w częściowej relacji zaufania, co najmniej jeden z metody dostępu właściwości można niepublicznych.  
  
 **✓ CONSIDER** przy użyciu wywołania zwrotne serializacji dla inicjowania wystąpienia zdeserializowany.  
  
 Konstruktorów nie są wywoływane, gdy obiekty są deserializacji. (Istnieją wyjątki od reguły. Konstruktory kolekcji z <xref:System.Runtime.Serialization.CollectionDataContractAttribute> oznaczeniem są wywoływane podczas deserializacji.) W związku z tym każda logika, która jest wykonywana podczas normalnej konstrukcji, musi być zaimplementowana jako jedno z wywołań zwrotnych serializacji.  
  
 `OnDeserializedAttribute`jest najczęściej używanym atrybutem wywołania zwrotnego. Inne atrybuty z rodziny są <xref:System.Runtime.Serialization.OnDeserializingAttribute>, <xref:System.Runtime.Serialization.OnSerializingAttribute>, i <xref:System.Runtime.Serialization.OnSerializedAttribute>. One służy do oznaczania wywołania zwrotne, które są wykonywane przed deserializacji, przed serializacji, a na końcu po serializacji, odpowiednio.  
  
 **✓ CONSIDER** przy użyciu <xref:System.Runtime.Serialization.KnownTypeAttribute> wskazująca konkretne typy, które mają być używane podczas deserializacji wykresu obiektu złożonego.  
  
 **✓ DO** należy wziąć pod uwagę zgodność z poprzednimi wersjami i do przodu podczas tworzenia lub zmiany typów możliwych do serializacji.  
  
 Należy pamiętać, który serializowany strumieni przyszłych wersjach tego typu mogą zostać przeprowadzona deserializacja bieżącą wersję tego typu i na odwrót.  
  
 Upewnij się, że rozumiesz, że członkowie danych, nawet prywatna i wewnętrzna, nie mogą zmienić swoich nazw, typów lub nawet ich kolejności w przyszłych wersjach typu, chyba że szczególna szczególna potrzeba zachowywać się w celu zachowania kontraktu przy użyciu jawnych parametrów do atrybutów kontraktu danych. .  
  
 Przetestuj zgodność serializacji podczas wprowadzania zmian w możliwych do serializacji typach. Spróbuj wykonać deserializacji nowej wersji w starszej wersji i na odwrót.  
  
 **✓ CONSIDER** implementacja <xref:System.Runtime.Serialization.IExtensibleDataObject> umożliwiają dwustronną komunikację między różnymi wersjami tego typu.  
  
 Interfejs umożliwia serializator upewnić się, że nie są żadne dane utracone podczas Pełna zgodnooć wersji. <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A?displayProperty=nameWithType> Właściwość służy do przechowywania wszelkich danych z przyszłej wersji typu, która jest nieznana w bieżącej wersji i dlatego nie może być przechowywana w jego elementach członkowskich danych. Gdy bieżąca wersja jest następnie serializowana i deserializowana w przyszłej wersji, dodatkowe dane będą dostępne w strumieniu serializowanym.  
  
## <a name="supporting-xml-serialization"></a>Obsługa serializacji XML  
 Serializacja kontraktu danych jest główną (domyślną) technologią serializacji w .NET Framework, ale istnieją scenariusze serializacji, które nie obsługują serializacji kontraktu danych. Na przykład nie zapewnia pełnej kontroli nad kształtem XML produkowanym lub zużywanym przez serializator. Jeśli wymagana jest taka kontrola, serializacja XML musi być używana i musisz zaprojektować typy do obsługi tej technologii serializacji.  
  
 **X AVOID** projektowania z typów specjalnie z myślą o serializacji XML, chyba że masz bardzo silnych Przyczyna do kontrolowania kształtu XML utworzony. Ta technologia serializacji została zastąpiona przez serializacji kontrakt danych opisanych w poprzedniej sekcji.  
  
 **✓ CONSIDER** implementacja <xref:System.Xml.Serialization.IXmlSerializable> interfejsu, jeśli chcesz większą kontrolę nad kształtu serializacji XML niż co to jest oferowany przez stosowanie atrybutów serializacji XML. Dwie metody interfejsu <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> i <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>umożliwiają pełną kontrolę serializowanego strumienia XML. Można również kontrolować schemat XML, który jest generowany dla typu przez zastosowanie `XmlSchemaProviderAttribute`.  
  
## <a name="supporting-runtime-serialization"></a>Obsługa czasu wykonywania serializacji  
 Serializacja środowiska uruchomieniowego jest technologią używaną przez funkcję komunikacji zdalnej platformy .NET. Jeśli uważasz, że Twoje typy będą transportowane przy użyciu komunikacji zdalnej .NET, musisz upewnić się, że obsługują one serializacji środowiska uruchomieniowego.  
  
 Podstawowe wsparcie dla serializacji środowiska uruchomieniowego może być zapewnione przez <xref:System.SerializableAttribute>zastosowanie, a bardziej zaawansowane scenariusze obejmują wdrożenie prostego wzorca serializacji środowiska uruchomieniowego <xref:System.Runtime.Serialization.ISerializable> (implementacja i dostarczenie konstruktora serializacji).  
  
 **✓ CONSIDER** obsługę środowiska uruchomieniowego serializacji, jeśli Twoje typów będą używane z funkcji zdalnych .NET. Na przykład <xref:System.AddIn?displayProperty=nameWithType> przestrzeń nazw używa komunikacji zdalnej .NET, a więc wszystkie typy wymieniane między `System.AddIn` dodatkami muszą obsługiwać serializację w czasie wykonywania.  
  
 **✓ CONSIDER** implementacja wzorca serializacji środowiska uruchomieniowego, jeśli mają pełną kontrolę nad procesem serializacji. Na przykład, jeśli chcesz przekształcić dane w sposób, w jaki są one serializowane lub deserializowane.  
  
 Wzorzec jest bardzo prosty. Wszystko, co musisz zrobić, implementuje <xref:System.Runtime.Serialization.ISerializable> interfejs i udostępnia specjalny Konstruktor, który jest używany podczas deserializacji obiektu.  
  
 **✓ DO** upewnij chroniony Konstruktor serializacji i podaj dwóch parametrów typu i o nazwie dokładnie tak jak pokazano w przykładzie poniżej.  
  
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
  
 **✓ DO** zaimplementować <xref:System.Runtime.Serialization.ISerializable> elementy członkowskie jawnie.  
  
 **✓ DO** Zastosuj żądanie łącza do <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> implementacji. Daje to pewność, że tylko w pełni zaufany rdzeń i Serializator środowiska uruchomieniowego mają dostęp do elementu członkowskiego.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: Konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku,](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 2. wydanie przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*  
  
## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
- [Zalecenia dotyczące użytkowania](../../../docs/standard/design-guidelines/usage-guidelines.md)
