---
title: Operacje asynchroniczne (Usługi danych programu WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, asynchronous operations
- asynchronous operations [WCF Data Services]
- WCF Data Services, client library
ms.assetid: 679644c7-e3fc-422c-b14a-b44b683900d0
ms.openlocfilehash: bb62b9ad214e5e268c3905df486f5914437b36d3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780528"
---
# <a name="asynchronous-operations-wcf-data-services"></a>Operacje asynchroniczne (Usługi danych programu WCF)
Aplikacje sieci Web muszą obsługiwać wyższe opóźnienia między klientem a serwerem niż aplikacje, które działają w sieciach wewnętrznych. Aby zoptymalizować wydajność i środowisko użytkownika aplikacji, zalecamy użycie asynchronicznych metod <xref:System.Data.Services.Client.DataServiceContext> klas i <xref:System.Data.Services.Client.DataServiceQuery%601> podczas uzyskiwania dostępu do [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] serwerów za pośrednictwem sieci Web.  
  
 Mimo że [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] serwery przetwarzają żądania HTTP asynchronicznie, niektóre metody bibliotek klienckich są synchroniczne i oczekują na ukończenie całego wymiany odpowiedzi na żądanie przed kontynuowaniem wykonywania. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Metody asynchroniczne bibliotek [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klienta nie oczekują na ukończenie tej wymiany i mogą zezwalać aplikacji na w międzyczasie obsługiwać interfejs użytkownika, który odpowiada.  
  
 Operacje asynchroniczne można wykonywać przy użyciu pary metod <xref:System.Data.Services.Client.DataServiceContext> w i <xref:System.Data.Services.Client.DataServiceQuery%601> klas, które zaczynają się odpowiednio *od początku* i *końca* . Metody *BEGIN* rejestrują delegata, który wywołuje Usługa po zakończeniu operacji. Metody *End* powinny być wywoływane w delegatze, który jest zarejestrowany do obsługi wywołania zwrotnego z ukończonych operacji. Gdy wywoływana jest metoda *End* w celu ukończenia operacji asynchronicznej, należy to zrobić z tego samego <xref:System.Data.Services.Client.DataServiceQuery%601> lub <xref:System.Data.Services.Client.DataServiceContext> wystąpienia, które zostało użyte do rozpoczęcia operacji. Każda metoda *BEGIN* przyjmuje `state` parametr, który może przekazać obiekt stanu do wywołania zwrotnego. Ten obiekt stanu jest pobierany z <xref:System.IAsyncResult> , który jest dostarczany z wywołaniem zwrotnym i jest używany do wywołania odpowiedniej metody *End* w celu ukończenia operacji asynchronicznej. Na przykład, gdy podasz <xref:System.Data.Services.Client.DataServiceQuery%601> wystąpienie `state` jako <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> parametr po wywołaniu metody w wystąpieniu <xref:System.IAsyncResult>, to to samo <xref:System.Data.Services.Client.DataServiceQuery%601> wystąpienie jest zwracane przez. To wystąpienie <xref:System.Data.Services.Client.DataServiceQuery%601> jest następnie używane do <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> wywołania metody w celu ukończenia operacji zapytania. Aby uzyskać więcej informacji, zobacz [jak: Wykonaj zapytania](how-to-execute-asynchronous-data-service-queries-wcf-data-services.md)asynchronicznej usługi danych.  
  
> [!NOTE]
> Tylko operacje asynchroniczne są obsługiwane przez biblioteki klienckie udostępniane w .NET Framework dla programu Silverlight. Aby uzyskać więcej informacji, zobacz [usługi danych programu WCF (Silverlight)](https://go.microsoft.com/fwlink/?LinkID=143149).  
  
 Biblioteki klienta .NET Framework obsługują następujące operacje asynchroniczne:  
  
|Operacja|Metody|  
|---------------|-------------|  
|<xref:System.Data.Services.Client.DataServiceQuery%601>Wykonywanie.|-   <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A>|  
|Wykonywanie zapytania z <xref:System.Data.Services.Client.DataServiceContext>.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>|  
|Wykonywanie zapytania wsadowego z <xref:System.Data.Services.Client.DataServiceContext>.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecuteBatch%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecuteBatch%2A>|  
|Ładowanie jednostki powiązanej do <xref:System.Data.Services.Client.DataServiceContext>.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginLoadProperty%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndLoadProperty%2A>|  
|Zapisywanie zmian w obiektach w<xref:System.Data.Services.Client.DataServiceContext>|-   <xref:System.Data.Services.Client.DataServiceContext.BeginSaveChanges%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndSaveChanges%2A>|  
  
## <a name="threading-considerations-for-asynchronous-operations"></a>Zagadnienia dotyczące wątkowania operacji asynchronicznych  
 W aplikacji wielowątkowej delegat, który jest zarejestrowany jako wywołanie zwrotne dla operacji asynchronicznej, nie jest koniecznie wywoływany w tym samym wątku, który został użyty do wywołania metody *BEGIN* , co powoduje utworzenie początkowego żądania. W aplikacji, w której wywołanie zwrotne musi być wywoływane w określonym wątku, należy jawnie zorganizować wykonywanie metody *End* , która obsługuje odpowiedź, do żądanego wątku. Na przykład w przypadku aplikacji opartych na Windows Presentation Foundation (WPF) i aplikacji opartych na technologii Silverlight odpowiedź musi być organizowana z powrotem do wątku interfejsu użytkownika przy <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> użyciu metody <xref:System.Windows.Threading.Dispatcher> dla obiektu. Aby uzyskać więcej informacji, zobacz [wykonywanie zapytań dotyczących usługi danych (usługi danych programu WCF/Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc903932(v=vs.95)).  
  
## <a name="see-also"></a>Zobacz także

- [Biblioteka klienta usług danych WCF](wcf-data-services-client-library.md)
