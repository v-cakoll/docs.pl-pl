---
title: Zapytanie projekcje (usługi danych WCF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- projection [WCF Data Services]
- WCF Data Services, projection
- query projection [WCF Data Services]
- WCF Data Services, querying
ms.assetid: a09f4985-9f0d-48c8-b183-83d67a3dfe5f
ms.openlocfilehash: 903acaa7493dc83fd6bf50f5a578a067c15e6294
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365725"
---
# <a name="query-projections-wcf-data-services"></a>Zapytanie projekcje (usługi danych WCF)
Projekcja zapewnia mechanizm w [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Aby zmniejszyć ilość danych w źródle danych zwróconych przez zapytanie, określając, który niektórych właściwości jednostki są zwracane w odpowiedzi. Aby uzyskać więcej informacji, zobacz [OData: wybierz opcję zapytania systemu ($select)](http://go.microsoft.com/fwlink/?LinkId=186076).  
  
 W tym temacie opisano sposób do zdefiniowania projekcji zapytań, jakie wymagania są jednostki i typu innego niż jednostka, co aktualizacje wyniki przewidywane tworzenie typów planowane i zawiera niektóre uwagi projekcji.  
  
## <a name="defining-a-query-projection"></a>Definiowanie projekcji zapytań  
 Możesz dodać klauzulę projekcji do zapytania przy użyciu `$select` opcji w identyfikatorze URI lub za pomocą zapytania [wybierz](~/docs/csharp/language-reference/keywords/select-clause.md) klauzuli ([wybierz](~/docs/visual-basic/language-reference/queries/select-clause.md) w języku Visual Basic) w zapytaniu składnika LINQ. Zwrócony obiekt, który może zostać przedstawione danych na typy jednostek i typy jednostek z systemem innym niż na kliencie. Przykłady w tym temacie przedstawiają sposób użycia `select` klauzuli w zapytaniu składnika LINQ.  
  
> [!IMPORTANT]
>  Podczas zapisywania aktualizacji, które zostały wprowadzone do typów planowane w usłudze danych może dojść do utraty danych. Aby uzyskać więcej informacji, zobacz [zagadnienia projekcji](#considerations).  
  
## <a name="requirements-for-entity-and-non-entity-types"></a>Wymagania dotyczące jednostek i typy jednostek z systemem innym niż  
 Typy jednostek musi mieć co najmniej jednej właściwości tożsamości, wchodzące w skład klucza jednostki. Typy jednostek są definiowane dla klientów w jednym z następujących sposobów:  
  
-   Stosując <xref:System.Data.Services.Common.DataServiceKeyAttribute> lub <xref:System.Data.Services.Common.DataServiceEntityAttribute> do typu.  
  
-   Jeśli typ ma właściwości o nazwie `ID`.  
  
-   Jeśli typ ma właściwości o nazwie *typu*`ID`, gdzie *typu* jest nazwa typu.  
  
 Domyślnie gdy projekt wyników zapytania na typ zdefiniowany po stronie klienta, właściwości wymaganych w projekcji musi istnieć w typ klienta. Jednak po określeniu wartość `true` dla <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> właściwość <xref:System.Data.Services.Client.DataServiceContext>, określonych w projekcji właściwości nie są wymagane w typ klienta.  
  
### <a name="making-updates-to-projected-results"></a>Wprowadzanie aktualizacji do planowanego wyników  
 Gdy projekt wyników zapytania do typów jednostek na kliencie, <xref:System.Data.Services.Client.DataServiceContext> można śledzić te obiekty z aktualizacji na wysyłanie danych do usługi, gdy <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metoda jest wywoływana. Jednak aktualizacje, które zostały wprowadzone dane przedstawione jako typu innego niż jednostka na kliencie nie można wysłać do usługi danych. Jest to spowodowane bez klucza do identyfikacji wystąpienia jednostki, usługi danych nie można zaktualizować prawidłowe jednostki w źródle danych. Typy non jednostek nie są dołączone do <xref:System.Data.Services.Client.DataServiceContext>.  
  
 Gdy co najmniej jednej właściwości typu jednostki, zdefiniowane w usłudze danych, nie występują w typie klienta, do którego jest zaprojektowana jednostki wstawiania nowych jednostek nie będzie zawierać te brakuje właściwości. W takim przypadku zostanie aktualizacje wprowadzone w istniejących jednostek **również** zawiera te brakuje właściwości. Jeśli istnieje wartość dla takich właściwości, aktualizacja Ponadto resetuje go do wartości domyślnej dla właściwości, zgodnie z definicją w źródle danych.  
  
### <a name="creating-projected-types"></a>Tworzenie typów planowanego  
 W poniższym przykładzie użyto anonimowe zapytania LINQ, który projektów związanych z adresem właściwości `Customers` typu w nowym `CustomerAddress` typu, który jest zdefiniowany na kliencie i jest przypisywana jako typ jednostki:  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddressSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#selectcustomeraddressspecific)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddressSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#selectcustomeraddressspecific)]  
  
 W tym przykładzie wzorzec inicjatora obiektu służy do utworzenia nowego wystąpienia `CustmerAddress` typu zamiast wywoływania konstruktora. Konstruktory nie są obsługiwane w przypadku projekcji typów jednostek, ale mogą być używane podczas projekcji typu innego niż jednostka i anonimowe. Ponieważ `CustomerAddress` jest typem jednostki można wprowadzone zmiany i wysyłane z powrotem do usługi danych.  
  
 Ponadto dane z `Customer` typu jest zaprojektowana do wystąpienia `CustomerAddress` typu jednostki zamiast typu anonimowego. Projekcja na typy anonimowe jest obsługiwana, ale danych jest tylko do odczytu, ponieważ typy anonimowe są traktowane jako typu innego niż jednostka.  
  
 <xref:System.Data.Services.Client.MergeOption> Ustawienia <xref:System.Data.Services.Client.DataServiceContext> są używane do rozpoznawania tożsamości podczas projekcji zapytań. Oznacza to, że jeśli wystąpienie `Customer` typ już istnieje w <xref:System.Data.Services.Client.DataServiceContext>, wystąpienie `CustomerAddress` o tej samej tożsamości zastosują rozpoznawania tożsamości reguły ustawione przez <xref:System.Data.Services.Client.MergeOption>  
  
 W poniższej tabeli opisano zachowania podczas wykonywania projekcji wyników na typy jednostek i innego niż jednostka:  
  
|Akcja|Typ jednostki|Typu innego niż jednostka|  
|------------|-----------------|----------------------|  
|Tworzenie nowego wystąpienia planowane przy użyciu inicjatory, jak w poniższym przykładzie:<br /><br /> [!code-csharp[Astoria Northwind Client#ProjectWithInitializer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#projectwithinitializer)]
 [!code-vb[Astoria Northwind Client#ProjectWithInitializer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#projectwithinitializer)]|Obsługiwane|Obsługiwane|  
|Tworzenie nowego wystąpienia planowane za pomocą konstruktorów, jak w poniższym przykładzie:<br /><br /> [!code-csharp[Astoria Northwind Client#ProjectWithConstructor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#projectwithconstructor)]
 [!code-vb[Astoria Northwind Client#ProjectWithConstructor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#projectwithconstructor)]|A <xref:System.NotSupportedException> jest wywoływane.|Obsługiwane|  
|Przy użyciu projekcji, aby przekształcić wartości właściwości, jak w poniższym przykładzie:<br /><br /> [!code-csharp[Astoria Northwind Client#ProjectWithTransform](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#projectwithtransform)]
 [!code-vb[Astoria Northwind Client#ProjectWithTransform](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#projectwithtransform)]<br /><br /> To przekształcenie nie jest obsługiwane dla typów jednostek, ponieważ może to prowadzić do nieporozumień i potencjalnie zastępowania danych w źródle danych, który należy do innej jednostki.|A <xref:System.NotSupportedException> jest wywoływane.|Obsługiwane|  
  
<a name="considerations"></a>   
## <a name="projection-considerations"></a>Zagadnienia dotyczące projekcji  
 Następujące dodatkowe kwestie podczas definiowania projekcji zapytań.  
  
-   Podczas definiowania niestandardowych źródeł danych w formacie Atom, należy się upewnić, że wszystkie właściwości jednostki, które mają niestandardowy mapowania zdefiniowane znajdują się w projekcji. Gdy właściwość zamapowanych jednostki nie jest uwzględniony w projekcji, może dojść do utraty danych. Aby uzyskać więcej informacji, zobacz [źródła danych dostosowywania](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md).  
  
-   Podczas operacji wstawiania o projektowanego typu, który nie zawiera wszystkich właściwości jednostki w modelu danych usługi danych, właściwości nie są uwzględnione w projekcji po stronie klienta są ustawiane na wartości domyślne.  
  
-   Gdy aktualizacje zostały projektowanego typu, który nie zawiera wszystkich właściwości jednostki w modelu danych usługi danych, istniejące wartości, które nie są uwzględnione w projekcji na kliencie zostaną zastąpione wartościami domyślnymi niezainicjowany.  
  
-   Gdy projekcji zawiera właściwość złożoną, należy ponownie cały obiekt złożony.  
  
-   Gdy projekcji zawiera właściwość nawigacji, powiązane obiekty są ładowane niejawnie bez konieczności kontaktowania się z <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> metody. <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> Metoda nie jest obsługiwana do użytku w zapytaniu planowane.  
  
-   Zapytanie projekcji zapytań na kliencie są tłumaczone na użyj `$select` opcji w identyfikatorze URI żądania zapytania. Po wykonaniu zapytania o projekcji względem poprzedniej wersji [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] , który nie obsługuje `$select` opcji zapytania zostanie zwrócony błąd. To również zdarzyć, gdy <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> z <xref:System.Data.Services.DataServiceBehavior> danych usługa jest ustawiona na wartość <xref:System.Data.Services.Common.DataServiceProtocolVersion.V1>. Aby uzyskać więcej informacji, zobacz [przechowywanie wersji usługi danych](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md).  
  
 Aby uzyskać więcej informacji, zobacz [porady: wyniki zapytania projektu](../../../../docs/framework/data/wcf/how-to-project-query-results-wcf-data-services.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wykonywanie zapytań do usługi danych](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
