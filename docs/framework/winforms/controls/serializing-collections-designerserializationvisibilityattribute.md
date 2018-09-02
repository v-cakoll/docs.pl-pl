---
title: 'Porady: serializowanie kolekcji standardowych typów za pomocą DesignerSerializationVisibilityAttribute'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- serialization [Windows Forms], collections
- standard types [Windows Forms], collections
- collections [Windows Forms], serializing
- collections [Windows Forms], standard types
ms.assetid: 020c9df4-fdc5-4dae-815a-963ecae5668c
ms.openlocfilehash: 54859b3065e8e9bb9680d8b6bf7946b393f73b9f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43402589"
---
# <a name="walkthrough-serializing-collections-of-standard-types-with-the-designerserializationvisibilityattribute"></a>Porady: serializowanie kolekcji standardowych typów za pomocą DesignerSerializationVisibilityAttribute
Kontrolki niestandardowe czasami udostępni kolekcji jako właściwość. W tym instruktażu przedstawiono sposób użycia <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> klasy do kontrolowania, jak kolekcja jest serializowany w czasie projektowania. Stosowanie <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> wartości właściwości z kolekcji zapewnia właściwość będzie serializowana.  
  
 Aby skopiować kod, w tym temacie na jednej liście, zobacz [jak: serializowanie kolekcji z standardowych typów za pomocą DesignerSerializationVisibilityAttribute](https://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby ukończyć ten przewodnik, potrzebne są:  
  
-   Wystarczające uprawnienia, aby można było utworzyć i uruchomić projekty aplikacji Windows Forms na komputerze, w którym jest zainstalowany program Visual Studio.  
  
## <a name="creating-a-control-that-has-a-serializable-collection"></a>Tworzenie formantu, który ma możliwy do serializacji kolekcji  
 Pierwszym krokiem jest, aby utworzyć formant, który jest możliwy do serializacji kolekcji jako właściwość. Możesz edytować zawartość tej kolekcji przy użyciu **— Edytor kolekcji**, który jest dostępny z **właściwości** okna.  
  
#### <a name="to-create-a-control-with-a-serializable-collection"></a>Aby utworzyć kontrolkę za pomocą kolekcji serializacji  
  
1.  Utwórz projekt Biblioteka formantów Windows o nazwie `SerializationDemoControlLib`. Aby uzyskać więcej informacji, zobacz [szablon biblioteki kontrolki Windows](https://msdn.microsoft.com/library/722f4e2d-1310-4ed5-8f33-593337ab66b4).  
  
2.  Zmień nazwę `UserControl1` do `SerializationDemoControl`. Aby uzyskać więcej informacji, zobacz [porady: zmiana nazwy identyfikatorów](https://msdn.microsoft.com/library/2430f732-2b70-4516-8cf6-a7bb71cc9724).  
  
3.  W **właściwości** okna, ustaw wartość <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> właściwość `10`.  
  
4.  Miejsce <xref:System.Windows.Forms.TextBox> w kontrolce `SerializationDemoControl`.  
  
5.  Wybierz <xref:System.Windows.Forms.TextBox> kontroli. W **właściwości** okna, ustaw następujące właściwości.  
  
    |Właściwość|Zmień na|  
    |--------------|---------------|  
    |**Wielowierszowy**|`true`|  
    |**Dock**|<xref:System.Windows.Forms.DockStyle.Fill>|  
    |**Paski przewijania**|<xref:System.Windows.Forms.ScrollBars.Vertical>|  
    |**ReadOnly**|`true`|  
  
6.  W **Edytor kodu**, Zadeklaruj pola tablicy ciągów o nazwie `stringsValue` w `SerializationDemoControl`.  
  
     [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#4)]
     [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#4)]
     [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#4)]  
  
7.  Zdefiniuj `Strings` właściwość `SerializationDemoControl`.  
  
> [!NOTE]
>  <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> Wartość jest używana do włączenia serializacji kolekcji.  
  
 [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#5)]
 [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#5)]
 [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#5)]  
  
1.  Naciśnij klawisz F5, aby skompilować projekt i uruchomić Twoją kontrolą w **UserControl — kontener testowy**.  
  
2.  Znajdź `Strings` właściwość <xref:System.Windows.Forms.PropertyGrid> z **UserControl — kontener testowy**. Kliknij przycisk `Strings` właściwości, następnie kliknij przycisk wielokropka (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) przycisk, aby otworzyć **Edytor kolekcji ciągów**.  
  
3.  Wprowadź kilka ciągów w **Edytor kolekcji ciągów**. Oddziel je, naciskając klawisz ENTER na końcu każdego ciągu. Kliknij przycisk **OK** po zakończeniu wprowadzania ciągów znaków.  
  
> [!NOTE]
>  Ciągi wpisany są wyświetlane w <xref:System.Windows.Forms.TextBox> z `SerializationDemoControl`.  
  
## <a name="serializing-a-collection-property"></a>Serializowanie właściwości kolekcji  
 Aby sprawdzić zachowanie serializacji kontrolki, będzie umieścić go w formularzu i zmieniać zawartość kolekcji przy użyciu **— Edytor kolekcji**. Można wyświetlić stan kolekcji serializacji, patrząc na plik projektanta specjalny, do którego **Windows Forms Designer** emituje kod.  
  
#### <a name="to-serialize-a-collection"></a>Do serializacji kolekcji  
  
1.  Dodaj projekt aplikacji Windows do rozwiązania. Nadaj projektowi nazwę `SerializationDemoControlTest`.  
  
2.  W **przybornika**, Znajdź kartę o nazwie **składniki SerializationDemoControlLib**. Na tej karcie można znaleźć `SerializationDemoControl`. Aby uzyskać więcej informacji, zobacz [wskazówki: automatyczne zapełnianie przybornika składnikami niestandardowe](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).  
  
3.  Miejsce `SerializationDemoControl` w formularzu.  
  
4.  Znajdź `Strings` właściwość **właściwości** okna. Kliknij przycisk `Strings` właściwości, następnie kliknij przycisk wielokropka (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) przycisk, aby otworzyć **Edytor kolekcji ciągów**.  
  
5.  Wpisz kilka ciągów w **Edytor kolekcji ciągów**. Oddziel je, naciskając klawisz ENTER na końcu każdego ciągu. Kliknij przycisk **OK** po zakończeniu wprowadzania ciągów znaków.  
  
> [!NOTE]
>  Ciągi wpisany są wyświetlane w <xref:System.Windows.Forms.TextBox> z `SerializationDemoControl`.  
  
1.  W **Eksploratora rozwiązań**, kliknij przycisk **Pokaż wszystkie pliki** przycisku.  
  
2.  Otwórz **Form1** węzła. Podrzędne jest plik o nazwie **Form1.Designer.cs** lub **Form1.Designer.vb**. Jest to plik, do którego **Windows Forms Designer** emituje kod reprezentujący stan projektowania formularza i jego formantów podrzędnych. Otwórz ten plik w **Edytor kodu**.  
  
3.  Otwórz region o nazwie **kod wygenerowany przez projektanta formularzy Windows** i Znajdź sekcję etykietą **serializationDemoControl1**. Pod tą etykietą jest kod reprezentujący Zserializowany stan kontrolki. Ciągi wpisywane w kroku 5 są wyświetlane w przypisaniu do `Strings` właściwości. W poniższych przykładach kodu w języku C# i Visual Basic, Pokaż kod podobny do będzie wyświetlanych Jeśli wpisano ciągi "red", "pomarańczowy" i "żółty".  
  
    ```csharp  
    this.serializationDemoControl1.Strings = new string[] {  
            "red",  
            "orange",  
            "yellow"};  
    ```  
    
    ```vb  
    Me.serializationDemoControl1.Strings = New String() {"red", "orange", "yellow"}  
    ```
  
4.  W **Edytor kodu**, zmień wartość właściwości <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> na `Strings` właściwość <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>.  
  
    ```csharp  
    [DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)]  
    ```  
    ```vb  
    <DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)> _  
    ```  
  
5. Ponownie skompiluj rozwiązanie i powtórz kroki 3 i 4.  
  
> [!NOTE]
>  W tym przypadku **Windows Forms Designer** emituje żadnego przypisania `Strings` właściwości.  
  
## <a name="next-steps"></a>Następne kroki  
 Wiesz, jak do serializacji kolekcji standardowych typów, należy wziąć pod uwagę integrowanie Kontrolki niestandardowe głębiej środowisku czasu projektowania. W poniższych tematach opisano, jak poprawić integracji czasu projektowania dla kontrolek niestandardowych:  
  
-   [Architektura czasu projektowania](https://msdn.microsoft.com/library/4881917b-628f-4689-b872-472e4f8a4e3a)  
  
-   [Atrybuty w kontrolkach formularzy Windows Forms](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
  
-   [Przegląd serializacji projektanta](https://msdn.microsoft.com/library/c342635a-aa5f-4281-915b-b013738af15a)  
  
-   [Przewodnik: tworzenie kontrolki formularzy Windows Forms wykorzystującej funkcje czasu projektowania programu Visual Studio](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>  
 [Przegląd serializacji projektanta](https://msdn.microsoft.com/library/c342635a-aa5f-4281-915b-b013738af15a)  
 [Instrukcje: serializowanie kolekcji standardowych typów za pomocą DesignerSerializationVisibilityAttribute](https://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9)  
 [Przewodnik: automatyczne zapełnianie Przybornika składnikami niestandardowymi](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
