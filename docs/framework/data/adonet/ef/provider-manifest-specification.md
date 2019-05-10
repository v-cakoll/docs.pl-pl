---
title: Specyfikacja manifestu dostawcy
ms.date: 03/30/2017
ms.assetid: bb450b47-8951-4f99-9350-26f05a4d4e46
ms.openlocfilehash: 0f3eaa73a26c3f8519e1c168ab2e2968ed4ab28d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64641163"
---
# <a name="provider-manifest-specification"></a><span data-ttu-id="fcdcf-102">Specyfikacja manifestu dostawcy</span><span class="sxs-lookup"><span data-stu-id="fcdcf-102">Provider Manifest Specification</span></span>
<span data-ttu-id="fcdcf-103">W tej sekcji omówiono, jak dostawca magazynu danych może obsługiwać typy i funkcje w magazynie danych.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-103">This section discusses how a data store provider can support the types and functions in the data store.</span></span>  
  
 <span data-ttu-id="fcdcf-104">Jednostki usługi działa niezależnie od danych specyficznych dla dostawcy magazynu, ale nadal umożliwia jawne zdefiniowanie sposobu interakcji modeli, mapowania i kwerendy z podstawowym magazynie danych dostawcy danych.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-104">Entity Services operates independently of a specific data store provider yet still allows a data provider to explicitly define how models, mappings, and queries interact with an underlying data store.</span></span> <span data-ttu-id="fcdcf-105">Bez warstwę abstrakcji jednostki usługi może być przeznaczony tylko dla określonych danych sklepu lub Dostawca danych.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-105">Without a layer of abstraction, Entity Services could only be targeted at a specific data store or data provider.</span></span>  
  
 <span data-ttu-id="fcdcf-106">Typy obsługiwane przez dostawcę są bezpośrednio lub pośrednio obsługiwane przez podstawowej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-106">Types that the provider supports are directly or indirectly supported by the underlying database.</span></span> <span data-ttu-id="fcdcf-107">Te typy nie są zawsze typów magazynów dokładnie, ale typy dostawca używa do obsługi [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fcdcf-107">These types are not necessarily the exact store types, but the types the provider uses to support the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="fcdcf-108">W warunkach Entity Data Model (EDM) opisano typy dostawcy/magazynowania.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-108">Provider/store types are described in the Entity Data Model (EDM) terms.</span></span>  
  
 <span data-ttu-id="fcdcf-109">Typy parametrów i zwrotu w funkcji obsługiwanych przez Magazyn danych są określone w postanowieniach EDM.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-109">Parameter and return types for the functions supported by the data store are specified in EDM terms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcdcf-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fcdcf-110">Requirements</span></span>  
 <span data-ttu-id="fcdcf-111">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] i magazynu danych muszą mieć możliwość przekazywania danych i z powrotem w znanych typów bez utraty danych lub obcięcie.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-111">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] and the data store need to be able to pass data back and forth in known types without any data loss or truncation.</span></span>  
  
 <span data-ttu-id="fcdcf-112">Manifest dostawcy musi być obciążana za pomocą narzędzi w czasie projektowania bez konieczności otwierania połączenia z magazynem danych.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-112">The provider manifest must be loadable by tools at design time without having to open a connection to the data store.</span></span>  
  
 <span data-ttu-id="fcdcf-113">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Jest przypadek wielkość liter, ale źródłowy magazyn danych może nie być.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-113">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] is case sensitive, but the underlying data store may not be.</span></span> <span data-ttu-id="fcdcf-114">Gdy artefakty EDM (identyfikatory i nazwy typów, na przykład) są zdefiniowane i używane w manifeście, należy użyć [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-114">When EDM artifacts (identifiers and type names, for example) are defined and used in the manifest, they must use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] case sensitivity.</span></span> <span data-ttu-id="fcdcf-115">Jeśli elementów magazynu danych, które mogą być uwzględniana wielkość liter są wyświetlane w manifeście dostawcy, że wielkość liter w wyrazie musi być utrzymywane w manifeście dostawcy.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-115">If data store elements that may be case sensitive appear in the provider manifest, that casing needs to be maintained in the provider manifest.</span></span>  
  
 <span data-ttu-id="fcdcf-116">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Wymaga manifest dostawcy dla wszystkich dostawców danych.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-116">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] requires a provider manifest for all data providers.</span></span> <span data-ttu-id="fcdcf-117">Jeśli spróbujesz użyć dostawcy, który nie ma dostawcy manifestu z [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], otrzymają komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-117">If you try to use a provider that does not have a provider manifest with the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], you will get an error.</span></span>  
  
 <span data-ttu-id="fcdcf-118">W poniższej tabeli opisano rodzaje wyjątków [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] powodowało zgłoszenie, gdy wyjątki wynikać dostawca interakcji:</span><span class="sxs-lookup"><span data-stu-id="fcdcf-118">The following table describes the kinds of exceptions the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] would throw when exceptions arise through provider interaction:</span></span>  
  
|<span data-ttu-id="fcdcf-119">Problem</span><span class="sxs-lookup"><span data-stu-id="fcdcf-119">Issue</span></span>|<span data-ttu-id="fcdcf-120">Wyjątek</span><span class="sxs-lookup"><span data-stu-id="fcdcf-120">Exception</span></span>|  
|-----------|---------------|  
|<span data-ttu-id="fcdcf-121">Dostawca nie obsługuje GetProviderManifest w DbProviderServices.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-121">The Provider does not support GetProviderManifest in DbProviderServices.</span></span>|<span data-ttu-id="fcdcf-122">ProviderIncompatibleException</span><span class="sxs-lookup"><span data-stu-id="fcdcf-122">ProviderIncompatibleException</span></span>|  
|<span data-ttu-id="fcdcf-123">Brak manifestu dostawcy: dostawca zwraca `null` podczas próby pobrania manifestu dostawcy.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-123">Missing provider manifest: the provider returns `null` when attempting to retrieve the provider manifest.</span></span>|<span data-ttu-id="fcdcf-124">ProviderIncompatibleException</span><span class="sxs-lookup"><span data-stu-id="fcdcf-124">ProviderIncompatibleException</span></span>|  
|<span data-ttu-id="fcdcf-125">Nieprawidłowy dostawca manifest: dostawca zwraca nieprawidłowy kod XML, podczas próby pobrania manifestu dostawcy.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-125">Invalid provider manifest: the provider returns invalid XML when attempting to retrieve the provider manifest.</span></span>|<span data-ttu-id="fcdcf-126">ProviderIncompatibleException</span><span class="sxs-lookup"><span data-stu-id="fcdcf-126">ProviderIncompatibleException</span></span>|  
  
## <a name="scenarios"></a><span data-ttu-id="fcdcf-127">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="fcdcf-127">Scenarios</span></span>  
 <span data-ttu-id="fcdcf-128">Dostawca powinien obsługiwać następujące scenariusze:</span><span class="sxs-lookup"><span data-stu-id="fcdcf-128">A provider should support the following scenarios:</span></span>  
  
### <a name="writing-a-provider-with-symmetric-type-mapping"></a><span data-ttu-id="fcdcf-129">Pisanie dostawcy za pomocą mapowania typu symetryczne</span><span class="sxs-lookup"><span data-stu-id="fcdcf-129">Writing a Provider with Symmetric Type Mapping</span></span>  
 <span data-ttu-id="fcdcf-130">Można napisać dostawcę dla [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] gdzie każdego typu magazynu jest mapowany na pojedynczy typ EDM, niezależnie od tego, w kierunku mapowania.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-130">You can write a provider for the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] where each store type maps to a single EDM type, regardless of the mapping direction.</span></span> <span data-ttu-id="fcdcf-131">Dla typu dostawcy, który znajduje się bardzo prostego mapowanie odpowiada za pomocą typu EDM można użyć symetrycznego rozwiązania, ponieważ system typu prostego lub pasuje do typu EDM.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-131">For a provider type that has very simple mapping that corresponds with an EDM type, you can use a symmetric solution because the type system is simple or matches EDM types.</span></span>  
  
 <span data-ttu-id="fcdcf-132">Można użyć prostotę ich domeny i wygenerować manifest dostawcy deklaratywne statyczne.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-132">You can use the simplicity of their domain and produce a static declarative provider manifest.</span></span>  
  
 <span data-ttu-id="fcdcf-133">Możesz napisać plik XML, który ma dwie sekcje:</span><span class="sxs-lookup"><span data-stu-id="fcdcf-133">You write an XML file that has two sections:</span></span>  
  
- <span data-ttu-id="fcdcf-134">Lista typy dostawców, wyrażonych "EDM odpowiednikiem" typ magazynu lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-134">A list of provider types expressed in terms of the "EDM counterpart" of a store type or function.</span></span> <span data-ttu-id="fcdcf-135">Typy Store mają odpowiednika typów EDM.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-135">Store types have counterpart EDM types.</span></span> <span data-ttu-id="fcdcf-136">Funkcje Store mają odpowiednie funkcje EDM.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-136">Store functions have corresponding EDM functions.</span></span> <span data-ttu-id="fcdcf-137">Na przykład varchar jest typem programu SQL Server, ale odpowiedni typ EDM jest ciągiem.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-137">For example, varchar is a SQL Server type but the corresponding EDM type is string.</span></span>  
  
- <span data-ttu-id="fcdcf-138">Lista funkcji obsługiwanych przez dostawcę, w których typy parametrów i zwrotu jest wyrażany w kategoriach EDM.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-138">A list of functions supported by the provider where parameter and return types are expressed in EDM terms.</span></span>  
  
### <a name="writing-a-provider-with-asymmetric-type-mapping"></a><span data-ttu-id="fcdcf-139">Pisanie dostawcy za pomocą asymetrycznych Typ mapowania</span><span class="sxs-lookup"><span data-stu-id="fcdcf-139">Writing a Provider with Asymmetric Type Mapping</span></span>  
 <span data-ttu-id="fcdcf-140">Podczas pisania dostawca magazynu danych dla [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], typ EDM do dostawcy mapowanie dla niektórych typów może się różnić od typu dostawcy do EDM mapowania.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-140">When writing a data store provider for the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], the EDM-to-provider type mapping for some types may be different from provider-to-EDM type mapping.</span></span> <span data-ttu-id="fcdcf-141">Na przykład niepowiązane PrimitiveTypeKind.String EDM mogą być mapowane do nvarchar(4000) na dostawcy, gdy nvarchar(4000) mapuje EDM PrimitiveTypeKind.String(MaxLength=4000).</span><span class="sxs-lookup"><span data-stu-id="fcdcf-141">For instance, unbounded EDM PrimitiveTypeKind.String may map to nvarchar(4000) on the provider, while nvarchar(4000) maps to the EDM PrimitiveTypeKind.String(MaxLength=4000).</span></span>  
  
 <span data-ttu-id="fcdcf-142">Możesz napisać plik XML, który ma dwie sekcje:</span><span class="sxs-lookup"><span data-stu-id="fcdcf-142">You write an XML file that has two sections:</span></span>  
  
- <span data-ttu-id="fcdcf-143">Lista typów dostawcy wyrażany w kategoriach EDM i zdefiniować mapowanie dla obu kierunku: EDM do dostawcy i dostawcy do EDM.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-143">A list of provider types expressed in EDM terms and define mapping for both direction: EDM-to-provider and provider-to-EDM.</span></span>  
  
- <span data-ttu-id="fcdcf-144">Lista funkcji obsługiwanych przez dostawcę, w których typy parametrów i zwrotu jest wyrażany w kategoriach EDM.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-144">A list of functions supported by the provider where parameter and return types are expressed in EDM terms.</span></span>  
  
## <a name="provider-manifest-discoverability"></a><span data-ttu-id="fcdcf-145">Odnajdowanie manifestu dostawcy</span><span class="sxs-lookup"><span data-stu-id="fcdcf-145">Provider Manifest Discoverability</span></span>  
 <span data-ttu-id="fcdcf-146">Manifest używany jest pośrednio w różnych typach składnika w jednostki usługi (na przykład narzędzia lub zapytanie), ale przechowywać więcej bezpośrednio wykorzystywane przez metadane za pomocą danych modułu ładującego metadanych.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-146">The manifest is used indirectly by several component types in Entity Services (for example Tools or Query) but more directly leveraged by metadata through the use of the data store metadata loader.</span></span>  
  
 <span data-ttu-id="fcdcf-147">![dfb3d02b&#45;7a8c&#45;4d51&#45;ac5a&#45;a73d8aa145e6](../../../../../docs/framework/data/adonet/ef/media/dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6.gif "dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6")</span><span class="sxs-lookup"><span data-stu-id="fcdcf-147">![dfb3d02b&#45;7a8c&#45;4d51&#45;ac5a&#45;a73d8aa145e6](../../../../../docs/framework/data/adonet/ef/media/dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6.gif "dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6")</span></span>  
  
 <span data-ttu-id="fcdcf-148">Jednak danego dostawcy mogą obsługiwać różne wersje tego samego magazynu lub różnych magazynów danych.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-148">However, a given provider may support different stores or different versions of the same store.</span></span> <span data-ttu-id="fcdcf-149">W związku z tym dostawca, musisz zgłosić różnych manifestu dla każdego obsługiwanego magazynu danych.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-149">Therefore, a provider must report a different manifest for each supported data store.</span></span>  
  
### <a name="provider-manifest-token"></a><span data-ttu-id="fcdcf-150">Token manifestu dostawcy</span><span class="sxs-lookup"><span data-stu-id="fcdcf-150">Provider Manifest Token</span></span>  
 <span data-ttu-id="fcdcf-151">Po otwarciu połączenia magazynu danych dostawcy mogą wysyłać zapytania dotyczące informacji do zwrócenia prawo manifestu.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-151">When a data store connection is opened, the provider can query for information to return the right manifest.</span></span> <span data-ttu-id="fcdcf-152">To może nie być możliwe w scenariuszach w trybie offline gdy informacje o połączeniu nie są dostępne lub kiedy nie jest możliwość nawiązywania połączeń do magazynu.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-152">This may not be possible in offline scenarios where connection information is not available or when it is not possible to connect to the store.</span></span> <span data-ttu-id="fcdcf-153">Identyfikowanie manifest za pomocą `ProviderManifestToken` atrybutu `Schema` elementu souboru ssdl.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-153">Identify the manifest by using the `ProviderManifestToken` attribute of the `Schema` element in the .ssdl file.</span></span> <span data-ttu-id="fcdcf-154">Brak ma wymaganego formatu dla tego atrybutu; Dostawca wybiera minimalne informacje potrzebne do identyfikowania manifestu bez konieczności otwierania połączenia z magazynem.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-154">There is no required format for this attribute; the provider chooses the minimum information needed to identify a manifest without opening a connection to the store.</span></span>  
  
 <span data-ttu-id="fcdcf-155">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="fcdcf-155">For example:</span></span>  
  
```xml  
<Schema Namespace="Northwind" Provider="System.Data.SqlClient" ProviderManifestToken="2005" xmlns:edm="http://schemas.microsoft.com/ado/2006/04/edm/ssdl" xmlns="http://schemas.microsoft.com/ado/2006/04/edm/ssdl">  
```  
  
## <a name="provider-manifest-programming-model"></a><span data-ttu-id="fcdcf-156">Model programowania z manifestu dostawcy</span><span class="sxs-lookup"><span data-stu-id="fcdcf-156">Provider Manifest Programming Model</span></span>  
 <span data-ttu-id="fcdcf-157">Dostawców pochodzić od <xref:System.Data.Common.DbXmlEnabledProviderManifest>, co pozwala określić swoich manifestach deklaratywnie.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-157">Providers derive from <xref:System.Data.Common.DbXmlEnabledProviderManifest>, which allows them to specify their manifests declaratively.</span></span> <span data-ttu-id="fcdcf-158">Poniższa ilustracja przedstawia hierarchii klas dostawcy:</span><span class="sxs-lookup"><span data-stu-id="fcdcf-158">The following illustration shows the class hierarchy of a provider:</span></span>  
  
 <span data-ttu-id="fcdcf-159">![None](../../../../../docs/framework/data/adonet/ef/media/d541eba3-2ee6-4cd1-88f5-89d0b2582a6c.gif "d541eba3-2ee6-4cd1-88f5-89d0b2582a6c")</span><span class="sxs-lookup"><span data-stu-id="fcdcf-159">![None](../../../../../docs/framework/data/adonet/ef/media/d541eba3-2ee6-4cd1-88f5-89d0b2582a6c.gif "d541eba3-2ee6-4cd1-88f5-89d0b2582a6c")</span></span>  
  
### <a name="discoverability-api"></a><span data-ttu-id="fcdcf-160">Odnajdowanie interfejsu API</span><span class="sxs-lookup"><span data-stu-id="fcdcf-160">Discoverability API</span></span>  
 <span data-ttu-id="fcdcf-161">Manifest dostawcy jest ładowany przez moduł ładujący Store metadanych (obiektu StoreItemCollection), przy użyciu danych przechowywać połączenia lub tokenu manifestu dostawcy.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-161">The provider manifest is loaded by the Store Metadata loader (StoreItemCollection), either by using a data store connection or a provider manifest token.</span></span>  
  
#### <a name="using-a-data-store-connection"></a><span data-ttu-id="fcdcf-162">Przy użyciu połączenia danych Store</span><span class="sxs-lookup"><span data-stu-id="fcdcf-162">Using a Data Store Connection</span></span>  
 <span data-ttu-id="fcdcf-163">Gdy magazyn danych jest dostępne połączenie, wywołaj DbProvderServices.GetProviderManifestToken do zwracania tokenu, który jest przekazywany do metody GetProviderManifest, która zwraca DbProviderManifest.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-163">When the data store connection is available, call DbProvderServices.GetProviderManifestToken to return the token that is passed to the GetProviderManifest method, which returns DbProviderManifest.</span></span> <span data-ttu-id="fcdcf-164">Ta metoda deleguje do implementacji dostawcy GetDbProviderManifestToken.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-164">This method delegates to the provider's implementation of GetDbProviderManifestToken.</span></span>  
  
```  
public string GetProviderManifestToken(DbConnection connection);  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
#### <a name="using-a-provider-manifest-token"></a><span data-ttu-id="fcdcf-165">Za pomocą tokenu manifestu dostawcy</span><span class="sxs-lookup"><span data-stu-id="fcdcf-165">Using a Provider Manifest Token</span></span>  
 <span data-ttu-id="fcdcf-166">W scenariuszu w trybie offline token jest pobierany z reprezentacji SSDL.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-166">For the offline scenario, the token is picked from SSDL representation.</span></span> <span data-ttu-id="fcdcf-167">SSDL pozwala na określenie ProviderManifestToken (zobacz [elementu schematu (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl) Aby uzyskać więcej informacji).</span><span class="sxs-lookup"><span data-stu-id="fcdcf-167">The SSDL allows you to specify a ProviderManifestToken (see [Schema Element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl) for more information).</span></span> <span data-ttu-id="fcdcf-168">Na przykład jeśli nie można otworzyć połączenia, SSDL ma token manifestu dostawcy, który określa informacje dotyczące manifestu.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-168">For example, if a connection cannot be opened, the SSDL has a provider manifest token that specifies information about the manifest.</span></span>  
  
```  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
### <a name="provider-manifest-schema"></a><span data-ttu-id="fcdcf-169">Schematu manifestu dostawcy</span><span class="sxs-lookup"><span data-stu-id="fcdcf-169">Provider Manifest Schema</span></span>  
 <span data-ttu-id="fcdcf-170">Schemat informacje zdefiniowane dla każdego dostawcy zawiera dane statyczne do użycia przez metadane:</span><span class="sxs-lookup"><span data-stu-id="fcdcf-170">The schema of information defined for each provider contains the static information to be consumed by metadata:</span></span>  
  
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
  
#### <a name="types-node"></a><span data-ttu-id="fcdcf-171">Typy węzłów</span><span class="sxs-lookup"><span data-stu-id="fcdcf-171">Types Node</span></span>  
 <span data-ttu-id="fcdcf-172">Węzeł typów w manifeście dostawcy zawiera informacje o typach, które są obsługiwane natywnie przez Magazyn danych lub za pośrednictwem dostawcy.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-172">The Types node in the provider manifest contains information about the Types that are supported natively by the data store or through the provider.</span></span>  
  
##### <a name="type-node"></a><span data-ttu-id="fcdcf-173">Typ węzła</span><span class="sxs-lookup"><span data-stu-id="fcdcf-173">Type Node</span></span>  
 <span data-ttu-id="fcdcf-174">Każdy typ węzła definiuje typ dostawcy pod względem EDM.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-174">Each Type node defines a provider type in terms of EDM.</span></span> <span data-ttu-id="fcdcf-175">Węzeł typu w tym artykule opisano nazwa, typ dostawcy i informacje dotyczące typ modelu, który jest on mapowany i zestawów reguł do opisania mapowania typu.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-175">The Type node describes the name of the provider type, and information related to the model type it maps to and facets to describe that type mapping.</span></span>  
  
 <span data-ttu-id="fcdcf-176">Aby można było express to informacje o typie w manifeście dostawcy, każdego zgłoszenia TypeInformation należy zdefiniować kilka opisów reguł dla każdego typu:</span><span class="sxs-lookup"><span data-stu-id="fcdcf-176">In order to express this type information in the provider manifest, each TypeInformation declaration must define several facet descriptions for each Type:</span></span>  
  
|<span data-ttu-id="fcdcf-177">Nazwa atrybutu</span><span class="sxs-lookup"><span data-stu-id="fcdcf-177">Attribute Name</span></span>|<span data-ttu-id="fcdcf-178">Typ danych</span><span class="sxs-lookup"><span data-stu-id="fcdcf-178">Data Type</span></span>|<span data-ttu-id="fcdcf-179">Wymagane</span><span class="sxs-lookup"><span data-stu-id="fcdcf-179">Required</span></span>|<span data-ttu-id="fcdcf-180">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="fcdcf-180">Default Value</span></span>|<span data-ttu-id="fcdcf-181">Opis</span><span class="sxs-lookup"><span data-stu-id="fcdcf-181">Description</span></span>|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|<span data-ttu-id="fcdcf-182">Nazwa</span><span class="sxs-lookup"><span data-stu-id="fcdcf-182">Name</span></span>|<span data-ttu-id="fcdcf-183">String</span><span class="sxs-lookup"><span data-stu-id="fcdcf-183">String</span></span>|<span data-ttu-id="fcdcf-184">Tak</span><span class="sxs-lookup"><span data-stu-id="fcdcf-184">Yes</span></span>|<span data-ttu-id="fcdcf-185">n/d</span><span class="sxs-lookup"><span data-stu-id="fcdcf-185">n/a</span></span>|<span data-ttu-id="fcdcf-186">Nazwa typu danych specyficznego dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="fcdcf-186">Provider-specific data type name</span></span>|  
|<span data-ttu-id="fcdcf-187">PrimitiveTypeKind</span><span class="sxs-lookup"><span data-stu-id="fcdcf-187">PrimitiveTypeKind</span></span>|<span data-ttu-id="fcdcf-188">PrimitiveTypeKind</span><span class="sxs-lookup"><span data-stu-id="fcdcf-188">PrimitiveTypeKind</span></span>|<span data-ttu-id="fcdcf-189">Yes</span><span class="sxs-lookup"><span data-stu-id="fcdcf-189">Yes</span></span>|<span data-ttu-id="fcdcf-190">n/d</span><span class="sxs-lookup"><span data-stu-id="fcdcf-190">n/a</span></span>|<span data-ttu-id="fcdcf-191">Nazwa typu EDM</span><span class="sxs-lookup"><span data-stu-id="fcdcf-191">EDM type name</span></span>|  
  
###### <a name="function-node"></a><span data-ttu-id="fcdcf-192">Węzeł — funkcja</span><span class="sxs-lookup"><span data-stu-id="fcdcf-192">Function Node</span></span>  
 <span data-ttu-id="fcdcf-193">Każda funkcja określa jednej funkcji dostępnych za pośrednictwem dostawcy.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-193">Each Function defines a single function available through the provider.</span></span>  
  
|<span data-ttu-id="fcdcf-194">Nazwa atrybutu</span><span class="sxs-lookup"><span data-stu-id="fcdcf-194">Attribute Name</span></span>|<span data-ttu-id="fcdcf-195">Typ danych</span><span class="sxs-lookup"><span data-stu-id="fcdcf-195">Data Type</span></span>|<span data-ttu-id="fcdcf-196">Wymagane</span><span class="sxs-lookup"><span data-stu-id="fcdcf-196">Required</span></span>|<span data-ttu-id="fcdcf-197">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="fcdcf-197">Default Value</span></span>|<span data-ttu-id="fcdcf-198">Opis</span><span class="sxs-lookup"><span data-stu-id="fcdcf-198">Description</span></span>|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|<span data-ttu-id="fcdcf-199">Nazwa</span><span class="sxs-lookup"><span data-stu-id="fcdcf-199">Name</span></span>|<span data-ttu-id="fcdcf-200">String</span><span class="sxs-lookup"><span data-stu-id="fcdcf-200">String</span></span>|<span data-ttu-id="fcdcf-201">Tak</span><span class="sxs-lookup"><span data-stu-id="fcdcf-201">Yes</span></span>|<span data-ttu-id="fcdcf-202">n/d</span><span class="sxs-lookup"><span data-stu-id="fcdcf-202">n/a</span></span>|<span data-ttu-id="fcdcf-203">Identyfikator/nazwę funkcji</span><span class="sxs-lookup"><span data-stu-id="fcdcf-203">Identifier/name of the function</span></span>|  
|<span data-ttu-id="fcdcf-204">ReturnType</span><span class="sxs-lookup"><span data-stu-id="fcdcf-204">ReturnType</span></span>|<span data-ttu-id="fcdcf-205">String</span><span class="sxs-lookup"><span data-stu-id="fcdcf-205">String</span></span>|<span data-ttu-id="fcdcf-206">Nie</span><span class="sxs-lookup"><span data-stu-id="fcdcf-206">No</span></span>|<span data-ttu-id="fcdcf-207">Void</span><span class="sxs-lookup"><span data-stu-id="fcdcf-207">Void</span></span>|<span data-ttu-id="fcdcf-208">Zwracany typ EDM — funkcja</span><span class="sxs-lookup"><span data-stu-id="fcdcf-208">The EDM return type of the function</span></span>|  
|<span data-ttu-id="fcdcf-209">Agregowanie</span><span class="sxs-lookup"><span data-stu-id="fcdcf-209">Aggregate</span></span>|<span data-ttu-id="fcdcf-210">Boolean</span><span class="sxs-lookup"><span data-stu-id="fcdcf-210">Boolean</span></span>|<span data-ttu-id="fcdcf-211">Nie</span><span class="sxs-lookup"><span data-stu-id="fcdcf-211">No</span></span>|<span data-ttu-id="fcdcf-212">False</span><span class="sxs-lookup"><span data-stu-id="fcdcf-212">False</span></span>|<span data-ttu-id="fcdcf-213">Wartość true, jeśli funkcja znajduje się funkcja agregująca</span><span class="sxs-lookup"><span data-stu-id="fcdcf-213">True if the function is an aggregate function</span></span>|  
|<span data-ttu-id="fcdcf-214">BuiltIn</span><span class="sxs-lookup"><span data-stu-id="fcdcf-214">BuiltIn</span></span>|<span data-ttu-id="fcdcf-215">Boolean</span><span class="sxs-lookup"><span data-stu-id="fcdcf-215">Boolean</span></span>|<span data-ttu-id="fcdcf-216">Nie</span><span class="sxs-lookup"><span data-stu-id="fcdcf-216">No</span></span>|<span data-ttu-id="fcdcf-217">Prawda</span><span class="sxs-lookup"><span data-stu-id="fcdcf-217">True</span></span>|<span data-ttu-id="fcdcf-218">Wartość true, jeśli funkcja jest wbudowana w magazynie danych</span><span class="sxs-lookup"><span data-stu-id="fcdcf-218">True if the function is built into the data store</span></span>|  
|<span data-ttu-id="fcdcf-219">StoreFunctionName</span><span class="sxs-lookup"><span data-stu-id="fcdcf-219">StoreFunctionName</span></span>|<span data-ttu-id="fcdcf-220">String</span><span class="sxs-lookup"><span data-stu-id="fcdcf-220">String</span></span>|<span data-ttu-id="fcdcf-221">Nie</span><span class="sxs-lookup"><span data-stu-id="fcdcf-221">No</span></span>|<span data-ttu-id="fcdcf-222">\<Nazwa ></span><span class="sxs-lookup"><span data-stu-id="fcdcf-222">\<Name></span></span>|<span data-ttu-id="fcdcf-223">Nazwa funkcji w magazynie danych.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-223">Function Name in the data store.</span></span>  <span data-ttu-id="fcdcf-224">Zezwala na poziomie przekierowywania nazwy funkcji.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-224">Allows for a level of redirection of function names.</span></span>|  
|<span data-ttu-id="fcdcf-225">NiladicFunction</span><span class="sxs-lookup"><span data-stu-id="fcdcf-225">NiladicFunction</span></span>|<span data-ttu-id="fcdcf-226">Boolean</span><span class="sxs-lookup"><span data-stu-id="fcdcf-226">Boolean</span></span>|<span data-ttu-id="fcdcf-227">Nie</span><span class="sxs-lookup"><span data-stu-id="fcdcf-227">No</span></span>|<span data-ttu-id="fcdcf-228">False</span><span class="sxs-lookup"><span data-stu-id="fcdcf-228">False</span></span>|<span data-ttu-id="fcdcf-229">Wartość true, jeśli funkcja nie wymaga parametrów i jest wywoływana bez parametrów</span><span class="sxs-lookup"><span data-stu-id="fcdcf-229">True if the function does not require parameters and is called without any parameters</span></span>|  
|<span data-ttu-id="fcdcf-230">Zgodność</span><span class="sxs-lookup"><span data-stu-id="fcdcf-230">ParameterType</span></span><br /><br /> <span data-ttu-id="fcdcf-231">Semantyka</span><span class="sxs-lookup"><span data-stu-id="fcdcf-231">Semantics</span></span>|<span data-ttu-id="fcdcf-232">ParameterSemantics</span><span class="sxs-lookup"><span data-stu-id="fcdcf-232">ParameterSemantics</span></span>|<span data-ttu-id="fcdcf-233">Nie</span><span class="sxs-lookup"><span data-stu-id="fcdcf-233">No</span></span>|<span data-ttu-id="fcdcf-234">AllowImplicit</span><span class="sxs-lookup"><span data-stu-id="fcdcf-234">AllowImplicit</span></span><br /><br /> <span data-ttu-id="fcdcf-235">Konwersja</span><span class="sxs-lookup"><span data-stu-id="fcdcf-235">Conversion</span></span>|<span data-ttu-id="fcdcf-236">Wybór sposobu potoku zapytania powinien zająć się podstawienie typ parametru:</span><span class="sxs-lookup"><span data-stu-id="fcdcf-236">Choice of how the query pipeline should deal with parameter type substitution:</span></span><br /><br /> <span data-ttu-id="fcdcf-237">-ExactMatchOnly</span><span class="sxs-lookup"><span data-stu-id="fcdcf-237">-   ExactMatchOnly</span></span><br /><span data-ttu-id="fcdcf-238">-AllowImplicitPromotion</span><span class="sxs-lookup"><span data-stu-id="fcdcf-238">-   AllowImplicitPromotion</span></span><br /><span data-ttu-id="fcdcf-239">-AllowImplicitConversion</span><span class="sxs-lookup"><span data-stu-id="fcdcf-239">-   AllowImplicitConversion</span></span>|  
  
 <span data-ttu-id="fcdcf-240">**Parametry węzła**</span><span class="sxs-lookup"><span data-stu-id="fcdcf-240">**Parameters Node**</span></span>  
  
 <span data-ttu-id="fcdcf-241">Każda funkcja ma zbiór jednego lub więcej węzłów parametrów.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-241">Each function has a collection of one or more Parameter nodes.</span></span>  
  
|<span data-ttu-id="fcdcf-242">Nazwa atrybutu</span><span class="sxs-lookup"><span data-stu-id="fcdcf-242">Attribute Name</span></span>|<span data-ttu-id="fcdcf-243">Typ danych</span><span class="sxs-lookup"><span data-stu-id="fcdcf-243">Data Type</span></span>|<span data-ttu-id="fcdcf-244">Wymagane</span><span class="sxs-lookup"><span data-stu-id="fcdcf-244">Required</span></span>|<span data-ttu-id="fcdcf-245">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="fcdcf-245">Default Value</span></span>|<span data-ttu-id="fcdcf-246">Opis</span><span class="sxs-lookup"><span data-stu-id="fcdcf-246">Description</span></span>|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|<span data-ttu-id="fcdcf-247">Nazwa</span><span class="sxs-lookup"><span data-stu-id="fcdcf-247">Name</span></span>|<span data-ttu-id="fcdcf-248">String</span><span class="sxs-lookup"><span data-stu-id="fcdcf-248">String</span></span>|<span data-ttu-id="fcdcf-249">Tak</span><span class="sxs-lookup"><span data-stu-id="fcdcf-249">Yes</span></span>|<span data-ttu-id="fcdcf-250">n/d</span><span class="sxs-lookup"><span data-stu-id="fcdcf-250">n/a</span></span>|<span data-ttu-id="fcdcf-251">Identyfikator/nazwę parametru.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-251">Identifier/name of the parameter.</span></span>|  
|<span data-ttu-id="fcdcf-252">Typ</span><span class="sxs-lookup"><span data-stu-id="fcdcf-252">Type</span></span>|<span data-ttu-id="fcdcf-253">String</span><span class="sxs-lookup"><span data-stu-id="fcdcf-253">String</span></span>|<span data-ttu-id="fcdcf-254">Tak</span><span class="sxs-lookup"><span data-stu-id="fcdcf-254">Yes</span></span>|<span data-ttu-id="fcdcf-255">n/d</span><span class="sxs-lookup"><span data-stu-id="fcdcf-255">n/a</span></span>|<span data-ttu-id="fcdcf-256">Typ EDM parametru.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-256">The EDM type of the parameter.</span></span>|  
|<span data-ttu-id="fcdcf-257">Tryb</span><span class="sxs-lookup"><span data-stu-id="fcdcf-257">Mode</span></span>|<span data-ttu-id="fcdcf-258">Parametr</span><span class="sxs-lookup"><span data-stu-id="fcdcf-258">Parameter</span></span><br /><br /> <span data-ttu-id="fcdcf-259">Kierunek</span><span class="sxs-lookup"><span data-stu-id="fcdcf-259">Direction</span></span>|<span data-ttu-id="fcdcf-260">Tak</span><span class="sxs-lookup"><span data-stu-id="fcdcf-260">Yes</span></span>|<span data-ttu-id="fcdcf-261">n/d</span><span class="sxs-lookup"><span data-stu-id="fcdcf-261">n/a</span></span>|<span data-ttu-id="fcdcf-262">Kierunek parametru:</span><span class="sxs-lookup"><span data-stu-id="fcdcf-262">Direction of parameter:</span></span><br /><br /> <span data-ttu-id="fcdcf-263">-w</span><span class="sxs-lookup"><span data-stu-id="fcdcf-263">-   in</span></span><br /><span data-ttu-id="fcdcf-264">-out</span><span class="sxs-lookup"><span data-stu-id="fcdcf-264">-   out</span></span><br /><span data-ttu-id="fcdcf-265">-inout</span><span class="sxs-lookup"><span data-stu-id="fcdcf-265">-   inout</span></span>|  
  
##### <a name="namespace-attribute"></a><span data-ttu-id="fcdcf-266">Atrybut Namespace</span><span class="sxs-lookup"><span data-stu-id="fcdcf-266">Namespace Attribute</span></span>  
 <span data-ttu-id="fcdcf-267">Każdy dostawca magazynu danych, należy zdefiniować przestrzeni nazw lub grupy w przestrzeni nazw dla informacje zdefiniowane w manifeście.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-267">Each data store provider must define a namespace or group of namespaces for information defined in the manifest.</span></span> <span data-ttu-id="fcdcf-268">Ta przestrzeń nazw może służyć w zapytań jednostki SQL do rozpoznawania nazw funkcji i typów.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-268">This namespace can be used in Entity SQL queries to resolve names of functions and types.</span></span> <span data-ttu-id="fcdcf-269">Przykład: SqlServer.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-269">For instance: SqlServer.</span></span> <span data-ttu-id="fcdcf-270">Przestrzeń nazw musi się różnić od canonical przestrzeni nazw, EDM, zdefiniowane przez jednostki Services na potrzeby standardowych funkcji są obsługiwane przez zapytania SQL jednostki.</span><span class="sxs-lookup"><span data-stu-id="fcdcf-270">That namespace must be different from the canonical namespace, EDM, defined by Entity Services for standard functions to be supported by Entity SQL queries.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcdcf-271">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fcdcf-271">See also</span></span>

- [<span data-ttu-id="fcdcf-272">Pisanie dostawcy danych programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="fcdcf-272">Writing an Entity Framework Data Provider</span></span>](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
