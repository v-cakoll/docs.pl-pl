---
title: "Dostosowywanie kanału informacyjnego (usługi danych WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, feeds
- WCF Data Services, Atom protocol
- Atom Publishing Protocol [WCF Data Services]
- WCF Data Services, customizing feeds
ms.assetid: 0d1a39bc-6462-4683-bd7d-e74e0fd28a85
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e31f14d59bb2ac7caa233ff60c60eb944ee5bbbf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="feed-customization-wcf-data-services"></a>Dostosowywanie kanału informacyjnego (usługi danych WCF)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]używa [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] do udostępniania danych jako źródło danych. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]obsługuje zarówno Atom i JavaScript Object Notation (JSON) formaty dla źródła danych. Korzystając z źródła danych, Atom [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] zawiera standardowe metody do serializowania danych, takich jak jednostki i relacje w formacie XML, który można umieścić w treści komunikatu HTTP. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]Definiuje właściwości jednostki domyślne mapowanie danych, który znajduje się w jednostkach i elementy Atom. Aby uzyskać więcej informacji, zobacz [OData: Atom Format](http://go.microsoft.com/fwlink/?LinkID=185794).  
  
 Może być scenariusz aplikacji, który wymaga się, że właściwość danych zwróconych przez usługę danych można zserializować w sposób dostosowany, a nie w standardzie formatu źródła. Z [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)], można dostosować serializacji w strumieniowego źródła danych, dzięki czemu można zamapować właściwości jednostki do nieużywanych elementów i atrybutów wpisu lub elementy niestandardowe wpisu w źródle danych.  
  
> [!NOTE]
>  Dostosowywanie źródła jest obsługiwana tylko dla źródła danych Atom. Niestandardowe źródła danych nie są zwracane, gdy formatu JSON jest wymagany dla zwracanych źródła danych.  
  
 Z [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], można zdefiniować alternatywny właściwości jednostki mapowania dla ładunku Atom ręcznie stosowanie atrybutów do typów jednostek w modelu danych. Dostawca źródła danych usługi danych określa, jak powinny zostać zastosowane te atrybuty.  
  
> [!IMPORTANT]
>  Po zdefiniowaniu źródeł niestandardowych musi gwarantuje, że wszystkie właściwości jednostki, które mają niestandardowy mapowania zdefiniowane znajdują się w projekcji. Gdy właściwość zamapowanych jednostki nie jest uwzględniony w projekcji, może dojść do utraty danych. Aby uzyskać więcej informacji, zobacz [projekcje zapytania](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md).  
  
## <a name="customizing-feeds-with-the-entity-framework-provider"></a>Dostosowywanie źródła danych za pomocą dostawcy programu Entity Framework  
 Model danych używany z [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] dostawcy jest reprezentowany jako kodu XML w pliku edmx. W takim przypadku atrybutów definiujących źródła niestandardowego są dodawane do `EntityType` i `Property` elementy, które reprezentują typów jednostek i właściwości w modelu danych. Te atrybuty dostosowania źródła strumieniowego nie są zdefiniowane w [ \[MC CSDL\]: formatu pliku definicji schematu koncepcyjnego](http://go.microsoft.com/fwlink/?LinkId=159072), która jest format który [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] używa dostawcy, aby zdefiniować modelu danych. W związku z tym należy zadeklarować źródła dostosowywania atrybutów w przestrzeni nazw schematu, która jest zdefiniowana jako `m="http://schemas.microsoft.com/ado/2007/08/dataservices/metadata"`. Poniższy fragment XML zawiera atrybuty dostosowania źródła `Property` elementy `Products` typu jednostki, który definiuje `ProductName`, `ReorderLevel`, i `UnitsInStock` właściwości.  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedAttributes](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/northwind.csdl#edmfeedattributes)]  
  
 Te atrybuty tworzy następujące dane niestandardowe dla `Products` zestawu jednostek. Dostosowane danych źródła danych `ProductName` wartość właściwości jest wyświetlany zarówno w `author` elementu a jako `ProductName` elementu właściwości i `UnitsInStock` właściwość jest wyświetlana w elementu niestandardowego, który ma własną unikatową przestrzeń nazw i z `ReorderLevel` właściwość jako atrybutu:  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedResultProduct](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/edmfeedresult.xml#edmfeedresultproduct)]  
  
 Aby uzyskać więcej informacji, zobacz [porady: dostosowywanie źródeł danych z dostawcy programu Entity Framework](../../../../docs/framework/data/wcf/how-to-customize-feeds-with-ef-provider-wcf-data-services.md).  
  
> [!NOTE]
>  Rozszerzenia do modelu danych nie są obsługiwane przez program Entity Designer, należy ręcznie zmodyfikować plik XML, który zawiera model danych. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]pliku edmx, który jest generowany przez [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] narzędzia, zobacz [pliku Przegląd edmx](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4).  
  
### <a name="custom-feed-attributes"></a>Niestandardowe źródła atrybutów  
 W poniższej tabeli przedstawiono atrybuty XML, które dostosować źródła danych, które można dodać do języka definicji schematu koncepcyjnego (CSDL), który definiuje modelu danych. Te atrybuty są równoważne właściwości <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> użycia z dostawcą odbicia.  
  
|Nazwa atrybutu|Opis|  
|--------------------|-----------------|  
|`FC_ContentKind`|Wskazuje typ zawartości. Poniższe słowa kluczowe Definiowanie typów zawartości zespolonego.<br /><br /> `text:`Wartość właściwości jest wyświetlana w źródle danych jako tekst.<br /><br /> `html:`Wartość właściwości jest wyświetlana w źródle danych jako HTML.<br /><br /> `xhtml:`Wartość właściwości jest wyświetlana w źródle danych jako HTML w formacie XML.<br /><br /> Słowa kluczowe są równoważne wartości <xref:System.Data.Services.Common.SyndicationTextContentKind> wyliczenie użycia z dostawcą odbicia.<br /><br /> Ten atrybut nie jest obsługiwane w przypadku `FC_NsPrefix` i `FC_NsUri` są używane atrybuty.<br /><br /> Po określeniu wartość `xhtml` dla `FC_ContentKind` atrybutu, użytkownik musi zapewnić, że wartość właściwości zawiera poprawnie sformatowany XML. Usługi danych zwraca wartość bez żadnych przekształcenia. Upewnij się że wszystkie prefiksy — element XML w zwróconego kodu XML ma identyfikator URI przestrzeni nazw i prefiks zdefiniowany w mapowanej źródle danych.|  
|`FC_KeepInContent`|Wskazuje, że wartość właściwości przywoływanego powinny być dołączone zarówno w sekcji zawartości źródła danych, jak i w mapowanej lokalizacji. Prawidłowe wartości to `true` i `false`. Aby wynikowe źródła danych zgodny z wcześniejszymi wersjami programu [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], określ wartość `true` aby upewnić się, że wartość znajduje się w sekcji zawartości kanału informacyjnego.|  
|`FC_NsPrefix`|Prefiks przestrzeni nazw elementu XML w mapowaniu nie zespolonego. Ten atrybut musi być używany z `FC_NsUri` atrybutu i nie można używać z `FC_ContentKind` atrybutu.|  
|`FC_NsUri`|Identyfikator URI przestrzeni nazw elementu XML w mapowaniu nie zespolonego. Ten atrybut musi być używany z `FC_NsPrefix` atrybutu i nie można używać z `FC_ContentKind` atrybutu.|  
|`FC_SourcePath`|Ścieżka właściwości jednostki, które tego źródła danych mapowanie dotyczy dana reguła. Ten atrybut jest obsługiwany tylko, gdy jest używany w `EntityType` elementu.<br /><br /> <xref:System.Data.Services.Common.EntityPropertyMappingAttribute.SourcePath%2A> Właściwości bezpośrednio nie może odwoływać się do typu złożonego. Dla typów złożonych, należy użyć wyrażenie ścieżki gdzie nazw właściwości oddzielonych ukośnik odwrotny (`/`) znaków. Na przykład, dozwolone są następujące wartości dla typu jednostki `Person` z właściwością liczby całkowitej `Age` i właściwości złożonej<br /><br /> `Address`:<br /><br /> `Age`<br /><br /> `Address/Street`<br /><br /> <xref:System.Data.Services.Common.EntityPropertyMappingAttribute.SourcePath%2A> Nie można ustawić właściwości na wartość zawiera spację lub dowolny znak, który jest nieprawidłowy w nazwie właściwości.|  
|`FC_TargetPath`|Nazwa elementu docelowego wynikowy źródła danych, aby zamapować właściwości. Ten element może być elementu ze specyfikacją Atom lub elementu niestandardowego.<br /><br /> Poniższe słowa kluczowe są zespolonego wstępnie zdefiniowanych wartości ścieżkę docelową, odnoszące się do określonej lokalizacji w [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych.<br /><br /> `SyndicationAuthorEmail:``atom:email` Elementem podrzędnym `atom:author` elementu.<br /><br /> `SyndicationAuthorName:``atom:name` Elementem podrzędnym `atom:author` elementu.<br /><br /> `SyndicationAuthorUri:``atom:uri` Elementem podrzędnym `atom:author` elementu.<br /><br /> `SyndicationContributorEmail:``atom:email` Elementem podrzędnym `atom:contributor` elementu.<br /><br /> `SyndicationContributorName:``atom:name` Elementem podrzędnym `atom:contributor` elementu.<br /><br /> `SyndicationContributorUri:``atom:uri` Elementem podrzędnym `atom:contributor` elementu.<br /><br /> `SyndicationCustomProperty:`Element właściwości niestandardowej. Podczas mapowania do elementu niestandardowego, element docelowy musi być wyrażenie ścieżki, w którym zagnieżdżone elementy są oddzielone ukośnik odwrotny (`/`) i atrybuty są określone przez handlowego "i" (`@`). W poniższym przykładzie ciąg `UnitsInStock/@ReorderLevel` mapuje wartości właściwości do atrybutu o nazwie `ReorderLevel` na element podrzędny o nazwie `UnitsInStock` głównego elementu wpis.<br /><br /> `<Property Name="ReorderLevel" Type="Int16"               m:FC_TargetPath="UnitsInStock/@ReorderLevel"               m:FC_NsPrefix="Northwind"               m:FC_NsUri="http://schemas.examples.microsoft.com/dataservices"               m:FC_KeepInContent="false"               />`<br /><br /> Gdy element docelowy jest nazwą elementu niestandardowego `FC_NsPrefix` i `FC_NsUri` atrybutów musi być także określona.<br /><br /> `SyndicationPublished:``atom:published` Elementu.<br /><br /> `SyndicationRights:``atom:rights` Elementu.<br /><br /> `SyndicationSummary:``atom:summary` Elementu.<br /><br /> `SyndicationTitle:``atom:title` Elementu.<br /><br /> `SyndicationUpdated:``atom:updated` Elementu.<br /><br /> Słowa kluczowe są równoważne wartości <xref:System.Data.Services.Common.SyndicationItemProperty> wyliczenie użycia z dostawcą odbicia.|  
  
> [!NOTE]
>  Nazwy i wartości atrybutów jest uwzględniana wielkość liter. Atrybuty mogą być stosowane do `EntityType` elementu jednego lub więcej `Property` elementów, ale nie oba.  
  
## <a name="customizing-feeds-with-the-reflection-provider"></a>Dostosowywanie źródła danych za pomocą dostawcy odbicia  
 Aby dostosować źródeł danych dla modelu danych, który został wdrożony przy użyciu dostawcy odbicia, należy dodać co najmniej jedno wystąpienie elementu <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> atrybutu dla klasy, które reprezentują typy jednostek w modelu danych. Właściwości <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> klasy odpowiadają atrybutów dostosowania źródła, które są opisane w poprzedniej sekcji. Poniżej przedstawiono przykład deklaracja `Order` typu z niestandardowego źródła mapowania zdefiniowane dla obu właściwości.  
  
> [!NOTE]
>  Model danych w tym przykładzie jest zdefiniowana w temacie [porady: Tworzenie usługi danych przy użyciu dostawcy odbicia](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md).  
  
 [!code-csharp[Astoria Custom Feeds#CustomOrderFeed](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria custom feeds/cs/orderitems.svc.cs#customorderfeed)]
 [!code-vb[Astoria Custom Feeds#CustomOrderFeed](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria custom feeds/vb/orderitems.svc.vb#customorderfeed)]  
  
 Te atrybuty tworzy następujące dane niestandardowe dla `Orders` zestawu jednostek. W tym dostosowane źródła danych, `OrderId` wartość właściwości wyświetla tylko w `title` elementu `entry` i `Customer` zarówno w wyświetlana jest wartość właściwości `author` elementu a jako `Customer` elementu właściwości:  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResult](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/iqueryablefeedresult.xml#iqueryablefeedresult)]  
  
 Aby uzyskać więcej informacji, zobacz [porady: Dostosowywanie źródła z dostawcą odbicia](../../../../docs/framework/data/wcf/how-to-customize-feeds-with-the-reflection-provider-wcf-data-services.md).  
  
## <a name="customizing-feeds-with-a-custom-data-service-provider"></a>Dostosowywanie źródła danych za pomocą dostawcy usług danych niestandardowych  
 Źródła danych dostosowywania dla modelu danych zdefiniowany przy użyciu dostawcy usług danych niestandardowych jest zdefiniowany dla typu zasobu przez wywołanie metody <xref:System.Data.Services.Providers.ResourceType.AddEntityPropertyMappingAttribute%2A> na <xref:System.Data.Services.Providers.ResourceType> reprezentujący typ jednostki w modelu danych. Aby uzyskać więcej informacji, zobacz [dostawców usług danych niestandardowych](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md).  
  
## <a name="consuming-custom-feeds"></a>Korzystanie z niestandardowych źródeł danych  
 Gdy aplikacja zużywa bezpośrednio [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych, musi być w stanie przetworzyć wszystkie niestandardowe elementy i atrybuty w źródle danych zwracanych. Implementując niestandardowych źródeł danych w modelu danych, niezależnie od dostawcy usług danych `$metadata` punktu końcowego zwraca niestandardowe źródła informacji jak niestandardowe atrybuty źródła strumieniowego w pliku CSDL zwrócony przez usługę do dane. Jeśli używasz **Dodaj odwołanie do usługi** okna dialogowego lub [datasvcutil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) narzędzie do generowania klasy usługi danych klienta, dostosowane źródła danych, aby zagwarantować, że żądania są używane atrybuty i odpowiedzi usługi danych są poprawnie obsługiwane.  
  
## <a name="feed-customization-considerations"></a>Zagadnienia dotyczące dostosowywania źródła  
 Należy rozważyć następujące podczas definiowania niestandardowe mapowanie kanału informacyjnego.  
  
-   [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Klienta traktuje mapowanych elementów w źródle strumieniowym jako pusta jeśli zawierają tylko białe znaki. W związku z tym mapowanych elementów, które zawierają tylko białe znaki nie są materializować na kliencie z tej samej odstępu. Aby zachować ten odstępów na kliencie, należy ustawić wartość `KeepInContext` do `true` w atrybucie źródła mapowania.  
  
## <a name="versioning-requirements"></a>Wymagania dotyczące kontroli wersji  
 Dostosowania źródła zawiera następujące [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokołu wymagań dotyczących przechowywania wersji:  
  
-   Dostosowywanie źródła wymaga tego klienta i danych usługi pomocy technicznej w wersji 2.0 z [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokołu i nowszych wersjach.  
  
 Aby uzyskać więcej informacji, zobacz [przechowywanie wersji usługi danych](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Dostawca odbicia](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)  
 [Dostawcy programu Entity Framework](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)
