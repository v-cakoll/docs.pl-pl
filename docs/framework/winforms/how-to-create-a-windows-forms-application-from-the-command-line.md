---
title: 'Instrukcje: Tworzenie aplikacji Windows Forms z wiersza polecenia'
ms.date: 03/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, application development from command line
- Windows Forms, getting started
- Windows Forms, creating basic form
ms.assetid: 45ad3f8b-1c26-4c9f-91a9-3bb0759a47a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce97089ec71fc910079910957e784605387f3e06
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61966884"
---
# <a name="how-to-create-a-windows-forms-application-from-the-command-line"></a>Instrukcje: Tworzenie aplikacji Windows Forms z wiersza polecenia
W poniższych procedurach opisano podstawowe kroki, które należy wykonać, aby utworzyć i uruchomić aplikację Windows Forms z wiersza polecenia. Brak kompleksową obsługę tych procedur w programie Visual Studio.  Zobacz też [instruktażu: Kontrolki hostingu Windows formularzy na platformie WPF](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).  
  
## <a name="procedure"></a>Procedura  
  
#### <a name="to-create-the-form"></a>Aby utworzyć formularz  
  
1. W pliku kodu pusty należy wpisać następujący import lub używając instrukcji:  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2. Zadeklaruj klasę o nazwie `Form1` która dziedziczy z klasy formularza.  
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3. Tworzenie domyślnego konstruktora dla `Form1`.  
  
     Dodasz więcej kodu do konstruktora, aby w kolejnej procedurze.  
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4. Dodaj `Main` metodę do klasy.  
  
    1. Zastosuj <xref:System.STAThreadAttribute> do języka C# `Main` metodę, aby określić aplikację Windows Forms jest jednowątkowym apartamentem. (Ten atrybut nie jest niezbędne w języku Visual Basic, ponieważ Windows forms aplikacji opracowanych przy użyciu języka Visual Basic modelu apartamentem jednowątkowym domyślnie).  
  
    2. Wywołaj <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> na stosowanie stylów systemu operacyjnego do Twojej aplikacji.  
  
    3. Utwórz wystąpienie obiektu do formularza i uruchom go.  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### <a name="to-compile-and-run-the-application"></a>Aby skompilować i uruchomić aplikację  
  
1. W wierszu polecenia środowiska .NET Framework, przejdź do katalogu, który został utworzony `Form1` klasy.  
  
2. Skompiluj formularza.  
  
    - Jeśli używasz języka C#, wpisz: `csc form1.cs`  
  
         `-or-`  
  
    - Jeśli używasz języka Visual Basic, wpisz: `vbc form1.vb`  
  
3. W wierszu polecenia wpisz polecenie: `Form1.exe`  
  
## <a name="adding-a-control-and-handling-an-event"></a>Dodawanie kontrolki i obsługa zdarzeń  
 W poprzednich krokach procedury przedstawione instrukcje po prostu Utwórz podstawowej postaci Windows, który kompiluje i uruchamia. Następna procedura pokazują sposób tworzenia i dodawanie formantu do formularza i obsługiwać zdarzenia formantu. Aby uzyskać więcej informacji na temat formantów, można dodać do formularzy Windows Forms, zobacz [kontrolek formularzy Windows Forms](./controls/index.md).  
  
 Oprócz zapoznania się jak tworzyć aplikacje Windows Forms, należy zrozumieć Programowanie oparte na zdarzeniach i sposób obsługi danych wejściowych użytkownika. Aby uzyskać więcej informacji, zobacz [tworzenie obsługi zdarzeń w formularzach Windows Forms](creating-event-handlers-in-windows-forms.md), i [obsługi danych wejściowych użytkownika](./controls/handling-user-input.md)  
  
#### <a name="to-declare-a-button-control-and-handle-its-click-event"></a>Aby zadeklarować formant przycisku i obsługiwać jego zdarzenia kliknięcia  
  
1. Zadeklaruj formant przycisku o nazwie `button1`.  
  
2. W konstruktorze, należy utworzyć przycisk i ustaw jego <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> i <xref:System.Windows.Forms.Control.Text%2A> właściwości.  
  
3. Przycisk Dodaj do formularza.  
  
     Poniższy przykład kodu pokazuje sposób deklarowania formant przycisku.  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4. Utwórz metodę, aby obsłużyć <xref:System.Windows.Forms.Control.Click> zdarzeń dla przycisku.  
  
5. W procedurze obsługi zdarzeń kliknij przycisk Wyświetl <xref:System.Windows.Forms.MessageBox> z komunikatem "Hello World".  
  
     Poniższy przykład kodu demonstruje sposób obsługi przycisku kontrolki kliknij zdarzenie.  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6. Skojarz <xref:System.Windows.Forms.Control.Click> zdarzeń za pomocą metody tworzenia.  
  
     Poniższy przykład kodu pokazuje, jak skojarzyć zdarzenia przy użyciu metody.  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7. Skompiluj i uruchom aplikację zgodnie z opisem w poprzedniej procedurze.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu jest kompletny przykład z poprzednich procedur.  
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
- Aby skompilować ten kod, postępuj zgodnie z instrukcjami procedury postępowania, które opisują sposób skompilować i uruchomić aplikację.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Control>
- [Zmienianie wyglądu formularzy Windows Forms](changing-the-appearance-of-windows-forms.md)
- [Rozszerzanie aplikacji Windows Forms](./advanced/index.md)
- [Wprowadzenie do formularzy Windows Forms](getting-started-with-windows-forms.md)
