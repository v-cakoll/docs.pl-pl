---
title: 'Instrukcje: Powiązywanie kontrolek formularzy Windows ze składnikiem BindingSource przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding
- BindingSource component [Windows Forms], binding controls
- data binding [Windows Forms], BindingSource component
ms.assetid: 391ae170-de5c-40f8-8233-91cb2ee4683a
ms.openlocfilehash: 1a9baa5a602edd0ef91ef7dff5cdc42832bd7532
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54633324"
---
# <a name="how-to-bind-windows-forms-controls-with-the-bindingsource-component-using-the-designer"></a>Instrukcje: Powiązywanie kontrolek formularzy Windows ze składnikiem BindingSource przy użyciu narzędzia Projektant
Po dodać formanty do formularza i określić interfejsu użytkownika dla aplikacji, formanty można powiązać ze źródłem danych, tak, aby w czasie wykonywania, użytkownicy mogą zmienić i zapisać dane związane z aplikacją.  
  
 Powiązania kontroli lub szeregu formantów w formularzach Windows Forms najłatwiej odbywa się przy użyciu <xref:System.Windows.Forms.BindingSource> kontroli jako Most między kontrolek w formularzu i źródła danych.  
  
 Co najmniej jedną kontrolkę w formularzu można powiązać z danych. w poniższej procedurze <xref:System.Windows.Forms.TextBox> kontrolka jest powiązana ze źródłem danych.  
  
 Aby ukończyć tę procedurę, zakłada się, czy zostaną powiązane ze źródłem danych pochodzących z bazy danych. Aby uzyskać więcej informacji na temat tworzenia źródeł danych z innych magazynów danych, zobacz [dodasz nowe źródła danych](/visualstudio/data-tools/add-new-data-sources).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-bind-a-control-at-design-time"></a>Aby powiązać formant w czasie projektowania  
  
1.  Przeciągnij <xref:System.Windows.Forms.TextBox> formantu do formularza.  
  
2.  W **właściwości** okna:  
  
    1.  Rozwiń **(powiązania danych)** węzła.  
  
    2.  Kliknij strzałkę obok pozycji <xref:System.Windows.Forms.TextBox.Text%2A> właściwości.  
  
         **DataSource** zostanie otwarty Edytor typów interfejsu użytkownika.  
  
         Jeśli wcześniej skonfigurowano źródła danych dla projektu lub formularza, pojawi się.  
  
3.  Kliknij przycisk **Dodaj źródło danych projektu** do nawiązywania połączeń z danymi i Utwórz źródło danych.  
  
4.  Na **Kreatora konfiguracji źródła danych** strona powitalna, kliknij przycisk **dalej**.  
  
5.  Na **wybierz typ źródła danych** wybierz opcję **bazy danych**.  
  
6.  Na **wybierz połączenie danych** wybierz połączenie danych z listy dostępnych połączeń. Jeśli żądane połączenie danych nie jest dostępna, wybierz **nowe połączenie** Aby utworzyć nowe połączenie danych.  
  
7.  Wybierz **tak, Zapisz połączenie** można zapisać parametry połączenia w pliku konfiguracyjnym aplikacji.  
  
8.  Wybierz obiekty bazy danych w celu dostosowania do aplikacji. W takim przypadku wybierz pola w tabeli, które chcieliby <xref:System.Windows.Forms.TextBox> do wyświetlenia.  
  
9. Zastąp domyślną nazwę zestawu danych, jeśli chcesz.  
  
10. Kliknij przycisk **Zakończ**.  
  
11. W **właściwości** okna, kliknij strzałkę obok pozycji <xref:System.Windows.Forms.TextBox.Text%2A> właściwość ponownie. W **DataSource** Edytor typów interfejsu użytkownika, wybierz nazwę pola, które można powiązać <xref:System.Windows.Forms.TextBox> do.  
  
     **DataSource** typ interfejsu użytkownika edytora zostanie zamknięty i zestaw danych <xref:System.Windows.Forms.BindingSource> karty tabeli specyficzne dla, połączenia danych są dodawane do formularza.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.BindingNavigator>
- [Dodawanie nowych źródeł danych](/visualstudio/data-tools/add-new-data-sources)
- [Okno źródeł danych](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)
