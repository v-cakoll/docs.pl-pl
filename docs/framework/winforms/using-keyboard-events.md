---
title: "Używanie zdarzeń klawiatury"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- KeyPress event [Windows Forms]
- keyboards [Windows Forms], keyboard events
- KeyUp event
- KeyDown event
- keyboard events
- events [Windows Forms], keyboard
ms.assetid: d3f3e14b-a459-4ee6-9875-8957e34f8ee9
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 394ebc503338ad73001aa9859e0aa0d9c3fa42b4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="using-keyboard-events"></a>Używanie zdarzeń klawiatury
Większość programów formularzy systemu Windows przetwarzania danych wprowadzonych z klawiatury poprzez obsługi zdarzenia klawiatury. Ten temat zawiera omówienie zdarzenia klawiatury, w tym informacji o tym, kiedy należy używać każdego zdarzenia i dane, które jest dostarczone dla każdego zdarzenia.  Zobacz też [Przegląd obsługi zdarzeń (formularze systemu Windows)](http://msdn.microsoft.com/library/be6fx1bb\(v=vs.110\)), [Przegląd zdarzeń (formularze systemu Windows)](http://msdn.microsoft.com/library/1h12f09z\(v=vs.110\)).  
  
## <a name="keyboard-events"></a>Zdarzenia klawiatury  
 Formularze systemu Windows udostępnia dwa zdarzenia, które wystąpić, gdy użytkownik naciśnie klawisz i jedno zdarzenie, gdy użytkownik zwolni klawisz:  
  
-   <xref:System.Windows.Forms.Control.KeyDown> Po wystąpieniu zdarzenia  
  
-   <xref:System.Windows.Forms.Control.KeyPress> Zdarzenie, które mogą wystąpić wiele razy, gdy użytkownik posiada w dół tego samego klucza.  
  
-   <xref:System.Windows.Forms.Control.KeyUp> Zdarzenie po gdy użytkownik zwolni klawisz.  
  
 Po naciśnięciu klawisza, formularzy systemu Windows określa, które zdarzeń, aby podnieść oparte na czy komunikatów klawiatury określa znakowy klucz lub klucz fizycznych. Aby uzyskać więcej informacji o znaków i fizycznej kluczy, zobacz [sposób działania wejście klawiatury](../../../docs/framework/winforms/how-keyboard-input-works.md).  
  
 W poniższej tabeli opisano zdarzenia klawiatury trzy.  
  
|Zdarzenia klawiatury|Opis|Wyniki|  
|--------------------|-----------------|-------------|  
|<xref:System.Windows.Forms.Control.KeyDown>|To zdarzenie jest wywoływane, gdy użytkownik naciśnie klawisz fizycznych.|Program obsługi dla <xref:System.Windows.Forms.Control.KeyDown> odbiera:<br /><br /> <ul><li>A <xref:System.Windows.Forms.KeyEventArgs> parametru zapewnia <xref:System.Windows.Forms.KeyEventArgs.KeyCode%2A> właściwości (który określa przycisku klawiatury fizycznych).</li><li><xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> Właściwości (SHIFT, CTRL lub ALT).</li><li><xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> Właściwości (które łączy kod klucza i modyfikatora). <xref:System.Windows.Forms.KeyEventArgs> Udostępnia również parametr:<br /><br /> <ul><li><xref:System.Windows.Forms.KeyEventArgs.Handled%2A> Właściwość, którą można ustawić, aby uniemożliwić odbieranie klucz podstawowy formantu.</li><li><xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A> Właściwość, która może służyć do pomijania <xref:System.Windows.Forms.Control.KeyPress> i <xref:System.Windows.Forms.Control.KeyUp> zdarzeń związanych z tym naciśnięcie klawisza.</li></ul></li></ul>|  
|<xref:System.Windows.Forms.Control.KeyPress>|To zdarzenie jest wywoływane po klucz lub klucze wynik znakiem. Na przykład naciśnięciu klawisza SHIFT i małej litery "" klucze, które powoduje wielkiej litery "" znaków.|<xref:System.Windows.Forms.Control.KeyPress>jest wywoływane po wykonaniu <xref:System.Windows.Forms.Control.KeyDown>.<br /><br /> <ul><li>Program obsługi dla <xref:System.Windows.Forms.Control.KeyPress> odbiera:</li><li>A <xref:System.Windows.Forms.KeyPressEventArgs> parametr, który zawiera kod znaku klucza, który został naciśnięty. Ten kod znaku jest unikatowa dla każdej kombinacji znakowy klucz i klawisz modyfikujący.<br /><br />     Na przykład generuje klucz "":<br /><br /> <ul><li>Kod znaku 65, gdy zostanie naciśnięty klawisz SHIFT</li><li>Lub klawisz CAPS LOCK 97, gdy zostanie naciśnięty</li><li>I 1, gdy zostanie naciśnięty klawisz CTRL.</li></ul></li></ul>|  
|<xref:System.Windows.Forms.Control.KeyUp>|To zdarzenie jest wywoływane, gdy użytkownik zwolni klawisz fizycznych.|Program obsługi dla <xref:System.Windows.Forms.Control.KeyUp> odbiera:<br /><br /> <ul><li>A <xref:System.Windows.Forms.KeyEventArgs> parametru:<br /><br /> <ul><li>Zapewniające <xref:System.Windows.Forms.KeyEventArgs.KeyCode%2A> właściwości (który określa przycisku klawiatury fizycznych).</li><li><xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> Właściwości (SHIFT, CTRL lub ALT).</li><li><xref:System.Globalization.SortKey.KeyData%2A> Właściwości (które łączy kod klucza i modyfikatora).</li></ul></li></ul>|  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzanie z klawiatury w aplikacjach Windows Forms](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)  
 [Działanie wprowadzania z klawiatury](../../../docs/framework/winforms/how-keyboard-input-works.md)  
 [Wprowadzanie za pomocą myszy w aplikacjach Windows Forms](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
