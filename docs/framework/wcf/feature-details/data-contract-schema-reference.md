---
title: Odwołanie do schematu kontraktu danych
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts [WCF], schema reference
ms.assetid: 9ebb0ebe-8166-4c93-980a-7c8f1f38f7c0
ms.openlocfilehash: 5eb4caee5c2057e112ed4f5a88f46fa82b1f57cc
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43554696"
---
# <a name="data-contract-schema-reference"></a>Odwołanie do schematu kontraktu danych
W tym temacie opisano podzbioru elementu schematu XML (XSD) używane przez <xref:System.Runtime.Serialization.DataContractSerializer> do opisania wspólnego języka wspólnego (CLR) typy serializacji XML.  
  
## <a name="datacontractserializer-mappings"></a>Mapowania elementu DataContractSerializer  
 `DataContractSerializer` Typy CLR jest mapowany do XSD, gdy metadane są eksportowane z usługi Windows Communication Foundation (WCF) przy użyciu punktu końcowego metadanych lub [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Aby uzyskać więcej informacji, zobacz [serializator kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md).  
  
 `DataContractSerializer` Również mapuje XSD do typów CLR stosowania Svcutil.exe dostępu do sieci Web Services Description Language (WSDL) lub XSD dokumentów i generować kontrakty danych dotyczących usług i klientów.  
  
 Tylko te wystąpienia schematu XML, które są zgodne z wymagania określone w tym dokumencie mogą być mapowane na typy CLR za pomocą funkcji `DataContractSerializer`.  
  
### <a name="support-levels"></a>Poziomy pomocy technicznej  
 `DataContractSerializer` Zawiera następujące poziomy pomocy technicznej dla danej funkcji schematu XML:  
  
-   **Obsługiwane**. Brak jawnego mapowania z tej funkcji CLR typy atrybutów (lub obu tych) przy użyciu `DataContractSerializer`.  
  
-   **Ignorowane**. Funkcja jest dozwolona w schematach importowane przez `DataContractSerializer`, ale nie ma wpływu na generowanie kodu.  
  
-   **Dostęp zabroniony**. `DataContractSerializer` Nie obsługuje importowania schematu za pomocą funkcji. Na przykład Svcutil.exe, podczas uzyskiwania dostępu do WSDL ze schematem, który używa takich funkcji przełączy się <xref:System.Xml.Serialization.XmlSerializer> zamiast tego. Jest to domyślnie.  
  
## <a name="general-information"></a>Informacje ogólne  
  
-   Przestrzeń nazw schematu jest opisany w [schematu XML](https://go.microsoft.com/fwlink/?LinkId=95475). Prefiks "xs" jest używany w tym dokumencie.  
  
-   Wszelkie atrybuty z przestrzeni nazw bez schematu są ignorowane.  
  
-   Wszystkie adnotacje (z wyjątkiem tych opisanych w tym dokumencie) są ignorowane.  
  
### <a name="xsschema-attributes"></a>\<xs:Schema >: atrybuty  
  
|Atrybut|DataContract|  
|---------------|------------------|  
|`attributeFormDefault`|Ignorowane.|  
|`blockDefault`|Ignorowane.|  
|`elementFormDefault`|Musi być kwalifikowany. Wszystkie elementy muszą zakwalifikować się do schematu obsługiwane przez `DataContractSerializer`. Można to osiągnąć przez ustawienie albo xs:schema/@elementFormDefault "kwalifikowany" lub przez ustawienie xs:element/@form pozycji "kwalifikowany" w deklaracji każdego pojedynczego elementu.|  
|`finalDefault`|Ignorowane.|  
|`Id`|Ignorowane.|  
|`targetNamespace`|Obsługiwane i mapowane na przestrzeń nazw kontraktu danych. Jeśli ten atrybut nie jest określony, pustą przestrzeń nazw jest używana. Nie może być zarezerwowaną przestrzenią nazw http://schemas.microsoft.com/2003/10/Serialization/.|  
|`version`|Ignorowane.|  
  
### <a name="xsschema-contents"></a>\<xs:Schema >: zawartość  
  
|Spis treści|Schemat|  
|--------------|------------|  
|`include`|Obsługiwane. `DataContractSerializer` obsługuje xs: obejmują i xs:import. Jednak ogranicza Svcutil.exe następujące `xs:include/@schemaLocation` i `xs:import/@location` odwołuje się podczas ładowania metadanych z pliku lokalnego. Lista plików schematu muszą być przekazywane za pośrednictwem mechanizmu poza pasmem, a nie za pośrednictwem `include` w tym przypadku; `include`dokumentów schematu d są ignorowane.|  
|`redefine`|Jest zabronione. Korzystanie z `xs:redefine` jest zabroniona przez `DataContractSerializer` ze względów bezpieczeństwa: `x:redefine` wymaga `schemaLocation` postępowania. W pewnych okolicznościach Svcutil.exe przy użyciu schematu DataContract ogranicza użycie `schemaLocation`.|  
|`import`|Obsługiwane. `DataContractSerializer` obsługuje `xs:include` i `xs:import`. Jednak ogranicza Svcutil.exe następujące `xs:include/@schemaLocation` i `xs:import/@location` odwołuje się podczas ładowania metadanych z pliku lokalnego. Lista plików schematu muszą być przekazywane za pośrednictwem mechanizmu poza pasmem, a nie za pośrednictwem `include` w tym przypadku; `include`dokumentów schematu d są ignorowane.|  
|`simpleType`|Obsługiwane. Zobacz `xs:simpleType` sekcji.|  
|`complexType`|Obsługiwane, mapy i kontrakty danych. Zobacz `xs:complexType` sekcji.|  
|`group`|Ignorowane. `DataContractSerializer` nie obsługuje użycia `xs:group`, `xs:attributeGroup`, i `xs:attribute`. Deklaracje te są ignorowane jako elementy podrzędne `xs:schema`, ale nie może być przywoływany z poziomu `complexType` lub inne konstrukcje obsługiwane.|  
|`attributeGroup`|Ignorowane. `DataContractSerializer` nie obsługuje użycia `xs:group`, `xs:attributeGroup`, i `xs:attribute`. Deklaracje te są ignorowane jako elementy podrzędne `xs:schema`, ale nie może być przywoływany z poziomu `complexType` lub inne konstrukcje obsługiwane.|  
|`element`|Obsługiwane. Zobacz deklarację elementu globalnego (e).|  
|`attribute`|Ignorowane. `DataContractSerializer` nie obsługuje użycia `xs:group`, `xs:attributeGroup`, i `xs:attribute`. Deklaracje te są ignorowane jako elementy podrzędne `xs:schema`, ale nie może być przywoływany z poziomu `complexType` lub inne konstrukcje obsługiwane.|  
|`notation`|Ignorowane.|  
  
## <a name="complex-types--xscomplextype"></a>Typy złożone — \<xs:complexType >  
  
### <a name="general-information"></a>Informacje ogólne  
 Każdy typ złożony \<xs:complexType > mapuje kontraktu danych.  
  
### <a name="xscomplextype-attributes"></a>\<xs:complexType >: atrybuty  
  
|Atrybut|Schemat|  
|---------------|------------|  
|`abstract`|Musi mieć wartość false (domyślnie).|  
|`block`|Jest zabronione.|  
|`final`|Ignorowane.|  
|`id`|Ignorowane.|  
|`mixed`|Musi mieć wartość false (domyślnie).|  
|`name`|Obsługiwane i mapowane na nazwie kontraktu danych. W przypadku kropki w nazwie, jest podejmowana próba mapowania typu do typu wewnętrznego. Na przykład typ złożony o nazwie `A.B` mapuje do kontraktu danych typu to znaczy wewnętrznego typu o nazwie kontraktu danych `A`, ale tylko wtedy, gdy typ kontraktu takich danych nie istnieje. Możliwe jest więcej niż jeden poziom zagnieżdżenia: na przykład `A.B.C` może być typu wewnętrznego, ale tylko wtedy, gdy `A` i `A.B` zarówno istnieje.|  
  
### <a name="xscomplextype-contents"></a>\<xs:complexType >: zawartość  
  
|Spis treści|Schemat|  
|--------------|------------|  
|`simpleContent`|Rozszerzenia są zabronione.<br /><br /> Ograniczenie jest dozwolone tylko w `anySimpleType`.|  
|`complexContent`|Obsługiwane. Zobacz "Dziedziczenie".|  
|`group`|Jest zabronione.|  
|`all`|Jest zabronione.|  
|`choice`|Dostęp zabroniony|  
|`sequence`|Obsługiwane mapują do elementów członkowskich danych kontraktu danych.|  
|`attribute`|Dostęp zabroniony, nawet w przypadku użycia = "prohibited" (z jednym wyjątkiem). Obsługiwane są tylko opcjonalne atrybuty z przestrzeni nazw standardowego schematu serializacji. Nie są mapowane na elementy członkowskie danych w modelu programowania kontraktu danych. Obecnie tylko jeden taki atrybut ma znaczenie i został opisany w sekcji ISerializable. Wszystkie pozostałe są ignorowane.|  
|`attributeGroup`|Jest zabronione. W wersji v1 usługi WCF `DataContractSerializer` ignoruje obecności `attributeGroup` wewnątrz `xs:complexType`.|  
|`anyAttribute`|Jest zabronione.|  
|(pusty)|Mapuje do kontraktu danych za pomocą żadnych składowych danych.|  
  
### <a name="xssequence-in-a-complex-type-attributes"></a>\<użyto w nim wartości > w typie złożonym: atrybuty  
  
|Atrybut|Schemat|  
|---------------|------------|  
|`id`|Ignorowane.|  
|`maxOccurs`|Musi mieć wartość 1 (ustawienie domyślne).|  
|`minOccurs`|Musi mieć wartość 1 (ustawienie domyślne).|  
  
### <a name="xssequence-in-a-complex-type-contents"></a>\<użyto w nim wartości > w typie złożonym: zawartość  
  
|Spis treści|Schemat|  
|--------------|------------|  
|`element`|Każde wystąpienie jest mapowany na element członkowski danych.|  
|`group`|Jest zabronione.|  
|`choice`|Jest zabronione.|  
|`sequence`|Jest zabronione.|  
|`any`|Jest zabronione.|  
|(pusty)|Mapuje do kontraktu danych za pomocą żadnych składowych danych.|  
  
## <a name="elements--xselement"></a>Elementy — \<elementu xs: element >  
  
### <a name="general-information"></a>Informacje ogólne  
 `<xs:element>` może wystąpić w następujących okolicznościach:  
  
-   Może wystąpić w `<xs:sequence>`, która opisuje element członkowski danych kontraktu regularnych danych (bez kolekcji). W tym przypadku `maxOccurs` atrybut musi mieć wartość 1. (Wartość 0 nie jest dozwolona).  
  
-   Może wystąpić w `<xs:sequence>`, która opisuje składowa danych klasy kontraktu danych kolekcji. W tym przypadku `maxOccurs` atrybut musi być większa niż 1 lub "niepowiązanego".  
  
-   Może wystąpić w `<xs:schema>` jako globalny Element deklaracji (e).  
  
### <a name="xselement-with-maxoccurs1-within-an-xssequence-data-members"></a>\<elementu xs: element > maxOccurs = 1, w ramach \<użyto w nim wartości > (elementy członkowskie danych)  
  
|Atrybut|Schemat|  
|---------------|------------|  
|`ref`|Jest zabronione.|  
|`name`|Obsługiwane, mapy i nazwę elementu członkowskiego danych.|  
|`type`|Obsługiwane, mapy, element członkowski danych jest typu. Aby uzyskać więcej informacji zobacz typ/element mapowania. Jeśli nie określono (i elementu nie zawiera typu anonimowego) `xs:anyType` zakłada, że.|  
|`block`|Ignorowane.|  
|`default`|Jest zabronione.|  
|`fixed`|Jest zabronione.|  
|`form`|Musi być kwalifikowany. Ten atrybut można określać za pośrednictwem `elementFormDefault` na `xs:schema`.|  
|`id`|Ignorowane.|  
|`maxOccurs`|1|  
|`minOccurs`|Mapuje <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> właściwość element członkowski danych (`IsRequired` jest istotne, kiedy `minOccurs` 1).|  
|`nillable`|Mapowanie typu ma wpływ na. Zobacz mapowania typu/podstawowego.|  
  
### <a name="xselement-with-maxoccurs1-within-an-xssequence-collections"></a>\<elementu xs: element > za pomocą elementu maxOccurs > 1 w ramach \<użyto w nim wartości > (kolekcji)  
  
-   Mapuje <xref:System.Runtime.Serialization.CollectionDataContractAttribute>.  
  
-   Typy kolekcji tylko jednego elementu xs: element jest dozwolony w ramach użyto w nim wartości.  
  
 Kolekcje mogą być następujące:  
  
-   Kolekcje regularnie (na przykład, tablice).  
  
-   Kolekcje słownika (mapowanie jedną wartość na inny; na przykład <xref:System.Collections.Hashtable>).  
  
-   Jedyną różnicą między słownik i tablicę typu pary klucz/wartość jest w wygenerowanym modelu programowania. Istnieje mechanizm adnotację schematu, który może służyć do wskazywania danego typu kolekcji słownika.  
  
 Reguły dotyczące `ref`, `block`, `default`, `fixed`, `form`, i `id` atrybuty są takie same jak w przypadku innych kolekcji. Inne atrybuty obejmuje występujące w poniższej tabeli.  
  
|Atrybut|Schemat|  
|---------------|------------|  
|`name`|Obsługiwane, mapy i <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> właściwość `CollectionDataContractAttribute` atrybutu.|  
|`type`|Obsługiwane, mapy do typu, przechowywane w kolekcji.|  
|`maxOccurs`|Większa niż 1 lub "niepowiązanego". Schemat kontrolera domeny, należy użyć "niepowiązanego".|  
|`minOccurs`|Ignorowane.|  
|`nillable`|Mapowanie typu ma wpływ na. Ten atrybut jest ignorowany dla kolekcji słownika.|  
  
### <a name="xselement-within-an-xsschema-global-element-declaration"></a>\<elementu xs: element > w ramach \<xs:schema > deklaracji elementu globalnego  
  
-   Globalny Element deklaracji (Jściowa) jako typ w schemacie, ma taką samą nazwę i przestrzeń nazw lub definiujący typu anonimowego wewnątrz siebie, jest nazywany ma zostać skojarzony z typem.  
  
-   Eksport schematu: GEDs skojarzone są generowane dla każdego wygenerowanego typu proste i złożone.  
  
-   Serializacji/deserializacji: GEDs skojarzone są używane jako elementy główne dla typu.  
  
-   Importowanie schematu: skojarzone GEDs nie są wymagane i są ignorowane, jeśli używają następujących reguł (o ile nie mogą definiować typy).  
  
|Atrybut|Schemat|  
|---------------|------------|  
|`abstract`|Musi mieć wartość false w GEDs skojarzone.|  
|`block`|Dostęp zabroniony w GEDs skojarzone.|  
|`default`|Dostęp zabroniony w GEDs skojarzone.|  
|`final`|Musi mieć wartość false w GEDs skojarzone.|  
|`fixed`|Dostęp zabroniony w GEDs skojarzone.|  
|`id`|Ignorowane.|  
|`name`|Obsługiwane. Zobacz definicję GEDs skojarzone.|  
|`nillable`|Muszą być spełnione GEDs skojarzone.|  
|`substitutionGroup`|Dostęp zabroniony w GEDs skojarzone.|  
|`type`|Obsługiwane i musi odpowiadać typowi skojarzone dla skojarzonego GEDs (chyba że element zawiera typ anonimowy).|  
  
### <a name="xselement-contents"></a>\<elementu xs: element >: zawartość  
  
|Spis treści|Schemat|  
|--------------|------------|  
|`simpleType`|Supported.*|  
|`complexType`|Supported.*|  
|`unique`|Ignorowane.|  
|`key`|Ignorowane.|  
|`keyref`|Ignorowane.|  
|(pusty)|Obsługiwane.|  
  
 \* Korzystając z `simpleType` i `complexType,` mapowania dla typów anonimowych jest tak samo nieanonimowym typów, z tą różnicą, że nie ma żadnych umów anonimowych danych, więc kontrakt danych o podanej nazwie zostanie utworzony, z użyciem nazwy wygenerowanej pochodzi od nazwy elementu. Na poniższej liście są następujące reguły dla typów anonimowych:  
  
-   Szczegóły implementacji usługi WCF: Jeśli `xs:element` nazwa nie zawiera kropek, typu anonimowego mapuje do typu wewnętrznego typu kontraktu danych zewnętrznych. Jeśli nazwa zawiera kropek, wynikowy typ kontraktu danych jest niezależne (nie wewnętrznego typu).  
  
-   Nazwa kontraktu wygenerowane dane typu wewnętrznego jest nazwie kontraktu danych typu zewnętrznego, następnie kropkę i nazwę elementu i ciągu "Type".  
  
-   Jeśli kontraktu danych o takiej nazwie już istnieje, nazwa jest unikatowa, dodając "1", "2", "3", i tak dalej do momentu utworzenia unikatowej nazwy.  
  
## <a name="simple-types---xssimpletype"></a>Typy proste — \<xs:simpleType >  
  
### <a name="xssimpletype-attributes"></a>\<xs:simpleType >: atrybuty  
  
|Atrybut|Schemat|  
|---------------|------------|  
|`final`|Ignorowane.|  
|`id`|Ignorowane.|  
|`name`|Obsługiwane, mapy do danych nazwę kontraktu.|  
  
### <a name="xssimpletype-contents"></a>\<xs:simpleType >: zawartość  
  
|Spis treści|Schemat|  
|--------------|------------|  
|`restriction`|Obsługiwane. Mapuje do wyliczenia kontraktów danych. Ten atrybut jest ignorowany, jeśli nie jest zgodny ze wzorcem wyliczenia. Zobacz `xs:simpleType` sekcji ograniczenia.|  
|`list`|Obsługiwane. Mapuje flagi kontraktów danych wyliczenia. Zobacz `xs:simpleType` Wyświetla sekcji.|  
|`union`|Jest zabronione.|  
  
### <a name="xsrestriction"></a>\<xs:restriction >  
  
-   Ograniczenia typu złożonego są obsługiwane tylko dla podstawowego = "`xs:anyType`".  
  
-   Ograniczenia typu prostego `xs:string` nie mają żadnych ograniczeń aspekty inne niż `xs:enumeration` są mapowane na wyliczenie kontraktów danych.  
  
-   Wszystkie inne ograniczenia typu prostego są mapowane na typy, które ograniczają one. Na przykład ograniczenia `xs:int` mapuje na liczbę całkowitą, podobnie jak `xs:int` sam przeprowadza. Aby uzyskać więcej informacji na temat mapowania typów pierwotnych Zobacz typ/element mapowania.  
  
### <a name="xsrestriction-attributes"></a>\<xs:restriction >: atrybuty  
  
|Atrybut|Schemat|  
|---------------|------------|  
|`base`|Musi być obsługiwanego typu prostego lub `xs:anyType`.|  
|`id`|Ignorowane.|  
  
### <a name="xsrestriction-for-all-other-cases-contents"></a>\<xs:restriction > dla wszystkich innych przypadkach: zawartość  
  
|Spis treści|Schemat|  
|--------------|------------|  
|`simpleType`|Jeśli jest obecna, musi pochodzić od obsługiwanego typu pierwotnego.|  
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
|(pusty)|Obsługiwane.|  
  
## <a name="enumeration"></a>Wyliczenie  
  
### <a name="xsrestriction-for-enumerations-attributes"></a>\<xs:restriction > dla wyliczenia: atrybuty  
  
|Atrybut|Schemat|  
|---------------|------------|  
|`base`|Jeśli jest obecna, musi być `xs:string`.|  
|`id`|Ignorowane.|  
  
### <a name="xsrestriction-for-enumerations-contents"></a>\<xs:restriction > dla wyliczenia: zawartość  
  
|Spis treści|Schemat|  
|--------------|------------|  
|`simpleType`|Jeśli jest obecny, muszą być ograniczenia wyliczenia obsługiwane przez kontraktu danych (w tej sekcji).|  
|`minExclusive`|Ignorowane.|  
|`minInclusive`|Ignorowane.|  
|`maxExclusive`|Ignorowane.|  
|`maxInclusive`|Ignorowane.|  
|`totalDigits`|Ignorowane.|  
|`fractionDigits`|Ignorowane.|  
|`length`|Jest zabronione.|  
|`minLength`|Jest zabronione.|  
|`maxLength`|Jest zabronione.|  
|`enumeration`|Obsługiwane. Wyliczenie "id" jest ignorowana, a "value" mapowany na nazwę wartości wyliczenia umowy danych.|  
|`whiteSpace`|Jest zabronione.|  
|`pattern`|Jest zabronione.|  
|(pusty)|Obsługiwane, mapy do typu puste wyliczenie.|  
  
 Poniższy kod przedstawia klasy wyliczenie C#.  
  
```  
public enum MyEnum  
{  
   first = 3,  
   second = 4,  
   third =5  
```  
  
 }  
  
 Ta klasa jest mapowany na poniższe schemat, `DataContractSerializer`. Jeśli wartości wyliczenia, zacznij od 1, `xs:annotation` bloki nie są generowane.  
  
```xml  
<xs:simpleType name="MyEnum">  
<xs:restriction base="xs:string">  
 <xs:enumeration value="first">  
  <xs:annotation>  
   <xs:appinfo>  
    <EnumerationValue   
     xmlns="http://schemas.microsoft.com/2003/10/Serialization/">  
     3  
    </EnumerationValue>  
   </xs:appinfo>  
  </xs:annotation>  
 </xs:enumeration>  
 <xs:enumeration value="second">  
  <xs:annotation>  
   <xs:appinfo>  
    <EnumerationValue   
     xmlns="http://schemas.microsoft.com/2003/10/Serialization/">  
     4  
    </EnumerationValue>  
   </xs:appinfo>  
  </xs:annotation>  
 </xs:enumeration>  
</xs:restriction>  
</xs:simpleType>  
```  
  
### <a name="xslist"></a>\<xs:list>  
 `DataContractSerializer` Typy wyliczeniowe mapy, oznaczone `System.FlagsAttribute` do `xs:list` pochodną `xs:string`. Żadne inne `xs:list` różnice są obsługiwane.  
  
### <a name="xslist-attributes"></a>\<xs:list >: atrybuty  
  
|Atrybut|Schemat|  
|---------------|------------|  
|`itemType`|Jest zabronione.|  
|`id`|Ignorowane.|  
  
### <a name="xslist-contents"></a>\<xs:list >: zawartość  
  
|Spis treści|Schemat|  
|--------------|------------|  
|`simpleType`|Musi być ograniczenie `xs:string` przy użyciu `xs:enumeration` zestawu reguł.|  
  
 Jeśli wartość wyliczenia nie jest zgodna z potęgą liczby 2 postępu (wartość domyślna dla flag), wartość jest przechowywana w `xs:annotation/xs:appInfo/ser:EnumerationValue` elementu.  
  
 Na przykład poniższy kod flagi typem wyliczenia.  
  
```  
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
  
 Ten typ jest mapowany na zgodny z następującym schematem.  
  
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
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Se  
rialization/">16</EnumerationValue>  
              </xs:appinfo>  
            </xs:annotation>  
          </xs:enumeration>  
          <xs:enumeration value="AuthWindowsLiveID">  
            <xs:annotation>  
              <xs:appinfo>  
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Se  
rialization/">64</EnumerationValue>  
              </xs:appinfo>  
            </xs:annotation>  
          </xs:enumeration>  
        </xs:restriction>  
      </xs:simpleType>  
    </xs:list>  
  </xs:simpleType>  
```  
  
## <a name="inheritance"></a>Dziedziczenie  
  
### <a name="general-rules"></a>Ogólne zasady  
 Kontrakt danych może dziedziczyć z innego kontraktu danych. Takie kontraktów danych mapy podstawowy i są uzyskiwane przez typy rozszerzeń przy użyciu `<xs:extension>` konstrukcji schematu XML.  
  
 Kontrakt danych nie może dziedziczyć z kontraktu danych kolekcji.  
  
 Na przykład poniższy kod jest kontraktu danych.  
  
```  
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
  
 Ten kontrakt danych mapuje następującą deklarację typu schematu XML.  
  
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
  
### <a name="xscomplexcontent-attributes"></a>\<xs:complexContent >: atrybuty  
  
|Atrybut|Schemat|  
|---------------|------------|  
|`id`|Ignorowane.|  
|`mixed`|Musi mieć wartość false.|  
  
### <a name="xscomplexcontent-contents"></a>\<xs:complexContent >: zawartość  
  
|Spis treści|Schemat|  
|--------------|------------|  
|`restriction`|Dostęp zabroniony, z wyjątkiem sytuacji, podstawowy = "`xs:anyType`". Jest odpowiednikiem umieszczenie zawartość `xs:restriction` bezpośrednio w kontenerze `xs:complexContent`.|  
|`extension`|Obsługiwane. Mapy i dziedziczenie kontraktów danych.|  
  
### <a name="xsextension-in-xscomplexcontent-attributes"></a>\<xs:Extension > w \<xs:complexContent >: atrybuty  
  
|Atrybut|Schemat|  
|---------------|------------|  
|`id`|Ignorowane.|  
|`base`|Obsługiwane. Mapuje do kontraktu danych podstawowych typu, że ten typ dziedziczy z.|  
  
### <a name="xsextension-in-xscomplexcontent-contents"></a>\<xs:Extension > w \<xs:complexContent >: zawartość  
 Zasady są takie same jak w przypadku `<xs:complexType>` zawartość.  
  
 Jeśli `<xs:sequence>` podano członków elementy mapy członkom dodatkowe dane, które znajdują się w kontrakcie pochodnego danych.  
  
 Jeśli typ pochodny zawiera element o takiej samej nazwie jako element w typie podstawowym, deklaracja zduplikowany element mapuje element członkowski danych o nazwie, który jest generowany, aby była unikatowa. Dodatnia liczba całkowita liczby są dodawane do nazwy elementu członkowskiego danych ("Członek1", "członek2" itd.) aż do znalezienia unikatową nazwę. Z drugiej strony:  
  
-   Gdy kontrakt danych pochodnych ma element członkowski danych o tej samej nazwie i typie jako element członkowski danych w kontrakt danych podstawowych `DataContractSerializer` generuje ten odpowiadający mu element w typie pochodnym.  
  
-   Jeśli element członkowski danych o takiej samej nazwie jak element członkowski danych w kontraktu danych podstawowych, ale jest innego typu kontraktu danych pochodnych `DataContractSerializer` Importuje schemat z elementem typu `xs:anyType` zarówno w typie podstawowym, jak i w deklaracji typu pochodnego. Oryginalna nazwa typu jest zachowywana w `xs:annotations/xs:appInfo/ser:ActualType/@Name`.  
  
 Obu wariantów może prowadzić do schematu o niejednoznaczne modelu zawartości, który zależy od kolejności elementów członkowskich odpowiednich danych.  
  
## <a name="typeprimitive-mapping"></a>Mapowania typ/element  
 `DataContractSerializer` Używa następującego mapowania dla typów pierwotnych schematu XML.  
  
|Typ XSD|Typ architektury .NET|  
|--------------|---------------|  
|`anyType`|<xref:System.Object>.|  
|`anySimpleType`|<xref:System.String>.|  
|`duration`|<xref:System.TimeSpan>.|  
|`dateTime`|<xref:System.DateTime>.|  
|`dateTimeOffset`|<xref:System.DateTime> i <xref:System.TimeSpan> przesunięcia. Zobacz poniższe serializacji DateTimeOffset.|  
|`time`|<xref:System.String>.|  
|`date`|<xref:System.String>.|  
|`gYearMonth`|<xref:System.String>.|  
|`gYear`|<xref:System.String>.|  
|`gMonthDay`|<xref:System.String>.|  
|`gDay`|<xref:System.String>.|  
|`gMonth`|<xref:System.String>.|  
|`boolean`|<xref:System.Boolean>|  
|`base64Binary`|<xref:System.Byte> Tablica.|  
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
  
## <a name="iserializable-types-mapping"></a>Mapowanie typów iSerializable  
 W [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] w wersji 1.0 `ISerializable` została wprowadzona jako mechanizm ogólnego do wykonywania serializacji obiektów dla trwałości lub transfer danych. Istnieje wiele [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typami, które implementują `ISerializable` i mogą być przekazywane między aplikacjami. `DataContractSerializer` naturalnie zapewnia obsługę `ISerializable` klasy. `DataContractSerializer` Mapuje `ISerializable` typów schematu implementacji różnią się jedynie QName (kwalifikowana nazwa) tego typu, które są faktycznymi kolekcji właściwości. Na przykład `DataContractSerializer` mapuje <xref:System.Exception> następujący typ XSD w http://schemas.datacontract.org/2004/07/System przestrzeni nazw.  
  
```xml  
<xs:complexType name="Exception">  
 <xs:sequence>  
  <xs:any minOccurs="0" maxOccurs="unbounded"   
      namespace="##local" processContents="skip"/>  
 </xs:sequence>  
 <xs:attribute ref="ser:FactoryType"/>  
</xs:complexType>  
```  
  
 Opcjonalny atrybut `ser:FactoryType` zadeklarowanych w danych serializacji umowy schematu odwołuje się do klasy fabryki, które może wykonywać deserializację typu. Klasa fabryki musi należeć do kolekcji znanych typów `DataContractSerializer` wystąpienia używane. Aby uzyskać więcej informacji na temat znanych typów, zobacz [znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
## <a name="datacontract-serialization-schema"></a>DataContract schematu serializacji  
 Liczba schematów wyeksportowany przez `DataContractSerializer` typy, elementy i atrybuty z przestrzeni nazw specjalnych serializacji kontrakt danych:  
  
 http://schemas.microsoft.com/2003/10/Serialization  
  
 Poniżej przedstawiono pełną deklarację schematu serializacji kontrakt danych.  
  
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
  
 Należy można zauważyć następujące czynności:  
  
-   `ser:char` został wprowadzony do reprezentowania znaków Unicode typu <xref:System.Char>.  
  
-   `valuespace` z `xs:duration` jest ograniczona do uporządkowany zestaw, dzięki czemu mogą być mapowane na <xref:System.TimeSpan>.  
  
-   `FactoryType` jest używany w schematach wyeksportowane z typów, które są uzyskiwane z <xref:System.Runtime.Serialization.ISerializable>.  
  
## <a name="importing-non-datacontract-schemas"></a>Importowanie schematów innych niż typ  
 `DataContractSerializer` ma `ImportXmlTypes` opcję, aby umożliwić Importowanie schematów, które nie są zgodne z `DataContractSerializer` profilu XSD (zobacz <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> właściwości). Ustawienie tej opcji na `true` umożliwia przyjmowanie niezgodnych typów schematu i mapowania ich na następującą implementacją <xref:System.Xml.Serialization.IXmlSerializable> zawijania tablicę <xref:System.Xml.XmlNode> (różni się tylko nazwę klasy).  
  
```  
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
 <xref:System.DateTimeOffset> Nie jest traktowana jako typu podstawowego. Zamiast tego jest serializowana jako element złożonych z dwóch części. Pierwsza część reprezentuje daty, godziny, a druga sekcja przedstawia przesunięcie od czasu daty. W poniższym kodzie przedstawiono przykładowy serializowanej wartości DateTimeOffset.  
  
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
  
 Schemat jest w następujący sposób.  
  
```xml  
<xs:schema targetNamespace="http://schemas.datacontract.org/2004/07/System">  
   <xs:complexType name="DateTimeOffset">  
      <xs:sequence minOccurs="1" maxOccurs="1">  
         <xs:element name="DateTime" type="xs:dateTime"  
         minOccurs="1" maxOccurs="1" />  
         <xs:elementname="OffsetMinutes" type="xs:short"  
         minOccurs="1" maxOccurs="1" />  
      </xs:sequence>  
   </xs:complexType>  
</xs:schema>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 <xref:System.Runtime.Serialization.XsdDataContractImporter>  
 [Używanie kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
