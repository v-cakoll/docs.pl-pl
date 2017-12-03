---
title: "Instalowanie usługi kolejkowania komunikatów (MSMQ)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7ddcd497-3e04-427e-bc04-3610ad98b01e
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6a7ee646c2f6b20410c493ee139f08d11fc55d54
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="installing-message-queuing-msmq"></a>Instalowanie usługi kolejkowania komunikatów (MSMQ)
Poniższe procedury pokazują, jak zainstalować w usłudze MSMQ 4.0 i 3.0 usługi kolejkowania komunikatów.  
  
> [!NOTE]
>  Komunikatów usługi kolejkowania wiadomości 4.0 nie jest dostępna w [!INCLUDE[wxp](../../../../includes/wxp-md.md)] i [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].  
  
#### <a name="to-install-message-queuing-40-on-windows-server-2008-or-windows-server-2008-r2"></a>Aby zainstalować usłudze MSMQ 4.0 w systemie Windows Server 2008 lub Windows Server 2008 R2  
  
1.  W Menedżerze serwera kliknij **funkcji**.  
  
2.  W prawym okienku w obszarze **Podsumowanie funkcji**, kliknij przycisk **Dodaj funkcje**.  
  
3.  W oknie wynikowy rozwiń **usługi kolejkowania komunikatów**.  
  
4.  Rozwiń węzeł **komunikatów usługi kolejkowania wiadomości**.  
  
5.  Kliknij przycisk **integracji z usługami katalogu** (komputery przyłączone do domeny), a następnie kliknij przycisk **obsługi protokołu HTTP**.  
  
6.  Kliknij przycisk **dalej**, następnie kliknij przycisk **zainstalować**.  
  
#### <a name="to-install-message-queuing-40-on-windows-7-or-windows-vista"></a>Aby zainstalować usłudze MSMQ 4.0 w systemie Windows 7 lub Windows Vista  
  
1.  Otwórz **Panel sterowania**.  
  
2.  Kliknij przycisk **programy** , a następnie w obszarze **programy i funkcje**, kliknij przycisk **włączyć lub wyłączyć funkcje systemu Windows**.  
  
3.  Rozwiń węzeł serwera Microsoft kolejki komunikatów (MSMQ), rozwiń Microsoft kolejki komunikatów (MSMQ) Server Core, a następnie zaznacz pola wyboru dla następujące funkcje usługi kolejkowania komunikatów do zainstalowania:  
  
    -   Usługa MSMQ domeny integracji usług Active Directory (na komputerach przyłączonych do domeny).  
  
    -   Obsługa protokołu HTTP w usłudze MSMQ.  
  
4.  Kliknij przycisk **OK**.  
  
5.  Jeśli zostanie wyświetlony monit o ponowne uruchomienie komputera, kliknij przycisk **OK** do ukończenia instalacji.  
  
#### <a name="to-install-message-queuing-30-on-windows-xp-and-windows-server-2003"></a>Aby zainstalować MSMQ 3.0 w systemie Windows XP i Windows Server 2003  
  
1.  Otwórz **Panel sterowania**.  
  
2.  Kliknij przycisk **Dodaj Usuń programy** , a następnie kliknij przycisk **dodać składniki systemu Windows**.  
  
3.  Wybierz usługi kolejkowania komunikatów, a następnie kliknij przycisk **szczegóły**.  
  
    > [!NOTE]
    >  Jeśli używasz [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], wybierz serwer aplikacji można uzyskać dostępu do usługi kolejkowania komunikatów.  
  
4.  Upewnij się, że opcji wybranych na stronie Szczegóły dotyczące obsługi protokołu HTTP usługi MSMQ.  
  
5.  Kliknij przycisk **OK** zakończyć strony szczegółów, a następnie kliknij przycisk **dalej**. Ukończ instalację.  
  
6.  Jeśli zostanie wyświetlony monit o ponowne uruchomienie komputera, kliknij przycisk **OK** do ukończenia instalacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje dotyczące konfiguracji](../../../../docs/framework/wcf/samples/set-up-instructions.md)
