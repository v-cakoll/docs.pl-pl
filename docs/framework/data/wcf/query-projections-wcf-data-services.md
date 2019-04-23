---
title: Projekcje zapytania (WCF Data Services)
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
ms.openlocfilehash: 2e4c40d6c71a254d5f40ea42788608e10c5872a7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59517177"
---
# <a name="query-projections-wcf-data-services"></a>Projekcje zapytania (WCF Data Services)

Projekcja udostępnia mechanizm w [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] zmniejszenie ilości danych w źródle danych zwróconych przez zapytanie, określając, że zwracane są tylko niektóre właściwości jednostki w odpowiedzi. Aby uzyskać więcej informacji, zobacz [OData: Wybierz opcję zapytania systemu ($select)](https://go.microsoft.com/fwlink/?LinkId=186076).

W tym temacie opisano, jak zdefiniować projekcji zapytań, jakie wymagania są dostępne dla jednostki i typu innego niż jednostka, dzięki czemu aktualizuje przewidywane wyniki, tworzenie typów przewidywane i wymieniono kilka kwestii projekcji.

## <a name="defining-a-query-projection"></a>Definiowanie projekcji zapytań

Możesz dodać klauzulę projekcji do zapytania przy użyciu `$select` zapytania w identyfikatorze URI lub za pomocą [wybierz](~/docs/csharp/language-reference/keywords/select-clause.md) — klauzula ([wybierz](~/docs/visual-basic/language-reference/queries/select-clause.md) w języku Visual Basic) w zapytaniu programu LINQ. Zwrócone jednostki danych może być przekazywany do typy jednostek i typów innych niż jednostek na komputerze klienckim. Przykłady w tym temacie prezentują sposób użycia `select` klauzuli w zapytaniu LINQ.

> [!IMPORTANT]
> Po zapisaniu aktualizacji, które zostały wprowadzone do typów przewidywanych w usłudze danych może dojść do utraty danych. Aby uzyskać więcej informacji, zobacz [zagadnienia projekcji](#considerations).

## <a name="requirements-for-entity-and-non-entity-types"></a>Wymagania dotyczące jednostek i typów innych niż jednostek

Typy jednostek musi mieć jedną lub więcej właściwości tożsamości, które tworzą klucz jednostki. Typy jednostek są definiowane na komputerach klienckich w jednej z następujących sposobów:

- Stosując <xref:System.Data.Services.Common.DataServiceKeyAttribute> lub <xref:System.Data.Services.Common.DataServiceEntityAttribute> do typu.

- Jeśli typ ma właściwość o nazwie `ID`.

- Jeśli typ ma właściwość o nazwie *typu*`ID`, gdzie *typu* jest nazwą typu.

Domyślnie gdy projekt wyników zapytania do typu zdefiniowanego po stronie klienta właściwości wymaganych w projekcji musi istnieć w typ klienta. Jednak po określeniu wartości `true` dla <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> właściwość <xref:System.Data.Services.Client.DataServiceContext>, właściwości określonych w projekcji nie muszą występować w typ klienta.

### <a name="making-updates-to-projected-results"></a>Wprowadzanie aktualizacji przewidywane wyniki

Gdy projekt wyników zapytania do typów jednostek na kliencie, <xref:System.Data.Services.Client.DataServiceContext> można śledzić tych obiektów za pomocą aktualizacji do wysłania do danych usługi, kiedy <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metoda jest wywoływana. Jednak aktualizacje, które zostały wprowadzone dane przedstawione typu innego niż jednostka na kliencie nie można wysłać do usługi danych. Jest to spowodowane bez klucza do identyfikowania wystąpienia jednostki, usługi danych nie można zaktualizować prawidłowe jednostki w źródle danych. Typy non jednostek nie są dołączone do <xref:System.Data.Services.Client.DataServiceContext>.

W przypadku przynajmniej jednej właściwości zdefiniowane w usłudze danych typu jednostki, nie występują w typie klienta, w którym przewidywany jest jednostka wstawia nowe jednostki nie będzie zawierać te brakujące właściwości. W tym przypadku będzie aktualizacji, które zostały wprowadzone do istniejących jednostek **również** nie zawierają tych brakuje właściwości. Jeśli wartość istnieje dla takich właściwości, aktualizacji Ponadto resetuje ją na wartość domyślną dla właściwości, zgodnie z definicją w źródle danych.

### <a name="creating-projected-types"></a>Tworzenie typów przewidywany

W poniższym przykładzie użyto anonimowe zapytania LINQ, która projektów związanych z adresem właściwości `Customers` typu w nowym `CustomerAddress` typ, który jest zdefiniowany na kliencie i jest określane jako typ jednostki:

[!code-csharp[Astoria Northwind Client#SelectCustomerAddressSpecific](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#selectcustomeraddressspecific)]
[!code-vb[Astoria Northwind Client#SelectCustomerAddressSpecific](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#selectcustomeraddressspecific)]

W tym przykładzie wzór inicjatora obiektu jest używany do utworzenia nowego wystąpienia `CustomerAddress` typu zamiast wywoływania konstruktora. Konstruktory nie są obsługiwane podczas projekcji do typów jednostek, ale mogą być używane podczas projekcji do typu innego niż jednostka i anonimowe. Ponieważ `CustomerAddress` jest typem jednostki, zmiany mogą być wykonywane i wysyłane z powrotem do usługi danych.

Ponadto dane z `Customer` typu jest rzutowany jako wystąpienia elementu `CustomerAddress` typu jednostki, a nie typu anonimowego. Projekcja do typów anonimowych jest obsługiwane, ale dane jest tylko do odczytu, ponieważ typy anonimowe są traktowane jako typu innego niż jednostka.

<xref:System.Data.Services.Client.MergeOption> Ustawienia <xref:System.Data.Services.Client.DataServiceContext> są używane do rozpoznawania tożsamości podczas projekcji zapytań. Oznacza to, że jeśli wystąpienie `Customer` typ już istnieje w <xref:System.Data.Services.Client.DataServiceContext>, wystąpienie `CustomerAddress` z tą samą tożsamością będą zgodne z reguły ustawione przez rozwiązanie tożsamości <xref:System.Data.Services.Client.MergeOption>

Poniżej opisano zachowania podczas przedstawiania wyników na typy jednostek i innego niż jednostka:

**Tworzenie nowego wystąpienia przewidywany przy użyciu inicjatorów**

- Przykład:

   [!code-csharp[Astoria Northwind Client#ProjectWithInitializer](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#projectwithinitializer)]
   [!code-vb[Astoria Northwind Client#ProjectWithInitializer](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#projectwithinitializer)]

- Typ jednostki: Obsługiwane

- Typ jednostki inne niż: Obsługiwane

**Tworzenie nowego wystąpienia przewidywany za pomocą konstruktorów**

- Przykład:

   [!code-csharp[Astoria Northwind Client#ProjectWithConstructor](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#projectwithconstructor)]
   [!code-vb[Astoria Northwind Client#ProjectWithConstructor](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#projectwithconstructor)]

- Typ jednostki: Element <xref:System.NotSupportedException> jest wywoływane.

- Typ jednostki inne niż: Obsługiwane

**Przy użyciu projekcji, aby przekształcić wartości właściwości**

- Przykład:

   [!code-csharp[Astoria Northwind Client#ProjectWithTransform](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#projectwithtransform)]
   [!code-vb[Astoria Northwind Client#ProjectWithTransform](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#projectwithtransform)]

- Typ jednostki: Ta transformacja nie jest obsługiwana dla typów jednostek, ponieważ może to prowadzić do nieporozumień i potencjalnie zastąpienie danych w źródle danych, który należy do innej jednostki. Element <xref:System.NotSupportedException> jest wywoływane.

- Typ jednostki inne niż: Obsługiwane

<a name="considerations"></a>

## <a name="projection-considerations"></a>Zagadnienia dotyczące projekcji

Następujące dodatkowe kwestie podczas definiowania projekcji zapytań.

- Podczas definiowania niestandardowego źródła danych dla formatu Atom, należy się upewnić, że wszystkie właściwości jednostki, które mają niestandardowe mapowania zdefiniowane są uwzględniane w projekcji danych. Gdy właściwość zamapowanego jednostki nie jest uwzględniony w projekcji, może dojść do utraty danych. Aby uzyskać więcej informacji, zobacz [kanału informacyjnego dostosowywania](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md).

- Podczas wstawiania zostaną wprowadzone do przewidywanego typu, który nie zawiera wszystkich właściwości jednostki w modelu danych usługi danych, właściwości nie są uwzględnione w projekcji po stronie klienta są ustawione na wartości domyślne.

- Gdy aktualizacje zostaną wprowadzone do przewidywanego typu, który nie zawiera wszystkich właściwości jednostki w modelu danych usługi danych, istniejące wartości, które nie są uwzględnione w projekcji na kliencie zostaną zastąpione wartościami domyślnymi niezainicjowany.

- Podczas projekcji zawiera właściwość typu złożonego, należy ponownie całego obiektu złożonego.

- Podczas projekcji zawiera właściwość nawigacji, powiązane obiekty są ładowane niejawnie, bez konieczności <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> metody. <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> Metoda do użycia w zapytaniu przewidywany jest nieobsługiwana.

- Kwerend projekcji zapytań na komputerze klienckim są tłumaczone na użyj `$select` zapytania opcji w identyfikatorze URI żądania. Gdy zapytanie o projekcji jest wykonywane względem poprzedniej wersji [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] , który nie obsługuje `$select` opcji zapytania zostanie zwrócony błąd. Przyczyną może też być podczas <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> z <xref:System.Data.Services.DataServiceBehavior> danych usługa jest ustawiona na wartość <xref:System.Data.Services.Common.DataServiceProtocolVersion.V1>. Aby uzyskać więcej informacji, zobacz [przechowywanie wersji usługi danych](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md).

Aby uzyskać więcej informacji, zobacz [jak: Projekt wyników zapytania](../../../../docs/framework/data/wcf/how-to-project-query-results-wcf-data-services.md).

## <a name="see-also"></a>Zobacz także

- [Wykonywanie zapytań do usługi danych](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
