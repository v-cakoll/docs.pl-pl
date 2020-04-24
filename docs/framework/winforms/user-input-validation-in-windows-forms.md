---
title: Sprawdzanie poprawności danych wejściowych użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, validating user input
- validation [Windows Forms], Windows Forms user input
- user input [Windows Forms], validating in Windows Forms
- validating user input [Windows Forms], Windows Forms
ms.assetid: 4ec07681-1dee-4bf9-be5e-718f635a33a1
ms.openlocfilehash: eafbf54552566011fef9d2dbeb5e9f9fa3facabd
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646301"
---
# <a name="user-input-validation-in-windows-forms"></a>Walidacja danych użytkownika w formularzach systemu Windows
Gdy użytkownicy wejdą dane do aplikacji, można sprawdzić, czy dane są prawidłowe, zanim aplikacja będzie z niej korzystać. Może być wymagane, aby niektóre pola tekstowe nie były o zerowej długości, aby pole było sformatowane jako numer telefonu lub inny typ dobrze sformułowanych danych lub aby ciąg nie zawierał żadnych niebezpiecznych znaków, które mogłyby zostać użyte do naruszenia bezpieczeństwa bazy danych. Formularze systemu Windows udostępnia kilka sposobów sprawdzania poprawności danych wejściowych w aplikacji.  
  
## <a name="validation-with-the-maskedtextbox-control"></a>Sprawdzanie poprawności za pomocą formantu MaskedTextBox  
 Jeśli musisz wymagać od użytkowników wprowadzania danych w dobrze zdefiniowanym formacie, takim jak numer telefonu lub numer <xref:System.Windows.Forms.MaskedTextBox> części, można to osiągnąć szybko i przy minimalnym kodzie za pomocą formantu. *Maska* to ciąg składający się ze znaków z języka maskującego, który określa, które znaki mogą być wprowadzane w dowolnym miejscu w polu tekstowym. Formant wyświetla zestaw monitów do użytkownika. Jeśli użytkownik wpisze niepoprawny wpis, na przykład użytkownik wpisze literę, gdy wymagana jest cyfra, formant automatycznie odrzuci dane wejściowe.  
  
 Język maskujący, który <xref:System.Windows.Forms.MaskedTextBox> jest używany przez jest bardzo elastyczny. Umożliwia określenie wymaganych znaków, znaków opcjonalnych, znaków dosłownych, takich jak łączniki i nawiasy, znaki walutowe i separatory daty. Formant działa również dobrze, gdy jest powiązany ze źródłem danych. Zdarzenie <xref:System.Windows.Forms.Binding.Format> dotyczące powiązania danych może służyć do formatowania danych przychodzących <xref:System.Windows.Forms.Binding.Parse> w celu zapewnienia zgodności z maską, a zdarzenie może służyć do formatowania wychodzących danych w celu zapewnienia zgodności ze specyfikacjami pola danych.  
  
 Aby uzyskać więcej informacji, zobacz [MaskedTextBox Control](./controls/maskedtextbox-control-windows-forms.md).  
  
## <a name="event-driven-validation"></a>Sprawdzanie poprawności oparte na zdarzeniach  
 Jeśli chcesz pełną kontrolę programową nad sprawdzaniem poprawności lub trzeba wykonać złożone sprawdzanie poprawności, należy użyć zdarzeń sprawdzania poprawności wbudowanych w większości formantów windows forms. Każdy formant, który akceptuje dane <xref:System.Windows.Forms.Control.Validating> wejściowe użytkownika w postaci swobodnej, ma zdarzenie, które będzie występować za każdym razem, gdy formant wymaga sprawdzania poprawności danych. W <xref:System.Windows.Forms.Control.Validating> metodzie obsługi zdarzeń można sprawdzić poprawność danych wejściowych użytkownika na kilka sposobów. Na przykład jeśli masz pole tekstowe, które musi zawierać kod pocztowy, można wykonać sprawdzanie poprawności w następujący sposób:  
  
- Jeśli kod pocztowy musi należeć do określonej grupy kodów pocztowych, można wykonać porównanie ciągów na danych wejściowych, aby sprawdzić poprawność danych wprowadzonych przez użytkownika. Jeśli na przykład kod pocztowy musi znajdować się w zestawie {10001, 10002, 10003}, można użyć porównania ciągów, aby sprawdzić poprawność danych.  
  
- Jeśli kod pocztowy musi być w określonej formie, można użyć wyrażeń regularnych, aby sprawdzić poprawność danych wprowadzonych przez użytkownika. Na przykład, aby sprawdzić `#####` `#####-####`poprawność formularza lub `^(\d{5})(-\d{4})?$`, można użyć wyrażenia regularnego . Aby sprawdzić poprawność formularza, `A#A #A#`można `[A-Z]\d[A-Z] \d[A-Z]\d`użyć wyrażenia regularnego . Aby uzyskać więcej informacji na temat wyrażeń regularnych, zobacz .NET Framework Wyrażenia regularne i [przykłady wyrażeń](../../standard/base-types/regular-expressions.md) [regularnych](../../standard/base-types/regular-expression-example-scanning-for-hrefs.md).  
  
- Jeśli kod pocztowy musi być prawidłowym kodem pocztowym Stanów Zjednoczonych, można wywołać usługę sieci Web z kodem pocztowym, aby sprawdzić poprawność danych wprowadzonych przez użytkownika.  
  
 Zdarzenie <xref:System.Windows.Forms.Control.Validating> jest dostarczane obiekt <xref:System.ComponentModel.CancelEventArgs>typu . Jeśli okaże się, że dane formantu są <xref:System.Windows.Forms.Control.Validating> nieprawidłowe, można anulować zdarzenie, ustawiając <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> właściwość tego obiektu na `true`. Jeśli właściwość nie <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> zostanie ustawiona, windows forms przyjmie, że sprawdzanie <xref:System.Windows.Forms.Control.Validated> poprawności powiodło się dla tego formantu i wywoła zdarzenie.  
  
 Przykład kodu, który sprawdza poprawność <xref:System.Windows.Controls.TextBox>adresu <xref:System.Windows.Forms.Control.Validating>e-mail w pliku , zobacz .  
  
### <a name="data-binding-and-event-driven-validation"></a>Powiązanie danych i sprawdzanie poprawności oparte na zdarzeniach  
 Sprawdzanie poprawności jest bardzo przydatne, gdy masz związane formantów do źródła danych, takich jak tabela bazy danych. Za pomocą sprawdzania poprawności, można upewnić się, że dane formantu spełnia format wymagany przez źródło danych i że nie zawiera żadnych znaków specjalnych, takich jak cudzysłowy i ukośniki wsteczne, które mogą być niebezpieczne.  
  
 Podczas korzystania z powiązania danych dane w formancie są synchronizowane <xref:System.Windows.Forms.Control.Validating> ze źródłem danych podczas wykonywania zdarzenia. Jeśli anulujesz <xref:System.Windows.Forms.Control.Validating> zdarzenie, dane nie zostaną zsynchronizowane ze źródłem danych.  
  
> [!IMPORTANT]
> Jeśli masz niestandardowe sprawdzanie poprawności, które odbywa się po zdarzeniu, <xref:System.Windows.Forms.Control.Validating> nie wpłynie na powiązanie danych. Na przykład jeśli masz kod <xref:System.Windows.Forms.Control.Validated> w przypadku, który próbuje anulować powiązanie danych, powiązanie danych będzie nadal występować. W takim przypadku, aby <xref:System.Windows.Forms.Control.Validated> wykonać sprawdzanie poprawności w zdarzeniu, zmień właściwość **tryb aktualizacji źródła danych** formantu **(w obszarze (Databindings)**\\ **(Zaawansowane)**) z **OnValidation na** **Never**i dodaj *control*`.DataBindings["`*\<YOURFIELD>* `"].WriteValue()` do kodu sprawdzania poprawności.  
  
### <a name="implicit-and-explicit-validation"></a>Sprawdzanie poprawności niejawnej i jawnej  
 Więc kiedy dane formantu są sprawdzane? To zależy od Ciebie, dewelopera. Można użyć niejawne lub jawne sprawdzanie poprawności, w zależności od potrzeb aplikacji.  
  
#### <a name="implicit-validation"></a>Niejawna weryfikacja  
 Podejście niejawnego sprawdzania poprawności sprawdza poprawność danych, gdy użytkownik wprowadza go. Można sprawdzić poprawność danych, jak dane są wprowadzane w formancie, odczytywania klawiszy, ponieważ są one naciśnięte lub częściej, gdy użytkownik odbierze fokus wejściowy z dala od jednego formantu i przechodzi do następnego. Takie podejście jest przydatne, gdy chcesz dać użytkownikowi natychmiastową opinię na temat danych podczas ich pracy.  
  
 Jeśli chcesz użyć niejawnej sprawdzania poprawności dla formantu, należy ustawić <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> właściwość tego formantu na <xref:System.Windows.Forms.AutoValidate.EnablePreventFocusChange> lub <xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>. Jeśli anulujesz <xref:System.Windows.Forms.Control.Validating> zdarzenie, zachowanie formantu będzie zależeć od <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>wartości przypisanej do . Jeśli przypisano, <xref:System.Windows.Forms.AutoValidate.EnablePreventFocusChange>anulowanie zdarzenia spowoduje, że <xref:System.Windows.Forms.Control.Validated> zdarzenie nie wystąpi. Fokus wejściowy pozostanie na bieżącej formancie, dopóki użytkownik nie zmieni danych na prawidłowe dane wejściowe. Jeśli został <xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>przypisany <xref:System.Windows.Forms.Control.Validated> , zdarzenie nie nastąpi po anulowaniu zdarzenia, ale fokus nadal zmieni się na następny formant.  
  
 Przypisywanie <xref:System.Windows.Forms.AutoValidate.Disable> do <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> właściwości zapobiega niejawnej weryfikacji całkowicie. Aby sprawdzić poprawność formantów, należy użyć jawnego sprawdzania poprawności.  
  
#### <a name="explicit-validation"></a>Jawna weryfikacja  
 Podejście jawne sprawdzanie poprawności sprawdza poprawność danych w tym samym czasie. Można sprawdzić poprawność danych w odpowiedzi na akcję użytkownika, taką jak kliknięcie przycisku Zapisz lub łącza Dalej. Po wystąpieniu akcji użytkownika można wyzwolić jawne sprawdzanie poprawności w jeden z następujących sposobów:  
  
- Wywołanie, <xref:System.Windows.Forms.ContainerControl.Validate%2A> aby sprawdzić poprawność ostatniego formantu, aby utracić fokus.  
  
- Wywołanie, <xref:System.Windows.Forms.ContainerControl.ValidateChildren%2A> aby sprawdzić poprawność wszystkich formantów podrzędnych w formularzu lub formancie kontenera.  
  
- Wywołanie metody niestandardowej, aby ręcznie sprawdzić poprawność danych w formantach.  
  
#### <a name="default-implicit-validation-behavior-for-windows-forms-controls"></a>Domyślne zachowanie niejawnego sprawdzania poprawności dla formantów formularzy systemu Windows  
 Różne formanty formularzy systemu <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> Windows mają różne wartości domyślne dla ich właściwości. W poniższej tabeli przedstawiono najczęściej zadawane przez kontrolki i ich wartości domyślne.  
  
|Kontrola|Domyślne zachowanie sprawdzania poprawności|  
|-------------|---------------------------------|  
|<xref:System.Windows.Forms.ContainerControl>|<xref:System.Windows.Forms.AutoValidate.Inherit>|  
|<xref:System.Windows.Forms.Form>|<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>|  
|<xref:System.Windows.Forms.PropertyGrid>|Właściwość nie jest widoczna w programie Visual Studio|  
|<xref:System.Windows.Forms.ToolStripContainer>|Właściwość nie jest widoczna w programie Visual Studio|  
|<xref:System.Windows.Forms.SplitContainer>|<xref:System.Windows.Forms.AutoValidate.Inherit>|  
|<xref:System.Windows.Forms.UserControl>|<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>|  
  
## <a name="closing-the-form-and-overriding-validation"></a>Zamykanie formularza i sprawdzanie poprawności zastępowania  
 Gdy formant zachowuje fokus, ponieważ dane, które zawiera, są nieprawidłowe, nie można zamknąć formularza nadrzędnego w jeden ze zwykłych sposobów:  
  
- Klikając przycisk **Zamknij.**  
  
- Wybierając **przycisk Zamknij** w menu **System.**  
  
- Wywołując <xref:System.Windows.Forms.Form.Close%2A> metodę programowo.  
  
 Jednak w niektórych przypadkach można pozwolić użytkownikowi zamknąć formularz, niezależnie od tego, czy wartości w formanty są prawidłowe. Można zastąpić sprawdzanie poprawności i zamknąć formularz, który nadal zawiera nieprawidłowe <xref:System.Windows.Forms.Form.FormClosing> dane, tworząc program obsługi dla zdarzenia formularza. W przypadku, ustaw <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> właściwość na `false`. Wymusza to zamknięcie formularza. Aby uzyskać więcej informacji <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>i przykład, zobacz .  
  
> [!NOTE]
> Jeśli wymusisz zamknięcie formularza w ten sposób, wszelkie dane w formantach formularza, które nie zostały jeszcze zapisane, są tracone. Ponadto formularze modalne nie sprawdzają poprawności zawartości formantów, gdy są zamknięte. Nadal można użyć sprawdzania poprawności formantu, aby zablokować fokus do formantu, ale nie trzeba się martwić o zachowanie skojarzone z zamknięciem formularza.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.Control.Validating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>
- <xref:System.Windows.Forms.FormClosingEventArgs?displayProperty=nameWithType>
- [MaskedTextBox, kontrolka](./controls/maskedtextbox-control-windows-forms.md)
- [Przykłady wyrażeń regularnych](../../standard/base-types/regular-expression-example-scanning-for-hrefs.md)
