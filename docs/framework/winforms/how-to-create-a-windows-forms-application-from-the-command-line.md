---
title: 'Porady: tworzenie aplikacji formularzy systemu Windows z wiersza polecenia'
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-winforms
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, application development from command line
- Windows Forms, getting started
- Windows Forms, creating basic form
ms.assetid: 45ad3f8b-1c26-4c9f-91a9-3bb0759a47a4
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e6ddb27f724e30071be339ac753cfd85599ccd86
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-windows-forms-application-from-the-command-line"></a>Porady: tworzenie aplikacji formularzy systemu Windows z wiersza polecenia
W poniższych procedurach opisano podstawowe kroki, które należy wykonać w celu tworzenia i uruchamiania aplikacji Windows Forms z wiersza polecenia. Brak kompleksową obsługę tych procedur w programie Visual Studio.  Zobacz też [wskazówki: Tworzenie prostego formularza systemu Windows](http://msdn.microsoft.com/library/z9w2f38k\(v=vs.100\)).  
  
## <a name="procedure"></a>Procedura  
  
#### <a name="to-create-the-form"></a>Aby utworzyć formularz  
  
1.  W pliku kodu pusta wpisz następujące importu lub przy użyciu instrukcji:  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2.  Deklarowanie klasy o nazwie `Form1` dziedziczącego z klasy formularza.  
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3.  Tworzenie domyślnego konstruktora dla `Form1`.  
  
     Więcej kodu zostaną dodane do konstruktora w następnej procedurze.  
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4.  Dodaj `Main` metodę do klasy.  
  
    1.  Zastosuj <xref:System.STAThreadAttribute> do `Main` metodę, aby określić aplikacji formularzy systemu Windows jest pojedynczy komórek wielowątkowych.  
  
    2.  Wywołanie <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> umożliwiają wygląd systemu Windows XP, do aplikacji.  
  
    3.  Utwórz wystąpienie formularza i uruchom go.  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### <a name="to-compile-and-run-the-application"></a>Aby skompilować i uruchomić aplikację  
  
1.  W wierszu polecenia środowiska .NET Framework, przejdź do katalogu utworzonego `Form1` klasy.  
  
2.  Kompiluj formularza.  
  
    -   Jeśli używasz języka C#, wpisz:`csc form1.cs`  
  
         `-or-`  
  
    -   Jeśli używasz programu Visual Basic, wpisz:`vbc form1.vb /r:system.dll,system.drawing.dll,system.windows.forms.dll`  
  
3.  W wierszu polecenia wpisz:`Form1.exe`  
  
## <a name="adding-a-control-and-handling-an-event"></a>Dodawanie formantu i obsługi zdarzeń  
 Poprzednie kroki procedury przedstawionej tylko tworzenie podstawowych formularza systemu Windows, który kompiluje i uruchamia. Następnej procedury opisano, jak utworzyć i dodać kontrolkę w formularzu i obsługi zdarzeń dla formantu. Aby uzyskać więcej informacji dotyczących formantów, można dodać do formularzy systemu Windows, zobacz [formantów formularzy systemu Windows](../../../docs/framework/winforms/controls/index.md).  
  
 Oprócz opis sposobu tworzenia aplikacji formularzy systemu Windows, należy pamiętać programowania opartego na zdarzeniach i sposób obsługi danych wejściowych użytkownika. Aby uzyskać więcej informacji, zobacz [tworzenie obsługi zdarzeń w formularzach systemu Windows](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md), i [obsługi danych wejściowych użytkownika](../../../docs/framework/winforms/controls/handling-user-input.md)  
  
#### <a name="to-declare-a-button-control-and-handle-its-click-event"></a>Aby zadeklarować formantu przycisku i obsługiwać jego Zdarzenie kliknięcia  
  
1.  Deklarowanie kontrolkę przycisku o nazwie `button1`.  
  
2.  W konstruktorze, utworzyć przycisku i ustawić jej <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> i <xref:System.Windows.Forms.Control.Text%2A> właściwości.  
  
3.  Dodawanie przycisku do formularza.  
  
     Poniższy przykład kodu pokazuje, jak można zadeklarować formantu przycisku.  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4.  Tworzenie metody, aby obsłużyć <xref:System.Windows.Forms.Control.Click> zdarzenia dla przycisku.  
  
5.  W obsłudze zdarzeń, kliknij przycisk Wyświetl <xref:System.Windows.Forms.MessageBox> z komunikatem "Hello World".  
  
     Poniższy przykład kodu pokazuje sposób obsługi przycisku Zdarzenie kliknięcia formantu.  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6.  Skojarz <xref:System.Windows.Forms.Control.Click> zdarzeń przy użyciu metody tworzenia.  
  
     Poniższy przykład kodu pokazuje, jak skojarzone zdarzenie z metodą.  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7.  Kompilowanie i uruchamianie aplikacji, zgodnie z opisem w poprzedniej procedurze.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu jest pełny przykład z poprzedniej procedury.  
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Aby skompilować kod, postępuj zgodnie z instrukcjami procedury postępowania opisujących sposób skompilować i uruchomić aplikację.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Form>  
 <xref:System.Windows.Forms.Control>  
 [Zmienianie wyglądu formularzy systemu Windows](../../../docs/framework/winforms/changing-the-appearance-of-windows-forms.md)  
 [Rozszerzanie aplikacji Windows Forms](../../../docs/framework/winforms/advanced/index.md)  
 [Wprowadzenie do formularzy systemu Windows](../../../docs/framework/winforms/getting-started-with-windows-forms.md)
