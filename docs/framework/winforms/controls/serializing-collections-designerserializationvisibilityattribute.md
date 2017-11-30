---
title: "Porady: serializowanie kolekcji standardowych typów za pomocą DesignerSerializationVisibilityAttribute"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9efad2da27f4003632b643b9f5f0602be0d55480
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-serializing-collections-of-standard-types-with-the-designerserializationvisibilityattribute"></a>Porady: serializowanie kolekcji standardowych typów za pomocą DesignerSerializationVisibilityAttribute
Kontrolki niestandardowe czasami powoduje to udostępnienie kolekcji jako właściwość. W tym przewodniku przedstawiono sposób użycia <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> klasę, aby kontrolować sposób kolekcji jest serializowany w czasie projektowania. Stosowanie <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> zapewnia wartość właściwości z kolekcji zostaną Zserializowane właściwości.  
  
 Aby skopiować kod w tym temacie na jednej liście, zobacz [porady: serializacji kolekcji o standardowych typów za pomocą DesignerSerializationVisibilityAttribute](http://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 W celu przeprowadzenia tego instruktażu potrzebne są:  
  
-   Wystarczających uprawnień, aby mieć możliwość tworzenia i uruchamiania projektów aplikacji formularzy systemu Windows na komputerze, którym jest zainstalowany program Visual Studio.  
  
## <a name="creating-a-control-that-has-a-serializable-collection"></a>Tworzenie formantu, który ma serializacji kolekcji  
 Pierwszym krokiem jest można utworzyć formantu, który ma serializacji kolekcji jako właściwość. Można edytować zawartość tej kolekcji przy użyciu **edytora kolekcji**, które jest dostępne **właściwości** okna.  
  
#### <a name="to-create-a-control-with-a-serializable-collection"></a>Aby utworzyć formant z kolekcji serializacji  
  
1.  Tworzenie projektu Biblioteka formantów systemu Windows o nazwie `SerializationDemoControlLib`. Aby uzyskać więcej informacji, zobacz [szablon biblioteki systemu Windows formantu](http://msdn.microsoft.com/en-us/722f4e2d-1310-4ed5-8f33-593337ab66b4).  
  
2.  Zmień nazwę `UserControl1` do `SerializationDemoControl`. Aby uzyskać więcej informacji, zobacz [porady: Zmienianie nazwy identyfikatorów](http://msdn.microsoft.com/en-us/2430f732-2b70-4516-8cf6-a7bb71cc9724).  
  
3.  W **właściwości** okna, ustaw wartość <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> właściwości `10`.  
  
4.  Miejsce <xref:System.Windows.Forms.TextBox> kontroli w `SerializationDemoControl`.  
  
5.  Wybierz <xref:System.Windows.Forms.TextBox> formantu. W **właściwości** okna, ustaw następujące właściwości.  
  
    |Właściwość|Zmień na|  
    |--------------|---------------|  
    |**Wiele linii**|`true`|  
    |**Doku.**|<xref:System.Windows.Forms.DockStyle.Fill>|  
    |**Paski przewijania**|<xref:System.Windows.Forms.ScrollBars.Vertical>|  
    |**Tylko do odczytu**|`true`|  
  
6.  W **edytora kodu**, Zadeklaruj pola tablicy ciągu o nazwie `stringsValue` w `SerializationDemoControl`.  
  
     [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#4)]
     [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#4)]
     [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#4)]  
  
7.  Zdefiniuj `Strings` właściwość `SerializationDemoControl`.  
  
> [!NOTE]
>  <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> Wartość jest używana do włączenia serializacji kolekcji.  
  
 [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#5)]
 [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#5)]
 [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#5)]  
  
1.  Naciśnij klawisz F5, aby skompilować projekt i uruchomić kontrolę w **kontener testu UserControl**.  
  
2.  Znajdź `Strings` właściwości w <xref:System.Windows.Forms.PropertyGrid> z **kontener testu UserControl**. Kliknij przycisk `Strings` właściwości, kliknij przycisk wielokropka (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) przycisk, aby otworzyć **edytora kolekcji ciąg**.  
  
3.  Wprowadź kilka ciągów w **edytora kolekcji ciąg**. Oddziel je po naciśnięciu klawisza ENTER na końcu każdej ciągu. Kliknij przycisk **OK** po zakończeniu wprowadzania ciągów znaków.  
  
> [!NOTE]
>  Ciągi wpisany są wyświetlane w <xref:System.Windows.Forms.TextBox> z `SerializationDemoControl`.  
  
## <a name="serializing-a-collection-property"></a>Właściwości kolekcji serializacji  
 Aby przetestować działanie serializacji formantu, będzie umieszczenie go w formie i zmienić zawartość kolekcji z **edytora kolekcji**. Analizując projektanta specjalny plik, w którym można zobaczyć stan serializacji kolekcji **Projektant formularzy systemu Windows** emituje kod.  
  
#### <a name="to-serialize-a-collection"></a>Do serializacji kolekcji  
  
1.  Dodaj projekt aplikacji systemu Windows do rozwiązania. Nazwij projekt `SerializationDemoControlTest`.  
  
2.  W **przybornika**, Znajdź kartę o nazwie **składniki SerializationDemoControlLib**. Na tej karcie można znaleźć `SerializationDemoControl`. Aby uzyskać więcej informacji, zobacz [wskazówki: automatyczne zapełnianie przybornika składnikami niestandardowe](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).  
  
3.  Miejsce `SerializationDemoControl` w formularzu.  
  
4.  Znajdź `Strings` właściwości w **właściwości** okna. Kliknij przycisk `Strings` właściwości, kliknij przycisk wielokropka (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) przycisk, aby otworzyć **edytora kolekcji ciąg**.  
  
5.  Wpisz kilka ciągów w **edytora kolekcji ciąg**. Oddziel je po naciśnięciu klawisza ENTER na końcu każdej ciągu. Kliknij przycisk **OK** po zakończeniu wprowadzania ciągów znaków.  
  
> [!NOTE]
>  Ciągi wpisany są wyświetlane w <xref:System.Windows.Forms.TextBox> z `SerializationDemoControl`.  
  
1.  W **Eksploratora rozwiązań**, kliknij przycisk **Pokaż wszystkie pliki** przycisku.  
  
2.  Otwórz **Form1** węzła. Podrzędne jest plik o nazwie **Form1.Designer.cs** lub **Form1.Designer.vb**. Jest to plik, do którego **Projektant formularzy systemu Windows** emituje kod reprezentujący stan czasu projektowania formularza i jej kontrolkach podrzędnych. Otwórz ten plik w **edytora kodu**.  
  
3.  Otwórz obszar o nazwie **kod wygenerowany przez projektanta formularzy systemu Windows** i Znajdź sekcję etykietą **serializationDemoControl1**. Pod tą etykietą jest kod reprezentujący Zserializowany stan formantu. Ciągi wpisane w kroku 5 są wyświetlane w przypisaniu do `Strings` właściwości. W poniższych przykładach kodu w języku C# i Visual Basic, Pokaż kodu podobne do co zobaczysz Jeśli wpisano ciągów "red", "pomarańczowy" i "żółty".  
  
    ```csharp  
    this.serializationDemoControl1.Strings = new string[] {  
            "red",  
            "orange",  
            "yellow"};  
    ```  
    
    ```vb  
    Me.serializationDemoControl1.Strings = New String() {"red", "orange", "yellow"}  
    ```
  
4.  W **edytora kodu**, zmień wartość <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> na `Strings` właściwości <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>.  
  
    ```csharp  
    [DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)]  
    ```  
    ```vb  
    <DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)> _  
    ```  
  
5. Ponowne kompilowanie rozwiązania i powtórz kroki 3 i 4.  
  
> [!NOTE]
>  W takim przypadku **Projektant formularzy systemu Windows** emituje żadnego przypisania `Strings` właściwości.  
  
## <a name="next-steps"></a>Następne kroki  
 Po sprawdzeniu, jak do serializacji kolekcji standardowych typów, należy wziąć pod uwagę integrowanie Kontrolki niestandardowe głębsze środowiska czasu projektowania. W poniższych tematach opisano, jak zwiększyć integracji czasu projektowania Kontrolki niestandardowe:  
  
-   [Architektura w czasie projektowania](http://msdn.microsoft.com/library/4881917b-628f-4689-b872-472e4f8a4e3a)  
  
-   [Atrybuty w formantach formularzy systemu Windows](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
  
-   [Omówienie projektanta serializacji](http://msdn.microsoft.com/library/c342635a-aa5f-4281-915b-b013738af15a)  
  
-   [Wskazówki: Tworzenie formantu formularzy systemu Windows wykorzystującego funkcje czasu projektowania Visual Studio](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>  
 [Omówienie projektanta serializacji](http://msdn.microsoft.com/library/c342635a-aa5f-4281-915b-b013738af15a)  
 [Porady: serializacji kolekcji standardowych typów za pomocą DesignerSerializationVisibilityAttribute](http://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9)  
 [Wskazówki: Automatyczne zapełnianie przybornika składnikami niestandardowymi](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
