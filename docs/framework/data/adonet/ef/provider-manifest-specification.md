---
title: Specyfikacja manifestu dostawcy
ms.date: 03/30/2017
ms.assetid: bb450b47-8951-4f99-9350-26f05a4d4e46
ms.openlocfilehash: 592d435dd0da3a66fb3bbd278a53facb6cf08cb7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54734055"
---
# <a name="provider-manifest-specification"></a>Specyfikacja manifestu dostawcy
W tej sekcji omówiono, jak dostawca magazynu danych może obsługiwać typy i funkcje w magazynie danych.  
  
 Jednostki usługi działa niezależnie od danych specyficznych dla dostawcy magazynu, ale nadal umożliwia jawne zdefiniowanie sposobu interakcji modeli, mapowania i kwerendy z podstawowym magazynie danych dostawcy danych. Bez warstwę abstrakcji jednostki usługi może być przeznaczony tylko dla określonych danych sklepu lub Dostawca danych.  
  
 Typy obsługiwane przez dostawcę są bezpośrednio lub pośrednio obsługiwane przez podstawowej bazy danych. Te typy nie są zawsze typów magazynów dokładnie, ale typy dostawca używa do obsługi [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. W warunkach Entity Data Model (EDM) opisano typy dostawcy/magazynowania.  
  
 Typy parametrów i zwrotu w funkcji obsługiwanych przez Magazyn danych są określone w postanowieniach EDM.  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] i magazynu danych muszą mieć możliwość przekazywania danych i z powrotem w znanych typów bez utraty danych lub obcięcie.  
  
 Manifest dostawcy musi być obciążana za pomocą narzędzi w czasie projektowania bez konieczności otwierania połączenia z magazynem danych.  
  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Jest przypadek wielkość liter, ale źródłowy magazyn danych może nie być. Gdy artefakty EDM (identyfikatory i nazwy typów, na przykład) są zdefiniowane i używane w manifeście, należy użyć [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] wielkość liter. Jeśli elementów magazynu danych, które mogą być uwzględniana wielkość liter są wyświetlane w manifeście dostawcy, że wielkość liter w wyrazie musi być utrzymywane w manifeście dostawcy.  
  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Wymaga manifest dostawcy dla wszystkich dostawców danych. Jeśli spróbujesz użyć dostawcy, który nie ma dostawcy manifestu z [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], otrzymają komunikat o błędzie.  
  
 W poniższej tabeli opisano rodzaje wyjątków [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] powodowało zgłoszenie, gdy wyjątki wynikać dostawca interakcji:  
  
|Problem|Wyjątek|  
|-----------|---------------|  
|Dostawca nie obsługuje GetProviderManifest w DbProviderServices.|ProviderIncompatibleException|  
|Brak manifestu dostawcy: dostawca zwraca `null` podczas próby pobrania manifestu dostawcy.|ProviderIncompatibleException|  
|Nieprawidłowy dostawca manifest: dostawca zwraca nieprawidłowy kod XML, podczas próby pobrania manifestu dostawcy.|ProviderIncompatibleException|  
  
## <a name="scenarios"></a>Scenariusze  
 Dostawca powinien obsługiwać następujące scenariusze:  
  
### <a name="writing-a-provider-with-symmetric-type-mapping"></a>Pisanie dostawcy za pomocą mapowania typu symetryczne  
 Można napisać dostawcę dla [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] gdzie każdego typu magazynu jest mapowany na pojedynczy typ EDM, niezależnie od tego, w kierunku mapowania. Dla typu dostawcy, który znajduje się bardzo prostego mapowanie odpowiada za pomocą typu EDM można użyć symetrycznego rozwiązania, ponieważ system typu prostego lub pasuje do typu EDM.  
  
 Można użyć prostotę ich domeny i wygenerować manifest dostawcy deklaratywne statyczne.  
  
 Możesz napisać plik XML, który ma dwie sekcje:  
  
-   Lista typy dostawców, wyrażonych "EDM odpowiednikiem" typ magazynu lub funkcji. Typy Store mają odpowiednika typów EDM. Funkcje Store mają odpowiednie funkcje EDM. Na przykład varchar jest typem programu SQL Server, ale odpowiedni typ EDM jest ciągiem.  
  
-   Lista funkcji obsługiwanych przez dostawcę, w których typy parametrów i zwrotu jest wyrażany w kategoriach EDM.  
  
### <a name="writing-a-provider-with-asymmetric-type-mapping"></a>Pisanie dostawcy za pomocą asymetrycznych Typ mapowania  
 Podczas pisania dostawca magazynu danych dla [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], typ EDM do dostawcy mapowanie dla niektórych typów może się różnić od typu dostawcy do EDM mapowania. Na przykład niepowiązane PrimitiveTypeKind.String EDM mogą być mapowane do nvarchar(4000) na dostawcy, gdy nvarchar(4000) mapuje EDM PrimitiveTypeKind.String(MaxLength=4000).  
  
 Możesz napisać plik XML, który ma dwie sekcje:  
  
-   Lista typów dostawcy wyrażany w kategoriach EDM i zdefiniować mapowanie dla obu kierunku: EDM do dostawcy i dostawcy do EDM.  
  
-   Lista funkcji obsługiwanych przez dostawcę, w których typy parametrów i zwrotu jest wyrażany w kategoriach EDM.  
  
## <a name="provider-manifest-discoverability"></a>Odnajdowanie manifestu dostawcy  
 Manifest używany jest pośrednio w różnych typach składnika w jednostki usługi (na przykład narzędzia lub zapytanie), ale przechowywać więcej bezpośrednio wykorzystywane przez metadane za pomocą danych modułu ładującego metadanych.  
  
 ![dfb3d02b&#45;7a8c&#45;4d51&#45;ac5a&#45;a73d8aa145e6](../../../../../docs/framework/data/adonet/ef/media/dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6.gif "dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6")  
  
 Jednak danego dostawcy mogą obsługiwać różne wersje tego samego magazynu lub różnych magazynów danych. W związku z tym dostawca, musisz zgłosić różnych manifestu dla każdego obsługiwanego magazynu danych.  
  
### <a name="provider-manifest-token"></a>Token manifestu dostawcy  
 Po otwarciu połączenia magazynu danych dostawcy mogą wysyłać zapytania dotyczące informacji do zwrócenia prawo manifestu. To może nie być możliwe w scenariuszach w trybie offline gdy informacje o połączeniu nie są dostępne lub kiedy nie jest możliwość nawiązywania połączeń do magazynu. Identyfikowanie manifest za pomocą `ProviderManifestToken` atrybutu `Schema` elementu souboru ssdl. Brak ma wymaganego formatu dla tego atrybutu; Dostawca wybiera minimalne informacje potrzebne do identyfikowania manifestu bez konieczności otwierania połączenia z magazynem.  
  
 Na przykład:  
  
```xml  
<Schema Namespace="Northwind" Provider="System.Data.SqlClient" ProviderManifestToken="2005" xmlns:edm="http://schemas.microsoft.com/ado/2006/04/edm/ssdl" xmlns="http://schemas.microsoft.com/ado/2006/04/edm/ssdl">  
```  
  
## <a name="provider-manifest-programming-model"></a>Model programowania z manifestu dostawcy  
 Dostawców pochodzić od <xref:System.Data.Common.DbXmlEnabledProviderManifest>, co pozwala określić swoich manifestach deklaratywnie. Poniższa ilustracja przedstawia hierarchii klas dostawcy:  
  
 ![None](../../../../../docs/framework/data/adonet/ef/media/d541eba3-2ee6-4cd1-88f5-89d0b2582a6c.gif "d541eba3-2ee6-4cd1-88f5-89d0b2582a6c")  
  
### <a name="discoverability-api"></a>Odnajdowanie interfejsu API  
 Manifest dostawcy jest ładowany przez moduł ładujący Store metadanych (obiektu StoreItemCollection), przy użyciu danych przechowywać połączenia lub tokenu manifestu dostawcy.  
  
#### <a name="using-a-data-store-connection"></a>Przy użyciu połączenia danych Store  
 Gdy magazyn danych jest dostępne połączenie, wywołaj DbProvderServices.GetProviderManifestToken do zwracania tokenu, który jest przekazywany do metody GetProviderManifest, która zwraca DbProviderManifest. Ta metoda deleguje do implementacji dostawcy GetDbProviderManifestToken.  
  
```  
public string GetProviderManifestToken(DbConnection connection);  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
#### <a name="using-a-provider-manifest-token"></a>Za pomocą tokenu manifestu dostawcy  
 W scenariuszu w trybie offline token jest pobierany z reprezentacji SSDL. SSDL pozwala na określenie ProviderManifestToken (zobacz [elementu schematu (SSDL)](https://msdn.microsoft.com/library/fec75ae4-7f16-4421-9265-9dac61509222) Aby uzyskać więcej informacji). Na przykład jeśli nie można otworzyć połączenia, SSDL ma token manifestu dostawcy, który określa informacje dotyczące manifestu.  
  
```  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
### <a name="provider-manifest-schema"></a>Schematu manifestu dostawcy  
 Schemat informacje zdefiniowane dla każdego dostawcy zawiera dane statyczne do użycia przez metadane:  
  
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
  
#### <a name="types-node"></a>Typy węzłów  
 Węzeł typów w manifeście dostawcy zawiera informacje o typach, które są obsługiwane natywnie przez Magazyn danych lub za pośrednictwem dostawcy.  
  
##### <a name="type-node"></a>Typ węzła  
 Każdy typ węzła definiuje typ dostawcy pod względem EDM. Węzeł typu w tym artykule opisano nazwa, typ dostawcy i informacje dotyczące typ modelu, który jest on mapowany i zestawów reguł do opisania mapowania typu.  
  
 Aby można było express to informacje o typie w manifeście dostawcy, każdego zgłoszenia TypeInformation należy zdefiniować kilka opisów reguł dla każdego typu:  
  
|Nazwa atrybutu|Typ danych|Wymagane|Wartość domyślna|Opis|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|Nazwa|String|Tak|n/d|Nazwa typu danych specyficznego dla dostawcy|  
|PrimitiveTypeKind|PrimitiveTypeKind|Tak|n/d|Nazwa typu EDM|  
  
###### <a name="function-node"></a>Węzeł — funkcja  
 Każda funkcja określa jednej funkcji dostępnych za pośrednictwem dostawcy.  
  
|Nazwa atrybutu|Typ danych|Wymagane|Wartość domyślna|Opis|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|Nazwa|String|Tak|n/d|Identyfikator/nazwę funkcji|  
|ReturnType|String|Nie|Void|Zwracany typ EDM — funkcja|  
|Agregowanie|Boolean|Nie|False|Wartość true, jeśli funkcja znajduje się funkcja agregująca|  
|BuiltIn|Boolean|Nie|Prawda|Wartość true, jeśli funkcja jest wbudowana w magazynie danych|  
|StoreFunctionName|String|Nie|\<Nazwa >|Nazwa funkcji w magazynie danych.  Zezwala na poziomie przekierowywania nazwy funkcji.|  
|NiladicFunction|Boolean|Nie|False|Wartość true, jeśli funkcja nie wymaga parametrów i jest wywoływana bez parametrów|  
|Zgodność<br /><br /> Semantyka|ParameterSemantics|Nie|AllowImplicit<br /><br /> Konwersja|Wybór sposobu potoku zapytania powinien zająć się podstawienie typ parametru:<br /><br /> -ExactMatchOnly<br />-AllowImplicitPromotion<br />-AllowImplicitConversion|  
  
 **Parametry węzła**  
  
 Każda funkcja ma zbiór jednego lub więcej węzłów parametrów.  
  
|Nazwa atrybutu|Typ danych|Wymagane|Wartość domyślna|Opis|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|Nazwa|String|Tak|n/d|Identyfikator/nazwę parametru.|  
|Typ|String|Tak|n/d|Typ EDM parametru.|  
|Tryb|Parametr<br /><br /> Kierunek|Tak|n/d|Kierunek parametru:<br /><br /> -w<br />-out<br />-inout|  
  
##### <a name="namespace-attribute"></a>Atrybut Namespace  
 Każdy dostawca magazynu danych, należy zdefiniować przestrzeni nazw lub grupy w przestrzeni nazw dla informacje zdefiniowane w manifeście. Ta przestrzeń nazw może służyć w zapytań jednostki SQL do rozpoznawania nazw funkcji i typów. Przykład: SqlServer. Przestrzeń nazw musi się różnić od canonical przestrzeni nazw, EDM, zdefiniowane przez jednostki Services na potrzeby standardowych funkcji są obsługiwane przez zapytania SQL jednostki.  
  
## <a name="see-also"></a>Zobacz także
- [Pisanie dostawcy danych programu Entity Framework](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
