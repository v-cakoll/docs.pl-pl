---
title: 'Instrukcje: Lista zainstalowanych koderów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image codecs [Windows Forms], listing
- image encoders [Windows Forms], listing
ms.assetid: 49e8e4e9-7a67-42d9-86bf-08821cdc282e
ms.openlocfilehash: 492930b7d8a47db478c8fa0f282cb5f491e144ac
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708460"
---
# <a name="how-to-list-installed-encoders"></a>Instrukcje: Lista zainstalowanych koderów
Możesz wyświetlić listę kodeków obrazu dostępne na komputerze, w celu ustalenia, czy aplikację można zapisać do pliku określonego obrazu w formacie. <xref:System.Drawing.Imaging.ImageCodecInfo> Klasa udostępnia <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> metody statyczne, aby określić, który obraz koderów są dostępne. <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> Zwraca tablicę <xref:System.Drawing.Imaging.ImageCodecInfo> obiektów.  
  
## <a name="example"></a>Przykład  
 Poniższy kod generuje lista zainstalowanych koderów i ich wartości właściwości.  
  
 [!code-csharp[UsingImageEncodersDecoders#1](~/samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#1)]
 [!code-vb[UsingImageEncodersDecoders#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Aplikacja Windows Forms.  
  
-   A <xref:System.Windows.Forms.PaintEventArgs>, czyli parametrem <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Zobacz także
- [Instrukcje: Lista zainstalowanych dekoderów](how-to-list-installed-decoders.md)
- [Używanie kodeków obrazu w zarządzanym GDI+](using-image-encoders-and-decoders-in-managed-gdi.md)
