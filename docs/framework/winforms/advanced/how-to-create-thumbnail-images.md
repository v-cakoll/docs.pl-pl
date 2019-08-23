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
# <a name="how-to-create-thumbnail-images"></a><span data-ttu-id="d2394-102">Instrukcje: Tworzenie obrazów miniatur</span><span class="sxs-lookup"><span data-stu-id="d2394-102">How to: Create Thumbnail Images</span></span>
<span data-ttu-id="d2394-103">Obraz miniatury jest małą wersją obrazu.</span><span class="sxs-lookup"><span data-stu-id="d2394-103">A thumbnail image is a small version of an image.</span></span> <span data-ttu-id="d2394-104">Można utworzyć miniaturę obrazu, wywołując <xref:System.Drawing.Image.GetThumbnailImage%2A> metodę <xref:System.Drawing.Image> obiektu.</span><span class="sxs-lookup"><span data-stu-id="d2394-104">You can create a thumbnail image by calling the <xref:System.Drawing.Image.GetThumbnailImage%2A> method of an <xref:System.Drawing.Image> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2394-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="d2394-105">Example</span></span>  
 <span data-ttu-id="d2394-106">Poniższy przykład konstruuje <xref:System.Drawing.Image> obiekt z pliku jpg.</span><span class="sxs-lookup"><span data-stu-id="d2394-106">The following example constructs an <xref:System.Drawing.Image> object from a JPG file.</span></span> <span data-ttu-id="d2394-107">Oryginalny obraz ma szerokość 640 pikseli i wysokość 479 pikseli.</span><span class="sxs-lookup"><span data-stu-id="d2394-107">The original image has a width of 640 pixels and a height of 479 pixels.</span></span> <span data-ttu-id="d2394-108">Kod tworzy obraz miniatury o szerokości 100 pikseli i wysokości 100 pikseli.</span><span class="sxs-lookup"><span data-stu-id="d2394-108">The code creates a thumbnail image that has a width of 100 pixels and a height of 100 pixels.</span></span>  
  
 <span data-ttu-id="d2394-109">Na poniższej ilustracji przedstawiono obraz miniatury:</span><span class="sxs-lookup"><span data-stu-id="d2394-109">The following illustration shows the thumbnail image:</span></span>  
  
 ![Zrzut ekranu przedstawiający miniaturę danych wyjściowych.](./media/how-to-create-thumbnail-images/construct-thumbnail-image.png)  
  
> [!NOTE]
> <span data-ttu-id="d2394-111">W tym przykładzie metoda wywołania zwrotnego jest zadeklarowana, ale nigdy nie jest używana.</span><span class="sxs-lookup"><span data-stu-id="d2394-111">In this example, a callback method is declared, but never used.</span></span> <span data-ttu-id="d2394-112">Obsługuje to wszystkie wersje interfejsu GDI+.</span><span class="sxs-lookup"><span data-stu-id="d2394-112">This supports all versions of GDI+.</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#71](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.WorkingWithImages#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d2394-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="d2394-113">Compiling the Code</span></span>  
 <span data-ttu-id="d2394-114">Poprzedni przykład jest przeznaczony do użycia z Windows Forms i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który <xref:System.Windows.Forms.Control.Paint> jest parametrem programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d2394-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="d2394-115">Aby uruchomić ten przykład, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="d2394-115">To run the example, follow these steps:</span></span>  
  
1. <span data-ttu-id="d2394-116">Utwórz nową aplikację Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d2394-116">Create a new Windows Forms application.</span></span>  
  
2. <span data-ttu-id="d2394-117">Dodaj przykładowy kod do formularza.</span><span class="sxs-lookup"><span data-stu-id="d2394-117">Add the example code to the form.</span></span>  
  
3. <span data-ttu-id="d2394-118">Utwórz procedurę obsługi dla <xref:System.Windows.Forms.Control.Paint> zdarzenia formularza</span><span class="sxs-lookup"><span data-stu-id="d2394-118">Create a handler for the form's <xref:System.Windows.Forms.Control.Paint> event</span></span>  
  
4. <span data-ttu-id="d2394-119">W programie `GetThumbnail` `e` obsługi Wywołaj metodę i przekaż <xref:System.Windows.Forms.PaintEventArgs>polecenie. <xref:System.Windows.Forms.Control.Paint></span><span class="sxs-lookup"><span data-stu-id="d2394-119">In the <xref:System.Windows.Forms.Control.Paint> handler, call the `GetThumbnail` method and pass `e` for <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
5. <span data-ttu-id="d2394-120">Znajdź plik obrazu, dla którego chcesz utworzyć miniaturę.</span><span class="sxs-lookup"><span data-stu-id="d2394-120">Find an image file that you want to make a thumbnail of.</span></span>  
  
6. <span data-ttu-id="d2394-121">`GetThumbnail` W metodzie określ ścieżkę i nazwę pliku do obrazu.</span><span class="sxs-lookup"><span data-stu-id="d2394-121">In the `GetThumbnail` method, specify the path and file name to your image.</span></span>  
  
7. <span data-ttu-id="d2394-122">Naciśnij klawisz F5, aby uruchomić przykład.</span><span class="sxs-lookup"><span data-stu-id="d2394-122">Press F5 to run the example.</span></span>  
  
     <span data-ttu-id="d2394-123">Obraz miniatury 100 według 100 pojawia się w formularzu.</span><span class="sxs-lookup"><span data-stu-id="d2394-123">A 100 by 100 thumbnail image appears on the form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2394-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d2394-124">See also</span></span>

- [<span data-ttu-id="d2394-125">Obrazy, mapy bitowe i metapliki</span><span class="sxs-lookup"><span data-stu-id="d2394-125">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="d2394-126">Praca z obrazami, mapami bitowymi, ikonami i metaplikami</span><span class="sxs-lookup"><span data-stu-id="d2394-126">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
