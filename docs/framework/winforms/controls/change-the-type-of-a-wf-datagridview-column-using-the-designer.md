---
title: Zmienianie typu kolumny DataGridView przy użyciu narzędzia Projektant
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], types
- DataGridView control [Windows Forms], changing column type
- data [Windows Forms], displaying
ms.assetid: 7f994d45-600d-4190-a187-35803214b40c
ms.openlocfilehash: 976f257d38dc7be5c904e63da47c61486bd3301c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737130"
---
# <a name="how-to-change-the-type-of-a-windows-forms-datagridview-column-using-the-designer"></a>Porady: zmienianie typu formantu DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant
Czasami trzeba zmienić typ kolumny, która została już dodana do kontrolki <xref:System.Windows.Forms.DataGridView> Windows Forms. Na przykład możesz chcieć zmodyfikować typy niektórych kolumn, które są generowane automatycznie podczas wiązania kontrolki ze źródłem danych. Jest to przydatne, gdy wyświetlana tabela zawiera kolumny zawierające klucze obce do wierszy w powiązanej tabeli. W takim przypadku można zastąpić kolumny pól tekstowych, które wyświetlają te klucze obce z kolumnami pól kombi, które wyświetlają bardziej zrozumiałe wartości z powiązanej tabeli.

 Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym formant <xref:System.Windows.Forms.DataGridView>. Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Create a Windows Forms Project Application](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [How to: Add controls to Windows Forms](how-to-add-controls-to-windows-forms.md).

### <a name="to-change-the-type-of-a-column-using-the-designer"></a>Aby zmienić typ kolumny przy użyciu narzędzia Projektant

1. Kliknij symbol taga inteligentnego (![symbol tagu inteligentnego](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) w prawym górnym rogu kontrolki <xref:System.Windows.Forms.DataGridView>, a następnie wybierz pozycję **Edytuj kolumny**.

2. Wybierz kolumnę z listy **wybrane kolumny** .

3. W siatce **Właściwości kolumny** ustaw właściwość `ColumnType` na nowy typ kolumny.

    > [!NOTE]
    > Właściwość `ColumnType` jest właściwością czasu projektowania, która wskazuje klasę reprezentującą typ kolumny. Nie jest to rzeczywista Właściwość zdefiniowana w klasie Column.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [Instrukcje: Tworzenie projektu aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Instrukcje: dodawanie kontrolek do formularzy Windows Forms](how-to-add-controls-to-windows-forms.md)
