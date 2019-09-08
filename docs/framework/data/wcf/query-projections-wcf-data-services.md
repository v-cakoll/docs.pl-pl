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
ms.openlocfilehash: 8128fd3cab0ca20da87a1a98c2657aefab96beaf
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779819"
---
# <a name="query-projections-wcf-data-services"></a>Projekcje zapytań (Usługi danych programu WCF)

Projekcja udostępnia mechanizm w [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] celu zmniejszenia ilości danych w strumieniu informacyjnym zwracanym przez zapytanie przez określenie, że tylko niektóre właściwości jednostki są zwracane w odpowiedzi. Aby uzyskać więcej informacji, [zobacz OData: Wybierz opcję kwerendy systemowej ($select](https://go.microsoft.com/fwlink/?LinkId=186076)).

W tym temacie opisano, jak zdefiniować projekcję zapytania, jakie są wymagania dotyczące jednostek i typów niezwiązanych z jednostkami, wprowadzać aktualizacje przewidywanych wyników, tworzyć projekcje typy i wymieniać niektóre zagadnienia dotyczące projekcji.

## <a name="defining-a-query-projection"></a>Definiowanie projekcji zapytania

Do zapytania można dodać klauzulę projekcji przy użyciu `$select` opcji zapytania w identyfikatorze URI lub przy użyciu klauzuli [SELECT](../../../csharp/language-reference/keywords/select-clause.md) ([SELECT](../../../visual-basic/language-reference/queries/select-clause.md) in Visual Basic) w zapytaniu LINQ. Zwrócone dane jednostki mogą być rzutowane na typy jednostek lub typy niezwiązane z jednostką na kliencie. Przykłady w tym temacie przedstawiają sposób użycia `select` klauzuli w zapytaniu LINQ.

> [!IMPORTANT]
> Utrata danych może wystąpić w usłudze danych podczas zapisywania aktualizacji, które zostały wprowadzone do przewidywanych typów. Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące projekcji](#considerations).

## <a name="requirements-for-entity-and-non-entity-types"></a>Wymagania dotyczące jednostek i typów niebędących jednostkami

Typy jednostek muszą mieć co najmniej jedną właściwość tożsamości, która składa się z klucza jednostki. Typy jednostek są zdefiniowane na klientach w jeden z następujących sposobów:

- Stosując <xref:System.Data.Services.Common.DataServiceKeyAttribute> lub<xref:System.Data.Services.Common.DataServiceEntityAttribute> do typu.

- Gdy typ ma właściwość o nazwie `ID`.

- Gdy typ ma *Właściwość o nazwie*`ID`Type, gdzie *Type* jest nazwą typu.

Domyślnie podczas tworzenia projektu wyników zapytania do typu zdefiniowanego na kliencie właściwości wymagane w projekcji muszą istnieć w typie klienta. Jeśli jednak określisz wartość `true` <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> właściwości <xref:System.Data.Services.Client.DataServiceContext>, właściwości określone w projekcji nie są wymagane do wystąpienia w typie klienta.

### <a name="making-updates-to-projected-results"></a>Wprowadzanie aktualizacji rzutowanych wyników

Podczas tworzenia projektu wyników zapytania w typach jednostek na kliencie <xref:System.Data.Services.Client.DataServiceContext> można śledzić te obiekty z aktualizacjami, które zostaną wysłane z powrotem do usługi danych <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> po wywołaniu metody. Jednak aktualizacje wprowadzane do danych rzutowanych na typy niebędące jednostkami na kliencie nie mogą być wysyłane z powrotem do usługi danych. Jest to spowodowane brakiem klucza do zidentyfikowania wystąpienia jednostki, ponieważ usługa danych nie może zaktualizować prawidłowej jednostki w źródle danych. Typy inne niż jednostki nie są dołączone do <xref:System.Data.Services.Client.DataServiceContext>elementu.

Gdy co najmniej jedna z właściwości typu jednostki zdefiniowanego w usłudze danych nie występuje w typie klienta, do którego jest rzutowana jednostka, wstawienia nowych jednostek nie będą zawierać tych brakujących właściwości. W takim przypadku aktualizacje wprowadzane do istniejących jednostek **również** nie będą zawierać tych brakujących właściwości. Gdy dla takiej właściwości istnieje wartość, aktualizacja resetuje ją do wartości domyślnej właściwości, zgodnie z definicją w źródle danych.

### <a name="creating-projected-types"></a>Tworzenie typów projekcji

W poniższym przykładzie jest używane anonimowe zapytanie LINQ, które tworzy projekty właściwości `Customers` związanych z adresem typu w nowym `CustomerAddress` typie, który jest zdefiniowany na kliencie i jest przypisany jako typ jednostki:

[!code-csharp[Astoria Northwind Client#SelectCustomerAddressSpecific](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#selectcustomeraddressspecific)]
[!code-vb[Astoria Northwind Client#SelectCustomerAddressSpecific](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#selectcustomeraddressspecific)]

W tym przykładzie wzorzec inicjatora obiektów jest używany do utworzenia nowego wystąpienia `CustomerAddress` typu zamiast wywołania konstruktora. Konstruktory nie są obsługiwane podczas projekcji w typach jednostek, ale mogą być używane podczas projekcji do typów nienależących do jednostki i anonimowe. Ponieważ `CustomerAddress` jest typem jednostki, zmiany mogą być wprowadzane i wysyłane z powrotem do usługi danych.

Ponadto dane z `Customer` typu są rzutowane na wystąpienie `CustomerAddress` typu jednostki zamiast typu anonimowego. Obsługiwane są projekcje w typach anonimowych, ale dane są tylko do odczytu, ponieważ typy anonimowe są traktowane jako typy niebędące jednostkami.

<xref:System.Data.Services.Client.MergeOption> Ustawienia<xref:System.Data.Services.Client.DataServiceContext> są używane do rozpoznawania tożsamości podczas projekcji zapytania. Oznacza to, że jeśli wystąpienie `Customer` typu już istnieje <xref:System.Data.Services.Client.DataServiceContext>w, wystąpienie `CustomerAddress` o tej samej tożsamości będzie zgodne z regułami rozpoznawania tożsamości ustawionymi przez<xref:System.Data.Services.Client.MergeOption>

Poniżej opisano zachowania podczas projekcji wyników do jednostek i typów nienależących do jednostek:

**Tworzenie nowego projektu wystąpienia przy użyciu inicjatorów**

- Przykład:

   [!code-csharp[Astoria Northwind Client#ProjectWithInitializer](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#projectwithinitializer)]
   [!code-vb[Astoria Northwind Client#ProjectWithInitializer](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#projectwithinitializer)]

- Typ jednostki: Obsługiwane

- Typ niebędący jednostką: Obsługiwane

**Tworzenie nowego projektu wystąpienia przy użyciu konstruktorów**

- Przykład:

   [!code-csharp[Astoria Northwind Client#ProjectWithConstructor](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#projectwithconstructor)]
   [!code-vb[Astoria Northwind Client#ProjectWithConstructor](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#projectwithconstructor)]

- Typ jednostki: <xref:System.NotSupportedException> Jest wywoływany.

- Typ niebędący jednostką: Obsługiwane

**Przekształcanie wartości właściwości przy użyciu projekcji**

- Przykład:

   [!code-csharp[Astoria Northwind Client#ProjectWithTransform](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#projectwithtransform)]
   [!code-vb[Astoria Northwind Client#ProjectWithTransform](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#projectwithtransform)]

- Typ jednostki: Ta transformacja nie jest obsługiwana w przypadku typów jednostek, ponieważ może to prowadzić do pomyłek i może zastępowanie danych w źródle danych, które należą do innej jednostki. <xref:System.NotSupportedException> Jest wywoływany.

- Typ niebędący jednostką: Obsługiwane

<a name="considerations"></a>

## <a name="projection-considerations"></a>Zagadnienia dotyczące projekcji

Podczas definiowania projekcji zapytania należy stosować następujące zagadnienia dodatkowe.

- Podczas definiowania niestandardowych kanałów informacyjnych dla formatu Atom należy upewnić się, że wszystkie właściwości jednostki, które mają zdefiniowane niestandardowe mapowania, są zawarte w projekcji. Gdy właściwość mapowanego obiektu nie jest uwzględniona w projekcji, może dojść do utraty danych. Aby uzyskać więcej informacji, zobacz temat [Dostosowywanie kanału informacyjnego](feed-customization-wcf-data-services.md).

- Gdy operacje wstawiania są wprowadzane do typu przewidywanego, który nie zawiera wszystkich właściwości jednostki w modelu danych usługi danych, właściwości, które nie są uwzględnione w projekcji na kliencie, są ustawiane na wartości domyślne.

- Gdy aktualizacje są wprowadzane do typu przewidywanego, który nie zawiera wszystkich właściwości jednostki w modelu danych usługi danych, istniejące wartości, które nie są uwzględnione w projekcji na kliencie, zostaną zastąpione zainicjowanymi wartościami domyślnymi.

- Gdy projekcja zawiera złożoną właściwość, należy zwrócić cały obiekt złożony.

- Gdy projekcja zawiera właściwość nawigacji, powiązane obiekty są ładowane niejawnie bez konieczności wywoływania <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> metody. <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> Metoda nie jest obsługiwana w zapytaniach rzutowanych.

- Zapytania o projekcje zapytań na kliencie są tłumaczone na użycie `$select` opcji zapytania w identyfikatorze URI żądania. Gdy zapytanie z projekcją jest wykonywane względem poprzedniej wersji [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] , która nie `$select` obsługuje opcji zapytania, zwracany jest błąd. Taka sytuacja może mieć miejsce, <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> gdy <xref:System.Data.Services.DataServiceBehavior> dla usługi dla danych <xref:System.Data.Services.Common.DataServiceProtocolVersion.V1>ustawiono wartość. Aby uzyskać więcej informacji, zobacz [przechowywanie wersji usługi danych](data-service-versioning-wcf-data-services.md).

Aby uzyskać więcej informacji, zobacz [jak: Wyniki](how-to-project-query-results-wcf-data-services.md)zapytania projektu.

## <a name="see-also"></a>Zobacz także

- [Wykonywanie zapytań do usługi danych](querying-the-data-service-wcf-data-services.md)
