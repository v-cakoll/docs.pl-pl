---
title: Dostosowywanie kanału informacyjnego (Usługi danych programu WCF)
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
ms.openlocfilehash: baa97bb32f8af4e034a78b44f9776be42c204b80
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918735"
---
# <a name="feed-customization-wcf-data-services"></a>Dostosowywanie kanału informacyjnego (Usługi danych programu WCF)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]używa programu [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] , aby udostępnić dane jako źródło danych. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]obsługuje formaty Atom i JavaScript Object Notation (JSON) dla strumieniowych źródeł danych. W przypadku korzystania z kanału informacyjnego [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Atom, program zapewnia standardową metodę serializacji danych, takich jak jednostki i relacje, do formatu XML, który może zostać uwzględniony w treści wiadomości HTTP. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]definiuje domyślne mapowanie właściwości jednostki między danymi zawartymi w jednostkach i elementach Atom. Aby uzyskać więcej informacji, [zobacz OData: Format](https://go.microsoft.com/fwlink/?LinkID=185794)Atom.  
  
 Może istnieć scenariusz aplikacji, który wymaga, aby dane właściwości zwrócone przez usługę danych były serializowane w sposób dostosowany, a nie w standardowym formacie kanału informacyjnego. Za [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]pomocą programu można dostosować serializację w strumieniowym źródle danych, tak aby właściwości jednostki mogły być mapowane do nieużywanych elementów i atrybutów wpisu lub do niestandardowych elementów wpisu w kanale informacyjnym.  
  
> [!NOTE]
> Dostosowanie kanału informacyjnego jest obsługiwane tylko dla kanałów informacyjnych Atom. Niestandardowe źródła danych nie są zwracane, gdy wymagany jest format JSON dla zwracanego źródła danych.  
  
 Za [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]pomocą można zdefiniować alternatywne mapowanie właściwości jednostki dla ładunku Atom, ręcznie stosując atrybuty do typów jednostek w modelu danych. Dostawca źródła danych usługi danych określa, jak należy zastosować te atrybuty.  
  
> [!IMPORTANT]
> Podczas definiowania niestandardowych kanałów informacyjnych należy zagwarantować, że wszystkie właściwości jednostki, które mają zdefiniowane mapowania niestandardowe, są uwzględniane w projekcji. Gdy właściwość mapowanego obiektu nie jest uwzględniona w projekcji, może dojść do utraty danych. Aby uzyskać więcej informacji, zobacz [projekcje zapytań](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md).  
  
## <a name="customizing-feeds-with-the-entity-framework-provider"></a>Dostosowywanie kanałów informacyjnych za pomocą dostawcy Entity Framework  
 Model danych używany z [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] dostawcą jest reprezentowany jako XML w pliku. edmx. W takim przypadku atrybuty definiujące niestandardowe źródła są dodawane do `EntityType` elementów i `Property` , które reprezentują typy jednostek i właściwości w modelu danych. Te atrybuty dostosowania kanału informacyjnego nie są [zdefiniowane w \[MC\]-CSDL: Koncepcyjny format](https://go.microsoft.com/fwlink/?LinkId=159072)pliku definicji schematu, który jest formatem [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] używanym przez dostawcę do definiowania modelu danych. W związku z tym należy zadeklarować atrybuty dostosowania kanału informacyjnego w określonej przestrzeni nazw schematu, `m="http://schemas.microsoft.com/ado/2007/08/dataservices/metadata"`która jest zdefiniowana jako. Poniższy fragment kodu XML przedstawia atrybuty dostosowania źródła zastosowane do `Property` elementów `Products` typu `ProductName`jednostki, które definiują właściwości, `ReorderLevel`i `UnitsInStock` .  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedAttributes](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/northwind.csdl#edmfeedattributes)]  
  
 Te atrybuty generują następujące niestandardowe strumieniowe źródło danych `Products` dla zestawu jednostek. W niestandardowym strumieniu `ProductName` danych wartość właściwości jest wyświetlana zarówno `author` w elemencie, jak i jako `ProductName` element właściwości, a `UnitsInStock` właściwość jest wyświetlana w niestandardowym elemencie, który ma własną unikatową przestrzeń nazw i z `ReorderLevel` właściwość jako atrybut:  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedResultProduct](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/edmfeedresult.xml#edmfeedresultproduct)]  
  
 Aby uzyskać więcej informacji, zobacz [jak: Dostosuj źródła danych za pomocą dostawcy](../../../../docs/framework/data/wcf/how-to-customize-feeds-with-ef-provider-wcf-data-services.md)Entity Framework.  
  
> [!NOTE]
> Ponieważ rozszerzenia do modelu danych nie są obsługiwane przez Entity Designer, należy ręcznie zmodyfikować plik XML zawierający model danych. Aby uzyskać więcej informacji na temat pliku edmx, który jest generowany przez narzędzia Entity Data Model, zobacz [plik. edmx Entity Framework — Omówienie](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)).  
  
### <a name="custom-feed-attributes"></a>Atrybuty niestandardowego kanału informacyjnego  
 W poniższej tabeli przedstawiono atrybuty XML, które dostosowują źródła danych, które można dodać do języka definicji schematu koncepcyjnego (CSDL) definiującego model. Te atrybuty są równoważne właściwościom <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> używanym z dostawcą odbicia.  
  
|Nazwa atrybutu|Opis|  
|--------------------|-----------------|  
|`FC_ContentKind`|Wskazuje typ zawartości. Poniższe słowa kluczowe definiują typy zawartości zespolonej.<br /><br /> `text:`Wartość właściwości jest wyświetlana w kanale informacyjnym jako tekst.<br /><br /> `html:`Wartość właściwości jest wyświetlana w kanale informacyjnym jako HTML.<br /><br /> `xhtml:`Wartość właściwości jest wyświetlana w kanale informacyjnym HTML.<br /><br /> Te słowa kluczowe są równoważne z wartościami <xref:System.Data.Services.Common.SyndicationTextContentKind> wyliczenia używanymi z dostawcą odbicia.<br /><br /> Ten atrybut nie jest obsługiwany, `FC_NsPrefix` gdy są używane atrybuty i. `FC_NsUri`<br /><br /> Po określeniu wartości `xhtml` `FC_ContentKind` dla atrybutu, należy się upewnić, że wartość właściwości zawiera poprawnie sformatowany kod XML. Usługa danych zwraca wartość bez wykonywania żadnych transformacji. Należy również upewnić się, że wszystkie prefiksy elementów XML w zwracanym kodzie XML mają identyfikator URI przestrzeni nazw oraz prefiks zdefiniowany w mapowanym źródle danych.|  
|`FC_KeepInContent`|Wskazuje, że wartość właściwości, której dotyczy odwołanie, powinna być uwzględniona w sekcji zawartość kanału informacyjnego i w mapowanej lokalizacji. Prawidłowe wartości to `true` i `false`. Aby wyniki strumieniowo były zgodne ze starszymi wersjami programu [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], należy określić `true` wartość, aby upewnić się, że wartość jest uwzględniona w sekcji zawartość kanału informacyjnego.|  
|`FC_NsPrefix`|Prefiks przestrzeni nazw elementu XML w mapowaniu innym niż zespolone. Ten atrybut musi być używany z `FC_NsUri` atrybutem i nie może być używany `FC_ContentKind` z atrybutem.|  
|`FC_NsUri`|Identyfikator URI przestrzeni nazw elementu XML w mapowaniu niezespolonym. Ten atrybut musi być używany z `FC_NsPrefix` atrybutem i nie może być używany `FC_ContentKind` z atrybutem.|  
|`FC_SourcePath`|Ścieżka właściwości jednostki, do której zostanie zastosowana ta reguła mapowania kanału informacyjnego. Ten atrybut jest obsługiwany tylko w przypadku, gdy jest używany `EntityType` w elemencie.<br /><br /> <xref:System.Data.Services.Common.EntityPropertyMappingAttribute.SourcePath%2A> Właściwość nie może bezpośrednio odwoływać się do typu złożonego. W przypadku typów złożonych należy użyć wyrażenia ścieżki, gdzie nazwy właściwości są oddzielone znakiem ukośnika odwrotnego (`/`). Na przykład następujące wartości są dozwolone dla typu `Person` jednostki z właściwością `Age` integer i właściwością złożoną<br /><br /> `Address`:<br /><br /> `Age`<br /><br /> `Address/Street`<br /><br /> <xref:System.Data.Services.Common.EntityPropertyMappingAttribute.SourcePath%2A> Właściwość nie może być ustawiona na wartość, która zawiera spację lub jakikolwiek inny znak, który jest nieprawidłowy w nazwie właściwości.|  
|`FC_TargetPath`|Nazwa elementu docelowego otrzymanego kanału informacyjnego do mapowania właściwości. Ten element może być elementem zdefiniowanym przez specyfikację Atom lub elementem niestandardowym.<br /><br /> Następujące słowa kluczowe to wstępnie zdefiniowane wartości elementu docelowego zespolonego, które wskazują konkretną lokalizację [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] w źródle danych.<br /><br /> `SyndicationAuthorEmail:``atom:email` Element`atom:author` podrzędny elementu.<br /><br /> `SyndicationAuthorName:``atom:name` Element`atom:author` podrzędny elementu.<br /><br /> `SyndicationAuthorUri:``atom:uri` Element`atom:author` podrzędny elementu.<br /><br /> `SyndicationContributorEmail:``atom:email` Element`atom:contributor` podrzędny elementu.<br /><br /> `SyndicationContributorName:``atom:name` Element`atom:contributor` podrzędny elementu.<br /><br /> `SyndicationContributorUri:``atom:uri` Element`atom:contributor` podrzędny elementu.<br /><br /> `SyndicationCustomProperty:`Niestandardowy element właściwości. Podczas mapowania do elementu niestandardowego, obiekt docelowy musi być wyrażeniem ścieżki, w którym zagnieżdżone elementy są rozdzielone ukośnikiem odwrotnym`/`(), a atrybuty są określone przez`@`znak handlowego "i". W poniższym przykładzie ciąg `UnitsInStock/@ReorderLevel` mapuje wartość właściwości na atrybut o nazwie `ReorderLevel` w elemencie podrzędnym o nazwie `UnitsInStock` root entry elementu.<br /><br /> `<Property Name="ReorderLevel" Type="Int16"               m:FC_TargetPath="UnitsInStock/@ReorderLevel"               m:FC_NsPrefix="Northwind"               m:FC_NsUri="http://schemas.examples.microsoft.com/dataservices"               m:FC_KeepInContent="false"               />`<br /><br /> Jeśli obiektem docelowym jest nazwa elementu niestandardowego, `FC_NsPrefix` należy również określić atrybuty i. `FC_NsUri`<br /><br /> `SyndicationPublished:``atom:published` Element.<br /><br /> `SyndicationRights:``atom:rights` Element.<br /><br /> `SyndicationSummary:``atom:summary` Element.<br /><br /> `SyndicationTitle:``atom:title` Element.<br /><br /> `SyndicationUpdated:``atom:updated` Element.<br /><br /> Te słowa kluczowe są równoważne z wartościami <xref:System.Data.Services.Common.SyndicationItemProperty> wyliczenia używanymi z dostawcą odbicia.|  
  
> [!NOTE]
> W nazwach atrybutów i wartościach jest rozróżniana wielkość liter. Atrybuty mogą być stosowane do `EntityType` elementu lub do jednego lub kilku `Property` elementów, ale nie do obu.  
  
## <a name="customizing-feeds-with-the-reflection-provider"></a>Dostosowywanie kanałów informacyjnych za pomocą dostawcy odbicia  
 Aby dostosować kanały informacyjne dla modelu danych, który został zaimplementowany przy użyciu dostawcy odbicia, Dodaj co najmniej jedno wystąpienie <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> atrybutu do klas, które reprezentują typy jednostek w modelu danych. Właściwości <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> klasy odpowiadają atrybutom dostosowania kanału informacyjnego, które są opisane w poprzedniej sekcji. Poniżej znajduje się przykład deklaracji `Order` typu z niestandardowym mapowaniem źródła danych zdefiniowanym dla obu właściwości.  
  
> [!NOTE]
> Model danych dla tego przykładu został zdefiniowany w temacie [How to: Utwórz usługę danych przy użyciu dostawcy](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)odbicia.  
  
 [!code-csharp[Astoria Custom Feeds#CustomOrderFeed](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_custom_feeds/cs/orderitems.svc.cs#customorderfeed)]
 [!code-vb[Astoria Custom Feeds#CustomOrderFeed](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_custom_feeds/vb/orderitems.svc.vb#customorderfeed)]  
  
 Te atrybuty generują następujące niestandardowe strumieniowe źródło danych `Orders` dla zestawu jednostek. W tym dostosowanym strumieniu `OrderId` wartość właściwości jest wyświetlana tylko `title` w `Customer` elemencie `entry` `author` i wartość właściwości jest wyświetlana zarówno w elemencie, jak i jako `Customer` element właściwości:  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResult](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/iqueryablefeedresult.xml#iqueryablefeedresult)]  
  
 Aby uzyskać więcej informacji, zobacz [jak: Dostosuj źródła danych za pomocą dostawcy](../../../../docs/framework/data/wcf/how-to-customize-feeds-with-the-reflection-provider-wcf-data-services.md)odbicia.  
  
## <a name="customizing-feeds-with-a-custom-data-service-provider"></a>Dostosowywanie kanałów informacyjnych za pomocą niestandardowego dostawcy usługi danych  
 Dostosowanie kanału informacyjnego dla modelu danych zdefiniowanego za pomocą niestandardowego dostawcy usługi danych jest zdefiniowane dla typu zasobu przez wywołanie <xref:System.Data.Services.Providers.ResourceType.AddEntityPropertyMappingAttribute%2A> <xref:System.Data.Services.Providers.ResourceType> elementu, który reprezentuje typ jednostki w modelu danych. Aby uzyskać więcej informacji, zobacz [niestandardowe dostawcy usług danych](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md).  
  
## <a name="consuming-custom-feeds"></a>Zużywanie niestandardowych kanałów informacyjnych  
 Gdy aplikacja bezpośrednio korzysta ze [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych, musi być w stanie przetwarzać wszelkie niestandardowe elementy i atrybuty w zwracanym źródle danych. W przypadku zaimplementowania niestandardowych kanałów informacyjnych w modelu danych, niezależnie od dostawcy usługi danych, `$metadata` punkt końcowy zwraca niestandardowe informacje o źródle jako atrybuty niestandardowego kanału informacyjnego w CSDL zwróconym przez usługę danych. Korzystając z okna dialogowego **Dodaj odwołanie do usługi** lub narzędzia [DataSvcUtil. exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) do generowania klas usługi danych klienta, niestandardowe atrybuty kanału informacyjnego są używane do zagwarantowania, że żądania i odpowiedzi do usługi danych są obsługiwane poprawnie.  
  
## <a name="feed-customization-considerations"></a>Zagadnienia dotyczące dostosowywania kanału informacyjnego  
 Podczas definiowania mapowań niestandardowych kanałów informacyjnych należy wziąć pod uwagę następujące kwestie.  
  
- [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Klient traktuje zamapowane elementy w strumieniu jako puste, gdy zawierają tylko biały znak. W związku z tym mapowane elementy, które zawierają tylko biały znak, nie są w tym samym odstępie dostępne na kliencie. Aby zachować ten biały znak na kliencie, należy ustawić wartość `KeepInContext` na na `true` w atrybucie mapowanie źródła strumieniowego.  
  
## <a name="versioning-requirements"></a>Wymagania dotyczące wersji  
 Dostosowanie kanału informacyjnego ma [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] następujące wymagania dotyczące wersji protokołu:  
  
- Dostosowanie kanału informacyjnego wymaga, aby usługa klienta i danych obsługiwały wersję 2,0 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokołu i nowszych wersji.  
  
 Aby uzyskać więcej informacji, zobacz [przechowywanie wersji usługi danych](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md).  
  
## <a name="see-also"></a>Zobacz także

- [Dostawca odbicia](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)
- [Dostawca programu Entity Framework](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)
