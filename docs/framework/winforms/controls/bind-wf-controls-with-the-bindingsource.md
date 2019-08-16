---
title: 'Instrukcje: wiązanie kontrolek formularzy systemu Windows ze składnikiem BindingSource przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding
- BindingSource component [Windows Forms], binding controls
- data binding [Windows Forms], BindingSource component
ms.assetid: 391ae170-de5c-40f8-8233-91cb2ee4683a
ms.openlocfilehash: 180fafa9ace5927fd84ec5dc0a1b2a342f771efd
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040016"
---
# <a name="how-to-bind-windows-forms-controls-with-the-bindingsource-component-using-the-designer"></a>Instrukcje: wiązanie kontrolek formularzy systemu Windows ze składnikiem BindingSource przy użyciu narzędzia Projektant
Po dodaniu kontrolek do formularza i określeniu interfejsu użytkownika dla aplikacji można powiązać kontrolki ze źródłem danych, aby w czasie wykonywania użytkownicy mogli zmieniać i zapisywać dane związane z aplikacją.

 Powiązanie kontrolki lub serii formantów w Windows Forms jest najłatwiej realizowane przy użyciu <xref:System.Windows.Forms.BindingSource> formantu jako mostka między kontrolkami w formularzu a źródłem danych.

 Co najmniej jedna kontrolka w formularzu może być powiązana z danymi; w poniższej procedurze <xref:System.Windows.Forms.TextBox> formant jest powiązany ze źródłem danych.

 Aby wykonać tę procedurę, zakłada się, że zostanie utworzone powiązanie ze źródłem danych uzyskanym z bazy danych. Aby uzyskać więcej informacji na temat tworzenia źródeł danych z innych magazynów danych, zobacz [Dodawanie nowych źródeł danych](/visualstudio/data-tools/add-new-data-sources).

## <a name="to-bind-a-control-at-design-time"></a>Aby powiązać formant w czasie projektowania

1. <xref:System.Windows.Forms.TextBox> Przeciągnij kontrolkę do formularza.

2. W oknie **Właściwości** :

    1. Rozwiń węzeł **(DataBindings)** .

    2. Kliknij strzałkę obok <xref:System.Windows.Forms.TextBox.Text%2A> właściwości.

         Zostanie otwarty Edytor typów interfejsu użytkownika **źródła danych** .

         Jeśli źródło danych zostało wcześniej skonfigurowane dla projektu lub formularza, pojawi się.

3. Kliknij pozycję **Dodaj źródło danych projektu** , aby połączyć się z danymi i utworzyć źródło danych.

4. Na stronie powitalnej **Kreatora konfiguracji źródła danych** kliknij przycisk **dalej**.

5. Na stronie **Wybierz typ źródła danych** wybierz pozycję **baza danych**.

6. Na stronie **Wybierz połączenie danych** wybierz połączenie danych z listy dostępnych połączeń. Jeśli żądane połączenie danych nie jest dostępne wybierz pozycję **nowe połączenie** , aby utworzyć nowe połączenie danych.

7. Wybierz opcję **tak, Zapisz połączenie,** aby zapisać parametry połączenia w pliku konfiguracyjnym aplikacji.

8. Wybierz obiekty bazy danych do dołączenia do aplikacji. W takim przypadku wybierz pole w tabeli, które <xref:System.Windows.Forms.TextBox> ma być wyświetlane.

9. W razie potrzeby Zastąp domyślną nazwę zestawu danych.

10. Kliknij przycisk **Zakończ**.

11. W oknie **Właściwości** kliknij strzałkę obok tej <xref:System.Windows.Forms.TextBox.Text%2A> właściwości. W edytorze typów interfejsu użytkownika **źródła danych** wybierz nazwę pola, do którego <xref:System.Windows.Forms.TextBox> ma zostać utworzone powiązanie.

     Edytor typów interfejsu użytkownika **źródła** danych zostanie zamknięty, a zestaw <xref:System.Windows.Forms.BindingSource> danych, a karta tabeli dla tego połączenia danych jest dodawana do formularza.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.BindingNavigator>
- [Dodawanie nowych źródeł danych](/visualstudio/data-tools/add-new-data-sources)
- [Okno źródeł danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120))
