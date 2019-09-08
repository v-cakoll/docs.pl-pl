---
title: Dostawca odbicia (Usługi danych programu WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: ef5ba300-6d7c-455e-a7bd-d0cc6d211ad4
ms.openlocfilehash: c3e160f96be2a95262776994152a06b42b475887
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779808"
---
# <a name="reflection-provider-wcf-data-services"></a>Dostawca odbicia (Usługi danych programu WCF)

Oprócz udostępniania danych z modelu danych za pośrednictwem Entity Framework, program [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] może uwidaczniać dane, które nie są ściśle zdefiniowane w modelu opartym na jednostkach. Dostawca odbicia uwidacznia dane w klasach, które zwracają typy implementujące <xref:System.Linq.IQueryable%601> interfejs. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]używa odbicia w celu wywnioskowania modelu danych dla tych klas i może tłumaczyć zapytania oparte na adresach do zasobów w zapytaniach opartych na programie Language <xref:System.Linq.IQueryable%601> Integrated Query (LINQ) względem uwidocznionych typów.

> [!NOTE]
> Można użyć <xref:System.Linq.Queryable.AsQueryable%2A> metody do <xref:System.Linq.IQueryable%601> zwrócenia interfejsu z <xref:System.Collections.Generic.IEnumerable%601> dowolnej klasy, która implementuje interfejs. Pozwala to na większość typów kolekcji ogólnych, które będą używane jako źródło danych dla usługi danych.

Dostawca odbicia obsługuje hierarchie typów. Aby uzyskać więcej informacji, zobacz [jak: Utwórz usługę danych przy użyciu dostawcy](create-a-data-service-using-rp-wcf-data-services.md)odbicia.

## <a name="inferring-the-data-model"></a>Wnioskowanie modelu danych

Podczas tworzenia usługi danych dostawca wnioskuje model danych przy użyciu odbicia. Na poniższej liście przedstawiono sposób, w jaki dostawca odbicia wnioskuje o model danych:

- Kontener jednostek — Klasa, która uwidacznia dane jako właściwości, które zwracają <xref:System.Linq.IQueryable%601> wystąpienie. Podczas rozwiązywania modelu danych opartych na odbiciach kontener jednostek reprezentuje element główny usługi. Dla danego obszaru nazw jest obsługiwana tylko jedna Klasa kontenera jednostek.

- Zestawy jednostek — właściwości zwracające <xref:System.Linq.IQueryable%601> wystąpienia są traktowane jako zestawy jednostek. Zestawy jednostek są rozkierowane bezpośrednio jako zasoby w zapytaniu. Tylko jedna Właściwość kontenera jednostek może zwracać <xref:System.Linq.IQueryable%601> wystąpienie danego typu.

- Typy jednostek — typ `T` <xref:System.Linq.IQueryable%601> zwracany przez zestaw jednostek. Klasy, które są częścią hierarchii dziedziczenia, są tłumaczone przez dostawcę odbicia na równoważną hierarchię typów jednostek.

- Klucze jednostek — każda klasa danych będąca typem jednostki musi mieć właściwość Key. Ta właściwość ma <xref:System.Data.Services.Common.DataServiceKeyAttribute> atrybut (`[DataServiceKeyAttribute]`).

    > [!NOTE]
    > Należy zastosować <xref:System.Data.Services.Common.DataServiceKeyAttribute> atrybut tylko do właściwości, która może służyć do unikatowego identyfikowania wystąpienia typu jednostki. Ten atrybut jest ignorowany w przypadku zastosowania do właściwości nawigacji.

- Właściwości typu jednostki — inne niż klucz jednostki, dostawca odbicia traktuje dostępne właściwości inne niż indeksator klasy, która jest typem jednostki w następujący sposób:

  - Jeśli właściwość zwraca typ pierwotny, przyjmuje się, że właściwość jest właściwością typu jednostki.

  - Jeśli właściwość zwraca typ, który jest również typem jednostki, przyjmuje się, że właściwość jest właściwością nawigacji reprezentującą "jeden" koniec relacji wiele-do-jednego lub jeden-do-jednego.

  - Jeśli właściwość zwraca <xref:System.Collections.Generic.IEnumerable%601> typ jednostki, przyjmuje się, że właściwość jest właściwością nawigacji reprezentującą "wiele" końce relacji jeden-do-wielu lub wiele-do-wielu.

  - Jeśli zwracany typ właściwości jest typem wartości, właściwość reprezentuje typ złożony.

> [!NOTE]
> W przeciwieństwie do modelu danych opartego na modelu Entity-relacyjnym modele, które są oparte na dostawcy odbicia, nie rozumieją danych relacyjnych. W celu udostępnienia danych [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]relacyjnych należy używać Entity Framework.

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

Aby zezwolić na aktualizacje danych, które są udostępniane za pomocą tego rodzaju modelu danych, dostawca odbicia definiuje <xref:System.Data.Services.IUpdatable> interfejs. Ten interfejs powoduje, że usługa danych będzie utrzymywać aktualizacje dla uwidocznionych typów. Aby włączyć aktualizacje dla zasobów, które są zdefiniowane przez model danych, Klasa kontenera jednostek musi implementować <xref:System.Data.Services.IUpdatable> interfejs. Przykład implementacji <xref:System.Data.Services.IUpdatable> interfejsu można znaleźć w temacie [How to: Tworzenie usługi danych przy użyciu źródła](create-a-data-service-using-linq-to-sql-wcf.md)danych LINQ to SQL.

<xref:System.Data.Services.IUpdatable> Interfejs wymaga, aby następujące składowe zostały zaimplementowane, aby aktualizacje mogły być propagowane do źródła danych za pomocą dostawcy odbicia:

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

[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]obsługuje optymistyczny model współbieżności, umożliwiając zdefiniowanie tokenu współbieżności dla jednostki. Ten token współbieżności, który zawiera co najmniej jedną właściwość jednostki, jest używany przez usługę danych w celu ustalenia, czy wprowadzono zmianę w danych, które są żądane, aktualizowane lub usuwane. Gdy wartości tokenu uzyskane z elementu eTag w żądaniu różnią się od bieżących wartości jednostki, wyjątek jest wywoływany przez usługę danych. Stosuje <xref:System.Data.Services.ETagAttribute> się do typu jednostki, aby zdefiniować Token współbieżności w dostawcy odbicia. Token współbieżności nie może zawierać właściwości Key ani właściwości nawigacji. Aby uzyskać więcej informacji, zobacz [Aktualizowanie usługi danych](updating-the-data-service-wcf-data-services.md).

## <a name="using-linq-to-sql-with-the-reflection-provider"></a>Używanie LINQ to SQL z dostawcą odbicia

Ponieważ Entity Framework jest natywnie obsługiwana domyślnie, jest to zalecany dostawca danych służący do korzystania z danych relacyjnych [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]w programie. Można jednak użyć dostawcy odbicia, aby użyć LINQ to SQL klas z usługą danych. Zestawy wyników, które są zwracane przez metody <xref:System.Data.Linq.DataContext> wygenerowane przez Object Relational Designer LINQ to SQL (Projektant O/ <xref:System.Linq.IQueryable%601> R) implementują interfejs. <xref:System.Data.Linq.Table%601> Dzięki temu dostawca odbicia może uzyskiwać dostęp do tych metod i zwracać dane jednostki z SQL Server przy użyciu wygenerowanych klas LINQ to SQL. Jednak ponieważ LINQ to SQL nie implementuje <xref:System.Data.Services.IUpdatable> interfejsu, należy dodać klasę częściową, która rozszerza istniejącą <xref:System.Data.Linq.DataContext> klasę <xref:System.Data.Services.IUpdatable> częściową, aby dodać implementację. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie usługi danych przy użyciu źródła](create-a-data-service-using-linq-to-sql-wcf.md)danych LINQ to SQL.

## <a name="see-also"></a>Zobacz także

- [Dostawcy usług danych](data-services-providers-wcf-data-services.md)
