---
title: 'Instrukcje: tworzenie list wzorzec-szczegół za pomocą kontrolki DataGrid formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 19438ba2-f687-4417-a2fb-ab1cd69d4ded
ms.openlocfilehash: d1e598831954f17bdf3bc03ab880c344ca36aa5a
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039946"
---
# <a name="how-to-create-master-details-lists-with-the-windows-forms-datagrid-control-using-the-designer"></a>Instrukcje: tworzenie list wzorzec-szczegół za pomocą kontrolki DataGrid formularzy systemu Windows przy użyciu narzędzia Projektant

> [!NOTE]
>  Formant zastępuje i dodaje funkcję <xref:System.Windows.Forms.DataGrid> do <xref:System.Windows.Forms.DataGrid> kontrolki; jednak kontrolka jest zachowywana w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości, jeśli wybierzesz opcję. <xref:System.Windows.Forms.DataGridView> Aby uzyskać więcej informacji, zobacz [różnice między kontrolkami DataGridView i DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

 Jeśli zawiera serię powiązanych tabel, można użyć dwóch <xref:System.Windows.Forms.DataGrid> kontrolek, aby wyświetlić dane w formacie wzorzec-szczegóły. <xref:System.Data.DataSet> <xref:System.Windows.Forms.DataGrid> Wyznaczono ją jako siatkę główną, a druga wyznaczono jako siatkę szczegółów. Po wybraniu wpisu na liście głównej wszystkie powiązane wpisy podrzędne zostaną wyświetlone na liście szczegóły. Na przykład, jeśli <xref:System.Data.DataSet> zawiera tabelę Customers i powiązanej tabeli Orders, należy określić tabelę Customers jako siatkę główną oraz tabelę Orders, która będzie siatką szczegółów. Po wybraniu klienta z siatki głównej wszystkie zamówienia powiązane z tym klientem w tabeli Orders będą wyświetlane w siatce szczegółów.

 Poniższa procedura wymaga projektu **aplikacji systemu Windows** (**plik** >  **C# Visual** **New** > **Project** > lub **Visual Basic**  >   **Klasyczna** > **aplikacja Windows Forms**Desktop).

## <a name="to-create-a-master-details-list-in-the-designer"></a>Aby utworzyć listę wzorzec-szczegóły w projektancie

1. Dodaj dwa <xref:System.Windows.Forms.DataGrid> kontrolki do formularza. Aby uzyskać więcej informacji, zobacz [jak: Dodaj formanty do Windows Forms](how-to-add-controls-to-windows-forms.md). W programie Visual Studio 2005 <xref:System.Windows.Forms.DataGrid> formant domyślnie nie znajduje się w **przyborniku** . Aby uzyskać więcej informacji, zobacz [jak: Dodaj elementy do przybornika](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)).

    > [!NOTE]
    >  Następujące kroki nie mają zastosowania do programu Visual Studio 2005, który używa okna **źródła danych** do tworzenia powiązań danych czasu projektowania. Aby uzyskać więcej informacji, zobacz temat [Powiązywanie kontrolek z danymi w programie Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio) i [instrukcje: Wyświetl powiązane dane w aplikacji](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/57tx3hhe(v=vs.120))Windows Forms.

2. Przeciągnij dwie lub więcej tabel z **Eksplorator serwera** do formularza.

3. Z menu **dane** wybierz polecenie **Generuj zestaw danych**.

4. Ustaw relacje między tabelami przy użyciu projektanta XML. Aby uzyskać szczegółowe informacje, zobacz "How to: Utwórz relacje jeden do wielu w schematach XML i zestawach danych w witrynie MSDN.

5. Zapisz relacje, wybierając pozycję **Zapisz wszystko** w menu **plik** .

6. <xref:System.Windows.Forms.DataGrid> Skonfiguruj kontrolkę, która ma wyznaczyć siatkę główną w następujący sposób:

    1. Wybierz z listy rozwijanej <xref:System.Windows.Forms.DataGrid.DataSource%2A> we właściwości. <xref:System.Data.DataSet>

    2. Wybierz tabelę główną (na przykład "Customers") z listy rozwijanej we <xref:System.Windows.Forms.DataGrid.DataMember%2A> właściwości.

7. <xref:System.Windows.Forms.DataGrid> Skonfiguruj kontrolkę, dla której chcesz określić siatkę szczegółów w następujący sposób:

    1. Wybierz z listy rozwijanej <xref:System.Windows.Forms.DataGrid.DataSource%2A> we właściwości. <xref:System.Data.DataSet>

    2. Wybierz relację (na przykład "Customers. custord") między tabelami głównymi i szczegółowymi z listy rozwijanej we <xref:System.Windows.Forms.DataGrid.DataMember%2A> właściwości. Aby wyświetlić relację, rozwiń węzeł, klikając znak plus ( **+** ) obok tabeli głównej na liście rozwijanej.

## <a name="see-also"></a>Zobacz także

- [DataGrid, kontrolka](datagrid-control-windows-forms.md)
- [DataGrid, kontrolka — omówienie](datagrid-control-overview-windows-forms.md)
- [Instrukcje: Powiązywanie kontrolki DataGrid Windows Forms ze źródłem danych](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
- [Wiązanie kontrolek z danymi w programie Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
