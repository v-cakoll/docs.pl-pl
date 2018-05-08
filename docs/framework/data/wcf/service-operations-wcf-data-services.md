---
title: Operacje usługi (usługi danych WCF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: 583a690a-e60f-4990-8991-d6efce069d76
ms.openlocfilehash: da8d482fbf506749f9805edcbbaad3c893ad56b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="service-operations-wcf-data-services"></a>Operacje usługi (usługi danych WCF)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Umożliwia zdefiniowanie operacji usługi w usłudze danych, aby udostępniać metod na serwerze. Podobnie jak inne zasoby usługi danych operacji usługi są opisane przez identyfikator URI. Operacje usług umożliwiają udostępnianie logiki biznesowej w usłudze danych, takich jak wdrożyć logikę sprawdzania poprawności, zastosować opartej na rolach zabezpieczeń lub do udostępnienia specjalizowany możliwości zapytań. Operacje usług są dodawane do klasy usługi danych, która pochodzi z metody <xref:System.Data.Services.DataService%601>. Podobnie jak wszystkie inne usługi zasobów danych możesz podać parametry metody operacji usługi. Na przykład następujące operacja identyfikator URI usługi (na podstawie [szybkiego startu](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) Usługa danych) przekazuje wartość `London` do `city` parametru:  
  
```  
http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'  
```  
  
 Definicja dla tej operacji usługi jest następujący:  
  
 [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperationdef)]
 [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperationdef)]  
  
 Można użyć <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> z <xref:System.Data.Services.DataService%601> bezpośredni dostęp do źródła danych, którego używa Usługa danych. Aby uzyskać więcej informacji, zobacz [porady: Definiowanie operacji usługi](../../../../docs/framework/data/wcf/how-to-define-a-service-operation-wcf-data-services.md).  
  
 Aby uzyskać informacje dotyczące wywoływanie operacji usługi z aplikacją kliencką programu .NET Framework, zobacz [wywoływanie operacji usługi](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md).  
  
## <a name="service-operation-requirements"></a>Wymagania dotyczące operacji usługi  
 Podczas definiowania operacji usługi dla usługi danych, mają zastosowanie następujące wymagania. Jeśli metoda nie spełnia te wymagania, nie będą widoczne jako operacji usługi dla usługi data.  
  
-   Operacja musi być metody wystąpienia publicznego, która jest elementem członkowskim klasy usługi danych.  
  
-   Metoda operacji może akceptować tylko parametry wejściowe. Usługa danych nie można uzyskać dostępu do danych przesyłanych w treści wiadomości.  
  
-   Jeśli parametry są określone, typ każdego parametru musi być typu pierwotnego. Wszystkie dane typu innego niż pierwotny musi serializować i przekazany parametr typu string.  
  
-   Metoda musi zwracać jedną z następujących czynności:  
  
    -   `void` (`Nothing` w języku Visual Basic)  
  
    -   <xref:System.Collections.Generic.IEnumerable%601>  
  
    -   <xref:System.Linq.IQueryable%601>  
  
    -   Typ jednostki w modelu danych, czy dane usługi ujawnia.  
  
    -   Pierwotne klasy takie jak liczba całkowita lub ciąg.  
  
-   Aby zapewnić obsługę opcje zapytania, takie jak sortowania, stronicowania i filtrowania, metody Operacja usługi powinna zwrócić <xref:System.Linq.IQueryable%601>. Do operacji usługi, które obejmują opcje zapytania będą odrzucane dla operacji, które zwraca tylko <xref:System.Collections.Generic.IEnumerable%601>.  
  
-   Aby zapewnić obsługę dostęp do powiązanych jednostek przy użyciu właściwości nawigacji, musi zwracać operacji usługi <xref:System.Linq.IQueryable%601>.  
  
-   Metoda musi być adnotowany przy `[WebGet]` lub `[WebInvoke]` atrybutu.  
  
    -   `[WebGet]` Włącza metodę można wywołać za pomocą żądania GET.  
  
    -   `[WebInvoke(Method = "POST")]` Włącza metodę można wywołać za pomocą żądania POST. Inne <xref:System.ServiceModel.Web.WebInvokeAttribute> metody nie są obsługiwane.  
  
-   Operacja usługi może być oznaczony za pomocą <xref:System.Data.Services.SingleResultAttribute> określający, czy wartość zwracaną z metody jest pojedynczy element zamiast kolekcji jednostek. Ta różnica nakazują wynikowy serializacji odpowiedzi oraz sposób, w których traversals właściwości nawigacji dodatkowe są reprezentowane w identyfikatorze URI. Na przykład używając AtomPub serializacji, wystąpienie typu pojedynczego zasobu jest reprezentowany jako element wpisu i zestaw wystąpień jako element źródła.  
  
## <a name="addressing-service-operations"></a>Adresowanie operacji usługi  
 Operacje usługi można rozwiązać przez umieszczenie nazwę metody w pierwszy segment ścieżki identyfikatora URI. Na przykład następujący identyfikator URI uzyskuje dostęp do `GetOrdersByState` operację, która zwraca <xref:System.Linq.IQueryable%601> Kolekcja `Orders` obiektów.  
  
```  
http://localhost:12345/Northwind.svc/GetOrdersByState?state='CA'&includeItems=true  
```  
  
 Podczas wywoływania operacji usługi, parametry są określane jako opcje zapytania. Poprzednia operacja usługi akceptuje zarówno parametr typu string `state` i parametrem logicznym `includeItems` wskazująca, czy do uwzględnienia powiązane `Order_Detail` obiektów w odpowiedzi.  
  
 Poniżej przedstawiono prawidłowe typy zwracane dla operacji usługi:  
  
|Prawidłowe typy zwracane|Identyfikator URI zasad|  
|------------------------|---------------|  
|`void` (`Nothing` w języku Visual Basic)<br /><br /> —lub—<br /><br /> Typy jednostek<br /><br /> —lub—<br /><br /> Typy pierwotne|Identyfikator URI musi być segment pojedynczą ścieżkę, który jest nazwa operacji usługi. Opcje zapytania nie są dozwolone.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Identyfikator URI musi być segment pojedynczą ścieżkę, który jest nazwa operacji usługi. Ponieważ nie jest typem wyniku <xref:System.Linq.IQueryable%601> typu, opcje zapytania nie są dozwolone.|  
|<xref:System.Linq.IQueryable%601>|Segmenty ścieżki zapytania oprócz ścieżkę, która jest nazwa operacji usługi są dozwolone. Dozwolone są też opcji zapytania.|  
  
 Segmenty ścieżki dodatkowe lub opcje zapytania można dodać do identyfikatora URI w zależności od zwracany typ operacji usługi. Na przykład następujący identyfikator URI uzyskuje dostęp do `GetOrdersByCity` operację, która zwraca <xref:System.Linq.IQueryable%601> Kolekcja `Orders` obiektów, uporządkowanych według `RequiredDate` w kolejności malejącej, wraz z odnośnych `Order_Details` obiektów:  
  
```  
http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc  
```  
  
## <a name="service-operations-access-control"></a>Kontrola dostępu operacji usługi  
 Widoczność obejmujących całą usługę operacji usługi jest kontrolowany przez <xref:System.Data.Services.IDataServiceConfiguration.SetServiceOperationAccessRule%2A> metody w <xref:System.Data.Services.IDataServiceConfiguration> klasy w podobny sposób że widoczność zestawu jednostek jest kontrolowany za pomocą <xref:System.Data.Services.IDataServiceConfiguration.SetEntitySetAccessRule%2A> metody. Na przykład następujący wiersz kodu w definicji usługi danych umożliwia dostęp do `CustomersByCity` operacji usługi.  
  
 [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperationconfig)]
 [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperationconfig)]  
  
> [!NOTE]
>  Jeśli operacja usługi ma zwracany typ, który został ukryty przez ograniczenie dostępu na podstawowych zestawów jednostek, operacji usługi nie będzie dostępna dla aplikacji klienckich.  
  
 Aby uzyskać więcej informacji, zobacz [porady: Definiowanie operacji usługi](../../../../docs/framework/data/wcf/how-to-define-a-service-operation-wcf-data-services.md).  
  
## <a name="raising-exceptions"></a>Występowanie wyjątków  
 Firma Microsoft zaleca użycie <xref:System.Data.Services.DataServiceException> klasy zawsze, gdy Zgłoś wyjątek podczas wykonywania usługi danych. Jest to spowodowane wie, czas wykonywania usługi danych sposób mapowania właściwości tego obiektu wyjątek poprawnie komunikat odpowiedzi HTTP. Gdy zostanie podniesiony <xref:System.Data.Services.DataServiceException> operacji usługi otoczona zwrócony wyjątek <xref:System.Reflection.TargetInvocationException>. Aby zwracać wartość base <xref:System.Data.Services.DataServiceException> bez otaczający <xref:System.Reflection.TargetInvocationException>, konieczne jest przesłonięcie <xref:System.Data.Services.DataService%601.HandleException%2A> metody w <xref:System.Data.Services.DataService%601>, Wyodrębnij <xref:System.Data.Services.DataServiceException> z <xref:System.Reflection.TargetInvocationException>i zwraca je jako błąd najwyższego poziomu, jak w poniższym przykładzie:  
  
 [!code-csharp[Astoria Northwind Service#HandleExceptions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#handleexceptions)]
 [!code-vb[Astoria Northwind Service#HandleExceptions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#handleexceptions)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interceptory](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md)
