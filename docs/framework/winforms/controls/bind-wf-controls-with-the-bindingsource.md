---
title: "Porady: powiązywanie kontrolek formularzy systemu Windows ze składnikiem BindingSource przy użyciu narzędzia Projektant"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], binding
- BindingSource component [Windows Forms], binding controls
- data binding [Windows Forms], BindingSource component
ms.assetid: 391ae170-de5c-40f8-8233-91cb2ee4683a
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 18e89d0a236d3b370c521b73dfb640a09137a5dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-windows-forms-controls-with-the-bindingsource-component-using-the-designer"></a>Porady: powiązywanie kontrolek formularzy systemu Windows ze składnikiem BindingSource przy użyciu narzędzia Projektant
Po dodaniu formantów do formularza i ustalić interfejsu użytkownika dla aplikacji, kontrolki można powiązać źródła danych tak, aby w czasie wykonywania, użytkownicy mogą zmieniać i zapisywać danych związanych z aplikacją.  
  
 Powiązanie formantu lub serii formantów w formularzach systemu Windows najłatwiej odbywa się przy użyciu <xref:System.Windows.Forms.BindingSource> formant jako mostka między formantami formularza i źródła danych.  
  
 Jeden lub więcej formantów w formularzu można powiązać danych. w poniższej procedurze <xref:System.Windows.Forms.TextBox> kontrolka jest powiązana ze źródłem danych.  
  
 Aby ukończyć tę procedurę, zakłada się, że będzie powiązać ze źródłem danych pochodzących z bazy danych. Aby uzyskać więcej informacji na temat tworzenia źródła danych z innych magazynach danych, zobacz [Dodawanie nowych źródeł danych](/visualstudio/data-tools/add-new-data-sources).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-bind-a-control-at-design-time"></a>Aby powiązać formantu w czasie projektowania  
  
1.  Przeciągnij <xref:System.Windows.Forms.TextBox> sterowania do formularza.  
  
2.  W **właściwości** okno:  
  
    1.  Rozwiń węzeł **(DataBindings)** węzła.  
  
    2.  Kliknij strzałkę obok pozycji <xref:System.Windows.Forms.TextBox.Text%2A> właściwości.  
  
         **Źródła danych** otwiera edytor typów interfejsu użytkownika.  
  
         Jeśli wcześniej skonfigurowano źródła danych dla projektu lub formularza, będą wyświetlane.  
  
3.  Kliknij przycisk **Dodaj źródło danych projektu** Aby podłączyć się do danych i Utwórz źródło danych.  
  
4.  Na **Kreator konfiguracji źródła danych** stronie powitalnej kliknij **dalej**.  
  
5.  Na **wybierz typ źródła danych** wybierz pozycję **bazy danych**.  
  
6.  Na **wybierz połączenie danych** wybierz połączenie danych z listy dostępnych połączeń. Jeśli połączenie żądanych danych nie jest dostępne wybierz **nowe połączenie** można utworzyć nowego połączenia danych.  
  
7.  Wybierz **tak, Zapisz połączenie** Aby zapisać parametry połączenia w pliku konfiguracyjnym aplikacji.  
  
8.  Wybierz obiekty bazy danych do wprowadzenia w aplikacji. W takim przypadku wybierz pola w tabeli, która będzie <xref:System.Windows.Forms.TextBox> do wyświetlenia.  
  
9. Zastąp domyślną nazwę zestawu danych, jeśli chcesz.  
  
10. Kliknij przycisk **Zakończ**.  
  
11. W **właściwości** okna, kliknij strzałkę obok pozycji <xref:System.Windows.Forms.TextBox.Text%2A> właściwość ponownie. W **źródła danych** Edytor typów interfejsu użytkownika, wybierz nazwę pola, które można powiązać <xref:System.Windows.Forms.TextBox> do.  
  
     **Źródła danych** typ interfejsu użytkownika edytora zostanie zamknięty i zestawie danych <xref:System.Windows.Forms.BindingSource> i karty tabeli specyficzne dla czy połączenia danych są dodawane do formularza.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.BindingNavigator>  
 [Dodawanie nowych źródeł danych](/visualstudio/data-tools/add-new-data-sources)  
 [Okno źródła danych](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)
