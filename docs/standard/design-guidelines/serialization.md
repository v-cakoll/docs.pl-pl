---
title: Serialization1
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: bebb27ac-9712-4196-9931-de19fc04dbac
author: KrzysztofCwalina
ms.openlocfilehash: f0ef8ab378fb3898f2d2e134f0b38668f6794ef3
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409214"
---
# <a name="serialization"></a>Serializacja
Serializacja jest proces konwersji obiektu do formatu, który można łatwo utrwalona lub transportowana. Na przykład możesz wykonać serializację obiektu, transport go w Internecie przy użyciu protokołu HTTP i deserializować go na komputerze docelowym.  
  
 .NET Framework oferuje trzy technologii serializacji głównym, zoptymalizowane pod kątem różnych scenariuszy serializacji. W poniższej tabeli przedstawiono te technologie i typy struktury związane z tych technologii.  
  
|**Nazwa technologii**|**Główne typy**|**Scenariusze**|  
|-------------------------|--------------------|-------------------|  
|**Serializacja kontrakt danych**|<xref:System.Runtime.Serialization.DataContractAttribute> <br /> <xref:System.Runtime.Serialization.DataMemberAttribute> <br /> <xref:System.Runtime.Serialization.DataContractSerializer> <br /> <xref:System.Runtime.Serialization.NetDataContractSerializer> <br /> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> <br /> <xref:System.Runtime.Serialization.ISerializable>|Trwałość ogólne<br />Usługi sieci Web<br />JSON|  
|**Serializacji XML**|<xref:System.Xml.Serialization.XmlSerializer>|Format XML z pełną kontrolę nad kształt XML|  
|**Środowisko wykonawcze serializacji (binarnych i protokołu SOAP)**|<xref:System.SerializableAttribute> <br /> <xref:System.Runtime.Serialization.ISerializable> <br /> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> <br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>|Wywołaniem funkcji zdalnych .NET|  
  
 **✓ DO** Pomyśl o serializacji podczas projektowania nowych typów.  
  
## <a name="choosing-the-right-serialization-technology-to-support"></a>Wybranie opcji technologii serializacji prawo do pomocy technicznej  
 **✓ CONSIDER** obsługę serializacji kontraktu danych, jeśli wystąpień tego typu może być konieczne może być utrwalona lub używany w usługach sieci Web.  
  
 **✓ CONSIDER** obsługę serializacji XML zamiast lub oprócz serializacji kontraktu danych, jeśli potrzebujesz większej kontroli nad formacie XML, który jest generowany, gdy typ jest serializowany.  
  
 Może to być konieczne w niektórych interoperacyjności konstruowania scenariuszy, w którym należy użyć pliku XML, który nie jest obsługiwany przez danych serializacji umowy, na przykład do tworzenia atrybutów XML.  
  
 **✓ CONSIDER** obsługę serializacji środowiska uruchomieniowego, jeśli konieczne są przesyłane między granicami .NET Remoting wystąpień tego typu.  
  
 **X AVOID** Obsługa środowiska uruchomieniowego serializacji lub serializacji XML tylko ze względów ogólne trwałości. Zamiast tego wolisz serializacji kontrakt danych.  
  
## <a name="supporting-data-contract-serialization"></a>Pomocniczych serializacji kontrakt danych  
 Typy może obsługiwać serializacji kontrakt danych przez zastosowanie <xref:System.Runtime.Serialization.DataContractAttribute> do typu i <xref:System.Runtime.Serialization.DataMemberAttribute> do elementów członkowskich (pola i właściwości) tego typu.  
  
 **✓ CONSIDER** oznaczenie elementy członkowskie danych z typu publiczne, jeśli typ może być używany w częściowej relacji zaufania.  
  
 W pełnej relacji zaufania serializatory umowy danych mogą serializacji i deserializacji niepublicznych typy i elementy członkowskie, ale tylko publiczne składowe mogą być serializacji i deserializacji w częściowej relacji zaufania.  
  
 **✓ DO** implementuje metody pobierającej i ustawiającej dla wszystkich właściwości, które mają <xref:System.Runtime.Serialization.DataMemberAttribute>. Serializatory umowy danych wymagają zarówno getter i setter dla typu, który ma być brany pod uwagę serializacji. (W .NET Framework 3.5 z dodatkiem SP1, niektóre właściwości kolekcji można tylko do get.) Jeśli typ nie można używać w częściowej relacji zaufania, co najmniej jeden z metody dostępu właściwości można niepublicznych.  
  
 **✓ CONSIDER** przy użyciu wywołania zwrotne serializacji dla inicjowania wystąpienia zdeserializowany.  
  
 Konstruktorów nie są wywoływane, gdy obiekty są deserializacji. (Istnieją wyjątki od reguły. Konstruktory kolekcje oznaczone <xref:System.Runtime.Serialization.CollectionDataContractAttribute> są wywoływane podczas deserializacji.) W związku z tym wszelka logika, która wykonuje podczas konstruowania normalnych musi zostać wdrożone jako jeden wywołania zwrotne serializacji.  
  
 `OnDeserializedAttribute` jest atrybutem najczęściej używane wywołania zwrotnego. Inne atrybuty z rodziny są <xref:System.Runtime.Serialization.OnDeserializingAttribute>, <xref:System.Runtime.Serialization.OnSerializingAttribute>, i <xref:System.Runtime.Serialization.OnSerializedAttribute>. One służy do oznaczania wywołania zwrotne, które są wykonywane przed deserializacji, przed serializacji, a na końcu po serializacji, odpowiednio.  
  
 **✓ CONSIDER** przy użyciu <xref:System.Runtime.Serialization.KnownTypeAttribute> wskazująca konkretne typy, które mają być używane podczas deserializacji wykresu obiektu złożonego.  
  
 **✓ DO** należy wziąć pod uwagę zgodność z poprzednimi wersjami i do przodu podczas tworzenia lub zmiany typów możliwych do serializacji.  
  
 Należy pamiętać, który serializowany strumieni przyszłych wersjach tego typu mogą zostać przeprowadzona deserializacja bieżącą wersję tego typu i na odwrót.  
  
 Upewnij się, że rozumiesz, że danych elementów członkowskich, nawet prywatne i wewnętrzne, nie można zmienić ich nazwy, typy lub nawet ich kolejność w przyszłych wersjach tego typu, chyba że specjalne jest uwagę, aby zachować zamówienia przy użyciu jawne parametry, atrybuty kontraktu danych .  
  
 Testowanie zgodności serializacji podczas wprowadzania zmian do typów możliwych do serializacji. Spróbuj wykonać deserializacji nowej wersji w starszej wersji i na odwrót.  
  
 **✓ CONSIDER** implementacja <xref:System.Runtime.Serialization.IExtensibleDataObject> umożliwiają dwustronną komunikację między różnymi wersjami tego typu.  
  
 Interfejs umożliwia serializator upewnić się, że nie są żadne dane utracone podczas Pełna zgodnooć wersji. <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A?displayProperty=nameWithType> Właściwość jest używana do przechowywania wszelkich danych z przyszłej wersji typu, który jest nieznany do bieżącej wersji, a więc go nie można zapisać ją w składowych danych. Jeśli bieżąca wersja jest następnie serializacji i deserializacji w przyszłej wersji, dodatkowe dane są dostępne w strumieniu Zserializowany.  
  
## <a name="supporting-xml-serialization"></a>Obsługa serializacji XML  
 Serializacja kontrakt danych jest głównym (domyślnie) technologii serializacji w programie .NET Framework, ale istnieją scenariusze serializacji, które nie obsługuje serializacji kontrakt danych. Na przykład jego zapewnia pełną kontrolę nad kształt XML utworzone lub używane przez program. Jeśli takie precyzyjnego jest wymagany, serializacji XML, które ma być używany, a trzeba utworzyć swój typ do obsługi tej technologii serializacji.  
  
 **X AVOID** projektowania z typów specjalnie z myślą o serializacji XML, chyba że masz bardzo silnych Przyczyna do kontrolowania kształtu XML utworzony. Ta technologia serializacji została zastąpiona przez serializacji kontrakt danych opisanych w poprzedniej sekcji.  
  
 **✓ CONSIDER** implementacja <xref:System.Xml.Serialization.IXmlSerializable> interfejsu, jeśli chcesz większą kontrolę nad kształtu serializacji XML niż co to jest oferowany przez stosowanie atrybutów serializacji XML. Dwie metody interfejsu, <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> i <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>, pozwalają na w pełni kontrolować Zserializowany strumień XML. Możesz również kontrolować schematu XML, który pobiera wygenerowany dla typu przez zastosowanie `XmlSchemaProviderAttribute`.  
  
## <a name="supporting-runtime-serialization"></a>Obsługa czasu wykonywania serializacji  
 Środowisko wykonawcze serializacji to technologia używana przez wywołaniem funkcji zdalnych .NET. Jeśli uważasz, że Twoje typy będzie transportowane przy użyciu wywołaniem funkcji zdalnych .NET, należy się upewnić, że obsługują serializacji w czasie wykonywania.  
  
 Podstawowa pomoc techniczna dla serializacji w czasie wykonywania mogą być zapewniane przez zastosowanie <xref:System.SerializableAttribute>, i bardziej zaawansowanych scenariuszy wymagają, wykonania prostego czasu wykonywania serializacji wzorzec (Implementowanie <xref:System.Runtime.Serialization.ISerializable> i podaj konstruktora serializacji).  
  
 **✓ CONSIDER** obsługę środowiska uruchomieniowego serializacji, jeśli Twoje typów będą używane z funkcji zdalnych .NET. Na przykład <xref:System.AddIn?displayProperty=nameWithType> nazw korzysta z wywołaniem funkcji zdalnych .NET, a więc wszystkie typy wymieniane między `System.AddIn` dodatków musi obsługiwać serializacji w czasie wykonywania.  
  
 **✓ CONSIDER** implementacja wzorca serializacji środowiska uruchomieniowego, jeśli mają pełną kontrolę nad procesem serializacji. Na przykład jeśli chcesz przekształcania danych jako jej pobiera serializowany lub deserializowany.  
  
 Wzorzec jest bardzo proste. Wszystko, czego potrzebujesz, aby zrobić to zaimplementować <xref:System.Runtime.Serialization.ISerializable> interfejs i dostarczyć konstruktora specjalne, który jest używany, gdy deserializowany jest.  
  
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
  
 **✓ DO** Zastosuj żądanie łącza do <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> implementacji. Dzięki temu który tylko w pełni zaufanego podstawowych oraz serializator środowiska wykonawczego ma dostęp do elementu członkowskiego.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
- [Zalecenia dotyczące użytkowania](../../../docs/standard/design-guidelines/usage-guidelines.md)
