---
title: Tworzenie list Master-Details z kontrolką DataGrid przy użyciu narzędzia Projektant
ms.date: 03/30/2017
helpviewer_keywords:
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 19438ba2-f687-4417-a2fb-ab1cd69d4ded
ms.openlocfilehash: 0dea3dd88a8c6c2aceb894789ace8ef3b5c83632
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743386"
---
# <a name="how-to-create-master-details-lists-with-the-windows-forms-datagrid-control-using-the-designer"></a>Porady: tworzenie list wzorzec-szczegół za pomocą formantu DataGrid formularzy systemu Windows przy użyciu narzędzia Projektant

> [!NOTE]
> Formant <xref:System.Windows.Forms.DataGridView> zamienia i dodaje funkcje do kontrolki <xref:System.Windows.Forms.DataGrid>; Niemniej jednak kontrolka <xref:System.Windows.Forms.DataGrid> jest zachowywana na potrzeby zgodności z poprzednimi wersjami i w przyszłości. Aby uzyskać więcej informacji, zobacz [różnice między kontrolkami DataGridView i DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

 Jeśli <xref:System.Data.DataSet> zawiera serię powiązanych tabel, można użyć dwóch kontrolek <xref:System.Windows.Forms.DataGrid>, aby wyświetlić dane w formacie wzorzec-szczegóły. Jeden <xref:System.Windows.Forms.DataGrid> wyznaczono jako siatkę główną, a druga jest oznaczona jako siatka szczegółów. Po wybraniu wpisu na liście głównej wszystkie powiązane wpisy podrzędne zostaną wyświetlone na liście szczegóły. Na przykład jeśli <xref:System.Data.DataSet> zawiera tabelę Customers i powiązanej tabeli Orders, należy określić tabelę Customers jako siatkę główną oraz tabelę Orders, która będzie siatką szczegółów. Po wybraniu klienta z siatki głównej wszystkie zamówienia powiązane z tym klientem w tabeli Orders będą wyświetlane w siatce szczegółów.

 Poniższa procedura wymaga projektu **aplikacji systemu Windows** (**plik** > **Nowy** > **projekt** > **wizualizacji C#**  lub **Visual Basic** > **klasycznego pulpitu** > Windows Forms **aplikacji**).

## <a name="to-create-a-master-details-list-in-the-designer"></a>Aby utworzyć listę wzorzec-szczegóły w projektancie

1. Dodaj dwa <xref:System.Windows.Forms.DataGrid> kontrolki do formularza. Aby uzyskać więcej informacji, zobacz [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md). W programie Visual Studio 2005 formant <xref:System.Windows.Forms.DataGrid> nie jest domyślnie w **przyborniku** . Aby uzyskać więcej informacji, zobacz [jak: dodać elementy do przybornika](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)).

    > [!NOTE]
    > Następujące kroki nie mają zastosowania do programu Visual Studio 2005, który używa okna **źródła danych** do tworzenia powiązań danych czasu projektowania. Aby uzyskać więcej informacji, zobacz temat [Powiązywanie kontrolek z danymi w programie Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio) i [instrukcje: wyświetlanie powiązanych danych w aplikacji Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/57tx3hhe(v=vs.120)).

2. Przeciągnij dwie lub więcej tabel z **Eksplorator serwera** do formularza.

3. Z menu **dane** wybierz polecenie **Generuj zestaw danych**.

4. Ustaw relacje między tabelami przy użyciu projektanta XML. Aby uzyskać szczegółowe informacje, zobacz "Instrukcje: Tworzenie relacji jeden-do-wielu w schematach XML i zestawach danych" w witrynie MSDN.

5. Zapisz relacje, wybierając pozycję **Zapisz wszystko** w menu **plik** .

6. Skonfiguruj formant <xref:System.Windows.Forms.DataGrid>, który chcesz wyznaczyć siatkę główną w następujący sposób:

    1. Wybierz <xref:System.Data.DataSet> z listy rozwijanej we właściwości <xref:System.Windows.Forms.DataGrid.DataSource%2A>.

    2. Wybierz tabelę główną (na przykład "Customers") z listy rozwijanej we właściwości <xref:System.Windows.Forms.DataGrid.DataMember%2A>.

7. Skonfiguruj kontrolkę <xref:System.Windows.Forms.DataGrid>, która ma wyznaczyć siatkę szczegółów w następujący sposób:

    1. Wybierz <xref:System.Data.DataSet> z listy rozwijanej we właściwości <xref:System.Windows.Forms.DataGrid.DataSource%2A>.

    2. Wybierz relację (na przykład "Customers. CustOrd") między tabelami głównymi i szczegółowymi z listy rozwijanej we właściwości <xref:System.Windows.Forms.DataGrid.DataMember%2A>. Aby wyświetlić relację, rozwiń węzeł, klikając znak plus ( **+** ) obok tabeli głównej na liście rozwijanej.

## <a name="see-also"></a>Zobacz także

- [DataGrid, kontrolka](datagrid-control-windows-forms.md)
- [DataGrid, kontrolka — omówienie](datagrid-control-overview-windows-forms.md)
- [Instrukcje: powiązywanie kontrolki DataGrid formularzy Windows Forms ze źródłem danych](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
- [Wiązanie kontrolek z danymi w programie Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
