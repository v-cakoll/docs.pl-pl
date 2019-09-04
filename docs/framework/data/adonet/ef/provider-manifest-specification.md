---
title: Specyfikacja manifestu dostawcy
ms.date: 03/30/2017
ms.assetid: bb450b47-8951-4f99-9350-26f05a4d4e46
ms.openlocfilehash: 6b924f484e6635760d08d0eba9fb9436bdd8bc88
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248587"
---
# <a name="provider-manifest-specification"></a><span data-ttu-id="8bafc-102">Specyfikacja manifestu dostawcy</span><span class="sxs-lookup"><span data-stu-id="8bafc-102">Provider Manifest Specification</span></span>
<span data-ttu-id="8bafc-103">W tej sekcji omówiono, w jaki sposób dostawca magazynu danych może obsługiwać typy i funkcje w magazynie danych.</span><span class="sxs-lookup"><span data-stu-id="8bafc-103">This section discusses how a data store provider can support the types and functions in the data store.</span></span>  
  
 <span data-ttu-id="8bafc-104">Usługa Entity Services działa niezależnie od konkretnego dostawcy magazynu danych, mimo że dostawca danych jawnie definiuje sposób, w jaki modele, mapowania i zapytania współdziałają z bazowym magazynem danych.</span><span class="sxs-lookup"><span data-stu-id="8bafc-104">Entity Services operates independently of a specific data store provider yet still allows a data provider to explicitly define how models, mappings, and queries interact with an underlying data store.</span></span> <span data-ttu-id="8bafc-105">Bez warstwy abstrakcji usługi Entity Services mogą być wskazywane tylko przez określony magazyn danych lub dostawcę danych.</span><span class="sxs-lookup"><span data-stu-id="8bafc-105">Without a layer of abstraction, Entity Services could only be targeted at a specific data store or data provider.</span></span>  
  
 <span data-ttu-id="8bafc-106">Typy obsługujące dostawcę są bezpośrednio lub pośrednio obsługiwane przez podstawową bazę danych.</span><span class="sxs-lookup"><span data-stu-id="8bafc-106">Types that the provider supports are directly or indirectly supported by the underlying database.</span></span> <span data-ttu-id="8bafc-107">Te typy nie muszą być dokładnymi typami magazynów, ale typy stosowane przez dostawcę do obsługi [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8bafc-107">These types are not necessarily the exact store types, but the types the provider uses to support the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="8bafc-108">Typy dostawców/magazynów są opisane w tematach Entity Data Model (EDM).</span><span class="sxs-lookup"><span data-stu-id="8bafc-108">Provider/store types are described in the Entity Data Model (EDM) terms.</span></span>  
  
 <span data-ttu-id="8bafc-109">Parametry i typy zwracane dla funkcji obsługiwanych przez magazyn danych są określone w obszarze EDM.</span><span class="sxs-lookup"><span data-stu-id="8bafc-109">Parameter and return types for the functions supported by the data store are specified in EDM terms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bafc-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8bafc-110">Requirements</span></span>  
 <span data-ttu-id="8bafc-111">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] I magazyn danych musi być w stanie przekazać dane z powrotem i dalej w znanych typach bez utraty lub obcięcia danych.</span><span class="sxs-lookup"><span data-stu-id="8bafc-111">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] and the data store need to be able to pass data back and forth in known types without any data loss or truncation.</span></span>  
  
 <span data-ttu-id="8bafc-112">Manifest dostawcy musi być ładowany przez narzędzia w czasie projektowania bez konieczności otwierania połączenia z magazynem danych.</span><span class="sxs-lookup"><span data-stu-id="8bafc-112">The provider manifest must be loadable by tools at design time without having to open a connection to the data store.</span></span>  
  
 <span data-ttu-id="8bafc-113">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Jest uwzględniana wielkość liter, ale podstawowy magazyn danych może nie być.</span><span class="sxs-lookup"><span data-stu-id="8bafc-113">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] is case sensitive, but the underlying data store may not be.</span></span> <span data-ttu-id="8bafc-114">Gdy artefakty modelu EDM (na przykład identyfikatory i nazwy typów) są zdefiniowane i używane w manifeście, muszą używać [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] rozróżniania wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="8bafc-114">When EDM artifacts (identifiers and type names, for example) are defined and used in the manifest, they must use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] case sensitivity.</span></span> <span data-ttu-id="8bafc-115">Jeśli w manifeście dostawcy znajdują się elementy magazynu danych, które mogą uwzględniać wielkość liter, należy zachować wielkość liter w manifeście dostawcy.</span><span class="sxs-lookup"><span data-stu-id="8bafc-115">If data store elements that may be case sensitive appear in the provider manifest, that casing needs to be maintained in the provider manifest.</span></span>  
  
 <span data-ttu-id="8bafc-116">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Wymaga manifestu dostawcy dla wszystkich dostawców danych.</span><span class="sxs-lookup"><span data-stu-id="8bafc-116">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] requires a provider manifest for all data providers.</span></span> <span data-ttu-id="8bafc-117">Jeśli spróbujesz użyć dostawcy, który nie ma manifestu dostawcy z [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], zostanie wyświetlony komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="8bafc-117">If you try to use a provider that does not have a provider manifest with the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], you will get an error.</span></span>  
  
 <span data-ttu-id="8bafc-118">W poniższej tabeli opisano rodzaje wyjątków, które zostałyby zgłoszone w [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] przypadku wystąpienia wyjątków przez interakcję z dostawcą:</span><span class="sxs-lookup"><span data-stu-id="8bafc-118">The following table describes the kinds of exceptions the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] would throw when exceptions arise through provider interaction:</span></span>  
  
|<span data-ttu-id="8bafc-119">Problem</span><span class="sxs-lookup"><span data-stu-id="8bafc-119">Issue</span></span>|<span data-ttu-id="8bafc-120">Wyjątek</span><span class="sxs-lookup"><span data-stu-id="8bafc-120">Exception</span></span>|  
|-----------|---------------|  
|<span data-ttu-id="8bafc-121">Dostawca nie obsługuje GetProviderManifest w DbProviderServices.</span><span class="sxs-lookup"><span data-stu-id="8bafc-121">The Provider does not support GetProviderManifest in DbProviderServices.</span></span>|<span data-ttu-id="8bafc-122">ProviderIncompatibleException</span><span class="sxs-lookup"><span data-stu-id="8bafc-122">ProviderIncompatibleException</span></span>|  
|<span data-ttu-id="8bafc-123">Brak manifestu dostawcy: dostawca zwraca `null` podczas próby pobrania manifestu dostawcy.</span><span class="sxs-lookup"><span data-stu-id="8bafc-123">Missing provider manifest: the provider returns `null` when attempting to retrieve the provider manifest.</span></span>|<span data-ttu-id="8bafc-124">ProviderIncompatibleException</span><span class="sxs-lookup"><span data-stu-id="8bafc-124">ProviderIncompatibleException</span></span>|  
|<span data-ttu-id="8bafc-125">Nieprawidłowy manifest dostawcy: dostawca zwraca nieprawidłowy kod XML podczas próby pobrania manifestu dostawcy.</span><span class="sxs-lookup"><span data-stu-id="8bafc-125">Invalid provider manifest: the provider returns invalid XML when attempting to retrieve the provider manifest.</span></span>|<span data-ttu-id="8bafc-126">ProviderIncompatibleException</span><span class="sxs-lookup"><span data-stu-id="8bafc-126">ProviderIncompatibleException</span></span>|  
  
## <a name="scenarios"></a><span data-ttu-id="8bafc-127">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="8bafc-127">Scenarios</span></span>  
 <span data-ttu-id="8bafc-128">Dostawca powinien obsługiwać następujące scenariusze:</span><span class="sxs-lookup"><span data-stu-id="8bafc-128">A provider should support the following scenarios:</span></span>  
  
### <a name="writing-a-provider-with-symmetric-type-mapping"></a><span data-ttu-id="8bafc-129">Pisanie dostawcy z mapowaniem typu symetrycznego</span><span class="sxs-lookup"><span data-stu-id="8bafc-129">Writing a Provider with Symmetric Type Mapping</span></span>  
 <span data-ttu-id="8bafc-130">Można napisać dostawcę dla [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] każdego typu magazynu, który jest mapowany na pojedynczy typ modelu EDM, niezależnie od kierunku mapowania.</span><span class="sxs-lookup"><span data-stu-id="8bafc-130">You can write a provider for the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] where each store type maps to a single EDM type, regardless of the mapping direction.</span></span> <span data-ttu-id="8bafc-131">W przypadku typu dostawcy, który ma bardzo proste mapowanie odpowiadające typowi modelu EDM, można użyć rozwiązania symetrycznego, ponieważ system typów jest prosty lub zgodny z typami modelu EDM.</span><span class="sxs-lookup"><span data-stu-id="8bafc-131">For a provider type that has very simple mapping that corresponds with an EDM type, you can use a symmetric solution because the type system is simple or matches EDM types.</span></span>  
  
 <span data-ttu-id="8bafc-132">Możesz użyć prostoty swojej domeny i utworzyć statyczny manifest dostawcy deklaratywnego.</span><span class="sxs-lookup"><span data-stu-id="8bafc-132">You can use the simplicity of their domain and produce a static declarative provider manifest.</span></span>  
  
 <span data-ttu-id="8bafc-133">Napiszesz plik XML, który ma dwie sekcje:</span><span class="sxs-lookup"><span data-stu-id="8bafc-133">You write an XML file that has two sections:</span></span>  
  
- <span data-ttu-id="8bafc-134">Lista typów dostawców wyrażona w postaci "odpowiedniki modelu EDM" typu lub funkcji magazynu.</span><span class="sxs-lookup"><span data-stu-id="8bafc-134">A list of provider types expressed in terms of the "EDM counterpart" of a store type or function.</span></span> <span data-ttu-id="8bafc-135">Typy magazynów mają odpowiedni typ modelu EDM.</span><span class="sxs-lookup"><span data-stu-id="8bafc-135">Store types have counterpart EDM types.</span></span> <span data-ttu-id="8bafc-136">Funkcje magazynu mają odpowiednie funkcje modelu EDM.</span><span class="sxs-lookup"><span data-stu-id="8bafc-136">Store functions have corresponding EDM functions.</span></span> <span data-ttu-id="8bafc-137">Na przykład, varchar jest typem SQL Server, ale odpowiedni typ modelu EDM to ciąg.</span><span class="sxs-lookup"><span data-stu-id="8bafc-137">For example, varchar is a SQL Server type but the corresponding EDM type is string.</span></span>  
  
- <span data-ttu-id="8bafc-138">Lista funkcji obsługiwanych przez dostawcę, gdzie parametry i zwracane typy są wyrażane w warunkach EDM.</span><span class="sxs-lookup"><span data-stu-id="8bafc-138">A list of functions supported by the provider where parameter and return types are expressed in EDM terms.</span></span>  
  
### <a name="writing-a-provider-with-asymmetric-type-mapping"></a><span data-ttu-id="8bafc-139">Pisanie dostawcy z mapowaniem typu asymetrycznego</span><span class="sxs-lookup"><span data-stu-id="8bafc-139">Writing a Provider with Asymmetric Type Mapping</span></span>  
 <span data-ttu-id="8bafc-140">Podczas pisania dostawcy magazynu danych dla [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]programu, mapowanie typu modelu EDM do dostawcy dla niektórych typów może różnić się od mapowania typu dostawca-do-EDM.</span><span class="sxs-lookup"><span data-stu-id="8bafc-140">When writing a data store provider for the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], the EDM-to-provider type mapping for some types may be different from provider-to-EDM type mapping.</span></span> <span data-ttu-id="8bafc-141">Na przykład niezależny obiekt EDM PrimitiveTypeKind. String może być mapowany na nvarchar (4000) na dostawcy, podczas gdy nvarchar (4000) mapuje do modelu EDM PrimitiveTypeKind. String (MaxLength = 4000).</span><span class="sxs-lookup"><span data-stu-id="8bafc-141">For instance, unbounded EDM PrimitiveTypeKind.String may map to nvarchar(4000) on the provider, while nvarchar(4000) maps to the EDM PrimitiveTypeKind.String(MaxLength=4000).</span></span>  
  
 <span data-ttu-id="8bafc-142">Napiszesz plik XML, który ma dwie sekcje:</span><span class="sxs-lookup"><span data-stu-id="8bafc-142">You write an XML file that has two sections:</span></span>  
  
- <span data-ttu-id="8bafc-143">Lista typów dostawców wyrażona w warunkach EDM i zdefiniuj mapowanie dla obu kierunków: Modelu EDM-to-Provider i dostawcy do modelu EDM.</span><span class="sxs-lookup"><span data-stu-id="8bafc-143">A list of provider types expressed in EDM terms and define mapping for both direction: EDM-to-provider and provider-to-EDM.</span></span>  
  
- <span data-ttu-id="8bafc-144">Lista funkcji obsługiwanych przez dostawcę, gdzie parametry i zwracane typy są wyrażane w warunkach EDM.</span><span class="sxs-lookup"><span data-stu-id="8bafc-144">A list of functions supported by the provider where parameter and return types are expressed in EDM terms.</span></span>  
  
## <a name="provider-manifest-discoverability"></a><span data-ttu-id="8bafc-145">Odnajdywanie manifestu dostawcy</span><span class="sxs-lookup"><span data-stu-id="8bafc-145">Provider Manifest Discoverability</span></span>  
 <span data-ttu-id="8bafc-146">Manifest jest używany pośrednio przez kilka typów składników w usługach Entity Services (na przykład narzędzia lub zapytania), ale bardziej bezpośrednio korzystających z metadanych przy użyciu modułu ładującego metadanych magazynu danych.</span><span class="sxs-lookup"><span data-stu-id="8bafc-146">The manifest is used indirectly by several component types in Entity Services (for example Tools or Query) but more directly leveraged by metadata through the use of the data store metadata loader.</span></span>  
  
 <span data-ttu-id="8bafc-147">![dfb3d02b&#45;7a8c&#45;4d51&#45;ac5a&#45;a73d8aa145e6](./media/dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6.gif "dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6")</span><span class="sxs-lookup"><span data-stu-id="8bafc-147">![dfb3d02b&#45;7a8c&#45;4d51&#45;ac5a&#45;a73d8aa145e6](./media/dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6.gif "dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6")</span></span>  
  
 <span data-ttu-id="8bafc-148">Jednak dany dostawca może obsługiwać różne magazyny lub różne wersje tego samego magazynu.</span><span class="sxs-lookup"><span data-stu-id="8bafc-148">However, a given provider may support different stores or different versions of the same store.</span></span> <span data-ttu-id="8bafc-149">W związku z tym dostawca musi zgłosić inny manifest dla każdego z obsługiwanych magazynów danych.</span><span class="sxs-lookup"><span data-stu-id="8bafc-149">Therefore, a provider must report a different manifest for each supported data store.</span></span>  
  
### <a name="provider-manifest-token"></a><span data-ttu-id="8bafc-150">Token manifestu dostawcy</span><span class="sxs-lookup"><span data-stu-id="8bafc-150">Provider Manifest Token</span></span>  
 <span data-ttu-id="8bafc-151">Po otwarciu połączenia z magazynem danych dostawca może wysyłać zapytania o informacje w celu zwrócenia odpowiedniego manifestu.</span><span class="sxs-lookup"><span data-stu-id="8bafc-151">When a data store connection is opened, the provider can query for information to return the right manifest.</span></span> <span data-ttu-id="8bafc-152">Może to nie być możliwe w scenariuszach w trybie offline, w których informacje o połączeniu są niedostępne lub nie można nawiązać połączenia ze sklepem.</span><span class="sxs-lookup"><span data-stu-id="8bafc-152">This may not be possible in offline scenarios where connection information is not available or when it is not possible to connect to the store.</span></span> <span data-ttu-id="8bafc-153">Zidentyfikuj manifest przy użyciu `ProviderManifestToken` atrybutu `Schema` elementu w pliku SSDL.</span><span class="sxs-lookup"><span data-stu-id="8bafc-153">Identify the manifest by using the `ProviderManifestToken` attribute of the `Schema` element in the .ssdl file.</span></span> <span data-ttu-id="8bafc-154">Nie ma wymaganego formatu dla tego atrybutu; Dostawca wybiera minimalne informacje niezbędne do zidentyfikowania manifestu bez otwierania połączenia z magazynem.</span><span class="sxs-lookup"><span data-stu-id="8bafc-154">There is no required format for this attribute; the provider chooses the minimum information needed to identify a manifest without opening a connection to the store.</span></span>  
  
 <span data-ttu-id="8bafc-155">Przykład:</span><span class="sxs-lookup"><span data-stu-id="8bafc-155">For example:</span></span>  
  
```xml  
<Schema Namespace="Northwind" Provider="System.Data.SqlClient" ProviderManifestToken="2005" xmlns:edm="http://schemas.microsoft.com/ado/2006/04/edm/ssdl" xmlns="http://schemas.microsoft.com/ado/2006/04/edm/ssdl">  
```  
  
## <a name="provider-manifest-programming-model"></a><span data-ttu-id="8bafc-156">Model programowania manifestu dostawcy</span><span class="sxs-lookup"><span data-stu-id="8bafc-156">Provider Manifest Programming Model</span></span>  
 <span data-ttu-id="8bafc-157">Dostawcy pochodzą z <xref:System.Data.Common.DbXmlEnabledProviderManifest>, co umożliwia ich deklaratywne określanie ich manifestów.</span><span class="sxs-lookup"><span data-stu-id="8bafc-157">Providers derive from <xref:System.Data.Common.DbXmlEnabledProviderManifest>, which allows them to specify their manifests declaratively.</span></span> <span data-ttu-id="8bafc-158">Na poniższej ilustracji przedstawiono hierarchię klas dostawcy:</span><span class="sxs-lookup"><span data-stu-id="8bafc-158">The following illustration shows the class hierarchy of a provider:</span></span>  
  
 <span data-ttu-id="8bafc-159">![None](./media/d541eba3-2ee6-4cd1-88f5-89d0b2582a6c.gif "d541eba3-2ee6-4cd1-88f5-89d0b2582a6c")</span><span class="sxs-lookup"><span data-stu-id="8bafc-159">![None](./media/d541eba3-2ee6-4cd1-88f5-89d0b2582a6c.gif "d541eba3-2ee6-4cd1-88f5-89d0b2582a6c")</span></span>  
  
### <a name="discoverability-api"></a><span data-ttu-id="8bafc-160">Interfejs API odnajdywania</span><span class="sxs-lookup"><span data-stu-id="8bafc-160">Discoverability API</span></span>  
 <span data-ttu-id="8bafc-161">Manifest dostawcy jest ładowany przez moduł ładujący metadanych magazynu (StoreItemCollection), przy użyciu połączenia magazynu danych lub tokenu manifestu dostawcy.</span><span class="sxs-lookup"><span data-stu-id="8bafc-161">The provider manifest is loaded by the Store Metadata loader (StoreItemCollection), either by using a data store connection or a provider manifest token.</span></span>  
  
#### <a name="using-a-data-store-connection"></a><span data-ttu-id="8bafc-162">Korzystanie z połączenia magazynu danych</span><span class="sxs-lookup"><span data-stu-id="8bafc-162">Using a Data Store Connection</span></span>  
 <span data-ttu-id="8bafc-163">Gdy jest dostępne połączenie z magazynem danych, <xref:System.Data.Common.DbProviderServices.GetProviderManifestToken%2A?displayProperty=nameWithType> Wywołaj polecenie zwracające token, który jest <xref:System.Data.Common.DbProviderServices.GetProviderManifest%2A> przesyłany do metody <xref:System.Data.Common.DbProviderManifest>, która zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="8bafc-163">When the data store connection is available, call <xref:System.Data.Common.DbProviderServices.GetProviderManifestToken%2A?displayProperty=nameWithType> to return the token that is passed to the <xref:System.Data.Common.DbProviderServices.GetProviderManifest%2A> method, which returns <xref:System.Data.Common.DbProviderManifest>.</span></span> <span data-ttu-id="8bafc-164">Ta metoda deleguje do implementacji `GetDbProviderManifestToken`dostawcy.</span><span class="sxs-lookup"><span data-stu-id="8bafc-164">This method delegates to the provider's implementation of `GetDbProviderManifestToken`.</span></span>  
  
```csharp
public string GetProviderManifestToken(DbConnection connection);  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
#### <a name="using-a-provider-manifest-token"></a><span data-ttu-id="8bafc-165">Korzystanie z tokenu manifestu dostawcy</span><span class="sxs-lookup"><span data-stu-id="8bafc-165">Using a Provider Manifest Token</span></span>  
 <span data-ttu-id="8bafc-166">W przypadku scenariusza offline token jest wybierany z reprezentacji SSDL.</span><span class="sxs-lookup"><span data-stu-id="8bafc-166">For the offline scenario, the token is picked from SSDL representation.</span></span> <span data-ttu-id="8bafc-167">SSDL pozwala określić ProviderManifestToken (zobacz [element Schema (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl) , aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="8bafc-167">The SSDL allows you to specify a ProviderManifestToken (see [Schema Element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl) for more information).</span></span> <span data-ttu-id="8bafc-168">Na przykład jeśli nie można otworzyć połączenia, plik SSDL ma token manifestu dostawcy, który określa informacje o manifeście.</span><span class="sxs-lookup"><span data-stu-id="8bafc-168">For example, if a connection cannot be opened, the SSDL has a provider manifest token that specifies information about the manifest.</span></span>  
  
```  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
### <a name="provider-manifest-schema"></a><span data-ttu-id="8bafc-169">Schemat manifestu dostawcy</span><span class="sxs-lookup"><span data-stu-id="8bafc-169">Provider Manifest Schema</span></span>  
 <span data-ttu-id="8bafc-170">Schemat informacji zdefiniowanych dla każdego dostawcy zawiera informacje statyczne, które mają być używane przez metadane:</span><span class="sxs-lookup"><span data-stu-id="8bafc-170">The schema of information defined for each provider contains the static information to be consumed by metadata:</span></span>  
  
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
  
#### <a name="types-node"></a><span data-ttu-id="8bafc-171">Węzeł typów</span><span class="sxs-lookup"><span data-stu-id="8bafc-171">Types Node</span></span>  
 <span data-ttu-id="8bafc-172">Węzeł typy w manifeście dostawcy zawiera informacje o typach, które są obsługiwane natywnie przez magazyn danych lub przez dostawcę.</span><span class="sxs-lookup"><span data-stu-id="8bafc-172">The Types node in the provider manifest contains information about the Types that are supported natively by the data store or through the provider.</span></span>  
  
##### <a name="type-node"></a><span data-ttu-id="8bafc-173">Węzeł typu</span><span class="sxs-lookup"><span data-stu-id="8bafc-173">Type Node</span></span>  
 <span data-ttu-id="8bafc-174">Każdy węzeł typu definiuje typ dostawcy w kategoriach modelu EDM.</span><span class="sxs-lookup"><span data-stu-id="8bafc-174">Each Type node defines a provider type in terms of EDM.</span></span> <span data-ttu-id="8bafc-175">Węzeł typu zawiera opis nazwy typu dostawcy i informacje związane z typem modelu, który jest mapowany do i aspektami opisującymi tego mapowania typu.</span><span class="sxs-lookup"><span data-stu-id="8bafc-175">The Type node describes the name of the provider type, and information related to the model type it maps to and facets to describe that type mapping.</span></span>  
  
 <span data-ttu-id="8bafc-176">Aby można było wyrazić te informacje o typie w manifeście dostawcy, każda deklaracja TypeInformation musi definiować kilka opisów aspektów dla każdego typu:</span><span class="sxs-lookup"><span data-stu-id="8bafc-176">In order to express this type information in the provider manifest, each TypeInformation declaration must define several facet descriptions for each Type:</span></span>  
  
|<span data-ttu-id="8bafc-177">Nazwa atrybutu</span><span class="sxs-lookup"><span data-stu-id="8bafc-177">Attribute Name</span></span>|<span data-ttu-id="8bafc-178">Typ danych</span><span class="sxs-lookup"><span data-stu-id="8bafc-178">Data Type</span></span>|<span data-ttu-id="8bafc-179">Wymagane</span><span class="sxs-lookup"><span data-stu-id="8bafc-179">Required</span></span>|<span data-ttu-id="8bafc-180">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="8bafc-180">Default Value</span></span>|<span data-ttu-id="8bafc-181">Opis</span><span class="sxs-lookup"><span data-stu-id="8bafc-181">Description</span></span>|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|<span data-ttu-id="8bafc-182">Nazwa</span><span class="sxs-lookup"><span data-stu-id="8bafc-182">Name</span></span>|<span data-ttu-id="8bafc-183">String</span><span class="sxs-lookup"><span data-stu-id="8bafc-183">String</span></span>|<span data-ttu-id="8bafc-184">Tak</span><span class="sxs-lookup"><span data-stu-id="8bafc-184">Yes</span></span>|<span data-ttu-id="8bafc-185">n/d</span><span class="sxs-lookup"><span data-stu-id="8bafc-185">n/a</span></span>|<span data-ttu-id="8bafc-186">Nazwa typu danych specyficznych dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="8bafc-186">Provider-specific data type name</span></span>|  
|<span data-ttu-id="8bafc-187">PrimitiveTypeKind</span><span class="sxs-lookup"><span data-stu-id="8bafc-187">PrimitiveTypeKind</span></span>|<span data-ttu-id="8bafc-188">PrimitiveTypeKind</span><span class="sxs-lookup"><span data-stu-id="8bafc-188">PrimitiveTypeKind</span></span>|<span data-ttu-id="8bafc-189">Tak</span><span class="sxs-lookup"><span data-stu-id="8bafc-189">Yes</span></span>|<span data-ttu-id="8bafc-190">n/d</span><span class="sxs-lookup"><span data-stu-id="8bafc-190">n/a</span></span>|<span data-ttu-id="8bafc-191">Nazwa typu modelu EDM</span><span class="sxs-lookup"><span data-stu-id="8bafc-191">EDM type name</span></span>|  
  
###### <a name="function-node"></a><span data-ttu-id="8bafc-192">Węzeł funkcji</span><span class="sxs-lookup"><span data-stu-id="8bafc-192">Function Node</span></span>  
 <span data-ttu-id="8bafc-193">Każda funkcja definiuje pojedynczą funkcję dostępną za pomocą dostawcy.</span><span class="sxs-lookup"><span data-stu-id="8bafc-193">Each Function defines a single function available through the provider.</span></span>  
  
|<span data-ttu-id="8bafc-194">Nazwa atrybutu</span><span class="sxs-lookup"><span data-stu-id="8bafc-194">Attribute Name</span></span>|<span data-ttu-id="8bafc-195">Typ danych</span><span class="sxs-lookup"><span data-stu-id="8bafc-195">Data Type</span></span>|<span data-ttu-id="8bafc-196">Wymagane</span><span class="sxs-lookup"><span data-stu-id="8bafc-196">Required</span></span>|<span data-ttu-id="8bafc-197">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="8bafc-197">Default Value</span></span>|<span data-ttu-id="8bafc-198">Opis</span><span class="sxs-lookup"><span data-stu-id="8bafc-198">Description</span></span>|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|<span data-ttu-id="8bafc-199">Nazwa</span><span class="sxs-lookup"><span data-stu-id="8bafc-199">Name</span></span>|<span data-ttu-id="8bafc-200">String</span><span class="sxs-lookup"><span data-stu-id="8bafc-200">String</span></span>|<span data-ttu-id="8bafc-201">Tak</span><span class="sxs-lookup"><span data-stu-id="8bafc-201">Yes</span></span>|<span data-ttu-id="8bafc-202">n/d</span><span class="sxs-lookup"><span data-stu-id="8bafc-202">n/a</span></span>|<span data-ttu-id="8bafc-203">Identyfikator/nazwa funkcji</span><span class="sxs-lookup"><span data-stu-id="8bafc-203">Identifier/name of the function</span></span>|  
|<span data-ttu-id="8bafc-204">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8bafc-204">ReturnType</span></span>|<span data-ttu-id="8bafc-205">String</span><span class="sxs-lookup"><span data-stu-id="8bafc-205">String</span></span>|<span data-ttu-id="8bafc-206">Nie</span><span class="sxs-lookup"><span data-stu-id="8bafc-206">No</span></span>|<span data-ttu-id="8bafc-207">Pozycję</span><span class="sxs-lookup"><span data-stu-id="8bafc-207">Void</span></span>|<span data-ttu-id="8bafc-208">Typ zwracany funkcji modelu EDM</span><span class="sxs-lookup"><span data-stu-id="8bafc-208">The EDM return type of the function</span></span>|  
|<span data-ttu-id="8bafc-209">Agregowanie</span><span class="sxs-lookup"><span data-stu-id="8bafc-209">Aggregate</span></span>|<span data-ttu-id="8bafc-210">Boolean</span><span class="sxs-lookup"><span data-stu-id="8bafc-210">Boolean</span></span>|<span data-ttu-id="8bafc-211">Nie</span><span class="sxs-lookup"><span data-stu-id="8bafc-211">No</span></span>|<span data-ttu-id="8bafc-212">False</span><span class="sxs-lookup"><span data-stu-id="8bafc-212">False</span></span>|<span data-ttu-id="8bafc-213">True, jeśli funkcja jest funkcją agregującą</span><span class="sxs-lookup"><span data-stu-id="8bafc-213">True if the function is an aggregate function</span></span>|  
|<span data-ttu-id="8bafc-214">Wbudowan</span><span class="sxs-lookup"><span data-stu-id="8bafc-214">BuiltIn</span></span>|<span data-ttu-id="8bafc-215">Boolean</span><span class="sxs-lookup"><span data-stu-id="8bafc-215">Boolean</span></span>|<span data-ttu-id="8bafc-216">Nie</span><span class="sxs-lookup"><span data-stu-id="8bafc-216">No</span></span>|<span data-ttu-id="8bafc-217">Prawda</span><span class="sxs-lookup"><span data-stu-id="8bafc-217">True</span></span>|<span data-ttu-id="8bafc-218">Prawda, jeśli funkcja jest wbudowana w magazyn danych</span><span class="sxs-lookup"><span data-stu-id="8bafc-218">True if the function is built into the data store</span></span>|  
|<span data-ttu-id="8bafc-219">StoreFunctionName</span><span class="sxs-lookup"><span data-stu-id="8bafc-219">StoreFunctionName</span></span>|<span data-ttu-id="8bafc-220">String</span><span class="sxs-lookup"><span data-stu-id="8bafc-220">String</span></span>|<span data-ttu-id="8bafc-221">Nie</span><span class="sxs-lookup"><span data-stu-id="8bafc-221">No</span></span>|<span data-ttu-id="8bafc-222">\<> Nazwy</span><span class="sxs-lookup"><span data-stu-id="8bafc-222">\<Name></span></span>|<span data-ttu-id="8bafc-223">Nazwa funkcji w magazynie danych.</span><span class="sxs-lookup"><span data-stu-id="8bafc-223">Function Name in the data store.</span></span>  <span data-ttu-id="8bafc-224">Umożliwia przekierowanie nazw funkcji.</span><span class="sxs-lookup"><span data-stu-id="8bafc-224">Allows for a level of redirection of function names.</span></span>|  
|<span data-ttu-id="8bafc-225">NiladicFunction</span><span class="sxs-lookup"><span data-stu-id="8bafc-225">NiladicFunction</span></span>|<span data-ttu-id="8bafc-226">Boolean</span><span class="sxs-lookup"><span data-stu-id="8bafc-226">Boolean</span></span>|<span data-ttu-id="8bafc-227">Nie</span><span class="sxs-lookup"><span data-stu-id="8bafc-227">No</span></span>|<span data-ttu-id="8bafc-228">False</span><span class="sxs-lookup"><span data-stu-id="8bafc-228">False</span></span>|<span data-ttu-id="8bafc-229">Prawda, jeśli funkcja nie wymaga parametrów i jest wywoływana bez żadnych parametrów</span><span class="sxs-lookup"><span data-stu-id="8bafc-229">True if the function does not require parameters and is called without any parameters</span></span>|  
|<span data-ttu-id="8bafc-230">ParameterType</span><span class="sxs-lookup"><span data-stu-id="8bafc-230">ParameterType</span></span><br /><br /> <span data-ttu-id="8bafc-231">Semantyki</span><span class="sxs-lookup"><span data-stu-id="8bafc-231">Semantics</span></span>|<span data-ttu-id="8bafc-232">ParameterSemantics</span><span class="sxs-lookup"><span data-stu-id="8bafc-232">ParameterSemantics</span></span>|<span data-ttu-id="8bafc-233">Nie</span><span class="sxs-lookup"><span data-stu-id="8bafc-233">No</span></span>|<span data-ttu-id="8bafc-234">AllowImplicit</span><span class="sxs-lookup"><span data-stu-id="8bafc-234">AllowImplicit</span></span><br /><br /> <span data-ttu-id="8bafc-235">Konwersja</span><span class="sxs-lookup"><span data-stu-id="8bafc-235">Conversion</span></span>|<span data-ttu-id="8bafc-236">Wybór sposobu postępowania z zastępowaniem typu parametru przez potok zapytania:</span><span class="sxs-lookup"><span data-stu-id="8bafc-236">Choice of how the query pipeline should deal with parameter type substitution:</span></span><br /><br /> <span data-ttu-id="8bafc-237">- ExactMatchOnly</span><span class="sxs-lookup"><span data-stu-id="8bafc-237">-   ExactMatchOnly</span></span><br /><span data-ttu-id="8bafc-238">- AllowImplicitPromotion</span><span class="sxs-lookup"><span data-stu-id="8bafc-238">-   AllowImplicitPromotion</span></span><br /><span data-ttu-id="8bafc-239">- AllowImplicitConversion</span><span class="sxs-lookup"><span data-stu-id="8bafc-239">-   AllowImplicitConversion</span></span>|  
  
 <span data-ttu-id="8bafc-240">**Węzeł parametrów**</span><span class="sxs-lookup"><span data-stu-id="8bafc-240">**Parameters Node**</span></span>  
  
 <span data-ttu-id="8bafc-241">Każda funkcja ma kolekcję z co najmniej jednym węzłem parametrów.</span><span class="sxs-lookup"><span data-stu-id="8bafc-241">Each function has a collection of one or more Parameter nodes.</span></span>  
  
|<span data-ttu-id="8bafc-242">Nazwa atrybutu</span><span class="sxs-lookup"><span data-stu-id="8bafc-242">Attribute Name</span></span>|<span data-ttu-id="8bafc-243">Typ danych</span><span class="sxs-lookup"><span data-stu-id="8bafc-243">Data Type</span></span>|<span data-ttu-id="8bafc-244">Wymagane</span><span class="sxs-lookup"><span data-stu-id="8bafc-244">Required</span></span>|<span data-ttu-id="8bafc-245">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="8bafc-245">Default Value</span></span>|<span data-ttu-id="8bafc-246">Opis</span><span class="sxs-lookup"><span data-stu-id="8bafc-246">Description</span></span>|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|<span data-ttu-id="8bafc-247">Nazwa</span><span class="sxs-lookup"><span data-stu-id="8bafc-247">Name</span></span>|<span data-ttu-id="8bafc-248">String</span><span class="sxs-lookup"><span data-stu-id="8bafc-248">String</span></span>|<span data-ttu-id="8bafc-249">Tak</span><span class="sxs-lookup"><span data-stu-id="8bafc-249">Yes</span></span>|<span data-ttu-id="8bafc-250">n/d</span><span class="sxs-lookup"><span data-stu-id="8bafc-250">n/a</span></span>|<span data-ttu-id="8bafc-251">Identyfikator/Nazwa parametru.</span><span class="sxs-lookup"><span data-stu-id="8bafc-251">Identifier/name of the parameter.</span></span>|  
|<span data-ttu-id="8bafc-252">Typ</span><span class="sxs-lookup"><span data-stu-id="8bafc-252">Type</span></span>|<span data-ttu-id="8bafc-253">String</span><span class="sxs-lookup"><span data-stu-id="8bafc-253">String</span></span>|<span data-ttu-id="8bafc-254">Tak</span><span class="sxs-lookup"><span data-stu-id="8bafc-254">Yes</span></span>|<span data-ttu-id="8bafc-255">n/d</span><span class="sxs-lookup"><span data-stu-id="8bafc-255">n/a</span></span>|<span data-ttu-id="8bafc-256">Typ modelu EDM.</span><span class="sxs-lookup"><span data-stu-id="8bafc-256">The EDM type of the parameter.</span></span>|  
|<span data-ttu-id="8bafc-257">Tryb</span><span class="sxs-lookup"><span data-stu-id="8bafc-257">Mode</span></span>|<span data-ttu-id="8bafc-258">Parametr</span><span class="sxs-lookup"><span data-stu-id="8bafc-258">Parameter</span></span><br /><br /> <span data-ttu-id="8bafc-259">Kierunek</span><span class="sxs-lookup"><span data-stu-id="8bafc-259">Direction</span></span>|<span data-ttu-id="8bafc-260">Tak</span><span class="sxs-lookup"><span data-stu-id="8bafc-260">Yes</span></span>|<span data-ttu-id="8bafc-261">n/d</span><span class="sxs-lookup"><span data-stu-id="8bafc-261">n/a</span></span>|<span data-ttu-id="8bafc-262">Kierunek parametru:</span><span class="sxs-lookup"><span data-stu-id="8bafc-262">Direction of parameter:</span></span><br /><br /> <span data-ttu-id="8bafc-263">-in</span><span class="sxs-lookup"><span data-stu-id="8bafc-263">-   in</span></span><br /><span data-ttu-id="8bafc-264">-out</span><span class="sxs-lookup"><span data-stu-id="8bafc-264">-   out</span></span><br /><span data-ttu-id="8bafc-265">-Inout</span><span class="sxs-lookup"><span data-stu-id="8bafc-265">-   inout</span></span>|  
  
##### <a name="namespace-attribute"></a><span data-ttu-id="8bafc-266">Namespace — atrybut</span><span class="sxs-lookup"><span data-stu-id="8bafc-266">Namespace Attribute</span></span>  
 <span data-ttu-id="8bafc-267">Każdy dostawca magazynu danych musi definiować przestrzeń nazw lub grupę przestrzeni nazw, aby uzyskać informacje zdefiniowane w manifeście.</span><span class="sxs-lookup"><span data-stu-id="8bafc-267">Each data store provider must define a namespace or group of namespaces for information defined in the manifest.</span></span> <span data-ttu-id="8bafc-268">Ta przestrzeń nazw może być używana w Entity SQL zapytania do rozpoznawania nazw funkcji i typów.</span><span class="sxs-lookup"><span data-stu-id="8bafc-268">This namespace can be used in Entity SQL queries to resolve names of functions and types.</span></span> <span data-ttu-id="8bafc-269">Przykład: SqlServer.</span><span class="sxs-lookup"><span data-stu-id="8bafc-269">For instance: SqlServer.</span></span> <span data-ttu-id="8bafc-270">Ta przestrzeń nazw musi być różna od kanonicznej przestrzeni nazw, EDM zdefiniowanej przez usługi jednostek dla funkcji standardowych, które mają być obsługiwane przez Entity SQL zapytań.</span><span class="sxs-lookup"><span data-stu-id="8bafc-270">That namespace must be different from the canonical namespace, EDM, defined by Entity Services for standard functions to be supported by Entity SQL queries.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bafc-271">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8bafc-271">See also</span></span>

- [<span data-ttu-id="8bafc-272">Pisanie dostawcy danych programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="8bafc-272">Writing an Entity Framework Data Provider</span></span>](writing-an-ef-data-provider.md)
