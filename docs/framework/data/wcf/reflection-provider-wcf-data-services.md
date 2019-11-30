---
title: Dostawca odbicia (Usługi danych programu WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: ef5ba300-6d7c-455e-a7bd-d0cc6d211ad4
ms.openlocfilehash: 0eeb223093d709cfe2722c2ad7cf622164eab32f
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568875"
---
# <a name="reflection-provider-wcf-data-services"></a>Dostawca odbicia (Usługi danych programu WCF)

Oprócz udostępniania danych z modelu danych za pośrednictwem Entity Framework, Usługi danych programu WCF może uwidaczniać dane, które nie są ściśle zdefiniowane w modelu opartym na jednostkach. Dostawca odbicia uwidacznia dane w klasach, które zwracają typy implementujące interfejs <xref:System.Linq.IQueryable%601>. Usługi danych programu WCF używa odbicia w celu wywnioskowania modelu danych dla tych klas i może tłumaczyć zapytania oparte na adresach do zasobów w zapytaniach opartych na programie Language Integrated Query (LINQ) na <xref:System.Linq.IQueryable%601> uwidocznionych typów.

> [!NOTE]
> Za pomocą metody <xref:System.Linq.Queryable.AsQueryable%2A> można zwrócić interfejs <xref:System.Linq.IQueryable%601> z dowolnej klasy implementującej interfejs <xref:System.Collections.Generic.IEnumerable%601>. Pozwala to na większość typów kolekcji ogólnych, które będą używane jako źródło danych dla usługi danych.

Dostawca odbicia obsługuje hierarchie typów. Aby uzyskać więcej informacji, zobacz [How to: Create a Data Service przy użyciu dostawcy odbicia](create-a-data-service-using-rp-wcf-data-services.md).

## <a name="inferring-the-data-model"></a>Wnioskowanie modelu danych

Podczas tworzenia usługi danych dostawca wnioskuje model danych przy użyciu odbicia. Na poniższej liście przedstawiono sposób, w jaki dostawca odbicia wnioskuje o model danych:

- Kontener jednostek — Klasa, która uwidacznia dane jako właściwości, które zwracają wystąpienie <xref:System.Linq.IQueryable%601>. Podczas rozwiązywania modelu danych opartych na odbiciach kontener jednostek reprezentuje element główny usługi. Dla danego obszaru nazw jest obsługiwana tylko jedna Klasa kontenera jednostek.

- Zestawy jednostek — właściwości zwracające wystąpienia <xref:System.Linq.IQueryable%601> są traktowane jako zestawy jednostek. Zestawy jednostek są rozkierowane bezpośrednio jako zasoby w zapytaniu. Tylko jedna Właściwość kontenera jednostek może zwracać wystąpienie <xref:System.Linq.IQueryable%601> danego typu.

- Typy jednostek — typ `T` <xref:System.Linq.IQueryable%601>, które zwraca zestaw jednostek. Klasy, które są częścią hierarchii dziedziczenia, są tłumaczone przez dostawcę odbicia na równoważną hierarchię typów jednostek.

- Klucze jednostek — każda klasa danych będąca typem jednostki musi mieć właściwość Key. Ta właściwość ma atrybut <xref:System.Data.Services.Common.DataServiceKeyAttribute> (`[DataServiceKeyAttribute]`).

    > [!NOTE]
    > Do właściwości, która może być używana do unikatowego identyfikowania wystąpienia typu jednostki, należy zastosować atrybut <xref:System.Data.Services.Common.DataServiceKeyAttribute>. Ten atrybut jest ignorowany w przypadku zastosowania do właściwości nawigacji.

- Właściwości typu jednostki — inne niż klucz jednostki, dostawca odbicia traktuje dostępne właściwości inne niż indeksator klasy, która jest typem jednostki w następujący sposób:

  - Jeśli właściwość zwraca typ pierwotny, przyjmuje się, że właściwość jest właściwością typu jednostki.

  - Jeśli właściwość zwraca typ, który jest również typem jednostki, przyjmuje się, że właściwość jest właściwością nawigacji reprezentującą "jeden" koniec relacji wiele-do-jednego lub jeden-do-jednego.

  - Jeśli właściwość zwraca <xref:System.Collections.Generic.IEnumerable%601> typu jednostki, przyjmuje się, że właściwość jest właściwością nawigacji reprezentującą "wiele" końce relacji jeden-do-wielu lub wiele-do-wielu.

  - Jeśli zwracany typ właściwości jest typem wartości, właściwość reprezentuje typ złożony.

> [!NOTE]
> W przeciwieństwie do modelu danych opartego na modelu Entity-relacyjnym modele, które są oparte na dostawcy odbicia, nie rozumieją danych relacyjnych. Użyj Entity Framework, aby uwidocznić dane relacyjne za pomocą Usługi danych programu WCF.

## <a name="data-type-mapping"></a>Mapowanie typu danych

Gdy model danych jest wywnioskowany na podstawie klas .NET Framework, typy pierwotne w modelu danych są mapowane na .NET Framework typów danych w następujący sposób:

|Typ danych .NET Framework|Typ modelu danych|
|------------------------------|---------------------|
|<xref:System.Byte>`[]`|`Edm.Binary`|
|<xref:System.Boolean>|`Edm.Boolean`|
|<xref:System.Byte>|`Edm.Byte`|
|<xref:System.DateTime>|`Edm.DateTime`|
|<xref:System.Decimal>|`Edm.Decimal`|
|<xref:System.Double>|`Edm.Double`|
|<xref:System.Guid>|`Edm.Guid`|
|<xref:System.Int16>|`Edm.Int16`|
|<xref:System.Int32>|`Edm.Int32`|
|<xref:System.Int64>|`Edm.Int64`|
|<xref:System.SByte>|`Edm.SByte`|
|<xref:System.Single>|`Edm.Single`|
|<xref:System.String>|`Edm.String`|

> [!NOTE]
> Typy wartości null .NET Framework są mapowane na te same typy modeli danych co odpowiednie typy wartości, których nie można przypisać do wartości null.

## <a name="enabling-updates-in-the-data-model"></a>Włączanie aktualizacji w modelu danych

Aby zezwolić na aktualizacje danych, które są udostępniane za pomocą tego rodzaju modelu danych, dostawca odbicia definiuje interfejs <xref:System.Data.Services.IUpdatable>. Ten interfejs powoduje, że usługa danych będzie utrzymywać aktualizacje dla uwidocznionych typów. Aby włączyć aktualizacje dla zasobów, które są zdefiniowane przez model danych, Klasa kontenera jednostek musi implementować interfejs <xref:System.Data.Services.IUpdatable>. Przykład implementacji interfejsu <xref:System.Data.Services.IUpdatable> można znaleźć w temacie [How to: Create a Data Service przy użyciu LINQ to SQL źródła danych](create-a-data-service-using-linq-to-sql-wcf.md).

Interfejs <xref:System.Data.Services.IUpdatable> wymaga zaimplementowania następujących elementów członkowskich, aby aktualizacje mogły być propagowane do źródła danych za pomocą dostawcy odbicia:

|Element członkowski|Opis|
|------------|-----------------|
|<xref:System.Data.Services.IUpdatable.AddReferenceToCollection%2A>|Udostępnia funkcje umożliwiające dodanie obiektu do kolekcji powiązanych obiektów, do których uzyskuje się dostęp z właściwości nawigacji.|
|<xref:System.Data.Services.IUpdatable.ClearChanges%2A>|Oferuje funkcje, które anulują oczekujące zmiany w danych.|
|<xref:System.Data.Services.IUpdatable.CreateResource%2A>|Oferuje funkcje do tworzenia nowego zasobu w określonym kontenerze.|
|<xref:System.Data.Services.IUpdatable.DeleteResource%2A>|Zapewnia funkcjonalność do usunięcia zasobu.|
|<xref:System.Data.Services.IUpdatable.GetResource%2A>|Oferuje funkcje do pobierania zasobu, który jest identyfikowany przez określone zapytanie i nazwę typu.|
|<xref:System.Data.Services.IUpdatable.GetValue%2A>|Oferuje funkcje zwracające wartość właściwości zasobu.|
|<xref:System.Data.Services.IUpdatable.RemoveReferenceFromCollection%2A>|Oferuje funkcje do usuwania obiektu do kolekcji powiązanych obiektów, do których można uzyskać dostęp z właściwości nawigacji.|
|<xref:System.Data.Services.IUpdatable.ResetResource%2A>|Oferuje funkcje do aktualizowania określonego zasobu.|
|<xref:System.Data.Services.IUpdatable.ResolveResource%2A>|Oferuje funkcje do zwracania zasobu reprezentowanego przez określone wystąpienie obiektu.|
|<xref:System.Data.Services.IUpdatable.SaveChanges%2A>|Oferuje funkcje do zapisywania wszystkich oczekujących zmian.|
|<xref:System.Data.Services.IUpdatable.SetReference%2A>|Zapewnia funkcjonalność do ustawiania powiązanego odwołania do obiektu za pomocą właściwości nawigacji.|
|<xref:System.Data.Services.IUpdatable.SetValue%2A>|Udostępnia funkcje do ustawiania wartości właściwości zasobu.|

## <a name="handling-concurrency"></a>Obsługa współbieżności

Usługi danych programu WCF obsługuje optymistyczny model współbieżności, umożliwiając zdefiniowanie tokenu współbieżności dla jednostki. Ten token współbieżności, który zawiera co najmniej jedną właściwość jednostki, jest używany przez usługę danych w celu ustalenia, czy wprowadzono zmianę w danych, które są żądane, aktualizowane lub usuwane. Gdy wartości tokenu uzyskane z elementu eTag w żądaniu różnią się od bieżących wartości jednostki, wyjątek jest wywoływany przez usługę danych. <xref:System.Data.Services.ETagAttribute> jest stosowany do typu jednostki w celu zdefiniowania tokenu współbieżności w dostawcy odbicia. Token współbieżności nie może zawierać właściwości Key ani właściwości nawigacji. Aby uzyskać więcej informacji, zobacz [Aktualizowanie usługi danych](updating-the-data-service-wcf-data-services.md).

## <a name="using-linq-to-sql-with-the-reflection-provider"></a>Używanie LINQ to SQL z dostawcą odbicia

Ponieważ Entity Framework jest natywnie obsługiwana domyślnie, jest to zalecany dostawca danych służący do korzystania z danych relacyjnych z Usługi danych programu WCF. Można jednak użyć dostawcy odbicia, aby użyć LINQ to SQL klas z usługą danych. Zestawy wyników <xref:System.Data.Linq.Table%601>, które są zwracane przez metody <xref:System.Data.Linq.DataContext> generowane przez LINQ to SQL Object Relational Designer (Projektant O/R) implementują interfejs <xref:System.Linq.IQueryable%601>. Dzięki temu dostawca odbicia może uzyskiwać dostęp do tych metod i zwracać dane jednostki z SQL Server przy użyciu wygenerowanych klas LINQ to SQL. Jednak ponieważ LINQ to SQL nie implementuje interfejsu <xref:System.Data.Services.IUpdatable>, należy dodać klasę częściową, która rozszerza istniejącą <xref:System.Data.Linq.DataContext> częściowej klasy w celu dodania implementacji <xref:System.Data.Services.IUpdatable>. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie usługi danych przy użyciu źródła danych LINQ to SQL](create-a-data-service-using-linq-to-sql-wcf.md).

## <a name="see-also"></a>Zobacz także

- [Dostawcy usług danych](data-services-providers-wcf-data-services.md)
