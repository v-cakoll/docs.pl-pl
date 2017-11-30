---
title: "Porady: lista zainstalowanych dekoderów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image codecs [Windows Forms], listing
- image decoders [Windows Forms], listing
ms.assetid: 11417191-8c95-40ca-8024-779e61706fb6
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 17cbdebfa6cbb0cacacd923de4bd22125c812938
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-list-installed-decoders"></a>Porady: lista zainstalowanych dekoderów
Możesz wyświetlić listę dekodery obrazów dostępne na komputerze, w celu ustalenia, czy aplikacja może odczytywać format pliku określonego obrazu. <xref:System.Drawing.Imaging.ImageCodecInfo> Klasa udostępnia <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> metody statyczne, aby ustalić, który obraz dekodery są dostępne. <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A>Zwraca tablicę <xref:System.Drawing.Imaging.ImageCodecInfo> obiektów.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu generuje listę zainstalowanych dekoderów i ich wartości właściwości.  
  
 [!code-csharp[UsingImageEncodersDecoders#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#2)]
 [!code-vb[UsingImageEncodersDecoders#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#2)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Aplikacji formularzy systemu Windows.  
  
-   A <xref:System.Windows.Forms.PaintEventArgs>, który jest parametrem <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: lista zainstalowanych koderów](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 [Używanie kodeków obrazu w zarządzanym GDI +](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
