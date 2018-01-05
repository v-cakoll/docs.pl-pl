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
ms.workload: dotnet
ms.openlocfilehash: 7cc62780579c852aaa637a3ccc13ce2929423868
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="mouse-capture-in-windows-forms"></a>Przechwytywanie myszy w formularzach systemu Windows
*Przechwytywanie myszy* odwołuje się do formantu wprowadzającymi polecenia myszy wszystkich danych wejściowych. Po przechwyceniu myszy formantu odbiera myszą czy kursor znajduje się w jej granicach.  
  
## <a name="setting-mouse-capture"></a>Ustawienie przechwytywania myszy  
 W formularzach systemu Windows są przechwytywane przez formant myszy, gdy użytkownik naciśnie przycisk myszy w formancie i mysz został wydany przez formant, gdy użytkownik zwolni przycisk myszy.  
  
 <xref:System.Windows.Forms.Control.Capture%2A> Właściwość <xref:System.Windows.Forms.Control> klasy określa, czy formant ma przechwytywane myszy. Aby określić, gdy formant utraci przechwytywanie myszy, obsługi <xref:System.Windows.Forms.Control.MouseCaptureChanged> zdarzeń.  
  
 Tylko okna pierwszoplanowego można przechwytywanie myszy. Gdy oknem tła próbuje przechwytywanie myszy, okno odbiera wiadomości tylko w przypadku zdarzeń myszy, gdy wskaźnik myszy znajduje się w widoczną część okna. Ponadto nawet wtedy, gdy przechwyceniu myszy okna pierwszoplanowego użytkownik może nadal kliknąć inne okno jej przejściem w tryb na pierwszy plan. Po przechwyceniu myszy klawiszy skrótów nie działa.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzanie za pomocą myszy w aplikacjach Windows Forms](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
