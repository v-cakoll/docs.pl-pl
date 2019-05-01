---
title: Walidacja danych użytkownika w formularzach systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, validating user input
- validation [Windows Forms], Windows Forms user input
- user input [Windows Forms], validating in Windows Forms
- validating user input [Windows Forms], Windows Forms
ms.assetid: 4ec07681-1dee-4bf9-be5e-718f635a33a1
ms.openlocfilehash: c8a40706df4274728b438cff2539173a0e94b767
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61800129"
---
# <a name="user-input-validation-in-windows-forms"></a>Walidacja danych użytkownika w formularzach systemu Windows
Gdy użytkownicy wprowadzają dane do aplikacji, można sprawdzić, czy dane są prawidłowe, zanim aplikacja używa go. Może wymagać, że niektóre pola tekstowego jest o zerowej długości, że pole formatowane jako numer telefonu lub innego typu danych sformułowany lub czy ciąg zawiera niebezpiecznych znaków, które mogłyby zostać użyte w celu złamania zabezpieczeń bazy danych. Formularze Windows oferuje kilka sposobów umożliwiające sprawdzanie poprawności danych wejściowych w aplikacji.  
  
## <a name="validation-with-the-maskedtextbox-control"></a>Sprawdzanie poprawności z kontrolką Maskedtextbox  
 Jeśli potrzebujesz wymagać od użytkowników wprowadzania danych w dobrze zdefiniowanym formacie, takie jak numer telefonu lub numeru części można to zrobić szybko i przy minimalnej ilości kodu za pomocą <xref:System.Windows.Forms.MaskedTextBox> kontroli. A *maski* jest ciągiem składają się ze znaków z języka maskowanie, który określa znaki, które można wprowadzić na żadnej pozycji podanej w polu tekstowym. Kontrolka ma wyświetlać zestawu monitów dla użytkownika. Jeśli użytkownik wpisze niepoprawny wpis, na przykład użytkownik wpisze literę, gdy wymagana jest cyfra, formant automatycznie odrzuci dane wejściowe.  
  
 Język maskowanie, który jest używany przez <xref:System.Windows.Forms.MaskedTextBox> jest bardzo elastyczny. Umożliwia określenie wymaganych znaków, znaki opcjonalne, literałów znaków, takich jak łączniki i nawiasy, waluty znaków i separatory daty. Kontrolki działa dobrze powiązany ze źródłem danych. <xref:System.Windows.Forms.Binding.Format> Zdarzeń w powiązaniu danych może służyć do formatowania danych przychodzących do wykonania z maską i <xref:System.Windows.Forms.Binding.Parse> zdarzeń może służyć do formatowania danych wychodzących, aby spełnić wymogi pola danych.  
  
 Aby uzyskać więcej informacji, zobacz [maskedtextbox — formant](./controls/maskedtextbox-control-windows-forms.md).  
  
## <a name="event-driven-validation"></a>Weryfikacja oparte na zdarzeniach  
 Ma programowe pełnej kontroli nad weryfikacji, czy trzeba będzie wykonać sprawdzanie poprawności złożonych, należy użyć zdarzenia sprawdzania poprawności, wbudowane w większości kontrolek Windows Forms. Każdy formant, który akceptuje dane wejściowe użytkownika w dowolnej postaci ma <xref:System.Windows.Forms.Control.Validating> zdarzenia, które będzie wysyłane zawsze, gdy kontrolka wymaga sprawdzania poprawności danych. W <xref:System.Windows.Forms.Control.Validating> metody obsługi zdarzeń, można sprawdzić poprawność danych wejściowych na kilka sposobów użytkownika. Na przykład jeśli masz pole tekstowe, które mogą zawierać kod pocztowy, należy wykonać sprawdzanie poprawności w następujący sposób:  
  
- Jeśli kod pocztowy musi należeć do konkretnej grupy kodów pocztowych, można wykonać porównania ciągów w danych wejściowych do sprawdzania poprawności danych wprowadzonych przez użytkownika. Na przykład jeśli kod pocztowy musi być w zestawie {10001 10002, 10003}, następnie umożliwia porównanie ciągów sprawdzania poprawności danych.  
  
- Jeśli kod pocztowy musi znajdować się w określonej formy można użyć wyrażeń regularnych do sprawdzania poprawności danych wprowadzonych przez użytkownika. Na przykład, aby zweryfikować formularza `#####` lub `#####-####`, można użyć wyrażenia regularnego `^(\d{5})(-\d{4})?$`. Aby zweryfikować formularza `A#A #A#`, można użyć wyrażenia regularnego `[A-Z]\d[A-Z] \d[A-Z]\d`. Aby uzyskać więcej informacji na temat wyrażeń regularnych, zobacz [wyrażeń regularnych programu .NET Framework](../../standard/base-types/regular-expressions.md) i [przykłady wyrażeń regularnych](../../standard/base-types/regular-expression-examples.md).  
  
- Jeśli kod pocztowy musi być prawidłowy kod pocztowy w Stanach Zjednoczonych, można wywołać usługę sieci Web kod pocztowy i sprawdzanie poprawności danych wprowadzonych przez użytkownika.  
  
 <xref:System.Windows.Forms.Control.Validating> Zdarzeń jest podany obiekt typu <xref:System.ComponentModel.CancelEventArgs>. Jeśli okaże się, że dane formantu są nieprawidłowe, możesz anulować <xref:System.Windows.Forms.Control.Validating> zdarzeń przez ustawienie dla tego obiektu <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> właściwość `true`. Jeśli nie ustawisz <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> właściwości Windows Forms będzie założono tego sprawdzanie poprawności zakończyło się pomyślnie dla tej kontrolki i wywoływania <xref:System.Windows.Forms.Control.Validated> zdarzeń.  
  
 Dla przykładu kodu, który sprawdza poprawność adresu e-mail w <xref:System.Windows.Controls.TextBox>, zobacz <xref:System.Windows.Forms.Control.Validating>.  
  
### <a name="data-binding-and-event-driven-validation"></a>Powiązanie danych oraz weryfikacja oparte na zdarzeniach  
 Sprawdzanie poprawności jest bardzo przydatne, gdy kontrolki mają powiązana ze źródłem danych, takich jak tabela bazy danych. Za pomocą weryfikacji, można upewnić się, że kontroli nad danych spełnia formatowanie wymaganej przez źródło danych, i że nie zawierać żadnych znaków specjalnych, takich jak znaki cudzysłowu i utworzyć kopię ukośników, który może być niebezpieczne.  
  
 Gdy używasz wiązania danych, danych w kontrolce jest zsynchronizowany ze źródłem danych podczas wykonywania <xref:System.Windows.Forms.Control.Validating> zdarzeń. Jeśli anulujesz <xref:System.Windows.Forms.Control.Validating> zdarzenia, dane nie zostaną zsynchronizowane ze źródłem danych.  
  
> [!IMPORTANT]
>  W przypadku niestandardowego sprawdzania poprawności, który ma miejsce po <xref:System.Windows.Forms.Control.Validating> zdarzenia nie wpłynie to na powiązanie danych. Na przykład, jeśli masz kod <xref:System.Windows.Forms.Control.Validated> zdarzenia, które próbuje anulować powiązania danych, powiązanie danych są nadal naliczane. W tym przypadku do wykonywania sprawdzania poprawności w <xref:System.Windows.Forms.Control.Validated> zdarzeń, kontroli zmian **tryb aktualizacji źródła danych** właściwości (**w obszarze powiązania (danych)**\\ **(zaawansowane)** ) z **OnValidation** do **nigdy**i Dodaj *kontroli*`.DataBindings["`*\<YOURFIELD >*  `"].WriteValue()` kodu sprawdzania poprawności.  
  
### <a name="implicit-and-explicit-validation"></a>Sprawdzanie poprawności jawne i niejawne  
 Dlatego jeśli kontrolki danych walidacji? To zależy od użytkownika, dla deweloperów. Umożliwia jawne lub niejawne sprawdzania poprawności, w zależności od potrzeb aplikacji.  
  
#### <a name="implicit-validation"></a>Niejawne sprawdzania poprawności  
 Podejście weryfikacji niejawna sprawdza poprawność danych, ponieważ użytkownik musi wprowadzić. Można sprawdzić poprawności danych, dane wprowadzone w kontrolce, zapoznając się z kluczami są naciśnięte przyciski lub więcej często zawsze wtedy, gdy użytkownik ma fokus wprowadzania od jeden formant i przechodzi do następnego. To podejście jest przydatne, gdy chcesz nadać opinii natychmiastowego użytkowników o danych, jak one działają.  
  
 Jeśli chcesz użyć niejawnego sprawdzania poprawności dla formantu, należy ustawić tę kontrolkę <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> właściwość `true`. Jeśli anulujesz <xref:System.Windows.Forms.Control.Validating> zdarzeń i zachowanie kontrolki jest zależna od co, przypisany do wartości <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>. Po przypisaniu <xref:System.Windows.Forms.AutoValidate.EnablePreventFocusChange>, spowoduje anulowanie zdarzenia <xref:System.Windows.Forms.Control.Validated> nie wystąpienie zdarzenia. Fokus wprowadzania nadal korzystać z kontrolą bieżącą dopóki użytkownik nie zmieni dane prawidłowych danych wejściowych. Po przypisaniu <xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>, <xref:System.Windows.Forms.Control.Validated> zdarzeń nie ma miejsce, gdy anulowanie zdarzenia, ale nadal zmieni fokus do następnego formantu.  
  
 Przypisywanie <xref:System.Windows.Forms.AutoValidate.Disable> do <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> właściwość całkowicie uniemożliwia niejawne sprawdzania poprawności. Aby zweryfikować swoje formanty, trzeba będzie Użyj jawnego sprawdzania poprawności.  
  
#### <a name="explicit-validation"></a>Jawne sprawdzania poprawności  
 Podejście jawne weryfikacji sprawdza poprawność danych w tym samym czasie. Możesz walidować dane w odpowiedzi na akcję użytkownika, takie jak kliknięcie przycisku Zapisz lub łącze do następnej. W przypadku akcji użytkownika jawne sprawdzania poprawności mogą być uruchamiane w jednym z następujących sposobów:  
  
- Wywołaj <xref:System.Windows.Forms.ContainerControl.Validate%2A> można zweryfikować ostatni formant, aby utracić fokus.  
  
- Wywołaj <xref:System.Windows.Forms.ContainerControl.ValidateChildren%2A> do sprawdzania poprawności wszystkich kontrolek podrzędnych w kontrolce formularza lub kontenera.  
  
- Wywołanie niestandardowej metody sprawdzania poprawności danych w kontrolkach, ręcznie.  
  
#### <a name="default-implicit-validation-behavior-for-windows-forms-controls"></a>Formanty formularzy domyślne zachowanie weryfikacji niejawna systemu Windows  
 Różne formanty Windows Forms mają różne wartości domyślne dla ich <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> właściwości. W poniższej tabeli przedstawiono najbardziej typowe kontrolki i ich wartości domyślne.  
  
|formant|Domyślne zachowanie walidacji|  
|-------------|---------------------------------|  
|<xref:System.Windows.Forms.ContainerControl>|<xref:System.Windows.Forms.AutoValidate.Inherit>|  
|<xref:System.Windows.Forms.Form>|<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>|  
|<xref:System.Windows.Forms.PropertyGrid>|Właściwości, które nie są widoczne w programie Visual Studio|  
|<xref:System.Windows.Forms.ToolStripContainer>|Właściwości, które nie są widoczne w programie Visual Studio|  
|<xref:System.Windows.Forms.SplitContainer>|<xref:System.Windows.Forms.AutoValidate.Inherit>|  
|<xref:System.Windows.Forms.UserControl>|<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>|  
  
## <a name="closing-the-form-and-overriding-validation"></a>Zamyka formularz i zastępowanie sprawdzania poprawności  
 Formant przechowuje koncentracji uwagi, ponieważ zawartych w nim danych jest nieprawidłowa, jest niemożliwe zamknąć formularz nadrzędny w zwykły sposób:  
  
- Klikając **Zamknij** przycisku.  
  
- Wybierając **Zamknij** w **systemu** menu.  
  
- Przez wywołanie metody <xref:System.Windows.Forms.Form.Close%2A> metoda programowo.  
  
 Jednak w niektórych przypadkach możesz chcieć umożliwić użytkownikowi Zamknij formularz, niezależnie od tego, czy są prawidłowe wartości w formantach. Można zastąpić sprawdzania poprawności i zamknij formularz, która nadal zawiera nieprawidłowe dane, tworząc Obsługa formularza <xref:System.Windows.Forms.Form.Closing> zdarzeń. W tym przypadku, należy ustawić <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> właściwość `false`. Wymusza formularza, aby zamknąć. Aby uzyskać więcej informacji i obejrzeć przykład, zobacz <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>.  
  
> [!NOTE]
>  Jeśli wymusisz formularza, aby zamknąć w ten sposób, wszystkie dane w kontrolek formularza, który nie został już zapisany zostaną utracone. Ponadto formularze modalne nie weryfikują zawartość kontrolki po zamknięciu. Można nadal używać sprawdzania poprawności formantu do blokowania fokus do formantu, ale nie trzeba mieć wątpliwości dotyczące zachowania związanego z zamknięciem formularza.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Control.Validating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>
- <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType>
- [MaskedTextBox, kontrolka](./controls/maskedtextbox-control-windows-forms.md)
- [Przykłady wyrażeń regularnych](../../standard/base-types/regular-expression-examples.md)
