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
ms.openlocfilehash: 84f0caace70f9877e84fdd01dc69216dc10fe485
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950577"
---
# <a name="how-to-create-a-windows-forms-control-that-shows-progress"></a>Instrukcje: tworzenie kontrolki formularzy systemu Windows pokazującego postęp
Poniższy przykład kodu pokazuje kontrolkę niestandardową `FlashTrackBar` o nazwie, która może służyć do wyświetlania użytkownikowi poziomu lub postępu aplikacji. Używa gradientu do wizualnego reprezentowania postępu.  
  
 `FlashTrackBar` Kontrolka ilustruje następujące koncepcje:  
  
- Definiowanie właściwości niestandardowych.  
  
- Definiowanie zdarzeń niestandardowych. `FlashTrackBar` (`ValueChanged` definiuje zdarzenie).  
  
- Zastępowanie <xref:System.Windows.Forms.Control.OnPaint%2A> metody w celu zapewnienia logiki do rysowania kontrolki.  
  
- Obliczanie obszaru dostępnego do rysowania kontrolki przy użyciu jej <xref:System.Windows.Forms.Control.ClientRectangle%2A> właściwości. `FlashTrackBar`robi to w `OptimizedInvalidate` metodzie.  
  
- Implementowanie serializacji lub trwałości dla właściwości w przypadku zmiany w Projektant formularzy systemu Windows. `FlashTrackBar`definiuje metody i `ShouldSerializeEndColor` dla serializowania właściwości `EndColor` i.`StartColor` `ShouldSerializeStartColor`  
  
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
  
 W poniższej tabeli przedstawiono dodatkowe elementy członkowskie zdefiniowane `FlashTrackBar:` przez zdarzenie zmiany właściwości i metodę, która wywołuje zdarzenie.  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`ValueChanged`|Zdarzenie wywoływane, gdy `Value` zostanie zmieniona właściwość paska śledzenia.|  
|`OnValueChanged`|Metoda, która wywołuje `ValueChanged` zdarzenie.|  
  
> [!NOTE]
> `FlashTrackBar`używa klasy dla danych zdarzeń i <xref:System.EventHandler> dla delegata zdarzenia. <xref:System.EventArgs>  
  
 Aby obsłużyć odpowiednie zdarzenia EventName `FlashTrackBar` , program zastępuje następujące metody, z <xref:System.Windows.Forms.Control?displayProperty=nameWithType>których dziedziczy:  
  
- <xref:System.Windows.Forms.Control.OnPaint%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseDown%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseMove%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseUp%2A>  
  
- <xref:System.Windows.Forms.Control.OnResize%2A>  
  
 Aby obsłużyć odpowiednie zdarzenia zmiany właściwości, `FlashTrackBar` program zastępuje następujące metody, z <xref:System.Windows.Forms.Control?displayProperty=nameWithType>których dziedziczy:  
  
- <xref:System.Windows.Forms.Control.OnBackColorChanged%2A>  
  
- <xref:System.Windows.Forms.Control.OnBackgroundImageChanged%2A>  
  
- <xref:System.Windows.Forms.Control.OnTextChanged%2A>  
  
## <a name="example"></a>Przykład  
 Kontrolka definiuje dwa `FlashTrackBarValueEditor` edytory typów interfejsu użytkownika `FlashTrackBarDarkenByEditor`i, które są wyświetlane w poniższych listach kodu. `FlashTrackBar` `HostApp` Klasa`FlashTrackBar` używa kontrolki w formularzu systemu Windows.  
  
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
