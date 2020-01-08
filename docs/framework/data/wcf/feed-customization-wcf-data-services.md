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
ms.openlocfilehash: f34ee198ba49a168ed8b56785bea68beee2eb214
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348124"
---
# <a name="feed-customization-wcf-data-services"></a>Dostosowywanie kanału informacyjnego (Usługi danych programu WCF)
Usługi danych programu WCF używa protokołu Open Data Protocol (OData) do udostępniania danych jako źródła strumieniowego. Usługa OData obsługuje formaty Atom i JavaScript Object Notation (JSON) dla strumieniowych źródeł danych. Korzystając z kanału informacyjnego Atom, usługa OData zapewnia standardową metodę serializowania danych, takich jak jednostki i relacje, do formatu XML, który może zostać uwzględniony w treści wiadomości HTTP. Usługa OData definiuje domyślne mapowanie właściwości jednostki między danymi zawartymi w jednostkach i elementach Atom. Aby uzyskać więcej informacji, zobacz [Format OData: Atom](https://www.odata.org/documentation/odata-version-2-0/atom-format/).  
  
 Może istnieć scenariusz aplikacji, który wymaga, aby dane właściwości zwrócone przez usługę danych były serializowane w sposób dostosowany, a nie w standardowym formacie kanału informacyjnego. Za pomocą protokołu OData można dostosować serializację w strumieniowym źródle danych, tak aby właściwości jednostki mogły być mapowane do nieużywanych elementów i atrybutów wpisu lub do niestandardowych elementów wpisu w strumieniu.  
  
> [!NOTE]
> Dostosowanie kanału informacyjnego jest obsługiwane tylko dla kanałów informacyjnych Atom. Niestandardowe źródła danych nie są zwracane, gdy wymagany jest format JSON dla zwracanego źródła danych.  
  
 Za pomocą Usługi danych programu WCF można zdefiniować alternatywne mapowanie właściwości jednostki dla ładunku Atom, ręcznie stosując atrybuty do typów jednostek w modelu danych. Dostawca źródła danych usługi danych określa, jak należy zastosować te atrybuty.  
  
> [!IMPORTANT]
> Podczas definiowania niestandardowych kanałów informacyjnych należy zagwarantować, że wszystkie właściwości jednostki, które mają zdefiniowane mapowania niestandardowe, są uwzględniane w projekcji. Gdy właściwość mapowanego obiektu nie jest uwzględniona w projekcji, może dojść do utraty danych. Aby uzyskać więcej informacji, zobacz [projekcje zapytań](query-projections-wcf-data-services.md).  
  
## <a name="customizing-feeds-with-the-entity-framework-provider"></a>Dostosowywanie kanałów informacyjnych za pomocą dostawcy Entity Framework  
 Model danych używany z dostawcą Entity Framework jest reprezentowany jako XML w pliku edmx. W takim przypadku atrybuty definiujące niestandardowe źródła są dodawane do `EntityType` i `Property` elementów, które reprezentują typy jednostek i właściwości w modelu danych. Te atrybuty dostosowania kanału informacyjnego nie są zdefiniowane w [\[MC-CSDL\]: Format pliku definicji schematu koncepcyjnego](https://docs.microsoft.com/openspecs/windows_protocols/mc-csdl/c03ad8c3-e8b7-4306-af96-a9e52bb3df12), który jest formatem używanym przez dostawcę Entity Framework do definiowania modelu danych. W związku z tym należy zadeklarować atrybuty dostosowania kanału informacyjnego w określonej przestrzeni nazw schematu, która jest definiowana jako `m="http://schemas.microsoft.com/ado/2007/08/dataservices/metadata"`. Poniższy fragment kodu XML przedstawia atrybuty dostosowania źródła zastosowane do `Property` elementów `Products` typu jednostki, które definiują właściwości `ProductName`, `ReorderLevel`i `UnitsInStock`.  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedAttributes](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/northwind.csdl#edmfeedattributes)]  
  
 Te atrybuty generują następujące niestandardowe strumieniowe źródło danych dla zestawu jednostek `Products`. W dostosowanym strumieniu danych `ProductName` wartość właściwości jest wyświetlana zarówno w elemencie `author`, jak i jako element właściwości `ProductName`, a właściwość `UnitsInStock` jest wyświetlana w niestandardowym elemencie, który ma własną unikatową przestrzeń nazw i z właściwością `ReorderLevel` jako atrybut:  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedResultProduct](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/edmfeedresult.xml#edmfeedresultproduct)]  
  
 Aby uzyskać więcej informacji, zobacz [How to: Dostosowywanie kanałów informacyjnych za pomocą dostawcy Entity Framework](how-to-customize-feeds-with-ef-provider-wcf-data-services.md).  
  
> [!NOTE]
> Ponieważ rozszerzenia do modelu danych nie są obsługiwane przez Entity Designer, należy ręcznie zmodyfikować plik XML zawierający model danych. Aby uzyskać więcej informacji na temat pliku edmx, który jest generowany przez narzędzia Entity Data Model, zobacz [plik. edmx Entity Framework — Omówienie](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)).  
  
### <a name="custom-feed-attributes"></a>Atrybuty niestandardowego kanału informacyjnego  
 W poniższej tabeli przedstawiono atrybuty XML, które dostosowują źródła danych, które można dodać do języka definicji schematu koncepcyjnego (CSDL) definiującego model. Te atrybuty są równoważne właściwościom <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> używanym z dostawcą odbicia.  
  
|Nazwa atrybutu|Opis|  
|--------------------|-----------------|  
|`FC_ContentKind`|Wskazuje typ zawartości. Poniższe słowa kluczowe definiują typy zawartości zespolonej.<br /><br /> `text:` wartość właściwości jest wyświetlana w kanale informacyjnym jako tekst.<br /><br /> `html:` wartość właściwości jest wyświetlana w kanale informacyjnym jako HTML.<br /><br /> `xhtml:` wartość właściwości jest wyświetlana w kanale informacyjnym HTML.<br /><br /> Te słowa kluczowe są równoważne z wartościami wyliczenia <xref:System.Data.Services.Common.SyndicationTextContentKind> używanymi z dostawcą odbicia.<br /><br /> Ten atrybut nie jest obsługiwany, gdy są używane atrybuty `FC_NsPrefix` i `FC_NsUri`.<br /><br /> Po określeniu wartości `xhtml` atrybutu `FC_ContentKind`, należy się upewnić, że wartość właściwości zawiera poprawnie sformatowany kod XML. Usługa danych zwraca wartość bez wykonywania żadnych transformacji. Należy również upewnić się, że wszystkie prefiksy elementów XML w zwracanym kodzie XML mają identyfikator URI przestrzeni nazw oraz prefiks zdefiniowany w mapowanym źródle danych.|  
|`FC_KeepInContent`|Wskazuje, że wartość właściwości, której dotyczy odwołanie, powinna być uwzględniona w sekcji zawartość kanału informacyjnego i w mapowanej lokalizacji. Prawidłowe wartości to `true` i `false`. Aby uzyskać strumieniowe źródło danych wstecz zgodne ze starszymi wersjami Usługi danych programu WCF, określ wartość `true`, aby upewnić się, że wartość jest uwzględniona w sekcji zawartość kanału informacyjnego.|  
|`FC_NsPrefix`|Prefiks przestrzeni nazw elementu XML w mapowaniu innym niż zespolone. Ten atrybut musi być używany z atrybutem `FC_NsUri` i nie może być używany z atrybutem `FC_ContentKind`.|  
|`FC_NsUri`|Identyfikator URI przestrzeni nazw elementu XML w mapowaniu niezespolonym. Ten atrybut musi być używany z atrybutem `FC_NsPrefix` i nie może być używany z atrybutem `FC_ContentKind`.|  
|`FC_SourcePath`|Ścieżka właściwości jednostki, do której zostanie zastosowana ta reguła mapowania kanału informacyjnego. Ten atrybut jest obsługiwany tylko w przypadku, gdy jest używany w elemencie `EntityType`.<br /><br /> Właściwość <xref:System.Data.Services.Common.EntityPropertyMappingAttribute.SourcePath%2A> nie może bezpośrednio odwoływać się do typu złożonego. W przypadku typów złożonych należy użyć wyrażenia ścieżki, gdzie nazwy właściwości są oddzielane znakiem ukośnika odwrotnego (`/`). Na przykład następujące wartości są dozwolone dla typu jednostki `Person` za pomocą właściwości Integer `Age` i złożonej właściwości<br /><br /> `Address`:<br /><br /> `Age`<br /><br /> `Address/Street`<br /><br /> Dla właściwości <xref:System.Data.Services.Common.EntityPropertyMappingAttribute.SourcePath%2A> nie można ustawić wartości zawierającej spację ani innego znaku, który jest nieprawidłowy w nazwie właściwości.|  
|`FC_TargetPath`|Nazwa elementu docelowego otrzymanego kanału informacyjnego do mapowania właściwości. Ten element może być elementem zdefiniowanym przez specyfikację Atom lub elementem niestandardowym.<br /><br /> Następujące słowa kluczowe to wstępnie zdefiniowane wartości elementu docelowego zespolonego, które wskazują konkretną lokalizację w strumieniowym źródle danych OData.<br /><br /> `SyndicationAuthorEmail:` `atom:email` elementu podrzędnego elementu `atom:author`.<br /><br /> `SyndicationAuthorName:` `atom:name` elementu podrzędnego elementu `atom:author`.<br /><br /> `SyndicationAuthorUri:` `atom:uri` elementu podrzędnego elementu `atom:author`.<br /><br /> `SyndicationContributorEmail:` `atom:email` elementu podrzędnego elementu `atom:contributor`.<br /><br /> `SyndicationContributorName:` `atom:name` elementu podrzędnego elementu `atom:contributor`.<br /><br /> `SyndicationContributorUri:` `atom:uri` elementu podrzędnego elementu `atom:contributor`.<br /><br /> `SyndicationCustomProperty:` niestandardowego elementu właściwości. Podczas mapowania do elementu niestandardowego, obiekt docelowy musi być wyrażeniem ścieżki, w którym zagnieżdżone elementy są rozdzielone ukośnikiem odwrotnym (`/`), a atrybuty są określane przez znak handlowego "i" (`@`). W poniższym przykładzie ciąg `UnitsInStock/@ReorderLevel` mapuje wartość właściwości na atrybut o nazwie `ReorderLevel` w elemencie podrzędnym o nazwie `UnitsInStock` elementu głównego wpisu.<br /><br /> `<Property Name="ReorderLevel" Type="Int16"               m:FC_TargetPath="UnitsInStock/@ReorderLevel"               m:FC_NsPrefix="Northwind"               m:FC_NsUri="http://schemas.examples.microsoft.com/dataservices"               m:FC_KeepInContent="false"               />`<br /><br /> Jeśli obiektem docelowym jest nazwa elementu niestandardowego, należy również określić atrybuty `FC_NsPrefix` i `FC_NsUri`.<br /><br /> `SyndicationPublished:` `atom:published` elementu.<br /><br /> `SyndicationRights:` `atom:rights` elementu.<br /><br /> `SyndicationSummary:` `atom:summary` elementu.<br /><br /> `SyndicationTitle:` `atom:title` elementu.<br /><br /> `SyndicationUpdated:` `atom:updated` elementu.<br /><br /> Te słowa kluczowe są równoważne z wartościami wyliczenia <xref:System.Data.Services.Common.SyndicationItemProperty> używanymi z dostawcą odbicia.|  
  
> [!NOTE]
> W nazwach atrybutów i wartościach jest rozróżniana wielkość liter. Atrybuty mogą być stosowane do elementu `EntityType` lub do jednego lub kilku elementów `Property`, ale nie do obu.  
  
## <a name="customizing-feeds-with-the-reflection-provider"></a>Dostosowywanie kanałów informacyjnych za pomocą dostawcy odbicia  
 Aby dostosować kanały informacyjne dla modelu danych, który został zaimplementowany przy użyciu dostawcy odbicia, Dodaj co najmniej jedno wystąpienie atrybutu <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> do klas, które reprezentują typy jednostek w modelu danych. Właściwości klasy <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> odpowiadają atrybutom dostosowania kanału informacyjnego, które są opisane w poprzedniej sekcji. Poniżej znajduje się przykład deklaracji typu `Order` z mapowaniem niestandardowego źródła danych zdefiniowanego dla obu właściwości.  
  
> [!NOTE]
> Model danych dla tego przykładu został zdefiniowany w temacie [How to: Create a Data Service przy użyciu dostawcy odbicia](create-a-data-service-using-rp-wcf-data-services.md).  
  
 [!code-csharp[Astoria Custom Feeds#CustomOrderFeed](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_custom_feeds/cs/orderitems.svc.cs#customorderfeed)]
 [!code-vb[Astoria Custom Feeds#CustomOrderFeed](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_custom_feeds/vb/orderitems.svc.vb#customorderfeed)]  
  
 Te atrybuty generują następujące niestandardowe strumieniowe źródło danych dla zestawu jednostek `Orders`. W tym dostosowanym kanale wartość właściwości `OrderId` jest wyświetlana tylko w `title` elemencie `entry`, a wartość właściwości `Customer` jest wyświetlana zarówno w elemencie `author`, jak i jako element właściwości `Customer`:  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResult](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/iqueryablefeedresult.xml#iqueryablefeedresult)]  
  
 Aby uzyskać więcej informacji, zobacz [How to: Dostosowywanie kanałów informacyjnych za pomocą dostawcy odbicia](how-to-customize-feeds-with-the-reflection-provider-wcf-data-services.md).  
  
## <a name="customizing-feeds-with-a-custom-data-service-provider"></a>Dostosowywanie kanałów informacyjnych za pomocą niestandardowego dostawcy usługi danych  
 Dostosowanie kanału informacyjnego dla modelu danych zdefiniowanego za pomocą niestandardowego dostawcy usługi danych jest zdefiniowane dla typu zasobu przez wywołanie <xref:System.Data.Services.Providers.ResourceType.AddEntityPropertyMappingAttribute%2A> na <xref:System.Data.Services.Providers.ResourceType>, który reprezentuje typ jednostki w modelu danych. Aby uzyskać więcej informacji, zobacz [niestandardowe dostawcy usług danych](custom-data-service-providers-wcf-data-services.md).  
  
## <a name="consuming-custom-feeds"></a>Zużywanie niestandardowych kanałów informacyjnych  
 Gdy aplikacja bezpośrednio zużywa strumieniowe źródło danych OData, musi być w stanie przetwarzać wszelkie niestandardowe elementy i atrybuty w zwracanym źródle danych. W przypadku zaimplementowania niestandardowych kanałów informacyjnych w modelu danych, niezależnie od dostawcy usługi danych, punkt końcowy `$metadata` zwraca niestandardowe informacje o źródle jako atrybuty niestandardowego kanału informacyjnego w CSDL zwróconym przez usługę danych. Korzystając z okna dialogowego **Dodaj odwołanie do usługi** lub narzędzia [DataSvcUtil. exe](wcf-data-service-client-utility-datasvcutil-exe.md) do generowania klas usługi danych klienta, niestandardowe atrybuty kanału informacyjnego są używane do zagwarantowania, że żądania i odpowiedzi do usługi danych są obsługiwane poprawnie.  
  
## <a name="feed-customization-considerations"></a>Zagadnienia dotyczące dostosowywania kanału informacyjnego  
 Podczas definiowania mapowań niestandardowych kanałów informacyjnych należy wziąć pod uwagę następujące kwestie.  
  
- Klient Usługi danych programu WCF traktuje zmapowane elementy w źródle danych jako puste, gdy zawierają tylko biały znak. W związku z tym mapowane elementy, które zawierają tylko biały znak, nie są w tym samym odstępie dostępne na kliencie. Aby zachować ten biały znak na kliencie, należy ustawić wartość `KeepInContext` na `true` w atrybucie mapowania źródła strumieniowego.  
  
## <a name="versioning-requirements"></a>Wymagania dotyczące wersji  
 Dostosowanie kanału informacyjnego ma następujące wymagania dotyczące wersji protokołu OData:  
  
- Dostosowanie kanału informacyjnego wymaga, aby usługa klienta i danych obsługiwały wersję 2,0 protokołu OData i nowsze wersje.  
  
 Aby uzyskać więcej informacji, zobacz [przechowywanie wersji usługi danych](data-service-versioning-wcf-data-services.md).  
  
## <a name="see-also"></a>Zobacz także

- [Dostawca odbicia](reflection-provider-wcf-data-services.md)
- [Dostawca programu Entity Framework](entity-framework-provider-wcf-data-services.md)
