---
title: "Właściwości formantów formularzy systemu Windows obsługujące dostęp — Wytyczne"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, accessibility properties of controls
- accessibility [Windows Forms], Windows Forms control properties
ms.assetid: ad3567a6-313b-4708-9e15-f487a831f049
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 967b4a0e883338c756aceef37d11edecfb978527
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="properties-on-windows-forms-controls-that-support-accessibility-guidelines"></a>Właściwości formantów formularzy systemu Windows obsługujące dostęp — Wytyczne
Formanty standardowe przyborniku dla formularzy systemu Windows obsługują wiele wytycznych ułatwień dostępu, w tym udostępnianie fokus klawiatury i udostępnianie elementów ekranu.  
  
## <a name="planning-ahead-for-accessibility"></a>Planowanie wyprzedzeniem ułatwień dostępu  
 Właściwości formantów mogą służyć do obsługi innych dostęp — wytyczne, jak pokazano w poniższej tabeli. Ponadto należy używać menu, aby zapewnić dostęp do funkcji programu.  
  
|Właściwość formantu|Zagadnienia dotyczące ułatwień dostępu|  
|----------------------|--------------------------------------|  
|AccessibleDescription|Opis jest zgłaszane do narzędzi ułatwień dostępu, takich jak czytniki ekranu. Narzędzi ułatwień dostępu są programy specjalistyczne i urządzenia, które pomagają osób niepełnosprawnych komputerów wydajniej wykorzystywać.|  
|AccessibleName|Nazwa przekazywana do narzędzi ułatwień dostępu.|  
|AccessibleRole|Opisuje elementu w interfejsie użytkownika.|  
|TabIndex|Tworzy ścieżkę nawigacyjną za pośrednictwem za pomocą formularza. Jest ważne dla formantów bez etykiet wewnętrznych, takich jak pola tekstowe, ich skojarzone etykiety poprzedzają w kolejności tabulacji.|  
|Tekst|Użyj znaku "&", aby utworzyć klucze dostępu. Za pomocą klawiszy dostępu jest częścią klawiaturę udokumentowaną dostępowi do funkcji.|  
|Rozmiar czcionki|Jeśli rozmiar czcionki nie jest regulowany, następnie go ustawić punkty 10 lub większą. Po ustawieniu formularza rozmiar czcionki, wszystkie formanty, które są następnie dodany do formularza będą miały taki sam rozmiar.|  
|ForeColor|Jeśli ta właściwość ma ustawioną wartość domyślna, preferencje kolorów dla użytkownika będą używane w formularzu.|  
|Kolor tła|Jeśli ta właściwość ma ustawioną wartość domyślna, preferencje kolorów dla użytkownika będą używane w formularzu.|  
|BackgroundImage|Pozostaw pole puste, aby zwiększyć czytelność tekstu tej właściwości.|  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: tworzenie dostępnej aplikacji bazującej na systemie Windows](../../../../docs/framework/winforms/advanced/walkthrough-creating-an-accessible-windows-based-application.md)
