---
title: 'Instrukcje: ukrywanie kolumn w kontrolce DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], hiding
- DataGridView control [Windows Forms], column hiding
- data [Windows Forms], displaying
ms.assetid: a81c38e6-2527-426a-bcb1-be691403be04
ms.openlocfilehash: 35aa1cdeef919d4267cb27da79f183c4c52aefa2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916380"
---
# <a name="how-to-hide-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Instrukcje: ukrywanie kolumn w kontrolce DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant
Czasami chcesz wyświetlić tylko niektóre kolumny, które są dostępne w kontrolce Windows Forms <xref:System.Windows.Forms.DataGridView> . Na przykład możesz chcieć wyświetlić kolumnę wynagrodzenia pracownika dla użytkowników z poświadczeniami zarządzania, jednocześnie ukrywając ją od innych użytkowników. Alternatywnie można powiązać formant ze źródłem danych zawierającym wiele kolumn, tylko niektóre elementy, które mają być wyświetlane. W takim przypadku zwykle usuniesz kolumny, które nie są wyświetlane, zamiast ukrywania. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie i usuwanie kolumn w kontrolce DataGridView Windows Forms przy użyciu narzędzia](add-and-remove-columns-in-the-datagrid-using-the-designer.md)Projektant.

 Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym <xref:System.Windows.Forms.DataGridView> kontrolkę. Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Utwórz projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikacji Windows Forms i [instrukcje: Dodaj formanty do Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="to-hide-a-column-using-the-designer"></a>Aby ukryć kolumnę przy użyciu narzędzia Projektant

1. Kliknij symbol taga inteligentnego (![tag inteligentny](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) w prawym górnym <xref:System.Windows.Forms.DataGridView> rogu kontrolki, a następnie wybierz pozycję **Edytuj kolumny**.

2. Wybierz kolumnę z listy **wybrane kolumny** .

3. W siatce **Właściwości kolumny** Ustaw <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> właściwość na `false`.

    > [!NOTE]
    > Możesz również ukryć kolumnę podczas dodawania jej, czyszcząc pole wyboru **widoczny** w oknie dialogowym **Dodaj kolumnę** .

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>
- [Instrukcje: Dodawanie i usuwanie kolumn w kontrolce DataGridView Windows Forms przy użyciu narzędzia Projektant](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Instrukcje: Tworzenie projektu aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Instrukcje: Dodawanie formantów do Windows Forms](how-to-add-controls-to-windows-forms.md)
