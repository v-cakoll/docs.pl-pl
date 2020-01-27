---
title: Ukrywanie kolumn w formancie DataGridView przy użyciu narzędzia Projektant
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], hiding
- DataGridView control [Windows Forms], column hiding
- data [Windows Forms], displaying
ms.assetid: a81c38e6-2527-426a-bcb1-be691403be04
ms.openlocfilehash: 3c9a6bdeacbeb5929488e6af0054403db73c4239
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738658"
---
# <a name="how-to-hide-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Porady: ukrywanie kolumn w formancie DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant
Czasami chcesz wyświetlić tylko niektóre kolumny, które są dostępne w kontrolce <xref:System.Windows.Forms.DataGridView> Windows Forms. Na przykład możesz chcieć wyświetlić kolumnę wynagrodzenia pracownika dla użytkowników z poświadczeniami zarządzania, jednocześnie ukrywając ją od innych użytkowników. Alternatywnie można powiązać formant ze źródłem danych zawierającym wiele kolumn, tylko niektóre elementy, które mają być wyświetlane. W takim przypadku zwykle usuniesz kolumny, które nie są wyświetlane, zamiast ukrywania. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie i usuwanie kolumn w kontrolce DataGridView Windows Forms przy użyciu narzędzia Projektant](add-and-remove-columns-in-the-datagrid-using-the-designer.md).

 Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym formant <xref:System.Windows.Forms.DataGridView>. Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Create a Windows Forms Project Application](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [How to: Add controls to Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="to-hide-a-column-using-the-designer"></a>Aby ukryć kolumnę przy użyciu narzędzia Projektant

1. Kliknij symbol taga inteligentnego (![symbol tagu inteligentnego](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) w prawym górnym rogu kontrolki <xref:System.Windows.Forms.DataGridView>, a następnie wybierz pozycję **Edytuj kolumny**.

2. Wybierz kolumnę z listy **wybrane kolumny** .

3. W siatce **Właściwości kolumny** ustaw właściwość <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> na `false`.

    > [!NOTE]
    > Możesz również ukryć kolumnę podczas dodawania jej, czyszcząc pole wyboru **widoczny** w oknie dialogowym **Dodaj kolumnę** .

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>
- [Instrukcje: dodawanie i usuwanie kolumn do kontrolki DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Instrukcje: Tworzenie projektu aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Instrukcje: dodawanie kontrolek do formularzy Windows Forms](how-to-add-controls-to-windows-forms.md)
