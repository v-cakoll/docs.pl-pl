---
title: "Porady: powiązywanie formantu formularzy systemu Windows z typem przy użyciu narzędzia Projektant"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 5ab984b5-c2d0-4638-a572-1c84013e8746
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 215a69a47b0588e45fcc28202dce4c6210b1dfe6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type-using-the-designer"></a>Porady: powiązywanie formantu formularzy systemu Windows z typem przy użyciu narzędzia Projektant
Podczas tworzenia formantów, które współdziałają z danymi, czasami trzeba powiązanie formantu typu, a nie obiektu. Zazwyczaj należy powiązać z typem formantu w czasie projektowania, gdy dane mogą nie być dostępne, ale nadal ma formantów powiązanych z danymi do wyświetlania danych z interfejsu publicznego typu. Poniższe procedury pokazują, jak utworzyć nową <xref:System.Windows.Forms.BindingSource> który jest powiązany z typem, a następnie powiązać z jednej z właściwości typu do <xref:System.Windows.Forms.TextBox.Text%2A> właściwość <xref:System.Windows.Forms.TextBox>.  
  
### <a name="to-bind-the-bindingsource-to-a-type"></a>Aby powiązać element BindingSource typu  
  
1.  Utwórz projekt formularzy systemu Windows.  
  
     Aby uzyskać więcej informacji, zobacz [porady: Tworzenie projektu aplikacji Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  W **projekt** wyświetlić, przeciągnij <xref:System.Windows.Forms.BindingSource> składnika na formularzu.  
  
3.  W **właściwości** okna, kliknij strzałkę obok <xref:System.Windows.Forms.BindingSource.DataSource%2A> właściwości.  
  
4.  W **Edytor typów interfejsu użytkownika dla źródła danych**, kliknij przycisk **Dodaj źródło danych projektu**.  
  
5.  Na **wybierz typ źródła danych** wybierz pozycję **obiektu** i kliknij przycisk **dalej**.  
  
6.  Wybierz typ, aby powiązać:  
  
    -   Jeśli typ, który chcesz powiązać to w bieżącym projekcie, lub zestawu zawierającego typ został już dodany jako odwołanie, rozwiń węzły można znaleźć żądanego typu, a następnie wybierz go.  
  
         —lub—  
  
    -   Jeśli chcesz powiązać typu jest w innym zestawie nie jest obecnie na liście odwołań, kliknij przycisk **Dodaj odwołanie**, a następnie kliknij przycisk **projekty** kartę. Wybierz projekt, który zawiera obiektu biznesowego, a następnie kliknij przycisk **OK**. Ten projekt zostanie wyświetlony na liście zestawów, dlatego można rozwinąć węzły można znaleźć typu można mają, a następnie wybierz go.  
  
        > [!NOTE]
        >  Jeśli chcesz powiązać z typem w ramach lub zestawu Microsoft, wyczyść **Ukryj zestawy, które zaczynają się od firmy Microsoft lub System** pole wyboru.  
  
7.  Kliknij przycisk **dalej**, a następnie kliknij przycisk **Zakończ**.  
  
### <a name="to-bind-the-control-to-the-bindingsource"></a>Aby powiązać formantu BindingSource  
  
1.  Dodaj <xref:System.Windows.Forms.TextBox> do formularza.  
  
2.  W **właściwości** okna, rozwiń węzeł **(DataBindings)** węzła.  
  
3.  Kliknij strzałkę obok pozycji <xref:System.Windows.Forms.TextBox.Text%2A> właściwości.  
  
4.  W **Edytor typów interfejsu użytkownika dla źródła danych**, rozwiń węzeł <xref:System.Windows.Forms.BindingSource> dodane wcześniej, a następnie wybierz właściwość typu powiązanej chcesz powiązać <xref:System.Windows.Forms.TextBox.Text%2A> właściwość <xref:System.Windows.Forms.TextBox>.  
  
## <a name="see-also"></a>Zobacz też  
 [BindingSource — składnik](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Porady: powiązanie formantu formularzy systemu Windows z typem](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)  
 [Powiązywanie formantów z danymi w Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
