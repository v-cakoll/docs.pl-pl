---
title: 'Porady: dodawanie lub usuwanie obrazów ImageList przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
ms.assetid: 5699b244-e37c-4d20-bc35-7441e55c1e3a
ms.openlocfilehash: c85e55b6aef45eea65e6f82269375f80acf71017
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-or-remove-imagelist-images-with-the-designer"></a><span data-ttu-id="ff091-102">Porady: dodawanie lub usuwanie obrazów ImageList przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="ff091-102">How to: Add or Remove ImageList Images with the Designer</span></span>
<span data-ttu-id="ff091-103">Można dodać obrazy <xref:System.Windows.Forms.ImageList> składnika kilka różnych sposobów.</span><span class="sxs-lookup"><span data-stu-id="ff091-103">You can add images to an <xref:System.Windows.Forms.ImageList> component several different ways.</span></span> <span data-ttu-id="ff091-104">Można dodać obrazy bardzo szybko przy użyciu tagów inteligentnych skojarzone z <xref:System.Windows.Forms.ImageList>, lub jeśli kilka innych właściwości są ustawiane na <xref:System.Windows.Forms.ImageList>, może być wygodniejsze dodać obrazy z okna właściwości.</span><span class="sxs-lookup"><span data-stu-id="ff091-104">You can add images very quickly by using the smart tag associated with the <xref:System.Windows.Forms.ImageList>, or if you are setting several other properties on the <xref:System.Windows.Forms.ImageList>, you may find it more convenient to add images with the Properties window.</span></span> <span data-ttu-id="ff091-105">Obrazy można także dodać przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="ff091-105">You can also add images by using code.</span></span> <span data-ttu-id="ff091-106">Aby uzyskać więcej informacji o dodawaniu obrazów z kodem, zobacz [porady: Dodawanie lub usuwanie obrazów za pomocą składnika ImageList formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span><span class="sxs-lookup"><span data-stu-id="ff091-106">For more information about how to add images with code, see [How to: Add or Remove Images with the Windows Forms ImageList Component](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span> <span data-ttu-id="ff091-107">Zwykle wypełnić <xref:System.Windows.Forms.ImageList> składnika z obrazami przed jest skojarzony z formantem, ale nie jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="ff091-107">Typically you populate the <xref:System.Windows.Forms.ImageList> component with images before it is associated with a control, but this is not required.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ff091-108">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="ff091-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="ff091-109">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="ff091-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="ff091-110">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="ff091-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-or-remove-images-by-using-the-properties-window"></a><span data-ttu-id="ff091-111">Aby dodać lub usunąć obrazów przy użyciu okna właściwości</span><span class="sxs-lookup"><span data-stu-id="ff091-111">To add or remove images by using the Properties window</span></span>  
  
1.  <span data-ttu-id="ff091-112">Wybierz <xref:System.Windows.Forms.ImageList> składnika, lub dodaj je do formularza.</span><span class="sxs-lookup"><span data-stu-id="ff091-112">Select the <xref:System.Windows.Forms.ImageList> component, or add one to the form.</span></span>  
  
2.  <span data-ttu-id="ff091-113">W oknie właściwości kliknij przycisk oznaczony wielokropkiem (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) obok pozycji <xref:System.Windows.Forms.ImageList.Images%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="ff091-113">In the Properties window, click the ellipsis button (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.ImageList.Images%2A> property.</span></span>  
  
3.  <span data-ttu-id="ff091-114">W **edytora kolekcji obrazów**, kliknij przycisk **Dodaj** lub **Usuń** można dodać ani usunąć z listy obrazów.</span><span class="sxs-lookup"><span data-stu-id="ff091-114">In the **Image Collection Editor**, click **Add** or **Remove** to add or remove images from the list.</span></span>  
  
### <a name="to-add-or-remove-images-using-the-smart-tag"></a><span data-ttu-id="ff091-115">Aby dodać lub usunąć obrazów za pomocą tagów inteligentnych</span><span class="sxs-lookup"><span data-stu-id="ff091-115">To add or remove images using the smart tag</span></span>  
  
1.  <span data-ttu-id="ff091-116">Wybierz <xref:System.Windows.Forms.ImageList> składnika, lub dodaj je do formularza.</span><span class="sxs-lookup"><span data-stu-id="ff091-116">Select the <xref:System.Windows.Forms.ImageList> component, or add one to the form.</span></span>  
  
2.  <span data-ttu-id="ff091-117">Kliknij symbol tagu inteligentnego (![symbol tagu inteligentnego](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))</span><span class="sxs-lookup"><span data-stu-id="ff091-117">Click the smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))</span></span>  
  
3.  <span data-ttu-id="ff091-118">W **zadania ImageList** okno dialogowe, wybierz opcję **wybierz obrazy**.</span><span class="sxs-lookup"><span data-stu-id="ff091-118">In the **ImageList Tasks** dialog box, select **Choose Images**.</span></span>  
  
4.  <span data-ttu-id="ff091-119">W **edytora kolekcji obrazów** kliknij **Dodaj** lub **Usuń** można dodać ani usunąć z listy obrazów.</span><span class="sxs-lookup"><span data-stu-id="ff091-119">In the **Images Collection Editor** click **Add** or **Remove** to add or remove images from the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff091-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ff091-120">See Also</span></span>  
 [<span data-ttu-id="ff091-121">Obrazy, mapy bitowe i metapliki</span><span class="sxs-lookup"><span data-stu-id="ff091-121">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [<span data-ttu-id="ff091-122">Przewodnik: przeprowadzanie typowych zadań z tagami inteligentnymi na kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ff091-122">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls.md)  
 [<span data-ttu-id="ff091-123">ImageList, składnik</span><span class="sxs-lookup"><span data-stu-id="ff091-123">ImageList Component</span></span>](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)
