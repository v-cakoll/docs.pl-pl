---
title: 'Instrukcje: wiązanie kontrolki formularzy systemu Windows z typem przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 5ab984b5-c2d0-4638-a572-1c84013e8746
ms.openlocfilehash: 5069d7d3b5ef4c5b05159dac521d32f5be8abdd1
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046043"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type-using-the-designer"></a>Instrukcje: wiązanie kontrolki formularzy systemu Windows z typem przy użyciu narzędzia Projektant

Podczas kompilowania formantów, które współpracują z danymi, czasami trzeba powiązać formant z typem, a nie obiektem. Zazwyczaj należy powiązać kontrolkę z typem w czasie projektowania, gdy dane mogą nie być dostępne, ale nadal chcesz, aby formanty powiązane z danymi wyświetlały dane z interfejsu publicznego typu. W poniższych procedurach pokazano, jak utworzyć nową <xref:System.Windows.Forms.BindingSource> , która jest powiązana z typem, a następnie powiązać jedną z właściwości <xref:System.Windows.Forms.TextBox.Text%2A> typu z właściwością <xref:System.Windows.Forms.TextBox>.

### <a name="to-bind-the-bindingsource-to-a-type"></a>Aby powiązać źródło BindingSource z typem

1. Utwórz projekt Windows Forms (**plik** > **Nowy** > **projekt** > **Visual C#**  lub **Visual Basic** **klasyczny** pulpit >   >  **Windows Forms aplikacji**).

2. W widoku **projektu** przeciągnij <xref:System.Windows.Forms.BindingSource> składnik na formularz.

3. W oknie **Właściwości** kliknij strzałkę dla <xref:System.Windows.Forms.BindingSource.DataSource%2A> właściwości.

4. W **Edytorze typów interfejsu użytkownika źródła**danych kliknij przycisk **Dodaj źródło dane projektu**.

5. Na stronie **Wybierz typ źródła danych** wybierz pozycję **obiekt** i kliknij przycisk **dalej**.

6. Wybierz typ do powiązania:

    - Jeśli typ, który ma zostać powiązany, znajduje się w bieżącym projekcie lub zestaw, który zawiera typ, został już dodany jako odwołanie, rozwiń węzły, aby znaleźć żądany typ, a następnie wybierz go.

      \-oraz

    - Jeśli typ, który ma zostać powiązany, znajduje się w innym zestawie, nie jest obecnie na liście odwołań, kliknij przycisk **Dodaj odwołanie**, a następnie kliknij kartę **projekty** . Wybierz projekt zawierający obiekt biznesowy, a następnie kliknij przycisk **OK**. Ten projekt pojawi się na liście zestawów, dzięki czemu można rozwinąć węzły w celu znalezienia żądanego typu, a następnie wybrać.

      > [!NOTE]
      > Jeśli chcesz powiązać z typem w strukturze lub zestawie Microsoft, usuń zaznaczenie pola wyboru **Ukryj zestawy, które zaczynają się od firmy Microsoft lub systemu** .

7. Kliknij przycisk **dalej**, a następnie kliknij przycisk **Zakończ**.

### <a name="to-bind-the-control-to-the-bindingsource"></a>Aby powiązać formant z BindingSource

1. <xref:System.Windows.Forms.TextBox> Dodaj do formularza.

2. W oknie **Właściwości** rozwiń węzeł **(DataBindings)** .

3. Kliknij strzałkę obok <xref:System.Windows.Forms.TextBox.Text%2A> właściwości.

4. W **Edytorze typów interfejsu użytkownika źródła danych**rozwiń węzeł <xref:System.Windows.Forms.BindingSource> dodany poprzednio i wybierz właściwość powiązanego typu, który chcesz powiązać z <xref:System.Windows.Forms.TextBox.Text%2A> właściwością <xref:System.Windows.Forms.TextBox>.

## <a name="see-also"></a>Zobacz także

- [BindingSource, składnik](bindingsource-component.md)
- [Instrukcje: Powiąż formant Windows Forms z typem](how-to-bind-a-windows-forms-control-to-a-type.md)
- [Wiązanie kontrolek z danymi w programie Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
