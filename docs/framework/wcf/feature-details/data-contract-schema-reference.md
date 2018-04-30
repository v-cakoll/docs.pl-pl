---
title: Odwołanie do schematu kontraktu danych
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data contracts [WCF], schema reference
ms.assetid: 9ebb0ebe-8166-4c93-980a-7c8f1f38f7c0
caps.latest.revision: 24
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 075f8d89caccd7723f3a1dc54fde695a8fb624ab
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="data-contract-schema-reference"></a>Odwołanie do schematu kontraktu danych
W tym temacie opisano podzestawu elementu schematu XML (XSD) używany przez <xref:System.Runtime.Serialization.DataContractSerializer> do opisywania wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) typy serializacji XML.  
  
## <a name="datacontractserializer-mappings"></a>Mapowania DataContractSerializer  
 `DataContractSerializer` Typy CLR jest mapowany na XSD, gdy metadane są eksportowane z [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi przy użyciu punktu końcowego metadanych lub [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Aby uzyskać więcej informacji, zobacz [serializator kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md).  
  
 `DataContractSerializer` Również mapuje XSD do typów CLR stosowania Svcutil.exe dostępu do sieci Web Services Description Language (WSDL) lub XSD dokumentów i generowanie kontraktów danych dotyczących usług i klientów.  
  
 Schematu XML tylko te wystąpienia, które odpowiadają wymagania określone w tym dokumencie mogą być mapowane na typy CLR za pomocą funkcji `DataContractSerializer`.  
  
### <a name="support-levels"></a>Poziomach pomocy technicznej  
 `DataContractSerializer` Zawiera następujące poziomy wsparcia dla danej funkcji schematu XML:  
  
-   **Obsługiwane**. Istnieje jawne mapowanie z tej funkcji CLR typy atrybutów (i/lub) przy użyciu `DataContractSerializer`.  
  
-   **Ignorowane**. Funkcja jest dozwolona w schematach zaimportowanej przez `DataContractSerializer`, ale nie ma wpływu na generowanie kodu.  
  
-   **Dostęp zabroniony**. `DataContractSerializer` Nie obsługuje importowania schematu za pomocą funkcji. Na przykład Svcutil.exe, podczas uzyskiwania dostępu do WSDL ze schematem, który korzysta z takich funkcji przełączy się <xref:System.Xml.Serialization.XmlSerializer> zamiast tego. Jest to domyślnie.  
  
## <a name="general-information"></a>Informacje ogólne  
  
-   Przestrzeń nazw schematu jest w sposób opisany w [schematu XML](http://go.microsoft.com/fwlink/?LinkId=95475). Prefiks "xs" jest używany w tym dokumencie.  
  
-   Atrybuty z przestrzeni nazw z systemem innym niż schematu są ignorowane.  
  
-   Adnotacji (z wyjątkiem opisane w tym dokumencie) są ignorowane.  
  
### <a name="xsschema-attributes"></a>\<xs:Schema >: atrybuty  
  
|Atrybut|DataContract|  
|---------------|------------------|  
|`attributeFormDefault`|Ignorowane.|  
|`blockDefault`|Ignorowane.|  
|`elementFormDefault`|Musi być kwalifikowany. Wszystkie elementy musi być kwalifikowana dla schematu obsługiwany przez `DataContractSerializer`. Można to zrobić przez dowolnego z tych ustawień xs:schema/@elementFormDefault "kwalifikowana" lub przez ustawienie xs:element/@form do "kwalifikowana" dla każdej deklaracji pojedynczy element.|  
|`finalDefault`|Ignorowane.|  
|`Id`|Ignorowane.|  
|`targetNamespace`|Obsługiwane i mapowany na przestrzeń nazw kontraktu danych. Jeśli ten atrybut nie jest określony, używana jest pusta przestrzeń nazw. Nie może być zarezerwowaną przestrzenią nazw http://schemas.microsoft.com/2003/10/Serialization/.|  
|`version`|Ignorowane.|  
  
### <a name="xsschema-contents"></a>\<xs:Schema >: zawartość  
  
|Spis treści|Schemat|  
|--------------|------------|  
|`include`|Obsługiwane. `DataContractSerializer` obsługuje xs: obejmują i xs:import. Jednak ogranicza Svcutil.exe następujące `xs:include/@schemaLocation` i `xs:import/@location` odwołuje się po załadowaniu metadanych z pliku lokalnego. Lista plików schematów muszą być przekazywane za pośrednictwem mechanizmu poza pasmem, a nie za pomocą `include` w takim przypadku; `include`d schematu dokumentów są ignorowane.|  
|`redefine`|Dostęp jest zabroniony. Korzystanie z `xs:redefine` jest zabronione przez `DataContractSerializer` ze względów bezpieczeństwa: `x:redefine` wymaga `schemaLocation` postępowania. W pewnych okolicznościach Svcutil.exe przy użyciu obiektu DataContract ogranicza użycie `schemaLocation`.|  
|`import`|Obsługiwane. `DataContractSerializer` obsługuje `xs:include` i `xs:import`. Jednak ogranicza Svcutil.exe następujące `xs:include/@schemaLocation` i `xs:import/@location` odwołuje się po załadowaniu metadanych z pliku lokalnego. Lista plików schematów muszą być przekazywane za pośrednictwem mechanizmu poza pasmem, a nie za pomocą `include` w takim przypadku; `include`d schematu dokumentów są ignorowane.|  
|`simpleType`|Obsługiwane. Zobacz `xs:simpleType` sekcji.|  
|`complexType`|Obsługiwane, map do kontraktów danych. Zobacz `xs:complexType` sekcji.|  
|`group`|Ignorowane. `DataContractSerializer` nie obsługuje użycia `xs:group`, `xs:attributeGroup`, i `xs:attribute`. Deklaracje te są ignorowane jako elementy podrzędne `xs:schema`, ale nie można odwoływać się za pomocą `complexType` lub inne konstrukcje obsługiwane.|  
|`attributeGroup`|Ignorowane. `DataContractSerializer` nie obsługuje użycia `xs:group`, `xs:attributeGroup`, i `xs:attribute`. Deklaracje te są ignorowane jako elementy podrzędne `xs:schema`, ale nie można odwoływać się za pomocą `complexType` lub inne konstrukcje obsługiwane.|  
|`element`|Obsługiwane. Zobacz Element globalny deklaracji (e).|  
|`attribute`|Ignorowane. `DataContractSerializer` nie obsługuje użycia `xs:group`, `xs:attributeGroup`, i `xs:attribute`. Deklaracje te są ignorowane jako elementy podrzędne `xs:schema`, ale nie można odwoływać się za pomocą `complexType` lub inne konstrukcje obsługiwane.|  
|`notation`|Ignorowane.|  
  
## <a name="complex-types--xscomplextype"></a>Typy złożone — \<xs:complexType >  
  
### <a name="general-information"></a>Informacje ogólne  
 Każdy typ złożony \<xs:complexType > mapuje kontraktu danych.  
  
### <a name="xscomplextype-attributes"></a>\<xs:complexType >: atrybuty  
  
|Atrybut|Schemat|  
|---------------|------------|  
|`abstract`|Musi mieć wartość FAŁSZ (ustawienie domyślne).|  
|`block`|Dostęp jest zabroniony.|  
|`final`|Ignorowane.|  
|`id`|Ignorowane.|  
|`mixed`|Musi mieć wartość FAŁSZ (ustawienie domyślne).|  
|`name`|Obsługiwane i zamapowany na nazwę kontraktu danych. Jeśli istnieją kropki w nazwie, podejmowana jest próba mapowania typu na typ wewnętrzny. Na przykład typu złożonego o nazwie `A.B` map do kontraktu danych typ wewnętrzny typ typu o nazwie kontraktu danych `A`, ale tylko wtedy, gdy typ kontraktu tych danych istnieje. Możliwe jest więcej niż jeden poziom zagnieżdżenia: na przykład `A.B.C` może być typu wewnętrznego, ale tylko wtedy, gdy `A` i `A.B` istnieją.|  
  
### <a name="xscomplextype-contents"></a>\<xs:complexType >: zawartość  
  
|Spis treści|Schemat|  
|--------------|------------|  
|`simpleContent`|Rozszerzenia są zabronione.<br /><br /> Ograniczenie jest dozwolone tylko w `anySimpleType`.|  
|`complexContent`|Obsługiwane. Zobacz "Dziedziczenia".|  
|`group`|Dostęp jest zabroniony.|  
|`all`|Dostęp jest zabroniony.|  
|`choice`|Dostęp zabroniony|  
|`sequence`|Obsługiwane, mapy do elementów członkowskich danych kontraktu danych.|  
|`attribute`|Dostęp jest zabroniony, nawet jeśli Użyj = "prohibited" (z wyjątkiem jednego). Obsługiwane są tylko opcjonalne atrybuty z przestrzeni nazw standardowe schematu serializacji. Nie są mapowane na elementy członkowskie danych w modelu programowania kontraktu danych. Obecnie tylko jeden taki atrybut ma znaczenie i została szczegółowo opisana w sekcji ISerializable. Wszystkie pozostałe są ignorowane.|  
|`attributeGroup`|Dostęp jest zabroniony. W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wersji v1 `DataContractSerializer` ignoruje obecności `attributeGroup` wewnątrz `xs:complexType`.|  
|`anyAttribute`|Dostęp jest zabroniony.|  
|(pusta)|Mapowany do kontraktu danych z żadnych elementów członkowskich danych.|  
  
### <a name="xssequence-in-a-complex-type-attributes"></a>\<użyto > w typie złożonym: atrybuty  
  
|Atrybut|Schemat|  
|---------------|------------|  
|`id`|Ignorowane.|  
|`maxOccurs`|Musi mieć wartość 1 (ustawienie domyślne).|  
|`minOccurs`|Musi mieć wartość 1 (ustawienie domyślne).|  
  
### <a name="xssequence-in-a-complex-type-contents"></a>\<użyto > w typie złożonym: zawartość  
  
|Spis treści|Schemat|  
|--------------|------------|  
|`element`|Każde wystąpienie mapuje do elementu członkowskiego danych.|  
|`group`|Dostęp jest zabroniony.|  
|`choice`|Dostęp jest zabroniony.|  
|`sequence`|Dostęp jest zabroniony.|  
|`any`|Dostęp jest zabroniony.|  
|(pusta)|Mapowany do kontraktu danych z żadnych elementów członkowskich danych.|  
  
## <a name="elements--xselement"></a>Elementy — \<elementu xs: element >  
  
### <a name="general-information"></a>Informacje ogólne  
 `<xs:element>` może wystąpić w następujących sytuacjach:  
  
-   Może wystąpić w `<xs:sequence>`, która opisuje element członkowski danych klasy kontraktu regularnych danych (z systemem innym niż kolekcji). W takim przypadku `maxOccurs` atrybutu musi być równa 1. (Wartość 0 nie jest dozwolona).  
  
-   Może wystąpić w `<xs:sequence>`, która opisuje element członkowski danych klasy kontraktu danych kolekcji. W takim przypadku `maxOccurs` atrybutu musi być większa niż 1 lub "unbounded".  
  
-   Może wystąpić w `<xs:schema>` jako globalny Element deklaracji (e).  
  
### <a name="xselement-with-maxoccurs1-within-an-xssequence-data-members"></a>\<elementu xs: element > maxOccurs = 1 w \<użyto > (elementy członkowskie danych)  
  
|Atrybut|Schemat|  
|---------------|------------|  
|`ref`|Dostęp jest zabroniony.|  
|`name`|Obsługiwane mapowana na nazwę elementu członkowskiego danych.|  
|`type`|Obsługiwane, typu map do elementu członkowskiego danych. Aby uzyskać więcej informacji zobacz Mapowanie typu/typów pierwotnych. Jeśli nie określono (i element nie zawiera typu anonimowego) `xs:anyType` zakłada, że.|  
|`block`|Ignorowane.|  
|`default`|Dostęp jest zabroniony.|  
|`fixed`|Dostęp jest zabroniony.|  
|`form`|Musi być kwalifikowany. Ten atrybut można określać za pośrednictwem `elementFormDefault` na `xs:schema`.|  
|`id`|Ignorowane.|  
|`maxOccurs`|1|  
|`minOccurs`|Mapuje <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> właściwości elementu członkowskiego danych (`IsRequired` ma wartość true, gdy `minOccurs` 1).|  
|`nillable`|Mapowanie typu wpływ. Zobacz Mapowanie typu/typów pierwotnych.|  
  
### <a name="xselement-with-maxoccurs1-within-an-xssequence-collections"></a>\<elementu xs: element > z maxOccurs > 1 \<użyto > (kolekcji)  
  
-   Mapuje <xref:System.Runtime.Serialization.CollectionDataContractAttribute>.  
  
-   Typy kolekcji tylko jednego elementu xs: element jest dozwolone w ramach użyto.  
  
 Kolekcje mogą być następujące:  
  
-   Kolekcje regularne (na przykład tablice).  
  
-   Kolekcje słownika (mapowanie jeden wartość; na przykład <xref:System.Collections.Hashtable>).  
  
-   Jedyną różnicą między słownika i tablicy typu pary klucz wartość znajduje się w wygenerowanym modelu programowania. Istnieje mechanizm adnotacji schemat, który może służyć do wskazywania danego typu kolekcji słownika.  
  
 Zasady `ref`, `block`, `default`, `fixed`, `form`, i `id` atrybuty są takie same jak w przypadku — do kolekcji. Inne atrybuty zawiera w poniższej tabeli.  
  
|Atrybut|Schemat|  
|---------------|------------|  
|`name`|Obsługiwane map do <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> właściwości w `CollectionDataContractAttribute` atrybutu.|  
|`type`|Obsługiwane mapowana na typie przechowywane w kolekcji.|  
|`maxOccurs`|Większa niż 1 lub "unbounded". Schemat kontrolera domeny, należy użyć "unbounded".|  
|`minOccurs`|Ignorowane.|  
|`nillable`|Mapowanie typu wpływ. Ten atrybut jest ignorowany dla kolekcji słownika.|  
  
### <a name="xselement-within-an-xsschema-global-element-declaration"></a>\<elementu xs: element > w \<xs:schema > globalne deklarację elementu  
  
-   Globalny Element deklaracji (e) jako typu w schemacie, który ma taką samą nazwę i przestrzeń nazw lub definiujący typu anonimowego wewnątrz, jest określany jako skojarzone z typem.  
  
-   Eksportowania schematu: GEDs skojarzone są generowane dla każdego typu wygenerowanego, zarówno proste i złożone.  
  
-   Serializacji/deserializacji: GEDs skojarzone są używane jako elementy główne dla typu.  
  
-   Importowanie schematu: skojarzony GEDs nie są wymagane i są ignorowane, jeśli następujące reguły są zgodne (chyba że są one Definiowanie typów).  
  
|Atrybut|Schemat|  
|---------------|------------|  
|`abstract`|Musi mieć wartość false dla GEDs skojarzone.|  
|`block`|Jest zabronione w GEDs skojarzone.|  
|`default`|Jest zabronione w GEDs skojarzone.|  
|`final`|Musi mieć wartość false dla GEDs skojarzone.|  
|`fixed`|Jest zabronione w GEDs skojarzone.|  
|`id`|Ignorowane.|  
|`name`|Obsługiwane. Patrz definicja GEDs skojarzone.|  
|`nillable`|Musi mieć wartość true dla GEDs skojarzone.|  
|`substitutionGroup`|Jest zabronione w GEDs skojarzone.|  
|`type`|Obsługiwane i musi odpowiadać typowi skojarzone dla skojarzonego GEDs (chyba, że element zawiera typu anonimowego).|  
  
### <a name="xselement-contents"></a>\<elementu xs: element >: zawartość  
  
|Spis treści|Schemat|  
|--------------|------------|  
|`simpleType`|Supported.*|  
|`complexType`|Supported.*|  
|`unique`|Ignorowane.|  
|`key`|Ignorowane.|  
|`keyref`|Ignorowane.|  
|(pusty)|Obsługiwane.|  
  
 \* Korzystając z `simpleType` i `complexType,` mapowania typów anonimowych są takie same jak typy nieanonimowych z tą różnicą, że nie istnieje żaden kontrakt anonimowe dane, w związku z czym kontrakt danych o podanej nazwie jest tworzony z nazwą wygenerowanego pochodzi od nazwy elementu. Zasady dla typów anonimowych są na poniższej liście:  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Szczegóły implementacji: Jeśli `xs:element` nazwa nie zawiera okresów, mapy typu anonimowego na wewnętrzny typ typu kontraktu danych zewnętrznych. Jeśli nazwa zawiera okresów, wynikowy typ kontraktu danych jest niezależna (nie wewnętrzny typ).  
  
-   Nazwa kontraktu danych wygenerowanych wewnętrzny typu jest nazwą kontraktu danych typu zewnętrznego, a następnie kropką, nazwę elementu i ciągu "Type".  
  
-   Kontraktu danych o takiej nazwie już istnieje, nazwa ma zostać unikatowy przez dołączenie "1", "2", "3", i tak dalej do momentu utworzenia unikatowej nazwy.  
  
## <a name="simple-types---xssimpletype"></a>Proste typy - \<xs:simpleType >  
  
### <a name="xssimpletype-attributes"></a>\<xs:simpleType >: atrybuty  
  
|Atrybut|Schemat|  
|---------------|------------|  
|`final`|Ignorowane.|  
|`id`|Ignorowane.|  
|`name`|Obsługiwane, mapy danych nazwę kontraktu.|  
  
### <a name="xssimpletype-contents"></a>\<xs:simpleType >: zawartość  
  
|Spis treści|Schemat|  
|--------------|------------|  
|`restriction`|Obsługiwane. Mapowany do kontraktów danych wyliczenia. Ten atrybut jest ignorowana, jeśli nie jest zgodny ze wzorcem wyliczenia. Zobacz `xs:simpleType` sekcji ograniczenia.|  
|`list`|Obsługiwane. Mapuje Flaga kontraktów danych wyliczenia. Zobacz `xs:simpleType` wymieniono sekcji.|  
|`union`|Dostęp jest zabroniony.|  
  
### <a name="xsrestriction"></a>\<xs:restriction >  
  
-   Ograniczenia typu złożonego są obsługiwane tylko dla podstawy = "`xs:anyType`".  
  
-   Ograniczenia typu prostego `xs:string` nie mają żadnych ograniczeń aspekty inne niż `xs:enumeration` są mapowane na wyliczenie kontraktów danych.  
  
-   Wszystkie inne ograniczenia typu prostego są mapowane na typy, które ograniczają one. Na przykład ograniczenia `xs:int` mapowana na liczbę całkowitą, podobnie jak `xs:int` sam przeprowadza. Aby uzyskać więcej informacji o mapowaniu typu pierwotnego Zobacz Mapowanie typu/typów pierwotnych.  
  
### <a name="xsrestriction-attributes"></a>\<xs:restriction >: atrybuty  
  
|Atrybut|Schemat|  
|---------------|------------|  
|`base`|Musi być typem prostym obsługiwanych lub `xs:anyType`.|  
|`id`|Ignorowane.|  
  
### <a name="xsrestriction-for-all-other-cases-contents"></a>\<xs:restriction > dla wszystkich innych przypadkach: zawartość  
  
|Spis treści|Schemat|  
|--------------|------------|  
|`simpleType`|Jeśli jest obecny, musi pochodzić z nieobsługiwanym typem pierwotnym.|  
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
|`base`|Jeśli jest obecny, musi być `xs:string`.|  
|`id`|Ignorowane.|  
  
### <a name="xsrestriction-for-enumerations-contents"></a>\<xs:restriction > dla wyliczenia: zawartość  
  
|Spis treści|Schemat|  
|--------------|------------|  
|`simpleType`|Jeśli jest obecny, musi być ograniczenia wyliczenia obsługiwana przez kontrakt danych (w tej sekcji).|  
|`minExclusive`|Ignorowane.|  
|`minInclusive`|Ignorowane.|  
|`maxExclusive`|Ignorowane.|  
|`maxInclusive`|Ignorowane.|  
|`totalDigits`|Ignorowane.|  
|`fractionDigits`|Ignorowane.|  
|`length`|Dostęp jest zabroniony.|  
|`minLength`|Dostęp jest zabroniony.|  
|`maxLength`|Dostęp jest zabroniony.|  
|`enumeration`|Obsługiwane. Wyliczenie "id" zostanie zignorowany, a "wartość" mapuje nazwę wartości wyliczenia umowy danych.|  
|`whiteSpace`|Dostęp jest zabroniony.|  
|`pattern`|Dostęp jest zabroniony.|  
|(pusta)|Obsługiwane, mapy na typ wyliczeniowy puste.|  
  
 Poniższy kod przedstawia klasy wyliczenie C#.  
  
```  
public enum MyEnum  
{  
   first = 3,  
   second = 4,  
   third =5  
```  
  
 }  
  
 Ta klasa mapuje następującego schematu przez `DataContractSerializer`. Jeśli wartości wyliczenia można uruchomić z zakresu od 1, `xs:annotation` bloków nie zostały wygenerowane.  
  
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
 `DataContractSerializer` Typy wyliczeniowe mapy oznaczonych `System.FlagsAttribute` do `xs:list` pochodną `xs:string`. Żaden inny `xs:list` zmian są obsługiwane.  
  
### <a name="xslist-attributes"></a>\<xs:list >: atrybuty  
  
|Atrybut|Schemat|  
|---------------|------------|  
|`itemType`|Dostęp jest zabroniony.|  
|`id`|Ignorowane.|  
  
### <a name="xslist-contents"></a>\<xs:list >: zawartość  
  
|Spis treści|Schemat|  
|--------------|------------|  
|`simpleType`|Musi być ograniczenia z `xs:string` przy użyciu `xs:enumeration` zestawu reguł.|  
  
 Jeśli wartość wyliczenia nie jest zgodna z potęgą liczby 2 postępu (domyślnie flagi), wartość jest przechowywana w `xs:annotation/xs:appInfo/ser:EnumerationValue` elementu.  
  
 Na przykład następujący kod flagi typem wyliczenia.  
  
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
  
 Ten typ jest mapowany na następującego schematu.  
  
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
 Kontrakt danych może dziedziczyć z innego kontraktu danych. Takie kontraktów danych mapowania do podstawowej i są uzyskiwane przez typy rozszerzeń przy użyciu `<xs:extension>` konstrukcja schematu XML.  
  
 Kontrakt danych nie może dziedziczyć kontraktu danych kolekcji.  
  
 Na przykład następujący kod jest kontraktu danych.  
  
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
  
 Mapuje tego kontraktu danych do następujących deklaracji typu schematu XML.  
  
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
|`restriction`|Dostęp jest zabroniony, o ile podstawowy = "`xs:anyType`". Nie jest odpowiednikiem umieszczenie zawartość `xs:restriction` bezpośrednio w kontenerze `xs:complexContent`.|  
|`extension`|Obsługiwane. Mapowany do Dziedziczenie kontraktów danych.|  
  
### <a name="xsextension-in-xscomplexcontent-attributes"></a>\<xs:Extension > w \<xs:complexContent >: atrybuty  
  
|Atrybut|Schemat|  
|---------------|------------|  
|`id`|Ignorowane.|  
|`base`|Obsługiwane. Typu map do kontraktu danych podstawowych, że ten typ dziedziczy z.|  
  
### <a name="xsextension-in-xscomplexcontent-contents"></a>\<xs:Extension > w \<xs:complexContent >: zawartość  
 Reguły są takie same jak w przypadku `<xs:complexType>` zawartość.  
  
 Jeśli `<xs:sequence>` podano jego elementów członkowskich elementy mapy do elementów członkowskich dodatkowe dane, które znajdują się w kontraktu danych pochodnych.  
  
 Jeśli typ pochodny zawiera element o takiej samej nazwy jak element w typie podstawowym, deklaracji zduplikowany element mapy do elementu członkowskiego danych o nazwie, która jest generowana unikatowa. Dodatnia liczba całkowita numery są dodawane do nazwę elementu członkowskiego danych ("Członek1", "member2" itd.) aż do znalezienia unikatową nazwę. Z drugiej strony:  
  
-   Jeśli kontraktu danych pochodnej ma element członkowski danych z taką samą nazwę i typ jako element członkowski danych w kontrakt danych podstawowych `DataContractSerializer` generuje ten odpowiadający mu element w typie pochodnym.  
  
-   Jeśli kontraktu danych pochodnej ma element członkowski danych o takiej samej nazwie jako element członkowski danych, ale jest innego typu kontraktu danych podstawowych `DataContractSerializer` Importuje schemat z elementem typu `xs:anyType` w typie podstawowym i deklaracje typu pochodnego. Oryginalna nazwa typu jest zachowywana w `xs:annotations/xs:appInfo/ser:ActualType/@Name`.  
  
 Zarówno zmian może doprowadzić do schematu z niejednoznaczne modelu zawartości, który jest zależny rzędu elementy członkowskie odpowiednich danych.  
  
## <a name="typeprimitive-mapping"></a>Mapowanie typu/pierwotnego  
 `DataContractSerializer` Używa następującego mapowania dla typów pierwotnych schematu XML.  
  
|Typ XSD|Typ architektury .NET|  
|--------------|---------------|  
|`anyType`|<xref:System.Object>.|  
|`anySimpleType`|<xref:System.String>.|  
|`duration`|<xref:System.TimeSpan>.|  
|`dateTime`|<xref:System.DateTime>.|  
|`dateTimeOffset`|<xref:System.DateTime> i <xref:System.TimeSpan> przesunięcia. Zobacz poniższe serializacji typu DateTimeOffset.|  
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
 W [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] w wersji 1.0 `ISerializable` została wprowadzona jako mechanizm ogólne do serializacji obiektów do transferu danych lub trwałości. Istnieje wiele [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy, które implementują `ISerializable` i mogą być przekazywane między aplikacjami. `DataContractSerializer` Oczywiście zapewnia obsługę `ISerializable` klasy. `DataContractSerializer` Mapy `ISerializable` implementacja schematu typy, które różnią się tylko wielkością QName (kwalifikowana nazwa) tego typu i są efektywne kolekcji właściwości. Na przykład `DataContractSerializer` mapy <xref:System.Exception> do następującego typu XSD w http://schemas.datacontract.org/2004/07/System przestrzeni nazw.  
  
```xml  
<xs:complexType name="Exception">  
 <xs:sequence>  
  <xs:any minOccurs="0" maxOccurs="unbounded"   
      namespace="##local" processContents="skip"/>  
 </xs:sequence>  
 <xs:attribute ref="ser:FactoryType"/>  
</xs:complexType>  
```  
  
 Opcjonalny atrybut `ser:FactoryType` zadeklarowany w danych serializacji kontraktu schematu odwołuje się do klasy fabryki, która może wykonywać deserializację typu. Klasa fabryki muszą być częścią kolekcji znanych typów `DataContractSerializer` wystąpienie używane. Aby uzyskać więcej informacji na temat znanych typów, zobacz [znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
## <a name="datacontract-serialization-schema"></a>Schematu serializacji DataContract  
 Liczba schematów wyeksportowane przez `DataContractSerializer` użyć typów, elementy i atrybuty z specjalne nazw serializacji kontraktu danych:  
  
 http://schemas.microsoft.com/2003/10/Serialization  
  
 Poniżej znajduje się pełna deklaracja schematu serializacji kontraktu danych.  
  
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
  
-   `ser:char` wprowadzane do reprezentowania znaków Unicode typu <xref:System.Char>.  
  
-   `valuespace` z `xs:duration` zostanie zmniejszona do zestawu uporządkowanych, dzięki czemu mogą być mapowane na <xref:System.TimeSpan>.  
  
-   `FactoryType` jest używany w schematach wyeksportowane z typów, które są pochodnymi <xref:System.Runtime.Serialization.ISerializable>.  
  
## <a name="importing-non-datacontract-schemas"></a>Importowanie schematów innych niż typ  
 `DataContractSerializer` ma `ImportXmlTypes` opcję, aby umożliwić Importowanie schematów, które nie są zgodne z `DataContractSerializer` profilu XSD (zobacz <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> właściwości). Ustawienie tej opcji na `true` umożliwia akceptacji niezgodnych typów schematów i mapując je do wykonania następujących <xref:System.Xml.Serialization.IXmlSerializable> zawijania tablicę <xref:System.Xml.XmlNode> (różni się tylko nazwę klasy).  
  
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
 <xref:System.DateTimeOffset> Nie jest traktowana jako typ pierwotny. Zamiast tego jest serializowany jako element złożonych z dwóch części. Pierwsza część reprezentuje daty, godziny, a druga część — przesunięcie od chwili daty. Przykład serializacji wartości DateTimeOffset przedstawiono w poniższym kodzie.  
  
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
