---
title: 'Porady: opracowywanie prostego formantu formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms]
- custom controls [Windows Forms], creating simple controls using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 86cbe435-45b7-4cb4-9b5a-47418369758d
ms.openlocfilehash: 04cedc0df60ef95acb79b651ddcbcbb34ae5e920
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-develop-a-simple-windows-forms-control"></a>Porady: opracowywanie prostego formantu formularzy systemu Windows
W tej sekcji przedstawiono podstawowe etapy tworzenia niestandardowego formantu formularzy systemu Windows. Proste kontrolki opracowane w tym przewodniku umożliwia wyrównanie jego <xref:System.Windows.Forms.Control.Text%2A> właściwość zostanie zmieniony. Nie podnieść lub obsługę zdarzeń.  
  
### <a name="to-create-a-simple-custom-control"></a>Aby utworzyć prosty formantu niestandardowego  
  
1.  Definiowanie klasy, która jest pochodną <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.  
  
    ```vb  
    Public Class FirstControl  
       Inherits Control  
  
    End Class  
    ```  
  
    ```csharp  
    public class FirstControl:Control{}  
    ```  
  
2.  Definiowanie właściwości. (Nie należy do definiowania właściwości, ponieważ formant dziedziczy wiele właściwości z <xref:System.Windows.Forms.Control> klasy, ale większość formantów niestandardowych zazwyczaj zdefiniować dodatkowe właściwości.) Poniższy fragment kodu definiuje właściwość o nazwie `TextAlignment` który `FirstControl` jest używany do formatowania wyświetlania <xref:System.Windows.Forms.Control.Text%2A> właściwość dziedziczona z <xref:System.Windows.Forms.Control>. Aby uzyskać więcej informacji na temat definiowania właściwości, zobacz [Przegląd właściwości](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52).  
  
     [!code-csharp[System.Windows.Forms.FirstControl#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#3)]
     [!code-vb[System.Windows.Forms.FirstControl#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#3)]  
  
     Gdy właściwość zmiany wyświetlania kontrolki, należy wywołać <xref:System.Windows.Forms.Control.Invalidate%2A> metodę, aby odświeżyć formantu. <xref:System.Windows.Forms.Control.Invalidate%2A> jest zdefiniowany w klasie podstawowej <xref:System.Windows.Forms.Control>.  
  
3.  Zastąpienie chronionej <xref:System.Windows.Forms.Control.OnPaint%2A> odziedziczone metody <xref:System.Windows.Forms.Control> zapewnienie logikę renderowania formantu. Jeśli nie zastępują <xref:System.Windows.Forms.Control.OnPaint%2A>, formantu nie będzie mógł się rysowanie. W poniższy fragment kodu <xref:System.Windows.Forms.Control.OnPaint%2A> metoda Wyświetla <xref:System.Windows.Forms.Control.Text%2A> właściwość dziedziczona z <xref:System.Windows.Forms.Control> z wyrównanie określone przez `alignmentValue` pola.  
  
     [!code-csharp[System.Windows.Forms.FirstControl#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#4)]
     [!code-vb[System.Windows.Forms.FirstControl#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#4)]  
  
4.  Podaj atrybuty dla formantu. Atrybuty Włącz wizualnego projektanta wyświetlić właściwości i zdarzeń formantu i jego odpowiednio w czasie projektowania. Poniższy fragment kodu stosuje atrybuty `TextAlignment` właściwości. W projektancie, takiego jak Visual Studio <xref:System.ComponentModel.CategoryAttribute.Category%2A> atrybut (wyświetlany we fragmencie kodu) powoduje, że właściwości, które mają być wyświetlane w obszarze kategoria logiczna. <xref:System.ComponentModel.DescriptionAttribute.Description%2A> Atrybut powoduje opisowy ciąg mają być wyświetlane w dolnej części **właściwości** okna po `TextAlignment` właściwości jest zaznaczone. Aby uzyskać więcej informacji na temat atrybutów, zobacz [atrybuty czasu projektowania dla składników](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3).  
  
     [!code-csharp[System.Windows.Forms.FirstControl#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#5)]
     [!code-vb[System.Windows.Forms.FirstControl#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#5)]  
  
5.  (opcjonalnie) Podaj zasobów dla formantu. Możesz podać zasobów, takich jak mapy bitowej dla formantu przy użyciu opcji kompilatora (`/res` dla C#) do pakietu zasobów za pomocą formantu. W czasie wykonywania, można pobrać zasobu przy użyciu metody <xref:System.Resources.ResourceManager> klasy. Aby uzyskać więcej informacji na temat tworzenia i używania zasobów, zobacz [zasobów w aplikacjach pulpitu](../../../../docs/framework/resources/index.md).  
  
6.  Skompiluj i wdróż formantu. Aby skompilować i wdrożyć `FirstControl,` wykonaj następujące czynności:  
  
    1.  Zapisz kod w poniższym przykładzie do pliku źródłowego (na przykład FirstControl.cs lub FirstControl.vb).  
  
    2.  Kompilowanie kodu źródłowego w zestawie i zapisz go w katalogu aplikacji. Aby to zrobić, uruchom następujące polecenie z katalogu, który zawiera plik źródłowy.  
  
        ```console  
        vbc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.vb  
        ```  
  
        ```console 
        csc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.cs  
        ```  
  
         `/t:library` — Opcja kompilatora informuje kompilator, że zestaw tworzona jest biblioteki (a nie plik wykonywalny). `/out` Opcja określa ścieżkę i nazwę zestawu. `/r` Opcja zawiera nazwę zestawy, do których odwołuje się kod. W tym przykładzie utworzysz zestaw prywatny, który można używać tylko aplikacji. W związku z tym należy zapisać go w katalogu aplikacji. Aby uzyskać więcej informacji dotyczących pakowania i wdrażania kontrolkę do dystrybucji, zobacz [wdrożenia](../../../../docs/framework/deployment/index.md).  
  
 Poniższy przykład przedstawia kod dla `FirstControl`. Kontroli jest ujęty w przestrzeni nazw `CustomWinControls`. Przestrzeń nazw zapewnia logiczne grupowanie powiązanych typów. Można utworzyć formantu w nowej lub istniejącej przestrzeni nazw. W języku C# `using` deklaracji (w języku Visual Basic `Imports`) umożliwia typów można uzyskać dostęp z przestrzeni nazw, bez korzystania z w pełni kwalifikowana nazwa typu. W poniższym przykładzie `using` deklaracji umożliwia kodu dostępu do tej klasy <xref:System.Windows.Forms.Control> z <xref:System.Windows.Forms?displayProperty=nameWithType> tylko <xref:System.Windows.Forms.Control> zamiast w pełni kwalifikowana nazwa <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.  
  
 [!code-csharp[System.Windows.Forms.FirstControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#1)]
 [!code-vb[System.Windows.Forms.FirstControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#1)]  
  
## <a name="using-the-custom-control-on-a-form"></a>Za pomocą kontrolki niestandardowej w formularzu  
 W poniższym przykładzie przedstawiono prosty formularz, który używa `FirstControl`. Tworzy trzy wystąpienia `FirstControl`, każdy z inną wartością `TextAlignment` właściwości.  
  
#### <a name="to-compile-and-run-this-sample"></a>Aby skompilować i uruchomić ten przykład  
  
1.  Zapisz kod w poniższym przykładzie do pliku źródłowego (SimpleForm.cs lub SimpleForms.vb).  
  
2.  Kompilowanie kodu źródłowego do pliku wykonywalnego zestawu, wykonując następujące polecenie z katalogu, który zawiera plik źródłowy.  
  
    ```console  
    vbc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.vb  
    ```  
  
    ```console 
    csc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.cs  
    ```  
  
     Zestaw zawierający klasę jest CustomWinControls.dll `FirstControl`. Ten zestaw musi być w tym samym katalogu co plik źródłowy dla formularza, który uzyskuje dostęp do niego (SimpleForm.cs lub SimpleForms.vb).  
  
3.  Wykonanie SimpleForm.exe przy użyciu następującego polecenia.  
  
    ```console
    SimpleForm  
    ```  
  
 [!code-csharp[System.Windows.Forms.FirstControl#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/SimpleForm.cs#10)]
 [!code-vb[System.Windows.Forms.FirstControl#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/SimpleForm.vb#10)]  
  
## <a name="see-also"></a>Zobacz też  
 [Właściwości kontrolek formularzy Windows Forms](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [Zdarzenia w kontrolkach formularzy Windows Forms](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)
