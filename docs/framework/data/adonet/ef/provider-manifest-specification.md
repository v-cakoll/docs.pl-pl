---
title: Specyfikacja manifestu dostawcy
ms.date: 03/30/2017
ms.assetid: bb450b47-8951-4f99-9350-26f05a4d4e46
ms.openlocfilehash: bef4868ccc52d287baaceca32c4943723be7531f
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040492"
---
# <a name="provider-manifest-specification"></a>Specyfikacja manifestu dostawcy
W tej sekcji omówiono, w jaki sposób dostawca magazynu danych może obsługiwać typy i funkcje w magazynie danych.  
  
 Usługa Entity Services działa niezależnie od konkretnego dostawcy magazynu danych, mimo że dostawca danych jawnie definiuje sposób, w jaki modele, mapowania i zapytania współdziałają z bazowym magazynem danych. Bez warstwy abstrakcji usługi Entity Services mogą być wskazywane tylko przez określony magazyn danych lub dostawcę danych.  
  
 Typy obsługujące dostawcę są bezpośrednio lub pośrednio obsługiwane przez podstawową bazę danych. Te typy nie muszą być dokładnymi typami magazynów, ale typy stosowane przez dostawcę do obsługi Entity Framework. Typy dostawców/magazynów są opisane w tematach Entity Data Model (EDM).  
  
 Parametry i typy zwracane dla funkcji obsługiwanych przez magazyn danych są określone w obszarze EDM.  
  
## <a name="requirements"></a>Wymagania  
 Entity Framework i magazyn danych muszą być w stanie przekazywać dane z powrotem i dalej w znanych typach bez utraty lub obcięcia danych.  
  
 Manifest dostawcy musi być ładowany przez narzędzia w czasie projektowania bez konieczności otwierania połączenia z magazynem danych.  
  
 W Entity Framework rozróżniana jest wielkość liter, ale podstawowy magazyn danych może nie być. Gdy artefakty modelu EDM (na przykład identyfikatory i nazwy typów) są zdefiniowane i używane w manifeście, muszą używać Entity Framework rozróżniana wielkość liter. Jeśli w manifeście dostawcy znajdują się elementy magazynu danych, które mogą uwzględniać wielkość liter, należy zachować wielkość liter w manifeście dostawcy.  
  
 Entity Framework wymaga manifestu dostawcy dla wszystkich dostawców danych. Jeśli spróbujesz użyć dostawcy, który nie ma manifestu dostawcy z Entity Framework, zostanie wyświetlony komunikat o błędzie.  
  
 W poniższej tabeli opisano rodzaje wyjątków, jakie Entity Framework zostałyby zgłoszone w przypadku wystąpienia wyjątków przez interakcję z dostawcą:  
  
|Problem|Wyjątek|  
|-----------|---------------|  
|Dostawca nie obsługuje GetProviderManifest w DbProviderServices.|ProviderIncompatibleException|  
|Brak manifestu dostawcy: dostawca zwraca `null` podczas próby pobrania manifestu dostawcy.|ProviderIncompatibleException|  
|Nieprawidłowy manifest dostawcy: dostawca zwraca nieprawidłowy kod XML podczas próby pobrania manifestu dostawcy.|ProviderIncompatibleException|  
  
## <a name="scenarios"></a>Scenariusze  
 Dostawca powinien obsługiwać następujące scenariusze:  
  
### <a name="writing-a-provider-with-symmetric-type-mapping"></a>Pisanie dostawcy z mapowaniem typu symetrycznego  
 Można napisać dostawcę dla Entity Framework, w którym każdy typ sklepu mapuje do pojedynczego typu EDM, niezależnie od kierunku mapowania. W przypadku typu dostawcy, który ma bardzo proste mapowanie odpowiadające typowi modelu EDM, można użyć rozwiązania symetrycznego, ponieważ system typów jest prosty lub zgodny z typami modelu EDM.  
  
 Możesz użyć prostoty swojej domeny i utworzyć statyczny manifest dostawcy deklaratywnego.  
  
 Napiszesz plik XML, który ma dwie sekcje:  
  
- Lista typów dostawców wyrażona w postaci "odpowiedniki modelu EDM" typu lub funkcji magazynu. Typy magazynów mają odpowiedni typ modelu EDM. Funkcje magazynu mają odpowiednie funkcje modelu EDM. Na przykład, varchar jest typem SQL Server, ale odpowiedni typ modelu EDM to ciąg.  
  
- Lista funkcji obsługiwanych przez dostawcę, gdzie parametry i zwracane typy są wyrażane w warunkach EDM.  
  
### <a name="writing-a-provider-with-asymmetric-type-mapping"></a>Pisanie dostawcy z mapowaniem typu asymetrycznego  
 Podczas pisania dostawcy magazynu danych dla Entity Framework mapowanie typu modelu EDM do dostawcy dla niektórych typów może różnić się od mapowania typu dostawca-do-EDM. Na przykład niezależny obiekt EDM PrimitiveTypeKind. String może być mapowany na nvarchar (4000) na dostawcy, podczas gdy nvarchar (4000) mapuje do modelu EDM PrimitiveTypeKind. String (MaxLength = 4000).  
  
 Napiszesz plik XML, który ma dwie sekcje:  
  
- Lista typów dostawców wyrażona w warunkach modelu EDM i zdefiniuj mapowanie dla obu kierunków: EDM-to-Provider i Provider-do-EDM.  
  
- Lista funkcji obsługiwanych przez dostawcę, gdzie parametry i zwracane typy są wyrażane w warunkach EDM.  
  
## <a name="provider-manifest-discoverability"></a>Odnajdywanie manifestu dostawcy  
 Manifest jest używany pośrednio przez kilka typów składników w usługach Entity Services (na przykład narzędzia lub zapytania), ale bardziej bezpośrednio korzystających z metadanych przy użyciu modułu ładującego metadanych magazynu danych.  
  
 ![dfb3d02b&#45;7a8c&#45;4d51&#45;ac5a&#45;a73d8aa145e6](./media/dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6.gif "dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6")  
  
 Jednak dany dostawca może obsługiwać różne magazyny lub różne wersje tego samego magazynu. W związku z tym dostawca musi zgłosić inny manifest dla każdego z obsługiwanych magazynów danych.  
  
### <a name="provider-manifest-token"></a>Token manifestu dostawcy  
 Po otwarciu połączenia z magazynem danych dostawca może wysyłać zapytania o informacje w celu zwrócenia odpowiedniego manifestu. Może to nie być możliwe w scenariuszach w trybie offline, w których informacje o połączeniu są niedostępne lub nie można nawiązać połączenia ze sklepem. Zidentyfikuj manifest przy użyciu atrybutu `ProviderManifestToken` elementu `Schema` w pliku SSDL. Nie ma wymaganego formatu dla tego atrybutu; Dostawca wybiera minimalne informacje niezbędne do zidentyfikowania manifestu bez otwierania połączenia z magazynem.  
  
 Na przykład:  
  
```xml  
<Schema Namespace="Northwind" Provider="System.Data.SqlClient" ProviderManifestToken="2005" xmlns:edm="http://schemas.microsoft.com/ado/2006/04/edm/ssdl" xmlns="http://schemas.microsoft.com/ado/2006/04/edm/ssdl">  
```  
  
## <a name="provider-manifest-programming-model"></a>Model programowania manifestu dostawcy  
 Dostawcy pochodzą z <xref:System.Data.Common.DbXmlEnabledProviderManifest>, co umożliwia ich deklaratywne określanie ich manifestów. Na poniższej ilustracji przedstawiono hierarchię klas dostawcy:  
  
 ![Dawaj](./media/d541eba3-2ee6-4cd1-88f5-89d0b2582a6c.gif "d541eba3-2ee6-4cd1-88f5-89d0b2582a6c")  
  
### <a name="discoverability-api"></a>Interfejs API odnajdywania  
 Manifest dostawcy jest ładowany przez moduł ładujący metadanych magazynu (StoreItemCollection), przy użyciu połączenia magazynu danych lub tokenu manifestu dostawcy.  
  
#### <a name="using-a-data-store-connection"></a>Korzystanie z połączenia magazynu danych  
 Gdy jest dostępne połączenie z magazynem danych, wywołaj <xref:System.Data.Common.DbProviderServices.GetProviderManifestToken%2A?displayProperty=nameWithType>, aby zwrócić token, który jest przesyłany do metody <xref:System.Data.Common.DbProviderServices.GetProviderManifest%2A>, która zwraca <xref:System.Data.Common.DbProviderManifest>. Ta metoda deleguje do implementacji dostawcy `GetDbProviderManifestToken`.  
  
```csharp
public string GetProviderManifestToken(DbConnection connection);  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
#### <a name="using-a-provider-manifest-token"></a>Korzystanie z tokenu manifestu dostawcy  
 W przypadku scenariusza offline token jest wybierany z reprezentacji SSDL. SSDL pozwala określić ProviderManifestToken (zobacz [element Schema (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl) , aby uzyskać więcej informacji. Na przykład jeśli nie można otworzyć połączenia, plik SSDL ma token manifestu dostawcy, który określa informacje o manifeście.  
  
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
  
#### <a name="types-node"></a>Węzeł typów  
 Węzeł typy w manifeście dostawcy zawiera informacje o typach, które są obsługiwane natywnie przez magazyn danych lub przez dostawcę.  
  
##### <a name="type-node"></a>Węzeł typu  
 Każdy węzeł typu definiuje typ dostawcy w kategoriach modelu EDM. Węzeł typu zawiera opis nazwy typu dostawcy i informacje związane z typem modelu, który jest mapowany do i aspektami opisującymi tego mapowania typu.  
  
 Aby można było wyrazić te informacje o typie w manifeście dostawcy, każda deklaracja TypeInformation musi definiować kilka opisów aspektów dla każdego typu:  
  
|Nazwa atrybutu|Typ danych|Wymagane|Wartość domyślna|Opis|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|Nazwa|String|Tak|n/d|Nazwa typu danych specyficznych dla dostawcy|  
|PrimitiveTypeKind|PrimitiveTypeKind|Tak|n/d|Nazwa typu modelu EDM|  
  
###### <a name="function-node"></a>Węzeł funkcji  
 Każda funkcja definiuje pojedynczą funkcję dostępną za pomocą dostawcy.  
  
|Nazwa atrybutu|Typ danych|Wymagane|Wartość domyślna|Opis|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|Nazwa|String|Tak|n/d|Identyfikator/nazwa funkcji|  
|Atrybuty|String|Nie|Pozycję|Typ zwracany funkcji modelu EDM|  
|Agregowanie|Boolean|Nie|False|True, jeśli funkcja jest funkcją agregującą|  
|Wbudowan|Boolean|Nie|Oznacza|Prawda, jeśli funkcja jest wbudowana w magazyn danych|  
|StoreFunctionName|String|Nie|Nazwa \<|Nazwa funkcji w magazynie danych.  Umożliwia przekierowanie nazw funkcji.|  
|NiladicFunction|Boolean|Nie|False|Prawda, jeśli funkcja nie wymaga parametrów i jest wywoływana bez żadnych parametrów|  
|ParameterType<br /><br /> Semantyki|ParameterSemantics|Nie|AllowImplicit<br /><br /> Konwersja|Wybór sposobu postępowania z zastępowaniem typu parametru przez potok zapytania:<br /><br /> - ExactMatchOnly<br />- AllowImplicitPromotion<br />- AllowImplicitConversion|  
  
 **Węzeł parametrów**  
  
 Każda funkcja ma kolekcję z co najmniej jednym węzłem parametrów.  
  
|Nazwa atrybutu|Typ danych|Wymagane|Wartość domyślna|Opis|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|Nazwa|String|Tak|n/d|Identyfikator/Nazwa parametru.|  
|Typ|String|Tak|n/d|Typ modelu EDM.|  
|Tryb|Parametr<br /><br /> Kierunek|Tak|n/d|Kierunek parametru:<br /><br /> -in<br />-out<br />-Inout|  
  
##### <a name="namespace-attribute"></a>Namespace — atrybut  
 Każdy dostawca magazynu danych musi definiować przestrzeń nazw lub grupę przestrzeni nazw, aby uzyskać informacje zdefiniowane w manifeście. Ta przestrzeń nazw może być używana w Entity SQL zapytania do rozpoznawania nazw funkcji i typów. Na przykład: SqlServer. Ta przestrzeń nazw musi być różna od kanonicznej przestrzeni nazw, EDM zdefiniowanej przez usługi jednostek dla funkcji standardowych, które mają być obsługiwane przez Entity SQL zapytań.  
  
## <a name="see-also"></a>Zobacz także

- [Pisanie dostawcy danych programu Entity Framework](writing-an-ef-data-provider.md)
