---
title: Opracowywanie prostej kontrolki
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms]
- custom controls [Windows Forms], creating simple controls using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 86cbe435-45b7-4cb4-9b5a-47418369758d
ms.openlocfilehash: 5383cee5358dbd260fc6c023d3db607da6b10ea4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742255"
---
# <a name="how-to-develop-a-simple-windows-forms-control"></a>Porady: opracowywanie prostego formantu formularzy systemu Windows

Ta sekcja przeprowadzi Cię przez kluczowe kroki tworzenia niestandardowej kontrolki Windows Forms. Prosta kontrolka opracowana w tym instruktażu umożliwia zmianę wyrównania właściwości <xref:System.Windows.Forms.Control.Text%2A>. Nie zgłasza ani nie obsługuje zdarzeń.

### <a name="to-create-a-simple-custom-control"></a>Aby utworzyć prostą kontrolkę niestandardową

1. Zdefiniuj klasę, która pochodzi od <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.

    ```vb
    Public Class FirstControl
       Inherits Control

    End Class
    ```

    ```csharp
    public class FirstControl:Control {}
    ```

2. Zdefiniuj właściwości. (Nie trzeba definiować właściwości, ponieważ kontrolka dziedziczy wiele właściwości z klasy <xref:System.Windows.Forms.Control>, ale większość formantów niestandardowych zwykle definiuje dodatkowe właściwości.) Poniższy fragment kodu definiuje właściwość o nazwie `TextAlignment`, która `FirstControl` używa do formatowania wyświetlania właściwości <xref:System.Windows.Forms.Control.Text%2A> dziedziczonej z <xref:System.Windows.Forms.Control>. Aby uzyskać więcej informacji na temat definiowania właściwości, zobacz [Omówienie właściwości](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v%3dvs.120)).

     [!code-csharp[System.Windows.Forms.FirstControl#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#3)]
     [!code-vb[System.Windows.Forms.FirstControl#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#3)]

     Po ustawieniu właściwości, która zmienia wizualizację wyświetlania kontrolki, należy wywołać metodę <xref:System.Windows.Forms.Control.Invalidate%2A>, aby ponownie narysować formant. <xref:System.Windows.Forms.Control.Invalidate%2A> jest zdefiniowany w klasie bazowej <xref:System.Windows.Forms.Control>.

3. Przesłoń metodę chronioną <xref:System.Windows.Forms.Control.OnPaint%2A> dziedziczoną z <xref:System.Windows.Forms.Control>, aby zapewnić logikę renderowania dla kontrolki. Jeśli nie zastąpisz <xref:System.Windows.Forms.Control.OnPaint%2A>, formant nie będzie mógł narysować siebie. W poniższym fragmencie kodu Metoda <xref:System.Windows.Forms.Control.OnPaint%2A> wyświetla Właściwość <xref:System.Windows.Forms.Control.Text%2A> dziedziczoną z <xref:System.Windows.Forms.Control> z wyrównaniem określonym przez pole `alignmentValue`.

     [!code-csharp[System.Windows.Forms.FirstControl#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#4)]
     [!code-vb[System.Windows.Forms.FirstControl#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#4)]

4. Podaj atrybuty dla kontrolki. Atrybuty umożliwiają projektantowi wizualnemu wyświetlanie kontrolki i jej właściwości i zdarzeń odpowiednio w czasie projektowania. Poniższy fragment kodu stosuje atrybuty do właściwości `TextAlignment`. W projektancie, takim jak Visual Studio, atrybut <xref:System.ComponentModel.CategoryAttribute.Category%2A> (pokazany w fragmencie kodu) powoduje, że właściwość jest wyświetlana w kategorii logicznej. Atrybut <xref:System.ComponentModel.DescriptionAttribute.Description%2A> powoduje wyświetlenie ciągu opisowego w dolnej części okna **Właściwości** po wybraniu właściwości `TextAlignment`. Aby uzyskać więcej informacji na temat atrybutów, zobacz [atrybuty czasu projektowania dla składników](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120)).

     [!code-csharp[System.Windows.Forms.FirstControl#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#5)]
     [!code-vb[System.Windows.Forms.FirstControl#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#5)]

5. obowiązkowe Zapewnianie zasobów dla kontrolki. Możesz dostarczyć zasób, taki jak mapa bitowa, dla kontrolki przy użyciu opcji kompilatora (`/res` for C#), aby spakować zasoby z kontrolką. W czasie wykonywania zasób można pobrać przy użyciu metod klasy <xref:System.Resources.ResourceManager>. Aby uzyskać więcej informacji na temat tworzenia i używania zasobów, zobacz [zasoby w aplikacjach klasycznych](../../resources/index.md).

6. Kompiluj i Wdróż swój formant. Aby skompilować i wdrożyć `FirstControl,` wykonaj następujące czynności:

    1. Zapisz kod w następującym przykładzie do pliku źródłowego (na przykład FirstControl.cs lub FirstControl. vb).

    2. Skompiluj kod źródłowy do zestawu i Zapisz go w katalogu aplikacji. Aby to osiągnąć, wykonaj następujące polecenie w katalogu, który zawiera plik źródłowy.

        ```console
        vbc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.vb
        ```

        ```console
        csc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.cs
        ```

         Opcja kompilatora `/t:library` informuje kompilator, że tworzony zestaw jest biblioteką (a nie plikiem wykonywalnym). Opcja `/out` określa ścieżkę i nazwę zestawu. Opcja`/r` zawiera nazwę zestawów, do których odwołuje się kod. W tym przykładzie utworzysz prywatny zestaw, którego mogą używać tylko Twoje aplikacje. W związku z tym należy zapisać go w katalogu aplikacji. Aby uzyskać więcej informacji o pakowaniu i wdrażaniu kontrolki do dystrybucji, zobacz [wdrażanie](../../deployment/index.md).

Poniższy przykład pokazuje kod dla `FirstControl`. Kontrolka jest zawarta w przestrzeni nazw `CustomWinControls`. Przestrzeń nazw zawiera logiczne grupowanie typów pokrewnych. Formant można utworzyć w nowej lub istniejącej przestrzeni nazw. W C#programie deklaracja `using` (w Visual Basic, `Imports`) umożliwia dostęp do typów z przestrzeni nazw bez używania w pełni kwalifikowanej nazwy typu. W poniższym przykładzie deklaracja `using` pozwala kodowi uzyskać dostęp do klasy <xref:System.Windows.Forms.Control> z <xref:System.Windows.Forms?displayProperty=nameWithType> jako <xref:System.Windows.Forms.Control>, zamiast używać w pełni kwalifikowanej nazwy <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.

[!code-csharp[System.Windows.Forms.FirstControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#1)]
[!code-vb[System.Windows.Forms.FirstControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#1)]

## <a name="using-the-custom-control-on-a-form"></a>Używanie kontrolki niestandardowej w formularzu

Poniższy przykład pokazuje prosty formularz, który używa `FirstControl`. Tworzy trzy wystąpienia `FirstControl`, z których każda ma inną wartość właściwości `TextAlignment`.

#### <a name="to-compile-and-run-this-sample"></a>Aby skompilować i uruchomić ten przykład

1. Zapisz kod w poniższym przykładzie do pliku źródłowego (SimpleForm.cs lub SimpleForms. vb).

2. Skompiluj kod źródłowy do zestawu wykonywalnego, wykonując następujące polecenie z katalogu, który zawiera plik źródłowy.

    ```console
    vbc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.vb
    ```

    ```console
    csc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.cs
    ```

     CustomWinControls. dll jest zestawem zawierającym klasę `FirstControl`. Ten zestaw musi znajdować się w tym samym katalogu, co plik źródłowy dla formularza, który uzyskuje do niego dostęp (SimpleForm.cs lub SimpleForms. vb).

3. Wykonaj SimpleForm. exe przy użyciu następującego polecenia.

    ```console
    SimpleForm
    ```

[!code-csharp[System.Windows.Forms.FirstControl#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/SimpleForm.cs#10)]
[!code-vb[System.Windows.Forms.FirstControl#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/SimpleForm.vb#10)]

## <a name="see-also"></a>Zobacz także

- [Właściwości kontrolek formularzy Windows Forms](properties-in-windows-forms-controls.md)
- [Zdarzenia w kontrolkach formularzy Windows Forms](events-in-windows-forms-controls.md)
