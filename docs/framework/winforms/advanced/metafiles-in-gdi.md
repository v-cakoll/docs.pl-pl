---
title: Metapliki w GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], metafiles
- GDI+, metafiles
- metafiles
ms.assetid: 51da872c-c783-440f-8bf6-1e580a966c31
ms.openlocfilehash: df54289722cf12bad840722c6eafdaa43279a5dc
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504583"
---
# <a name="metafiles-in-gdi"></a>Metapliki w GDI+
GDI + zapewnia <xref:System.Drawing.Imaging.Metafile> klasy, dzięki czemu mogą rejestrować i wyświetlanie metaplików. Metaplik, nazywany również obrazem wektora jest obraz, który jest przechowywany jako sekwencja rysowania poleceń i ustawień. Polecenia i ustawienia są rejestrowane w <xref:System.Drawing.Imaging.Metafile> obiektu, które mogą być przechowywane w pamięci lub zapisany do pliku lub strumienia.  
  
## <a name="metafile-formats"></a>Formaty metaplików  
 GDI + można wyświetlić metapliki, które były przechowywane w następujących formatach:  
  
- Windows metaplików (WMF)  
  
- Rozszerzony metaplik (EMF)  
  
- EMF+  
  
 GDI + można rejestrować metapliki format EMF i EMF +, ale nie w formacie programu WMF.  
  
 EMF + jest rozszerzeniem EMF umożliwiająca GDI + rekordy mają być przechowywane. Istnieją dwie odmiany format EMF +: EMF + tylko i EMF + dwa porty. Metapliki EMF + tylko zawierać tylko rekordy GDI +. Metapliki takie mogą być wyświetlane w GDI +, ale nie GDI. Metapliki EMF + podwójnego zawiera rekordy GDI + i GDI. Każdy rekord GDI + w metaplik EMF + podwójnego jest powiązany z alternatywny rekord GDI. Metapliki takie mogą być wyświetlane w GDI + lub GDI.  
  
 Poniższy przykład wyświetla metaplik, który został wcześniej zapisany jako plik. Metaplik jest wyświetlany z jego lewego górnego rogu w (100, 100).  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>Zobacz także

- [Obrazy, mapy bitowe i metapliki](images-bitmaps-and-metafiles.md)
