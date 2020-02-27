---
title: Zmienianie typu kolumny DataGridView przy użyciu narzędzia Projektant
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], types
- DataGridView control [Windows Forms], changing column type
- data [Windows Forms], displaying
ms.assetid: 7f994d45-600d-4190-a187-35803214b40c
ms.openlocfilehash: 470f350a4791a3db39d08ab7992d86eb7b2e270a
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628621"
---
# <a name="how-to-change-the-type-of-a-windows-forms-datagridview-column-using-the-designer"></a>Porady: zmienianie typu formantu DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant
Czasami trzeba zmienić typ kolumny, która została już dodana do kontrolki <xref:System.Windows.Forms.DataGridView> Windows Forms. Na przykład możesz chcieć zmodyfikować typy niektórych kolumn, które są generowane automatycznie podczas wiązania kontrolki ze źródłem danych. Jest to przydatne, gdy wyświetlana tabela zawiera kolumny zawierające klucze obce do wierszy w powiązanej tabeli. W takim przypadku można zastąpić kolumny pól tekstowych, które wyświetlają te klucze obce z kolumnami pól kombi, które wyświetlają bardziej zrozumiałe wartości z powiązanej tabeli.

 Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym formant <xref:System.Windows.Forms.DataGridView>. Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Create a Windows Forms Project Application](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [How to: Add controls to Windows Forms](how-to-add-controls-to-windows-forms.md).

### <a name="to-change-the-type-of-a-column-using-the-designer"></a>Aby zmienić typ kolumny przy użyciu narzędzia Projektant

1. Kliknij symbol akcji projektanta (![małą czarną strzałkę](./media/designer-actions-glyph.gif)) w prawym górnym rogu kontrolki <xref:System.Windows.Forms.DataGridView>, a następnie wybierz pozycję **Edytuj kolumny**.

2. Wybierz kolumnę z listy **wybrane kolumny** .

3. W siatce **Właściwości kolumny** ustaw właściwość `ColumnType` na nowy typ kolumny.

    > [!NOTE]
    > Właściwość `ColumnType` jest właściwością czasu projektowania, która wskazuje klasę reprezentującą typ kolumny. Nie jest to rzeczywista Właściwość zdefiniowana w klasie Column.

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [Instrukcje: Tworzenie projektu aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Instrukcje: dodawanie kontrolek do formularzy Windows Forms](how-to-add-controls-to-windows-forms.md)
