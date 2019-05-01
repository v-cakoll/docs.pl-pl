---
title: Współrzędne formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms coordinates
- screen coordinates
- client coordinates
- coordinates [Windows Forms], Windows Forms
ms.assetid: cc06e61f-43b6-4408-a676-2542dcfcd96e
ms.openlocfilehash: 6feabadff17538f4a7368c348f7b72226e2d678e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61800155"
---
# <a name="windows-forms-coordinates"></a>Współrzędne formularzy systemu Windows
System współrzędnych dla formularza Windows opiera się na współrzędnych urządzenia i podstawowa jednostka miary Rysowanie w formularzach Windows Forms jest jednostką urządzenia (zazwyczaj w pikselach). Punkty na ekranie są opisane przez pary współrzędną x i y, za pomocą współrzędnych x zwiększa się po prawej stronie i współrzędne y zwiększenie od góry do dołu. Lokalizacja pochodzenia względem ekranu, różnią się w zależności od tego, czy określasz współrzędne ekranu lub klienta.  
  
## <a name="screen-coordinates"></a>Współrzędne ekranu  
 Aplikacja Windows Forms Określa położenie okna na ekranie współrzędne ekranu. Na współrzędne ekranu pochodzi w lewym górnym rogu ekranu. Pełne położenie okna jest często opisywana przez <xref:System.Drawing.Rectangle> struktury zawierającej współrzędne ekranu dwa punkty, które definiują lewym i prawym dolnym rogu okna.  
  
## <a name="client-coordinates"></a>Współrzędne klienta  
 Aplikacji Windows Forms określa pozycję punktów w formularza lub formantu przy użyciu współrzędnych klienta. Początek dla współrzędnych klienta znajduje się w lewym górnym rogu obszaru klienta formularza lub formantu. Współrzędne klienta upewnij się, że aplikacja może użyć spójnego wartości współrzędnych podczas rysowania w formularza lub formantu, niezależnie od tego, położenie formularza lub kontrolki na ekranie.  
  
 Wymiary obszaru klienta są także opisane przez <xref:System.Drawing.Rectangle> strukturę, która zawiera współrzędne klienta dla danego obszaru. We wszystkich przypadkach Współrzędna lewej górnej krawędzi prostokąta znajduje się w obszar klienta, gdy prawą dolną współrzędną jest wykluczona. Operacje graficzne nie dołączaj dolnej i prawej krawędzi obszaru klienta. Na przykład <xref:System.Drawing.Graphics.FillRectangle%2A> metody zastaną zapełnione prawo i dolną krawędzią prostokąt określony, ale nie będzie zawierać tych krawędzi.  
  
## <a name="mapping-from-one-type-of-coordinate-to-another"></a>Mapowania z jednego typu współrzędnych  
 Od czasu do czasu może być konieczne mapowania współrzędne ekranu na współrzędne klienta. Można to łatwo zrobić przy użyciu <xref:System.Windows.Forms.Control.PointToClient%2A> i <xref:System.Windows.Forms.Control.PointToScreen%2A> metod dostępnych w <xref:System.Windows.Forms.Control> klasy. Na przykład <xref:System.Windows.Forms.Control.MousePosition%2A> właściwość <xref:System.Windows.Forms.Control> jest zgłaszany we współrzędnych ekranu, ale można je przekształcić w współrzędne klienta.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Control.PointToClient%2A>
- <xref:System.Windows.Forms.Control.PointToScreen%2A>
