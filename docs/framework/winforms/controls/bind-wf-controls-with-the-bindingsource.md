---
title: Powiązywanie formantów ze składnikiem BindingSource przy użyciu narzędzia Projektant
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding
- BindingSource component [Windows Forms], binding controls
- data binding [Windows Forms], BindingSource component
ms.assetid: 391ae170-de5c-40f8-8233-91cb2ee4683a
ms.openlocfilehash: 35b3fb7b9884f07dd6e2aef311a01d3090c44227
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744391"
---
# <a name="how-to-bind-windows-forms-controls-with-the-bindingsource-component-using-the-designer"></a>Porady: powiązywanie kontrolek formularzy systemu Windows ze składnikiem BindingSource przy użyciu narzędzia Projektant
Po dodaniu kontrolek do formularza i określeniu interfejsu użytkownika dla aplikacji można powiązać kontrolki ze źródłem danych, aby w czasie wykonywania użytkownicy mogli zmieniać i zapisywać dane związane z aplikacją.

 Powiązanie kontrolki lub serii formantów w Windows Forms jest najłatwiej realizowane przy użyciu kontrolki <xref:System.Windows.Forms.BindingSource> jako mostka między kontrolkami w formularzu a źródłem danych.

 Co najmniej jedna kontrolka w formularzu może być powiązana z danymi; w poniższej procedurze formant <xref:System.Windows.Forms.TextBox> jest powiązany ze źródłem danych.

 Aby wykonać tę procedurę, zakłada się, że zostanie utworzone powiązanie ze źródłem danych uzyskanym z bazy danych. Aby uzyskać więcej informacji na temat tworzenia źródeł danych z innych magazynów danych, zobacz [Dodawanie nowych źródeł danych](/visualstudio/data-tools/add-new-data-sources).

## <a name="to-bind-a-control-at-design-time"></a>Aby powiązać formant w czasie projektowania

1. Przeciągnij kontrolkę <xref:System.Windows.Forms.TextBox> do formularza.

2. W oknie **Właściwości** :

    1. Rozwiń węzeł **(DataBindings)** .

    2. Kliknij strzałkę obok właściwości <xref:System.Windows.Forms.TextBox.Text%2A>.

         Zostanie otwarty Edytor typów interfejsu użytkownika **źródła danych** .

         Jeśli źródło danych zostało wcześniej skonfigurowane dla projektu lub formularza, pojawi się.

3. Kliknij pozycję **Dodaj źródło danych projektu** , aby połączyć się z danymi i utworzyć źródło danych.

4. Na stronie powitalnej **Kreatora konfiguracji źródła danych** kliknij przycisk **dalej**.

5. Na stronie **Wybierz typ źródła danych** wybierz pozycję **baza danych**.

6. Na stronie **Wybierz połączenie danych** wybierz połączenie danych z listy dostępnych połączeń. Jeśli żądane połączenie danych nie jest dostępne wybierz pozycję **nowe połączenie** , aby utworzyć nowe połączenie danych.

7. Wybierz opcję **tak, Zapisz połączenie,** aby zapisać parametry połączenia w pliku konfiguracyjnym aplikacji.

8. Wybierz obiekty bazy danych do dołączenia do aplikacji. W takim przypadku wybierz pole w tabeli, które ma być wyświetlane <xref:System.Windows.Forms.TextBox>.

9. W razie potrzeby Zastąp domyślną nazwę zestawu danych.

10. Kliknij przycisk **Zakończ**.

11. W oknie **Właściwości** kliknij strzałkę obok właściwości <xref:System.Windows.Forms.TextBox.Text%2A>. W edytorze typów interfejsu użytkownika **źródła danych** wybierz nazwę pola, do którego ma zostać powiązana <xref:System.Windows.Forms.TextBox>.

     Edytor typów interfejsu użytkownika **źródła** danych zostanie zamknięty, a zestaw danych, <xref:System.Windows.Forms.BindingSource> i karta tabeli dla tego połączenia danych są dodawane do formularza.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.BindingNavigator>
- [Dodawanie nowych źródeł danych](/visualstudio/data-tools/add-new-data-sources)
- [Okno źródeł danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120))
