---
title: "Współrzędne formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms coordinates
- screen coordinates
- client coordinates
- coordinates [Windows Forms], Windows Forms
ms.assetid: cc06e61f-43b6-4408-a676-2542dcfcd96e
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8f4b42fd71dacb0071013067dc3c14add96c8aca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="windows-forms-coordinates"></a>Współrzędne formularzy systemu Windows
System współrzędnych dla formularza systemu Windows jest oparta na współrzędnych urządzenia i jednostkę urządzenie (zazwyczaj pikseli) jest podstawową jednostką miary Rysowanie w formularzach systemu Windows. Punkty na ekranie są opisane przez pary współrzędną x i y, z współrzędne x zwiększenie w prawo i współrzędną y zwiększenie od góry do dołu. Miejsce pochodzenia względem ekranu, będą się różnić w zależności od tego, czy są określający współrzędne ekranu lub klienta.  
  
## <a name="screen-coordinates"></a>Współrzędne ekranu  
 Aplikacji formularzy systemu Windows określa położenie okna na ekranie we współrzędnych ekranu. Współrzędne ekranu źródła jest lewym górnym rogu ekranu. Pełna położenie okna jest często opisanego przez <xref:System.Drawing.Rectangle> struktury zawierającej współrzędne ekranu dwa punkty, które definiują górnym rogu i prawym dolnym rogu okna.  
  
## <a name="client-coordinates"></a>Współrzędne klienta  
 Aplikacji formularzy systemu Windows określa pozycję punktów w formularzu lub formantu przy użyciu współrzędnych klienta. Punkt początkowy współrzędne klienta jest lewego górnego rogu obszaru klienta formularza lub kontrolki. Współrzędne klienta upewnij się, czy aplikacja może użyć spójne wartości współrzędnych podczas rysowania formularza lub kontrolki, niezależnie od położenia formularza lub kontrolki, na ekranie.  
  
 Wymiary obszaru klienckiego są także opisane przez <xref:System.Drawing.Rectangle> struktury, która zawiera współrzędne klienta dla obszaru. We wszystkich przypadkach Współrzędna lewej górnej krawędzi prostokąta znajduje się w obszarze klienta podczas prawą dolną współrzędną jest wyłączone. Operacje graficzne nie dołączaj dolnej i prawej krawędzi obszaru klienckiego. Na przykład <xref:System.Drawing.Graphics.FillRectangle%2A> metoda będzie zapełnić do prawej i w dolnej krawędzi prostokąt określony, ale nie będzie zawierał te krawędzi.  
  
## <a name="mapping-from-one-type-of-coordinate-to-another"></a>Mapowanie typu współrzędnych  
 Czasami może być konieczne mapowania współrzędne ekranu na współrzędne klienta. Możesz to łatwo zrobić przy użyciu <xref:System.Windows.Forms.Control.PointToClient%2A> i <xref:System.Windows.Forms.Control.PointToScreen%2A> metod w <xref:System.Windows.Forms.Control> klasy. Na przykład <xref:System.Windows.Forms.Control.MousePosition%2A> właściwość <xref:System.Windows.Forms.Control> jest zgłaszany we współrzędnych ekranu, ale chcesz przekonwertować je na współrzędne klienta.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Control.PointToClient%2A>  
 <xref:System.Windows.Forms.Control.PointToScreen%2A>
