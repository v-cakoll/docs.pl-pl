---
title: Projekcje zapytań (Usługi danych programu WCF)
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
ms.openlocfilehash: 17475cccf461371a909660bfe3f8db29bf1fa2fe
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975171"
---
# <a name="query-projections-wcf-data-services"></a>Projekcje zapytań (Usługi danych programu WCF)

Projekcja zapewnia mechanizm w protokole Open Data Protocol (OData), aby zmniejszyć ilość danych w kanale informacyjnym zwracanym przez zapytanie, określając, że tylko niektóre właściwości jednostki są zwracane w odpowiedzi. Aby uzyskać więcej informacji, zobacz Usługa [OData: SELECT system Query Option ($Select)](https://go.microsoft.com/fwlink/?LinkId=186076).

W tym temacie opisano, jak zdefiniować projekcję zapytania, jakie są wymagania dotyczące jednostek i typów niezwiązanych z jednostkami, wprowadzać aktualizacje przewidywanych wyników, tworzyć projekcje typy i wymieniać niektóre zagadnienia dotyczące projekcji.

## <a name="defining-a-query-projection"></a>Definiowanie projekcji zapytania

Do zapytania można dodać klauzulę projekcji przy użyciu opcji zapytania `$select` w identyfikatorze URI lub przy użyciu klauzuli [SELECT](../../../csharp/language-reference/keywords/select-clause.md) ([SELECT](../../../visual-basic/language-reference/queries/select-clause.md) in Visual Basic) w zapytaniu LINQ. Zwrócone dane jednostki mogą być rzutowane na typy jednostek lub typy niezwiązane z jednostką na kliencie. Przykłady w tym temacie przedstawiają sposób użycia klauzuli `select` w zapytaniu LINQ.

> [!IMPORTANT]
> Utrata danych może wystąpić w usłudze danych podczas zapisywania aktualizacji, które zostały wprowadzone do przewidywanych typów. Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące projekcji](#considerations).

## <a name="requirements-for-entity-and-non-entity-types"></a>Wymagania dotyczące jednostek i typów niebędących jednostkami

Typy jednostek muszą mieć co najmniej jedną właściwość tożsamości, która składa się z klucza jednostki. Typy jednostek są zdefiniowane na klientach w jeden z następujących sposobów:

- Zastosowanie <xref:System.Data.Services.Common.DataServiceKeyAttribute> lub <xref:System.Data.Services.Common.DataServiceEntityAttribute> do typu.

- Gdy typ ma właściwość o nazwie `ID`.

- Gdy typ ma właściwość o nazwie *type*`ID`, gdzie *Type* jest nazwą typu.

Domyślnie podczas tworzenia projektu wyników zapytania do typu zdefiniowanego na kliencie właściwości wymagane w projekcji muszą istnieć w typie klienta. Jednak po określeniu wartości `true` właściwości <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> <xref:System.Data.Services.Client.DataServiceContext>właściwości określone w projekcji nie są wymagane do wystąpienia w typie klienta.

### <a name="making-updates-to-projected-results"></a>Wprowadzanie aktualizacji rzutowanych wyników

Podczas tworzenia projektu wyników zapytania w typach jednostek na kliencie <xref:System.Data.Services.Client.DataServiceContext> mogą śledzić te obiekty z aktualizacjami, które zostaną wysłane z powrotem do usługi danych po wywołaniu metody <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A>. Jednak aktualizacje wprowadzane do danych rzutowanych na typy niebędące jednostkami na kliencie nie mogą być wysyłane z powrotem do usługi danych. Jest to spowodowane brakiem klucza do zidentyfikowania wystąpienia jednostki, ponieważ usługa danych nie może zaktualizować prawidłowej jednostki w źródle danych. Typy inne niż jednostki nie są dołączone do <xref:System.Data.Services.Client.DataServiceContext>.

Gdy co najmniej jedna z właściwości typu jednostki zdefiniowanego w usłudze danych nie występuje w typie klienta, do którego jest rzutowana jednostka, wstawienia nowych jednostek nie będą zawierać tych brakujących właściwości. W takim przypadku aktualizacje wprowadzane do istniejących jednostek **również** nie będą zawierać tych brakujących właściwości. Gdy dla takiej właściwości istnieje wartość, aktualizacja resetuje ją do wartości domyślnej właściwości, zgodnie z definicją w źródle danych.

### <a name="creating-projected-types"></a>Tworzenie typów projekcji

W poniższym przykładzie zastosowano anonimowe zapytanie LINQ, które projektuje właściwości powiązane z adresem typu `Customers`, do nowego typu `CustomerAddress`, który jest zdefiniowany na kliencie i jest przypisany jako typ jednostki:

[!code-csharp[Astoria Northwind Client#SelectCustomerAddressSpecific](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#selectcustomeraddressspecific)]
[!code-vb[Astoria Northwind Client#SelectCustomerAddressSpecific](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#selectcustomeraddressspecific)]

W tym przykładzie wzorzec inicjatora obiektów jest używany do utworzenia nowego wystąpienia typu `CustomerAddress`, a nie wywołania konstruktora. Konstruktory nie są obsługiwane podczas projekcji w typach jednostek, ale mogą być używane podczas projekcji do typów nienależących do jednostki i anonimowe. Ponieważ `CustomerAddress` jest typem jednostki, zmiany można wprowadzać i wysyłać z powrotem do usługi danych.

Ponadto dane z typu `Customer` są rzutowane na wystąpienie typu jednostki `CustomerAddress`, a nie typu anonimowego. Obsługiwane są projekcje w typach anonimowych, ale dane są tylko do odczytu, ponieważ typy anonimowe są traktowane jako typy niebędące jednostkami.

<xref:System.Data.Services.Client.MergeOption> ustawienia <xref:System.Data.Services.Client.DataServiceContext> są używane do rozpoznawania tożsamości podczas projekcji zapytania. Oznacza to, że jeśli wystąpienie `Customer` typu już istnieje w <xref:System.Data.Services.Client.DataServiceContext>, wystąpienie `CustomerAddress` z tą samą tożsamością będzie zgodne z regułami rozpoznawania tożsamości ustawionymi przez <xref:System.Data.Services.Client.MergeOption>

Poniżej opisano zachowania podczas projekcji wyników do jednostek i typów nienależących do jednostek:

**Tworzenie nowego projektu wystąpienia przy użyciu inicjatorów**

- Przykład:

   [!code-csharp[Astoria Northwind Client#ProjectWithInitializer](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#projectwithinitializer)]
   [!code-vb[Astoria Northwind Client#ProjectWithInitializer](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#projectwithinitializer)]

- Typ jednostki: obsługiwane

- Typ niebędący jednostką: obsługiwane

**Tworzenie nowego projektu wystąpienia przy użyciu konstruktorów**

- Przykład:

   [!code-csharp[Astoria Northwind Client#ProjectWithConstructor](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#projectwithconstructor)]
   [!code-vb[Astoria Northwind Client#ProjectWithConstructor](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#projectwithconstructor)]

- Typ jednostki: wywołano <xref:System.NotSupportedException>.

- Typ niebędący jednostką: obsługiwane

**Przekształcanie wartości właściwości przy użyciu projekcji**

- Przykład:

   [!code-csharp[Astoria Northwind Client#ProjectWithTransform](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#projectwithtransform)]
   [!code-vb[Astoria Northwind Client#ProjectWithTransform](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#projectwithtransform)]

- Typ jednostki: to transformacja nie jest obsługiwana w przypadku typów jednostek, ponieważ może to prowadzić do pomyłek i może zastępowanie danych w źródle danych, które należą do innej jednostki. Zostanie zgłoszony <xref:System.NotSupportedException>.

- Typ niebędący jednostką: obsługiwane

<a name="considerations"></a>

## <a name="projection-considerations"></a>Zagadnienia dotyczące projekcji

Podczas definiowania projekcji zapytania należy stosować następujące zagadnienia dodatkowe.

- Podczas definiowania niestandardowych kanałów informacyjnych dla formatu Atom należy upewnić się, że wszystkie właściwości jednostki, które mają zdefiniowane niestandardowe mapowania, są zawarte w projekcji. Gdy właściwość mapowanego obiektu nie jest uwzględniona w projekcji, może dojść do utraty danych. Aby uzyskać więcej informacji, zobacz temat [Dostosowywanie kanału informacyjnego](feed-customization-wcf-data-services.md).

- Gdy operacje wstawiania są wprowadzane do typu przewidywanego, który nie zawiera wszystkich właściwości jednostki w modelu danych usługi danych, właściwości, które nie są uwzględnione w projekcji na kliencie, są ustawiane na wartości domyślne.

- Gdy aktualizacje są wprowadzane do typu przewidywanego, który nie zawiera wszystkich właściwości jednostki w modelu danych usługi danych, istniejące wartości, które nie są uwzględnione w projekcji na kliencie, zostaną zastąpione zainicjowanymi wartościami domyślnymi.

- Gdy projekcja zawiera złożoną właściwość, należy zwrócić cały obiekt złożony.

- Gdy projekcja zawiera właściwość nawigacji, powiązane obiekty są ładowane niejawnie bez konieczności wywoływania metody <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A>. Metoda <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> nie jest obsługiwana w zapytaniach rzutowanych.

- Zapytania dotyczące projekcji zapytań na kliencie są tłumaczone na użycie opcji zapytania `$select` w identyfikatorze URI żądania. Gdy zapytanie z projekcją jest wykonywane względem poprzedniej wersji [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], która nie obsługuje opcji zapytania `$select`, zwracany jest błąd. Może się to zdarzyć, gdy <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> <xref:System.Data.Services.DataServiceBehavior> dla usługi danych ma ustawioną wartość <xref:System.Data.Services.Common.DataServiceProtocolVersion.V1>. Aby uzyskać więcej informacji, zobacz [przechowywanie wersji usługi danych](data-service-versioning-wcf-data-services.md).

Aby uzyskać więcej informacji, zobacz [How to: Project Results Query](how-to-project-query-results-wcf-data-services.md).

## <a name="see-also"></a>Zobacz także

- [Wykonywanie zapytań do usługi danych](querying-the-data-service-wcf-data-services.md)
