---
title: Specyfikacja manifestu dostawcy
ms.date: 03/30/2017
ms.assetid: bb450b47-8951-4f99-9350-26f05a4d4e46
ms.openlocfilehash: 28bae8a6e249aa1fdab3c67759c8f8575cbdaa10
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149729"
---
# <a name="provider-manifest-specification"></a>Specyfikacja manifestu dostawcy
W tej sekcji omówiono sposób, w jaki dostawca magazynu danych może obsługiwać typy i funkcje w magazynie danych.  
  
 Usługi jednostek działają niezależnie od określonego dostawcy magazynu danych, ale nadal umożliwia dostawcy danych jawne zdefiniowanie interakcji modeli, mapowań i zapytań z podstawowym magazynem danych. Bez warstwy abstrakcji usługi encji mogą być kierowane tylko do określonego magazynu danych lub dostawcy danych.  
  
 Typy obsługiwane przez dostawcę są bezpośrednio lub pośrednio obsługiwane przez podstawową bazę danych. Te typy nie są koniecznie dokładne typy magazynu, ale typy, których dostawca używa do obsługi entity framework. Typy dostawcy/magazynu są opisane w warunkach modelu danych jednostki (EDM).  
  
 Typy parametrów i zwracanych dla funkcji obsługiwanych przez magazyn danych są określone w warunkach EDM.  
  
## <a name="requirements"></a>Wymagania  
 Entity Framework i magazynu danych muszą mieć możliwość przekazywania danych tam iz powrotem w znanych typów bez utraty danych lub obcinania.  
  
 Manifest dostawcy musi być ładowany przez narzędzia w czasie projektowania bez konieczności otwierania połączenia z magazynem danych.  
  
 W ramach jednostki rozróżniana jest wielkość liter, ale podstawowy magazyn danych może nie być. Gdy artefakty EDM (identyfikatory i nazwy typów, na przykład) są zdefiniowane i używane w manifeście, muszą używać czułości wielkości liter entity framework. Jeśli elementy magazynu danych, które mogą być rozróżniane wielkość liter pojawiają się w manifeście dostawcy, że wielkość liter musi być obsługiwana w manifeście dostawcy.  
  
 Entity Framework wymaga manifestu dostawcy dla wszystkich dostawców danych. Jeśli spróbujesz użyć dostawcy, który nie ma manifestu dostawcy z entity framework, pojawi się błąd.  
  
 W poniższej tabeli opisano rodzaje wyjątków, które struktura jednostek zgłaszałaby, gdy wyjątki powstają za pośrednictwem interakcji z dostawcą:  
  
|Problem|Wyjątek|  
|-----------|---------------|  
|Dostawca nie obsługuje GetProviderManifest w DbProviderServices.|Providerincompatibleexception|  
|Brak oczywistego dostawcy: `null` dostawca zwraca podczas próby pobrania manifestu dostawcy.|Providerincompatibleexception|  
|Nieprawidłowy manifest dostawcy: dostawca zwraca nieprawidłowy kod XML podczas próby pobrania manifestu dostawcy.|Providerincompatibleexception|  
  
## <a name="scenarios"></a>Scenariusze  
 Dostawca powinien obsługiwać następujące scenariusze:  
  
### <a name="writing-a-provider-with-symmetric-type-mapping"></a>Pisanie dostawcy za pomocą mapowania typów symetrycznych  
 Można napisać dostawcę dla entity framework, gdzie każdy typ magazynu mapuje do jednego typu EDM, niezależnie od kierunku mapowania. Dla typu dostawcy, który ma bardzo proste mapowanie, które odpowiada typowi EDM, można użyć rozwiązania symetrycznego, ponieważ system typów jest prosty lub pasuje do typów EDM.  
  
 Można użyć prostoty ich domeny i utworzyć statyczny manifest dostawcy deklaratywnego.  
  
 Piszesz plik XML, który ma dwie sekcje:  
  
- Lista typów dostawców wyrażona w kategoriach "odpowiednika EDM" typu sklepu lub funkcji. Typy sklepów mają odpowiednik typów EDM. Funkcje sklepu mają odpowiednie funkcje EDM. Na przykład varchar jest typem programu SQL Server, ale odpowiedni typ EDM to ciąg.  
  
- Lista funkcji obsługiwanych przez dostawcę, gdzie typy parametrów i zwracanych są wyrażone w warunkach EDM.  
  
### <a name="writing-a-provider-with-asymmetric-type-mapping"></a>Pisanie dostawcy za pomocą mapowania typów asymetrycznych  
 Podczas zapisywania dostawcy magazynu danych dla entity framework mapowanie typu EDM-to-provider dla niektórych typów może się różnić od mapowania typu dostawcy do EDM. Na przykład niezwiązany EDM PrimitiveTypeKind.String może mapować do nvarchar(4000) w dostawcy, podczas gdy nvarchar(4000) mapuje do EDM PrimitiveTypeKind.String(MaxLength=4000).  
  
 Piszesz plik XML, który ma dwie sekcje:  
  
- Lista typów dostawców wyrażona w warunkach EDM i definiowanie mapowania dla obu kierunków: EDM-to-provider i provider-to-EDM.  
  
- Lista funkcji obsługiwanych przez dostawcę, gdzie typy parametrów i zwracanych są wyrażone w warunkach EDM.  
  
## <a name="provider-manifest-discoverability"></a>Wykrywalność manifestu dostawcy  
 Manifest jest używany pośrednio przez kilka typów składników w usługach encji (na przykład Narzędzia lub kwerenda), ale bardziej bezpośrednio wykorzystywane przez metadane za pomocą modułu ładującego metadane magazynu danych.  
  
 ![dfb3d02b&#45;7a8c&#45;4d51&#45;ac5a&#45;a73d8aa145e6](./media/dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6.gif "dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6")  
  
 Jednak dany dostawca może obsługiwać różne sklepy lub różne wersje tego samego sklepu. W związku z tym dostawca musi zgłosić inny manifest dla każdego obsługiwanego magazynu danych.  
  
### <a name="provider-manifest-token"></a>Token manifestu dostawcy  
 Po otwarciu połączenia magazynu danych dostawca może wysyłać zapytania o informacje, aby zwrócić odpowiedni manifest. Może to nie być możliwe w scenariuszach offline, w których informacje o połączeniu nie są dostępne lub gdy nie można połączyć się ze sklepem. Zidentyfikuj `ProviderManifestToken` manifest przy `Schema` użyciu atrybutu elementu w pliku .ssdl. Nie ma wymaganego formatu dla tego atrybutu; dostawca wybiera minimalne informacje potrzebne do identyfikacji manifestu bez otwierania połączenia ze sklepem.  
  
 Przykład:  
  
```xml  
<Schema Namespace="Northwind" Provider="System.Data.SqlClient" ProviderManifestToken="2005" xmlns:edm="http://schemas.microsoft.com/ado/2006/04/edm/ssdl" xmlns="http://schemas.microsoft.com/ado/2006/04/edm/ssdl">  
```  
  
## <a name="provider-manifest-programming-model"></a>Model programowania manifestu dostawcy  
 Dostawcy wywodzą się z <xref:System.Data.Common.DbXmlEnabledProviderManifest>, co pozwala im określić ich manifesty deklaratywnie. Na poniższej ilustracji przedstawiono hierarchię klas dostawcy:  
  
 ![Brak](./media/d541eba3-2ee6-4cd1-88f5-89d0b2582a6c.gif "d541eba3-2ee6-4cd1-88f5-89d0b2582a6c")  
  
### <a name="discoverability-api"></a>Interfejs API wykrywania  
 Manifest dostawcy jest ładowany przez program ładujący metadane magazynu (StoreItemCollection), przy użyciu połączenia magazynu danych lub tokenu manifestu dostawcy.  
  
#### <a name="using-a-data-store-connection"></a>Korzystanie z połączenia magazynu danych  
 Gdy połączenie magazynu danych jest <xref:System.Data.Common.DbProviderServices.GetProviderManifestToken%2A?displayProperty=nameWithType> dostępne, wywołanie zwrócenia <xref:System.Data.Common.DbProviderServices.GetProviderManifest%2A> tokenu, <xref:System.Data.Common.DbProviderManifest>który jest przekazywany do metody, która zwraca . Ta metoda deleguje do implementacji dostawcy `GetDbProviderManifestToken`.  
  
```csharp
public string GetProviderManifestToken(DbConnection connection);  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
#### <a name="using-a-provider-manifest-token"></a>Korzystanie z tokenu manifestu dostawcy  
 W scenariuszu offline token jest pobierany z reprezentacji SSDL. SSDL umożliwia określenie ProviderManifestToken (zobacz [Element schematu (SSDL), aby](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl) uzyskać więcej informacji). Na przykład jeśli nie można otworzyć połączenia, SSDL ma token manifestu dostawcy, który określa informacje o manifeście.  
  
```csharp
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
### <a name="provider-manifest-schema"></a>Schemat manifestu dostawcy  
 Schemat informacji zdefiniowanych dla każdego dostawcy zawiera informacje statyczne, które mają być używane przez metadane:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema elementFormDefault="qualified"  
   xmlns:xs="http://www.w3.org/2001/XMLSchema"  
   targetNamespace="http://schemas.microsoft.com/ado/2006/04/edm/providermanifest"  
   xmlns:pm="http://schemas.microsoft.com/ado/2006/04/edm/providermanifest">  
  
  <xs:element name="ProviderManifest">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="Types" type="pm:TTypes" minOccurs="1" maxOccurs="1" />  
        <xs:element name="Functions" type="pm:TFunctions" minOccurs="0" maxOccurs="1"/>  
      </xs:sequence>  
      <xs:attribute name="Namespace" type="xs:string" use="required"/>  
    </xs:complexType>  
  </xs:element>  
  <xs:complexType name="TVersion">  
    <xs:attribute name="Major" type="xs:int" use="required" />  
    <xs:attribute name="Minor" type="xs:int" use="required" />  
    <xs:attribute name="Build" type="xs:int" use="required" />  
    <xs:attribute name="Revision" type="xs:int" use="required" />  
  </xs:complexType>  
  
  <xs:complexType name="TIntegerFacetDescription">  
    <xs:attribute name="Minimum" type="xs:int" use="optional" />  
    <xs:attribute name="Maximum" type="xs:int" use="optional" />  
    <xs:attribute name="DefaultValue" type="xs:int" use="optional" />  
    <xs:attribute name="Constant" type="xs:boolean" default="false" />  
  </xs:complexType>  
  
  <xs:complexType name="TBooleanFacetDescription">  
    <xs:attribute name="DefaultValue" type="xs:boolean" use="optional" />  
    <xs:attribute name="Constant" type="xs:boolean" default="true" />  
  </xs:complexType>  
  
  <xs:complexType name="TDateTimeFacetDescription">  
    <xs:attribute name="Constant" type="xs:boolean" default="false" />  
  </xs:complexType>  
  
  <xs:complexType name="TFacetDescriptions">  
    <xs:choice maxOccurs="unbounded">  
      <xs:element name="Precision" minOccurs="0" maxOccurs="1" type="pm:TIntegerFacetDescription"/>  
      <xs:element name="Scale" minOccurs="0" maxOccurs="1" type="pm:TIntegerFacetDescription"/>  
      <xs:element name="MaxLength" minOccurs="0" maxOccurs="1" type="pm:TIntegerFacetDescription"/>  
      <xs:element name="Unicode" minOccurs="0" maxOccurs="1" type="pm:TBooleanFacetDescription"/>  
      <xs:element name="FixedLength" minOccurs="0" maxOccurs="1" type="pm:TBooleanFacetDescription"/>  
    </xs:choice>  
  </xs:complexType>  
  
  <xs:complexType name="TType">  
    <xs:sequence>  
      <xs:element name="FacetDescriptions" type="pm:TFacetDescriptions" minOccurs="0" maxOccurs="1"/>  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="required"/>  
    <xs:attribute name="PrimitiveTypeKind" type="pm:TPrimitiveTypeKind" use="required" />  
  </xs:complexType>  
  
  <xs:complexType name="TTypes">  
    <xs:sequence>  
      <xs:element name="Type" type="pm:TType" minOccurs="0" maxOccurs="unbounded"/>  
    </xs:sequence>  
  </xs:complexType>  
  
  <xs:attributeGroup name="TFacetAttribute">  
    <xs:attribute name="Precision" type="xs:int" use="optional"/>  
    <xs:attribute name="Scale" type="xs:int" use="optional"/>  
    <xs:attribute name="MaxLength" type="xs:int" use="optional"/>  
    <xs:attribute name="Unicode" type="xs:boolean" use="optional"/>  
    <xs:attribute name="FixedLength" type="xs:boolean" use="optional"/>  
  </xs:attributeGroup>  
  
  <xs:complexType name="TFunctionParameter">  
    <xs:attribute name="Name" type="xs:string" use="required" />  
    <xs:attribute name="Type" type="xs:string" use="required" />  
    <xs:attributeGroup ref="pm:TFacetAttribute" />  
    <xs:attribute name="Mode" type="pm:TParameterDirection" use="required" />  
  </xs:complexType>  
  
  <xs:complexType name="TReturnType">  
    <xs:attribute name="Type" type="xs:string" use="required" />  
    <xs:attributeGroup ref="pm:TFacetAttribute" />  
  </xs:complexType>  
  
  <xs:complexType name="TFunction">  
    <xs:choice minOccurs="0" maxOccurs ="unbounded">  
      <xs:element name ="ReturnType" type="pm:TReturnType" minOccurs="0" maxOccurs="1" />  
      <xs:element name="Parameter" type="pm:TFunctionParameter" minOccurs="0" maxOccurs="unbounded"/>  
    </xs:choice>  
    <xs:attribute name="Name" type="xs:string" use="required" />  
    <xs:attribute name="Aggregate" type="xs:boolean" use="optional" />  
    <xs:attribute name="BuiltIn" type="xs:boolean" use="optional" />  
    <xs:attribute name="StoreFunctionName" type="xs:string" use="optional" />  
    <xs:attribute name="NiladicFunction" type="xs:boolean" use="optional" />  
    <xs:attribute name="ParameterTypeSemantics" type="pm:TParameterTypeSemantics" use="optional" default="AllowImplicitConversion" />  
  </xs:complexType>  
  
  <xs:complexType name="TFunctions">  
    <xs:sequence>  
      <xs:element name="Function" type="pm:TFunction" minOccurs="0" maxOccurs="unbounded"/>  
    </xs:sequence>  
  </xs:complexType>  
  
  <xs:simpleType name="TPrimitiveTypeKind">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Binary"/>  
      <xs:enumeration value="Boolean"/>  
      <xs:enumeration value="Byte"/>  
      <xs:enumeration value="Decimal"/>  
      <xs:enumeration value="DateTime"/>  
      <xs:enumeration value="Time"/>  
      <xs:enumeration value="DateTimeOffset"/>
      <xs:enumeration value="Double"/>  
      <xs:enumeration value="Guid"/>  
      <xs:enumeration value="Single"/>  
      <xs:enumeration value="SByte"/>  
      <xs:enumeration value="Int16"/>  
      <xs:enumeration value="Int32"/>  
      <xs:enumeration value="Int64"/>  
      <xs:enumeration value="String"/>  
    </xs:restriction>  
  </xs:simpleType>  
  
  <xs:simpleType name="TParameterDirection">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="In"/>  
      <xs:enumeration value="Out"/>  
      <xs:enumeration value="InOut"/>  
    </xs:restriction>  
  </xs:simpleType>  
  
  <xs:simpleType name="TParameterTypeSemantics">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="ExactMatchOnly" />  
      <xs:enumeration value="AllowImplicitPromotion" />  
      <xs:enumeration value="AllowImplicitConversion" />  
    </xs:restriction>  
  </xs:simpleType>  
</xs:schema>  
```  
  
#### <a name="types-node"></a>Typy węzła  
 Węzeł Typy w manifeście dostawcy zawiera informacje o typach, które są obsługiwane natywnie przez magazyn danych lub za pośrednictwem dostawcy.  
  
##### <a name="type-node"></a>Typ węzła  
 Każdy węzeł typu definiuje typ dostawcy pod względem EDM. Węzeł Typ opisuje nazwę typu dostawcy i informacje związane z typem modelu, do który jest mapowana, oraz aspekty opisujące mapowanie tego typu.  
  
 Aby wyrazić informacje o tym typie w manifeście dostawcy, każda deklaracja TypeInformation musi zdefiniować kilka opisów aspektu dla każdego typu:  
  
|Nazwa atrybutu|Typ danych|Wymagany|Wartość domyślna|Opis|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|Nazwa|Ciąg|Tak|Nie dotyczy|Nazwa typu danych specyficznych dla dostawcy|  
|PrymitywTypeKind|PrymitywTypeKind|Tak|Nie dotyczy|Nazwa typu EDM|  
  
###### <a name="function-node"></a>Węzeł funkcji  
 Każda funkcja definiuje jedną funkcję dostępną za pośrednictwem dostawcy.  
  
|Nazwa atrybutu|Typ danych|Wymagany|Wartość domyślna|Opis|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|Nazwa|Ciąg|Tak|Nie dotyczy|Identyfikator/nazwa funkcji|  
|Returntype|Ciąg|Nie|Void|Typ zwracany EDM funkcji|  
|Agregacja|Wartość logiczna|Nie|False|Wartość true, jeśli funkcja jest funkcją agregującą|  
|Wbudowane|Wartość logiczna|Nie|True|Wartość true, jeśli funkcja jest wbudowana w magazyn danych|  
|Nazwa magazynu|Ciąg|Nie|\<Nazwa>|Nazwa funkcji w magazynie danych.  Pozwala na poziom przekierowania nazw funkcji.|  
|Funkcja Niladic|Wartość logiczna|Nie|False|Prawda, jeśli funkcja nie wymaga parametrów i jest wywoływana bez żadnych parametrów|  
|Parametertype<br /><br /> Semantyka|ParametrSemantyka|Nie|Zezwalaj Na Implikowanie<br /><br /> Konwersja|Wybór sposobu, w jaki potok zapytań powinien radzić sobie z podstawianiam typu parametrów:<br /><br /> - ExactMatchOnly<br />- AllowImplicitPromotion<br />- AllowImplicitConversion|  
  
 **Węzeł parametrów**  
  
 Każda funkcja ma kolekcję jednego lub więcej węzłów parametrów.  
  
|Nazwa atrybutu|Typ danych|Wymagany|Wartość domyślna|Opis|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|Nazwa|Ciąg|Tak|Nie dotyczy|Identyfikator/nazwa parametru.|  
|Typ|Ciąg|Tak|Nie dotyczy|Typ EDM parametru.|  
|Tryb|Parametr<br /><br /> Kierunek|Tak|Nie dotyczy|Kierunek parametru:<br /><br /> - w<br />- na zewnątrz<br />- inout|  
  
##### <a name="namespace-attribute"></a>Atrybut obszaru nazw  
 Każdy dostawca magazynu danych musi zdefiniować obszar nazw lub grupę obszarów nazw dla informacji zdefiniowanych w manifeście. Ten obszar nazw może służyć w kwerendach SQL encji do rozpoznawania nazw funkcji i typów. Na przykład: SqlServer. Ten obszar nazw musi się różnić od kanonicznego obszaru nazw EDM, zdefiniowanego przez usługi encji dla standardowych funkcji, które mają być obsługiwane przez zapytania SQL jednostki.  
  
## <a name="see-also"></a>Zobacz też

- [Pisanie dostawcy danych programu Entity Framework](writing-an-ef-data-provider.md)
