---
title: "Porady: stosowanie modyfikatorów i właściwości „GenerateMember\""
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
f1_keywords:
- Designer_GenerateMember
- Designer_Modifiers
helpviewer_keywords:
- base forms
- inheritance [Windows Forms], forms
- inherited forms [Windows Forms], Windows Forms
- inherited forms
- form inheritance
- Windows Forms, inheritance
ms.assetid: 3381a5e4-e1a3-44e2-a765-a0b758937b85
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f11595daac74ceb76c5d017af015d5523506bdf3
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-use-the-modifiers-and-generatemember-properties"></a>Porady: stosowanie modyfikatorów i właściwości „GenerateMember"
Po umieszczeniu składnika w formularzu systemu Windows, dwie właściwości są udostępniane przez środowisko projektowania: `GenerateMember` i `Modifiers`. `GenerateMember` Właściwość określa, gdy projektant formularzy systemu Windows generuje zmienną członkowską dla składnika. `Modifiers` Właściwość jest modyfikator dostępu przypisany do tej zmiennej elementu członkowskiego. Jeśli wartość `GenerateMember` właściwość jest `false`, wartość `Modifiers` właściwość nie ma wpływu.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-specify-whether-a-component-is-a-member-of-the-form"></a>Aby określić, czy składnik jest elementem członkowskim formularza  
  
1.  Otwórz formularza w narzędziu Projektant dla formularzy systemu Windows.  
  
2.  Otwórz **przybornika**i na formularzu, należy umieścić trzy <xref:System.Windows.Forms.Button> kontrolki.  
  
3.  Ustaw `GenerateMember` i `Modifiers` właściwości dla każdego <xref:System.Windows.Forms.Button> kontroli zgodnie z poniższą tabelą.  
  
    |Nazwa przycisku|Wartość "generatemember"|Wartość modyfikatorów|  
    |-----------------|--------------------------|---------------------|  
    |`button1`|`true`|`private`|  
    |`button2`|`true`|`protected`|  
    |`button3`|`false`|Brak zmian|  
  
4.  Skompiluj rozwiązanie.  
  
5.  W **Eksploratora rozwiązań**, kliknij przycisk **Pokaż wszystkie pliki** przycisku.  
  
6.  Otwórz **Form1** węzeł, a następnie w **edytora kodu**, otwórz **Form1.Designer.vb** lub **Form1.Designer.cs** pliku. Ten plik zawiera kod emitowane przez projektanta formularzy systemu Windows.  
  
7.  Znajdź deklaracje trzech przycisków. Poniższy przykładowy kod przedstawia różnice określony przez `GenerateMember` i `Modifiers` właściwości.  
  
     [!code-csharp[System.Windows.Forms.GenerateMember#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.GenerateMember#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.GenerateMember#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.GenerateMember#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#2)]  
  
> [!NOTE]
>  Domyślnie przypisuje Projektant formularzy systemu Windows `private` (`Friend` w języku Visual Basic) modyfikator do kontenera formantów, takich jak <xref:System.Windows.Forms.Panel>. Jeśli podstawowym <xref:System.Windows.Forms.UserControl> lub <xref:System.Windows.Forms.Form> ma formantu kontenera, nie będzie akceptować nowych elementów podrzędnych w formularzach i formanty dziedziczone. Rozwiązanie to zmienić modyfikator do formantu kontenera podstawowej `protected` lub `public`.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Button>  
 [Formularze Windows Forms — dziedziczenie wizualizacji](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)  
 [Przewodnik: demonstrowanie dziedziczenia wizualizacji](../../../../docs/framework/winforms/advanced/walkthrough-demonstrating-visual-inheritance.md)  
 [Instrukcje: dziedziczenie formularzy Windows Forms](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)
