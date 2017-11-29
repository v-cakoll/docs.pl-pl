---
title: "Porady: rejestrowanie informacji o usługach"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "17"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: 612b983f53f147102ddf7bab03d4ec6783dc4026
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-log-information-about-services"></a>Porady: rejestrowanie informacji o usługach
Domyślnie wszystkie projekty usługi systemu Windows mają możliwość interakcji z dziennika zdarzeń aplikacji i zapisywać do niego informacje i wyjątki. Możesz użyć <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> Właściwość wskazująca, czy ma tę funkcję w aplikacji. Domyślnie rejestrowanie jest włączone dla żadnej usługi utworzone przy użyciu szablonu projektu usług systemu Windows. Można użyć statycznej formę <xref:System.Diagnostics.EventLog> klasa umożliwiająca zapisanie informacji o usłudze dziennika bez tworzenia wystąpienia <xref:System.Diagnostics.EventLog> składnika lub ręcznie zarejestrować źródło.  
  
 Instalator usługi automatycznie rejestruje każdej usługi w projekcie jako prawidłowe źródło zdarzenia z dziennika aplikacji na komputerze, którym jest zainstalowana usługa, gdy jest włączone rejestrowanie. Rejestruje informacje za każdym razem, usługa jest uruchomiona, zatrzymana, wstrzymana, wznowione, zainstalowany lub odinstalowany. Rejestruje wszystkie błędy występujące. Nie ma potrzeby pisania kodu na zapisywanie wpisów w dzienniku, używając domyślnego zachowania; Usługa obsługuje to dla Ciebie automatycznie.  
  
 Jeśli chcesz zapisać do dziennika zdarzeń niż dziennik aplikacji, musisz ustawić <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> właściwości `false`, tworzyć własne niestandardowe dziennika zdarzeń w kodzie usługi i zarejestrować usługi jako prawidłowe źródło pozycji dla tego dziennika. Następnie należy napisać kodu do rejestrowania wpisów w dzienniku zawsze, gdy interesujący Cię w akcji.  
  
> [!NOTE]
>  Jeśli używasz niestandardowego dziennika zdarzeń i konfigurowania aplikacji usługi do zapisu, nie musi podejmować dostępu do dziennika zdarzeń przed skonfigurowaniem usługi <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> właściwości w kodzie. Dziennik zdarzeń musi wartość tej właściwości można zarejestrować usługi jako prawidłowe źródło zdarzeń.  
  
### <a name="to-enable-default-event-logging-for-your-service"></a>Aby włączyć rejestrowanie zdarzeń domyślne usługi  
  
-   Ustaw <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> właściwość składnikowi `true`.  
  
    > [!NOTE]
    >  Domyślnie wartość tej właściwości to `true`. Nie trzeba ustawić to jawnie, chyba że tworzysz złożonych przetwarzania, takich jak oceniania warunku, a następnie ustawić <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> właściwości na podstawie wyniku tego warunku.  
  
### <a name="to-disable-event-logging-for-your-service"></a>Aby wyłączyć rejestrowanie zdarzeń dla usługi  
  
-   Ustaw <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> właściwość składnikowi `false`.  
  
     [!code-csharp[VbRadconService#17](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#17)]
     [!code-vb[VbRadconService#17](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#17)]  
  
### <a name="to-set-up-logging-to-a-custom-log"></a>Aby skonfigurować rejestrowanie do dziennika niestandardowego  
  
1.  Ustaw <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> właściwości `false`.  
  
    > [!NOTE]
    >  Należy ustawić <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> na wartość false, aby można było używać dziennik niestandardowy.  
  
2.  Konfigurowanie wystąpienia <xref:System.Diagnostics.EventLog> składnika aplikacji usługi systemu Windows.  
  
3.  Utworzyć dziennika niestandardowego przez wywołanie metody <xref:System.Diagnostics.EventLog.CreateEventSource%2A> — metoda i określania ciągu źródła i nazwa dziennika plik chcesz utworzyć.  
  
4.  Ustaw <xref:System.Diagnostics.EventLog.Source%2A> właściwość <xref:System.Diagnostics.EventLog> wystąpienie składnika ciąg źródłowy został utworzony w kroku 3.  
  
5.  Zapis wpisy uzyskując dostęp do <xref:System.Diagnostics.EventLog.WriteEntry%2A> metoda <xref:System.Diagnostics.EventLog> wystąpienia składnika.  
  
     Poniższy kod przedstawia sposób rejestrowania w dzienniku niestandardowe.  
  
    > [!NOTE]
    >  W tym przykładzie kodu wystąpienia <xref:System.Diagnostics.EventLog> nosi nazwę składnika `eventLog1` (`EventLog1` w języku Visual Basic). Jeśli wystąpienie zostało utworzone z inną nazwą w kroku 2, należy odpowiednio zmienić kod.  
  
     [!code-csharp[VbRadconService#14](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#14)]
     [!code-vb[VbRadconService#14](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#14)]  
    [!code-csharp[VbRadconService#15](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#15)]
    [!code-vb[VbRadconService#15](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#15)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do aplikacji usług systemu Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
