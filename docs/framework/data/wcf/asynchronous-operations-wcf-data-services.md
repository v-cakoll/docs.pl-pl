---
title: Operacje asynchroniczne (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, asynchronous operations
- asynchronous operations [WCF Data Services]
- WCF Data Services, client library
ms.assetid: 679644c7-e3fc-422c-b14a-b44b683900d0
ms.openlocfilehash: ef41b458a3f5b977eaaff523413c1a8d3b1982a3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59126646"
---
# <a name="asynchronous-operations-wcf-data-services"></a>Operacje asynchroniczne (WCF Data Services)
Aplikacje sieci Web musi obsługiwać większych opóźnień między klientem i serwerem niż aplikacji działających w sieciach wewnętrznych. Aby zoptymalizować wydajność i środowisko użytkownika aplikacji, firma Microsoft zaleca używanie metod asynchronicznych z <xref:System.Data.Services.Client.DataServiceContext> i <xref:System.Data.Services.Client.DataServiceQuery%601> klasy podczas uzyskiwania dostępu do [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] serwerów w sieci Web.  
  
 Mimo że [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] procesu serwery HTTP asynchronicznie żąda niektóre metody [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] biblioteki klienckie są synchroniczne i poczekaj na zakończenie wymianę całego żądań i odpowiedzi przed kontynuowaniem wykonywania. Metody asynchroniczne [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] biblioteki klienckie nie Czekaj na zakończenie tej wymiany i umożliwia aplikacji do obsługi interfejsu użytkownika dynamiczne w tym samym czasie.  
  
 Można wykonać operacji asynchronicznych za pomocą pary metod na <xref:System.Data.Services.Client.DataServiceContext> i <xref:System.Data.Services.Client.DataServiceQuery%601> klas, które zaczyna się *rozpocząć* i *zakończenia* odpowiednio. *Rozpocząć* metody rejestrowania delegata, który wywołuje usługę, po zakończeniu operacji. *Zakończenia* metody powinna być wywoływana dla delegata, która jest zarejestrowana w celu obsługi wywołania zwrotnego z zakończone operacje. Gdy wywołujesz *zakończenia* metodę, aby ukończyć operację asynchroniczną, należy to zrobić z tej samej <xref:System.Data.Services.Client.DataServiceQuery%601> lub <xref:System.Data.Services.Client.DataServiceContext> wystąpienie, którego użyto do rozpoczęcia operacji. Każdy *rozpocząć* metoda przyjmuje `state` parametr, który można przekazać obiekt stanu do wywołania zwrotnego. Obiekt stanu jest pobierana z <xref:System.IAsyncResult> który jest dostarczany za pomocą wywołania zwrotnego i służy do wywoływania odpowiednich *zakończenia* metodę, aby ukończyć operację asynchroniczną. Na przykład, jeśli użytkownik poda <xref:System.Data.Services.Client.DataServiceQuery%601> wystąpienia jako `state` parametru podczas wywoływania <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> metody wystąpienia, w taki sam <xref:System.Data.Services.Client.DataServiceQuery%601> wystąpienia jest zwracany przez <xref:System.IAsyncResult>. To wystąpienie <xref:System.Data.Services.Client.DataServiceQuery%601> jest następnie używany do wywoływania <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> metodę, aby ukończyć operację zapytania. Aby uzyskać więcej informacji, zobacz [jak: Wykonywanie asynchronicznych zapytań usługi danych](../../../../docs/framework/data/wcf/how-to-execute-asynchronous-data-service-queries-wcf-data-services.md).  
  
> [!NOTE]
>  Tylko operacje asynchroniczne są obsługiwane przez bibliotek klienckich, które znajdują się w programie .NET Framework dla programu Silverlight. Aby uzyskać więcej informacji, zobacz [usług danych WCF (Silverlight)](https://go.microsoft.com/fwlink/?LinkID=143149).  
  
 Biblioteki klienta .NET Framework obsługuje następujące operacje asynchroniczne:  
  
|Operacja|Metody|  
|---------------|-------------|  
|Wykonywanie <xref:System.Data.Services.Client.DataServiceQuery%601>.|-   <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A>|  
|Wykonywanie zapytania z <xref:System.Data.Services.Client.DataServiceContext>.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>|  
|Wykonywanie zapytania usługi batch z <xref:System.Data.Services.Client.DataServiceContext>.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecuteBatch%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecuteBatch%2A>|  
|Trwa ładowanie powiązanych jednostek do <xref:System.Data.Services.Client.DataServiceContext>.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginLoadProperty%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndLoadProperty%2A>|  
|Zapisywanie zmian w obiektach <xref:System.Data.Services.Client.DataServiceContext>|-   <xref:System.Data.Services.Client.DataServiceContext.BeginSaveChanges%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndSaveChanges%2A>|  
  
## <a name="threading-considerations-for-asynchronous-operations"></a>Wątkowość uwagi dotyczące operacji asynchronicznych  
 W przypadku aplikacji wielowątkowych, delegat, który jest zarejestrowany jako wywołanie zwrotne dla operacji asynchronicznej nie jest zawsze wywoływany w tym samym wątku, który został użyty do wywołania *rozpocząć* metody, która tworzy wstępne żądanie. W aplikacji, gdy wywołanie zwrotne musi być wywoływany w określonym wątku, musisz jawnie zarządzać wykonywania *zakończenia* metody, która obsługuje odpowiedzi, do żądanego wątku. Na przykład w aplikacji Windows Presentation Foundation WPF i aplikacji opartych na technologii Silverlight odpowiedzi musi być organizowany powrotem do wątku interfejsu użytkownika przy użyciu <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> metody <xref:System.Windows.Threading.Dispatcher> obiektu. Aby uzyskać więcej informacji, zobacz [zapytań usługi danych (WCF Data Services/Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc903932(v=vs.95)).  
  
## <a name="see-also"></a>Zobacz także

- [Biblioteka klienta usług danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
