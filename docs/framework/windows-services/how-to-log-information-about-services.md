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
ms.openlocfilehash: 3c974d5a98f8056e45899b109878e5a28ab2938e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053606"
---
# <a name="how-to-log-information-about-services"></a>Instrukcje: Rejestrowanie informacji o usługach
Domyślnie wszystkie projekty usług systemu Windows mają możliwość korzystania z dziennika zdarzeń aplikacji i zapisywania do niego informacji oraz wyjątków. Użyj właściwości, <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> aby określić, czy chcesz, aby ta funkcja w aplikacji. Domyślnie rejestrowanie jest włączone dla każdej usługi utworzonej przy użyciu szablonu projektu usługi systemu Windows. Możesz użyć statycznej formy <xref:System.Diagnostics.EventLog> klasy do zapisywania informacji o usłudze w dzienniku bez konieczności tworzenia wystąpienia <xref:System.Diagnostics.EventLog> składnika lub ręcznego rejestrowania źródła.  
  
 Instalator usługi automatycznie rejestruje każdą usługę w projekcie jako prawidłowe źródło zdarzeń w dzienniku aplikacji na komputerze, na którym zainstalowano usługę, gdy rejestrowanie jest włączone. Usługa rejestruje informacje za każdym razem, gdy usługa jest uruchomiona, zatrzymana, wstrzymana, wznowiona, zainstalowana lub odinstalowana. Rejestruje także wszystkie błędy, które wystąpiły. Nie trzeba pisać żadnego kodu w celu zapisania wpisów w dzienniku, gdy jest używane zachowanie domyślne; usługa obsługuje to automatycznie.  
  
 Jeśli chcesz zapisać w dzienniku zdarzeń innym niż dziennik aplikacji, musisz ustawić <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> właściwość na `false`, utworzyć własny dziennik zdarzeń w kodzie usług i zarejestrować usługę jako prawidłowe Źródło wpisów dla tego dziennika. Następnie należy napisać kod, aby zarejestrować wpisy w dzienniku za każdym razem, gdy akcja jest zainteresowana.  
  
> [!NOTE]
> Jeśli używasz niestandardowego dziennika zdarzeń i skonfigurujesz aplikację usługi do zapisu w niej, nie musisz próbować uzyskać dostępu do dziennika zdarzeń przed ustawieniem <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> właściwości usługi w kodzie. Dziennik zdarzeń wymaga wartości tej właściwości, aby zarejestrować usługę jako prawidłowe źródło zdarzeń.  
  
### <a name="to-enable-default-event-logging-for-your-service"></a>Aby włączyć domyślne rejestrowanie zdarzeń dla usługi  
  
- Ustaw właściwość dla składnika na `true`. <xref:System.ServiceProcess.ServiceBase.AutoLog%2A>  
  
    > [!NOTE]
    > Domyślnie wartość tej właściwości to `true`. Nie musisz jawnie ustawiać tego ustawienia, chyba że tworzysz bardziej skomplikowane przetwarzanie, takie jak szacowanie warunku, a następnie Ustawianie <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> właściwości na podstawie wyniku tego warunku.  
  
### <a name="to-disable-event-logging-for-your-service"></a>Aby wyłączyć rejestrowanie zdarzeń dla usługi  
  
- Ustaw właściwość dla składnika na `false`. <xref:System.ServiceProcess.ServiceBase.AutoLog%2A>  
  
     [!code-csharp[VbRadconService#17](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#17)]
     [!code-vb[VbRadconService#17](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#17)]  
  
### <a name="to-set-up-logging-to-a-custom-log"></a>Aby skonfigurować rejestrowanie do dziennika niestandardowego  
  
1. Ustaw <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> właściwość `false`.  
  
    > [!NOTE]
    > Aby można było <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> użyć dziennika niestandardowego, należy ustawić wartość false.  
  
2. Skonfiguruj wystąpienie <xref:System.Diagnostics.EventLog> składnika w aplikacji usługi systemu Windows.  
  
3. Utwórz dziennik niestandardowy, wywołując <xref:System.Diagnostics.EventLog.CreateEventSource%2A> metodę i określając ciąg źródłowy i nazwę pliku dziennika, który chcesz utworzyć.  
  
4. <xref:System.Diagnostics.EventLog.Source%2A> Ustaw właściwość <xref:System.Diagnostics.EventLog> w wystąpieniu składnika na ciąg źródłowy, który został utworzony w kroku 3.  
  
5. Zapisz swoje wpisy, uzyskując <xref:System.Diagnostics.EventLog.WriteEntry%2A> dostęp do metody <xref:System.Diagnostics.EventLog> w wystąpieniu składnika.  
  
     Poniższy kod pokazuje, jak skonfigurować rejestrowanie w dzienniku niestandardowym.  
  
    > [!NOTE]
    > W tym przykładzie kodu wystąpienie <xref:System.Diagnostics.EventLog> składnika nosi nazwę `eventLog1` (`EventLog1` w Visual Basic). Jeśli utworzono wystąpienie z inną nazwą w kroku 2, Zmień kod odpowiednio.  
  
     [!code-csharp[VbRadconService#14](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#14)]
     [!code-vb[VbRadconService#14](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#14)]  
    [!code-csharp[VbRadconService#15](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#15)]
    [!code-vb[VbRadconService#15](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#15)]  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do aplikacji usług systemu Windows](introduction-to-windows-service-applications.md)
