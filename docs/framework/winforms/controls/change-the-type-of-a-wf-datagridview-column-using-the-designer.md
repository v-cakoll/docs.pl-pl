---
title: "Porady: zmienianie typu formantu DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], types
- DataGridView control [Windows Forms], changing column type
- data [Windows Forms], displaying
ms.assetid: 7f994d45-600d-4190-a187-35803214b40c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1d4f27c9dcdc1bc7e00b0c809c62889b6c61cd16
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-type-of-a-windows-forms-datagridview-column-using-the-designer"></a>Porady: zmienianie typu formantu DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant
Czasami można zmienić typu kolumny, który został już dodany do formularzy systemu Windows <xref:System.Windows.Forms.DataGridView> formantu. Na przykład można zmodyfikować typy niektóre kolumny, które są generowane automatycznie, gdy powiązywanie formantu ze źródłem danych. Jest to przydatne, po kolumny zawierające kluczy obcych do wierszy w tabeli powiązanej tabeli, które można wyświetlić. W takim przypadku można zastąpić tekst kolumny pole zawierające te klucze obce z kolumnami pole kombi, zawierające bardziej zrozumiałej wartości z powiązanych tabel.  
  
 Poniższa procedura wymaga **aplikacji systemu Windows** projekt zawierający formularz <xref:System.Windows.Forms.DataGridView> formantu. Informacje o konfigurowaniu tych projektu, zobacz [jak: utworzyć projekt aplikacji systemu Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) i [porady: dodawanie formantów do formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-change-the-type-of-a-column-using-the-designer"></a>Aby zmienić typ kolumny przy użyciu narzędzia Projektant  
  
1.  Kliknij symbol tagu inteligentnego (![symbol tagu inteligentnego](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) w prawym górnym rogu <xref:System.Windows.Forms.DataGridView> kontroli, a następnie wybierz **Edytowanie kolumn**.  
  
2.  Wybierz kolumny z **wybrane kolumny** listy.  
  
3.  W **właściwości kolumny** siatki, ustaw `ColumnType` właściwości do nowego typu kolumny.  
  
    > [!NOTE]
    >  `ColumnType` Właściwość jest właściwością projektu tylko od czasu, który wskazuje klasę reprezentujący typ kolumny. Nie jest właściwością rzeczywiste zdefiniowana w klasie kolumny.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 [Porady: Tworzenie projektu aplikacji systemu Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [Porady: dodawanie formantów do formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
