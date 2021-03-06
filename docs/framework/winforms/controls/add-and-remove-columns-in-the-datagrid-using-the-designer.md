---
title: Dodawanie i usuwanie kolumn w formancie DataGridView przy użyciu narzędzia Projektant
ms.date: 03/30/2017
f1_keywords:
- vs.DataGridViewAddColumnDialog
helpviewer_keywords:
- DataGridView control [Windows Forms], adding columns
- DataGridView control [Windows Forms], removing columns
ms.assetid: 9e709f35-0a8c-4e7e-b4c4-bacb7a834077
ms.openlocfilehash: 8843b1d30f3e5f31a060e27b41b0105e6584f155
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628608"
---
# <a name="how-to-add-and-remove-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Porady: dodawanie i usuwanie kolumn do formantu DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant
Kontrolka <xref:System.Windows.Forms.DataGridView> Windows Forms musi zawierać kolumny, aby można było wyświetlić dane. Jeśli planujesz ręcznie wypełnić formant, musisz dodać kolumny samodzielnie. Alternatywnie można powiązać formant ze źródłem danych, które generuje i wypełnia kolumny automatycznie. Jeśli źródło danych zawiera więcej kolumn niż ma być wyświetlanych, można usunąć niepożądane kolumny.

 Poniższe procedury wymagają projektu **aplikacji systemu Windows** z formularzem zawierającym formant <xref:System.Windows.Forms.DataGridView>. Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Create a Windows Forms Project Application](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [How to: Add controls to Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="to-add-a-column-using-the-designer"></a>Aby dodać kolumnę przy użyciu narzędzia Projektant

1. Kliknij symbol akcji projektanta (![małą czarną strzałkę](./media/designer-actions-glyph.gif)) w prawym górnym rogu kontrolki <xref:System.Windows.Forms.DataGridView>, a następnie wybierz pozycję **Dodaj kolumnę**.

2. W oknie dialogowym **Dodawanie kolumny** wybierz opcję **kolumny** z danymi i wybierz kolumnę ze źródła danych lub wybierz opcję **kolumny niepowiązane** i zdefiniuj kolumnę przy użyciu udostępnionych pól.

3. Kliknij przycisk **Dodaj** , aby dodać kolumnę, powodując pojawienie się w projektancie, jeśli istniejące kolumny nie wypełniają jeszcze obszaru wyświetlania formantu.

    > [!NOTE]
    > Właściwości kolumny można modyfikować w oknie dialogowym **Edytowanie kolumn** , do którego można uzyskać dostęp za pomocą tagu inteligentnego kontrolki.

## <a name="to-remove-a-column-using-the-designer"></a>Aby usunąć kolumnę przy użyciu narzędzia Projektant

1. Wybierz pozycję **Edytuj kolumny** z tagu inteligentnego kontrolki.

2. Wybierz kolumnę z listy **wybrane kolumny** .

3. Kliknij przycisk **Usuń** , aby usunąć kolumnę, powodując zniknięcie jej z projektanta.

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.DataGridView>
- [Instrukcje: Tworzenie projektu aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Instrukcje: dodawanie kontrolek do formularzy Windows Forms](how-to-add-controls-to-windows-forms.md)
