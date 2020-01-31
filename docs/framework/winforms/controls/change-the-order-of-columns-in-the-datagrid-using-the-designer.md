---
title: Zmiana kolejności kolumn w formancie DataGridView przy użyciu narzędzia Projektant
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], order of
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- data [Windows Forms], displaying
ms.assetid: 7fe52a98-75d6-448c-97a5-65ca2c568c1a
ms.openlocfilehash: be4f67ca6530b74fc90cb50a10463b2378edb933
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743159"
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Porady: zmienianie kolejności kolumn w formancie DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant

Po powiązaniu kontrolki <xref:System.Windows.Forms.DataGridView> Windows Forms ze źródłem danych zostanie wyświetlona kolejność wyświetlania automatycznie generowanych kolumn. Jeśli ta kolejność nie jest preferowana, można zmienić kolejność kolumn za pomocą narzędzia Projektant. Możesz również dodać niepowiązane kolumny do kontrolki i zmienić ich kolejność wyświetlania. Informacje o sposobie zmiany kolejności kolumn w programie można znaleźć w temacie [How to: zmiana kolejności kolumn w kontrolce DataGridView Windows Forms](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md).

Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym formant <xref:System.Windows.Forms.DataGridView>. Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Create a Windows Forms Project Application](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [How to: Add controls to Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="to-change-the-column-order-using-the-designer"></a>Aby zmienić kolejność kolumn przy użyciu narzędzia Projektant

1. Kliknij symbol taga inteligentnego (![symbol tagu inteligentnego](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) w prawym górnym rogu kontrolki <xref:System.Windows.Forms.DataGridView>, a następnie wybierz pozycję **Edytuj kolumny**.

2. Wybierz kolumnę z listy **wybrane kolumny** .

3. Kliknij strzałkę w górę lub w dół znajdującą się po prawej stronie listy **wybrane kolumny** , dopóki wybrana kolumna nie znajduje się w pożądanej pozycji.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- [Instrukcje: dodawanie i usuwanie kolumn do kontrolki DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Instrukcje: Tworzenie projektu aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Instrukcje: dodawanie kontrolek do formularzy Windows Forms](how-to-add-controls-to-windows-forms.md)
