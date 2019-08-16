---
title: 'Instrukcje: nadawanie kolumnom statusu tylko do odczytu w kontrolce DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- DataGridView control [Windows Forms], read-only columns
- data [Windows Forms], displaying
- columns [Windows Forms], read-only
ms.assetid: b4ef7a75-ab33-4ee3-b2cf-201530e454e9
ms.openlocfilehash: 6bdd561c863a461f43a5a7aac025fead1f971bb0
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039811"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control-using-the-designer"></a>Instrukcje: nadawanie kolumnom statusu tylko do odczytu w kontrolce DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant
Domyślnie użytkownicy mogą modyfikować dane tekstowe i liczbowe wyświetlane w kontrolce Windows Forms <xref:System.Windows.Forms.DataGridView> . Aby wyświetlić dane, które nie są przeznaczone do modyfikacji, należy wprowadzić kolumny zawierające dane tylko do odczytu. Aby uzyskać informacje na temat sposobu, w jaki formant ma być całkowicie tylko [do odczytu, zobacz How to: Zapobiegaj dodawaniu i usuwaniu wierszy w kontrolce DataGridView Windows Forms](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)przy użyciu narzędzia Projektant.

 Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym <xref:System.Windows.Forms.DataGridView> kontrolkę. Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Utwórz projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikacji Windows Forms i [instrukcje: Dodaj formanty do Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="to-make-a-column-read-only-by-using-the-designer"></a>Aby utworzyć kolumnę tylko do odczytu przy użyciu narzędzia Projektant

1. Kliknij symbol taga inteligentnego (![tag inteligentny](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) w prawym górnym <xref:System.Windows.Forms.DataGridView> rogu kontrolki, a następnie wybierz pozycję **Edytuj kolumny**.

2. Wybierz kolumnę z listy **wybrane kolumny** .

3. W siatce **Właściwości kolumny** Ustaw <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> właściwość na `true`.

    > [!NOTE]
    >  Możesz również wprowadzić kolumnę tylko do odczytu, gdy dodasz ją, zaznaczając pole wyboru **tylko do odczytu** w oknie dialogowym **Dodaj kolumnę** .

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- [Instrukcje: Dodawanie i usuwanie kolumn w kontrolce DataGridView Windows Forms przy użyciu narzędzia Projektant](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Instrukcje: Zapobiegaj dodawaniu i usuwaniu wierszy w kontrolce DataGridView Windows Forms przy użyciu narzędzia Projektant](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)
- [Instrukcje: Tworzenie projektu aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Instrukcje: Dodawanie formantów do Windows Forms](how-to-add-controls-to-windows-forms.md)
