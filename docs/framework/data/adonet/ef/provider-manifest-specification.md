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
# <a name="provider-manifest-specification"></a><span data-ttu-id="244cf-102">Specyfikacja manifestu dostawcy</span><span class="sxs-lookup"><span data-stu-id="244cf-102">Provider Manifest Specification</span></span>
<span data-ttu-id="244cf-103">W tej sekcji omówiono sposób, w jaki dostawca magazynu danych może obsługiwać typy i funkcje w magazynie danych.</span><span class="sxs-lookup"><span data-stu-id="244cf-103">This section discusses how a data store provider can support the types and functions in the data store.</span></span>  
  
 <span data-ttu-id="244cf-104">Usługi jednostek działają niezależnie od określonego dostawcy magazynu danych, ale nadal umożliwia dostawcy danych jawne zdefiniowanie interakcji modeli, mapowań i zapytań z podstawowym magazynem danych.</span><span class="sxs-lookup"><span data-stu-id="244cf-104">Entity Services operates independently of a specific data store provider yet still allows a data provider to explicitly define how models, mappings, and queries interact with an underlying data store.</span></span> <span data-ttu-id="244cf-105">Bez warstwy abstrakcji usługi encji mogą być kierowane tylko do określonego magazynu danych lub dostawcy danych.</span><span class="sxs-lookup"><span data-stu-id="244cf-105">Without a layer of abstraction, Entity Services could only be targeted at a specific data store or data provider.</span></span>  
  
 <span data-ttu-id="244cf-106">Typy obsługiwane przez dostawcę są bezpośrednio lub pośrednio obsługiwane przez podstawową bazę danych.</span><span class="sxs-lookup"><span data-stu-id="244cf-106">Types that the provider supports are directly or indirectly supported by the underlying database.</span></span> <span data-ttu-id="244cf-107">Te typy nie są koniecznie dokładne typy magazynu, ale typy, których dostawca używa do obsługi entity framework.</span><span class="sxs-lookup"><span data-stu-id="244cf-107">These types are not necessarily the exact store types, but the types the provider uses to support the Entity Framework.</span></span> <span data-ttu-id="244cf-108">Typy dostawcy/magazynu są opisane w warunkach modelu danych jednostki (EDM).</span><span class="sxs-lookup"><span data-stu-id="244cf-108">Provider/store types are described in the Entity Data Model (EDM) terms.</span></span>  
  
 <span data-ttu-id="244cf-109">Typy parametrów i zwracanych dla funkcji obsługiwanych przez magazyn danych są określone w warunkach EDM.</span><span class="sxs-lookup"><span data-stu-id="244cf-109">Parameter and return types for the functions supported by the data store are specified in EDM terms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="244cf-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="244cf-110">Requirements</span></span>  
 <span data-ttu-id="244cf-111">Entity Framework i magazynu danych muszą mieć możliwość przekazywania danych tam iz powrotem w znanych typów bez utraty danych lub obcinania.</span><span class="sxs-lookup"><span data-stu-id="244cf-111">The Entity Framework and the data store need to be able to pass data back and forth in known types without any data loss or truncation.</span></span>  
  
 <span data-ttu-id="244cf-112">Manifest dostawcy musi być ładowany przez narzędzia w czasie projektowania bez konieczności otwierania połączenia z magazynem danych.</span><span class="sxs-lookup"><span data-stu-id="244cf-112">The provider manifest must be loadable by tools at design time without having to open a connection to the data store.</span></span>  
  
 <span data-ttu-id="244cf-113">W ramach jednostki rozróżniana jest wielkość liter, ale podstawowy magazyn danych może nie być.</span><span class="sxs-lookup"><span data-stu-id="244cf-113">The Entity Framework is case sensitive, but the underlying data store may not be.</span></span> <span data-ttu-id="244cf-114">Gdy artefakty EDM (identyfikatory i nazwy typów, na przykład) są zdefiniowane i używane w manifeście, muszą używać czułości wielkości liter entity framework.</span><span class="sxs-lookup"><span data-stu-id="244cf-114">When EDM artifacts (identifiers and type names, for example) are defined and used in the manifest, they must use the Entity Framework case sensitivity.</span></span> <span data-ttu-id="244cf-115">Jeśli elementy magazynu danych, które mogą być rozróżniane wielkość liter pojawiają się w manifeście dostawcy, że wielkość liter musi być obsługiwana w manifeście dostawcy.</span><span class="sxs-lookup"><span data-stu-id="244cf-115">If data store elements that may be case sensitive appear in the provider manifest, that casing needs to be maintained in the provider manifest.</span></span>  
  
 <span data-ttu-id="244cf-116">Entity Framework wymaga manifestu dostawcy dla wszystkich dostawców danych.</span><span class="sxs-lookup"><span data-stu-id="244cf-116">The Entity Framework requires a provider manifest for all data providers.</span></span> <span data-ttu-id="244cf-117">Jeśli spróbujesz użyć dostawcy, który nie ma manifestu dostawcy z entity framework, pojawi się błąd.</span><span class="sxs-lookup"><span data-stu-id="244cf-117">If you try to use a provider that does not have a provider manifest with the Entity Framework, you will get an error.</span></span>  
  
 <span data-ttu-id="244cf-118">W poniższej tabeli opisano rodzaje wyjątków, które struktura jednostek zgłaszałaby, gdy wyjątki powstają za pośrednictwem interakcji z dostawcą:</span><span class="sxs-lookup"><span data-stu-id="244cf-118">The following table describes the kinds of exceptions the Entity Framework would throw when exceptions arise through provider interaction:</span></span>  
  
|<span data-ttu-id="244cf-119">Problem</span><span class="sxs-lookup"><span data-stu-id="244cf-119">Issue</span></span>|<span data-ttu-id="244cf-120">Wyjątek</span><span class="sxs-lookup"><span data-stu-id="244cf-120">Exception</span></span>|  
|-----------|---------------|  
|<span data-ttu-id="244cf-121">Dostawca nie obsługuje GetProviderManifest w DbProviderServices.</span><span class="sxs-lookup"><span data-stu-id="244cf-121">The Provider does not support GetProviderManifest in DbProviderServices.</span></span>|<span data-ttu-id="244cf-122">Providerincompatibleexception</span><span class="sxs-lookup"><span data-stu-id="244cf-122">ProviderIncompatibleException</span></span>|  
|<span data-ttu-id="244cf-123">Brak oczywistego dostawcy: `null` dostawca zwraca podczas próby pobrania manifestu dostawcy.</span><span class="sxs-lookup"><span data-stu-id="244cf-123">Missing provider manifest: the provider returns `null` when attempting to retrieve the provider manifest.</span></span>|<span data-ttu-id="244cf-124">Providerincompatibleexception</span><span class="sxs-lookup"><span data-stu-id="244cf-124">ProviderIncompatibleException</span></span>|  
|<span data-ttu-id="244cf-125">Nieprawidłowy manifest dostawcy: dostawca zwraca nieprawidłowy kod XML podczas próby pobrania manifestu dostawcy.</span><span class="sxs-lookup"><span data-stu-id="244cf-125">Invalid provider manifest: the provider returns invalid XML when attempting to retrieve the provider manifest.</span></span>|<span data-ttu-id="244cf-126">Providerincompatibleexception</span><span class="sxs-lookup"><span data-stu-id="244cf-126">ProviderIncompatibleException</span></span>|  
  
## <a name="scenarios"></a><span data-ttu-id="244cf-127">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="244cf-127">Scenarios</span></span>  
 <span data-ttu-id="244cf-128">Dostawca powinien obsługiwać następujące scenariusze:</span><span class="sxs-lookup"><span data-stu-id="244cf-128">A provider should support the following scenarios:</span></span>  
  
### <a name="writing-a-provider-with-symmetric-type-mapping"></a><span data-ttu-id="244cf-129">Pisanie dostawcy za pomocą mapowania typów symetrycznych</span><span class="sxs-lookup"><span data-stu-id="244cf-129">Writing a Provider with Symmetric Type Mapping</span></span>  
 <span data-ttu-id="244cf-130">Można napisać dostawcę dla entity framework, gdzie każdy typ magazynu mapuje do jednego typu EDM, niezależnie od kierunku mapowania.</span><span class="sxs-lookup"><span data-stu-id="244cf-130">You can write a provider for the Entity Framework where each store type maps to a single EDM type, regardless of the mapping direction.</span></span> <span data-ttu-id="244cf-131">Dla typu dostawcy, który ma bardzo proste mapowanie, które odpowiada typowi EDM, można użyć rozwiązania symetrycznego, ponieważ system typów jest prosty lub pasuje do typów EDM.</span><span class="sxs-lookup"><span data-stu-id="244cf-131">For a provider type that has very simple mapping that corresponds with an EDM type, you can use a symmetric solution because the type system is simple or matches EDM types.</span></span>  
  
 <span data-ttu-id="244cf-132">Można użyć prostoty ich domeny i utworzyć statyczny manifest dostawcy deklaratywnego.</span><span class="sxs-lookup"><span data-stu-id="244cf-132">You can use the simplicity of their domain and produce a static declarative provider manifest.</span></span>  
  
 <span data-ttu-id="244cf-133">Piszesz plik XML, który ma dwie sekcje:</span><span class="sxs-lookup"><span data-stu-id="244cf-133">You write an XML file that has two sections:</span></span>  
  
- <span data-ttu-id="244cf-134">Lista typów dostawców wyrażona w kategoriach "odpowiednika EDM" typu sklepu lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="244cf-134">A list of provider types expressed in terms of the "EDM counterpart" of a store type or function.</span></span> <span data-ttu-id="244cf-135">Typy sklepów mają odpowiednik typów EDM.</span><span class="sxs-lookup"><span data-stu-id="244cf-135">Store types have counterpart EDM types.</span></span> <span data-ttu-id="244cf-136">Funkcje sklepu mają odpowiednie funkcje EDM.</span><span class="sxs-lookup"><span data-stu-id="244cf-136">Store functions have corresponding EDM functions.</span></span> <span data-ttu-id="244cf-137">Na przykład varchar jest typem programu SQL Server, ale odpowiedni typ EDM to ciąg.</span><span class="sxs-lookup"><span data-stu-id="244cf-137">For example, varchar is a SQL Server type but the corresponding EDM type is string.</span></span>  
  
- <span data-ttu-id="244cf-138">Lista funkcji obsługiwanych przez dostawcę, gdzie typy parametrów i zwracanych są wyrażone w warunkach EDM.</span><span class="sxs-lookup"><span data-stu-id="244cf-138">A list of functions supported by the provider where parameter and return types are expressed in EDM terms.</span></span>  
  
### <a name="writing-a-provider-with-asymmetric-type-mapping"></a><span data-ttu-id="244cf-139">Pisanie dostawcy za pomocą mapowania typów asymetrycznych</span><span class="sxs-lookup"><span data-stu-id="244cf-139">Writing a Provider with Asymmetric Type Mapping</span></span>  
 <span data-ttu-id="244cf-140">Podczas zapisywania dostawcy magazynu danych dla entity framework mapowanie typu EDM-to-provider dla niektórych typów może się różnić od mapowania typu dostawcy do EDM.</span><span class="sxs-lookup"><span data-stu-id="244cf-140">When writing a data store provider for the Entity Framework, the EDM-to-provider type mapping for some types may be different from provider-to-EDM type mapping.</span></span> <span data-ttu-id="244cf-141">Na przykład niezwiązany EDM PrimitiveTypeKind.String może mapować do nvarchar(4000) w dostawcy, podczas gdy nvarchar(4000) mapuje do EDM PrimitiveTypeKind.String(MaxLength=4000).</span><span class="sxs-lookup"><span data-stu-id="244cf-141">For instance, unbounded EDM PrimitiveTypeKind.String may map to nvarchar(4000) on the provider, while nvarchar(4000) maps to the EDM PrimitiveTypeKind.String(MaxLength=4000).</span></span>  
  
 <span data-ttu-id="244cf-142">Piszesz plik XML, który ma dwie sekcje:</span><span class="sxs-lookup"><span data-stu-id="244cf-142">You write an XML file that has two sections:</span></span>  
  
- <span data-ttu-id="244cf-143">Lista typów dostawców wyrażona w warunkach EDM i definiowanie mapowania dla obu kierunków: EDM-to-provider i provider-to-EDM.</span><span class="sxs-lookup"><span data-stu-id="244cf-143">A list of provider types expressed in EDM terms and define mapping for both direction: EDM-to-provider and provider-to-EDM.</span></span>  
  
- <span data-ttu-id="244cf-144">Lista funkcji obsługiwanych przez dostawcę, gdzie typy parametrów i zwracanych są wyrażone w warunkach EDM.</span><span class="sxs-lookup"><span data-stu-id="244cf-144">A list of functions supported by the provider where parameter and return types are expressed in EDM terms.</span></span>  
  
## <a name="provider-manifest-discoverability"></a><span data-ttu-id="244cf-145">Wykrywalność manifestu dostawcy</span><span class="sxs-lookup"><span data-stu-id="244cf-145">Provider Manifest Discoverability</span></span>  
 <span data-ttu-id="244cf-146">Manifest jest używany pośrednio przez kilka typów składników w usługach encji (na przykład Narzędzia lub kwerenda), ale bardziej bezpośrednio wykorzystywane przez metadane za pomocą modułu ładującego metadane magazynu danych.</span><span class="sxs-lookup"><span data-stu-id="244cf-146">The manifest is used indirectly by several component types in Entity Services (for example Tools or Query) but more directly leveraged by metadata through the use of the data store metadata loader.</span></span>  
  
 <span data-ttu-id="244cf-147">![dfb3d02b&#45;7a8c&#45;4d51&#45;ac5a&#45;a73d8aa145e6](./media/dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6.gif "dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6")</span><span class="sxs-lookup"><span data-stu-id="244cf-147">![dfb3d02b&#45;7a8c&#45;4d51&#45;ac5a&#45;a73d8aa145e6](./media/dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6.gif "dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6")</span></span>  
  
 <span data-ttu-id="244cf-148">Jednak dany dostawca może obsługiwać różne sklepy lub różne wersje tego samego sklepu.</span><span class="sxs-lookup"><span data-stu-id="244cf-148">However, a given provider may support different stores or different versions of the same store.</span></span> <span data-ttu-id="244cf-149">W związku z tym dostawca musi zgłosić inny manifest dla każdego obsługiwanego magazynu danych.</span><span class="sxs-lookup"><span data-stu-id="244cf-149">Therefore, a provider must report a different manifest for each supported data store.</span></span>  
  
### <a name="provider-manifest-token"></a><span data-ttu-id="244cf-150">Token manifestu dostawcy</span><span class="sxs-lookup"><span data-stu-id="244cf-150">Provider Manifest Token</span></span>  
 <span data-ttu-id="244cf-151">Po otwarciu połączenia magazynu danych dostawca może wysyłać zapytania o informacje, aby zwrócić odpowiedni manifest.</span><span class="sxs-lookup"><span data-stu-id="244cf-151">When a data store connection is opened, the provider can query for information to return the right manifest.</span></span> <span data-ttu-id="244cf-152">Może to nie być możliwe w scenariuszach offline, w których informacje o połączeniu nie są dostępne lub gdy nie można połączyć się ze sklepem.</span><span class="sxs-lookup"><span data-stu-id="244cf-152">This may not be possible in offline scenarios where connection information is not available or when it is not possible to connect to the store.</span></span> <span data-ttu-id="244cf-153">Zidentyfikuj `ProviderManifestToken` manifest przy `Schema` użyciu atrybutu elementu w pliku .ssdl.</span><span class="sxs-lookup"><span data-stu-id="244cf-153">Identify the manifest by using the `ProviderManifestToken` attribute of the `Schema` element in the .ssdl file.</span></span> <span data-ttu-id="244cf-154">Nie ma wymaganego formatu dla tego atrybutu; dostawca wybiera minimalne informacje potrzebne do identyfikacji manifestu bez otwierania połączenia ze sklepem.</span><span class="sxs-lookup"><span data-stu-id="244cf-154">There is no required format for this attribute; the provider chooses the minimum information needed to identify a manifest without opening a connection to the store.</span></span>  
  
 <span data-ttu-id="244cf-155">Przykład:</span><span class="sxs-lookup"><span data-stu-id="244cf-155">For example:</span></span>  
  
```xml  
<Schema Namespace="Northwind" Provider="System.Data.SqlClient" ProviderManifestToken="2005" xmlns:edm="http://schemas.microsoft.com/ado/2006/04/edm/ssdl" xmlns="http://schemas.microsoft.com/ado/2006/04/edm/ssdl">  
```  
  
## <a name="provider-manifest-programming-model"></a><span data-ttu-id="244cf-156">Model programowania manifestu dostawcy</span><span class="sxs-lookup"><span data-stu-id="244cf-156">Provider Manifest Programming Model</span></span>  
 <span data-ttu-id="244cf-157">Dostawcy wywodzą się z <xref:System.Data.Common.DbXmlEnabledProviderManifest>, co pozwala im określić ich manifesty deklaratywnie.</span><span class="sxs-lookup"><span data-stu-id="244cf-157">Providers derive from <xref:System.Data.Common.DbXmlEnabledProviderManifest>, which allows them to specify their manifests declaratively.</span></span> <span data-ttu-id="244cf-158">Na poniższej ilustracji przedstawiono hierarchię klas dostawcy:</span><span class="sxs-lookup"><span data-stu-id="244cf-158">The following illustration shows the class hierarchy of a provider:</span></span>  
  
 <span data-ttu-id="244cf-159">![Brak](./media/d541eba3-2ee6-4cd1-88f5-89d0b2582a6c.gif "d541eba3-2ee6-4cd1-88f5-89d0b2582a6c")</span><span class="sxs-lookup"><span data-stu-id="244cf-159">![None](./media/d541eba3-2ee6-4cd1-88f5-89d0b2582a6c.gif "d541eba3-2ee6-4cd1-88f5-89d0b2582a6c")</span></span>  
  
### <a name="discoverability-api"></a><span data-ttu-id="244cf-160">Interfejs API wykrywania</span><span class="sxs-lookup"><span data-stu-id="244cf-160">Discoverability API</span></span>  
 <span data-ttu-id="244cf-161">Manifest dostawcy jest ładowany przez program ładujący metadane magazynu (StoreItemCollection), przy użyciu połączenia magazynu danych lub tokenu manifestu dostawcy.</span><span class="sxs-lookup"><span data-stu-id="244cf-161">The provider manifest is loaded by the Store Metadata loader (StoreItemCollection), either by using a data store connection or a provider manifest token.</span></span>  
  
#### <a name="using-a-data-store-connection"></a><span data-ttu-id="244cf-162">Korzystanie z połączenia magazynu danych</span><span class="sxs-lookup"><span data-stu-id="244cf-162">Using a Data Store Connection</span></span>  
 <span data-ttu-id="244cf-163">Gdy połączenie magazynu danych jest <xref:System.Data.Common.DbProviderServices.GetProviderManifestToken%2A?displayProperty=nameWithType> dostępne, wywołanie zwrócenia <xref:System.Data.Common.DbProviderServices.GetProviderManifest%2A> tokenu, <xref:System.Data.Common.DbProviderManifest>który jest przekazywany do metody, która zwraca .</span><span class="sxs-lookup"><span data-stu-id="244cf-163">When the data store connection is available, call <xref:System.Data.Common.DbProviderServices.GetProviderManifestToken%2A?displayProperty=nameWithType> to return the token that is passed to the <xref:System.Data.Common.DbProviderServices.GetProviderManifest%2A> method, which returns <xref:System.Data.Common.DbProviderManifest>.</span></span> <span data-ttu-id="244cf-164">Ta metoda deleguje do implementacji dostawcy `GetDbProviderManifestToken`.</span><span class="sxs-lookup"><span data-stu-id="244cf-164">This method delegates to the provider's implementation of `GetDbProviderManifestToken`.</span></span>  
  
```csharp
public string GetProviderManifestToken(DbConnection connection);  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
#### <a name="using-a-provider-manifest-token"></a><span data-ttu-id="244cf-165">Korzystanie z tokenu manifestu dostawcy</span><span class="sxs-lookup"><span data-stu-id="244cf-165">Using a Provider Manifest Token</span></span>  
 <span data-ttu-id="244cf-166">W scenariuszu offline token jest pobierany z reprezentacji SSDL.</span><span class="sxs-lookup"><span data-stu-id="244cf-166">For the offline scenario, the token is picked from SSDL representation.</span></span> <span data-ttu-id="244cf-167">SSDL umożliwia określenie ProviderManifestToken (zobacz [Element schematu (SSDL), aby](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl) uzyskać więcej informacji).</span><span class="sxs-lookup"><span data-stu-id="244cf-167">The SSDL allows you to specify a ProviderManifestToken (see [Schema Element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl) for more information).</span></span> <span data-ttu-id="244cf-168">Na przykład jeśli nie można otworzyć połączenia, SSDL ma token manifestu dostawcy, który określa informacje o manifeście.</span><span class="sxs-lookup"><span data-stu-id="244cf-168">For example, if a connection cannot be opened, the SSDL has a provider manifest token that specifies information about the manifest.</span></span>  
  
```csharp
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
### <a name="provider-manifest-schema"></a><span data-ttu-id="244cf-169">Schemat manifestu dostawcy</span><span class="sxs-lookup"><span data-stu-id="244cf-169">Provider Manifest Schema</span></span>  
 <span data-ttu-id="244cf-170">Schemat informacji zdefiniowanych dla każdego dostawcy zawiera informacje statyczne, które mają być używane przez metadane:</span><span class="sxs-lookup"><span data-stu-id="244cf-170">The schema of information defined for each provider contains the static information to be consumed by metadata:</span></span>  
  
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
  
#### <a name="types-node"></a><span data-ttu-id="244cf-171">Typy węzła</span><span class="sxs-lookup"><span data-stu-id="244cf-171">Types Node</span></span>  
 <span data-ttu-id="244cf-172">Węzeł Typy w manifeście dostawcy zawiera informacje o typach, które są obsługiwane natywnie przez magazyn danych lub za pośrednictwem dostawcy.</span><span class="sxs-lookup"><span data-stu-id="244cf-172">The Types node in the provider manifest contains information about the Types that are supported natively by the data store or through the provider.</span></span>  
  
##### <a name="type-node"></a><span data-ttu-id="244cf-173">Typ węzła</span><span class="sxs-lookup"><span data-stu-id="244cf-173">Type Node</span></span>  
 <span data-ttu-id="244cf-174">Każdy węzeł typu definiuje typ dostawcy pod względem EDM.</span><span class="sxs-lookup"><span data-stu-id="244cf-174">Each Type node defines a provider type in terms of EDM.</span></span> <span data-ttu-id="244cf-175">Węzeł Typ opisuje nazwę typu dostawcy i informacje związane z typem modelu, do który jest mapowana, oraz aspekty opisujące mapowanie tego typu.</span><span class="sxs-lookup"><span data-stu-id="244cf-175">The Type node describes the name of the provider type, and information related to the model type it maps to and facets to describe that type mapping.</span></span>  
  
 <span data-ttu-id="244cf-176">Aby wyrazić informacje o tym typie w manifeście dostawcy, każda deklaracja TypeInformation musi zdefiniować kilka opisów aspektu dla każdego typu:</span><span class="sxs-lookup"><span data-stu-id="244cf-176">In order to express this type information in the provider manifest, each TypeInformation declaration must define several facet descriptions for each Type:</span></span>  
  
|<span data-ttu-id="244cf-177">Nazwa atrybutu</span><span class="sxs-lookup"><span data-stu-id="244cf-177">Attribute Name</span></span>|<span data-ttu-id="244cf-178">Typ danych</span><span class="sxs-lookup"><span data-stu-id="244cf-178">Data Type</span></span>|<span data-ttu-id="244cf-179">Wymagany</span><span class="sxs-lookup"><span data-stu-id="244cf-179">Required</span></span>|<span data-ttu-id="244cf-180">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="244cf-180">Default Value</span></span>|<span data-ttu-id="244cf-181">Opis</span><span class="sxs-lookup"><span data-stu-id="244cf-181">Description</span></span>|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|<span data-ttu-id="244cf-182">Nazwa</span><span class="sxs-lookup"><span data-stu-id="244cf-182">Name</span></span>|<span data-ttu-id="244cf-183">Ciąg</span><span class="sxs-lookup"><span data-stu-id="244cf-183">String</span></span>|<span data-ttu-id="244cf-184">Tak</span><span class="sxs-lookup"><span data-stu-id="244cf-184">Yes</span></span>|<span data-ttu-id="244cf-185">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="244cf-185">n/a</span></span>|<span data-ttu-id="244cf-186">Nazwa typu danych specyficznych dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="244cf-186">Provider-specific data type name</span></span>|  
|<span data-ttu-id="244cf-187">PrymitywTypeKind</span><span class="sxs-lookup"><span data-stu-id="244cf-187">PrimitiveTypeKind</span></span>|<span data-ttu-id="244cf-188">PrymitywTypeKind</span><span class="sxs-lookup"><span data-stu-id="244cf-188">PrimitiveTypeKind</span></span>|<span data-ttu-id="244cf-189">Tak</span><span class="sxs-lookup"><span data-stu-id="244cf-189">Yes</span></span>|<span data-ttu-id="244cf-190">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="244cf-190">n/a</span></span>|<span data-ttu-id="244cf-191">Nazwa typu EDM</span><span class="sxs-lookup"><span data-stu-id="244cf-191">EDM type name</span></span>|  
  
###### <a name="function-node"></a><span data-ttu-id="244cf-192">Węzeł funkcji</span><span class="sxs-lookup"><span data-stu-id="244cf-192">Function Node</span></span>  
 <span data-ttu-id="244cf-193">Każda funkcja definiuje jedną funkcję dostępną za pośrednictwem dostawcy.</span><span class="sxs-lookup"><span data-stu-id="244cf-193">Each Function defines a single function available through the provider.</span></span>  
  
|<span data-ttu-id="244cf-194">Nazwa atrybutu</span><span class="sxs-lookup"><span data-stu-id="244cf-194">Attribute Name</span></span>|<span data-ttu-id="244cf-195">Typ danych</span><span class="sxs-lookup"><span data-stu-id="244cf-195">Data Type</span></span>|<span data-ttu-id="244cf-196">Wymagany</span><span class="sxs-lookup"><span data-stu-id="244cf-196">Required</span></span>|<span data-ttu-id="244cf-197">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="244cf-197">Default Value</span></span>|<span data-ttu-id="244cf-198">Opis</span><span class="sxs-lookup"><span data-stu-id="244cf-198">Description</span></span>|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|<span data-ttu-id="244cf-199">Nazwa</span><span class="sxs-lookup"><span data-stu-id="244cf-199">Name</span></span>|<span data-ttu-id="244cf-200">Ciąg</span><span class="sxs-lookup"><span data-stu-id="244cf-200">String</span></span>|<span data-ttu-id="244cf-201">Tak</span><span class="sxs-lookup"><span data-stu-id="244cf-201">Yes</span></span>|<span data-ttu-id="244cf-202">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="244cf-202">n/a</span></span>|<span data-ttu-id="244cf-203">Identyfikator/nazwa funkcji</span><span class="sxs-lookup"><span data-stu-id="244cf-203">Identifier/name of the function</span></span>|  
|<span data-ttu-id="244cf-204">Returntype</span><span class="sxs-lookup"><span data-stu-id="244cf-204">ReturnType</span></span>|<span data-ttu-id="244cf-205">Ciąg</span><span class="sxs-lookup"><span data-stu-id="244cf-205">String</span></span>|<span data-ttu-id="244cf-206">Nie</span><span class="sxs-lookup"><span data-stu-id="244cf-206">No</span></span>|<span data-ttu-id="244cf-207">Void</span><span class="sxs-lookup"><span data-stu-id="244cf-207">Void</span></span>|<span data-ttu-id="244cf-208">Typ zwracany EDM funkcji</span><span class="sxs-lookup"><span data-stu-id="244cf-208">The EDM return type of the function</span></span>|  
|<span data-ttu-id="244cf-209">Agregacja</span><span class="sxs-lookup"><span data-stu-id="244cf-209">Aggregate</span></span>|<span data-ttu-id="244cf-210">Wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="244cf-210">Boolean</span></span>|<span data-ttu-id="244cf-211">Nie</span><span class="sxs-lookup"><span data-stu-id="244cf-211">No</span></span>|<span data-ttu-id="244cf-212">False</span><span class="sxs-lookup"><span data-stu-id="244cf-212">False</span></span>|<span data-ttu-id="244cf-213">Wartość true, jeśli funkcja jest funkcją agregującą</span><span class="sxs-lookup"><span data-stu-id="244cf-213">True if the function is an aggregate function</span></span>|  
|<span data-ttu-id="244cf-214">Wbudowane</span><span class="sxs-lookup"><span data-stu-id="244cf-214">BuiltIn</span></span>|<span data-ttu-id="244cf-215">Wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="244cf-215">Boolean</span></span>|<span data-ttu-id="244cf-216">Nie</span><span class="sxs-lookup"><span data-stu-id="244cf-216">No</span></span>|<span data-ttu-id="244cf-217">True</span><span class="sxs-lookup"><span data-stu-id="244cf-217">True</span></span>|<span data-ttu-id="244cf-218">Wartość true, jeśli funkcja jest wbudowana w magazyn danych</span><span class="sxs-lookup"><span data-stu-id="244cf-218">True if the function is built into the data store</span></span>|  
|<span data-ttu-id="244cf-219">Nazwa magazynu</span><span class="sxs-lookup"><span data-stu-id="244cf-219">StoreFunctionName</span></span>|<span data-ttu-id="244cf-220">Ciąg</span><span class="sxs-lookup"><span data-stu-id="244cf-220">String</span></span>|<span data-ttu-id="244cf-221">Nie</span><span class="sxs-lookup"><span data-stu-id="244cf-221">No</span></span>|<span data-ttu-id="244cf-222">\<Nazwa></span><span class="sxs-lookup"><span data-stu-id="244cf-222">\<Name></span></span>|<span data-ttu-id="244cf-223">Nazwa funkcji w magazynie danych.</span><span class="sxs-lookup"><span data-stu-id="244cf-223">Function Name in the data store.</span></span>  <span data-ttu-id="244cf-224">Pozwala na poziom przekierowania nazw funkcji.</span><span class="sxs-lookup"><span data-stu-id="244cf-224">Allows for a level of redirection of function names.</span></span>|  
|<span data-ttu-id="244cf-225">Funkcja Niladic</span><span class="sxs-lookup"><span data-stu-id="244cf-225">NiladicFunction</span></span>|<span data-ttu-id="244cf-226">Wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="244cf-226">Boolean</span></span>|<span data-ttu-id="244cf-227">Nie</span><span class="sxs-lookup"><span data-stu-id="244cf-227">No</span></span>|<span data-ttu-id="244cf-228">False</span><span class="sxs-lookup"><span data-stu-id="244cf-228">False</span></span>|<span data-ttu-id="244cf-229">Prawda, jeśli funkcja nie wymaga parametrów i jest wywoływana bez żadnych parametrów</span><span class="sxs-lookup"><span data-stu-id="244cf-229">True if the function does not require parameters and is called without any parameters</span></span>|  
|<span data-ttu-id="244cf-230">Parametertype</span><span class="sxs-lookup"><span data-stu-id="244cf-230">ParameterType</span></span><br /><br /> <span data-ttu-id="244cf-231">Semantyka</span><span class="sxs-lookup"><span data-stu-id="244cf-231">Semantics</span></span>|<span data-ttu-id="244cf-232">ParametrSemantyka</span><span class="sxs-lookup"><span data-stu-id="244cf-232">ParameterSemantics</span></span>|<span data-ttu-id="244cf-233">Nie</span><span class="sxs-lookup"><span data-stu-id="244cf-233">No</span></span>|<span data-ttu-id="244cf-234">Zezwalaj Na Implikowanie</span><span class="sxs-lookup"><span data-stu-id="244cf-234">AllowImplicit</span></span><br /><br /> <span data-ttu-id="244cf-235">Konwersja</span><span class="sxs-lookup"><span data-stu-id="244cf-235">Conversion</span></span>|<span data-ttu-id="244cf-236">Wybór sposobu, w jaki potok zapytań powinien radzić sobie z podstawianiam typu parametrów:</span><span class="sxs-lookup"><span data-stu-id="244cf-236">Choice of how the query pipeline should deal with parameter type substitution:</span></span><br /><br /> <span data-ttu-id="244cf-237">- ExactMatchOnly</span><span class="sxs-lookup"><span data-stu-id="244cf-237">-   ExactMatchOnly</span></span><br /><span data-ttu-id="244cf-238">- AllowImplicitPromotion</span><span class="sxs-lookup"><span data-stu-id="244cf-238">-   AllowImplicitPromotion</span></span><br /><span data-ttu-id="244cf-239">- AllowImplicitConversion</span><span class="sxs-lookup"><span data-stu-id="244cf-239">-   AllowImplicitConversion</span></span>|  
  
 <span data-ttu-id="244cf-240">**Węzeł parametrów**</span><span class="sxs-lookup"><span data-stu-id="244cf-240">**Parameters Node**</span></span>  
  
 <span data-ttu-id="244cf-241">Każda funkcja ma kolekcję jednego lub więcej węzłów parametrów.</span><span class="sxs-lookup"><span data-stu-id="244cf-241">Each function has a collection of one or more Parameter nodes.</span></span>  
  
|<span data-ttu-id="244cf-242">Nazwa atrybutu</span><span class="sxs-lookup"><span data-stu-id="244cf-242">Attribute Name</span></span>|<span data-ttu-id="244cf-243">Typ danych</span><span class="sxs-lookup"><span data-stu-id="244cf-243">Data Type</span></span>|<span data-ttu-id="244cf-244">Wymagany</span><span class="sxs-lookup"><span data-stu-id="244cf-244">Required</span></span>|<span data-ttu-id="244cf-245">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="244cf-245">Default Value</span></span>|<span data-ttu-id="244cf-246">Opis</span><span class="sxs-lookup"><span data-stu-id="244cf-246">Description</span></span>|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|<span data-ttu-id="244cf-247">Nazwa</span><span class="sxs-lookup"><span data-stu-id="244cf-247">Name</span></span>|<span data-ttu-id="244cf-248">Ciąg</span><span class="sxs-lookup"><span data-stu-id="244cf-248">String</span></span>|<span data-ttu-id="244cf-249">Tak</span><span class="sxs-lookup"><span data-stu-id="244cf-249">Yes</span></span>|<span data-ttu-id="244cf-250">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="244cf-250">n/a</span></span>|<span data-ttu-id="244cf-251">Identyfikator/nazwa parametru.</span><span class="sxs-lookup"><span data-stu-id="244cf-251">Identifier/name of the parameter.</span></span>|  
|<span data-ttu-id="244cf-252">Typ</span><span class="sxs-lookup"><span data-stu-id="244cf-252">Type</span></span>|<span data-ttu-id="244cf-253">Ciąg</span><span class="sxs-lookup"><span data-stu-id="244cf-253">String</span></span>|<span data-ttu-id="244cf-254">Tak</span><span class="sxs-lookup"><span data-stu-id="244cf-254">Yes</span></span>|<span data-ttu-id="244cf-255">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="244cf-255">n/a</span></span>|<span data-ttu-id="244cf-256">Typ EDM parametru.</span><span class="sxs-lookup"><span data-stu-id="244cf-256">The EDM type of the parameter.</span></span>|  
|<span data-ttu-id="244cf-257">Tryb</span><span class="sxs-lookup"><span data-stu-id="244cf-257">Mode</span></span>|<span data-ttu-id="244cf-258">Parametr</span><span class="sxs-lookup"><span data-stu-id="244cf-258">Parameter</span></span><br /><br /> <span data-ttu-id="244cf-259">Kierunek</span><span class="sxs-lookup"><span data-stu-id="244cf-259">Direction</span></span>|<span data-ttu-id="244cf-260">Tak</span><span class="sxs-lookup"><span data-stu-id="244cf-260">Yes</span></span>|<span data-ttu-id="244cf-261">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="244cf-261">n/a</span></span>|<span data-ttu-id="244cf-262">Kierunek parametru:</span><span class="sxs-lookup"><span data-stu-id="244cf-262">Direction of parameter:</span></span><br /><br /> <span data-ttu-id="244cf-263">- w</span><span class="sxs-lookup"><span data-stu-id="244cf-263">-   in</span></span><br /><span data-ttu-id="244cf-264">- na zewnątrz</span><span class="sxs-lookup"><span data-stu-id="244cf-264">-   out</span></span><br /><span data-ttu-id="244cf-265">- inout</span><span class="sxs-lookup"><span data-stu-id="244cf-265">-   inout</span></span>|  
  
##### <a name="namespace-attribute"></a><span data-ttu-id="244cf-266">Atrybut obszaru nazw</span><span class="sxs-lookup"><span data-stu-id="244cf-266">Namespace Attribute</span></span>  
 <span data-ttu-id="244cf-267">Każdy dostawca magazynu danych musi zdefiniować obszar nazw lub grupę obszarów nazw dla informacji zdefiniowanych w manifeście.</span><span class="sxs-lookup"><span data-stu-id="244cf-267">Each data store provider must define a namespace or group of namespaces for information defined in the manifest.</span></span> <span data-ttu-id="244cf-268">Ten obszar nazw może służyć w kwerendach SQL encji do rozpoznawania nazw funkcji i typów.</span><span class="sxs-lookup"><span data-stu-id="244cf-268">This namespace can be used in Entity SQL queries to resolve names of functions and types.</span></span> <span data-ttu-id="244cf-269">Na przykład: SqlServer.</span><span class="sxs-lookup"><span data-stu-id="244cf-269">For instance: SqlServer.</span></span> <span data-ttu-id="244cf-270">Ten obszar nazw musi się różnić od kanonicznego obszaru nazw EDM, zdefiniowanego przez usługi encji dla standardowych funkcji, które mają być obsługiwane przez zapytania SQL jednostki.</span><span class="sxs-lookup"><span data-stu-id="244cf-270">That namespace must be different from the canonical namespace, EDM, defined by Entity Services for standard functions to be supported by Entity SQL queries.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="244cf-271">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="244cf-271">See also</span></span>

- [<span data-ttu-id="244cf-272">Pisanie dostawcy danych programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="244cf-272">Writing an Entity Framework Data Provider</span></span>](writing-an-ef-data-provider.md)
