---
title: Zmiana kolejności kolumn w formancie DataGridView przy użyciu narzędzia Projektant
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], order of
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- data [Windows Forms], displaying
ms.assetid: 7fe52a98-75d6-448c-97a5-65ca2c568c1a
ms.openlocfilehash: 7540203fb1c0465caeb045275734d1a7c6f25ee8
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628751"
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Porady: zmienianie kolejności kolumn w formancie DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant

Po powiązaniu kontrolki <xref:System.Windows.Forms.DataGridView> Windows Forms ze źródłem danych zostanie wyświetlona kolejność wyświetlania automatycznie generowanych kolumn. Jeśli ta kolejność nie jest preferowana, można zmienić kolejność kolumn za pomocą narzędzia Projektant. Możesz również dodać niepowiązane kolumny do kontrolki i zmienić ich kolejność wyświetlania. Informacje o sposobie zmiany kolejności kolumn w programie można znaleźć w temacie [How to: zmiana kolejności kolumn w kontrolce DataGridView Windows Forms](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md).

Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym formant <xref:System.Windows.Forms.DataGridView>. Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Create a Windows Forms Project Application](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [How to: Add controls to Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="to-change-the-column-order-using-the-designer"></a>Aby zmienić kolejność kolumn przy użyciu narzędzia Projektant

1. Kliknij symbol akcji projektanta (![małą czarną strzałkę](./media/designer-actions-glyph.gif)) w prawym górnym rogu kontrolki <xref:System.Windows.Forms.DataGridView>, a następnie wybierz pozycję **Edytuj kolumny**.

2. Wybierz kolumnę z listy **wybrane kolumny** .

3. Kliknij strzałkę w górę lub w dół znajdującą się po prawej stronie listy **wybrane kolumny** , dopóki wybrana kolumna nie znajduje się w pożądanej pozycji.

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.DataGridView>
- [Instrukcje: dodawanie i usuwanie kolumn do kontrolki DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Instrukcje: Tworzenie projektu aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Instrukcje: dodawanie kontrolek do formularzy Windows Forms](how-to-add-controls-to-windows-forms.md)
