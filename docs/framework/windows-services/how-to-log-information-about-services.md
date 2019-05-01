---
title: 'Instrukcje: Rejestrowanie informacji o usługach'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AutoLog property
- services, logging information
- Windows Service applications, logging information about
- event logs, service applications
- application event logs, service applications
- logs, service applications
ms.assetid: c0d8140f-c055-4d8e-a2e0-37358a550116
author: ghogen
ms.openlocfilehash: dfcfb7370ffd59a50cf6d0b01e84e581ddc6fc52
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61914098"
---
# <a name="how-to-log-information-about-services"></a>Instrukcje: Rejestrowanie informacji o usługach
Domyślnie wszystkie projekty usługi Windows mają możliwość interakcji z dziennika zdarzeń aplikacji i w nim zapisywać informacje i wyjątki. Możesz użyć <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> właściwość wskazuje, czy ta funkcja w aplikacji. Domyślnie rejestrowanie jest włączone dla dowolnej usługi utworzonej przy użyciu szablonu projektu usługi Windows. Można użyć statycznej formy <xref:System.Diagnostics.EventLog> klasę umożliwiającą zapisanie informacji o usłudze do dziennika bez tworzenia wystąpienia <xref:System.Diagnostics.EventLog> składnika lub ręcznie zarejestrować źródła.  
  
 Instalator usługi powoduje automatyczne zarejestrowanie każdej usługi w projekcie jako poprawne źródło zdarzenia w dzienniku aplikacji na komputerze, gdzie usługa jest zainstalowana, gdy jest włączone rejestrowanie. Rejestruje informacje o każdym usługi jest uruchomiona, zatrzymana, wstrzymana, wznowione, zainstalowane lub odinstalowane. Rejestruje wszystkie błędy, które występują. Nie trzeba pisać kodu na zapisywanie wpisów do dziennika, korzystając z domyślnym zachowaniem; Usługa obsługuje to dla Ciebie automatycznie.  
  
 Jeśli chcesz zapisać do dziennika zdarzeń niż dziennik aplikacji, musisz ustawić <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> właściwości `false`, Utwórz własny niestandardowy dziennik zdarzeń w kodzie usługi i zarejestrować usługę jako poprawne źródło pozycji dla tego dziennika. Następnie należy napisać kodu do rejestrowania wpisów do dziennika zawsze wtedy, gdy akcję, którą chcesz.  
  
> [!NOTE]
>  Jeśli używasz niestandardowy dziennik zdarzeń i konfigurowanie aplikacji usługi do zapisu do nich, nie należy spróbować uzyskać dostęp w dzienniku zdarzeń przed ustawieniem usługi <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> właściwości w kodzie. W dzienniku zdarzeń musi wartość tej właściwości można zarejestrować usługi jako poprawne źródło zdarzeń.  
  
### <a name="to-enable-default-event-logging-for-your-service"></a>Aby włączyć rejestrowanie zdarzeń domyślnego dla usługi  
  
- Ustaw <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> właściwości składnika do `true`.  
  
    > [!NOTE]
    >  Domyślnie wartość tej właściwości to `true`. Nie musisz ustawić to jawnie, chyba że tworzysz bardziej złożonych przetwarzania, takich jak ocena warunku, a następnie ustawiając <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> właściwości na podstawie wyniku tego warunku.  
  
### <a name="to-disable-event-logging-for-your-service"></a>Aby wyłączyć rejestrowanie zdarzeń dla usługi  
  
- Ustaw <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> właściwości składnika do `false`.  
  
     [!code-csharp[VbRadconService#17](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#17)]
     [!code-vb[VbRadconService#17](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#17)]  
  
### <a name="to-set-up-logging-to-a-custom-log"></a>Aby skonfigurować rejestrowanie do dziennika niestandardowego  
  
1. Ustaw <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> właściwość `false`.  
  
    > [!NOTE]
    >  Należy ustawić <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> na wartość false, aby można było używać dzienników niestandardowych.  
  
2. Konfigurowanie wystąpienia <xref:System.Diagnostics.EventLog> składnika w aplikacji usługi Windows.  
  
3. Utworzyć dziennika niestandardowego przez wywołanie metody <xref:System.Diagnostics.EventLog.CreateEventSource%2A> metody i określając ciąg źródłowy i nazwę dziennika pliku, dla którego ma zostać utworzony.  
  
4. Ustaw <xref:System.Diagnostics.EventLog.Source%2A> właściwość <xref:System.Diagnostics.EventLog> wystąpienie składnika ciąg źródłowy został utworzony w kroku 3.  
  
5. Zapis wpisy, uzyskując dostęp do <xref:System.Diagnostics.EventLog.WriteEntry%2A> metody <xref:System.Diagnostics.EventLog> wystąpienia składnika.  
  
     Poniższy kod przedstawia sposób konfigurowania rejestrowania dzienników niestandardowych.  
  
    > [!NOTE]
    >  W tym przykładzie kodu wystąpienie <xref:System.Diagnostics.EventLog> nosi nazwę składnika `eventLog1` (`EventLog1` w języku Visual Basic). Jeśli utworzono wystąpienie z inną nazwą w kroku 2, należy odpowiednio zmienić kod.  
  
     [!code-csharp[VbRadconService#14](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#14)]
     [!code-vb[VbRadconService#14](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#14)]  
    [!code-csharp[VbRadconService#15](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#15)]
    [!code-vb[VbRadconService#15](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#15)]  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do aplikacji usług systemu Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
