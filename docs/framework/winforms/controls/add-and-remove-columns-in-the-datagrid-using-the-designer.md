---
title: "Porady: dodawanie i usuwanie kolumn do formantu DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.DataGridViewAddColumnDialog
helpviewer_keywords:
- DataGridView control [Windows Forms], adding columns
- DataGridView control [Windows Forms], removing columns
ms.assetid: 9e709f35-0a8c-4e7e-b4c4-bacb7a834077
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4fdb57cf2134ee4f221a26db61cfdcc48dc92548
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-add-and-remove-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Porady: dodawanie i usuwanie kolumn do formantu DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant
Formularze systemu Windows <xref:System.Windows.Forms.DataGridView> formant musi zawierać kolumny, aby wyświetlić dane. Jeśli planujesz ręczne wypełnić kontrolki, należy dodać kolumny samodzielnie. Alternatywnie można powiązać formantu ze źródłem danych, który generuje i automatycznie wypełnia kolumn. Jeśli źródło danych zawiera więcej kolumn niż mają być wyświetlane, możesz usunąć zbędne kolumny.  
  
 Wykonanie poniższych procedur wymaga **aplikacji systemu Windows** projekt zawierający formularz <xref:System.Windows.Forms.DataGridView> formantu. Informacje o konfigurowaniu tych projektu, zobacz [jak: utworzyć projekt aplikacji systemu Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) i [porady: dodawanie formantów do formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-a-column-using-the-designer"></a>Aby dodać kolumnę przy użyciu narzędzia Projektant  
  
1.  Kliknij symbol tagu inteligentnego (![symbol tagu inteligentnego](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) w prawym górnym rogu <xref:System.Windows.Forms.DataGridView> kontroli, a następnie wybierz **Dodaj kolumnę**.  
  
2.  W **Dodaj kolumnę** okno dialogowe Wybierz **kolumnę z danymi** opcję i wybierz kolumnę ze źródła danych lub **niepowiązanych kolumn** opcji i skonfiguruj kolumnę przy użyciu odpowiednich polach.  
  
3.  Kliknij przycisk **Dodaj** przycisk, aby dodać kolumnę, co powoduje widoczna w projektancie, jeśli istniejące kolumny już nie wypełnia obszaru wyświetlania formantu.  
  
    > [!NOTE]
    >  Można zmodyfikować właściwości kolumny w **Edytowanie kolumn** okno dialogowe, które są dostępne z tagu formantu.  
  
### <a name="to-remove-a-column-using-the-designer"></a>Aby usunąć kolumnę przy użyciu narzędzia Projektant  
  
1.  Wybierz **Edytowanie kolumn** z tagu formantu.  
  
2.  Wybierz kolumny z **wybrane kolumny** listy.  
  
3.  Kliknij przycisk **Usuń** przycisk, aby usunąć kolumnę, co powoduje są usuwane z projektanta.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 [Porady: Tworzenie projektu aplikacji systemu Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [Instrukcje: dodawanie kontrolek do formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
