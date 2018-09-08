---
title: Dostosowywanie kanału informacyjnego (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, feeds
- WCF Data Services, Atom protocol
- Atom Publishing Protocol [WCF Data Services]
- WCF Data Services, customizing feeds
ms.assetid: 0d1a39bc-6462-4683-bd7d-e74e0fd28a85
ms.openlocfilehash: 1922351ffb11d5ff6541ef22dee623c20d153d6a
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44137801"
---
# <a name="feed-customization-wcf-data-services"></a>Dostosowywanie kanału informacyjnego (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] używa [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] aby uwidocznić dane jako źródło danych. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] obsługuje formaty Atom i JavaScript Object Notation (JSON) dla źródła danych. Gdy używasz źródła danych, Atom [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] zapewnia standardową metodę do serializowania danych, takich jak jednostek i relacji w formacie XML, które mogą być zawarte w treści komunikatu HTTP. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Definiuje mapowanie właściwości jednostki domyślne między danych, które znajduje się w jednostkach i elementów Atom. Aby uzyskać więcej informacji, zobacz [OData: Atom Format](https://go.microsoft.com/fwlink/?LinkID=185794).  
  
 Może być scenariusz aplikacji, która wymaga, że danych właściwości zwracane przez usługę danych można serializować w sposób dostosowany, a nie w standardzie format źródła. Za pomocą [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)], można dostosować serializacji w danych kanału informacyjnego, tak, aby właściwości jednostki mogą być mapowane do nieużywanych elementów i atrybutów wpisu lub elementy niestandardowe wpisu w źródle danych.  
  
> [!NOTE]
>  Dostosowywanie źródła danych jest obsługiwana tylko dla źródła danych Atom. Niestandardowe źródła danych nie są zwracane, zleconą formatu JSON dla zwróconego źródła danych.  
  
 Za pomocą [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], można zdefiniować mapowania alternatywnych właściwości jednostki dla ładunek Atom przez ręczne zastosowanie atrybutów do typów jednostek w modelu danych. Dostawca źródła danych, usługi danych określa, jak należy zastosować te atrybuty.  
  
> [!IMPORTANT]
>  Podczas definiowania niestandardowego źródła danych musi zagwarantować, że wszystkie właściwości jednostki, które mają niestandardowe mapowania zdefiniowane są uwzględniane w projekcji. Gdy właściwość zamapowanego jednostki nie jest uwzględniony w projekcji, może dojść do utraty danych. Aby uzyskać więcej informacji, zobacz [projekcje zapytania](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md).  
  
## <a name="customizing-feeds-with-the-entity-framework-provider"></a>Dostosowywanie źródła danych za pomocą dostawcy programu Entity Framework  
 Model danych używany z [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] dostawcy jest reprezentowana jako kod XML w pliku edmx. W tym przypadku atrybutów, które definiują niestandardowego źródła danych są dodawane do `EntityType` i `Property` elementy, które reprezentują typy jednostek i właściwości w modelu danych. Te atrybuty Dostosowywanie źródła danych nie są zdefiniowane w [ \[MC CSDL\]: koncepcyjny formatu pliku definicji schematu](https://go.microsoft.com/fwlink/?LinkId=159072), czyli format, [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] używa dostawcy w celu zdefiniowania modelu danych. W związku z tym, należy zadeklarować atrybutów dostosowywania kanału informacyjnego w przestrzeni nazw określonego schematu, która jest zdefiniowana jako `m="http://schemas.microsoft.com/ado/2007/08/dataservices/metadata"`. Poniższy fragment XML zawiera atrybuty kanału informacyjnego dostosowania stosowane do `Property` elementy `Products` typu jednostki, które definiują `ProductName`, `ReorderLevel`, i `UnitsInStock` właściwości.  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedAttributes](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/northwind.csdl#edmfeedattributes)]  
  
 Te atrybuty generuje następujące dane niestandardowe źródło danych dla `Products` zestawu jednostek. W kanale, dostosowanych danych `ProductName` wartość właściwości jest wyświetlana zarówno w `author` elementu i `ProductName` element właściwości i `UnitsInStock` właściwości są wyświetlane w element niestandardowy, który ma własną unikatową przestrzeń nazw z `ReorderLevel` właściwości jako atrybut:  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedResultProduct](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/edmfeedresult.xml#edmfeedresultproduct)]  
  
 Aby uzyskać więcej informacji, zobacz [porady: Dostosowywanie źródła danych przy użyciu dostawcy programu Entity Framework](../../../../docs/framework/data/wcf/how-to-customize-feeds-with-ef-provider-wcf-data-services.md).  
  
> [!NOTE]
>  Ponieważ rozszerzenia do modelu danych nie są obsługiwane przez Projektanta obiektów, należy ręcznie zmodyfikować plik XML, który zawiera model danych. Aby uzyskać więcej informacji o plik edmx, który jest generowany przez [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] narzędzia, zobacz [Omówienie pliku edmx](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4).  
  
### <a name="custom-feed-attributes"></a>Atrybuty źródła niestandardowego  
 W poniższej tabeli przedstawiono atrybuty XML, które Dostosowywanie źródła danych, które można dodać do język definicji schematu koncepcyjnego (CSDL), który definiuje model danych. Te atrybuty są odpowiednikiem właściwości <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> używany przy użyciu dostawcy odbicia.  
  
|Nazwa atrybutu|Opis|  
|--------------------|-----------------|  
|`FC_ContentKind`|Wskazuje typ zawartości. Następujące słowa kluczowe zdefiniować typy zawartości syndykacji.<br /><br /> `text:` Wartość właściwości jest wyświetlana w źródle danych jako tekst.<br /><br /> `html:` Wartość właściwości jest wyświetlany w źródle danych w formacie HTML.<br /><br /> `xhtml:` Wartość właściwości jest wyświetlana w źródle danych w formacie HTML w formacie XML.<br /><br /> Te słowa kluczowe są odpowiednikiem wartości <xref:System.Data.Services.Common.SyndicationTextContentKind> wyliczenia używane przy użyciu dostawcy odbicia.<br /><br /> Ten atrybut nie jest obsługiwane w przypadku `FC_NsPrefix` i `FC_NsUri` atrybuty są używane.<br /><br /> Po określeniu wartości `xhtml` dla `FC_ContentKind` atrybut, upewnij się, że wartość właściwości zawiera kod XML poprawnie sformatowana. Usługa danych zwraca wartość, bez przeprowadzania żadnych przekształcenia. Upewnij się że wszelkie prefiksy — element XML w pliku XML zwrócony identyfikator URI przestrzeni nazw i prefiksu zdefiniowane w źródle danych zamapowanych.|  
|`FC_KeepInContent`|Wskazuje, że wartość właściwości odwołania powinny być dołączone, zarówno w sekcji zawartość źródła danych, jak i w mapowanych lokalizacji. Prawidłowe wartości to `true` i `false`. Aby wynikowy kanału informacyjnego zapewniającej zgodność z wcześniejszymi wersjami programu [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], określ wartość `true` aby upewnić się, że wartość znajduje się w sekcji zawartość kanału informacyjnego.|  
|`FC_NsPrefix`|Prefiks przestrzeni nazw elementu XML mapowania bez syndykacji. Ten atrybut musi być używany z `FC_NsUri` atrybutu i nie można używać z `FC_ContentKind` atrybutu.|  
|`FC_NsUri`|Identyfikator URI przestrzeni nazw elementu XML mapowania bez syndykacji. Ten atrybut musi być używany z `FC_NsPrefix` atrybutu i nie można używać z `FC_ContentKind` atrybutu.|  
|`FC_SourcePath`|Ścieżka właściwości jednostki, do którego należy to źródło danych mapowanie zostanie zastosowana reguła. Ten atrybut jest obsługiwana tylko, gdy jest używana w `EntityType` elementu.<br /><br /> <xref:System.Data.Services.Common.EntityPropertyMappingAttribute.SourcePath%2A> Właściwość nie może odwoływać się bezpośrednio do typu złożonego. W przypadku typów złożonych, należy użyć wyrażenie ścieżki gdzie nazwy właściwości są oddzielone znakiem ukośnika odwrotnego (`/`) znaków. Na przykład, następujące wartości są dozwolone dla typu jednostki `Person` z właściwością liczby całkowitej `Age` i właściwości złożonej<br /><br /> `Address`:<br /><br /> `Age`<br /><br /> `Address/Street`<br /><br /> <xref:System.Data.Services.Common.EntityPropertyMappingAttribute.SourcePath%2A> Nie można ustawić właściwości wartość, która zawiera spację lub jakikolwiek inny znak, który jest nieprawidłowy w nazwie właściwości.|  
|`FC_TargetPath`|Nazwa elementu docelowego wynikowy źródła danych, aby zamapować właściwość. Ten element może być element zdefiniowany przez specyfikację Atom lub element niestandardowy.<br /><br /> Następujące słowa kluczowe są syndykacji wstępnie zdefiniowane wartości ścieżkę docelową, prowadzące do określonej lokalizacji w [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych.<br /><br /> `SyndicationAuthorEmail:` `atom:email` Element podrzędny elementu `atom:author` elementu.<br /><br /> `SyndicationAuthorName:` `atom:name` Element podrzędny elementu `atom:author` elementu.<br /><br /> `SyndicationAuthorUri:` `atom:uri` Element podrzędny elementu `atom:author` elementu.<br /><br /> `SyndicationContributorEmail:` `atom:email` Element podrzędny elementu `atom:contributor` elementu.<br /><br /> `SyndicationContributorName:` `atom:name` Element podrzędny elementu `atom:contributor` elementu.<br /><br /> `SyndicationContributorUri:` `atom:uri` Element podrzędny elementu `atom:contributor` elementu.<br /><br /> `SyndicationCustomProperty:` Element właściwości niestandardowej. Podczas mapowania do elementu niestandardowego, element docelowy musi być wyrażenie ścieżki, w którym elementy zagnieżdżone są oddzielone znakiem ukośnika odwrotnego (`/`) i atrybuty są określone przez handlowe "i" (`@`). W poniższym przykładzie ciąg `UnitsInStock/@ReorderLevel` mapuje wartości właściwości do atrybutu o nazwie `ReorderLevel` na element podrzędny o nazwie `UnitsInStock` głównego elementu wpisu.<br /><br /> `<Property Name="ReorderLevel" Type="Int16"               m:FC_TargetPath="UnitsInStock/@ReorderLevel"               m:FC_NsPrefix="Northwind"               m:FC_NsUri="http://schemas.examples.microsoft.com/dataservices"               m:FC_KeepInContent="false"               />`<br /><br /> Gdy element docelowy jest nazwą elementu niestandardowego `FC_NsPrefix` i `FC_NsUri` atrybutów musi być także określona.<br /><br /> `SyndicationPublished:` `atom:published` Elementu.<br /><br /> `SyndicationRights:` `atom:rights` Elementu.<br /><br /> `SyndicationSummary:` `atom:summary` Elementu.<br /><br /> `SyndicationTitle:` `atom:title` Elementu.<br /><br /> `SyndicationUpdated:` `atom:updated` Elementu.<br /><br /> Te słowa kluczowe są odpowiednikiem wartości <xref:System.Data.Services.Common.SyndicationItemProperty> wyliczenia używane przy użyciu dostawcy odbicia.|  
  
> [!NOTE]
>  Nazwy i wartości atrybutów jest rozróżniana wielkość liter. Atrybuty mogą być stosowane do `EntityType` element lub do jednej lub kilku `Property` elementów, ale nie do obu.  
  
## <a name="customizing-feeds-with-the-reflection-provider"></a>Dostosowywanie źródła danych za pomocą dostawcy odbicia  
 Aby dostosować źródła danych dla modelu danych, który został wdrożony przy użyciu dostawcy odbicia, należy dodać co najmniej jedno z <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> atrybutu do klas, które reprezentują typy jednostek w modelu danych. Właściwości <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> odpowiadają klasy atrybutów Dostosowywanie źródła danych, które są opisane w poprzedniej sekcji. Oto przykład deklaracja `Order` typu z niestandardowego źródła danych mapowanie zdefiniowane dla obu właściwości.  
  
> [!NOTE]
>  Model danych w tym przykładzie jest zdefiniowana w temacie [porady: Tworzenie usługi danych przy użyciu dostawcy odbicia](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md).  
  
 [!code-csharp[Astoria Custom Feeds#CustomOrderFeed](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria custom feeds/cs/orderitems.svc.cs#customorderfeed)]
 [!code-vb[Astoria Custom Feeds#CustomOrderFeed](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria custom feeds/vb/orderitems.svc.vb#customorderfeed)]  
  
 Te atrybuty generuje następujące dane niestandardowe źródło danych dla `Orders` zestawu jednostek. W tym dostosowane kanału informacyjnego, `OrderId` wartość właściwości jest wyświetlana tylko w `title` elementu `entry` i `Customer` Wyświetla wartość właściwości, zarówno w `author` elementu i `Customer` element właściwości:  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResult](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/iqueryablefeedresult.xml#iqueryablefeedresult)]  
  
 Aby uzyskać więcej informacji, zobacz [porady: Dostosowywanie źródła danych za pomocą dostawcy odbicia](../../../../docs/framework/data/wcf/how-to-customize-feeds-with-the-reflection-provider-wcf-data-services.md).  
  
## <a name="customizing-feeds-with-a-custom-data-service-provider"></a>Dostosowywanie źródła danych za pomocą dostawcy usług dane niestandardowe  
 Dostosowywanie źródła dla modelu danych, zdefiniowane przy użyciu dostawcy usługi danych niestandardowych jest zdefiniowany dla typu zasobu, wywołując <xref:System.Data.Services.Providers.ResourceType.AddEntityPropertyMappingAttribute%2A> na <xref:System.Data.Services.Providers.ResourceType> który reprezentuje typ jednostki w modelu danych. Aby uzyskać więcej informacji, zobacz [dostawcy usługi danych niestandardowych](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md).  
  
## <a name="consuming-custom-feeds"></a>Korzystanie z niestandardowego źródła danych  
 Gdy aplikacja wykorzystuje bezpośrednio [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanału informacyjnego, musi być w stanie przetworzyć żadnych niestandardowych elementów i atrybutów w zwróconego źródła danych. Jeśli udało Ci się wdrożyć niestandardowego źródła danych w modelu danych, niezależnie od tego dostawcy danych usług `$metadata` punktu końcowego zwraca źródła niestandardowego informacji jak atrybutów niestandardowych, które kanału informacyjnego w CSDL zwracane przez usługę danych. Kiedy używasz **Dodaj odwołanie do usługi** okna dialogowego lub [datasvcutil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) narzędzie do generowania klas usługi danych klienta, kanał informacyjny niestandardowe atrybuty są używane w celu zagwarantowania, że żądania i odpowiedzi Usługa danych są obsługiwane poprawnie.  
  
## <a name="feed-customization-considerations"></a>Zagadnienia dotyczące dostosowywania kanału informacyjnego  
 Należy rozważyć następujące podczas definiowania niestandardowe mapowania źródła danych.  
  
-   [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Klienta traktuje zamapowane elementy w kanale informacyjnym puste zawierających tylko biały znak. W związku z tym zamapowane elementy, które zawiera białych znaków nie są zmaterializowanego na kliencie przy użyciu tego samego biały. Aby zachować ten biały na komputerze klienckim, należy ustawić wartość `KeepInContext` do `true` w atrybucie mapowania źródła danych.  
  
## <a name="versioning-requirements"></a>Wymagania dotyczące przechowywania wersji  
 Dostosowywanie kanału informacyjnego ma [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokołu wymagań dotyczących przechowywania wersji:  
  
-   Dostosowywanie kanału informacyjnego wymaga tego klienta i dane usługi pomocy technicznej wersji 2.0 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokołu i nowszych wersjach.  
  
 Aby uzyskać więcej informacji, zobacz [przechowywanie wersji usługi danych](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Dostawca odbicia](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)  
 [Dostawca programu Entity Framework](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)
