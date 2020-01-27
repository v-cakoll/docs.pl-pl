---
title: Włączanie zmiany kolejności kolumn w formancie DataGridView przy użyciu narzędzia Projektant
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- columns [Windows Forms], reordering
- data [Windows Forms], displaying
ms.assetid: d82bd69c-6799-4439-a32c-91139c5901d1
ms.openlocfilehash: 823c0064b2710ab5dfd0f67edf95374590d4490b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745843"
---
# <a name="how-to-enable-column-reordering-in-the-windows-forms-datagridview-control-using-the-designer"></a>Porady: włączanie zmiany układu kolumn w formancie DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant
Podczas wyświetlania danych wyświetlanych w kontrolce <xref:System.Windows.Forms.DataGridView> Windows Forms użytkownicy czasami chcą porównać wartości w określonych kolumnach. Może to być niewygodne, jeśli kolumny są szeroko oddzielone w kontrolce, szczególnie jeśli użytkownicy muszą przewinąć w dół i w dół w celu wyświetlenia wszystkich interesujących Cię kolumn. Zadanie porównywania wartości kolumn można ułatwić, umożliwiając użytkownikom zmianę kolejności kolumn. Po włączeniu zmiany kolejności kolumn użytkownicy mogą przenieść kolumnę do nowej pozycji, przeciągając nagłówek kolumny za pomocą myszy.

 Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym formant <xref:System.Windows.Forms.DataGridView>. Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Create a Windows Forms Project Application](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [How to: Add controls to Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="to-enable-column-reordering"></a>Aby włączyć Zmienianie kolejności kolumn

- Kliknij symbol taga inteligentnego (![symbol tagu inteligentnego](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) w prawym górnym rogu kontrolki <xref:System.Windows.Forms.DataGridView>, a następnie wybierz pozycję **Włącz zmienianie kolejności kolumn**.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType>
- [Instrukcje: blokowanie kolumn w kontrolce DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant](freeze-columns-in-the-datagrid-using-the-designer.md)
- [Instrukcje: Tworzenie projektu aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Instrukcje: dodawanie kontrolek do formularzy Windows Forms](how-to-add-controls-to-windows-forms.md)
