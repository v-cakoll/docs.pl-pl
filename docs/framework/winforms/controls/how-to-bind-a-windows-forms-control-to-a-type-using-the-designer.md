---
title: 'Porady: powiązywanie formantu formularzy systemu Windows z typem przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 5ab984b5-c2d0-4638-a572-1c84013e8746
ms.openlocfilehash: 33df9e050dd8c2b3ace8ff89cbd5939b538fcd95
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44098345"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type-using-the-designer"></a>Porady: powiązywanie formantu formularzy systemu Windows z typem przy użyciu narzędzia Projektant
Podczas tworzenia formantów, które współdziałają z danymi, czasami konieczne Powiąż formant typu, a nie obiekt. Zazwyczaj konieczne powiązanie z typem formantu w czasie projektowania, gdy dane nie mogą być dostępne, ale nadal chcesz formantów powiązanych z danymi do wyświetlania danych z interfejsu publicznego typu. Poniższe procedury pokazują, jak utworzyć nową <xref:System.Windows.Forms.BindingSource> oznacza to powiązane z typem, a następnie jak powiązać z jednej z właściwości typu do <xref:System.Windows.Forms.TextBox.Text%2A> właściwość <xref:System.Windows.Forms.TextBox>.  
  
### <a name="to-bind-the-bindingsource-to-a-type"></a>Aby powiązać BindingSource — typ  
  
1.  Utwórz projekt Windows Forms (**pliku** > **New** > **projektu** > **Visual C#** lub **Języka Visual Basic** > **Classic Desktop** > **Windows Forms aplikacji**).  
  
2.  W **projektowania** wyświetlić, przeciągnij <xref:System.Windows.Forms.BindingSource> składnika do formularza.  
  
3.  W **właściwości** okna, kliknij strzałkę obok <xref:System.Windows.Forms.BindingSource.DataSource%2A> właściwości.  
  
4.  W **edytora typów Interfejsu DataSource**, kliknij przycisk **Dodaj źródło danych projektu**.  
  
5.  Na **wybierz typ źródła danych** wybierz opcję **obiektu** i kliknij przycisk **dalej**.  
  
6.  Wybierz typ można powiązać:  
  
    -   Jeśli typ, który chcesz powiązać w bieżącym projekcie lub zestawu, który zawiera typ został już dodany jako odwołanie, rozwiń węzły, które można znaleźć żądanego typu, a następnie wybierz ją.  
  
         —lub—  
  
    -   Jeśli typ, który chcesz powiązać to w innym zestawie, nie jest obecnie na liście odwołań, kliknij przycisk **Dodaj odwołanie**, a następnie kliknij przycisk **projektów** kartę. Wybierz projekt, który zawiera obiekt biznesowych, a następnie kliknij przycisk **OK**. Tego projektu, pojawi się na liście zestawów, dzięki czemu można rozwinąć węzły można znaleźć typu użytkownik ma, a następnie wybierz go.  
  
        > [!NOTE]
        >  Jeśli chcesz powiązać z typem w ramach lub zestawu Microsoft, wyczyść **Ukryj zestawy, które zaczynają się od firmy Microsoft lub System** pole wyboru.  
  
7.  Kliknij przycisk **dalej**, a następnie kliknij przycisk **Zakończ**.  
  
### <a name="to-bind-the-control-to-the-bindingsource"></a>Aby powiązać kontrolki BindingSource  
  
1.  Dodaj <xref:System.Windows.Forms.TextBox> do formularza.  
  
2.  W **właściwości** okna, rozwiń węzeł **(powiązania danych)** węzła.  
  
3.  Kliknij strzałkę obok pozycji <xref:System.Windows.Forms.TextBox.Text%2A> właściwości.  
  
4.  W **edytora typów Interfejsu DataSource**, rozwiń węzeł <xref:System.Windows.Forms.BindingSource> dodane wcześniej, a następnie wybierz pozycję Właściwości powiązanej typ, który chcesz powiązać <xref:System.Windows.Forms.TextBox.Text%2A> właściwość <xref:System.Windows.Forms.TextBox>.  
  
## <a name="see-also"></a>Zobacz też  
 [BindingSource, składnik](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Instrukcje: powiązanie kontrolki Windows Forms z typem](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)  
 [Wiązanie kontrolek z danymi w programie Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
