---
title: Operacje usługi (Usługi danych programu WCF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: 583a690a-e60f-4990-8991-d6efce069d76
ms.openlocfilehash: c254a7362c7bc28f4b38fc0189ae0ea763bc90cc
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568847"
---
# <a name="service-operations-wcf-data-services"></a>Operacje usługi (Usługi danych programu WCF)

Usługi danych programu WCF umożliwia zdefiniowanie operacji usługi w usłudze danych w celu udostępnienia metod na serwerze. Podobnie jak w przypadku innych zasobów usługi danych, operacje usługi są rozwiązywane przez identyfikatory URI. Operacje usługi umożliwiają uwidocznienie logiki biznesowej w usłudze danych, na przykład w celu zaimplementowania logiki walidacji, zastosowania zabezpieczeń opartych na rolach lub udostępnienia wyspecjalizowanych funkcji zapytań. Operacje usługi to metody dodawane do klasy usługi danych, która pochodzi od <xref:System.Data.Services.DataService%601>. Podobnie jak w przypadku wszystkich innych zasobów usługi danych, można dostarczyć parametry do metody operacji usługi. Na przykład następujący identyfikator URI operacji usługi (oparty na usłudze danych [szybkiego startu](quickstart-wcf-data-services.md) ) przekazuje wartość `London` do parametru `city`:

```http
http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'
```

Definicja tej operacji usługi jest następująca:

[!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationdef)]
[!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationdef)]

Za pomocą <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> <xref:System.Data.Services.DataService%601> można bezpośrednio uzyskać dostęp do źródła danych używanego przez usługę danych. Aby uzyskać więcej informacji, zobacz [How to: define a Service Operation](how-to-define-a-service-operation-wcf-data-services.md).

Aby uzyskać informacje na temat wywoływania operacji usługi z .NET Framework aplikacji klienckiej, zobacz [wywoływanie operacji usługi](calling-service-operations-wcf-data-services.md).

## <a name="service-operation-requirements"></a>Wymagania dotyczące operacji usługi

Podczas definiowania operacji usługi w usłudze danych obowiązują następujące wymagania. Jeśli metoda nie spełnia tych wymagań, nie zostanie udostępniona jako operacja usługi dla usługi danych.

- Operacja musi być publicznym wystąpieniem metody, która jest elementem członkowskim klasy usługi danych.

- Metoda operacji może akceptować tylko parametry wejściowe. Usługa danych nie może uzyskać dostępu do danych wysłanych w treści komunikatu.

- Jeśli parametry są zdefiniowane, typ każdego parametru musi być typem pierwotnym. Wszystkie dane typu niepierwotnego muszą być serializowane i przekazywać do parametru ciągu.

- Metoda musi zwracać jedną z następujących wartości:

  - `void` (`Nothing` w Visual Basic)

  - <xref:System.Collections.Generic.IEnumerable%601>

  - <xref:System.Linq.IQueryable%601>

  - Typ jednostki w modelu danych, który uwidacznia usługa danych.

  - Klasa pierwotna, taka jak liczba całkowita lub ciąg.

- W celu obsługi opcji zapytania, takich jak sortowanie, stronicowanie i filtrowanie, metody operacji usługi powinny zwracać <xref:System.Linq.IQueryable%601>. Żądania dotyczące operacji usługi, które obejmują opcje zapytania, są odrzucane dla operacji, które zwracają tylko <xref:System.Collections.Generic.IEnumerable%601>.

- Aby można było obsługiwać dostęp do powiązanych jednostek przy użyciu właściwości nawigacji, operacja usługi musi zwracać <xref:System.Linq.IQueryable%601>.

- Metoda musi mieć adnotację z atrybutem `[WebGet]` lub `[WebInvoke]`.

  - `[WebGet]` umożliwia wywoływanie metody przy użyciu żądania GET.

  - `[WebInvoke(Method = "POST")]` umożliwia wywoływanie metody przy użyciu żądania POST. Inne metody <xref:System.ServiceModel.Web.WebInvokeAttribute> nie są obsługiwane.

- Operacja usługi może mieć adnotację z <xref:System.Data.Services.SingleResultAttribute>, która określa, że wartość zwracana z metody jest pojedynczą jednostką, a nie kolekcją jednostek. To rozróżnienie określa powstającą serializację odpowiedzi i sposób, w jaki dodatkowe przechodzenie między właściwościami nawigacji jest reprezentowane w identyfikatorze URI. Na przykład podczas korzystania z serializacji AtomPub wystąpienie pojedynczego typu zasobu jest reprezentowane jako element wpisu i zestaw wystąpień jako element źródła danych.

## <a name="addressing-service-operations"></a>Operacje usługi Addressing

Operacje na usłudze można rozwiązać, umieszczając nazwę metody w pierwszym segmencie ścieżki identyfikatora URI. Na przykład następujący identyfikator URI uzyskuje dostęp do `GetOrdersByState` operacji, która zwraca <xref:System.Linq.IQueryable%601> kolekcję obiektów `Orders`.

```http
http://localhost:12345/Northwind.svc/GetOrdersByState?state='CA'&includeItems=true
```

Podczas wywoływania operacji usługi parametry są dostarczane jako opcje zapytania. Poprzednia operacja usługi akceptuje zarówno parametr ciągu `state`, jak i wartość logiczną `includeItems` wskazujące, czy w odpowiedzi mają być uwzględniane powiązane obiekty `Order_Detail`.

Następujące prawidłowe typy zwracane dla operacji usługi:

|Prawidłowe zwracane typy|Reguły identyfikatorów URI|
|------------------------|---------------|
|`void` (`Nothing` w Visual Basic)<br /><br /> lub<br /><br /> Typy jednostek<br /><br /> lub<br /><br /> Typy pierwotne|Identyfikator URI musi być pojedynczym segmentem ścieżki, który jest nazwą operacji usługi. Opcje zapytania są niedozwolone.|
|<xref:System.Collections.Generic.IEnumerable%601>|Identyfikator URI musi być pojedynczym segmentem ścieżki, który jest nazwą operacji usługi. Ponieważ typ wyniku nie jest typem <xref:System.Linq.IQueryable%601>, opcje zapytania są niedozwolone.|
|<xref:System.Linq.IQueryable%601>|Segmenty ścieżki zapytania oprócz ścieżki, która jest nazwą operacji usługi, są dozwolone. Opcje zapytania są również dozwolone.|

Do identyfikatora URI można dodać dodatkowe segmenty ścieżki lub opcje zapytania w zależności od typu zwracanego operacji usługi. Na przykład następujący identyfikator URI uzyskuje dostęp do `GetOrdersByCity` operacji, która zwraca <xref:System.Linq.IQueryable%601> kolekcję obiektów `Orders`, uporządkowaną według `RequiredDate` w kolejności malejącej, wraz z powiązanymi obiektami `Order_Details`:

```http
http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc
```

## <a name="service-operations-access-control"></a>Access Control operacji usługi

Widoczność operacji usługi jest kontrolowana przez metodę <xref:System.Data.Services.IDataServiceConfiguration.SetServiceOperationAccessRule%2A> w klasie <xref:System.Data.Services.IDataServiceConfiguration> tak samo, jak widoczność zestawu jednostek jest kontrolowana za pomocą metody <xref:System.Data.Services.IDataServiceConfiguration.SetEntitySetAccessRule%2A>. Na przykład poniższy wiersz kodu w definicji usługi danych umożliwia dostęp do `CustomersByCity` operacji usługi.

[!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationconfig)]
[!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationconfig)]

> [!NOTE]
> Jeśli operacja usługi ma zwracany typ, który został ukryty przez ograniczenie dostępu do zestawów jednostek źródłowych, operacja usługi nie będzie dostępna dla aplikacji klienckich.

Aby uzyskać więcej informacji, zobacz [How to: define a Service Operation](how-to-define-a-service-operation-wcf-data-services.md).

## <a name="raising-exceptions"></a>Wywoływanie wyjątków

Zalecamy używanie klasy <xref:System.Data.Services.DataServiceException> za każdym razem, gdy wystąpi wyjątek w wykonywaniu usługi danych. Wynika to z faktu, że środowisko uruchomieniowe usługi danych wie, jak poprawnie zmapować właściwości tego obiektu wyjątku do komunikatu odpowiedzi HTTP. Po podniesieniu <xref:System.Data.Services.DataServiceException> w operacji usługi zwrócony wyjątek jest opakowany w <xref:System.Reflection.TargetInvocationException>. Aby zwrócić <xref:System.Data.Services.DataServiceException> podstawowe bez otaczających <xref:System.Reflection.TargetInvocationException>, należy zastąpić metodę <xref:System.Data.Services.DataService%601.HandleException%2A> w <xref:System.Data.Services.DataService%601>, wyodrębnić <xref:System.Data.Services.DataServiceException> z <xref:System.Reflection.TargetInvocationException>i zwrócić go jako błąd najwyższego poziomu, jak w poniższym przykładzie:

[!code-csharp[Astoria Northwind Service#HandleExceptions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#handleexceptions)]
[!code-vb[Astoria Northwind Service#HandleExceptions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#handleexceptions)]

## <a name="see-also"></a>Zobacz także

- [Interceptory](interceptors-wcf-data-services.md)
