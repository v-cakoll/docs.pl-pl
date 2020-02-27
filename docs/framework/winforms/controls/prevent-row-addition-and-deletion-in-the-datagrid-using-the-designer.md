---
title: Zapobiegaj dodawaniu i usuwaniu wierszy w formancie DataGridView przy użyciu narzędzia Projektant
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], preventing row addition or deletion
ms.assetid: a17722bd-9400-41e6-8dcc-c9c151f0a749
ms.openlocfilehash: cca497aeaedd0c9f988241092eed707ecc259859
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628894"
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control-using-the-designer"></a>Porady: zapobieganie dodawaniu i usuwaniu rzędów do formantu DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant
Czasami chcesz uniemożliwić użytkownikom wprowadzanie nowych wierszy danych lub usuwanie istniejących wierszy w kontrolce <xref:System.Windows.Forms.DataGridView>. Nowe wiersze są wprowadzane w specjalnym wierszu dla nowych rekordów w dolnej części formantu. Po wyłączeniu dodawania wierszy nie jest wyświetlany wiersz dla nowych rekordów. Następnie można sprawić, aby formant całkowicie tylko do odczytu przez wyłączenie usuwania wierszy i edytowanie komórek.

 Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym formant <xref:System.Windows.Forms.DataGridView>. Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Create a Windows Forms Project Application](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [How to: Add controls to Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="to-prevent-row-addition-and-deletion"></a>Aby zapobiec dodawaniu i usuwaniu wierszy

- Kliknij symbol akcji projektanta (![małą czarną strzałkę](./media/designer-actions-glyph.gif)) w prawym górnym rogu kontrolki <xref:System.Windows.Forms.DataGridView>, a następnie wyczyść pola wyboru **Włącz Dodawanie** i **Włączanie usuwania** .

    > [!NOTE]
    > Aby formant można było całkowicie tylko do odczytu, usuń zaznaczenie pola wyboru **Włącz edycję** .

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- [Instrukcje: Tworzenie projektu aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Instrukcje: dodawanie kontrolek do formularzy Windows Forms](how-to-add-controls-to-windows-forms.md)
