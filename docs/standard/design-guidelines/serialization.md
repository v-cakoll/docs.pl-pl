---
title: Serialization1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bebb27ac-9712-4196-9931-de19fc04dbac
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: dd6989e651f09a5e4d3354227a44b823b1b3ddcf
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="serialization"></a>Serializacja
Serializacja jest proces konwersji obiektu do formatu, który można łatwo utrwalona lub transportu. Na przykład można serializować obiektu, przetransportować go przez Internet przy użyciu protokołu HTTP i rozszeregować go na komputerze docelowym.  
  
 .NET Framework oferuje trzy technologie głównego serializacji zoptymalizowane pod kątem różnych scenariuszy serializacji. W poniższej tabeli przedstawiono te technologie i typy struktury związane z tych technologii.  
  
|**Nazwa technologii**|**Typy**|**Scenariusze**|  
|-------------------------|--------------------|-------------------|  
|**Serializacja kontraktu danych**|<xref:System.Runtime.Serialization.DataContractAttribute> <br /> <xref:System.Runtime.Serialization.DataMemberAttribute> <br /> <xref:System.Runtime.Serialization.DataContractSerializer> <br /> <xref:System.Runtime.Serialization.NetDataContractSerializer> <br /> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> <br /> <xref:System.Runtime.Serialization.ISerializable>|Trwałość ogólne<br />Usługi sieci Web<br />JSON|  
|**Serializacja XML**|<xref:System.Xml.Serialization.XmlSerializer>|Format XML z pełną kontrolę nad kształtu XML|  
|**Środowisko uruchomieniowe serializacji (pliku binarnego i SOAP)**|<xref:System.SerializableAttribute> <br /> <xref:System.Runtime.Serialization.ISerializable> <br /> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> <br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>|Wywołaniem funkcji zdalnych .NET|  
  
 **CZY ✓** Pomyśl o serializacji podczas projektowania nowych typów.  
  
## <a name="choosing-the-right-serialization-technology-to-support"></a>Wybranie opcji technologii serializacji prawo do pomocy technicznej  
 **ROZWAŻ ✓** obsługę serializacji kontraktu danych, jeśli wystąpień tego typu może być konieczne może być utrwalona lub używany w usługach sieci Web.  
  
 **ROZWAŻ ✓** obsługę serializacji XML zamiast lub oprócz serializacji kontraktu danych, jeśli potrzebujesz większej kontroli nad formacie XML, który jest generowany, gdy typ jest serializowany.  
  
 Może to być konieczne w niektórych współdziałanie, który skonstruować scenariusze, w których należy użyć pliku XML, który nie jest obsługiwany przez serializacji kontraktu danych, na przykład, aby wygenerować atrybutów XML.  
  
 **ROZWAŻ ✓** obsługę serializacji środowiska uruchomieniowego, jeśli konieczne są przesyłane między granicami .NET Remoting wystąpień tego typu.  
  
 **X należy UNIKAĆ** Obsługa środowiska uruchomieniowego serializacji lub serializacji XML tylko ze względów ogólne trwałości. Zamiast tego użyć serializacji kontraktu danych.  
  
## <a name="supporting-data-contract-serialization"></a>Pomocniczych serializacji kontrakt danych  
 Typy może obsługiwać serializację kontraktu danych poprzez zastosowanie <xref:System.Runtime.Serialization.DataContractAttribute> do typu i <xref:System.Runtime.Serialization.DataMemberAttribute> do elementów członkowskich (pola i właściwości) tego typu.  
  
 **ROZWAŻ ✓** oznaczenie elementy członkowskie danych z typu publiczne, jeśli typ może być używany w częściowej relacji zaufania.  
  
 W trybie pełnego zaufania serializatorów kontraktu danych można serializacji i deserializacji niepubliczne typy i składniki, ale tylko publiczne elementy Członkowskie mogą być serializowane i zdeserializować w częściowej relacji zaufania.  
  
 **CZY ✓** implementuje metody pobierającej i ustawiającej dla wszystkich właściwości, które mają <xref:System.Runtime.Serialization.DataMemberAttribute>. Serializatorów kontraktu danych wymaga metody pobierającej i ustawiającej dla typu, który ma być traktowane jako możliwy do serializacji. (W .NET Framework 3.5 z dodatkiem SP1, niektóre właściwości kolekcji można tylko do pobrania.) Jeśli typ nie można używać w częściowej relacji zaufania, co najmniej jeden z metody dostępu właściwości można niepublicznych.  
  
 **ROZWAŻ ✓** przy użyciu wywołania zwrotne serializacji dla inicjowania wystąpienia zdeserializowany.  
  
 Konstruktorów nie są wywoływane, gdy obiekty są deserializacji. (Istnieją wyjątki od reguły. Konstruktory kolekcje oznaczonych <xref:System.Runtime.Serialization.CollectionDataContractAttribute> wywoływane podczas deserializacji.) W związku z tym wszelka logika wykonujący podczas konstruowania normalne musi można zaimplementować jako jeden z wywołania zwrotne serializacji.  
  
 `OnDeserializedAttribute`jest to atrybut najczęściej używane wywołania zwrotnego. Inne atrybuty z rodziny są <xref:System.Runtime.Serialization.OnDeserializingAttribute>, <xref:System.Runtime.Serialization.OnSerializingAttribute>, i <xref:System.Runtime.Serialization.OnSerializedAttribute>. One służy do oznaczania wywołania zwrotne, które są wykonywane przed deserializacji, przed serializacji, a na końcu po serializacji, odpowiednio.  
  
 **ROZWAŻ ✓** przy użyciu <xref:System.Runtime.Serialization.KnownTypeAttribute> wskazująca konkretne typy, które mają być używane podczas deserializacji wykresu obiektu złożonego.  
  
 **CZY ✓** należy wziąć pod uwagę zgodność z poprzednimi wersjami i do przodu podczas tworzenia lub zmiany typów możliwych do serializacji.  
  
 Należy pamiętać, który serializowany strumieni przyszłych wersjach tego typu mogą zostać przeprowadzona deserializacja bieżącą wersję tego typu i na odwrót.  
  
 Upewnij się, że rozumiesz, że elementy członkowskie danych, nawet prywatne i wewnętrzne, nie można zmienić ich nazw, typu lub nawet ich kolejność, w przyszłych wersjach tego typu, chyba że specjalne zadbać o zachowanie zamówienia przy użyciu jawne parametry atrybutów kontraktu danych .  
  
 Testowanie zgodności serializacji podczas wprowadzania zmian do typów możliwych do serializacji. Spróbuj wykonać deserializacji nowej wersji w starszej wersji i na odwrót.  
  
 **ROZWAŻ ✓** implementacja <xref:System.Runtime.Serialization.IExtensibleDataObject> umożliwiają dwustronną komunikację między różnymi wersjami tego typu.  
  
 Interfejs umożliwia serializator upewnić się, że nie są żadne dane utracone podczas Pełna zgodnooć wersji. <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A?displayProperty=nameWithType> Właściwość jest używana do przechowywania wszelkich danych z przyszłych wersji typu, który jest nieznany w bieżącej wersji, a więc go nie można zapisać go w jego elementy członkowskie danych. Jeśli bieżącą wersję jest następnie serializacji i deserializacji w przyszłych wersjach, dodatkowe dane są dostępne w strumieniu serializowanym.  
  
## <a name="supporting-xml-serialization"></a>Obsługa serializacji XML  
 Serializacja kontraktu danych jest głównym (ustawienie domyślne) technologii serializacji w programie .NET Framework, ale są serializacji scenariusze, które nie obsługuje serializacji kontraktu danych. Na przykład go nie zapewniają pełną kontrolę nad kształtu XML utworzony lub zużyte przez serializator. Jeśli takie dokładnej kontroli jest wymagana, serializacji XML ma być używane, i należy do sieci obsługują tę technologię serializacji typy projektów.  
  
 **X należy UNIKAĆ** projektowania z typów specjalnie z myślą o serializacji XML, chyba że masz bardzo silnych Przyczyna do kontrolowania kształtu XML utworzony. Ta technologia serializacji została zastąpiona przez serializacji kontrakt danych opisanych w poprzedniej sekcji.  
  
 **ROZWAŻ ✓** implementacja <xref:System.Xml.Serialization.IXmlSerializable> interfejsu, jeśli chcesz większą kontrolę nad kształtu serializacji XML niż co to jest oferowany przez stosowanie atrybutów serializacji XML. Dwie metody interfejsu <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> i <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>, pozwala na w pełni kontrolować serializowanym strumieniu XML. Można również sterować schematu XML, który pobiera wygenerowany dla typu przez zastosowanie `XmlSchemaProviderAttribute`.  
  
## <a name="supporting-runtime-serialization"></a>Obsługa czasu wykonywania serializacji  
 Środowisko uruchomieniowe serializacji to technologia używana przez .NET Remoting. Jeśli uważasz, że Twoje typy będzie transportowane przy użyciu funkcji zdalnych .NET, należy upewnij się, że obsługuje środowisko uruchomieniowe serializacji.  
  
 Podstawowa pomoc techniczna dla serializacji środowiska uruchomieniowego można podać, stosując <xref:System.SerializableAttribute>, i bardziej zaawansowanych scenariuszy może dotyczyć Implementowanie prostego wzorca serializacji środowiska uruchomieniowego (implementować <xref:System.Runtime.Serialization.ISerializable> i podaj Konstruktor serializacji).  
  
 **ROZWAŻ ✓** obsługę środowiska uruchomieniowego serializacji, jeśli Twoje typów będą używane z funkcji zdalnych .NET. Na przykład <xref:System.AddIn?displayProperty=nameWithType> przestrzeń nazw używa funkcji zdalnych .NET, a wszystkie typy wymieniane między `System.AddIn` dodatków musi obsługiwać środowiska uruchomieniowego serializacji.  
  
 **ROZWAŻ ✓** implementacja wzorca serializacji środowiska uruchomieniowego, jeśli mają pełną kontrolę nad procesem serializacji. Na przykład jeśli chcesz przekształcania danych jako jego pobiera serializowany lub deserializowany.  
  
 Wzorzec jest bardzo proste. Wszystko co należy zrobić to wdrożenie <xref:System.Runtime.Serialization.ISerializable> interfejsu i podaj specjalne konstruktora, który jest używany podczas deserializowany jest obiekt.  
  
 **CZY ✓** upewnij chroniony Konstruktor serializacji i podaj dwóch parametrów typu i o nazwie dokładnie tak jak pokazano w przykładzie poniżej.  
  
```  
[Serializable]  
public class Person : ISerializable {  
    protected Person(SerializationInfo info, StreamingContext context) {  
        ...  
    }  
}  
```  
  
 **CZY ✓** zaimplementować `ISerializable` elementy członkowskie jawnie.  
  
 **CZY ✓** Zastosuj żądanie łącza do <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> implementacji. Dzięki temu, że tylko w pełni zaufanych core i serializator środowiska uruchomieniowego mieć dostępu do elementu członkowskiego.  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)  
 [Zalecenia dotyczące użytkowania](../../../docs/standard/design-guidelines/usage-guidelines.md)
