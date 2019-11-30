---
title: Operacje asynchroniczne (Usługi danych programu WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, asynchronous operations
- asynchronous operations [WCF Data Services]
- WCF Data Services, client library
ms.assetid: 679644c7-e3fc-422c-b14a-b44b683900d0
ms.openlocfilehash: 3e8d3ec46362751ea8bbfe5120e35a050d0e7a6c
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569362"
---
# <a name="asynchronous-operations-wcf-data-services"></a>Operacje asynchroniczne (Usługi danych programu WCF)
Aplikacje sieci Web muszą obsługiwać wyższe opóźnienia między klientem a serwerem niż aplikacje, które działają w sieciach wewnętrznych. Aby zoptymalizować wydajność i środowisko użytkownika aplikacji, zalecamy używanie asynchronicznych metod klas <xref:System.Data.Services.Client.DataServiceContext> i <xref:System.Data.Services.Client.DataServiceQuery%601> podczas uzyskiwania dostępu do serwerów Usługi danych programu WCF za pośrednictwem sieci Web.  
  
 Mimo że serwery Usługi danych programu WCF przetwarzają żądania HTTP asynchronicznie, niektóre metody bibliotek klienckich Usługi danych programu WCF są synchroniczne i oczekują na ukończenie całego wymiany odpowiedzi na żądanie przed kontynuowaniem wykonywania. Metody asynchroniczne bibliotek klienta Usługi danych programu WCF nie czekają na ukończenie tej wymiany i mogą umożliwić aplikacji obsługę interfejsu użytkownika w międzyczasie.  
  
 Operacje asynchroniczne można wykonywać przy użyciu pary metod na <xref:System.Data.Services.Client.DataServiceContext> i <xref:System.Data.Services.Client.DataServiceQuery%601> klas, które zaczynają *się od początku* i na *końcu* . Metody *BEGIN* rejestrują delegata, który wywołuje Usługa po zakończeniu operacji. Metody *End* powinny być wywoływane w delegatze, który jest zarejestrowany do obsługi wywołania zwrotnego z ukończonych operacji. Gdy wywoływana jest metoda *End* w celu ukończenia operacji asynchronicznej, należy to zrobić z tego samego <xref:System.Data.Services.Client.DataServiceQuery%601> lub wystąpienia <xref:System.Data.Services.Client.DataServiceContext>, które zostało użyte do rozpoczęcia operacji. Każda metoda *BEGIN* przyjmuje parametr `state`, który może przekazać obiekt stanu do wywołania zwrotnego. Ten obiekt stanu jest pobierany z <xref:System.IAsyncResult>, który jest dostarczany z wywołaniem zwrotnym i jest używany do wywołania odpowiedniej metody *End* w celu ukończenia operacji asynchronicznej. Na przykład, jeśli podasz wystąpienie <xref:System.Data.Services.Client.DataServiceQuery%601> jako parametr `state` po wywołaniu metody <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> w wystąpieniu, to to samo wystąpienie <xref:System.Data.Services.Client.DataServiceQuery%601> jest zwracane przez <xref:System.IAsyncResult>. To wystąpienie <xref:System.Data.Services.Client.DataServiceQuery%601> jest następnie używane do wywołania metody <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> w celu ukończenia operacji zapytania. Aby uzyskać więcej informacji, zobacz [jak: wykonywanie zapytań asynchronicznych usługi danych](how-to-execute-asynchronous-data-service-queries-wcf-data-services.md).  
  
> [!NOTE]
> Tylko operacje asynchroniczne są obsługiwane przez biblioteki klienckie udostępniane w .NET Framework dla programu Silverlight. Aby uzyskać więcej informacji, zobacz [usługi danych programu WCF (Silverlight)](https://go.microsoft.com/fwlink/?LinkID=143149).  
  
 Biblioteki klienta .NET Framework obsługują następujące operacje asynchroniczne:  
  
|Operacja|Metody|  
|---------------|-------------|  
|Wykonywanie <xref:System.Data.Services.Client.DataServiceQuery%601>.|-   <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A>|  
|Wykonywanie zapytania z <xref:System.Data.Services.Client.DataServiceContext>.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>|  
|Wykonywanie zapytania wsadowego z <xref:System.Data.Services.Client.DataServiceContext>.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecuteBatch%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecuteBatch%2A>|  
|Ładowanie powiązanej jednostki do <xref:System.Data.Services.Client.DataServiceContext>.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginLoadProperty%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndLoadProperty%2A>|  
|Zapisywanie zmian w obiektach w <xref:System.Data.Services.Client.DataServiceContext>|-   <xref:System.Data.Services.Client.DataServiceContext.BeginSaveChanges%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndSaveChanges%2A>|  
  
## <a name="threading-considerations-for-asynchronous-operations"></a>Zagadnienia dotyczące wątkowania operacji asynchronicznych  
 W aplikacji wielowątkowej delegat, który jest zarejestrowany jako wywołanie zwrotne dla operacji asynchronicznej, nie jest koniecznie wywoływany w tym samym wątku, który został użyty do wywołania metody *BEGIN* , co powoduje utworzenie początkowego żądania. W aplikacji, w której wywołanie zwrotne musi być wywoływane w określonym wątku, należy jawnie zorganizować wykonywanie metody *End* , która obsługuje odpowiedź, do żądanego wątku. Na przykład w aplikacjach opartych na Windows Presentation Foundation (WPF) i aplikacjach opartych na technologii Silverlight odpowiedź musi być organizowana z powrotem do wątku interfejsu użytkownika przy użyciu metody <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> na obiekcie <xref:System.Windows.Threading.Dispatcher>. Aby uzyskać więcej informacji, zobacz [wykonywanie zapytań dotyczących usługi danych (usługi danych programu WCF/Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc903932(v=vs.95)).  
  
## <a name="see-also"></a>Zobacz także

- [Biblioteka klienta usług danych WCF](wcf-data-services-client-library.md)
