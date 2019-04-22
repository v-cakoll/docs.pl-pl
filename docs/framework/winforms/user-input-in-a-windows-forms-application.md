---
title: Wprowadzanie z klawiatury w aplikacjach formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, user input
ms.assetid: 9d61fa96-70f7-4754-885a-49a4a6316bdb
ms.openlocfilehash: 0eb39f0ecd8fcd12918b38bd77fed2ff32cac1d8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59124153"
---
# <a name="user-input-in-a-windows-forms-application"></a>Wprowadzanie z klawiatury w aplikacjach formularzy systemu Windows
W formularzach Windows Forms dane wejściowe użytkownika są wysyłane do aplikacji w postaci komunikatów Windows. Szereg możliwym do zastąpienia metody przetwarzania tych komunikatów w aplikacji formularza i kontrolować poziom. Te metody otrzymują komunikaty klawiatury i myszy, ich wywoływać zdarzenia, które mogą być obsługiwane, aby uzyskać informacje na temat myszy lub klawiatury danych wejściowych. W wielu przypadkach aplikacje Windows Forms będzie można przetworzyć wszystkie dane wejściowe użytkownika poprzez obsługi tych zdarzeń. W innych przypadkach aplikacja może być konieczne zastąpienie jednej z metod, które przetwarzają komunikaty, aby przechwycić określonej wiadomości, zanim aplikacja, formularza lub formantu odebrał.  
  
## <a name="mouse-and-keyboard-events"></a>Zdarzeń myszy i klawiatury  
 Wszystkie kontrolki Windows Forms dziedziczą zestaw zdarzeń związanych z myszy i klawiatury. Na przykład, można obsługiwać formant <xref:System.Windows.Forms.Control.KeyPress> może obsługiwać zdarzenia w celu określenia kod znaku klawisza, który został naciśnięty lub kontrolki <xref:System.Windows.Forms.Control.MouseClick> zdarzenia w celu określenia lokalizacji myszy, kliknij przycisk. Aby uzyskać więcej informacji na temat zdarzeń klawiatury oraz myszy, zobacz [zdarzenia klawiatury przy użyciu](using-keyboard-events.md) i [zdarzeń myszy w formularzach Windows Forms](mouse-events-in-windows-forms.md).  
  
## <a name="methods-that-process-user-input-messages"></a>Metody, które przetwarzają komunikatów wejściowych użytkownika  
 Formularze i formanty mają dostęp do <xref:System.Windows.Forms.IMessageFilter> interfejsu i zestaw możliwym do zastąpienia metody, które przetwarzają komunikatów Windows na różnych etapach kolejki komunikatów. Te metody wszystkie mają <xref:System.Windows.Forms.Message> parametr, który hermetyzuje szczegóły niskiego poziomu Windows komunikatów. Można zaimplementować lub zastąpienie tych metod, aby zbadać wiadomości, a następnie używanie wiadomości lub przekazuje dalej konsumenta w kolejce komunikatów. W poniższej tabeli przedstawiono metody, które przetwarzają wszystkie komunikaty Windows w formularzach Windows Forms.  
  
|Metoda|Uwagi|  
|------------|-----------|  
|<xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A>|Ta metoda przechwytuje (znany także jako opublikowane) Windows wiadomości w kolejce na poziomie aplikacji.|  
|<xref:System.Windows.Forms.Control.PreProcessMessage%2A>|Ta metoda przechwytuje Windows wiadomości na poziomie formularza i kontroli, zanim zostaną one przetworzone.|  
|<xref:System.Windows.Forms.Control.WndProc%2A>|Ta metoda przetwarza wiadomości Windows na poziomie formularza i kontroli.|  
|<xref:System.Windows.Forms.Control.DefWndProc%2A>|Ta metoda wykonuje przetwarzanie domyślne Windows wiadomości na poziomie formularza i kontroli. Zapewnia to minimalne funkcje okna.|  
|<xref:System.Windows.Forms.Control.OnNotifyMessage%2A>|Ta metoda przechwytuje wiadomości na poziomie formularza i kontroli, po ich przetworzeniu. <xref:System.Windows.Forms.ControlStyles.EnableNotifyMessage> Bit stylu musi być ustawiona dla tej metody do wywołania.|  
  
 Komunikaty klawiatury i myszy są również przetwarzane przez dodatkowego zestawu możliwym do zastąpienia metody, które są specyficzne dla tych typów komunikatów. Aby uzyskać więcej informacji, zobacz [sposób działania wejście klawiatury](how-keyboard-input-works.md) i [sposób działania wejście myszy w formularzach Windows Forms](how-mouse-input-works-in-windows-forms.md).  
  
## <a name="see-also"></a>Zobacz także

- [Dane użytkownika w formularzach Windows Forms](user-input-in-windows-forms.md)
- [Wprowadzanie z klawiatury w aplikacjach Windows Forms](keyboard-input-in-a-windows-forms-application.md)
- [Wprowadzanie za pomocą myszy w aplikacjach Windows Forms](mouse-input-in-a-windows-forms-application.md)
