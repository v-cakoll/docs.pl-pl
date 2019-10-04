---
title: 'Instrukcje: Tworzenie aplikacji Windows Forms z poziomu wiersza polecenia'
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
ms.openlocfilehash: da7fdab1cf67ffd47acb75533fcfdb89664c86d3
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834805"
---
# <a name="how-to-create-a-windows-forms-application-from-the-command-line"></a>Instrukcje: Tworzenie aplikacji Windows Forms z poziomu wiersza polecenia

W poniższych procedurach opisano podstawowe kroki, które należy wykonać w celu utworzenia i uruchomienia aplikacji Windows Forms z poziomu wiersza polecenia. Istnieją rozległe wsparcie dla tych procedur w programie Visual Studio.  Zobacz również [Przewodnik: hosting formantu Windows Forms w WPF](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).
  
## <a name="procedure"></a>Procedura  
  
#### <a name="to-create-the-form"></a>Aby utworzyć formularz  
  
1. W pustym pliku kodu wpisz następujące instrukcje `Imports` lub `using`:  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2. Zadeklaruj klasę o nazwie `Form1`, która dziedziczy z klasy form:
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3. Utwórz Konstruktor bez parametrów dla `Form1`.
  
     Do konstruktora zostanie dodany kod w kolejnej procedurze.
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4. Dodaj metodę `Main` do klasy.
  
    1. Zastosuj <xref:System.STAThreadAttribute> do metody C# `Main`, aby określić, że aplikacja Windows Forms jest apartamentem jednowątkowym. (Atrybut nie jest konieczny w Visual Basic, ponieważ aplikacje Windows Forms opracował z Visual Basic domyślnie korzystają z jednowątkowego modelu apartamentu).  
  
    2. Wywołaj <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>, aby zastosować style systemu operacyjnego do aplikacji.  
  
    3. Utwórz wystąpienie formularza i uruchom je.  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### <a name="to-compile-and-run-the-application"></a>Aby skompilować i uruchomić aplikację  
  
1. W wierszu polecenia .NET Framework przejdź do katalogu, w którym została utworzona Klasa `Form1`.  
  
2. Kompiluj formularz.  
  
    - Jeśli używasz programu C#, wpisz: `csc form1.cs`  
  
         `-or-`  
  
    - Jeśli używasz Visual Basic, wpisz: `vbc form1.vb`  
  
3. W wierszu polecenia wpisz: `Form1.exe`  
  
## <a name="adding-a-control-and-handling-an-event"></a>Dodawanie kontrolki i obsługa zdarzenia

Poprzednie kroki procedury pokazują, jak po prostu utworzyć podstawowy formularz systemu Windows, który kompiluje i uruchamia. Kolejna procedura pokazuje, jak utworzyć i dodać kontrolkę do formularza i obsłużyć zdarzenie dla kontrolki. Aby uzyskać więcej informacji o kontrolkach, które można dodać do Windows Forms, zobacz [Windows Forms Controls](./controls/index.md).
  
 Oprócz zrozumienia sposobu tworzenia aplikacji Windows Forms, należy zrozumieć Programowanie oparte na zdarzeniach i sposób obsługi danych wejściowych użytkownika. Aby uzyskać więcej informacji, zobacz [Tworzenie programów obsługi zdarzeń w Windows Forms](creating-event-handlers-in-windows-forms.md)i [Obsługa danych wejściowych użytkownika](./controls/handling-user-input.md)  
  
#### <a name="to-declare-a-button-control-and-handle-its-click-event"></a>Aby zadeklarować formant Button i obsłużyć jego zdarzenie kliknięcia  
  
1. Zadeklaruj kontrolkę przycisku o nazwie `button1`.  
  
2. W konstruktorze Utwórz przycisk i ustaw jego właściwości <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> i <xref:System.Windows.Forms.Control.Text%2A>.  
  
3. Dodaj przycisk do formularza.  
  
     Poniższy przykład kodu demonstruje, jak zadeklarować formant Button:
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4. Utwórz metodę, aby obsłużyć <xref:System.Windows.Forms.Control.Click> zdarzenia dla przycisku.  
  
5. W obsłudze zdarzeń kliknięcia Wyświetl <xref:System.Windows.Forms.MessageBox> z komunikatem "Hello world".  
  
     Poniższy przykład kodu demonstruje, jak obsłużyć zdarzenie kliknięcia kontrolki przycisku:
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6. Skojarz zdarzenie <xref:System.Windows.Forms.Control.Click> z utworzoną metodą.  
  
     Poniższy przykład kodu demonstruje, jak skojarzyć zdarzenie z metodą.  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7. Skompiluj i uruchom aplikację zgodnie z opisem w poprzedniej procedurze.  
  
## <a name="example"></a>Przykład  
 
Poniższy przykład kodu jest kompletnym przykładem z poprzednich procedur:
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Control>
- [Zmienianie wyglądu formularzy Windows Forms](changing-the-appearance-of-windows-forms.md)
- [Rozszerzanie aplikacji Windows Forms](./advanced/index.md)
- [Wprowadzenie do formularzy Windows Forms](getting-started-with-windows-forms.md)
