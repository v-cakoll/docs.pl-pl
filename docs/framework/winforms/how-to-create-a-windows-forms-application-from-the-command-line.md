---
title: Tworzenie aplikacji Windows Forms z wiersza polecenia
titleSuffix: ''
ms.date: 03/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, application development from command line
- Windows Forms, getting started
- Windows Forms, creating basic form
ms.assetid: 45ad3f8b-1c26-4c9f-91a9-3bb0759a47a4
ms.openlocfilehash: 7bd3add526a6b60d628b05d46eca22ce407c36b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181989"
---
# <a name="how-to-create-a-windows-forms-application-from-the-command-line"></a>Jak: Tworzenie aplikacji Windows Forms z wiersza polecenia

W poniższych procedurach opisano podstawowe kroki, które należy wykonać, aby utworzyć i uruchomić aplikację Windows Forms z wiersza polecenia. Istnieje obszerna obsługa tych procedur w programie Visual Studio.  Zobacz też [Przewodnik: Hostowanie formantu formularzy systemu Windows w programie WPF](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).
  
## <a name="procedure"></a>Procedura  
  
#### <a name="to-create-the-form"></a>Aby utworzyć formularz  
  
1. W pustym pliku kodu `Imports` wpisz `using` następujące lub instrukcje:  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2. Deklaruj klasę o nazwie, `Form1` która dziedziczy z klasy Form:
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3. Utwórz konstruktor `Form1`bez parametrów dla .
  
     Do konstruktora dodasz więcej kodu w kolejnej procedurze.
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4. Dodaj `Main` metodę do klasy.
  
    1. Zastosuj <xref:System.STAThreadAttribute> do C# `Main` metoda, aby określić aplikacji Windows Forms jest jednowątkowy apartament. (Atrybut nie jest konieczne w języku Visual Basic, ponieważ windows formularze aplikacje opracowane za pomocą języka Visual Basic używać jednowątkowego modelu mieszkania domyślnie.)  
  
    2. Wywołanie, <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> aby zastosować style systemu operacyjnego do aplikacji.  
  
    3. Utwórz wystąpienie formularza i uruchom je.  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### <a name="to-compile-and-run-the-application"></a>Aby skompilować i uruchomić aplikację  
  
1. W wierszu polecenia .NET Framework przejdź do `Form1` katalogu utworzonego klasy.  
  
2. Skompiluj formularz.  
  
    - Jeśli używasz języka C#, wpisz:`csc form1.cs`  
  
         `-or-`  
  
    - Jeśli używasz języka Visual Basic, wpisz:`vbc form1.vb`  
  
3. W wierszu polecenia wpisz:`Form1.exe`  
  
## <a name="adding-a-control-and-handling-an-event"></a>Dodawanie formantu i obsługa zdarzenia

W poprzednich krokach procedury pokazano, jak po prostu utworzyć podstawowy formularz systemu Windows, który kompiluje i uruchamia. Następna procedura pokaże, jak utworzyć i dodać formant do formularza i obsługi zdarzenia dla formantu. Aby uzyskać więcej informacji na temat formantów, które można dodać do formularzy systemu Windows, zobacz [Formanty formularzy systemu Windows](./controls/index.md).
  
 Oprócz zrozumienia sposobu tworzenia aplikacji Windows Forms, należy zrozumieć programowania opartego na zdarzeniach i jak obsługiwać dane wejściowe użytkownika. Aby uzyskać więcej informacji, zobacz [Tworzenie programów obsługi zdarzeń w formularzach systemu Windows](creating-event-handlers-in-windows-forms.md)i obsługa danych [wejściowych użytkownika](./controls/handling-user-input.md)  
  
#### <a name="to-declare-a-button-control-and-handle-its-click-event"></a>Aby zadeklarować kontrolkę przycisku i obsłużyć jego zdarzenie kliknięcia  
  
1. Deklarowanie formantu przycisku o nazwie `button1`.  
  
2. W konstruktorze utwórz przycisk <xref:System.Windows.Forms.Control.Size%2A> <xref:System.Windows.Forms.Control.Location%2A> i <xref:System.Windows.Forms.Control.Text%2A> ustaw jego , i właściwości.  
  
3. Dodaj przycisk do formularza.  
  
     Poniższy przykład kodu pokazuje, jak zadeklarować formant przycisku:
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4. Utwórz metodę obsługi <xref:System.Windows.Forms.Control.Click> zdarzenia dla przycisku.  
  
5. W programie obsługi zdarzeń <xref:System.Windows.Forms.MessageBox> click wyświetl komunikat "Hello World".  
  
     Poniższy przykład kodu pokazuje, jak obsługiwać zdarzenie kliknięcia formantu przycisku:
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6. Skojarz <xref:System.Windows.Forms.Control.Click> zdarzenie z utworzoną metodą.  
  
     Poniższy przykład kodu pokazuje, jak skojarzyć zdarzenie z metodą.  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7. Skompiluj i uruchom aplikację zgodnie z opisem w poprzedniej procedurze.  
  
## <a name="example"></a>Przykład  

Poniższy przykład kodu jest kompletnym przykładem z poprzednich procedur:
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Control>
- [Zmienianie wyglądu formularzy Windows Forms](changing-the-appearance-of-windows-forms.md)
- [Rozszerzanie aplikacji Windows Forms](./advanced/index.md)
- [Wprowadzenie do formularzy systemu Windows](getting-started-with-windows-forms.md)
