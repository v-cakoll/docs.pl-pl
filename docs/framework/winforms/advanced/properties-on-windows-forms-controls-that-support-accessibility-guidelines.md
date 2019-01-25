---
title: Właściwości formantów formularzy systemu Windows obsługujące dostęp — Wytyczne
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, accessibility properties of controls
- accessibility [Windows Forms], Windows Forms control properties
ms.assetid: ad3567a6-313b-4708-9e15-f487a831f049
ms.openlocfilehash: b731f277620925a333c8d9eba64c8900674327da
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54552216"
---
# <a name="properties-on-windows-forms-controls-that-support-accessibility-guidelines"></a>Właściwości formantów formularzy systemu Windows obsługujące dostęp — Wytyczne
Formanty standardowe przyborniku dla formularzy Windows Forms obsługują wiele wytyczne dotyczące ułatwień dostępu, w tym udostępnianie fokus klawiatury i udostępnianie elementów na ekranie.  
  
## <a name="planning-ahead-for-accessibility"></a>Planowanie z uwzględnieniem ułatwień dostępu  
 Właściwości kontrolek może służyć do obsługi innych wytyczne dotyczące ułatwień dostępu, jak pokazano w poniższej tabeli. Ponadto należy używać menu, aby zapewnić dostęp do funkcji programu.  
  
|Właściwości kontrolki|Zagadnienia dotyczące ułatwień dostępu|  
|----------------------|--------------------------------------|  
|AccessibleDescription|Opis jest zgłaszany do narzędzi ułatwień dostępu, takich jak czytniki zawartości ekranu. Narzędzi ułatwień dostępu są programy specjalistyczne i urządzenia, które pomagają osobom niepełnosprawnym bardziej efektywne wykorzystanie komputerów.|  
|AccessibleName|Nazwa, która będzie zgłaszana w odniesieniu do ułatwień dostępu pomocy.|  
|AccessibleRole|Opisuje elementu w interfejsie użytkownika.|  
|TabIndex|Tworzy rozsądne ścieżkę nawigacyjną, za pomocą formularza. Jest to ważne w przypadku kontrolek bez użycia etykiet wewnętrzne, takie jak pola tekstowe, aby ich etykiety skojarzone bezpośrednio poprzedzać je w kolejności tabulacji.|  
|Tekst|Użyj znaku "&", aby utworzyć klucze dostępu. Za pomocą kluczy dostępu jest częścią udostępniające udokumentowanego klawiatury do funkcji.|  
|Rozmiar czcionki|Jeśli rozmiar czcionki nie jest zmieniane, następnie należy ją ustawić do 10 punktów i większych. Po ustawieniu rozmiar czcionki wszystkich kontrolek, które są dodawane do formularza po tej dacie będą mieć taki sam rozmiar.|  
|ForeColor|Jeśli ta właściwość jest ustawiona na domyślną, preferencji koloru użytkownika będą używane w formularzu.|  
|Backcolor|Jeśli ta właściwość jest ustawiona na domyślną, preferencji koloru użytkownika będą używane w formularzu.|  
|BackgroundImage|Ta właściwość pozostaw pustą wartość, aby zwiększyć czytelność tekstu.|  
  
## <a name="see-also"></a>Zobacz także
- [Przewodnik: Tworzenie dostępnej aplikacji z systemem Windows](../../../../docs/framework/winforms/advanced/walkthrough-creating-an-accessible-windows-based-application.md)
