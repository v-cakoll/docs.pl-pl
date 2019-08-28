---
title: 'Instrukcje: Pobieranie danych ze schowka'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pasting Clipboard data
- Clipboard [Windows Forms], retrieving data
ms.assetid: 99612537-2c8a-449f-aab5-2b3b28d656e7
ms.openlocfilehash: ca24615049abcc145698c033f31e6c98a38253bf
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040568"
---
# <a name="how-to-retrieve-data-from-the-clipboard"></a>Instrukcje: Pobieranie danych ze schowka

<xref:System.Windows.Forms.Clipboard> Klasa zawiera metody, których można użyć do współdziałania z funkcją Schowka systemu operacyjnego Windows. Wiele aplikacji używa Schowka jako tymczasowego repozytorium dla danych. Na przykład edytory tekstów używają schowka podczas operacji wycinania i wklejania. Schowek jest również przydatny do transferowania informacji z jednej aplikacji do innej.

Niektóre aplikacje przechowują dane w schowku w wielu formatach, aby zwiększyć liczbę innych aplikacji, które mogą potencjalnie korzystać z danych. Format Schowka jest ciągiem, który identyfikuje format. Aplikacja używająca wskazanego formatu może pobrać skojarzone dane ze schowka. <xref:System.Windows.Forms.DataFormats> Klasa zawiera wstępnie zdefiniowane nazwy formatów do użycia. Możesz również użyć własnych nazw formatu lub użyć typu obiektu jako formatu. Aby uzyskać informacje na temat dodawania danych do schowka, [zobacz How to: Dodaj dane do schowka](how-to-add-data-to-the-clipboard.md).

Aby określić, czy Schowek zawiera dane w określonym formacie, użyj jednej z `Contains`metod *formatowania* lub <xref:System.Windows.Forms.Clipboard.GetData%2A> metody. Aby pobrać dane ze schowka, użyj jednej z `Get`metod *formatowania* lub <xref:System.Windows.Forms.Clipboard.GetData%2A> metody. Te metody są nowe w .NET Framework 2,0.

Aby uzyskać dostęp do danych ze schowka przy użyciu wersji wcześniejszej niż .NET Framework 2,0, <xref:System.Windows.Forms.Clipboard.GetDataObject%2A?displayProperty=nameWithType> Użyj metody i wywołaj metody zwrócone. <xref:System.Windows.Forms.IDataObject> Aby określić, czy określony format jest dostępny w zwracanym obiekcie, na przykład Wywołaj <xref:System.Windows.Forms.IDataObject.GetDataPresent%2A> metodę.

> [!NOTE]
> Wszystkie aplikacje oparte na systemie Windows współdzielą schowek systemowy. W związku z tym zawartość może ulec zmianie po przełączeniu do innej aplikacji.
>
> <xref:System.Windows.Forms.Clipboard> Klasy można używać tylko w wątkach ustawionych na tryb Single Thread Apartment (STA). Aby użyć tej klasy, należy się upewnić, że `Main` Metoda jest oznaczona <xref:System.STAThreadAttribute> przy użyciu atrybutu.

### <a name="to-retrieve-data-from-the-clipboard-in-a-single-common-format"></a>Aby pobrać dane ze schowka w jednym, wspólnym formacie

1. Użyj metody <xref:System.Windows.Forms.Clipboard.GetFileDropList%2A> ,,<xref:System.Windows.Forms.Clipboard.GetImage%2A>lub .<xref:System.Windows.Forms.Clipboard.GetText%2A> <xref:System.Windows.Forms.Clipboard.GetAudioStream%2A> Opcjonalnie należy najpierw użyć odpowiednich `Contains`metod *formatowania* , aby określić, czy dane są dostępne w określonym formacie. Te metody są dostępne tylko w .NET Framework 2,0.

    [!code-csharp[System.Windows.Forms.Clipboard#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
    [!code-vb[System.Windows.Forms.Clipboard#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]

### <a name="to-retrieve-data-from-the-clipboard-in-a-custom-format"></a>Aby pobrać dane ze schowka w formacie niestandardowym

1. <xref:System.Windows.Forms.Clipboard.GetData%2A> Użyj metody z niestandardową nazwą formatu. Ta metoda jest dostępna tylko w .NET Framework 2,0.

    Można również użyć wstępnie zdefiniowanych nazw formatu przy użyciu <xref:System.Windows.Forms.Clipboard.SetData%2A> metody. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.DataFormats>.

    [!code-csharp[System.Windows.Forms.Clipboard#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
    [!code-vb[System.Windows.Forms.Clipboard#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]

### <a name="to-retrieve-data-from-the-clipboard-in-multiple-formats"></a>Aby pobrać dane ze schowka w wielu formatach

1. <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> Użyj metody. Należy użyć tej metody do pobierania danych ze schowka w wersjach wcześniejszych niż .NET Framework 2,0.

    [!code-csharp[System.Windows.Forms.Clipboard#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
    [!code-vb[System.Windows.Forms.Clipboard#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]

## <a name="see-also"></a>Zobacz także

- [Operacje przeciągania i upuszczania oraz obsługa schowka](drag-and-drop-operations-and-clipboard-support.md)
- [Instrukcje: Dodawanie danych do schowka](how-to-add-data-to-the-clipboard.md)
