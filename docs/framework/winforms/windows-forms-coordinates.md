---
title: Coordinate
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms coordinates
- screen coordinates
- client coordinates
- coordinates [Windows Forms], Windows Forms
ms.assetid: cc06e61f-43b6-4408-a676-2542dcfcd96e
ms.openlocfilehash: c95888f31bfc867e9c028d53072ab3d710256708
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734666"
---
# <a name="windows-forms-coordinates"></a>Współrzędne formularzy systemu Windows
Układ współrzędnych dla formularza systemu Windows jest oparty na współrzędnych urządzenia, a podstawowa jednostka miary podczas rysowania w Windows Forms jest jednostką urządzenia (zazwyczaj piksel). Punkty na ekranie są opisane przez pary współrzędnych x i y, a współrzędne x zwiększają się po prawej stronie, a Współrzędne y rosną od góry do dołu. Lokalizacja pochodzenia względem ekranu różni się w zależności od tego, czy określasz Współrzędne ekranu lub klienta.  
  
## <a name="screen-coordinates"></a>Współrzędne ekranu  
 Aplikacja Windows Forms określa pozycję okna na ekranie w obszarze Współrzędne ekranu. Dla współrzędnych ekranu, początek jest lewym górnym rogu ekranu. Pełna pozycja okna jest często opisywana przez strukturę <xref:System.Drawing.Rectangle>ą zawierającą Współrzędne ekranu dwóch punktów, które definiują lewy górny i prawy dolny róg okna.  
  
## <a name="client-coordinates"></a>Współrzędne klienta  
 Aplikacja Windows Forms określa położenie punktów w formularzu lub kontrolce przy użyciu współrzędnych klienta. Podstawą współrzędnych klienta jest lewy górny róg obszaru klienckiego kontrolki lub formularza. Współrzędne klienta zapewniają, że aplikacja może używać spójnych wartości współrzędnych podczas rysowania w formularzu lub kontrolce, niezależnie od pozycji formularza lub kontrolki na ekranie.  
  
 Wymiary obszaru klienta są również opisane przez strukturę <xref:System.Drawing.Rectangle>, która zawiera współrzędne klienta dla obszaru. We wszystkich przypadkach Współrzędna górnej krawędzi prostokąta jest dołączana do obszaru klienckiego, podczas gdy podwyższanie poziomu jest wyłączone. Operacje graficzne nie obejmują praw i dolnych krawędzi obszaru klienckiego. Na przykład Metoda <xref:System.Drawing.Graphics.FillRectangle%2A> wypełni się do prawej i dolnej krawędzi określonego prostokąta, ale nie będzie zawierać tych krawędzi.  
  
## <a name="mapping-from-one-type-of-coordinate-to-another"></a>Mapowanie z jednego typu współrzędnej na inny  
 Czasami może być konieczne zamapowanie ze współrzędnych ekranu na współrzędne klienta. Można to łatwo zrobić przy użyciu <xref:System.Windows.Forms.Control.PointToClient%2A> i <xref:System.Windows.Forms.Control.PointToScreen%2A> metod dostępnych w klasie <xref:System.Windows.Forms.Control>. Na przykład właściwość <xref:System.Windows.Forms.Control.MousePosition%2A> <xref:System.Windows.Forms.Control> jest raportowana we współrzędnych ekranu, ale może być konieczne ich przekonwertowanie na współrzędne klienta.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Control.PointToClient%2A>
- <xref:System.Windows.Forms.Control.PointToScreen%2A>
