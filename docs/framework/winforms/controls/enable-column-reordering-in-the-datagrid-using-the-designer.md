---
title: 'Instrukcje: włączanie zmiany układu kolumn w kontrolce DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- columns [Windows Forms], reordering
- data [Windows Forms], displaying
ms.assetid: d82bd69c-6799-4439-a32c-91139c5901d1
ms.openlocfilehash: 3864ce70f058259b597df904311bd4a48218b151
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040344"
---
# <a name="how-to-enable-column-reordering-in-the-windows-forms-datagridview-control-using-the-designer"></a>Instrukcje: włączanie zmiany układu kolumn w kontrolce DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant
Podczas wyświetlania danych wyświetlanych w kontrolce Windows Forms <xref:System.Windows.Forms.DataGridView> użytkownicy czasami chcą porównać wartości w określonych kolumnach. Może to być niewygodne, jeśli kolumny są szeroko oddzielone w kontrolce, szczególnie jeśli użytkownicy muszą przewinąć w dół i w dół w celu wyświetlenia wszystkich interesujących Cię kolumn. Zadanie porównywania wartości kolumn można ułatwić, umożliwiając użytkownikom zmianę kolejności kolumn. Po włączeniu zmiany kolejności kolumn użytkownicy mogą przenieść kolumnę do nowej pozycji, przeciągając nagłówek kolumny za pomocą myszy.

 Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym <xref:System.Windows.Forms.DataGridView> kontrolkę. Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Utwórz projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikacji Windows Forms i [instrukcje: Dodaj formanty do Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="to-enable-column-reordering"></a>Aby włączyć Zmienianie kolejności kolumn

- Kliknij symbol taga inteligentnego (![tag inteligentny](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) w prawym górnym <xref:System.Windows.Forms.DataGridView> rogu kontrolki, a następnie wybierz pozycję **Włącz zmienianie kolejności kolumn**.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType>
- [Instrukcje: Zablokuj kolumny w kontrolce DataGridView Windows Forms przy użyciu narzędzia Projektant](freeze-columns-in-the-datagrid-using-the-designer.md)
- [Instrukcje: Tworzenie projektu aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Instrukcje: Dodawanie formantów do Windows Forms](how-to-add-controls-to-windows-forms.md)
