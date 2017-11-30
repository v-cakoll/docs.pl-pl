---
title: Metapliki w GDI+
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
- images [Windows Forms], metafiles
- GDI+, metafiles
- metafiles
ms.assetid: 51da872c-c783-440f-8bf6-1e580a966c31
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6b75ceb08df0454172a000d5d1ad15445f685ddf
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="metafiles-in-gdi"></a>Metapliki w GDI+
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]udostępnia <xref:System.Drawing.Imaging.Metafile> klasy, dzięki czemu można rejestrować i wyświetlanie metaplików. Metaplik, nazywany również obrazem wektora jest obraz, który jest przechowywany jako sekwencja rysowania poleceń i ustawień. Polecenia i ustawienia są rejestrowane w <xref:System.Drawing.Imaging.Metafile> można przechowywane w pamięci obiekt lub zapisać do pliku lub strumienia.  
  
## <a name="metafile-formats"></a>Formaty metaplików  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]można wyświetlić metapliki, które były przechowywane w następujących formatach:  
  
-   Windows Metafile (WMF)  
  
-   Rozszerzony metaplik (EMF)  
  
-   EMF +  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]można rejestrować metapliki w formatach EMF i EMF +, ale nie w formacie WMF.  
  
 EMF + jest rozszerzeniem EMF, który umożliwia [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] rekordów mają być przechowywane. Istnieją dwie odmiany EMF + format: EMF + tylko i EMF + procesory. Metapliki EMF + tylko zawierają tylko [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] rekordów. Metapliki takie mogą być wyświetlane przez [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] , ale nie przez [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]. Metapliki EMF + podwójnego zawierają [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] i [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] rekordów. Każdy [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] rekordów w dwóch EMF + metaplik łączyć alternatywny [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] rekordu. Metapliki takie mogą być wyświetlane przez [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] lub [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].  
  
 W poniższym przykładzie przedstawiono metaplik, który został wcześniej zapisany jako plik. Metaplik jest wyświetlana z jego lewego górnego rogu na (100, 100).  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>Zobacz też  
 [Obrazy, mapy bitowe i metapliki](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
