---
title: ProgressBar — Informacje o formancie [Formularze systemu Windows]
ms.date: 03/30/2017
f1_keywords:
- ProgressBar
helpviewer_keywords:
- ProgressBar control [Windows Forms], about ProgressBar control
- progress controls [Windows Forms], about progress controls
ms.assetid: a05d9cba-3a6a-4f8f-94b8-8ec12799fb80
ms.openlocfilehash: 65533bc8f9125666e39c53635f5798573f66ef14
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54523184"
---
# <a name="progressbar-control-overview-windows-forms"></a>ProgressBar — Informacje o formancie [Formularze systemu Windows]
> [!IMPORTANT]
>  <xref:System.Windows.Forms.ToolStripProgressBar> Kontroli zastępuje i dodaje funkcjonalność do <xref:System.Windows.Forms.ProgressBar> kontrolować; jednak <xref:System.Windows.Forms.ProgressBar> kontrolki została zachowana na potrzeby zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli wybierzesz.  
  
 Formularze Windows <xref:System.Windows.Forms.ProgressBar> formant wskazuje postęp procesu, wyświetlając odpowiednią liczbę prostokąty ułożone w poziomym pasku. Po zakończeniu procesu zostanie wypełniony pasku. Paski postępu są często używane, aby przyznać użytkownikowi pomysł, jak długie oczekiwania na ukończenie; procesu na przykład, gdy duże pliki są ładowane.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ProgressBar> Kontroli tylko może być orientacji poziomej w formularzu.  
  
## <a name="key-properties-and-methods"></a>Kluczowe właściwości i metody  
 Właściwości klucza obiektu <xref:System.Windows.Forms.ProgressBar> sterowania stanowią <xref:System.Windows.Forms.ProgressBar.Value%2A>, <xref:System.Windows.Forms.ProgressBar.Minimum%2A>, i <xref:System.Windows.Forms.ProgressBar.Maximum%2A>. <xref:System.Windows.Forms.ProgressBar.Minimum%2A> i <xref:System.Windows.Forms.ProgressBar.Maximum%2A> właściwości ustawione wartości maksymalne i minimalne, można wyświetlić pasek postępu. <xref:System.Windows.Forms.ProgressBar.Value%2A> Właściwość reprezentuje postęp, którego dokonano ukończenia operacji. Ponieważ wyświetlany w kontrolce pasek składa się z bloków, wartość wyświetlana przez <xref:System.Windows.Forms.ProgressBar> kontroli tylko przybliża <xref:System.Windows.Forms.ProgressBar.Value%2A> bieżącej wartości właściwości. Na podstawie rozmiaru <xref:System.Windows.Forms.ProgressBar> kontroli <xref:System.Windows.Forms.ProgressBar.Value%2A> właściwość określa, kiedy należy wyświetlić kolejny blok.  
  
 Najczęstszym sposobem zaktualizowania bieżącej wartości postęp jest napisać kod ustawiający <xref:System.Windows.Forms.ProgressBar.Value%2A> właściwości. W przykładzie ładowania dużych plików może ustawiona maksymalny rozmiar pliku w kilobajtach. Na przykład jeśli <xref:System.Windows.Forms.ProgressBar.Maximum%2A> właściwość jest ustawiona na 100, <xref:System.Windows.Forms.ProgressBar.Minimum%2A> właściwość jest ustawiona na 10 i <xref:System.Windows.Forms.ProgressBar.Value%2A> właściwość jest ustawiona na 50, pojawi się 5 prostokąty. Jest to połowę numer, który może być wyświetlany.  
  
 Istnieją inne sposoby, aby zmodyfikować wartości wyświetlanej przez <xref:System.Windows.Forms.ProgressBar> kontrolki, oprócz ustawienie <xref:System.Windows.Forms.ProgressBar.Value%2A> właściwość bezpośrednio. <xref:System.Windows.Forms.ProgressBar.Step%2A> Właściwość może służyć do określania wartość do zwiększenia <xref:System.Windows.Forms.ProgressBar.Value%2A> właściwość, według. Następnie podczas wywoływania <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> metody powoduje zwiększenie wartości. Aby różnią się wartość przyrostu, można użyć <xref:System.Windows.Forms.ProgressBar.Increment%2A> metody i określ wartość, z którym się zwiększać <xref:System.Windows.Forms.ProgressBar.Value%2A> właściwości.  
  
 Jest inna kontrolka, która graficznie informuje użytkownika o bieżącej akcji <xref:System.Windows.Forms.StatusBar> kontroli.  
  
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip> i <xref:System.Windows.Forms.ToolStripStatusLabel> kontrolki Zastąp i dodawania funkcjonalności do <xref:System.Windows.Forms.StatusBar> i <xref:System.Windows.Forms.StatusBarPanel> kontroluje; jednak <xref:System.Windows.Forms.StatusBar> i <xref:System.Windows.Forms.StatusBarPanel> kontrolek zostaną zachowane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli możesz Wybierz.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.ProgressBar>
- [ProgressBar, kontrolka](../../../../docs/framework/winforms/controls/progressbar-control-windows-forms.md)
