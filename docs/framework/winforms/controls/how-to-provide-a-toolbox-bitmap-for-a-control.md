---
title: 'Porady: dostarczanie mapy bitowej przybornika dla formantu'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Toolbox [Windows Forms], adding bitmaps for custom controls
- custom controls [Windows Forms], Toolbox bitmaps
- bitmaps [Windows Forms], custom controls
ms.assetid: 0ed0840a-616d-41ba-a27d-3573241932ad
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5d34cbb88805d9c034df61aba89ebd7bb224b1da
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-provide-a-toolbox-bitmap-for-a-control"></a>Porady: dostarczanie mapy bitowej przybornika dla formantu
Jeśli chcesz mieć specjalne ikon dla formantu są wyświetlane w **przybornika**, określonego obrazu można określić za pomocą <xref:System.Drawing.ToolboxBitmapAttribute>. Ta klasa jest *atrybutu*, specjalny rodzaj klasy można dołączyć do innych klas. Aby uzyskać więcej informacji na temat atrybutów, zobacz [NOT IN kompilacji: Omówienie atrybutów w języku Visual Basic](http://msdn.microsoft.com/library/0d0cff64-892d-4f57-83bd-bef388553d4f) w języku Visual Basic i [atrybuty](http://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205) Visual C#.  
  
 Przy użyciu <xref:System.Drawing.ToolboxBitmapAttribute>, można określić ciąg, który określa ścieżkę i nazwę pliku mapy bitowej pikseli 16 na 16. Ta mapa bitowa pojawia się obok formantu podczas dodawania do **przybornika**. Można również określić <xref:System.Type>, w którym to przypadku mapy bitowej skojarzony z danym typem jest załadowany. Jeśli możesz określić ich obu <xref:System.Type> i ciąg, formantu wyszukuje zasób obrazu o nazwie określonej przez parametr ciągu w zestaw zawierający typ określony przez <xref:System.Type> parametru.  
  
### <a name="to-specify-a-toolbox-bitmap-for-your-control"></a>Aby określić mapy bitowej przybornika dla formantu  
  
1.  Dodaj <xref:System.Drawing.ToolboxBitmapAttribute> deklaracji klasy z formantu przed `Class` słów kluczowych w języku visual Basic i powyżej deklaracji klasy Visual C#.  
  
    ```vb  
    ' Specifies the bitmap associated with the Button type.  
    <ToolboxBitmap(GetType(Button))> Class MyControl1  
    ' Specifies a bitmap file.  
    End Class  
    <ToolboxBitmap("C:\Documents and Settings\Joe\MyPics\myImage.bmp")> _  
       Class MyControl2  
    End Class  
    ' Specifies a type that indicates the assembly to search, and the name   
    ' of an image resource to look for.  
    <ToolboxBitmap(GetType(MyControl), "MyControlBitmap")> Class MyControl  
    End Class  
    ```  
  
    ```csharp  
    // Specifies the bitmap associated with the Button type.  
    [ToolboxBitmap(typeof(Button))]  
    class MyControl1 : UserControl  
    {  
    }  
    // Specifies a bitmap file.  
    [ToolboxBitmap(@"C:\Documents and Settings\Joe\MyPics\myImage.bmp")]  
    class MyControl2 : UserControl  
    {  
    }  
    // Specifies a type that indicates the assembly to search, and the name   
    // of an image resource to look for.  
    [ToolboxBitmap(typeof(MyControl), "MyControlBitmap")]  
    class MyControl : UserControl  
    {  
    }  
    ```  
  
2.  Skompiluj ponownie projekt.  
  
    > [!NOTE]
    >  Nie ma mapy bitowej przybornika dla formantów wygenerowany automatycznie i składniki. Aby wyświetlić mapę bitową, należy ponownie załadować formantu przy użyciu **wybierz elementy przybornika** okno dialogowe. Aby uzyskać więcej informacji, zobacz [wskazówki: automatyczne zapełnianie przybornika składnikami niestandardowe](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing.ToolboxBitmapAttribute>  
 [Przewodnik: automatyczne zapełnianie Przybornika składnikami niestandardowymi](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 [Opracowywanie kontrolek formularzy Windows Forms w czasie projektowania](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [Atrybuty (Visual Basic)](~/docs/visual-basic/language-reference/attributes.md)  
 [Atrybuty](http://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)
