---
title: 'Porady: tworzenie formantu formularzy systemu Windows pokazującego postęp'
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
ms.openlocfilehash: 5773181b8883f0f94ff451808c8c97ce3407970e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531433"
---
# <a name="how-to-create-a-windows-forms-control-that-shows-progress"></a>Porady: tworzenie formantu formularzy systemu Windows pokazującego postęp
Poniższy przykład kodu pokazuje formant niestandardowy o nazwie `FlashTrackBar` można wyświetlane użytkownikowi, poziomu lub postęp aplikacji. Gradient używa do wizualnego reprezentowania postępu.  
  
 `FlashTrackBar` Kontroli przedstawiono następujące kwestie:  
  
-   Definiowanie właściwości niestandardowych.  
  
-   Definiowanie zdarzeń niestandardowych. (`FlashTrackBar` definiuje `ValueChanged` zdarzeń.)  
  
-   Zastępowanie <xref:System.Windows.Forms.Control.OnPaint%2A> metodę w celu zapewnienia logiki, by narysować kontrolkę.  
  
-   Obliczanie dostępne do rysowania formantu przy użyciu obszaru jego <xref:System.Windows.Forms.Control.ClientRectangle%2A> właściwości. `FlashTrackBar` Dzieje się tak jego `OptimizedInvalidate` metody.  
  
-   Implementowanie serializacji lub trwałości dla właściwości, gdy zostanie zmieniona w narzędziu Projektant dla formularzy systemu Windows. `FlashTrackBar` definiuje `ShouldSerializeStartColor` i `ShouldSerializeEndColor` metody serializacji jego `StartColor` i `EndColor` właściwości.  
  
 W poniższej tabeli przedstawiono właściwości niestandardowe zdefiniowane przez `FlashTrackBar`.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|`AllowUserEdit`|Wskazuje, czy użytkownik może zmienić wartość pasek śledzenia flash, klikając i przeciągając go.|  
|`EndColor`|Określa kolor końcowy pasek śledzenia.|  
|`DarkenBy`|Określa stopień przyciemnianie tła względem gradientu pierwszego planu.|  
|`Max`|Określa maksymalną wartość pasek śledzenia.|  
|`Min`|Określa minimalną wartość pasek śledzenia.|  
|`StartColor`|Określa kolor początkowy gradientu.|  
|`ShowPercentage`|Wskazuje, czy ma być wyświetlana wartość procentową nad gradientu.|  
|`ShowValue`|Wskazuje, czy należy wyświetlić bieżącą wartość za pośrednictwem gradientu.|  
|`ShowGradient`|Wskazuje, czy pasek śledzenia powinien być wyświetlany kolor gradientu przedstawiający bieżącą wartość.|  
|-   `Value`|Określa bieżącą wartość pasek śledzenia.|  
  
 W poniższej tabeli przedstawiono dodatkowe elementów członkowskich zdefiniowanych przez `FlashTrackBar:` zdarzenie zmiany właściwości i metody, która wywołuje zdarzenie.  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`ValueChanged`|Zdarzenie wywoływane, gdy `Value` właściwości śledzenia pasek zmian.|  
|`OnValueChanged`|Metoda, który wywołuje `ValueChanged` zdarzeń.|  
  
> [!NOTE]
>  `FlashTrackBar` używa <xref:System.EventArgs> klasy na potrzeby danych zdarzenia i <xref:System.EventHandler> dla delegata zdarzenia.  
  
 Do obsługi odpowiednich *EventName* zdarzenia, `FlashTrackBar` zastępuje następujące metody, które dziedziczy z <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:  
  
-   <xref:System.Windows.Forms.Control.OnPaint%2A>  
  
-   <xref:System.Windows.Forms.Control.OnMouseDown%2A>  
  
-   <xref:System.Windows.Forms.Control.OnMouseMove%2A>  
  
-   <xref:System.Windows.Forms.Control.OnMouseUp%2A>  
  
-   <xref:System.Windows.Forms.Control.OnResize%2A>  
  
 Do obsługi odpowiednie zdarzenia zmiany właściwości `FlashTrackBar` zastępuje następujące metody, które dziedziczy z <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:  
  
-   <xref:System.Windows.Forms.Control.OnBackColorChanged%2A>  
  
-   <xref:System.Windows.Forms.Control.OnBackgroundImageChanged%2A>  
  
-   <xref:System.Windows.Forms.Control.OnTextChanged%2A>  
  
## <a name="example"></a>Przykład  
 `FlashTrackBar` Kontroli definiuje dwie edytory typ interfejsu użytkownika, `FlashTrackBarValueEditor` i `FlashTrackBarDarkenByEditor`, które przedstawiono w następujących fragmentów kodu. `HostApp` Klasy używa `FlashTrackBar` kontrolkę w formularzu systemu Windows.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#1)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#1)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarDarkenByEditor.cs#10)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarDarkenByEditor.vb#10)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarValueEditor.cs#20)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarValueEditor.vb#20)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/HostApp.cs#30)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/HostApp.vb#30)]  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzenie obsługi w czasie projektowania](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 [Podstawowe informacje o opracowywaniu kontrolek formularzy Windows Forms](../../../../docs/framework/winforms/controls/windows-forms-control-development-basics.md)
