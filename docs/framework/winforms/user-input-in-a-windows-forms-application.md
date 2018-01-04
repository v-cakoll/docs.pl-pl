---
title: "Wprowadzanie przez użytkownika w aplikacjach Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Windows Forms, user input
ms.assetid: 9d61fa96-70f7-4754-885a-49a4a6316bdb
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 60135c09f63bd98f753e151c515938cbf13e70ee
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="user-input-in-a-windows-forms-application"></a>Wprowadzanie przez użytkownika w aplikacjach Windows Forms
W formularzach systemu Windows dane wejściowe użytkownika są wysyłane do aplikacji w formie komunikatów systemu Windows. Szereg metod, które można przetworzyć tych wiadomości w aplikacji, formularz i sterować poziomem. Podczas tych metod odbieranie komunikatów myszy i klawiatury, zgłoś one zdarzenia, które są obsługiwane w celu uzyskania informacji na temat myszy lub klawiatury danych wejściowych. W wielu przypadkach aplikacji formularzy systemu Windows będzie można przetwarzać wszystkie dane wejściowe użytkownika za pomocą obsługi tych zdarzeń. W pozostałych przypadkach aplikacji może być konieczne zastąpienie jednej z metod, które przetwarzają wiadomości, aby przechwycić danego komunikatu, zanim aplikacja, formularz lub formant otrzymuje.  
  
## <a name="mouse-and-keyboard-events"></a>Zdarzeń myszy i klawiatury  
 Wszystkie formanty formularzy systemu Windows, dziedziczą zestaw zdarzeń związanych z myszy i klawiatury. Na przykład może obsłużyć formantu <xref:System.Windows.Forms.Control.KeyPress> może obsłużyć zdarzenia w celu określenia kod znaku klucza, który został naciśnięty lub formantu <xref:System.Windows.Forms.Control.MouseClick> zdarzenia w celu określenia lokalizacji myszy, kliknij przycisk. Aby uzyskać więcej informacji na temat zdarzeń myszy i klawiatury, zobacz [zdarzenia klawiatury przy użyciu](../../../docs/framework/winforms/using-keyboard-events.md) i [zdarzenia myszy w formularzach systemu Windows](../../../docs/framework/winforms/mouse-events-in-windows-forms.md).  
  
## <a name="methods-that-process-user-input-messages"></a>Metody, które przetwarzają komunikaty wejściowe użytkownika  
 Formularzy i kontrolek mają dostęp do <xref:System.Windows.Forms.IMessageFilter> interfejsu i zestaw możliwym do zastąpienia metod, które przetwarzają komunikatów systemu Windows w różnych punktach kolejki wiadomości. Te metody mają <xref:System.Windows.Forms.Message> parametr, który hermetyzuje szczegółów niskiego poziomu komunikatów systemu Windows. Można zaimplementować lub zastępować te metody, aby zbadać wiadomość, a następnie korzystać z wiadomości lub przekazuje dalej odbiorców w kolejce wiadomości. W poniższej tabeli przedstawiono metody, które przetwarzają wszystkie komunikaty systemu Windows w formularzach systemu Windows.  
  
|Metoda|Uwagi|  
|------------|-----------|  
|<xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A>|Ta metoda przechwytuje wiadomości w kolejce (znanej także jako oczekujących na opublikowanie) systemu Windows na poziomie aplikacji.|  
|<xref:System.Windows.Forms.Control.PreProcessMessage%2A>|Ta metoda przechwytuje komunikaty systemu Windows na poziomie formularza i kontroli, zanim zostaną one przetworzone.|  
|<xref:System.Windows.Forms.Control.WndProc%2A>|Ta metoda przetwarza komunikatów systemu Windows na poziomie formularza i kontroli.|  
|<xref:System.Windows.Forms.Control.DefWndProc%2A>|Ta metoda przetwarza domyślne komunikaty systemu Windows na poziomie formularza i kontroli. Zapewnia to funkcjonalność minimalnego okna.|  
|<xref:System.Windows.Forms.Control.OnNotifyMessage%2A>|Ta metoda przechwytuje wiadomości na poziomie formularza i kontroli po zostały przetworzone. <xref:System.Windows.Forms.ControlStyles.EnableNotifyMessage> Bit stylu musi być ustawiona dla tej metody do wywołania.|  
  
 Klawiatura i mysz wiadomości również są przetwarzane przez dodatkowy zestaw nadpisywalnych metod, które są specyficzne dla tych typów wiadomości. Aby uzyskać więcej informacji, zobacz [sposób działania wejście klawiatury](../../../docs/framework/winforms/how-keyboard-input-works.md) i [sposób działania wejście myszy w formularzach systemu Windows](../../../docs/framework/winforms/how-mouse-input-works-in-windows-forms.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Dane użytkownika w formularzach Windows Forms](../../../docs/framework/winforms/user-input-in-windows-forms.md)  
 [Wprowadzanie z klawiatury w aplikacjach Windows Forms](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)  
 [Wprowadzanie za pomocą myszy w aplikacjach Windows Forms](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
