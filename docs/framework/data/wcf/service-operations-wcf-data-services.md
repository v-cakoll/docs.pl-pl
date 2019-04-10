---
title: Operacje usługi (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: 583a690a-e60f-4990-8991-d6efce069d76
ms.openlocfilehash: b63c6d8f3a5a949299a925a321ca8f01c67b1d8f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211975"
---
# <a name="service-operations-wcf-data-services"></a>Operacje usługi (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Umożliwia zdefiniowanie operacji usługi w usłudze data ujawniać metod na serwerze. Podobnie jak inne zasoby usługi danych operacji usługi są rozwiązywane przez identyfikatory URI. Operacje usługi umożliwiają udostępnianie logikę biznesową w usłudze danych, takich jak zaimplementować logikę weryfikacji, aby zastosować zabezpieczenia oparte na rolach, lub do udostępnienia wyspecjalizowane możliwościami wysyłania zapytań. Operacje usługi są dodawane do klasie usługi danych, która pochodzi z metody <xref:System.Data.Services.DataService%601>. Podobnie jak wszystkich innych zasobów usługi danych możesz podać parametry do metody operacji usługi. Na przykład, następujące operacja identyfikator URI usługi (na podstawie [Szybki Start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) usługi danych) przekazuje wartość `London` do `city` parametru:  
  
```  
http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'  
```  
  
 Definicja dla tej operacji usługa jest w następujący sposób:  
  
 [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperationdef)]
 [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperationdef)]  
  
 Możesz użyć <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> z <xref:System.Data.Services.DataService%601> do uzyskania bezpośredniego dostępu do źródła danych, którego używa Usługa danych. Aby uzyskać więcej informacji, zobacz [jak: Definiowanie operacji usługi](../../../../docs/framework/data/wcf/how-to-define-a-service-operation-wcf-data-services.md).  
  
 Aby uzyskać informacji na temat do wywołania operacji usługi aplikacji klienta .NET Framework, zobacz [wywoływanie operacji usługi](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md).  
  
## <a name="service-operation-requirements"></a>Wymagania dotyczące operacji usługi  
 Obowiązują następujące wymagania podczas definiowania operacji usługi dla usługi danych. Jeśli metoda nie spełnia tych wymagań, nie będą widoczne jako operacje obsługi dla usługi danych.  
  
-   Operacja musi być metodą publiczne wystąpienia, która jest elementem członkowskim klasy usługi danych.  
  
-   Metoda operacji może akceptować tylko parametry wejściowe. Nie można uzyskać dostępu do danych przesyłanych w treści komunikatu przez usługę danych.  
  
-   Jeśli parametry są definiowane, typ każdego parametru musi być typem pierwotnym. Wszelkie dane typu innego niż podstawowy musi serializacji i przekazywana do parametru ciągu.  
  
-   Metoda musi zwracać jedną z następujących czynności:  
  
    -   `void` (`Nothing` w języku Visual Basic)  
  
    -   <xref:System.Collections.Generic.IEnumerable%601>  
  
    -   <xref:System.Linq.IQueryable%601>  
  
    -   Typ jednostki w modelu danych usługi ujawnia w danych.  
  
    -   Klasa pierwotnych, np. integer lub string.  
  
-   W celu obsługi opcji zapytania, takich jak sortowanie, stronicowanie i filtrowanie, powinna zwrócić metody operacji usługi <xref:System.Linq.IQueryable%601>. Do operacji usługi, które obejmują opcje zapytania będą odrzucane dla operacji, które zwraca tylko <xref:System.Collections.Generic.IEnumerable%601>.  
  
-   Aby można było obsługiwać dostęp do powiązanych jednostek przy użyciu właściwości nawigacji, operacja usługi musi zwracać <xref:System.Linq.IQueryable%601>.  
  
-   Metoda musi być oznaczona przy użyciu `[WebGet]` lub `[WebInvoke]` atrybutu.  
  
    -   `[WebGet]` Włącza metodę do wywołania przez za pomocą żądania GET.  
  
    -   `[WebInvoke(Method = "POST")]` Włącza metodę można wywołać za pomocą żądania POST. Inne <xref:System.ServiceModel.Web.WebInvokeAttribute> metody nie są obsługiwane.  
  
-   Operacja usługi może być oznaczona przy użyciu <xref:System.Data.Services.SingleResultAttribute> określający, że wartość zwracana z metody jest pojedynczy element, a nie w kolekcji jednostek. Wykonywania tego rozróżnienia nakazują wynikowy serializacji odpowiedzi i sposób, w których przejścia właściwość nawigacji dodatkowe są reprezentowane w identyfikatorze URI. Na przykład korzystając z AtomPub serializacji, wystąpienie typu pojedynczego zasobu jest reprezentowany jako element wejścia i zestaw wystąpień jako element kanału informacyjnego.  
  
## <a name="addressing-service-operations"></a>Adresowanie operacji usługi  
 Operacje usługi można rozwiązać, umieszczając nazwę metody w pierwszy segment ścieżki identyfikatora URI. Na przykład następujący identyfikator URI uzyskuje dostęp do `GetOrdersByState` operację, która zwraca <xref:System.Linq.IQueryable%601> zbiór `Orders` obiektów.  
  
```  
http://localhost:12345/Northwind.svc/GetOrdersByState?state='CA'&includeItems=true  
```  
  
 Podczas wywoływania operacji usługi, parametry są dostarczane jako opcji zapytania. Poprzednia operacja usługi przyjmuje jako parametr ciągu `state` i parametrem logicznym `includeItems` oznacza to, czy do uwzględnienia powiązane `Order_Detail` obiektów w odpowiedzi.  
  
 Poniżej przedstawiono prawidłowe typy zwracane dla operacji usługowej:  
  
|Prawidłowe typy zwracane|Reguł identyfikatorów URI|  
|------------------------|---------------|  
|`void` (`Nothing` w języku Visual Basic)<br /><br /> —lub—<br /><br /> Typy jednostek<br /><br /> —lub—<br /><br /> Typy pierwotne|Identyfikator URI musi być segmentu pojedynczą ścieżkę, która jest nazwą operacji usługi. Opcje zapytania nie są dozwolone.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Identyfikator URI musi być segmentu pojedynczą ścieżkę, która jest nazwą operacji usługi. Ponieważ nie jest typu wyniku <xref:System.Linq.IQueryable%601> typu, opcje zapytania są niedozwolone.|  
|<xref:System.Linq.IQueryable%601>|Segmenty ścieżki zapytanie poza ścieżką, która jest nazwą operacji usługi są dozwolone. Opcje zapytania są również dozwolone.|  
  
 Segmenty ścieżki dodatkowe lub opcje zapytania mogą być dodawane do identyfikatora URI, w zależności od typu zwracanego operacji usługi. Na przykład, następujący identyfikator URI uzyskuje dostęp do `GetOrdersByCity` operację, która zwraca <xref:System.Linq.IQueryable%601> zbiór `Orders` obiektów, uporządkowane według `RequiredDate` w kolejności malejącej, wraz z powiązane `Order_Details` obiektów:  
  
```  
http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc  
```  
  
## <a name="service-operations-access-control"></a>Kontrola dostępu operacji usługi  
 Widoczność obejmujących całą usługę operacji usługi jest kontrolowana przez <xref:System.Data.Services.IDataServiceConfiguration.SetServiceOperationAccessRule%2A> metody <xref:System.Data.Services.IDataServiceConfiguration> klasy w taki sam sposób czy widoczność zestaw jednostek jest kontrolowany za pomocą <xref:System.Data.Services.IDataServiceConfiguration.SetEntitySetAccessRule%2A> metody. Na przykład następujący wiersz kodu w definicji usługi danych umożliwia dostęp do `CustomersByCity` operacji usługi.  
  
 [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperationconfig)]
 [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperationconfig)]  
  
> [!NOTE]
>  Jeśli operacja usługi ma zwracany typ, który został ukryty przez ograniczenie dostępu na podstawowe zestawy jednostek, operacja usługi nie będzie dostępna dla aplikacji klienckich.  
  
 Aby uzyskać więcej informacji, zobacz [jak: Definiowanie operacji usługi](../../../../docs/framework/data/wcf/how-to-define-a-service-operation-wcf-data-services.md).  
  
## <a name="raising-exceptions"></a>Występowanie wyjątków  
 Firma Microsoft zaleca użycie <xref:System.Data.Services.DataServiceException> klasy zawsze wtedy, gdy zgłosić wyjątek podczas wykonywania usługi danych. Jest to spowodowane wie, środowisko wykonawcze usług danych jak poprawnie zamapować właściwości tego obiektu wyjątku komunikatu odpowiedzi HTTP. Gdy zostanie podniesiony <xref:System.Data.Services.DataServiceException> operacji usługi otoczona zwrócony wyjątek <xref:System.Reflection.TargetInvocationException>. Do zwrócenia z base <xref:System.Data.Services.DataServiceException> bez obejmującego <xref:System.Reflection.TargetInvocationException>, konieczne jest przesłonięcie <xref:System.Data.Services.DataService%601.HandleException%2A> method in Class metoda <xref:System.Data.Services.DataService%601>, Wyodrębnij <xref:System.Data.Services.DataServiceException> z <xref:System.Reflection.TargetInvocationException>i zwracanie go jako błąd najwyższego poziomu, jak w poniższym przykładzie:  
  
 [!code-csharp[Astoria Northwind Service#HandleExceptions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#handleexceptions)]
 [!code-vb[Astoria Northwind Service#HandleExceptions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#handleexceptions)]  
  
## <a name="see-also"></a>Zobacz także

- [Interceptory](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md)
