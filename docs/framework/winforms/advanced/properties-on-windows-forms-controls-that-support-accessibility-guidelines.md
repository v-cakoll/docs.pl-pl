---
title: Właściwości ułatwień dostępu w kontrolkach
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, accessibility properties of controls
- accessibility [Windows Forms], Windows Forms control properties
ms.assetid: ad3567a6-313b-4708-9e15-f487a831f049
ms.openlocfilehash: 73d81f5b5f656ed5ef90bdd9b6fe1b3293123f97
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743424"
---
# <a name="properties-on-windows-forms-controls-that-support-accessibility-guidelines"></a>Właściwości formantów formularzy systemu Windows obsługujące dostęp — Wytyczne
Kontrolki standardowego zestawu narzędzi dla Windows Forms obsługują wiele wytycznych dotyczących ułatwień dostępu, w tym Uwidacznianie fokusu klawiatury i Uwidacznianie elementów ekranu.  
  
## <a name="planning-ahead-for-accessibility"></a>Planowanie przed ułatwieniami dostępu  
 Właściwości formantów mogą służyć do obsługi innych wytycznych dotyczących ułatwień dostępu, jak pokazano w poniższej tabeli. Ponadto należy użyć menu, aby zapewnić dostęp do funkcji programu.  
  
|Właściwość kontrolki|Zagadnienia dotyczące ułatwień dostępu|  
|----------------------|--------------------------------------|  
|AccessibleDescription|Opis jest raportowany do pomocy ułatwień dostępu, takich jak czytniki zawartości ekranu. Ułatwienia dostępu są wyspecjalizowanymi programami i urządzeniami, które ułatwiają osobom niepełnosprawnym korzystanie z komputerów.|  
|AccessibleName|Nazwa, która będzie raportowana do pomocy ułatwień dostępu.|  
|AccessibleRole|Opisuje użycie elementu w interfejsie użytkownika.|  
|TabIndex|Tworzy rozsądną ścieżkę nawigacyjną w formularzu. Należy pamiętać o kontrolkach bez etykiet wewnętrznych, takich jak pola tekstowe, aby skojarzyć ich etykiety bezpośrednio z kolejnością tabulacji.|  
|Tekst|Użyj znaku "&", aby utworzyć klucze dostępu. Korzystanie z kluczy dostępu jest częścią udostępniania udokumentowanego dostępu klawiaturowego do funkcji.|  
|Rozmiar czcionki|Jeśli rozmiar czcionki nie jest zmieniany, należy ustawić na 10 punktów lub większą. Po ustawieniu rozmiaru czcionki formularza wszystkie kontrolki dodane do formularza będą miały ten sam rozmiar.|  
|ForeColor|Jeśli ta właściwość jest ustawiona na wartość domyślną, preferencje koloru użytkownika będą używane w formularzu.|  
|BackColor|Jeśli ta właściwość jest ustawiona na wartość domyślną, preferencje koloru użytkownika będą używane w formularzu.|  
|BackgroundImage|Pozostaw tę właściwość pustą, aby zwiększyć czytelność tekstu.|  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik: tworzenie dostępnej aplikacji bazującej na systemie Windows](walkthrough-creating-an-accessible-windows-based-application.md)
