---
title: 'Instrukcje: Lista zainstalowanych dekoderów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image codecs [Windows Forms], listing
- image decoders [Windows Forms], listing
ms.assetid: 11417191-8c95-40ca-8024-779e61706fb6
ms.openlocfilehash: 961862d6212b7e76812fc222d3a99f08528d9a16
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626905"
---
# <a name="how-to-list-installed-decoders"></a>Instrukcje: Lista zainstalowanych dekoderów
Możesz wyświetlić listę dekodery obrazów dostępnych na komputerze, w celu ustalenia, czy aplikacja może odczytywać format pliku określonego obrazu. <xref:System.Drawing.Imaging.ImageCodecInfo> Klasa udostępnia <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> metody statyczne, aby określić, który obraz dekodery są dostępne. <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> Zwraca tablicę <xref:System.Drawing.Imaging.ImageCodecInfo> obiektów.  
  
## <a name="example"></a>Przykład  
 Poniższy kod generuje lista zainstalowanych dekoderów i ich wartości właściwości.  
  
 [!code-csharp[UsingImageEncodersDecoders#2](~/samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#2)]
 [!code-vb[UsingImageEncodersDecoders#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#2)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Aplikacja Windows Forms.  
  
- A <xref:System.Windows.Forms.PaintEventArgs>, czyli parametrem <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Lista zainstalowanych koderów](how-to-list-installed-encoders.md)
- [Używanie kodeków obrazu w zarządzanym GDI+](using-image-encoders-and-decoders-in-managed-gdi.md)
