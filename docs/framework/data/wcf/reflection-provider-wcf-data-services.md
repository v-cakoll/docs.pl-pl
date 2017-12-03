---
title: "Dostawca odbicia (usługi danych WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF Data Services, providers
ms.assetid: ef5ba300-6d7c-455e-a7bd-d0cc6d211ad4
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 52fe7e777cfea04b6da2a04c0badfe92b2a0a756
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="reflection-provider-wcf-data-services"></a>Dostawca odbicia (usługi danych WCF)
Oprócz udostępnianie danych z modelu danych za pośrednictwem programu Entity Framework [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] mogą uwidaczniać ściśle nie jest zdefiniowany w modelu jednostki na podstawie danych. Dostawca odbicia udostępnia dane klas, które zwracają typów, które implementują <xref:System.Linq.IQueryable%601> interfejsu. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]używa odbicia do wywnioskowania modelu danych dla tych klas i może dokonywać translacji oparte na adresie zapytań względem zasobów na język kwerendy zintegrowanym (LINQ) — na podstawie zapytań dotyczących narażonych <xref:System.Linq.IQueryable%601> typów.  
  
> [!NOTE]
>  Można użyć <xref:System.Linq.Queryable.AsQueryable%2A> metodę, aby zwrócić <xref:System.Linq.IQueryable%601> każda klasa implementująca interfejs <xref:System.Collections.Generic.IEnumerable%601> interfejsu. Dzięki temu najbardziej ogólnym typy kolekcji do użycia jako źródło danych dla usługi danych.  
  
 Dostawca odbicia obsługuje hierarchie typu. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie usługi danych przy użyciu dostawcy odbicia](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md).  
  
## <a name="inferring-the-data-model"></a>Wnioskowanie modelu danych  
 Podczas tworzenia usługi data dostawcy wnioskuje modelu danych przy użyciu odbicia. Na poniższej liście przedstawiono, jak dostawca odbicia wnioskuje modelu danych:  
  
-   Kontener jednostki — klasa, która udostępnia dane jako właściwości, które zwracają <xref:System.Linq.IQueryable%601> wystąpienia. Podczas adresowania model oparty na odbiciu danych kontenera jednostek reprezentuje katalog główny usługi. Klasa kontenera tylko jednego podmiotu jest obsługiwana dla danej przestrzeni nazw.  
  
-   Ustawia jednostki — właściwości, które zwracają <xref:System.Linq.IQueryable%601> wystąpienia są traktowane jako zestawy jednostek. Zestawy jednostek są opisane bezpośrednio jako zasoby w zapytaniu. Tylko jedna właściwość w kontenerze obiektów, może zwrócić <xref:System.Linq.IQueryable%601> wystąpienia danego typu.  
  
-   Typy jednostek — typ `T` z <xref:System.Linq.IQueryable%601> czy zwraca zestaw jednostek. Klasy, które są częścią hierarchii dziedziczenia są tłumaczone przez dostawcę odbicia w hierarchii typów jednostek równoważne.  
  
-   Klucze jednostek - każdej klasy danych, który jest typem jednostki musi mieć właściwość klucza. Ta właściwość ma atrybut <xref:System.Data.Services.Common.DataServiceKeyAttribute> atrybutu (`[DataServiceKeyAttribute]`).  
  
    > [!NOTE]
    >  Stosuje tylko <xref:System.Data.Services.Common.DataServiceKeyAttribute> atrybutu do właściwości, która może służyć do unikatowego identyfikowania wystąpienia typu jednostki. Ten atrybut jest ignorowany, gdy jest stosowany do właściwości nawigacji.  
  
-   Właściwości typu jednostki - innych niż key jednostki dostawcy odbicia traktuje dostępny, — do indeksatora właściwości klasy, która jest typem jednostki w następujący sposób:  
  
    -   Jeśli właściwość zwraca typ pierwotny, następnie właściwość zakłada się, że właściwość typu jednostki.  
  
    -   Jeśli właściwość zwraca typ, który jest również typem jednostki, następnie właściwość zakłada się, że właściwość nawigacji, która reprezentuje "jeden" koniec relację wiele do jednego czy jeden.  
  
    -   Jeśli właściwość zwraca <xref:System.Collections.Generic.IEnumerable%601> typu jednostki, następnie właściwość zakłada się, że właściwość nawigacji, która reprezentuje stronie "wielu" relacji jeden do wielu lub wiele do wielu.  
  
    -   Jeśli zwracany typ właściwości jest typem wartości, właściwość reprezentuje typ złożony.  
  
> [!NOTE]
>  W przeciwieństwie do modelu danych jest oparty na modelu jednostki relacyjne modeli, które są oparte na dostawcy odbicia nie rozumie relacyjnej bazie danych. Należy używać programu Entity Framework do udostępnienia danych relacyjnych za pośrednictwem [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].  
  
## <a name="data-type-mapping"></a>Mapowanie typu danych  
 W przypadku modelu danych jest wywnioskowany na podstawie klasy .NET Framework, typy pierwotne w modelu danych są mapowane na typy danych .NET Framework w następujący sposób:  
  
|Typ danych .NET framework|Typ modelu danych|  
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
>  Typy dopuszczające wartości zerowe wartości .NET framework są mapowane na ten sam typ modelu danych jako odpowiednie typy wartości nie można przypisać wartości null.  
  
## <a name="enabling-updates-in-the-data-model"></a>Włączenie aktualizacji w modelu danych  
 Aby zezwalać na aktualizacje, aby dane, które jest dostępne za pośrednictwem tego rodzaju modelu danych, dostawca odbicia definiuje <xref:System.Data.Services.IUpdatable> interfejsu. Ten interfejs powoduje, że usługa danych na temat sposobu utrwalić aktualizacje narażonych typów. Aby włączyć aktualizacje z zasobami, które są zdefiniowane przez model danych, musi implementować klasę kontenera jednostek <xref:System.Data.Services.IUpdatable> interfejsu. Na przykład implementacja <xref:System.Data.Services.IUpdatable> interfejsu, zobacz [porady: Tworzenie usługi danych przy użyciu składnika LINQ to SQL źródła danych](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).  
  
 <xref:System.Data.Services.IUpdatable> Interfejs wymaga się wykonanie następujących członków tak, aby aktualizacje mogą być przekazywane do źródła danych przy użyciu odbicia dostawcy:  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|<xref:System.Data.Services.IUpdatable.AddReferenceToCollection%2A>|Udostępnia funkcje, które można dodać obiektu do kolekcji obiektów pokrewnych, które są dostępne z właściwości nawigacji.|  
|<xref:System.Data.Services.IUpdatable.ClearChanges%2A>|Zawiera funkcję, która spowoduje anulowanie oczekujących zmian danych.|  
|<xref:System.Data.Services.IUpdatable.CreateResource%2A>|Udostępnia funkcje umożliwiające tworzenie nowego zasobu w określonym kontenerze.|  
|<xref:System.Data.Services.IUpdatable.DeleteResource%2A>|Udostępnia funkcję można usunąć zasobu.|  
|<xref:System.Data.Services.IUpdatable.GetResource%2A>|Udostępnia funkcje, które można pobrać z zasobem, który jest identyfikowane przez nazwę zapytania i typu.|  
|<xref:System.Data.Services.IUpdatable.GetValue%2A>|Udostępnia funkcje, które ma zostać zwrócona wartość właściwości zasobu.|  
|<xref:System.Data.Services.IUpdatable.RemoveReferenceFromCollection%2A>|Udostępnia funkcje do usunięcia obiektu do kolekcji obiektów pokrewnych dostępne z właściwości nawigacji.|  
|<xref:System.Data.Services.IUpdatable.ResetResource%2A>|Udostępnia funkcje, które można zaktualizować określonego zasobu.|  
|<xref:System.Data.Services.IUpdatable.ResolveResource%2A>|Udostępnia funkcje umożliwiające zwrócił zasobu reprezentowanego przez wystąpienie określonego obiektu.|  
|<xref:System.Data.Services.IUpdatable.SaveChanges%2A>|Udostępnia funkcję, aby zapisać wszystkie zmiany oczekujące.|  
|<xref:System.Data.Services.IUpdatable.SetReference%2A>|Udostępnia funkcje, które można ustawić za pomocą właściwości nawigacji odwołania obiektu pokrewnego.|  
|<xref:System.Data.Services.IUpdatable.SetValue%2A>|Udostępnia funkcje, które można ustawić wartości właściwości zasobu.|  
  
## <a name="handling-concurrency"></a>Obsługa współbieżności  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]obsługuje model optymistycznej współbieżności, umożliwiając zdefiniowanie tokenem współbieżności dla jednostki. Ten token współbieżności, który zawiera co najmniej jednej właściwości jednostki, jest używany przez usługę danych do określenia, czy w danych, który jest wymagany, zaktualizowanych lub usuniętych nastąpiła zmiana. Gdy wartości tokenu z elementem eTag w żądaniu różnią się od bieżących wartości podmiotu, wyjątek zgłoszony przez usługę danych. <xref:System.Data.Services.ETagAttribute> Jest stosowany do typu jednostki, aby zdefiniować tokenem współbieżności w dostawcy odbicia. Token współbieżności nie może zawierać właściwości klucza lub właściwości nawigacji. Aby uzyskać więcej informacji, zobacz [aktualizacji usługi danych](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).  
  
## <a name="using-linq-to-sql-with-the-reflection-provider"></a>Przy użyciu składnika LINQ to SQL z dostawcą odbicia  
 Ponieważ programu Entity Framework jest obsługiwany natywnie domyślnie, dostawcę danych zalecane jest dotyczące korzystania z danych relacyjnych z [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Jednak można użyć dostawcy odbicia do użycia LINQ w klasach SQL z usługą danych. <xref:System.Data.Linq.Table%601> Zestawy, które są zwracane przez metody na wyników <xref:System.Data.Linq.DataContext> generowane przez składnik LINQ to SQL Projektant obiektów relacyjnych (Projektanta obiektów relacyjnych) wdrożenie <xref:System.Linq.IQueryable%601> interfejsu. Dzięki temu dostawcy odbicia dostępu do tych metod i zwróć jednostki danych z programu SQL Server za pomocą wygenerowanego LINQ w klasach SQL. Jednak ponieważ LINQ do SQL nie implementuje <xref:System.Data.Services.IUpdatable> interfejsu, musisz dodać częściowej klasy, która rozszerza istniejący <xref:System.Data.Linq.DataContext> częściowej klasy, aby dodać <xref:System.Data.Services.IUpdatable> implementacji. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie usługi danych przy użyciu składnika LINQ to SQL źródła danych](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Dostawców usług danych](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
