---
title: Dostawcy odbicia (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: ef5ba300-6d7c-455e-a7bd-d0cc6d211ad4
ms.openlocfilehash: e36f9124ec9979dac69b596c6d87491581ae9ec6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59159526"
---
# <a name="reflection-provider-wcf-data-services"></a>Dostawcy odbicia (WCF Data Services)
Oprócz udostępnianie danych z modelu danych przy użyciu platformy Entity Framework [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] mogą uwidocznić dane, które nie jest ściśle zdefiniowane w modelu opartego na jednostkę. Dostawca odbicia uwidacznia dane w klasach, które są zwracane typy, które implementują <xref:System.Linq.IQueryable%601> interfejsu. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] używa odbicia w celu model danych dla tych klas, a można przełożyć zapytania oparte na zasobach na zapytanie o języku zintegrowanym (LINQ)-na podstawie zapytań dotyczących narażonych <xref:System.Linq.IQueryable%601> typów.  
  
> [!NOTE]
>  Możesz użyć <xref:System.Linq.Queryable.AsQueryable%2A> metodę, aby zwrócić <xref:System.Linq.IQueryable%601> interfejsu od dowolnej klasy, która implementuje <xref:System.Collections.Generic.IEnumerable%601> interfejsu. Dzięki temu najbardziej ogólnych typów kolekcji ma być używany jako źródło danych dla usługi danych.  
  
 Dostawca odbicia obsługuje hierarchie typu. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie usługi danych przy użyciu dostawcy odbicia](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md).  
  
## <a name="inferring-the-data-model"></a>Wnioskowanie modelu danych  
 Podczas tworzenia usługi danych, dostawcę wnioskuje modelu danych przy użyciu odbicia. Na poniższej liście przedstawiono, jak dostawcy odbicia wnioskuje modelu danych:  
  
-   Kontener jednostek — klasa, która udostępnia dane jako właściwości, które zwracają <xref:System.Linq.IQueryable%601> wystąpienia. Podczas adresowania model danych oparty na odbiciu kontener jednostek reprezentuje katalog główny usługi. Tylko jedna jednostka klasy kontenera jest obsługiwana dla danego obszaru nazw.  
  
-   Zestawy jednostek - właściwości, które zwracają <xref:System.Linq.IQueryable%601> wystąpienia są traktowane jako zestawy jednostek. Zestawy jednostek są adresowane bezpośrednio jako zasoby w zapytaniu. Tylko jedna właściwość w kontenerze jednostki może zwrócić <xref:System.Linq.IQueryable%601> wystąpienia danego typu.  
  
-   Typy jednostek — typ `T` z <xref:System.Linq.IQueryable%601> , zwraca zestaw jednostek. Klasy, które są częścią hierarchii dziedziczenia są tłumaczone przez dostawcę odbicia w hierarchii typów jednostek równoważne.  
  
-   Klucze jednostek — każda klasa danych, który jest typem jednostki musi mieć właściwość klucza. Ta właściwość jest związana z <xref:System.Data.Services.Common.DataServiceKeyAttribute> atrybutu (`[DataServiceKeyAttribute]`).  
  
    > [!NOTE]
    >  Należy zastosować tylko <xref:System.Data.Services.Common.DataServiceKeyAttribute> atrybutu z właściwością, który może służyć do unikatowego identyfikowania wystąpienia typu jednostki. Ten atrybut jest ignorowany, gdy jest stosowany do właściwości nawigacji.  
  
-   Właściwości typu jednostki — inne niż klucz jednostki dostawcy odbicia traktuje dostępny, niebędące indeksatorami właściwości klasy, która jest typem jednostki w następujący sposób:  
  
    -   Jeśli właściwość zwraca typ pierwotny, właściwość jest przyjmowana przez właściwość typu jednostki.  
  
    -   Jeśli właściwość zwraca typ, który również jest typem jednostki, następnie właściwość jest zakłada się, że właściwość nawigacji, która reprezentuje "jeden" koniec relacji wiele do jednego czy jeden.  
  
    -   Jeśli właściwość ta zwraca <xref:System.Collections.Generic.IEnumerable%601> typu jednostki, następnie właściwość zakłada się, że właściwość nawigacji, który reprezentuje "many" end relacji jeden do wielu lub wiele do wielu.  
  
    -   Jeśli zwracany typ właściwości to typ wartości, właściwość reprezentuje typ złożony.  
  
> [!NOTE]
>  W przeciwieństwie do modelu danych, który jest oparty na modelu relacyjnego jednostki modeli, które są oparte na dostawcy odbicia nie rozumieją, opartego na danych relacyjnych. Należy używać programu Entity Framework do udostępnienia danych relacyjnych za pośrednictwem [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].  
  
## <a name="data-type-mapping"></a>Mapowanie typu danych  
 Gdy model danych jest wnioskowany z klas .NET Framework, typy pierwotne w modelu danych są mapowane na typy danych .NET Framework w następujący sposób:  
  
|Typ danych .NET framework|Typ modelu danych|  
|------------------------------|---------------------|  
|<xref:System.Byte> `[]`|`Edm.Binary`|  
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
>  Typy o wartości zerowalnej .NET framework są mapowane na te same typy danych w modelu, jako odpowiednie typy wartości nie można przypisać wartości null.  
  
## <a name="enabling-updates-in-the-data-model"></a>Włączenie aktualizacji w modelu danych  
 Aby zezwolić na aktualizacje danych, która jest dostępna za pośrednictwem tego rodzaju modelu danych, definiuje dostawcy odbicia <xref:System.Data.Services.IUpdatable> interfejsu. Ten interfejs powoduje, że usługi danych na temat sposobu utrwalić aktualizacje narażonych typów. Aby włączyć aktualizacje do zasobów, które są zdefiniowane w modelu danych, musi implementować klasy kontenera jednostki <xref:System.Data.Services.IUpdatable> interfejsu. Na przykład implementacja <xref:System.Data.Services.IUpdatable> interfejsu, zobacz [jak: Tworzenie usługi danych przy użyciu LINQ do SQL źródła danych](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).  
  
 <xref:System.Data.Services.IUpdatable> Interfejsu wymaga, że następujące elementy członkowskie można zaimplementować tak, aby aktualizacje mogą być przekazywane do źródła danych przy użyciu dostawcy odbicia:  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|<xref:System.Data.Services.IUpdatable.AddReferenceToCollection%2A>|Oferuje funkcje, aby dodać obiekt do kolekcji powiązanych obiektów, które są dostępne z właściwością nawigacji.|  
|<xref:System.Data.Services.IUpdatable.ClearChanges%2A>|Oferuje funkcje, który anuluje oczekujące zmiany w danych.|  
|<xref:System.Data.Services.IUpdatable.CreateResource%2A>|Oferuje funkcje w celu utworzenia nowego zasobu w określonym kontenerze.|  
|<xref:System.Data.Services.IUpdatable.DeleteResource%2A>|Oferuje funkcje, które można usunąć zasobu.|  
|<xref:System.Data.Services.IUpdatable.GetResource%2A>|Oferuje funkcje, które można pobrać z zasobem, który jest identyfikowany przez nazwę zapytania i typu.|  
|<xref:System.Data.Services.IUpdatable.GetValue%2A>|Zapewnia funkcje zwracają wartość właściwości zasobu.|  
|<xref:System.Data.Services.IUpdatable.RemoveReferenceFromCollection%2A>|Oferuje funkcje, aby usunąć obiekt kolekcji powiązanych obiektów dostępne z właściwością nawigacji.|  
|<xref:System.Data.Services.IUpdatable.ResetResource%2A>|Oferuje funkcje, które można zaktualizować określonego zasobu.|  
|<xref:System.Data.Services.IUpdatable.ResolveResource%2A>|Zapewnia funkcje zwracają zasobu, który jest reprezentowany przez wystąpienie określonego obiektu.|  
|<xref:System.Data.Services.IUpdatable.SaveChanges%2A>|Oferuje funkcje, aby zapisać wszystkie oczekujące zmiany.|  
|<xref:System.Data.Services.IUpdatable.SetReference%2A>|Oferuje funkcje, aby ustawić odwołanie do obiektu pokrewnego przy użyciu właściwości nawigacji.|  
|<xref:System.Data.Services.IUpdatable.SetValue%2A>|Oferuje funkcje, które można ustawić wartości właściwości zasobu.|  
  
## <a name="handling-concurrency"></a>Obsługa współbieżności  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] obsługuje model optymistycznej współbieżności, umożliwiając Definiowanie tokenem współbieżności dla jednostki. Ten token współbieżności, który zawiera jedną lub więcej właściwości jednostki, jest używany przez usługę danych do określenia, czy nastąpiła zmiana w danych, która jest wymagana, zaktualizowanych lub usuniętych. Gdy token wartości z elementu eTag w żądaniu różnią się od wartości bieżącej jednostki, wyjątek jest zgłaszany przez usługę danych. <xref:System.Data.Services.ETagAttribute> Jest stosowany do typu jednostki, aby zdefiniować tokenem współbieżności w dostawcy odbicia. Token współbieżności nie może zawierać właściwości klucza lub właściwości nawigacji. Aby uzyskać więcej informacji, zobacz [aktualizacja usługi danych](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).  
  
## <a name="using-linq-to-sql-with-the-reflection-provider"></a>Za pomocą LINQ to SQL za pomocą dostawcy odbicia  
 Ponieważ Entity Framework jest obsługiwany natywnie domyślne, dostawca danych zalecane jest dotyczące korzystania z danych relacyjnych z [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Jednak można użyć dostawcy odbicia używać programu LINQ do klas SQL z usługą danych. <xref:System.Data.Linq.Table%601> Zestawy, które są zwracane przez metody na wyników <xref:System.Data.Linq.DataContext> generowane w składniku LINQ to SQL Object Relational Designer (O/R Designer) implementacja <xref:System.Linq.IQueryable%601> interfejsu. Dzięki temu dostawcy odbicia, dostęp do tych metod oraz zwracanych danych jednostki z programu SQL Server przy użyciu wygenerowanej klasy programu LINQ to SQL. Jednak ponieważ LINQ to SQL nie implementuje <xref:System.Data.Services.IUpdatable> interfejsu, należy dodać częściową klasą, która rozszerza istniejący <xref:System.Data.Linq.DataContext> klasy częściowej, aby dodać <xref:System.Data.Services.IUpdatable> implementacji. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie usługi danych przy użyciu LINQ do SQL źródła danych](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).  
  
## <a name="see-also"></a>Zobacz także

- [Dostawcy usług danych](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
