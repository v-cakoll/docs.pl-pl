---
title: Walidacja danych użytkownika w formularzach systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, validating user input
- validation [Windows Forms], Windows Forms user input
- user input [Windows Forms], validating in Windows Forms
- validating user input [Windows Forms], Windows Forms
ms.assetid: 4ec07681-1dee-4bf9-be5e-718f635a33a1
ms.openlocfilehash: adc138ad1e277f69f27f9f86fc5c3ea28a8d5cce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="user-input-validation-in-windows-forms"></a>Walidacja danych użytkownika w formularzach systemu Windows
Podczas wprowadzania danych do aplikacji, można sprawdzić poprawność danych przed aplikacja używa go. Może wymagać pewnych pól tekstowych konieczności o zerowej długości, że pole można sformatować jako numer telefonu lub inny typ danych poprawnie sformułowany lub że ciąg nie zawiera znaków niebezpieczne, które mogą służyć do naruszenia zabezpieczeń bazy danych. Formularze systemu Windows udostępnia kilka metod można sprawdzić poprawności danych wejściowych w aplikacji.  
  
## <a name="validation-with-the-maskedtextbox-control"></a>Sprawdzanie poprawności z formantem MaskedTextBox  
 Jeśli chcesz wymagać od użytkowników wprowadzania danych w formacie dobrze zdefiniowany, takich jak numer telefonu lub numer części, można to zrobić szybko i z minimalnym kodu za pomocą <xref:System.Windows.Forms.MaskedTextBox> formantu. A *maski* to ciąg składający się z znaki w języku maskowania, która określa, znaki, które można wpisać w poszczególnych pozycji w polu tekstowym. Kontrolka Wyświetla zestaw wyświetla monit dla użytkownika. Jeśli użytkownik wpisze niepoprawny wpis, na przykład użytkownik wpisze literą, gdy wymagana jest cyfrą, formantu zostanie automatycznie Odrzuć dane wejściowe.  
  
 Język maskowania, który jest używany przez <xref:System.Windows.Forms.MaskedTextBox> jest bardzo elastyczny. Umożliwia określenie wymaganych znaków, znaki opcjonalne, literał znaków, takich jak łączniki i nawiasy, znaki waluty i separatorów daty. Formant działa dobrze powiązany ze źródłem danych. <xref:System.Windows.Forms.Binding.Format> Zdarzeń w powiązaniu danych może służyć do ponownego formatowania danych przychodzących ma zostać pasuje do maski i <xref:System.Windows.Forms.Binding.Parse> zdarzeń może służyć do ponownego formatowania danych wychodzących aby spełnić wymogi pola danych.  
  
 Aby uzyskać więcej informacji, zobacz [maskedtextbox — formant](../../../docs/framework/winforms/controls/maskedtextbox-control-windows-forms.md).  
  
## <a name="event-driven-validation"></a>Weryfikacja sterowane zdarzeniami  
 Mają programowe pełnej kontroli nad weryfikacji, czy należy wykonać sprawdzanie poprawności złożonego, należy używać zdarzenia walidacji, wbudowanych w większości formanty formularzy systemu Windows. Ma każdego formantu, który akceptuje dane wejściowe użytkownika dowolnych <xref:System.Windows.Forms.Control.Validating> zdarzenie wystąpi, gdy formant wymaga weryfikacji danych. W <xref:System.Windows.Forms.Control.Validating> metoda obsługi zdarzeń, można sprawdzić poprawność danych wejściowych na kilka sposobów użytkownika. Na przykład jeśli pole tekstowe, które musi zawierać kod pocztowy, można wykonać walidacji w następujący sposób:  
  
-   Jeśli kod pocztowy musi należeć do określonej grupy kodów pocztowych, można wykonać porównania ciągu na wejściu do sprawdzania poprawności danych wprowadzonych przez użytkownika. Na przykład jeśli kod pocztowy musi być w zestawie {10001 10002, 10003}, następnie służy porównania ciągów sprawdzania poprawności danych.  
  
-   Jeśli kod pocztowy musi być w formie określonych można używać wyrażeń regularnych, można sprawdzić poprawności danych wprowadzonych przez użytkownika. Na przykład, aby zweryfikować formularza `#####` lub `#####-####`, można użyć wyrażenia regularnego `^(\d{5})(-\d{4})?$`. Aby sprawdzić poprawność formularza `A#A #A#`, można użyć wyrażenia regularnego `[A-Z]\d[A-Z] \d[A-Z]\d`. Aby uzyskać więcej informacji na temat wyrażeń regularnych, zobacz [wyrażeń regularnych programu .NET Framework](../../../docs/standard/base-types/regular-expressions.md) i [przykłady wyrażeń regularnych](../../../docs/standard/base-types/regular-expression-examples.md).  
  
-   Jeśli kod pocztowy musi być prawidłowy kod pocztowy w Stanach Zjednoczonych, można wywołać usługi sieci Web kod do sprawdzania poprawności danych wprowadzonych przez użytkownika.  
  
 <xref:System.Windows.Forms.Control.Validating> Podano zdarzeń typu obiektu <xref:System.ComponentModel.CancelEventArgs>. Jeśli okaże się, że formantu danych jest nieprawidłowa, możesz anulować <xref:System.Windows.Forms.Control.Validating> zdarzenia przez ustawienie dla tego obiektu <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> właściwości `true`. Jeśli nie ustawisz <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> właściwości, formularze systemu Windows będzie założono, że Weryfikacja powiodła się dla tego formantu i wywoływania <xref:System.Windows.Forms.Control.Validated> zdarzeń.  
  
 Na przykład kodu, który sprawdza poprawność adresu e-mail w <xref:System.Windows.Controls.TextBox>, zobacz <xref:System.Windows.Forms.Control.Validating>.  
  
### <a name="data-binding-and-event-driven-validation"></a>Powiązanie danych i weryfikacji sterowane zdarzeniami  
 Sprawdzanie poprawności jest bardzo przydatny, gdy formanty mają powiązana ze źródłem danych, takich jak tabeli bazy danych. Przy użyciu weryfikacji, można upewnić się, że formantu danych spełnia na format wymagany przez źródło danych, i czy nie zawierać żadnych znaków specjalnych, takich jak znaków cudzysłowu i utworzyć kopię ułamkowe, który może być niebezpieczne.  
  
 Użycie wiązania danych, danych formantu jest zsynchronizowany ze źródłem danych podczas wykonywania <xref:System.Windows.Forms.Control.Validating> zdarzeń. Jeśli anulujesz <xref:System.Windows.Forms.Control.Validating> zdarzenia, dane nie będą synchronizowane ze źródłem danych.  
  
> [!IMPORTANT]
>  Jeśli masz walidacji niestandardowej, która ma miejsce po <xref:System.Windows.Forms.Control.Validating> zdarzenia nie wpłynie powiązania danych. Na przykład, jeśli masz kod <xref:System.Windows.Forms.Control.Validated> zdarzenia, które próbuje anulować wiązania danych, wiązania danych nastąpi. W tym przypadku do wykonywania sprawdzania poprawności w <xref:System.Windows.Forms.Control.Validated> zdarzeń, zmień formantu **trybu aktualizacji źródła danych** właściwości (**w obszarze (Databindings)**\\ **(zaawansowane)** ) z **OnValidation** do **nigdy**i Dodaj *kontroli*`.DataBindings["`*\<YOURFIELD >*  `"].WriteValue()` kodu sprawdzania poprawności.  
  
### <a name="implicit-and-explicit-validation"></a>Sprawdzanie poprawności jawne i niejawne  
 Dlatego po formantu uzyskać sprawdzana poprawność danych? To zależy od użytkownika, dewelopera. Korzystając z niejawnym lub jawnym argumentem weryfikacji, w zależności od potrzeb aplikacji.  
  
#### <a name="implicit-validation"></a>Niejawne weryfikacji  
 Podejście niejawne weryfikacji sprawdza poprawność danych jako użytkownik musi wprowadzić. Dane wprowadzone w formancie przez czytania kluczy, ponieważ są one naciśnięty, lub więcej najczęściej, gdy użytkownik ma fokus wprowadzania od jeden formant i przechodzi do następnego można sprawdzić poprawności danych. Takie rozwiązanie jest przydatne, gdy chcesz nadać natychmiast uzyskuje opinie użytkowników o danych, jak działają prawidłowo.  
  
 Jeśli chcesz użyć niejawnego sprawdzania poprawności dla formantu, należy ustawić tego formantu <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> właściwości `true`. Jeśli anulujesz <xref:System.Windows.Forms.Control.Validating> zdarzeń, zachowanie formantu będzie określana przez co ten zostanie przypisana do wartości <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>. Po przypisaniu <xref:System.Windows.Forms.AutoValidate.EnablePreventFocusChange>, spowoduje anulowanie zdarzenia <xref:System.Windows.Forms.Control.Validated> nie wystąpienie zdarzenia. Fokus wprowadzania pozostanie na bieżącego formantu, dopóki użytkownik nie zmieni się prawidłowe wartości wejściowe dane. Po przypisaniu <xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>, <xref:System.Windows.Forms.Control.Validated> nie nastąpi zdarzeń, gdy anulujesz zdarzenia, ale nadal zmieni fokus do następnego formantu.  
  
 Przypisywanie <xref:System.Windows.Forms.AutoValidate.Disable> do <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> właściwości całkowicie uniemożliwia niejawne sprawdzania poprawności. Aby sprawdzić poprawność formantów, konieczne będzie Użyj jawnego sprawdzania poprawności.  
  
#### <a name="explicit-validation"></a>Jawne weryfikacji  
 Podejście jawne weryfikacji sprawdza poprawność danych w tym samym czasie. Można sprawdzić poprawności danych w odpowiedzi na akcję użytkownika, takie jak kliknięcie przycisku Zapisz lub łącze do następnej. W przypadku akcji użytkownika możesz wyzwolić jawne weryfikacji w jednym z następujących sposobów:  
  
-   Wywołanie <xref:System.Windows.Forms.ContainerControl.Validate%2A> do sprawdzania poprawności ostatni formant, aby mieć utracie fokusu.  
  
-   Wywołanie <xref:System.Windows.Forms.ContainerControl.ValidateChildren%2A> do sprawdzania poprawności wszystkich formantów podrzędnych w formancie formularza lub kontenera.  
  
-   Wywołanie niestandardowej metody sprawdzania poprawności danych w kontrolkach ręcznie.  
  
#### <a name="default-implicit-validation-behavior-for-windows-forms-controls"></a>Formanty formularzy domyślne zachowanie niejawne sprawdzania poprawności dla systemu Windows  
 Inne formanty formularzy systemu Windows mają różne wartości domyślne dla ich <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> właściwości. W poniższej tabeli przedstawiono najbardziej typowych formantów i ich wartości domyślne.  
  
|Formant|Domyślne zachowanie sprawdzania poprawności|  
|-------------|---------------------------------|  
|<xref:System.Windows.Forms.ContainerControl>|<xref:System.Windows.Forms.AutoValidate.Inherit>|  
|<xref:System.Windows.Forms.Form>|<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>|  
|<xref:System.Windows.Forms.PropertyGrid>|Właściwości nie są widoczne w programie Visual Studio|  
|<xref:System.Windows.Forms.ToolStripContainer>|Właściwości nie są widoczne w programie Visual Studio|  
|<xref:System.Windows.Forms.SplitContainer>|<xref:System.Windows.Forms.AutoValidate.Inherit>|  
|<xref:System.Windows.Forms.UserControl>|<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>|  
  
## <a name="closing-the-form-and-overriding-validation"></a>Zamykanie formularza i zastępowanie sprawdzania poprawności  
 Formant ma fokus ponieważ dane, które zawiera jest nieprawidłowy, jest niemożliwe zamknąć formularz nadrzędny w zwykły sposób:  
  
-   Klikając **Zamknij** przycisku.  
  
-   Wybierając **Zamknij** w **systemu** menu.  
  
-   Wywołując <xref:System.Windows.Forms.Form.Close%2A> metody programowo.  
  
 W niektórych przypadkach może być użytkownikowi należy zamknąć formularz niezależnie od tego, czy wartości w formantach są prawidłowe. Można zastąpić sprawdzania poprawności i zamknij formularz, który nadal zawiera nieprawidłowe dane przez utworzenie obsługi w formularzu <xref:System.Windows.Forms.Form.Closing> zdarzeń. W tym przypadku należy ustawić <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> właściwości `false`. Dzięki temu formularza, aby zamknąć. Aby uzyskać więcej informacji i przykład zobacz <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>.  
  
> [!NOTE]
>  Jeśli wymusisz formularza, aby zamknąć w ten sposób dane w formantach formularza, które jeszcze nie zostały zapisane, zostaną utracone. Ponadto formularzy modalnych nie weryfikują zawartość formantów po zamknięciu. Sprawdzania poprawności kontroli nadal służy do blokowania fokus do formantu, ale nie trzeba mieć na uwadze zachowania związanego z zamknięciem formularza.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Control.Validating?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>  
 <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType>  
 [MaskedTextBox, kontrolka](../../../docs/framework/winforms/controls/maskedtextbox-control-windows-forms.md)  
 [Przykłady wyrażeń regularnych](../../../docs/standard/base-types/regular-expression-examples.md)
