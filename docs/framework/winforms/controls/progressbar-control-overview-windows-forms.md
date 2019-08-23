---
title: ProgressBar — Informacje o formancie [Formularze systemu Windows]
ms.date: 03/30/2017
f1_keywords:
- ProgressBar
helpviewer_keywords:
- ProgressBar control [Windows Forms], about ProgressBar control
- progress controls [Windows Forms], about progress controls
ms.assetid: a05d9cba-3a6a-4f8f-94b8-8ec12799fb80
ms.openlocfilehash: 7dd434492cd688527ddbce5aaffa442a0b40a9e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968319"
---
# <a name="progressbar-control-overview-windows-forms"></a>ProgressBar — Informacje o formancie [Formularze systemu Windows]
> [!IMPORTANT]
> Formant zastępuje i dodaje funkcję <xref:System.Windows.Forms.ProgressBar> do <xref:System.Windows.Forms.ProgressBar> kontrolki; jednak kontrolka jest zachowywana w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości, jeśli wybierzesz opcję. <xref:System.Windows.Forms.ToolStripProgressBar>  
  
 Formant Windows Forms <xref:System.Windows.Forms.ProgressBar> wskazuje postęp procesu przez wyświetlenie odpowiedniej liczby prostokątów uporządkowanych na poziomym pasku. Po zakończeniu procesu pasek zostanie wypełniony. Paski postępu są często używane do nadania użytkownikowi pomysłu na czas oczekiwania na ukończenie procesu; na przykład, gdy ładowany jest duży plik.  
  
> [!NOTE]
> <xref:System.Windows.Forms.ProgressBar> Formant może być zorientowany w poziomie tylko w formularzu.  
  
## <a name="key-properties-and-methods"></a>Właściwości i metody klucza  
 Właściwości <xref:System.Windows.Forms.ProgressBar> klucza kontrolki to <xref:System.Windows.Forms.ProgressBar.Value%2A>, <xref:System.Windows.Forms.ProgressBar.Minimum%2A>, i <xref:System.Windows.Forms.ProgressBar.Maximum%2A>. Właściwości <xref:System.Windows.Forms.ProgressBar.Minimum%2A> i<xref:System.Windows.Forms.ProgressBar.Maximum%2A> ustawiają maksymalne i minimalne wartości, które pasek postępu może wyświetlać. <xref:System.Windows.Forms.ProgressBar.Value%2A> Właściwość reprezentuje postęp, który został wykonany w kierunku ukończenia operacji. Ponieważ pasek wyświetlany w kontrolce składa się z bloków, wartość wyświetlana przez <xref:System.Windows.Forms.ProgressBar> formant tylko przybliża <xref:System.Windows.Forms.ProgressBar.Value%2A> bieżącą wartość właściwości. Na podstawie rozmiaru <xref:System.Windows.Forms.ProgressBar> kontrolki <xref:System.Windows.Forms.ProgressBar.Value%2A> Właściwość określa, kiedy ma być wyświetlany następny blok.  
  
 Najbardziej typowym sposobem na Zaktualizowanie bieżącej wartości postępu jest napisanie kodu w celu ustawienia <xref:System.Windows.Forms.ProgressBar.Value%2A> właściwości. W przykładzie ładowania dużego pliku można ustawić maksymalny rozmiar pliku w kilobajtach. Na przykład, jeśli <xref:System.Windows.Forms.ProgressBar.Maximum%2A> właściwość jest ustawiona na 100 <xref:System.Windows.Forms.ProgressBar.Minimum%2A> , właściwość jest ustawiona na wartość 10, a <xref:System.Windows.Forms.ProgressBar.Value%2A> właściwość jest ustawiona na 50, zostaną wyświetlone 5 prostokątów. Jest to połowa liczby, która może być wyświetlana.  
  
 Istnieją jednak inne sposoby modyfikacji wartości wyświetlanej przez <xref:System.Windows.Forms.ProgressBar> formant, poza <xref:System.Windows.Forms.ProgressBar.Value%2A> ustawieniem właściwości bezpośrednio. Właściwość może służyć do określania wartości, aby <xref:System.Windows.Forms.ProgressBar.Value%2A> zwiększyć Właściwość przez. <xref:System.Windows.Forms.ProgressBar.Step%2A> Następnie wywołanie <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> metody spowoduje zwiększenie wartości. Aby zmienić wartość przyrostu, można użyć <xref:System.Windows.Forms.ProgressBar.Increment%2A> metody i określić wartość, z którą ma zostać <xref:System.Windows.Forms.ProgressBar.Value%2A> zwiększona właściwość.  
  
 Inny formant, który graficznie informuje użytkownika o bieżącej akcji jest <xref:System.Windows.Forms.StatusBar> formantem.  
  
> [!IMPORTANT]
> <xref:System.Windows.Forms.StatusBarPanel> <xref:System.Windows.Forms.StatusBarPanel> <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.StatusBar> Formanty i zastępują i dodają funkcje do kontrolek i, natomiast kontrolki i są zachowywane w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości. <xref:System.Windows.Forms.StatusStrip> <xref:System.Windows.Forms.ToolStripStatusLabel> następnie.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ProgressBar>
- [ProgressBar, kontrolka](progressbar-control-windows-forms.md)
