---
title: 'Instrukcje: opracowywanie prostej kontrolki formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms]
- custom controls [Windows Forms], creating simple controls using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 86cbe435-45b7-4cb4-9b5a-47418369758d
ms.openlocfilehash: a190d86f5ebe258427ac4a73c16c7f271462b69c
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "63807923"
---
# <a name="how-to-develop-a-simple-windows-forms-control"></a>Instrukcje: opracowywanie prostej kontrolki formularzy systemu Windows

W tej sekcji przedstawiono podstawowe etapy tworzenia niestandardowego formantu Windows Forms. Prosty formant opracowanych w tym przewodniku umożliwia wyrównanie jego <xref:System.Windows.Forms.Control.Text%2A> właściwości, które mają być zmienione. Nie podnieść lub obsługi zdarzeń.

### <a name="to-create-a-simple-custom-control"></a>Aby utworzyć prosty formant niestandardowy

1. Definiowanie klasy, która jest pochodną <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.

    ```vb
    Public Class FirstControl
       Inherits Control

    End Class
    ```

    ```csharp
    public class FirstControl:Control {}
    ```

2. Zdefiniuj właściwości. (Nie wymagane do zdefiniowania właściwości, ponieważ formant dziedziczy wiele właściwości z <xref:System.Windows.Forms.Control> klasy, ale większość niestandardowe formanty ogólnie zdefiniować dodatkowe właściwości.) Poniższy fragment kodu definiuje właściwość o nazwie `TextAlignment` , `FirstControl` jest używany do formatowania wyświetlania <xref:System.Windows.Forms.Control.Text%2A> właściwość dziedziczona z <xref:System.Windows.Forms.Control>. Aby uzyskać więcej informacji na temat definiowania właściwości, zobacz [Przegląd właściwości](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v%3dvs.120)).

     [!code-csharp[System.Windows.Forms.FirstControl#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#3)]
     [!code-vb[System.Windows.Forms.FirstControl#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#3)]

     Po ustawieniu właściwości, która zmienia wyświetlania kontrolki, należy wywołać <xref:System.Windows.Forms.Control.Invalidate%2A> metodę, aby odświeżyć formantu. <xref:System.Windows.Forms.Control.Invalidate%2A> jest zdefiniowany w klasie bazowej <xref:System.Windows.Forms.Control>.

3. Zastąp chronionego <xref:System.Windows.Forms.Control.OnPaint%2A> metody dziedziczone z <xref:System.Windows.Forms.Control> zapewnienie logikę renderowania formantu. Jeśli nie zastąpisz <xref:System.Windows.Forms.Control.OnPaint%2A>, formant nie będzie można narysować sam. W poniższy fragment kodu <xref:System.Windows.Forms.Control.OnPaint%2A> metoda Wyświetla <xref:System.Windows.Forms.Control.Text%2A> właściwość dziedziczona z <xref:System.Windows.Forms.Control> z wyrównaniem, określony przez `alignmentValue` pola.

     [!code-csharp[System.Windows.Forms.FirstControl#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#4)]
     [!code-vb[System.Windows.Forms.FirstControl#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#4)]

4. Podaj atrybuty kontrolki. Atrybuty Włącz projektanta wizualnego wyświetlić kontrolki i ich właściwości i zdarzenia odpowiednio w czasie projektowania. Poniższy fragment kodu, ma zastosowanie atrybutów, które mają `TextAlignment` właściwości. W projektancie, takich jak Visual Studio <xref:System.ComponentModel.CategoryAttribute.Category%2A> atrybutu (pokazano we fragmencie kodu) powoduje, że właściwości, które mają być wyświetlane w obszarze kategoria logiczna. <xref:System.ComponentModel.DescriptionAttribute.Description%2A> Atrybutu powoduje, że opisowy ciąg, który będzie wyświetlany w dolnej części **właściwości** okna po `TextAlignment` właściwości jest zaznaczone. Aby uzyskać więcej informacji na temat atrybutów, zobacz [atrybuty czasu projektowania dla składników](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120)).

     [!code-csharp[System.Windows.Forms.FirstControl#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#5)]
     [!code-vb[System.Windows.Forms.FirstControl#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#5)]

5. (opcjonalnie) Zawierają zasoby dla kontrolki. Możesz podać zasobu, takie jak mapy bitowej kontrolki przy użyciu opcji kompilatora (`/res` dla języka C#) do zasobów pakietu przy użyciu kontrolki. W czasie wykonywania, można pobrać zasobu za pomocą metody <xref:System.Resources.ResourceManager> klasy. Aby uzyskać więcej informacji na temat tworzenia i używania zasobów, zobacz [zasoby w aplikacjach pulpitu](../../resources/index.md).

6. Skompiluj i wdróż formantu. Aby skompilować i wdrożyć `FirstControl,` wykonaj następujące czynności:

    1. Zapisz kod w następującym przykładzie do pliku źródłowego (na przykład FirstControl.cs lub FirstControl.vb).

    2. Skompilować kod źródłowy do zestawu i zapisz go w katalogu aplikacji. W tym celu wykonaj następujące polecenie z katalogu, który zawiera plik źródłowy.

        ```console
        vbc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.vb
        ```

        ```console
        csc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.cs
        ```

         `/t:library` — Opcja kompilatora informuje kompilator, to zestaw tworzysz bibliotekę (i nie plik wykonywalny). `/out` Opcja określa ścieżkę i nazwę zestawu. `/r` Opcja zawiera nazwę zestawów, które są przywoływane przez kod. W tym przykładzie utworzysz zestaw prywatny, można użyć tylko w Twojej aplikacji. W związku z tym należy zapisać go w katalogu aplikacji. Aby uzyskać więcej informacji na temat pakowania i wdrażania kontrolkę do dystrybucji, zobacz [wdrożenia](../../deployment/index.md).

Poniższy przykład przedstawia kod dla `FirstControl`. Kontrolka jest ujęty w przestrzeni nazw `CustomWinControls`. Przestrzeń nazw zapewnia powodują ustawienie logicznego grupowania powiązanych typów. Można utworzyć kontrolki w nowej lub istniejącej przestrzeni nazw. W języku C# `using` deklaracji (w języku Visual Basic `Imports`) zezwala na typy, które były dostępne z przestrzeni nazw bez korzystania z w pełni kwalifikowana nazwa typu. W poniższym przykładzie `using` deklaracja umożliwia kodu dostępu do tej klasy <xref:System.Windows.Forms.Control> z <xref:System.Windows.Forms?displayProperty=nameWithType> tylko <xref:System.Windows.Forms.Control> zamiast konieczności używania w pełni kwalifikowana nazwa <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.

[!code-csharp[System.Windows.Forms.FirstControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#1)]
[!code-vb[System.Windows.Forms.FirstControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#1)]

## <a name="using-the-custom-control-on-a-form"></a>Za pomocą niestandardowej kontrolki na formularzu

W poniższym przykładzie przedstawiono prosty formularz, który używa `FirstControl`. Tworzy trzy wystąpienia `FirstControl`, każdy z inną wartością `TextAlignment` właściwości.

#### <a name="to-compile-and-run-this-sample"></a>Aby skompilować i uruchomić ten przykład

1. Zapisz kod w przykładzie poniżej do pliku źródłowego (SimpleForm.cs lub SimpleForms.vb).

2. Skompilować kod źródłowy do zestawu pliku wykonywalnego, wykonując następujące polecenie z katalogu, który zawiera plik źródłowy.

    ```console
    vbc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.vb
    ```

    ```console
    csc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.cs
    ```

     CustomWinControls.dll jest zestawem, który zawiera klasę `FirstControl`. Ten zestaw musi być w tym samym katalogu co plik źródłowy do formularza, który uzyskuje dostęp do niego (SimpleForm.cs lub SimpleForms.vb).

3. Wykonaj SimpleForm.exe przy użyciu następującego polecenia.

    ```console
    SimpleForm
    ```

[!code-csharp[System.Windows.Forms.FirstControl#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/SimpleForm.cs#10)]
[!code-vb[System.Windows.Forms.FirstControl#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/SimpleForm.vb#10)]

## <a name="see-also"></a>Zobacz także

- [Właściwości kontrolek formularzy Windows Forms](properties-in-windows-forms-controls.md)
- [Zdarzenia w kontrolkach formularzy Windows Forms](events-in-windows-forms-controls.md)
