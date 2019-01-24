---
title: Instalowanie usługi kolejkowania komunikatów (MSMQ)
ms.date: 03/30/2017
ms.assetid: 7ddcd497-3e04-427e-bc04-3610ad98b01e
ms.openlocfilehash: 2aae92ba6e373af2d8bc9cff0b4c9d317ba10136
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54588028"
---
# <a name="installing-message-queuing-msmq"></a>Instalowanie usługi kolejkowania komunikatów (MSMQ)
Poniższe procedury pokazują, jak zainstalować usłudze MSMQ 4.0 i wersji 3.0.  
  
> [!NOTE]
>  Komunikatów usługi kolejkowania 4.0 nie jest dostępna w [!INCLUDE[wxp](../../../../includes/wxp-md.md)] i [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].  
  
#### <a name="to-install-message-queuing-40-on-windows-server-2008-or-windows-server-2008-r2"></a>Aby zainstalować usłudze MSMQ 4.0 w systemie Windows Server 2008 lub Windows Server 2008 R2  
  
1.  W Menedżerze serwera kliknij **funkcji**.  
  
2.  W okienku po prawej stronie w obszarze **Podsumowanie funkcji**, kliknij przycisk **Dodaj funkcje**.  
  
3.  W oknie wynikowy rozwiń **usługi kolejkowania komunikatów**.  
  
4.  Rozwiń **usługi kolejkowania komunikatów**.  
  
5.  Kliknij przycisk **integracji z usługami katalogu** (komputery przyłączone do domeny), a następnie kliknij przycisk **obsługi protokołu HTTP**.  
  
6.  Kliknij przycisk **dalej**, następnie kliknij przycisk **zainstalować**.  
  
#### <a name="to-install-message-queuing-40-on-windows-7-or-windows-vista"></a>Aby zainstalować usłudze MSMQ 4.0 na Windows 7 lub Windows Vista  
  
1.  Otwórz **Panel sterowania**.  
  
2.  Kliknij przycisk **programy** a następnie w obszarze **programy i funkcje**, kliknij przycisk **Włącz lub wyłącz funkcje Windows**.  
  
3.  Rozwiń węzeł serwera Microsoft kolejki komunikatów (MSMQ), rozwiń Microsoft kolejki komunikatów (MSMQ) Server Core, a następnie zaznacz pola wyboru dla następujących funkcji usługi kolejkowania komunikatów do zainstalowania:  
  
    -   Usługa MSMQ domeny integracji usług Active Directory (na komputery przyłączone do domeny).  
  
    -   Obsługa protokołu HTTP usługi MSMQ.  
  
4.  Kliknij przycisk **OK**.  
  
5.  Jeśli zostanie wyświetlony monit o ponowne uruchomienie komputera, kliknij przycisk **OK** do ukończenia instalacji.  
  
#### <a name="to-install-message-queuing-30-on-windows-xp-and-windows-server-2003"></a>Aby zainstalować 3.0 usługi kolejkowania komunikatów na Windows XP i Windows Server 2003  
  
1.  Otwórz **Panel sterowania**.  
  
2.  Kliknij przycisk **Dodaj/Usuń programy** a następnie kliknij przycisk **dodać składniki Windows**.  
  
3.  Wybierz usługę kolejkowania komunikatów, a następnie kliknij przycisk **szczegóły**.  
  
    > [!NOTE]
    >  Jeśli używasz [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], wybierz serwer aplikacji na dostęp do usługi kolejkowania komunikatów.  
  
4.  Upewnij się, że opcja, obsługa protokołu HTTP w usłudze MSMQ jest wybierane na stronie szczegółów.  
  
5.  Kliknij przycisk **OK** zamknąć stronę szczegółów, a następnie kliknij przycisk **dalej**. Ukończ instalację.  
  
6.  Jeśli zostanie wyświetlony monit o ponowne uruchomienie komputera, kliknij przycisk **OK** do ukończenia instalacji.  
  
## <a name="see-also"></a>Zobacz także
- [Instrukcje dotyczące konfiguracji](../../../../docs/framework/wcf/samples/set-up-instructions.md)
