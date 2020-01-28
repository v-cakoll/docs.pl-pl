---
title: Tworzenie kontrolki pokazującej postęp
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
ms.openlocfilehash: 9d2cf353ba2309380221bb51733baaca1b81a5d5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731175"
---
# <a name="how-to-create-a-windows-forms-control-that-shows-progress"></a>Porady: tworzenie formantu formularzy systemu Windows pokazującego postęp
Poniższy przykład kodu pokazuje kontrolkę niestandardową o nazwie `FlashTrackBar`, która może służyć do wyświetlania użytkownikowi poziomu lub postępu aplikacji. Używa gradientu do wizualnego reprezentowania postępu.  
  
 Formant `FlashTrackBar` ilustruje następujące koncepcje:  
  
- Definiowanie właściwości niestandardowych.  
  
- Definiowanie zdarzeń niestandardowych. (`FlashTrackBar` definiuje zdarzenie `ValueChanged`).  
  
- Zastępowanie metody <xref:System.Windows.Forms.Control.OnPaint%2A> w celu zapewnienia logiki do rysowania kontrolki.  
  
- Obliczanie obszaru dostępnego do rysowania formantu przy użyciu jego właściwości <xref:System.Windows.Forms.Control.ClientRectangle%2A>. `FlashTrackBar` robi to w `OptimizedInvalidate` metodzie.  
  
- Implementowanie serializacji lub trwałości dla właściwości w przypadku zmiany w Projektant formularzy systemu Windows. `FlashTrackBar` definiuje metody `ShouldSerializeStartColor` i `ShouldSerializeEndColor` do serializacji `StartColor` i `EndColor` właściwości.  
  
 W poniższej tabeli przedstawiono właściwości niestandardowe zdefiniowane przez `FlashTrackBar`.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|`AllowUserEdit`|Wskazuje, czy użytkownik może zmienić wartość paska śledzenia Flash, klikając i przeciągając go.|  
|`EndColor`|Określa kolor końcowy paska śledzenia.|  
|`DarkenBy`|Określa, jak dużo przyciemnienie tła względem gradientu pierwszego planu.|  
|`Max`|Określa maksymalną wartość paska śledzenia.|  
|`Min`|Określa minimalną wartość paska śledzenia.|  
|`StartColor`|Określa początkowy kolor gradientu.|  
|`ShowPercentage`|Wskazuje, czy w gradiencie ma być wyświetlana wartość procentowa.|  
|`ShowValue`|Wskazuje, czy bieżąca wartość ma być wyświetlana nad gradientem.|  
|`ShowGradient`|Wskazuje, czy na pasku śledzenia powinien zostać wyświetlony gradient koloru przedstawiający bieżącą wartość.|  
|-   `Value`|Określa bieżącą wartość paska śledzenia.|  
  
 W poniższej tabeli przedstawiono dodatkowe elementy członkowskie zdefiniowane przez `FlashTrackBar:` zdarzenia zmiany właściwości i metody, która wywołuje zdarzenie.  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`ValueChanged`|Zdarzenie wywoływane, gdy zostanie zmieniona właściwość `Value` paska śledzenia.|  
|`OnValueChanged`|Metoda, która wywołuje zdarzenie `ValueChanged`.|  
  
> [!NOTE]
> `FlashTrackBar` używa klasy <xref:System.EventArgs> dla danych zdarzenia i <xref:System.EventHandler> dla delegata zdarzenia.  
  
 Aby obsłużyć odpowiednie zdarzenia *EventName* , `FlashTrackBar` zastępuje następujące metody, które dziedziczy od <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:  
  
- <xref:System.Windows.Forms.Control.OnPaint%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseDown%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseMove%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseUp%2A>  
  
- <xref:System.Windows.Forms.Control.OnResize%2A>  
  
 Aby obsłużyć odpowiednie zdarzenia zmiany właściwości, `FlashTrackBar` zastępuje następujące metody, które dziedziczy po <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:  
  
- <xref:System.Windows.Forms.Control.OnBackColorChanged%2A>  
  
- <xref:System.Windows.Forms.Control.OnBackgroundImageChanged%2A>  
  
- <xref:System.Windows.Forms.Control.OnTextChanged%2A>  
  
## <a name="example"></a>Przykład  
 Formant `FlashTrackBar` definiuje dwa edytory typów interfejsu użytkownika, `FlashTrackBarValueEditor` i `FlashTrackBarDarkenByEditor`, które są wyświetlane na poniższej liście. Klasa `HostApp` używa kontrolki `FlashTrackBar` w formularzu systemu Windows.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#1)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#1)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarDarkenByEditor.cs#10)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarDarkenByEditor.vb#10)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarValueEditor.cs#20)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarValueEditor.vb#20)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/HostApp.cs#30)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/HostApp.vb#30)]  
  
## <a name="see-also"></a>Zobacz także

- [Rozszerzanie obsługi czasu projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))
- [Podstawowe informacje o opracowywaniu kontrolek formularzy Windows Forms](windows-forms-control-development-basics.md)
