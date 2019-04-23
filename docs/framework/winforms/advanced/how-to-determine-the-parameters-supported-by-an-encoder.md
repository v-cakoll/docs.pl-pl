---
title: 'Instrukcje: Określanie parametrów obsługiwanych przez koder'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encoder parameters [Windows Forms], determining supported
ms.assetid: f47ae459-e3ce-4d41-a140-2f6c6aea3f44
ms.openlocfilehash: 2626eee239d9876125340dd133c5a9b3e45c3d7e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59204578"
---
# <a name="how-to-determine-the-parameters-supported-by-an-encoder"></a>Instrukcje: Określanie parametrów obsługiwanych przez koder
Można dostosować parametry obrazu, takie jak poziom jakości i kompresji, ale musisz wiedzieć, które parametry są obsługiwane przez koder danego obrazu. <xref:System.Drawing.Image> Klasa udostępnia <xref:System.Drawing.Image.GetEncoderParameterList%2A> metody, dzięki czemu można określić parametry obrazu, które są obsługiwane w przypadku określonego kodera. Należy określić kodera z identyfikatorem GUID. <xref:System.Drawing.Image.GetEncoderParameterList%2A> Metoda zwraca tablicę <xref:System.Drawing.Imaging.EncoderParameter> obiektów.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu wyświetla obsługiwanych parametrów dla kodera JPEG. Użyj listy parametrów kategorii i skojarzone identyfikatory GUID <xref:System.Drawing.Imaging.Encoder> Przegląd klasy w celu ustalenia kategorii każdego parametru.  
  
 [!code-csharp[UsingImageEncodersDecoders#3](~/samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#3)]
 [!code-vb[UsingImageEncodersDecoders#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Aplikacja Windows Forms.  
  
-   A <xref:System.Windows.Forms.PaintEventArgs>, czyli parametrem <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Lista zainstalowanych koderów](how-to-list-installed-encoders.md)
- [Typy map bitowych](types-of-bitmaps.md)
- [Używanie kodeków obrazu w zarządzanym GDI+](using-image-encoders-and-decoders-in-managed-gdi.md)
