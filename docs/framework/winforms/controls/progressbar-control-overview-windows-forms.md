---
title: ProgressBar — Informacje o formancie
ms.date: 03/30/2017
f1_keywords:
- ProgressBar
helpviewer_keywords:
- ProgressBar control [Windows Forms], about ProgressBar control
- progress controls [Windows Forms], about progress controls
ms.assetid: a05d9cba-3a6a-4f8f-94b8-8ec12799fb80
ms.openlocfilehash: a0c4a0401d06614ab3ad148b932ebc64080c592c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741281"
---
# <a name="progressbar-control-overview-windows-forms"></a>ProgressBar — Informacje o formancie [Formularze systemu Windows]
> [!IMPORTANT]
> Formant <xref:System.Windows.Forms.ToolStripProgressBar> zamienia i dodaje funkcje do kontrolki <xref:System.Windows.Forms.ProgressBar>; Niemniej jednak kontrolka <xref:System.Windows.Forms.ProgressBar> jest zachowywana na potrzeby zgodności z poprzednimi wersjami i w przyszłości.  
  
 Kontrolka <xref:System.Windows.Forms.ProgressBar> Windows Forms wskazuje postęp procesu, wyświetlając odpowiednią liczbę prostokątów uporządkowaną na poziomym pasku. Po zakończeniu procesu pasek zostanie wypełniony. Paski postępu są często używane do nadania użytkownikowi pomysłu na czas oczekiwania na ukończenie procesu; na przykład, gdy ładowany jest duży plik.  
  
> [!NOTE]
> Formant <xref:System.Windows.Forms.ProgressBar> może być zorientowany w poziomie tylko w formularzu.  
  
## <a name="key-properties-and-methods"></a>Właściwości i metody klucza  
 Właściwości klucza kontrolki <xref:System.Windows.Forms.ProgressBar> są <xref:System.Windows.Forms.ProgressBar.Value%2A>, <xref:System.Windows.Forms.ProgressBar.Minimum%2A>i <xref:System.Windows.Forms.ProgressBar.Maximum%2A>. Właściwości <xref:System.Windows.Forms.ProgressBar.Minimum%2A> i <xref:System.Windows.Forms.ProgressBar.Maximum%2A> ustawiają maksymalne i minimalne wartości, które pasek postępu może wyświetlać. Właściwość <xref:System.Windows.Forms.ProgressBar.Value%2A> reprezentuje postęp, który został wykonany w kierunku ukończenia operacji. Ponieważ pasek wyświetlany w kontrolce składa się z bloków, wartość wyświetlana przez formant <xref:System.Windows.Forms.ProgressBar> jedynie przybliża bieżącą wartość właściwości <xref:System.Windows.Forms.ProgressBar.Value%2A>. Na podstawie rozmiaru kontrolki <xref:System.Windows.Forms.ProgressBar> Właściwość <xref:System.Windows.Forms.ProgressBar.Value%2A> określa, kiedy ma być wyświetlany następny blok.  
  
 Najbardziej typowym sposobem na Zaktualizowanie bieżącej wartości postępu jest pisanie kodu w celu ustawienia właściwości <xref:System.Windows.Forms.ProgressBar.Value%2A>. W przykładzie ładowania dużego pliku można ustawić maksymalny rozmiar pliku w kilobajtach. Na przykład, jeśli właściwość <xref:System.Windows.Forms.ProgressBar.Maximum%2A> jest ustawiona na 100, właściwość <xref:System.Windows.Forms.ProgressBar.Minimum%2A> ma wartość 10, a właściwość <xref:System.Windows.Forms.ProgressBar.Value%2A> jest ustawiona na 50, zostaną wyświetlone 5 prostokątów. Jest to połowa liczby, która może być wyświetlana.  
  
 Istnieją jednak inne sposoby modyfikacji wartości wyświetlanej przez formant <xref:System.Windows.Forms.ProgressBar>, poza ustawieniem właściwości <xref:System.Windows.Forms.ProgressBar.Value%2A>. Właściwość <xref:System.Windows.Forms.ProgressBar.Step%2A> może służyć do określania wartości, aby zwiększyć Właściwość <xref:System.Windows.Forms.ProgressBar.Value%2A> przez. Następnie wywołanie metody <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> spowoduje zwiększenie wartości. Aby zmienić wartość przyrostu, można użyć metody <xref:System.Windows.Forms.ProgressBar.Increment%2A> i określić wartość, z którą ma zostać zwiększona Właściwość <xref:System.Windows.Forms.ProgressBar.Value%2A>.  
  
 Inny formant, który graficznie informuje użytkownika o bieżącej akcji jest formantem <xref:System.Windows.Forms.StatusBar>.  
  
> [!IMPORTANT]
> Kontrolki <xref:System.Windows.Forms.StatusStrip> i <xref:System.Windows.Forms.ToolStripStatusLabel> zastępują i dodają funkcje do kontrolek <xref:System.Windows.Forms.StatusBar> i <xref:System.Windows.Forms.StatusBarPanel>; jednak kontrolki <xref:System.Windows.Forms.StatusBar> i <xref:System.Windows.Forms.StatusBarPanel> są zachowywane w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości, jeśli wybierzesz opcję.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ProgressBar>
- [ProgressBar, kontrolka](progressbar-control-windows-forms.md)
