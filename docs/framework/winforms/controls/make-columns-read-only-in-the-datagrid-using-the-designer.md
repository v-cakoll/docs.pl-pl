---
title: Określanie kolumn jako tylko do odczytu w formancie DataGridView przy użyciu narzędzia Projektant
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- DataGridView control [Windows Forms], read-only columns
- data [Windows Forms], displaying
- columns [Windows Forms], read-only
ms.assetid: b4ef7a75-ab33-4ee3-b2cf-201530e454e9
ms.openlocfilehash: 2dd3f8bfcad39ca3d530c79a6e6a8170585f7adf
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627958"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control-using-the-designer"></a>Porady: nadawanie kolumnom statusu tylko do odczytu w formancie DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant
Domyślnie użytkownicy mogą modyfikować dane tekstowe i liczbowe wyświetlane w kontrolce <xref:System.Windows.Forms.DataGridView> Windows Forms. Aby wyświetlić dane, które nie są przeznaczone do modyfikacji, należy wprowadzić kolumny zawierające dane tylko do odczytu. Aby uzyskać informacje na temat sposobu, w jaki formant ma być całkowicie tylko do odczytu, zobacz [How to: zapobiegaj dodawaniu i usuwaniu wierszy w kontrolce DataGridView Windows Forms przy użyciu narzędzia Projektant](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).

 Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym formant <xref:System.Windows.Forms.DataGridView>. Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Create a Windows Forms Project Application](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [How to: Add controls to Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="to-make-a-column-read-only-by-using-the-designer"></a>Aby utworzyć kolumnę tylko do odczytu przy użyciu narzędzia Projektant

1. Kliknij symbol akcji projektanta (![małą czarną strzałkę](./media/designer-actions-glyph.gif)) w prawym górnym rogu kontrolki <xref:System.Windows.Forms.DataGridView>, a następnie wybierz pozycję **Edytuj kolumny**.

2. Wybierz kolumnę z listy **wybrane kolumny** .

3. W siatce **Właściwości kolumny** ustaw właściwość <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> na `true`.

    > [!NOTE]
    > Możesz również wprowadzić kolumnę tylko do odczytu, gdy dodasz ją, zaznaczając pole wyboru **tylko do odczytu** w oknie dialogowym **Dodaj kolumnę** .

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- [Instrukcje: dodawanie i usuwanie kolumn do kontrolki DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Instrukcje: zapobieganie dodawaniu i usuwaniu wierszy do kontrolki DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)
- [Instrukcje: Tworzenie projektu aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Instrukcje: dodawanie kontrolek do formularzy Windows Forms](how-to-add-controls-to-windows-forms.md)
