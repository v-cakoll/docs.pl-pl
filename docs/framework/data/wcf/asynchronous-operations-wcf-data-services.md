---
title: "Operacje asynchroniczne (usługi danych WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, asynchronous operations
- asynchronous operations [WCF Data Services]
- WCF Data Services, client library
ms.assetid: 679644c7-e3fc-422c-b14a-b44b683900d0
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b79112878141fd791c2fba183d2d1fec9f1b7044
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="asynchronous-operations-wcf-data-services"></a>Operacje asynchroniczne (usługi danych WCF)
Aplikacje sieci Web musi obsłużyć większego opóźnienia między klientem a serwerem niż aplikacje, które działają w sieciach wewnętrznych. Aby zoptymalizować wydajność i środowisko użytkownika aplikacji, firma Microsoft zaleca używanie metod asynchronicznych <xref:System.Data.Services.Client.DataServiceContext> i <xref:System.Data.Services.Client.DataServiceQuery%601> klasy podczas uzyskiwania dostępu do [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] serwerami za pośrednictwem sieci Web.  
  
 Mimo że [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] proces serwerów HTTP asynchronicznie, żąda niektóre metody [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] bibliotek klienckich są synchroniczne i poczekaj na zakończenie przed kontynuowaniem wykonywania wymianę całego żądań i odpowiedzi. Metody asynchroniczne [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] bibliotek klienta nie należy czekać na zakończenie tego wymiany i umożliwia aplikacji do obsługi interfejsu użytkownika reakcji w tym samym czasie.  
  
 Asynchroniczne operacje można wykonywać za pomocą pary metod na <xref:System.Data.Services.Client.DataServiceContext> i <xref:System.Data.Services.Client.DataServiceQuery%601> klasy, które zaczynają się *rozpocząć* i *zakończenia* odpowiednio. *Rozpocząć* metody zarejestrować delegata, który wywołuje usługę po zakończeniu operacji. *Zakończenia* metody należy wywołać w elemencie delegowanym, który jest zarejestrowany do obsługi wywołania zwrotnego z ukończone operacje. Podczas wywoływania *zakończenia* metodę, aby zakończyć operację asynchroniczną, należy je z tej samej <xref:System.Data.Services.Client.DataServiceQuery%601> lub <xref:System.Data.Services.Client.DataServiceContext> wystąpienie, którego użyto do rozpoczęcia operacji. Każdy *rozpocząć* ma metodę `state` parametr, który może zostać przekazany obiekt stanu do wywołania zwrotnego. Ten obiekt stanu są pobierane z <xref:System.IAsyncResult> który jest dostarczany z wywołania zwrotnego i są używane do wywoływania odpowiadającego *zakończenia* metodę, aby ukończyć operację asynchroniczną. Na przykład, jeśli można podać <xref:System.Data.Services.Client.DataServiceQuery%601> jako `state` parametr podczas wywoływania <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> metody w wystąpieniu, takie same <xref:System.Data.Services.Client.DataServiceQuery%601> zwróconego przez wystąpienie <xref:System.IAsyncResult>. To wystąpienie <xref:System.Data.Services.Client.DataServiceQuery%601> są następnie używane do wywoływania <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> metodę, aby ukończyć operację zapytania. Aby uzyskać więcej informacji, zobacz [porady: wykonywanie asynchronicznych zapytań usługi danych](../../../../docs/framework/data/wcf/how-to-execute-asynchronous-data-service-queries-wcf-data-services.md).  
  
> [!NOTE]
>  Tylko operacje asynchroniczne są obsługiwane przez biblioteki klienta, które znajdują się w programie .NET Framework dla programu Silverlight. Aby uzyskać więcej informacji, zobacz [usługi danych WCF (platformy Silverlight)](http://go.microsoft.com/fwlink/?LinkID=143149).  
  
 Biblioteki klienta .NET Framework obsługują następujące operacje asynchroniczne:  
  
|Operacja|Metody|  
|---------------|-------------|  
|Wykonywanie <xref:System.Data.Services.Client.DataServiceQuery%601>.|-   <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A>|  
|Wykonywanie zapytania z <xref:System.Data.Services.Client.DataServiceContext>.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>|  
|Wykonywanie zapytania partii z <xref:System.Data.Services.Client.DataServiceContext>.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecuteBatch%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecuteBatch%2A>|  
|Podczas ładowania obiektu pokrewnego do <xref:System.Data.Services.Client.DataServiceContext>.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginLoadProperty%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndLoadProperty%2A>|  
|Trwa zapisywanie zmian w obiektach<xref:System.Data.Services.Client.DataServiceContext>|-   <xref:System.Data.Services.Client.DataServiceContext.BeginSaveChanges%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndSaveChanges%2A>|  
  
## <a name="threading-considerations-for-asynchronous-operations"></a>Uwagi dotyczące operacji asynchronicznych wątków  
 W aplikacji wielowątkowych delegata, który jest zarejestrowany jako wywołanie zwrotne dla operacji asynchronicznej nie jest zawsze wywoływany w tym samym wątku, którego użyto do wywołania *rozpocząć* metodę, która tworzy żądania początkowego. W aplikacji, gdzie należy wywołać metodę wywołania zwrotnego na konkretnym wątkiem, musisz jawnie kierować wykonywanie *zakończenia* metodę, która obsługuje odpowiedzi żądaną wątku. Na przykład w aplikacji Windows Presentation Foundation WPF i aplikacje Silverlight odpowiedzi musi być organizowany do wątku interfejsu użytkownika przy użyciu <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> metoda <xref:System.Windows.Threading.Dispatcher> obiektu. Aby uzyskać więcej informacji, zobacz [zapytanie usługi danych (WCF Data Services/Silverlight)](http://msdn.microsoft.com/library/3a7cdc07-c37e-4da2-b98b-c3763fd0970b).  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka klienta usług danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
