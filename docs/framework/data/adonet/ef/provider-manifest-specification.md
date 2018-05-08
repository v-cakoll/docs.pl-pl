---
title: Specyfikacja manifestu dostawcy
ms.date: 03/30/2017
ms.assetid: bb450b47-8951-4f99-9350-26f05a4d4e46
ms.openlocfilehash: 02faee9ad69bd75f4df608b9a4767560945c7bb3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="provider-manifest-specification"></a>Specyfikacja manifestu dostawcy
W tej sekcji omówiono sposób dostawcy magazynu danych może obsługiwać typy i funkcje w magazynie danych.  
  
 Jednostki usługi działa niezależnie od danych specyficznych dla dostawcy magazynu, ale nadal umożliwia dostawcy danych oznaczyć interakcje modele, mapowania i zapytania z odpowiedni magazyn danych. Bez warstwę abstrakcji jednostki usługi tylko może być wskazywane na określonej w magazynie danych lub dostawcy danych.  
  
 Typy obsługiwane przez dostawcę są bezpośrednio lub pośrednio obsługiwane przez podstawowej bazy danych. Te typy nie są niekoniecznie typów magazynów dokładne, ale typy, dostawca używa do obsługi [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Opisano typy dostawcy/store względem modelu danych jednostki (EDM).  
  
 Parametr i zwracane typy dla funkcje obsługiwane przez Magazyn danych są określone w warunkach EDM.  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] i magazynu danych muszą mieć możliwość przekazywania danych i z powrotem w znanych typów bez utraty danych lub obcięcie.  
  
 Manifest dostawcy musi istnieć możliwość załadowania przez narzędzia w czasie projektowania, bez konieczności otwierania połączenia z magazynem danych.  
  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Rozróżniana jest wielkość liter, ale nie może być odpowiedni magazyn danych. Gdy artefakty EDM (identyfikatorów i nazw typu, na przykład) są zdefiniowane i używane w manifeście, należy użyć [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] wielkość liter. Jeśli elementy magazynu danych, które mogą być uwzględniana wielkość liter są wyświetlane w manifeście dostawcy, wielkość liter w tym musi być obsługiwany w manifeście dostawcy.  
  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Wymaga manifestu dostawcy dla wszystkich dostawców danych. Jeśli spróbujesz użyć dostawcy, który nie ma dostawcy manifestu z [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], wystąpi błąd.  
  
 W poniższej tabeli opisano typy wyjątków [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] spowoduje zgłoszenie, gdy wyjątki wynikać interakcję dostawcy:  
  
|Problem|Wyjątek|  
|-----------|---------------|  
|Dostawca nie obsługuje GetProviderManifest w DbProviderServices.|ProviderIncompatibleException|  
|Brak manifestu dostawcy: dostawca zwraca `null` podczas próby pobrania manifestu dostawcy.|ProviderIncompatibleException|  
|Nieprawidłowy dostawca manifestu: dostawca zwraca nieprawidłowy kod XML, podczas próby pobrania manifestu dostawcy.|ProviderIncompatibleException|  
  
## <a name="scenarios"></a>Scenariusze  
 Dostawca powinien obsługuje następujące scenariusze:  
  
### <a name="writing-a-provider-with-symmetric-type-mapping"></a>Pisanie dostawcy z mapowania typu symetryczne  
 Można napisać dostawcę dla [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] gdzie mapuje każdego typu magazynu do jednego typu EDM, niezależnie od kierunku mapowania. Za pomocą symetrycznego rozwiązania, ponieważ system typu prostego lub odpowiada typów EDM dla typu dostawcy, który znajduje się bardzo proste mapowanie odpowiada z typem EDM.  
  
 Można użyć prostotę ich domeny i tworzenia manifestu dostawcy deklaratywne statycznych.  
  
 Możesz zapisać plik XML, który ma dwie sekcje:  
  
-   Lista typów dostawcy wyrażony w postaci "EDM odpowiednikiem" typ magazynu lub funkcji. Typy magazynu mają odpowiednika typów EDM. Funkcje magazynu ma odpowiednie funkcje EDM. Na przykład varchar jest typem programu SQL Server, ale odpowiedni typ modelu EDM jest ciągiem.  
  
-   Lista funkcje obsługiwane przez dostawcę, gdzie parametr i zwracane typy są wyrażone według warunków EDM.  
  
### <a name="writing-a-provider-with-asymmetric-type-mapping"></a>Pisanie dostawcy z mapowaniem asymetryczne  
 Podczas zapisywania danych dostawcy magazynu dla [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], typ EDM do dostawcy mapowania dla niektórych typów może być inny niż typ dostawcy do EDM mapowania. Na przykład niepowiązany PrimitiveTypeKind.String EDM mogą być mapowane do nvarchar(4000) w dostawcy podczas nvarchar(4000) mapuje EDM PrimitiveTypeKind.String(MaxLength=4000).  
  
 Możesz zapisać plik XML, który ma dwie sekcje:  
  
-   Lista typów dostawcy wyrażoną EDM i zdefiniować mapowanie dla obu kierunku: EDM do dostawcy i dostawcy do EDM.  
  
-   Lista funkcje obsługiwane przez dostawcę, gdzie parametr i zwracane typy są wyrażone według warunków EDM.  
  
## <a name="provider-manifest-discoverability"></a>Dostawca odnajdywania manifestu  
 Manifest jest pośrednio używana przez kilka typów składników w usługach jednostki (na przykład narzędzia lub zapytanie), ale więcej bezpośrednio wykorzystywane przez metadanych przy użyciu danych przechowywane metadane modułu ładującego.  
  
 ![dfb3d02b&#45;7a8c&#45;4d51&#45;ac5a&#45;a73d8aa145e6](../../../../../docs/framework/data/adonet/ef/media/dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6.gif "dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6")  
  
 Jednak danego dostawcy mogą obsługiwać sklepach lub różne wersje tego samego magazynu. W związku z tym dostawcą muszą zgłosić różnych manifestu dla każdego sklepu obsługiwane dane.  
  
### <a name="provider-manifest-token"></a>Token manifestu dostawcy  
 Po otwarciu połączenia magazynu danych dostawcy można wyszukiwać informacje do zwrócenia prawo manifestu. To nie można w trybie offline scenariuszach gdy nie są dostępne informacje o połączeniu lub gdy nie jest możliwe nawiązanie połączenia ze sklepem. Identyfikowanie manifest przy użyciu `ProviderManifestToken` atrybutu `Schema` elementu w pliku ssdl. Brak ma wymaganego formatu dla tego atrybutu; Dostawca wybiera minimalne informacje potrzebne do identyfikowania manifestu bez konieczności otwierania połączenia z magazynem.  
  
 Na przykład:  
  
```xml  
<Schema Namespace="Northwind" Provider="System.Data.SqlClient" ProviderManifestToken="2005" xmlns:edm="http://schemas.microsoft.com/ado/2006/04/edm/ssdl" xmlns="http://schemas.microsoft.com/ado/2006/04/edm/ssdl">  
```  
  
## <a name="provider-manifest-programming-model"></a>Model programowania manifestu dostawcy  
 Dostawcy pochodzić od <xref:System.Data.Common.DbXmlEnabledProviderManifest>, dzięki czemu do określania manifestów, ich deklaratywnie. Na poniższej ilustracji przedstawiono hierarchii klas dostawcy:  
  
 ![None](../../../../../docs/framework/data/adonet/ef/media/d541eba3-2ee6-4cd1-88f5-89d0b2582a6c.gif "d541eba3-2ee6-4cd1-88f5-89d0b2582a6c")  
  
### <a name="discoverability-api"></a>Odnajdowanie interfejsu API  
 Manifest dostawcy jest ładowany przez moduł ładujący przechowywania metadanych (StoreItemCollection), przy użyciu danych przechowywania połączenia i tokenu manifestu dostawcy.  
  
#### <a name="using-a-data-store-connection"></a>Za pomocą połączenia magazynu danych  
 Przechowywania danych jest dostępne połączenie, wywołaj DbProvderServices.GetProviderManifestToken, aby zwrócić token, który jest przekazywany do metody GetProviderManifest, która zwraca DbProviderManifest. Ta metoda deleguje do implementacji dostawcy GetDbProviderManifestToken.  
  
```  
public string GetProviderManifestToken(DbConnection connection);  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
#### <a name="using-a-provider-manifest-token"></a>Za pomocą tokenu manifestu dostawcy  
 W scenariuszu w trybie offline token jest pobierany z reprezentacji pliku SSDL. Plik SSDL pozwala na określenie ProviderManifestToken (zobacz [elementu schematu (SSDL)](http://msdn.microsoft.com/library/fec75ae4-7f16-4421-9265-9dac61509222) Aby uzyskać więcej informacji). Na przykład jeśli nie można otworzyć połączenia, pliku SSDL ma token manifestu dostawcy, który określa informacje o manifeście.  
  
```  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
### <a name="provider-manifest-schema"></a>Schematu manifestu dostawcy  
 Schemat informacje zdefiniowane dla każdego dostawcy zawiera informacje statycznych zużywanych przez metadanych:  
  
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
 Węzeł typów w manifeście dostawcy zawiera informacje o typach, które są natywnie obsługiwane przez Magazyn danych lub za pośrednictwem dostawcy.  
  
##### <a name="type-node"></a>Typ węzła  
 Każdy węzeł typu definiuje typ dostawcy pod względem modelu EDM. Węzeł typu opisuje nazwy typu dostawcy i informacje powiązane z typ modelu, który wskazuje na i aspekty do opisywania mapowania typu.  
  
 Aby wyrazić informacje tego typu w manifeście dostawcy, każda deklaracja TypeInformation musi definiować kilka opisy aspektu dla każdego typu:  
  
|Nazwa atrybutu|Typ danych|Wymagane|Wartość domyślna|Opis|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|Nazwa|String|Tak|n/d|Nazwa typu danych specyficznych dla dostawcy|  
|PrimitiveTypeKind|PrimitiveTypeKind|Tak|n/d|Nazwa typu EDM|  
  
###### <a name="function-node"></a>Węzeł — funkcja  
 Każda funkcja definiuje jednej funkcji dostępnych za pośrednictwem dostawcy.  
  
|Nazwa atrybutu|Typ danych|Wymagane|Wartość domyślna|Opis|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|Nazwa|String|Tak|n/d|Identyfikator/nazwę funkcji|  
|Obiekt ReturnType|String|Nie|Void|Zwracany typ EDM funkcji|  
|Agregowanie|Boolean|Nie|False|Wartość true, jeśli funkcja jest funkcją agregującą|  
|Wbudowane|Boolean|Nie|True|Wartość true, jeśli funkcja jest wbudowana w magazynie danych|  
|StoreFunctionName|String|Nie|\<Nazwa >|Nazwa funkcji w magazynie danych.  Zezwala na poziomie przekierowania nazwy funkcji.|  
|NiladicFunction|Boolean|Nie|False|Wartość true, jeśli funkcja nie wymaga parametrów i jest wywoływana bez parametrów|  
|ParameterType<br /><br /> Semantyka|ParameterSemantics|Nie|AllowImplicit<br /><br /> Konwersja|Wybór sposobu potoku zapytania powinien zająć się zamienny parametr typu:<br /><br /> -ExactMatchOnly<br />-AllowImplicitPromotion<br />-AllowImplicitConversion|  
  
 **Parametry węzła**  
  
 Każda funkcja ma kolekcję co najmniej jeden węzeł parametru.  
  
|Nazwa atrybutu|Typ danych|Wymagane|Wartość domyślna|Opis|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|Nazwa|String|Tak|n/d|Identyfikator/nazwę parametru.|  
|Typ|String|Tak|n/d|Typ EDM parametru.|  
|Tryb|Parametr<br /><br /> Kierunek|Tak|n/d|Kierunek parametru:<br /><br /> -w<br />-out<br />-inout|  
  
##### <a name="namespace-attribute"></a>Atrybut Namespace  
 Każdy dostawca magazynu danych należy zdefiniować przestrzeni nazw lub grupy przestrzeni nazw dla informacje zdefiniowane w manifeście. Tej przestrzeni nazw mogą być używane w zapytaniach SQL jednostki do rozpoznawania nazw funkcji i typów. Na przykład: SqlServer. Tej przestrzeni nazw musi się różnić od nazw canonical, EDM, zdefiniowane przez usługi jednostki dla standardowe funkcje obsługiwane przez zapytania SQL jednostki.  
  
## <a name="see-also"></a>Zobacz też  
 [Pisanie dostawcy danych programu Entity Framework](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
