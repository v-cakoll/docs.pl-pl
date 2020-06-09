---
title: Odwołanie do schematu kontraktu danych
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts [WCF], schema reference
ms.assetid: 9ebb0ebe-8166-4c93-980a-7c8f1f38f7c0
ms.openlocfilehash: 04d1f753e5788460404942a21a29e1612f674e90
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593571"
---
# <a name="data-contract-schema-reference"></a>Odwołanie do schematu kontraktu danych

W tym temacie opisano podzestaw schematu XML (XSD) używany przez program <xref:System.Runtime.Serialization.DataContractSerializer> do opisywania typów środowiska uruchomieniowego języka wspólnego (CLR) na potrzeby serializacji XML.

## <a name="datacontractserializer-mappings"></a>Mapowania DataContractSerializer

`DataContractSerializer`Mapuje typy CLR na XSD, gdy metadane są eksportowane z usługi Windows Communication Foundation (WCF) przy użyciu punktu końcowego metadanych lub [Narzędzia do obsługi metadanych ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md). Aby uzyskać więcej informacji, zobacz [serializator kontraktu danych](data-contract-serializer.md).

`DataContractSerializer`Ponadto mapuje XSD na typy CLR, gdy Svcutil. exe jest używany do uzyskiwania dostępu do Web Services Description Language (WSDL) lub dokumentów XSD i generowania kontraktów danych dla usług lub klientów.

Tylko wystąpienia schematu XML, które są zgodne z wymaganiami podanymi w tym dokumencie, można zamapować na typy CLR przy użyciu `DataContractSerializer` .

### <a name="support-levels"></a>Poziomy pomocy technicznej

Program `DataContractSerializer` udostępnia następujące poziomy obsługi dla danej funkcji schematu XML:

- **Obsługiwane**. Istnieje jawne mapowanie od tej funkcji do typów lub atrybutów CLR (lub obu) przy użyciu `DataContractSerializer` .

- **Zignorowano**. Funkcja jest dozwolona w schematach importowanych przez `DataContractSerializer` , ale nie ma wpływu na generowanie kodu.

- **Zabronione**. Program nie `DataContractSerializer` obsługuje importowania schematu przy użyciu funkcji. Na przykład, Svcutil. exe, podczas uzyskiwania dostępu do WSDL ze schematem, który używa takich funkcji, powraca do użycia <xref:System.Xml.Serialization.XmlSerializer> zamiast. Jest to domyślnie.

## <a name="general-information"></a>Informacje ogólne

- Przestrzeń nazw schematu jest opisana w [schemacie XML](https://www.w3.org/2001/XMLSchema). Prefiks "XS" jest używany w tym dokumencie.

- Wszystkie atrybuty z przestrzeni nazw nienależących do schematu są ignorowane.

- Wszelkie adnotacje (z wyjątkiem tych opisanych w tym dokumencie) są ignorowane.

### <a name="xsschema-attributes"></a>\<xs:schema>: atrybuty

|Atrybut|Contract|
|---------------|------------------|
|`attributeFormDefault`|Ignorowane.|
|`blockDefault`|Ignorowane.|
|`elementFormDefault`|Musi być kwalifikowana. Wszystkie elementy muszą być kwalifikowane dla schematu, który ma być obsługiwany przez program `DataContractSerializer` . Można to osiągnąć przez ustawienie xs:schema/@elementFormDefault "kwalifikowana" lub przez ustawienie xs:element/@form "kwalifikowana" w każdej deklaracji poszczególnych elementów.|
|`finalDefault`|Ignorowane.|
|`Id`|Ignorowane.|
|`targetNamespace`|Obsługiwane i mapowane do przestrzeni nazw kontraktu danych. Jeśli ten atrybut nie jest określony, zostanie użyta pusta przestrzeń nazw. Nie może być zarezerwowaną przestrzenią nazw `http://schemas.microsoft.com/2003/10/Serialization/` .|
|`version`|Ignorowane.|

### <a name="xsschema-contents"></a>\<xs:schema>: zawartość

|Zawartość|Schemat|
|--------------|------------|
|`include`|Obsługiwane. `DataContractSerializer`obsługuje polecenie XS: include i xs: import. Jednak program Svcutil. exe ogranicza następujące elementy `xs:include/@schemaLocation` i `xs:import/@location` odwołuje się do nich, gdy metadane są ładowane z pliku lokalnego. Lista plików schematu musi być przenoszona przez mechanizm poza pasmem, a nie `include` w tym przypadku. `include` dokumenty schematu d są ignorowane.|
|`redefine`|Zabrania. Korzystanie z programu `xs:redefine` jest zabronione ze `DataContractSerializer` względów bezpieczeństwa: `x:redefine` wymaga `schemaLocation` przestrzegania. W pewnych okolicznościach Svcutil. exe przy użyciu usługi DataContract ogranicza użycie programu `schemaLocation` .|
|`import`|Obsługiwane. `DataContractSerializer`obsługuje `xs:include` i `xs:import` . Jednak program Svcutil. exe ogranicza następujące elementy `xs:include/@schemaLocation` i `xs:import/@location` odwołuje się do nich, gdy metadane są ładowane z pliku lokalnego. Lista plików schematu musi być przenoszona przez mechanizm poza pasmem, a nie `include` w tym przypadku. `include` dokumenty schematu d są ignorowane.|
|`simpleType`|Obsługiwane. Zapoznaj się z `xs:simpleType` sekcją.|
|`complexType`|Obsługiwane mapowania do kontraktów danych. Zapoznaj się z `xs:complexType` sekcją.|
|`group`|Ignorowane. `DataContractSerializer`Program nie obsługuje używania elementów `xs:group` , `xs:attributeGroup` i `xs:attribute` . Te deklaracje są ignorowane jako elementy podrzędne `xs:schema` , ale nie można się do nich odwoływać z wewnątrz `complexType` lub innych obsługiwanych konstrukcji.|
|`attributeGroup`|Ignorowane. `DataContractSerializer`Program nie obsługuje używania elementów `xs:group` , `xs:attributeGroup` i `xs:attribute` . Te deklaracje są ignorowane jako elementy podrzędne `xs:schema` , ale nie można się do nich odwoływać z wewnątrz `complexType` lub innych obsługiwanych konstrukcji.|
|`element`|Obsługiwane. Zobacz globalna Deklaracja elementu (JŚCIOWA).|
|`attribute`|Ignorowane. `DataContractSerializer`Program nie obsługuje używania elementów `xs:group` , `xs:attributeGroup` i `xs:attribute` . Te deklaracje są ignorowane jako elementy podrzędne `xs:schema` , ale nie można się do nich odwoływać z wewnątrz `complexType` lub innych obsługiwanych konstrukcji.|
|`notation`|Ignorowane.|

## <a name="complex-types--xscomplextype"></a>Typy złożone —\<xs:complexType>

### <a name="general-information"></a>Informacje ogólne

Każdy typ złożony \<xs:complexType> jest mapowany do kontraktu danych.

### <a name="xscomplextype-attributes"></a>\<xs:complexType>: atrybuty

|Atrybut|Schemat|
|---------------|------------|
|`abstract`|Musi mieć wartość false (domyślnie).|
|`block`|Zabrania.|
|`final`|Ignorowane.|
|`id`|Ignorowane.|
|`mixed`|Musi mieć wartość false (domyślnie).|
|`name`|Obsługiwane i zamapowane na nazwę kontraktu danych. Jeśli nazwa zawiera kilka kropek, podejmowana jest próba mapowania typu na typ wewnętrzny. Na przykład typ złożony o nazwie `A.B` Maps do typu kontraktu danych, który jest typem wewnętrznym typu z nazwą kontraktu danych `A` , ale tylko wtedy, gdy istnieje taki typ kontraktu danych. Możliwe jest więcej niż jeden poziom zagnieżdżenia: na przykład `A.B.C` może być typem wewnętrznym, ale tylko wtedy, gdy `A` `A.B` istnieją.|

### <a name="xscomplextype-contents"></a>\<xs:complexType>: zawartość

|Zawartość|Schemat|
|--------------|------------|
|`simpleContent`|Rozszerzenia są zabronione.<br /><br /> Ograniczenie jest dozwolone tylko z `anySimpleType` .|
|`complexContent`|Obsługiwane. Zobacz "dziedziczenie".|
|`group`|Zabrania.|
|`all`|Zabrania.|
|`choice`|Forbidden|
|`sequence`|Obsługiwane, mapuje do członków danych kontraktu danych.|
|`attribute`|Zabronione, nawet jeśli użycie = "zabronione" (z jednym wyjątkiem). Obsługiwane są tylko opcjonalne atrybuty z przestrzeni nazw schematu serializacji standardowej. Nie są one mapowane na elementy członkowskie danych w modelu programowania kontraktu danych. Obecnie tylko jeden taki atrybut ma znaczenie i został omówiony w sekcji ISerializable. Wszystkie pozostałe są ignorowane.|
|`attributeGroup`|Zabrania. W wersji V1 programu WCF program `DataContractSerializer` ignoruje obecność `attributeGroup` wewnątrz `xs:complexType` .|
|`anyAttribute`|Zabrania.|
|ciągiem|Mapuje do kontraktu danych bez składowych danych.|

### <a name="xssequence-in-a-complex-type-attributes"></a>\<xs:sequence>w typie złożonym: atrybuty

|Atrybut|Schemat|
|---------------|------------|
|`id`|Ignorowane.|
|`maxOccurs`|Musi mieć wartość 1 (domyślna).|
|`minOccurs`|Musi mieć wartość 1 (domyślna).|

### <a name="xssequence-in-a-complex-type-contents"></a>\<xs:sequence>w typie złożonym: zawartość

|Zawartość|Schemat|
|--------------|------------|
|`element`|Każde wystąpienie jest mapowane na element członkowski danych.|
|`group`|Zabrania.|
|`choice`|Zabrania.|
|`sequence`|Zabrania.|
|`any`|Zabrania.|
|ciągiem|Mapuje do kontraktu danych bez składowych danych.|

## <a name="elements--xselement"></a>Części\<xs:element>

### <a name="general-information"></a>Informacje ogólne

`<xs:element>`może wystąpić w następujących kontekstach:

- Może wystąpić w ramach `<xs:sequence>` , która opisuje element członkowski danych regularnego (niebędącego kolekcją) kontraktu danych. W takim przypadku `maxOccurs` atrybut musi mieć wartość 1. (Wartość 0 jest niedozwolona).

- Może wystąpić w elemencie `<xs:sequence>` , który opisuje element członkowski danych w ramach kontraktu danych kolekcji. W tym przypadku `maxOccurs` atrybut musi mieć wartość większą niż 1 lub "Unbounded".

- Może wystąpić w ramach `<xs:schema>` deklaracji elementu globalnego (jściowa).

### <a name="xselement-with-maxoccurs1-within-an-xssequence-data-members"></a>\<xs:element>z elementami maxOccurs = 1 w ramach \<xs:sequence> (składowych danych)

|Atrybut|Schemat|
|---------------|------------|
|`ref`|Zabrania.|
|`name`|Obsługiwane, mapuje na nazwę elementu członkowskiego danych.|
|`type`|Obsługiwane, mapuje do typu elementu członkowskiego danych. Aby uzyskać więcej informacji, zobacz Mapowanie typu/elementu podstawowego. Jeśli nie zostanie określony (a element nie zawiera typu anonimowego), `xs:anyType` zostanie przyjęty.|
|`block`|Ignorowane.|
|`default`|Zabrania.|
|`fixed`|Zabrania.|
|`form`|Musi być kwalifikowana. Ten atrybut może być ustawiony `elementFormDefault` w dniu `xs:schema` .|
|`id`|Ignorowane.|
|`maxOccurs`|1|
|`minOccurs`|Mapuje do <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> właściwości elementu członkowskiego danych ( `IsRequired` ma wartość true, jeśli jest równa `minOccurs` 1).|
|`nillable`|Ma wpływ na mapowanie typu. Zobacz mapowanie typu/elementu podstawowego.|

### <a name="xselement-with-maxoccurs1-within-an-xssequence-collections"></a>\<xs:element>z elementem maxOccurs>1 w elemencie \<xs:sequence> (Kolekcje)

- Mapuje na <xref:System.Runtime.Serialization.CollectionDataContractAttribute> .

- W przypadku typów kolekcji tylko jeden element xs: jest dozwolony w obrębie sekwencji xs:.

 Kolekcje mogą być następujące:

- Regularne kolekcje (na przykład tablice).

- Kolekcje słowników (mapowanie jednej wartości na inną, na przykład a <xref:System.Collections.Hashtable> ).

- Jedyna różnica między słownikiem i tablicą typu pary klucz/wartość znajduje się w wygenerowanym modelu programowania. Istnieje mechanizm adnotacji schematu, którego można użyć, aby wskazać, że dany typ jest kolekcją słownika.

Reguły dla `ref` ,,, `block` , `default` `fixed` `form` i `id` atrybuty są takie same, jak w przypadku braku dla kolekcji. Inne atrybuty obejmują te zawarte w poniższej tabeli.

|Atrybut|Schemat|
|---------------|------------|
|`name`|Obsługiwane, mapuje do <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> właściwości w `CollectionDataContractAttribute` atrybucie.|
|`type`|Obsługiwane, mapuje do typu przechowywanego w kolekcji.|
|`maxOccurs`|Większe niż 1 lub "niepowiązane". Schemat kontrolera domeny powinien używać "Unbounded".|
|`minOccurs`|Ignorowane.|
|`nillable`|Ma wpływ na mapowanie typu. Ten atrybut jest ignorowany dla kolekcji słowników.|

### <a name="xselement-within-an-xsschema-global-element-declaration"></a>\<xs:element>w \<xs:schema> deklaracji elementu globalnego

- Deklaracja elementu globalnego (JŚCIOWA), która ma taką samą nazwę i przestrzeń nazw, jak typ w schemacie lub definiuje typ anonimowy wewnątrz siebie, jest określana jako skojarzona z typem.

- Eksport schematu: skojarzone GEDs są generowane dla każdego wygenerowanego typu, zarówno proste, jak i złożone.

- Deserializacja/Serializacja: skojarzone GEDs są używane jako elementy główne dla tego typu.

- Importowanie schematu: skojarzone GEDs nie są wymagane i są ignorowane, jeśli są zgodne z następującymi regułami (chyba że definiują typy).

|Atrybut|Schemat|
|---------------|------------|
|`abstract`|Dla skojarzonych GEDs należy określić wartość false.|
|`block`|Niedozwolone w skojarzonych GEDs.|
|`default`|Niedozwolone w skojarzonych GEDs.|
|`final`|Dla skojarzonych GEDs należy określić wartość false.|
|`fixed`|Niedozwolone w skojarzonych GEDs.|
|`id`|Ignorowane.|
|`name`|Obsługiwane. Zobacz definicję skojarzonych GEDs.|
|`nillable`|Dla skojarzonych GEDs należy mieć wartość true.|
|`substitutionGroup`|Niedozwolone w skojarzonych GEDs.|
|`type`|Obsługiwane i muszą być zgodne z skojarzonym typem dla skojarzonych GEDs (chyba że element zawiera typ anonimowy).|

### <a name="xselement-contents"></a>\<xs:element>: zawartość

|Zawartość|Schemat|
|--------------|------------|
|`simpleType`|Obsługiwane. *|
|`complexType`|Obsługiwane. *|
|`unique`|Ignorowane.|
|`key`|Ignorowane.|
|`keyref`|Ignorowane.|
|puste|Obsługiwane.|

\*Użycie `simpleType` `complexType,` mapowania i dla typów anonimowych jest takie samo jak w przypadku typów nieanonimowych, z tą różnicą, że nie ma żadnych kontraktów danych anonimowych i dlatego zostanie utworzona nazwana kontrakt danych z wygenerowaną nazwą pochodną od nazwy elementu. Reguły dla typów anonimowych znajdują się na poniższej liście:

- Szczegóły implementacji WCF: Jeśli `xs:element` nazwa nie zawiera kropek, typ anonimowy jest mapowany na typ wewnętrzny zewnętrznego kontraktu danych. Jeśli nazwa zawiera okresy, typ kontraktu danych będących wynikiem jest niezależny (nie jest typem wewnętrznym).

- Nazwa wygenerowanej kontraktu danych typu wewnętrznego to nazwa kontraktu danych typu zewnętrznego, po którym następuje kropka, nazwa elementu i ciąg "Type".

- Jeśli kontrakt danych o takiej nazwie już istnieje, nazwa jest unikatowa poprzez dołączenie "1", "2", "3" i tak dalej, aż do utworzenia unikatowej nazwy.

## <a name="simple-types---xssimpletype"></a>Typy proste —\<xs:simpleType>

### <a name="xssimpletype-attributes"></a>\<xs:simpleType>: atrybuty

|Atrybut|Schemat|
|---------------|------------|
|`final`|Ignorowane.|
|`id`|Ignorowane.|
|`name`|Obsługiwane, mapuje do nazwy kontraktu danych.|

### <a name="xssimpletype-contents"></a>\<xs:simpleType>: zawartość

|Zawartość|Schemat|
|--------------|------------|
|`restriction`|Obsługiwane. Mapuje na kontrakty danych wyliczenia. Ten atrybut jest ignorowany, jeśli nie pasuje do wzorca wyliczenia. Zapoznaj się z `xs:simpleType` sekcją ograniczenia.|
|`list`|Obsługiwane. Mapuje, aby oflagować Kontrakty danych wyliczenia. Zapoznaj się z `xs:simpleType` sekcją list.|
|`union`|Zabrania.|

### \<xs:restriction>

- Ograniczenia typu złożonego są obsługiwane tylko dla elementu Base = " `xs:anyType` ".

- Ograniczenia typu prostego `xs:string` , które nie mają żadnych aspektów ograniczeń innych niż `xs:enumeration` są zamapowane na kontrakty danych wyliczenia.

- Wszystkie inne ograniczenia typu prostego są mapowane na typy, które ograniczają. Na przykład ograniczenie `xs:int` mapowania do liczby całkowitej jest równie `xs:int` samo. Aby uzyskać więcej informacji na temat mapowania typu pierwotnego, zobacz Mapowanie typu/elementu podstawowego.

### <a name="xsrestriction-attributes"></a>\<xs:restriction>: atrybuty

|Atrybut|Schemat|
|---------------|------------|
|`base`|Musi być obsługiwanym typem prostym lub `xs:anyType` .|
|`id`|Ignorowane.|

### <a name="xsrestriction-for-all-other-cases-contents"></a>\<xs:restriction>we wszystkich innych przypadkach: zawartość

|Zawartość|Schemat|
|--------------|------------|
|`simpleType`|Jeśli jest obecny, musi pochodzić od obsługiwanego typu pierwotnego.|
|`minExclusive`|Ignorowane.|
|`minInclusive`|Ignorowane.|
|`maxExclusive`|Ignorowane.|
|`maxInclusive`|Ignorowane.|
|`totalDigits`|Ignorowane.|
|`fractionDigits`|Ignorowane.|
|`length`|Ignorowane.|
|`minLength`|Ignorowane.|
|`maxLength`|Ignorowane.|
|`enumeration`|Ignorowane.|
|`whiteSpace`|Ignorowane.|
|`pattern`|Ignorowane.|
|puste|Obsługiwane.|

## <a name="enumeration"></a>Wyliczenie

### <a name="xsrestriction-for-enumerations-attributes"></a>\<xs:restriction>dla wyliczeń: atrybuty

|Atrybut|Schemat|
|---------------|------------|
|`base`|Jeśli jest obecny, musi być `xs:string` .|
|`id`|Ignorowane.|

### <a name="xsrestriction-for-enumerations-contents"></a>\<xs:restriction>dla wyliczeń: zawartość

|Zawartość|Schemat|
|--------------|------------|
|`simpleType`|Jeśli jest obecny, musi to być ograniczenie wyliczenia obsługiwane przez umowę danych (w tej sekcji).|
|`minExclusive`|Ignorowane.|
|`minInclusive`|Ignorowane.|
|`maxExclusive`|Ignorowane.|
|`maxInclusive`|Ignorowane.|
|`totalDigits`|Ignorowane.|
|`fractionDigits`|Ignorowane.|
|`length`|Zabrania.|
|`minLength`|Zabrania.|
|`maxLength`|Zabrania.|
|`enumeration`|Obsługiwane. Wyliczenie "ID" jest ignorowane, a "value" mapuje do nazwy wartości w kontrakcie danych wyliczenia.|
|`whiteSpace`|Zabrania.|
|`pattern`|Zabrania.|
|ciągiem|Obsługiwane, mapuje do pustego typu wyliczenia.|

 Poniższy kod przedstawia klasę wyliczenia języka C#.

```csharp
public enum MyEnum
{
  first = 3,
  second = 4,
  third =5
}
```

Ta klasa mapuje do poniższego schematu przez `DataContractSerializer` . Jeśli wartości wyliczenia zaczynają się od 1, `xs:annotation` bloki nie są generowane.

```xml
<xs:simpleType name="MyEnum">
  <xs:restriction base="xs:string">
    <xs:enumeration value="first">
      <xs:annotation>
        <xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">
          3
          </EnumerationValue>
        </xs:appinfo>
      </xs:annotation>
    </xs:enumeration>
    <xs:enumeration value="second">
      <xs:annotation>
        <xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">
          4
          </EnumerationValue>
        </xs:appinfo>
      </xs:annotation>
    </xs:enumeration>
  </xs:restriction>
</xs:simpleType>
```

### \<xs:list>

`DataContractSerializer`mapuje typy wyliczeniowe oznaczone jako z `System.FlagsAttribute` na `xs:list` pochodne od `xs:string` . Żadne inne `xs:list` odmiany nie są obsługiwane.

### <a name="xslist-attributes"></a>\<xs:list>: atrybuty

|Atrybut|Schemat|
|---------------|------------|
|`itemType`|Zabrania.|
|`id`|Ignorowane.|

### <a name="xslist-contents"></a>\<xs:list>: zawartość

|Zawartość|Schemat|
|--------------|------------|
|`simpleType`|Musi być ograniczeniem `xs:string` użycia `xs:enumeration` zestawu reguł.|

Jeśli wartość wyliczenia nie jest zgodna z potęgą 2 postępu (domyślnie dla flag), wartość jest przechowywana w `xs:annotation/xs:appInfo/ser:EnumerationValue` elemencie.

Na przykład poniższy kod oznacza typ wyliczeniowy.

```csharp
[Flags]
public enum AuthFlags
{
  AuthAnonymous = 1,
  AuthBasic = 2,
  AuthNTLM = 4,
  AuthMD5 = 16,
  AuthWindowsLiveID = 64,
}
```

Ten typ jest mapowany na poniższy schemat.

```xml
<xs:simpleType name="AuthFlags">
    <xs:list>
      <xs:simpleType>
        <xs:restriction base="xs:string">
          <xs:enumeration value="AuthAnonymous" />
          <xs:enumeration value="AuthBasic" />
          <xs:enumeration value="AuthNTLM" />
          <xs:enumeration value="AuthMD5">
            <xs:annotation>
              <xs:appinfo>
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">16</EnumerationValue>
              </xs:appinfo>
            </xs:annotation>
          </xs:enumeration>
          <xs:enumeration value="AuthWindowsLiveID">
            <xs:annotation>
              <xs:appinfo>
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">64</EnumerationValue>
              </xs:appinfo>
            </xs:annotation>
          </xs:enumeration>
        </xs:restriction>
      </xs:simpleType>
    </xs:list>
  </xs:simpleType>
```

## <a name="inheritance"></a>Dziedziczenie

### <a name="general-rules"></a>Reguły ogólne

Kontrakt danych może dziedziczyć z innego kontraktu danych. Takie Kontrakty danych są mapowane na bazę i są wyprowadzane przez typy rozszerzeń przy użyciu `<xs:extension>` konstrukcji schematu XML.

Kontrakt danych nie może dziedziczyć z kontraktu danych kolekcji.

Na przykład poniższy kod jest kontraktem danych.

```csharp
[DataContract]
public class Person
{
  [DataMember]
  public string Name;
}
[DataContract]
public class Employee : Person
{
  [DataMember]
  public int ID;
}
```

Ten kontrakt danych mapuje do następującej deklaracji typu schematu XML.

```xml
<xs:complexType name="Employee">
 <xs:complexContent mixed="false">
  <xs:extension base="tns:Person">
   <xs:sequence>
    <xs:element minOccurs="0" name="ID" type="xs:int"/>
   </xs:sequence>
  </xs:extension>
 </xs:complexContent>
</xs:complexType>
<xs:complexType name="Person">
 <xs:sequence>
  <xs:element minOccurs="0" name="Name"
    nillable="true" type="xs:string"/>
 </xs:sequence>
</xs:complexType>
```

### <a name="xscomplexcontent-attributes"></a>\<xs:complexContent>: atrybuty

|Atrybut|Schemat|
|---------------|------------|
|`id`|Ignorowane.|
|`mixed`|Musi mieć wartość false.|

### <a name="xscomplexcontent-contents"></a>\<xs:complexContent>: zawartość

|Zawartość|Schemat|
|--------------|------------|
|`restriction`|Zabronione, z wyjątkiem sytuacji, gdy Base = " `xs:anyType` ". Drugie jest równoważne umieszczaniu zawartości `xs:restriction` bezpośrednio w kontenerze `xs:complexContent` .|
|`extension`|Obsługiwane. Mapuje na dziedziczenie kontraktu danych.|

### <a name="xsextension-in-xscomplexcontent-attributes"></a>\<xs:extension>w \<xs:complexContent> : atrybuty

|Atrybut|Schemat|
|---------------|------------|
|`id`|Ignorowane.|
|`base`|Obsługiwane. Mapuje do typu kontraktu danych podstawowych, z którego dziedziczy ten typ.|

### <a name="xsextension-in-xscomplexcontent-contents"></a>\<xs:extension>w \<xs:complexContent> : zawartość

Reguły są takie same jak w przypadku `<xs:complexType>` zawartości.

Jeśli `<xs:sequence>` jest podany, jego elementy członkowskie są mapowane na dodatkowe składowe danych, które znajdują się w umowie danych pochodnych.

Jeśli typ pochodny zawiera element o takiej samej nazwie jak element w typie podstawowym, deklaracja duplikatu elementu mapuje do składowej danych o nazwie, która jest generowana jako unikatowa. Dodatnie liczby całkowite są dodawane do nazwy elementu członkowskiego danych ("member1", "member2" itd.), dopóki nie zostanie znaleziona unikatowa nazwa. Drugiej

- Jeśli kontrakt danych pochodnych ma element członkowski danych o tej samej nazwie i typie co element członkowski danych w podstawowym kontrakcie danych, program `DataContractSerializer` wygeneruje ten odpowiadający element w typie pochodnym.

- Jeśli kontrakt danych pochodnych ma element członkowski danych o takiej samej nazwie jak element członkowski danych w podstawowej umowie danych, ale inny typ, `DataContractSerializer` importuje schemat z elementem typu `xs:anyType` w deklaracjach typu podstawowego i pochodnym. Oryginalna nazwa typu jest zachowywana w `xs:annotations/xs:appInfo/ser:ActualType/@Name` .

Obie warianty mogą prowadzić do schematu z niejednoznacznym modelem zawartości, który zależy od kolejności odpowiednich elementów członkowskich danych.

## <a name="typeprimitive-mapping"></a>Typ/mapowanie pierwotne

`DataContractSerializer`Używa następującego mapowania dla typów pierwotnych schematu XML.

|Typ XSD|Typ .NET|
|--------------|---------------|
|`anyType`|<xref:System.Object>.|
|`anySimpleType`|<xref:System.String>.|
|`duration`|<xref:System.TimeSpan>.|
|`dateTime`|<xref:System.DateTime>.|
|`dateTimeOffset`|<xref:System.DateTime>i <xref:System.TimeSpan> dla przesunięcia. Zobacz serializacji DateTimeOffset poniżej.|
|`time`|<xref:System.String>.|
|`date`|<xref:System.String>.|
|`gYearMonth`|<xref:System.String>.|
|`gYear`|<xref:System.String>.|
|`gMonthDay`|<xref:System.String>.|
|`gDay`|<xref:System.String>.|
|`gMonth`|<xref:System.String>.|
|`boolean`|<xref:System.Boolean>|
|`base64Binary`|<xref:System.Byte>macierzy.|
|`hexBinary`|<xref:System.String>.|
|`float`|<xref:System.Single>.|
|`double`|<xref:System.Double>.|
|`anyURI`|<xref:System.Uri>.|
|`QName`|<xref:System.Xml.XmlQualifiedName>.|
|`string`|<xref:System.String>.|
|`normalizedString`|<xref:System.String>.|
|`token`|<xref:System.String>.|
|`language`|<xref:System.String>.|
|`Name`|<xref:System.String>.|
|`NCName`|<xref:System.String>.|
|`ID`|<xref:System.String>.|
|`IDREF`|<xref:System.String>.|
|`IDREFS`|<xref:System.String>.|
|`ENTITY`|<xref:System.String>.|
|`ENTITIES`|<xref:System.String>.|
|`NMTOKEN`|<xref:System.String>.|
|`NMTOKENS`|<xref:System.String>.|
|`decimal`|<xref:System.Decimal>.|
|`integer`|<xref:System.Int64>.|
|`nonPositiveInteger`|<xref:System.Int64>.|
|`negativeInteger`|<xref:System.Int64>.|
|`long`|<xref:System.Int64>.|
|`int`|<xref:System.Int32>.|
|`short`|<xref:System.Int16>.|
|`Byte`|<xref:System.SByte>.|
|`nonNegativeInteger`|<xref:System.Int64>.|
|`unsignedLong`|<xref:System.UInt64>.|
|`unsignedInt`|<xref:System.UInt32>.|
|`unsignedShort`|<xref:System.UInt16>.|
|`unsignedByte`|<xref:System.Byte>.|
|`positiveInteger`|<xref:System.Int64>.|

## <a name="iserializable-types-mapping"></a>Mapowanie typów ISerializable

W .NET Framework w wersji 1,0 <xref:System.Runtime.Serialization.ISerializable> został wprowadzony jako ogólny mechanizm serializacji obiektów w celu zapewnienia trwałości lub transferu danych. Istnieje wiele typów .NET Framework, które implementują `ISerializable` i które mogą być przesyłane między aplikacjami. <xref:System.Runtime.Serialization.DataContractSerializer>naturalnie zapewnia obsługę `ISerializable` klas. `DataContractSerializer` `ISerializable` Typy schematów implementacji mapy, które różnią się tylko nazwą QName (kwalifikowana nazwa) typu i są efektywnymi kolekcjami właściwości. Na przykład `DataContractSerializer` mapuje <xref:System.Exception> do następującego typu XSD w `http://schemas.datacontract.org/2004/07/System` przestrzeni nazw.

```xml
<xs:complexType name="Exception">
 <xs:sequence>
  <xs:any minOccurs="0" maxOccurs="unbounded"
      namespace="##local" processContents="skip"/>
 </xs:sequence>
 <xs:attribute ref="ser:FactoryType"/>
</xs:complexType>
```

Opcjonalny atrybut `ser:FactoryType` zadeklarowany w schemacie serializacji kontraktu danych odwołuje się do klasy fabryki, która może deserializować typ. Klasa fabryki musi być częścią kolekcji znanych typów `DataContractSerializer` używanego wystąpienia. Aby uzyskać więcej informacji na temat znanych typów, zobacz [znane typy kontraktu danych](data-contract-known-types.md).

## <a name="datacontract-serialization-schema"></a>Schemat serializacji schematu DataContract

Szereg schematów wyeksportowanych przez `DataContractSerializer` typy użycia, elementy i atrybuty z obszaru nazw serializacji kontraktu danych:

`http://schemas.microsoft.com/2003/10/Serialization`

Poniżej przedstawiono kompletną deklarację schematu serializacji kontraktu danych.

```xml
<xs:schema attributeFormDefault="qualified"
   elementFormDefault="qualified"
   targetNamespace =
    "http://schemas.microsoft.com/2003/10/Serialization/"
   xmlns:xs="http://www.w3.org/2001/XMLSchema"
   xmlns:tns="http://schemas.microsoft.com/2003/10/Serialization/">

 <!-- Top-level elements for primitive types. -->
 <xs:element name="anyType" nillable="true" type="xs:anyType"/>
 <xs:element name="anyURI" nillable="true" type="xs:anyURI"/>
 <xs:element name="base64Binary"
       nillable="true" type="xs:base64Binary"/>
 <xs:element name="boolean" nillable="true" type="xs:boolean"/>
 <xs:element name="byte" nillable="true" type="xs:byte"/>
 <xs:element name="dateTime" nillable="true" type="xs:dateTime"/>
 <xs:element name="decimal" nillable="true" type="xs:decimal"/>
 <xs:element name="double" nillable="true" type="xs:double"/>
 <xs:element name="float" nillable="true" type="xs:float"/>
 <xs:element name="int" nillable="true" type="xs:int"/>
 <xs:element name="long" nillable="true" type="xs:long"/>
 <xs:element name="QName" nillable="true" type="xs:QName"/>
 <xs:element name="short" nillable="true" type="xs:short"/>
 <xs:element name="string" nillable="true" type="xs:string"/>
 <xs:element name="unsignedByte"
       nillable="true" type="xs:unsignedByte"/>
 <xs:element name="unsignedInt"
       nillable="true" type="xs:unsignedInt"/>
 <xs:element name="unsignedLong"
       nillable="true" type="xs:unsignedLong"/>
 <xs:element name="unsignedShort"
       nillable="true" type="xs:unsignedShort"/>

 <!-- Primitive types introduced for certain .NET simple types. -->
 <xs:element name="char" nillable="true" type="tns:char"/>
 <xs:simpleType name="char">
  <xs:restriction base="xs:int"/>
 </xs:simpleType>

 <!-- xs:duration is restricted to an ordered value space,
    to map to System.TimeSpan -->
 <xs:element name="duration" nillable="true" type="tns:duration"/>
 <xs:simpleType name="duration">
  <xs:restriction base="xs:duration">
   <xs:pattern
     value="\-?P(\d*D)?(T(\d*H)?(\d*M)?(\d*(\.\d*)?S)?)?"/>
   <xs:minInclusive value="-P10675199DT2H48M5.4775808S"/>
   <xs:maxInclusive value="P10675199DT2H48M5.4775807S"/>
  </xs:restriction>
 </xs:simpleType>

 <xs:element name="guid" nillable="true" type="tns:guid"/>
 <xs:simpleType name="guid">
  <xs:restriction base="xs:string">
   <xs:pattern value="[\da-fA-F]{8}-[\da-fA-F]{4}-[\da-fA-F]{4}-[\da-fA-F]{4}-[\da-fA-F]{12}"/>
  </xs:restriction>
 </xs:simpleType>

 <!-- This is used for schemas exported from ISerializable type. -->
 <xs:attribute name="FactoryType" type="xs:QName"/>
</xs:schema>
```

Należy zwrócić uwagę na następujące kwestie:

- `ser:char`jest wprowadzany do reprezentowania znaków Unicode typu <xref:System.Char> .

- `valuespace` `xs:duration` Jest zredukowany do uporządkowanego zestawu, aby można go było zmapować do <xref:System.TimeSpan> .

- `FactoryType`jest używany w schematach wyeksportowanych z typów pochodzących od <xref:System.Runtime.Serialization.ISerializable> .

## <a name="importing-non-datacontract-schemas"></a>Importowanie schematów nienależących do schematu DataContract

`DataContractSerializer``ImportXmlTypes`opcja zezwala na importowanie schematów, które nie są zgodne z `DataContractSerializer` profilem XSD (zobacz <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> Właściwość). Ustawienie tej opcji `true` umożliwia akceptowanie niezgodnych typów schematów i mapowanie ich do następującej implementacji, <xref:System.Xml.Serialization.IXmlSerializable> Zawijanie tablicy z <xref:System.Xml.XmlNode> (tylko nazwa klasy różni się).

```csharp
[GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]
[System.Xml.Serialization.XmlSchemaProviderAttribute("ExportSchema")]
[System.Xml.Serialization.XmlRootAttribute(IsNullable=false)]
public partial class Person : object, IXmlSerializable
{
  private XmlNode[] nodesField;
  private static XmlQualifiedName typeName =
new XmlQualifiedName("Person","http://Microsoft.ServiceModel.Samples");
  public XmlNode[] Nodes
  {
    get {return this.nodesField;}
    set {this.nodesField = value;}
  }
  public void ReadXml(XmlReader reader)
  {
    this.nodesField = XmlSerializableServices.ReadNodes(reader);
  }
  public void WriteXml(XmlWriter writer)
  {
    XmlSerializableServices.WriteNodes(writer, this.Nodes);
  }
  public System.Xml.Schema.XmlSchema GetSchema()
  {
    return null;
  }
  public static XmlQualifiedName ExportSchema(XmlSchemaSet schemas)
  {
    XmlSerializableServices.AddDefaultSchema(schemas, typeName);
    return typeName;
  }
}
```

## <a name="datetimeoffset-serialization"></a>Serializacja DateTimeOffset

<xref:System.DateTimeOffset>Nie jest traktowany jako typ pierwotny. Zamiast tego jest serializowany jako element złożony z dwiema częściami. Pierwsza część reprezentuje datę i godzinę, a druga część reprezentuje przesunięcie od daty i godziny. Przykład serializowanej wartości DateTimeOffset jest przedstawiony w poniższym kodzie.

```xml
<OffSet xmlns:a="http://schemas.datacontract.org/2004/07/System">
  <DateTime i:type="b:dateTime" xmlns=""
    xmlns:b="http://www.w3.org/2001/XMLSchema">2008-08-28T08:00:00
  </DateTime>
  <OffsetMinutes i:type="b:short" xmlns=""
   xmlns:b="http://www.w3.org/2001/XMLSchema">-480
   </OffsetMinutes>
</OffSet>
```

Schemat jest następujący:

```xml
<xs:schema targetNamespace="http://schemas.datacontract.org/2004/07/System">
   <xs:complexType name="DateTimeOffset">
      <xs:sequence minOccurs="1" maxOccurs="1">
         <xs:element name="DateTime" type="xs:dateTime"
         minOccurs="1" maxOccurs="1" />
         <xs:element name="OffsetMinutes" type="xs:short"
         minOccurs="1" maxOccurs="1" />
      </xs:sequence>
   </xs:complexType>
</xs:schema>
```

## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- [Używanie kontraktów danych](using-data-contracts.md)
