---
title: 'Instrukcje: dodawanie lub usuwanie obrazów ImageList przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
ms.assetid: 5699b244-e37c-4d20-bc35-7441e55c1e3a
ms.openlocfilehash: 346d7107c9c17c5df06fa0e47f7a35355344f590
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880737"
---
# <a name="how-to-add-or-remove-imagelist-images-with-the-designer"></a><span data-ttu-id="9ae1c-102">Instrukcje: dodawanie lub usuwanie obrazów ImageList przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="9ae1c-102">How to: Add or Remove ImageList Images with the Designer</span></span>
<span data-ttu-id="9ae1c-103">Możesz dodać obrazy do <xref:System.Windows.Forms.ImageList> składnika kilka różnych sposobów.</span><span class="sxs-lookup"><span data-stu-id="9ae1c-103">You can add images to an <xref:System.Windows.Forms.ImageList> component several different ways.</span></span> <span data-ttu-id="9ae1c-104">Dodawanie obrazów bardzo szybko przy użyciu tagu inteligentnego skojarzone z <xref:System.Windows.Forms.ImageList>, lub jeśli kilka innych właściwości są ustawiane na <xref:System.Windows.Forms.ImageList>, może okazać się bardziej wygodne do dodania obrazów za pomocą okna właściwości.</span><span class="sxs-lookup"><span data-stu-id="9ae1c-104">You can add images very quickly by using the smart tag associated with the <xref:System.Windows.Forms.ImageList>, or if you are setting several other properties on the <xref:System.Windows.Forms.ImageList>, you may find it more convenient to add images with the Properties window.</span></span> <span data-ttu-id="9ae1c-105">Można również dodać obrazy przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="9ae1c-105">You can also add images by using code.</span></span> <span data-ttu-id="9ae1c-106">Aby uzyskać więcej informacji o tym, jak dodać obrazy z kodem, zobacz [jak: Dodawanie lub usuwanie obrazów za pomocą Windows składnika ImageList formularzy](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span><span class="sxs-lookup"><span data-stu-id="9ae1c-106">For more information about how to add images with code, see [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span> <span data-ttu-id="9ae1c-107">Zazwyczaj wypełnić <xref:System.Windows.Forms.ImageList> składnika z obrazami, zanim zostanie skojarzony z formantem, ale nie jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="9ae1c-107">Typically you populate the <xref:System.Windows.Forms.ImageList> component with images before it is associated with a control, but this is not required.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9ae1c-108">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="9ae1c-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="9ae1c-109">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="9ae1c-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="9ae1c-110">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="9ae1c-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-or-remove-images-by-using-the-properties-window"></a><span data-ttu-id="9ae1c-111">Dodawanie lub usuwanie obrazów za pomocą okna właściwości</span><span class="sxs-lookup"><span data-stu-id="9ae1c-111">To add or remove images by using the Properties window</span></span>  
  
1. <span data-ttu-id="9ae1c-112">Wybierz <xref:System.Windows.Forms.ImageList> składnika, lub dodaj je do formularza.</span><span class="sxs-lookup"><span data-stu-id="9ae1c-112">Select the <xref:System.Windows.Forms.ImageList> component, or add one to the form.</span></span>  
  
2.  <span data-ttu-id="9ae1c-113">W oknie dialogowym właściwości kliknij przycisk oznaczony wielokropkiem (![przycisk wielokropka (...) w oknie dialogowym właściwości programu Visual Studio.](./media/visual-studio-ellipsis-button.png)) obok pozycji <xref:System.Windows.Forms.ImageList.Images%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="9ae1c-113">In the Properties window, click the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.ImageList.Images%2A> property.</span></span>  
  
3. <span data-ttu-id="9ae1c-114">W **Edytor kolekcji obrazów**, kliknij przycisk **Dodaj** lub **Usuń** do dodania lub usunięcia obrazów z listy.</span><span class="sxs-lookup"><span data-stu-id="9ae1c-114">In the **Image Collection Editor**, click **Add** or **Remove** to add or remove images from the list.</span></span>  
  
### <a name="to-add-or-remove-images-using-the-smart-tag"></a><span data-ttu-id="9ae1c-115">Dodawanie lub usuwanie obrazów za pomocą tagów inteligentnych</span><span class="sxs-lookup"><span data-stu-id="9ae1c-115">To add or remove images using the smart tag</span></span>  
  
1. <span data-ttu-id="9ae1c-116">Wybierz <xref:System.Windows.Forms.ImageList> składnika, lub dodaj je do formularza.</span><span class="sxs-lookup"><span data-stu-id="9ae1c-116">Select the <xref:System.Windows.Forms.ImageList> component, or add one to the form.</span></span>  
  
2. <span data-ttu-id="9ae1c-117">Kliknij symbol tagu inteligentnego (![symbol tagu inteligentnego](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))</span><span class="sxs-lookup"><span data-stu-id="9ae1c-117">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))</span></span>  
  
3. <span data-ttu-id="9ae1c-118">W **zadania ImageList** okno dialogowe, wybierz opcję **wybierz obrazy**.</span><span class="sxs-lookup"><span data-stu-id="9ae1c-118">In the **ImageList Tasks** dialog box, select **Choose Images**.</span></span>  
  
4. <span data-ttu-id="9ae1c-119">W **Editor Kolekce Images** kliknij **Dodaj** lub **Usuń** do dodania lub usunięcia obrazów z listy.</span><span class="sxs-lookup"><span data-stu-id="9ae1c-119">In the **Images Collection Editor** click **Add** or **Remove** to add or remove images from the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ae1c-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9ae1c-120">See also</span></span>

- [<span data-ttu-id="9ae1c-121">Obrazy, mapy bitowe i metapliki</span><span class="sxs-lookup"><span data-stu-id="9ae1c-121">Images, Bitmaps, and Metafiles</span></span>](../advanced/images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="9ae1c-122">Przewodnik: Wykonywania typowych zadań przy użyciu inteligentnych tagów w Windows Forms, formanty</span><span class="sxs-lookup"><span data-stu-id="9ae1c-122">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>](performing-common-tasks-using-smart-tags-on-wf-controls.md)
- [<span data-ttu-id="9ae1c-123">ImageList, składnik</span><span class="sxs-lookup"><span data-stu-id="9ae1c-123">ImageList Component</span></span>](imagelist-component-windows-forms.md)
