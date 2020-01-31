---
title: TrackBar — Informacje o formancie
ms.date: 03/30/2017
f1_keywords:
- TrackBar
helpviewer_keywords:
- sliders [Windows Forms], about sliders
- TrackBar control [Windows Forms], about TrackBar control
- slider controls [Windows Forms], about slider controls
ms.assetid: 95910ecb-8a4c-4776-89fa-206c89ed6973
ms.openlocfilehash: 6901405100df4633c84850757f55b756bc9a0199
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741467"
---
# <a name="trackbar-control-overview-windows-forms"></a>TrackBar — Informacje o formancie [Formularze systemu Windows]
Kontrolka <xref:System.Windows.Forms.TrackBar> Windows Forms (niekiedy nazywana również kontrolką "Slider") służy do nawigowania w dużej ilości informacji lub wizualnego dostosowywania ustawienia liczbowego. Kontrolka <xref:System.Windows.Forms.TrackBar> ma dwie części: pasek przewijania, znany również jako suwak i znaczniki. Kciuk jest częścią, którą można dostosować. Jego pozycja odpowiada właściwości <xref:System.Windows.Forms.TrackBar.Value%2A>. Znaczniki są wskaźnikami wizualizacji, które są odstępie w regularnych odstępach czasu. TrackBar przenosi w przyrostach, które określisz, i mogą być wyrównane w poziomie lub w pionie. Na przykład możesz użyć paska śledzenia, aby kontrolować częstotliwość migania kursora lub szybkość myszy dla systemu.  
  
## <a name="key-properties"></a>Właściwości klucza  
 Właściwości klucza kontrolki <xref:System.Windows.Forms.TrackBar> są <xref:System.Windows.Forms.TrackBar.Value%2A>, <xref:System.Windows.Forms.TrackBar.TickFrequency%2A>, <xref:System.Windows.Forms.TrackBar.Minimum%2A>i <xref:System.Windows.Forms.TrackBar.Maximum%2A>. <xref:System.Windows.Forms.TrackBar.TickFrequency%2A> jest odstępy między taktami. <xref:System.Windows.Forms.TrackBar.Minimum%2A> i <xref:System.Windows.Forms.TrackBar.Maximum%2A> to najmniejsza i największa wartość, którą można przedstawić na pasku śledzenia.  
  
 Dwie inne ważne właściwości to <xref:System.Windows.Forms.TrackBar.SmallChange%2A> i <xref:System.Windows.Forms.TrackBar.LargeChange%2A>. Wartość właściwości <xref:System.Windows.Forms.TrackBar.SmallChange%2A> to liczba pozycji, jaką przesuwa się kciuk w odpowiedzi na naciśnięcie klawisza Strzałka w lewo lub w prawo. Wartość właściwości <xref:System.Windows.Forms.TrackBar.LargeChange%2A> to liczba pozycji, jaką przesuwa się kciuk w odpowiedzi na naciśnięcie klawisza PAGE UP lub PAGE DOWN lub w odpowiedzi na kliknięcie myszy na pasku śledzenia po obu stronach przycisku przewijania.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.TrackBar>
- [TrackBar, kontrolka](trackbar-control-windows-forms.md)
