---
title: Sprawdzanie poprawności danych wejściowych użytkownika
description: Zapoznaj się z kilkoma sposobami używania Windows Forms do sprawdzania poprawności danych wejściowych użytkownika w aplikacjach.
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, validating user input
- validation [Windows Forms], Windows Forms user input
- user input [Windows Forms], validating in Windows Forms
- validating user input [Windows Forms], Windows Forms
ms.assetid: 4ec07681-1dee-4bf9-be5e-718f635a33a1
ms.openlocfilehash: 89f245a523d473f052a337d8f29c2c05105d75eb
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325553"
---
# <a name="user-input-validation-in-windows-forms"></a>Walidacja danych użytkownika w formularzach systemu Windows
Gdy użytkownicy wprowadzają dane do aplikacji, warto sprawdzić, czy dane są prawidłowe przed jej użyciem. Może być konieczne, aby niektóre pola tekstowe nie miały długości zerowej, że pole jest sformatowane jako numer telefonu lub inny typ poprawnie sformułowanych danych lub że ciąg nie zawiera żadnych niebezpiecznych znaków, których można użyć do złamania zabezpieczeń bazy danych. Windows Forms zapewnia kilka metod sprawdzania poprawności danych wejściowych w aplikacji.  
  
## <a name="validation-with-the-maskedtextbox-control"></a>Walidacja przy użyciu kontrolki formantem MaskedTextBox  
 Aby wymagać od użytkowników wprowadzenia danych w dobrze zdefiniowanym formacie, takim jak numer telefonu lub numer części, można to zrobić szybko i przy użyciu formantu o minimalnym kodzie <xref:System.Windows.Forms.MaskedTextBox> . *Maska* to ciąg składający się z znaków z języka maskującego, który określa, które znaki mogą być wprowadzane w dowolnym miejscu w polu tekstowym. Kontrolka Wyświetla zestaw wyświetleń do użytkownika. Jeśli użytkownik wpisze niepoprawny wpis, na przykład użytkownik wpisze literę, gdy jest wymagana cyfra, formant automatycznie odrzuci dane wejściowe.  
  
 Język maskowania używany przez program <xref:System.Windows.Forms.MaskedTextBox> jest bardzo elastyczny. Pozwala to określić wymagane znaki, znaki opcjonalne, znaki literału, takie jak łączniki i nawiasy, znaki walutowe i separatory dat. Formant również dobrze sprawdza się w przypadku powiązania ze źródłem danych. <xref:System.Windows.Forms.Binding.Format>Zdarzenie w powiązaniu danych może służyć do ponownego formatowania przychodzących danych w celu zachowania zgodności z maską i <xref:System.Windows.Forms.Binding.Parse> można użyć zdarzenia, aby ponownie sformatować dane wychodzące w celu zachowania zgodności z specyfikacjami pola dane.  
  
 Aby uzyskać więcej informacji, zobacz [formantem MaskedTextBox Control](./controls/maskedtextbox-control-windows-forms.md).  
  
## <a name="event-driven-validation"></a>Weryfikacja oparta na zdarzeniach  
 Jeśli chcesz, aby Pełna kontrola programowa została przetworzona przez proces weryfikacji lub trzeba przeprowadzić złożone testy weryfikacyjne, należy użyć zdarzeń walidacji wbudowanych w większości formantów Windows Forms. Każda kontrolka akceptująca dowolne dane wejściowe użytkownika ma <xref:System.Windows.Forms.Control.Validating> zdarzenie, które nastąpi, gdy kontrolka wymaga weryfikacji danych. W <xref:System.Windows.Forms.Control.Validating> metodzie obsługi zdarzeń można sprawdzić poprawność danych wejściowych użytkownika na kilka sposobów. Na przykład, jeśli masz pole tekstowe, które musi zawierać kod pocztowy, możesz przeprowadzić walidację w następujący sposób:  
  
- Jeśli kod pocztowy musi należeć do określonej grupy kodów pocztowych, można wykonać Porównywanie ciągów w danych wejściowych, aby sprawdzić poprawność danych wprowadzonych przez użytkownika. Na przykład, jeśli kod pocztowy musi znajdować się w zestawie {10001, 10002, 10003}, wówczas można użyć porównania ciągów do walidacji danych.  
  
- Jeśli kod pocztowy musi znajdować się w określonym formularzu, można użyć wyrażeń regularnych do walidacji danych wprowadzonych przez użytkownika. Na przykład, aby sprawdzić poprawność formularza `#####` lub `#####-####` , można użyć wyrażenia regularnego `^(\d{5})(-\d{4})?$` . Aby sprawdzić poprawność formularza `A#A #A#` , można użyć wyrażenia regularnego `[A-Z]\d[A-Z] \d[A-Z]\d` . Aby uzyskać więcej informacji na temat wyrażeń regularnych, zobacz [.NET Framework wyrażenia regularne](../../standard/base-types/regular-expressions.md) i [Przykłady wyrażeń regularnych](../../standard/base-types/regular-expression-example-scanning-for-hrefs.md).  
  
- Jeśli kod pocztowy musi być prawidłowym kodem pocztowym Stany Zjednoczone, można wywołać usługę sieci Web kod pocztowy, aby sprawdzić poprawność danych wprowadzonych przez użytkownika.  
  
 <xref:System.Windows.Forms.Control.Validating>Zdarzenie jest dostarczane do obiektu typu <xref:System.ComponentModel.CancelEventArgs> . Jeśli okaże się, że dane kontrolki są nieprawidłowe, można anulować <xref:System.Windows.Forms.Control.Validating> zdarzenie, ustawiając właściwość tego obiektu <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> na `true` . Jeśli właściwość nie zostanie ustawiona, Windows Forms przyjmie, <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> że Walidacja zakończyła się powodzeniem dla tej kontrolki i Zgłoś <xref:System.Windows.Forms.Control.Validated> zdarzenie.  
  
 Przykładowy kod, który sprawdza poprawność adresu e-mail w <xref:System.Windows.Controls.TextBox> , znajduje się w temacie <xref:System.Windows.Forms.Control.Validating> .  
  
### <a name="data-binding-and-event-driven-validation"></a>Powiązanie danych i walidacja oparta na zdarzeniach  
 Walidacja jest bardzo przydatna, jeśli masz powiązane kontrolki ze źródłem danych, takim jak tabela bazy danych. Korzystając z walidacji, można upewnić się, że dane kontrolki spełniają format wymagany przez źródło danych i że nie zawierają żadnych znaków specjalnych, takich jak cudzysłowy i ukośniki odwrotne, które mogą być niebezpieczne.  
  
 W przypadku używania powiązania danych dane w formancie są synchronizowane ze źródłem danych podczas wykonywania <xref:System.Windows.Forms.Control.Validating> zdarzenia. Jeśli anulujesz <xref:System.Windows.Forms.Control.Validating> zdarzenie, dane nie zostaną zsynchronizowane ze źródłem danych.  
  
> [!IMPORTANT]
> Jeśli masz niestandardowe sprawdzanie poprawności, które ma miejsce po <xref:System.Windows.Forms.Control.Validating> zdarzeniu, nie wpłynie to na powiązanie danych. Na przykład jeśli masz kod w <xref:System.Windows.Forms.Control.Validated> zdarzeniu, które próbuje anulować powiązanie danych, nadal będą wykonywane powiązania danych. W tym przypadku aby przeprowadzić walidację w <xref:System.Windows.Forms.Control.Validated> zdarzeniu, Zmień właściwość **trybu aktualizacji źródła danych** kontrolki (**w obszarze (DataBindings)** \\ **(Zaawansowane)**) od **OnValidation** na **Never**, a następnie Dodaj *kontrolkę* `.DataBindings["` *\<YOURFIELD>* `"].WriteValue()` do kodu weryfikacyjnego.  
  
### <a name="implicit-and-explicit-validation"></a>Niejawne i jawne sprawdzanie poprawności  
 Tak więc kiedy dane kontrolki są sprawdzane? Jest to Twoje Deweloper. W zależności od potrzeb aplikacji można użyć weryfikacji jawnej lub jawnej.  
  
#### <a name="implicit-validation"></a>Niejawna weryfikacja  
 Niejawne podejście weryfikacyjne sprawdza poprawność danych w miarę ich wprowadzania przez użytkownika. Możesz sprawdzić poprawność danych w miarę wprowadzania danych w kontrolce, odczytując klucze podczas ich naciskania lub częściej, za każdym razem, gdy użytkownik przejmuje fokus od jednej kontrolki i przechodzi do następnego. Takie podejście jest przydatne, gdy chcesz dać użytkownikowi natychmiastową opinię na temat danych podczas pracy.  
  
 Jeśli chcesz użyć niejawnej weryfikacji dla kontrolki, musisz ustawić właściwość tej kontrolki <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> na <xref:System.Windows.Forms.AutoValidate.EnablePreventFocusChange> lub <xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange> . Jeśli anulujesz <xref:System.Windows.Forms.Control.Validating> zdarzenie, zachowanie kontrolki zostanie określone przez wartość, którą przypisano do <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> . Jeśli przypisano <xref:System.Windows.Forms.AutoValidate.EnablePreventFocusChange> , anulowanie zdarzenia spowoduje, że <xref:System.Windows.Forms.Control.Validated> zdarzenie nie wystąpi. Fokus wprowadzania pozostanie w bieżącym formancie, dopóki użytkownik nie zmieni danych na prawidłowe dane wejściowe. Jeśli przypisano <xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange> , <xref:System.Windows.Forms.Control.Validated> zdarzenie nie zostanie wykonane po anulowaniu zdarzenia, ale fokus nadal zostanie zmieniony na następną kontrolkę.  
  
 Przypisanie <xref:System.Windows.Forms.AutoValidate.Disable> do <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> właściwości zapobiega całkowicie niejawnej weryfikacji. Aby sprawdzić poprawność kontrolek, należy użyć jawnej walidacji.  
  
#### <a name="explicit-validation"></a>Jawna weryfikacja  
 Jawne podejście sprawdzania poprawności weryfikuje dane jednocześnie. Możesz sprawdzić poprawność danych w odpowiedzi na akcję użytkownika, na przykład klikając przycisk Zapisz lub następny link. Gdy wystąpi akcja użytkownika, można wyzwolić jawną weryfikację w jeden z następujących sposobów:  
  
- Wywołaj <xref:System.Windows.Forms.ContainerControl.Validate%2A> , aby zweryfikować ostatnią kontrolkę w celu przegrania fokusu.  
  
- Wywołaj <xref:System.Windows.Forms.ContainerControl.ValidateChildren%2A> , aby sprawdzić poprawność wszystkich formantów podrzędnych w kontrolce formularza lub kontenera.  
  
- Wywołaj metodę niestandardową, aby ręcznie zweryfikować dane w kontrolkach.  
  
#### <a name="default-implicit-validation-behavior-for-windows-forms-controls"></a>Domyślne zachowanie niejawnego sprawdzania poprawności dla formantów Windows Forms  
 Różne kontrolki Windows Forms mają różne wartości domyślne dla ich <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> właściwości. W poniższej tabeli przedstawiono najczęściej używane kontrolki i ich ustawienia domyślne.  
  
|Kontrola|Domyślne zachowanie walidacji|  
|-------------|---------------------------------|  
|<xref:System.Windows.Forms.ContainerControl>|<xref:System.Windows.Forms.AutoValidate.Inherit>|  
|<xref:System.Windows.Forms.Form>|<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>|  
|<xref:System.Windows.Forms.PropertyGrid>|Właściwość nie jest ujawniona w programie Visual Studio|  
|<xref:System.Windows.Forms.ToolStripContainer>|Właściwość nie jest ujawniona w programie Visual Studio|  
|<xref:System.Windows.Forms.SplitContainer>|<xref:System.Windows.Forms.AutoValidate.Inherit>|  
|<xref:System.Windows.Forms.UserControl>|<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>|  
  
## <a name="closing-the-form-and-overriding-validation"></a>Zamykanie formularza i zastępowanie walidacji  
 Gdy kontrolka zachowuje fokus, ponieważ zawarte w niej dane są nieprawidłowe, nie można zamknąć formularza nadrzędnego w jeden z typowych sposobów:  
  
- Klikając przycisk **Zamknij** .  
  
- Wybierając pozycję **Zamknij** w menu **systemowym** .  
  
- Wywoływanie <xref:System.Windows.Forms.Form.Close%2A> metody programowo.  
  
 Jednak w niektórych przypadkach możesz chcieć pozwolić użytkownikowi na zamknięcie formularza niezależnie od tego, czy wartości w kontrolkach są prawidłowe. Możesz przesłonić walidację i zamknąć formularz, który nadal zawiera nieprawidłowe dane, tworząc procedurę obsługi dla <xref:System.Windows.Forms.Form.FormClosing> zdarzenia formularza. W zdarzeniu Ustaw <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> Właściwość na `false` . Wymusza to zamknięcie formularza. Aby uzyskać więcej informacji i zapoznać się z przykładem, zobacz <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType> .  
  
> [!NOTE]
> Jeśli wymusisz zamknięcie formularza w ten sposób, wszelkie dane w kontrolkach formularza, które nie zostały jeszcze zapisane, zostały utracone. Ponadto formularze modalne nie weryfikują zawartości formantów po ich zamknięciu. Nadal można użyć walidacji kontrolek, aby zablokować fokus do kontrolki, ale nie trzeba mieć informacji o zachowaniu związanym z zamknięciem formularza.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.Control.Validating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>
- <xref:System.Windows.Forms.FormClosingEventArgs?displayProperty=nameWithType>
- [MaskedTextBox, kontrolka](./controls/maskedtextbox-control-windows-forms.md)
- [Przykłady wyrażeń regularnych](../../standard/base-types/regular-expression-example-scanning-for-hrefs.md)
