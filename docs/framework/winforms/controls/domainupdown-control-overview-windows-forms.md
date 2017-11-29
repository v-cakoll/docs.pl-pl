---
title: "DomainUpDown — Informacje o formancie [Formularze systemu Windows]"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DomainUpDown
helpviewer_keywords:
- spin button control [Windows Forms], about spin button
- DomainUpDown control [Windows Forms], about DomainUpDown control
ms.assetid: 3f40f9c1-20ad-4331-b9b5-b0127eb36eb3
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a0692677b8ef596bb31b1869480603573a9ec98d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="domainupdown-control-overview-windows-forms"></a>DomainUpDown — Informacje o formancie [Formularze systemu Windows]
Formularze systemu Windows <xref:System.Windows.Forms.DomainUpDown> formant jest zasadniczo kombinację pola tekstowego, a para przyciski przenoszenia w górę lub w dół listy. Kontrolka Wyświetla i ustawia ciąg tekstowy, z listy dostępnych opcji. Użytkownik może wybrać ciąg, kilikając przyciski, aby przejść na liście, naciskając klawisze strzałek w górę i w dół lub wpisując ciąg zgodny element na liście. Jeden możliwości zastosowania dla tego formantu jest wybierania elementów z posortowane alfabetycznie listę nazw.  
  
> [!NOTE]
>  Aby posortować listę, należy ustawić <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> właściwości `true`.  
  
 Funkcja tego formantu jest bardzo podobny do pola listy lub pola kombi, ale zajmuje on bardzo mało miejsca.  
  
## <a name="key-properties"></a>Właściwości klucza  
 Właściwości klucza formantu są <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, i <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>. <xref:System.Windows.Forms.DomainUpDown.Items%2A> Właściwość zawiera listę obiektów, których wartości tekstowe są wyświetlane w formancie. Jeśli <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> ma ustawioną wartość `false`, formantu automatycznie wykonuje tekstu, czy użytkownik, typy i dopasowuje je do wartości na liście. Jeśli <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> ma ustawioną wartość `true`, przewijanie poza ostatni element spowoduje przejście do pierwszego elementu na liście i na odwrót. Metody klucza formantu są <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> i <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.  
  
 Ten formant wyświetla tylko ciągi. Formant, który wyświetla wartości liczbowe, należy użyć <xref:System.Windows.Forms.NumericUpDown> formantu. Aby uzyskać więcej informacji, zobacz [informacje o formancie NumericUpDown](../../../../docs/framework/winforms/controls/numericupdown-control-overview-windows-forms.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DomainUpDown>  
 [DomainUpDown — formant](../../../../docs/framework/winforms/controls/domainupdown-control-windows-forms.md)
