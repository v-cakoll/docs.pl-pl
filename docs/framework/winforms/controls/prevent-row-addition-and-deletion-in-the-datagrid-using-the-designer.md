---
title: Zapobiegaj dodawaniu i usuwaniu wierszy w formancie DataGridView przy użyciu narzędzia Projektant
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], preventing row addition or deletion
ms.assetid: a17722bd-9400-41e6-8dcc-c9c151f0a749
ms.openlocfilehash: cc9aff0f15d1bd6de5c469ee7069a99f3360837a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728707"
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control-using-the-designer"></a>Porady: zapobieganie dodawaniu i usuwaniu rzędów do formantu DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant
Czasami chcesz uniemożliwić użytkownikom wprowadzanie nowych wierszy danych lub usuwanie istniejących wierszy w kontrolce <xref:System.Windows.Forms.DataGridView>. Nowe wiersze są wprowadzane w specjalnym wierszu dla nowych rekordów w dolnej części formantu. Po wyłączeniu dodawania wierszy nie jest wyświetlany wiersz dla nowych rekordów. Następnie można sprawić, aby formant całkowicie tylko do odczytu przez wyłączenie usuwania wierszy i edytowanie komórek.

 Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym formant <xref:System.Windows.Forms.DataGridView>. Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Create a Windows Forms Project Application](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [How to: Add controls to Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="to-prevent-row-addition-and-deletion"></a>Aby zapobiec dodawaniu i usuwaniu wierszy

- Kliknij symbol taga inteligentnego (![symbol tagu inteligentnego](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) w prawym górnym rogu kontrolki <xref:System.Windows.Forms.DataGridView>, a następnie wyczyść pola wyboru **Włącz Dodawanie** i **Włączanie usuwania** .

    > [!NOTE]
    > Aby formant można było całkowicie tylko do odczytu, usuń zaznaczenie pola wyboru **Włącz edycję** .

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- [Instrukcje: Tworzenie projektu aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Instrukcje: dodawanie kontrolek do formularzy Windows Forms](how-to-add-controls-to-windows-forms.md)
