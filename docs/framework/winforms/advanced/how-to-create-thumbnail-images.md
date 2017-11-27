---
title: "Porady: tworzenie obrazów miniatur"
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
- thumbnail images [Windows Forms], creating
- images [Windows Forms], creating thumbnails
ms.assetid: e956242a-1e5b-4217-a3cf-5f3fb45d00ba
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2a3866274340932819a419c622c10072dd67c439
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-thumbnail-images"></a>Porady: tworzenie obrazów miniatur
Obraz miniatury jest małą wersję obrazu. Obraz miniatury można utworzyć przez wywołanie metody <xref:System.Drawing.Image.GetThumbnailImage%2A> metody <xref:System.Drawing.Image> obiektu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Drawing.Image> obiekt z pliku JPG. Oryginalny obraz ma 640 pikseli szerokości i wysokości 479 pikseli. Kod tworzy miniaturę, która zawiera 100 pikseli szerokości i wysokości 100 pikseli.  
  
 Na poniższej ilustracji przedstawiono obraz miniatury.  
  
 ![Obraz miniatury](../../../../docs/framework/winforms/advanced/media/thumbnail1.png "Thumbnail1")  
  
> [!NOTE]
>  W tym przykładzie metoda wywołania zwrotnego jest zadeklarowana, ale nigdy używane. Obejmuje to obsługę wszystkich wersji GDI +.  
  
 [!code-csharp[System.Drawing.WorkingWithImages#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.WorkingWithImages#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń. Aby uruchomić przykład, wykonaj następujące kroki:  
  
1.  Tworzenie nowej aplikacji formularzy systemu Windows.  
  
2.  Przykładowy kod należy dodać do formularza.  
  
3.  Tworzenie programu obsługi dla formularza <xref:System.Windows.Forms.Control.Paint> zdarzeń  
  
4.  W <xref:System.Windows.Forms.Control.Paint> obsługi, wywołaj `GetThumbnail` — metoda i przekazać `e` dla <xref:System.Windows.Forms.PaintEventArgs>.  
  
5.  Znajdź plik obrazu, który ma być miniaturę.  
  
6.  W `GetThumbnail` metody, określ ścieżkę i nazwę obrazu pliku.  
  
7.  Naciśnij klawisz F5, aby uruchomić w przykładzie.  
  
     Obraz miniatury 100 na 100 pojawia się w formularzu.  
  
## <a name="see-also"></a>Zobacz też  
 [Obrazy, mapy bitowe i metapliki](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [Praca z obrazami, mapami bitowymi, ikony i metapliki](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
