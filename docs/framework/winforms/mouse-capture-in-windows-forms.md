---
title: Przechwytywanie myszy w formularzach systemu Windows
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: mouse [Windows Forms], capture
ms.assetid: 8911d4b0-a4f8-4f93-8246-371aebd27d0c
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8004b05ea25341a142bfcfd9ae812ee3bebd6d5b
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="mouse-capture-in-windows-forms"></a>Przechwytywanie myszy w formularzach systemu Windows
*Przechwytywanie myszy* odwołuje się do formantu wprowadzającymi polecenia myszy wszystkich danych wejściowych. Po przechwyceniu myszy formantu odbiera myszą czy kursor znajduje się w jej granicach.  
  
## <a name="setting-mouse-capture"></a>Ustawienie przechwytywania myszy  
 W formularzach systemu Windows są przechwytywane przez formant myszy, gdy użytkownik naciśnie przycisk myszy w formancie i mysz został wydany przez formant, gdy użytkownik zwolni przycisk myszy.  
  
 <xref:System.Windows.Forms.Control.Capture%2A> Właściwość <xref:System.Windows.Forms.Control> klasy określa, czy formant ma przechwytywane myszy. Aby określić, gdy formant utraci przechwytywanie myszy, obsługi <xref:System.Windows.Forms.Control.MouseCaptureChanged> zdarzeń.  
  
 Tylko okna pierwszoplanowego można przechwytywanie myszy. Gdy oknem tła próbuje przechwytywanie myszy, okno odbiera wiadomości tylko w przypadku zdarzeń myszy, gdy wskaźnik myszy znajduje się w widoczną część okna. Ponadto nawet wtedy, gdy przechwyceniu myszy okna pierwszoplanowego użytkownik może nadal kliknąć inne okno jej przejściem w tryb na pierwszy plan. Po przechwyceniu myszy klawiszy skrótów nie działa.  
  
## <a name="see-also"></a>Zobacz też  
 [Wejście myszy w systemie Windows formularzy aplikacji](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
