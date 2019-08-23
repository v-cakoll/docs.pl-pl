---
title: 'Instrukcje: Tworzenie obrazów miniatur'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thumbnail images [Windows Forms], creating
- images [Windows Forms], creating thumbnails
ms.assetid: e956242a-1e5b-4217-a3cf-5f3fb45d00ba
ms.openlocfilehash: 786a92d99f5e7a0c27f502efa9a5fe617ac4d4d6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923753"
---
# <a name="how-to-create-thumbnail-images"></a>Instrukcje: Tworzenie obrazów miniatur
Obraz miniatury jest małą wersją obrazu. Można utworzyć miniaturę obrazu, wywołując <xref:System.Drawing.Image.GetThumbnailImage%2A> metodę <xref:System.Drawing.Image> obiektu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład konstruuje <xref:System.Drawing.Image> obiekt z pliku jpg. Oryginalny obraz ma szerokość 640 pikseli i wysokość 479 pikseli. Kod tworzy obraz miniatury o szerokości 100 pikseli i wysokości 100 pikseli.  
  
 Na poniższej ilustracji przedstawiono obraz miniatury:  
  
 ![Zrzut ekranu przedstawiający miniaturę danych wyjściowych.](./media/how-to-create-thumbnail-images/construct-thumbnail-image.png)  
  
> [!NOTE]
> W tym przykładzie metoda wywołania zwrotnego jest zadeklarowana, ale nigdy nie jest używana. Obsługuje to wszystkie wersje interfejsu GDI+.  
  
 [!code-csharp[System.Drawing.WorkingWithImages#71](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.WorkingWithImages#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użycia z Windows Forms i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który <xref:System.Windows.Forms.Control.Paint> jest parametrem programu obsługi zdarzeń. Aby uruchomić ten przykład, wykonaj następujące kroki:  
  
1. Utwórz nową aplikację Windows Forms.  
  
2. Dodaj przykładowy kod do formularza.  
  
3. Utwórz procedurę obsługi dla <xref:System.Windows.Forms.Control.Paint> zdarzenia formularza  
  
4. W programie `GetThumbnail` `e` obsługi Wywołaj metodę i przekaż <xref:System.Windows.Forms.PaintEventArgs>polecenie. <xref:System.Windows.Forms.Control.Paint>  
  
5. Znajdź plik obrazu, dla którego chcesz utworzyć miniaturę.  
  
6. `GetThumbnail` W metodzie określ ścieżkę i nazwę pliku do obrazu.  
  
7. Naciśnij klawisz F5, aby uruchomić przykład.  
  
     Obraz miniatury 100 według 100 pojawia się w formularzu.  
  
## <a name="see-also"></a>Zobacz także

- [Obrazy, mapy bitowe i metapliki](images-bitmaps-and-metafiles.md)
- [Praca z obrazami, mapami bitowymi, ikonami i metaplikami](working-with-images-bitmaps-icons-and-metafiles.md)
