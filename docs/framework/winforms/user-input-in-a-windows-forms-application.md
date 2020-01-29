---
title: Dane wejściowe użytkownika w aplikacji Windows Forms
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, user input
ms.assetid: 9d61fa96-70f7-4754-885a-49a4a6316bdb
ms.openlocfilehash: 8e82276f14519c4ef54948744c93014232bdff52
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734807"
---
# <a name="user-input-in-a-windows-forms-application"></a>Wprowadzanie z klawiatury w aplikacjach formularzy systemu Windows
W Windows Forms dane wejściowe użytkownika są wysyłane do aplikacji w postaci komunikatów systemu Windows. Szereg metod, które można przetwarzać te komunikaty na poziomie aplikacji, formularza i kontroli. Gdy te metody odbierają komunikaty myszy i klawiatury, zgłaszają zdarzenia, które mogą być obsługiwane w celu uzyskania informacji na temat myszy lub klawiatury. W wielu przypadkach Windows Forms aplikacje będą mogły przetwarzać wszystkie dane wejściowe użytkownika po prostu przez obsługę tych zdarzeń. W innych przypadkach może być konieczne przesłonięcie jednej z metod przetwarzania komunikatów w celu przechwycenia konkretnego komunikatu przed odebraniem go przez aplikację, formularz lub kontrolkę.  
  
## <a name="mouse-and-keyboard-events"></a>Zdarzenia myszy i klawiatury  
 Wszystkie kontrolki Windows Forms dziedziczą zestaw zdarzeń związanych z myszą i wprowadzaniem z klawiatury. Na przykład kontrolka może obsłużyć zdarzenie <xref:System.Windows.Forms.Control.KeyPress>, aby określić kod znaku naciśniętego klawisza lub formant może obsłużyć zdarzenie <xref:System.Windows.Forms.Control.MouseClick>, aby określić lokalizację kliknięcia myszą. Aby uzyskać więcej informacji na temat zdarzeń myszy i klawiatury, zobacz [Używanie zdarzeń klawiatury](using-keyboard-events.md) i [zdarzeń myszy w Windows Forms](mouse-events-in-windows-forms.md).  
  
## <a name="methods-that-process-user-input-messages"></a>Metody przetwarzania komunikatów wejściowych użytkownika  
 Formularze i kontrolki mają dostęp do interfejsu <xref:System.Windows.Forms.IMessageFilter> i zestawu metod, które przetwarzają komunikaty systemu Windows w różnych punktach w kolejce komunikatów. Wszystkie te metody mają <xref:System.Windows.Forms.Message> parametr, który hermetyzuje szczegóły niskiego poziomu komunikatów systemu Windows. Można zaimplementować lub zastąpić te metody, aby przeanalizować komunikat, a następnie wykorzystać komunikat lub przekazać go do następnego klienta w kolejce wiadomości. W poniższej tabeli przedstawiono metody przetwarzania wszystkich komunikatów systemu Windows w Windows Forms.  
  
|Metoda|Uwagi|  
|------------|-----------|  
|<xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A>|Ta metoda przechwytuje kolejkowane (znane także jako opublikowane) komunikaty systemu Windows na poziomie aplikacji.|  
|<xref:System.Windows.Forms.Control.PreProcessMessage%2A>|Ta metoda przechwytuje komunikaty systemu Windows na poziomie formularza i kontroli przed przetworzeniem.|  
|<xref:System.Windows.Forms.Control.WndProc%2A>|Ta metoda przetwarza komunikaty systemu Windows na poziomie formularza i kontroli.|  
|<xref:System.Windows.Forms.Control.DefWndProc%2A>|Ta metoda wykonuje domyślne przetwarzanie komunikatów systemu Windows na poziomie formularza i kontroli. Zapewnia to minimalną funkcjonalność okna.|  
|<xref:System.Windows.Forms.Control.OnNotifyMessage%2A>|Ta metoda przechwytuje komunikaty na poziomie formularza i kontroli po przetworzeniu. Aby można było wywołać tę metodę, należy ustawić bit stylu <xref:System.Windows.Forms.ControlStyles.EnableNotifyMessage>.|  
  
 Komunikaty klawiatury i myszy są również przetwarzane przez dodatkowy zestaw metod, które są specyficzne dla tych typów komunikatów. Aby uzyskać więcej informacji, zobacz [jak działa wprowadzanie z klawiatury](how-keyboard-input-works.md) oraz [jak działa wprowadzanie myszą w Windows Forms](how-mouse-input-works-in-windows-forms.md).  
  
## <a name="see-also"></a>Zobacz także

- [Dane użytkownika w formularzach Windows Forms](user-input-in-windows-forms.md)
- [Wprowadzanie z klawiatury w aplikacjach Windows Forms](keyboard-input-in-a-windows-forms-application.md)
- [Wprowadzanie za pomocą myszy w aplikacjach Windows Forms](mouse-input-in-a-windows-forms-application.md)
