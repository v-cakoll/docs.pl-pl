---
title: 'Instrukcje: tworzenie kontrolki formularzy systemu Windows pokazującego postęp'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], progress tracking
- controls [Windows Forms], creating
- progress [Windows Forms], reporting [Windows Forms]
- FlashTrackBar custom control
ms.assetid: 24c5a2e3-058c-4b8d-a217-c06e6a130c2f
ms.openlocfilehash: 877df5139fd0e626cd2242e3790bc7100f6233aa
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64599331"
---
# <a name="how-to-create-a-windows-forms-control-that-shows-progress"></a>Instrukcje: tworzenie kontrolki formularzy systemu Windows pokazującego postęp
Poniższy przykład kodu pokazuje kontrolkę niestandardową o nazwie `FlashTrackBar` można pokazać użytkownikowi, poziomu lub postęp aplikacji. Aby wizualnie przedstawić postęp używa gradientu.  
  
 `FlashTrackBar` Kontroli ilustruje następujące pojęcia:  
  
- Definiowanie właściwości niestandardowych.  
  
- Definiowanie zdarzeń niestandardowych. (`FlashTrackBar` definiuje `ValueChanged` zdarzenia.)  
  
- Zastępowanie <xref:System.Windows.Forms.Control.OnPaint%2A> metodę, aby zapewnić logikę narysuj kontrolkę.  
  
- Obliczenia obszar rysowania kontrolki przy użyciu jego <xref:System.Windows.Forms.Control.ClientRectangle%2A> właściwości. `FlashTrackBar` robi to jej `OptimizedInvalidate` metody.  
  
- Implementowanie serializacji lub stanów trwałych dla właściwości, gdy zostanie zmieniona w programie Windows Forms Designer. `FlashTrackBar` definiuje `ShouldSerializeStartColor` i `ShouldSerializeEndColor` metody serializacji jego `StartColor` i `EndColor` właściwości.  
  
 W poniższej tabeli przedstawiono właściwości niestandardowe zdefiniowane przez `FlashTrackBar`.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|`AllowUserEdit`|Wskazuje, czy użytkownik może zmienić wartość pasek śledzenia flash, klikając i przeciągając je.|  
|`EndColor`|Określa końcowy kolor pasek śledzenia.|  
|`DarkenBy`|Określa stopień ciemniejszy tła względem gradientu pierwszego planu.|  
|`Max`|Określa maksymalną wartość pasek śledzenia.|  
|`Min`|Określa minimalną wartość pasek śledzenia.|  
|`StartColor`|Określa kolor początkowy gradientu.|  
|`ShowPercentage`|Wskazuje, czy ma być wyświetlane wartości procentowej nad gradientu.|  
|`ShowValue`|Wskazuje, czy do wyświetlenia bieżącej wartości ciągu gradientu.|  
|`ShowGradient`|Wskazuje, czy pasek śledzenia powinien być wyświetlany kolor gradientu przedstawiający bieżącą wartość.|  
|-   `Value`|Określa bieżącą wartość pasek śledzenia.|  
  
 W poniższej tabeli przedstawiono dodatkowe elementy członkowskie zdefiniowane przez `FlashTrackBar:` zdarzenie zmiany właściwości i metody, która wywołuje zdarzenie.  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`ValueChanged`|Zdarzenie, które jest wywołane, gdy `Value` właściwości śledzenia zmian paska.|  
|`OnValueChanged`|Metoda, która wywołuje `ValueChanged` zdarzeń.|  
  
> [!NOTE]
>  `FlashTrackBar` używa <xref:System.EventArgs> klasę danych zdarzenia i <xref:System.EventHandler> dla delegata zdarzenia.  
  
 Do obsługi odpowiednich *EventName* zdarzenia, `FlashTrackBar` zastępuje następujących metod, która dziedziczy <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:  
  
- <xref:System.Windows.Forms.Control.OnPaint%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseDown%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseMove%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseUp%2A>  
  
- <xref:System.Windows.Forms.Control.OnResize%2A>  
  
 Do obsługi odpowiedniej zdarzenia zmiany właściwości `FlashTrackBar` zastępuje następujących metod, która dziedziczy <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:  
  
- <xref:System.Windows.Forms.Control.OnBackColorChanged%2A>  
  
- <xref:System.Windows.Forms.Control.OnBackgroundImageChanged%2A>  
  
- <xref:System.Windows.Forms.Control.OnTextChanged%2A>  
  
## <a name="example"></a>Przykład  
 `FlashTrackBar` Kontroli definiuje dwa edytory typu UI `FlashTrackBarValueEditor` i `FlashTrackBarDarkenByEditor`, które są wyświetlane w następujących fragmentów kodu. `HostApp` Klasy używa `FlashTrackBar` kontrolkę w formularzu Windows.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#1)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#1)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarDarkenByEditor.cs#10)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarDarkenByEditor.vb#10)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarValueEditor.cs#20)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarValueEditor.vb#20)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/HostApp.cs#30)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/HostApp.vb#30)]  
  
## <a name="see-also"></a>Zobacz także

- [Rozszerzenie obsługi w czasie projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))
- [Podstawowe informacje o opracowywaniu kontrolek formularzy Windows Forms](windows-forms-control-development-basics.md)
