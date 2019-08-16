---
title: 'Instrukcje: zmienianie kolejności kolumn w kontrolce DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], order of
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- data [Windows Forms], displaying
ms.assetid: 7fe52a98-75d6-448c-97a5-65ca2c568c1a
ms.openlocfilehash: bf77cf3705a470bbe00be383f6a5cb2d28bda34d
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039632"
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Instrukcje: zmienianie kolejności kolumn w kontrolce DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant

Gdy powiążesz formant <xref:System.Windows.Forms.DataGridView> Windows Forms ze źródłem danych, zostanie wyświetlona kolejność wyświetlania automatycznie generowanych kolumn. Jeśli ta kolejność nie jest preferowana, można zmienić kolejność kolumn za pomocą narzędzia Projektant. Możesz również dodać niepowiązane kolumny do kontrolki i zmienić ich kolejność wyświetlania. Informacje o sposobie zmiany kolejności kolumn w programie można znaleźć w temacie [How to: Zmień kolejność kolumn w kontrolce](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)DataGridView Windows Forms.

Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym <xref:System.Windows.Forms.DataGridView> kontrolkę. Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Utwórz projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikacji Windows Forms i [instrukcje: Dodaj formanty do Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="to-change-the-column-order-using-the-designer"></a>Aby zmienić kolejność kolumn przy użyciu narzędzia Projektant

1. Kliknij symbol taga inteligentnego (![tag inteligentny](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) w prawym górnym <xref:System.Windows.Forms.DataGridView> rogu kontrolki, a następnie wybierz pozycję **Edytuj kolumny**.

2. Wybierz kolumnę z listy **wybrane kolumny** .

3. Kliknij strzałkę w górę lub w dół znajdującą się po prawej stronie listy **wybrane kolumny** , dopóki wybrana kolumna nie znajduje się w pożądanej pozycji.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- [Instrukcje: Dodawanie i usuwanie kolumn w kontrolce DataGridView Windows Forms przy użyciu narzędzia Projektant](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Instrukcje: Tworzenie projektu aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Instrukcje: Dodawanie formantów do Windows Forms](how-to-add-controls-to-windows-forms.md)
