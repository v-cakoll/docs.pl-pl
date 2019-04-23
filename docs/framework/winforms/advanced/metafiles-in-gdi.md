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
ms.openlocfilehash: bb972f158496192aa38f10564209bb2781837414
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59119863"
---
# <a name="metafiles-in-gdi"></a>Metapliki w GDI+
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] udostępnia <xref:System.Drawing.Imaging.Metafile> klasy, dzięki czemu mogą rejestrować i wyświetlanie metaplików. Metaplik, nazywany również obrazem wektora jest obraz, który jest przechowywany jako sekwencja rysowania poleceń i ustawień. Polecenia i ustawienia są rejestrowane w <xref:System.Drawing.Imaging.Metafile> obiektu, które mogą być przechowywane w pamięci lub zapisany do pliku lub strumienia.  
  
## <a name="metafile-formats"></a>Formaty metaplików  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] można wyświetlić metapliki, które były przechowywane w następujących formatach:  
  
-   Windows metaplików (WMF)  
  
-   Rozszerzony metaplik (EMF)  
  
-   EMF+  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] można rejestrować metapliki format EMF i EMF +, ale nie w formacie programu WMF.  
  
 EMF + jest rozszerzeniem EMF, która umożliwia [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] rekordy, które mają być przechowywane. Istnieją dwie odmiany format EMF +: EMF + tylko i EMF + dwa porty. Metapliki EMF + tylko zawierają tylko [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] rekordów. Metapliki takie mogą być wyświetlane przez [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] , ale nie za [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]. Metapliki EMF + podwójne zawiera [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] i [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] rekordów. Każdy [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] rekordów w podwójne EMF + metaplik jest powiązany z alternatywnego [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] rekordu. Metapliki takie mogą być wyświetlane przez [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] lub [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].  
  
 Poniższy przykład wyświetla metaplik, który został wcześniej zapisany jako plik. Metaplik jest wyświetlany z jego lewego górnego rogu w (100, 100).  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>Zobacz także

- [Obrazy, mapy bitowe i metapliki](images-bitmaps-and-metafiles.md)
